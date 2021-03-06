---
title: Conceitos - com o Python para adquirir um token de acesso.
description: Este artigo ajuda-o a compreender como utilizar Python para adquirir um token de acesso de OAuth2. Isso é necessária para a implementação do delegado de autenticação.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 02/04/2019
ms.author: mbaldwin
ms.openlocfilehash: e325dc6c3b79cdd7e7720f0bca50d8bdda045979
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57331941"
---
# <a name="acquire-an-access-token-python"></a>Adquirir um token de acesso (Python)

Este exemplo demonstra como chamar um script de Python externo para obter um token OAuth2. Um token de acesso de OAuth2 válido é necessária para a implementação do delegado de autenticação.

## <a name="prerequisites"></a>Pré-requisitos

Para executar o exemplo abaixo:

- Instale o Python 2.7.
- Implemente utils.h/cpp no seu projeto. 
- auth.PY devem ser adicionados ao seu projeto e coexistem no mesmo diretório que os binários no build.
- Concluída [instalação do SDK (MIP) e configuração](setup-configure-mip.md). Entre outras tarefas, terá de registar a sua aplicação de cliente no seu inquilino do Azure Active Directory (Azure AD). O Azure AD irá fornecer um ID de aplicação, também conhecido como ID de cliente, que é utilizada na sua lógica de aquisição do token.

Esse código não foi concebido para utilização em produção. Só podem ser utilizada para desenvolvimento e conceitos de autenticação de compreensão. O exemplo é para várias plataformas.

## <a name="sampleauthacquiretoken"></a>sample::auth::AcquireToken()

No exemplo a autenticação simples, demonstramos uma simples `AcquireToken()` função que demorou sem parâmetros e devolveu um valor de token hard-coded. Neste exemplo, podemos irá sobrecarregar AcquireToken() aceitam parâmetros de autenticação e chamar um script de Python externo para devolver o token.

### <a name="authh"></a>auth.h

No auth.h, `AcquireToken()` está sobrecarregado e a função sobrecarregada e os parâmetros atualizados são os seguintes:

```cpp
//auth.h
#include <string>

namespace sample {
  namespace auth {
    std::string AcquireToken();

    std::string AcquireToken(
        const std::string& userName, //A string value containing the user's UPN.
        const std::string& password, //The user's password in plaintext
        const std::string& clientId, //The Azure AD client ID (also known as Application ID) of your application.
        const std::string& resource, //The resource URL for which an OAuth2 token is required. Provided by challenge object.
        const std::string& authority); //The authentication authority endpoint. Provided by challenge object.
    }
}
```

Os primeiros três parâmetros serão fornecidos pelo utilizador entrada ou de disco rígido codificada em seu aplicativo. Os últimos dois parâmetros são fornecidos pelo SDK para o delegado de autenticação. 


### <a name="authcpp"></a>auth.cpp

Na auth.cpp, podemos adicionar a definição da função sobrecarregado e definir o código necessário para chamar o script de Python. A função aceita todos os parâmetros fornecidos e passa para o script de Python. O script é executado e devolve o token no formato de cadeia de caracteres.

```cpp
#include "auth.h"
#include "utils.h"

#include <fstream>
#include <functional>
#include <memory>
#include <string>

using std::string;
using std::runtime_error;

namespace sample {
    namespace auth {

    string AcquireToken() { //ignore in this sample
    }

    //This function implements token acquisition in the application by calling an external Python script.
    //The Python script requires username, password, clientId, resource, and authority.
    //Username, Password, and ClientId are provided by the user/developer
    //Resource and Authority are provided as part of the OAuth2Challenge object that is passed in by the SDK to the AuthDelegate.
    string AcquireToken(
        const string& userName,
        const string& password,
        const string& clientId,
        const string& resource,
        const string& authority) {

    string cmd = "python";
    if (sample::FileExists("auth.py"))
        cmd += " auth.py -u ";

    else
        throw runtime_error("Unable to find auth script.");

    cmd += userName;
    cmd += " -p ";
    cmd += password;
    cmd += " -a ";
    cmd += authority;
    cmd += " -r ";
    cmd += resource;
    cmd += " -c ";
    // Replace <application-id> with the Application ID provided during your Azure AD application registration.
    cmd += (!clientId.empty() ? clientId : "<application-id>");

    string result = sample::Execute(cmd.c_str());
    if (result.empty())
        throw runtime_error("Failed to acquire token. Ensure Python is installed correctly.");

    return result;
    }
    }
}

```

