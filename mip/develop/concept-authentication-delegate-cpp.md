---
title: Conceitos - implementação de delegado de autenticação (C++)
description: Este artigo ajuda-o a compreender como implementar um delegado de autenticação em C++.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f80eb1f7ade5e024bd6d7d68775624b51f3f1809
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223913"
---
# <a name="microsoft-information-protection-sdk---implementing-an-authentication-delegate-c"></a>SDK - implementando um delegado de autenticação (C++) do Microsoft Information Protection

O SDK de MIP implementar um delegado de autenticação para lidar com os desafios de autenticação e a responder com um token. Não em si implementa aquisição do token. O processo de aquisição do token é cargo do desenvolvedor e é feito ao expandir a `mip::AuthDelegate` classe, especificamente o `AcquireOAuth2Token` função de membro.

## <a name="building-authdelegateimpl"></a>Criando AuthDelegateImpl

Para estender a classe base `mip::AuthDelegate`, criamos uma nova classe chamada `sample::auth::AuthDelegateImpl`. Essa classe implementa o `AcquireOAuth2Token` funcionalidade e configura o construtor para tirar nos nossos parâmetros de autenticação.

### <a name="authdelegateimplh"></a>auth_delegate_impl.h

Neste exemplo, o construtor padrão aceita apenas o nome de utilizador, palavra-passe e o aplicativo [ID da aplicação](/azure/active-directory/develop/developer-glossary#application-id-client-id). Estes serão armazenados nas variáveis privadas `mUserName`, `mPassword`, e `mClientId`.

É importante ter em conta essas informações como o fornecedor de identidade ou o URI do recurso não são necessários para implementar, pelo menos não no `AuthDelegateImpl` construtor. Que informações são transmitidas como parte da `AcquireOAuth2Token` no `OAuth2Challenge` objeto. Em vez disso, vamos passar esses detalhes para o `AcquireToken` chamar `AcquireOAuth2Token`.

```cpp
//auth_delegate_impl.h
#include <string.h>
#include "mip/common_types.h"

namespace sample {
namespace auth {
class AuthDelegateImpl final : public mip::AuthDelegate { //extend mip::AuthDelegate base class
public:
  AuthDelegateImpl() = delete;

  //constructor accepts username, password, and clientId, all plain strings.
  AuthDelegateImpl(
    const std::string& userName,
    const std::string& password,
    const std::string& clientId
  );

  bool AcquireOAuth2Token(const mip::Identity& identity, const OAuth2Challenge& challenge, OAuth2Token& token) override;

private:
  std::string mUserName;
  std::string mPassword;
  std::string mClientId;
};

}
}
```

### <a name="authdelegateimplcpp"></a>auth_delegate_impl.cpp

`AcquireOAuth2Token` é onde será efetuada a chamada para o fornecedor de OAuth2. No exemplo, abaixo daí são duas chamadas para `AcquireToken()`. Na prática, seria feita apenas uma chamada. Estas implementações serão abordadas nas secções fornecidas ao abrigo do [próximas etapas](#next-steps)

```cpp
//auth_delegate_impl.cpp
#include "auth_delegate_impl.h"
#include <stdexcept>
#include "auth.h" //contains the auth class used later for token acquisition

using std::runtime_error;
using std::string;

namespace sample {
namespace auth {

AuthDelegateImpl::AuthDelegateImpl(
    const string& userName,
    const string& password,
    const string& clientId)
    : mUserName(userName),
    mPassword(password),
    mClientId(clientId) {
}

//Here we could simply add our token acquisition code to AcquireOAuth2Token
//Instead, that code is implemented in auth.h/cpp to demonstrate calling an external library
bool AuthDelegateImpl::AcquireOAuth2Token(
    const mip::Identity& /*identity*/, //This won't be used
    const OAuth2Challenge& challenge,
    const OAuth2Token& token) {

      //sample::auth::AcquireToken is the code where the token acquisition routine is implemented.
      //AcquireToken() returns a string that contains the OAuth2 token.

      //Simple example for getting hard coded token. Comment out if not used.
      string accessToken = sample::auth::AcquireToken();

      //Practical example for calling external OAuth2 library with provided authentication details.
      string accessToken = sample::auth::AcquireToken(mUserName, mPassword, mClientId, challenge.GetAuthority(), challenge.GetResource());  

      //set the passed in OAuth2Token value to the access token acquired by our provider
      token.SetAccessToken(accessToken);
      return true;
    }
}
}
```

## <a name="next-steps"></a>Passos Seguintes

Para concluir a implementação de autenticação, é necessário criar o código por trás do `AcquireToken()` função. Os exemplos abaixo discutem algumas formas de adquirir o token.

- [Exemplo de aquisição do token simples/PowerShell](concept-authentication-acquire-token-ps.md)
- [Exemplo de aquisição do token de Python](concept-authentication-acquire-token-py.md)