## <a name="python-script"></a>Python Script

Este script adquire os tokens de autenticação diretamente através de um pedido de http simples. Isso é incluído apenas como um meio para adquirir os tokens de autenticação para utilização por aplicações de exemplo e não se destina a ser utilizado no código de produção. O script funciona apenas em inquilinos que suportam a autenticação http nome de utilizador/palavra-passe antigo sem formatação. MFA ou a autenticação baseada em certificado irá falhar.

```python
import getopt
import sys
import json
import urllib
import urllib2
import re

def printUsage():
  print('auth.py -u <username> -p <password> -a <authority> -r <resource> -c <clientId>')

def main(argv):
  try:
    options, args = getopt.getopt(argv, 'hu:p:a:r:c:')
  except getopt.GetoptError:
    printUsage()
    sys.exit(-1)

  username = ''
  password = ''
  authority = ''
  resource = ''
  clientId = ''

  for option, arg in options:
    if option == '-h':
      printUsage()
      sys.exit()
    elif option == '-u':
      username = arg
    elif option == '-p':
      password = arg
    elif option == '-a':
      authority = arg
    elif option == '-r':
      resource = arg
    elif option == '-c':
      clientId = arg

  if username == '' or password == '' or authority == '' or resource == '' or clientId == '':
    printUsage()
    sys.exit(-1)

  # Find everything after the last '/' and replace it with 'token'
  if not authority.endswith('token'):
    regex = re.compile('^(.*[\/])')
    match = regex.match(authority)
    authority = match.group()
    authority = authority + 'token'

  # Build REST call
  headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': 'application/json'
  }

  params = {
    'resource': resource,
    'client_id': clientId,
    'grant_type': 'password',
    'username': username,
    'password': password
  }

  req = urllib2.Request(
    url = authority,
    headers = headers,
    data = urllib.urlencode(params))

  f = urllib2.urlopen(req)
  response = f.read()
  f.close()
  sys.stdout.write(json.loads(response)['access_token'])

if __name__ == '__main__':
  main(sys.argv[1:])
```

## <a name="update-acquireoauth2token"></a>Atualizar AcquireOAuth2Token

Por fim, atualize o `AcquireOAuth2Token` funcionar `AuthDelegateImpl` para chamar o sobrecarregado `AcquireToken` função. Os recursos e a autoridade de URLs são obtidos lendo `challenge.GetResource()` e `challenge.GetAuthority()`. O `OAuth2Challenge` é passado para o delegado de autenticação quando o motor é adicionado. Esse trabalho é feito com o SDK e não requer nenhum trabalho adicional por parte do desenvolvedor. 

```cpp
bool AuthDelegateImpl::AcquireOAuth2Token(
    const mip::Identity& /*identity*/,
    const OAuth2Challenge& challenge,
    OAuth2Token& token) {

    //call our AcquireToken function, passing in username, password, clientId, and getting the resource/authority from the OAuth2Challenge object
    string accessToken = sample::auth::AcquireToken(mUserName, mPassword, mClientId, challenge.GetResource(), challenge.GetAuthority());
    token.SetAccessToken(accessToken);
    return true;
}
```

Quando o `engine` é adicionado, o SDK chamará o "AcquireOAuth2Token função, passando o desafio, executar o script de Python, receber um token, em seguida, apresentar o token para o serviço.


