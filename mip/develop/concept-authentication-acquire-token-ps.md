---
title: Conceitos - utilizar o PowerShell para adquirir um token de acesso.
description: Este artigo ajuda-o a compreender como utilizar o PowerShell para adquirir um token de acesso de OAuth2. Isso é necessária para a implementação do delegado de autenticação.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 02/04/2019
ms.author: bryanla
ms.openlocfilehash: 85c06979a5010a17b60751ccd8a09529be2c362d
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252899"
---
# <a name="acquire-an-access-token-powershell"></a>Adquirir um token de acesso (PowerShell)

O exemplo mostrado demonstra como chamar um script do PowerShell externo para obter um token OAuth2. Um token de acesso de OAuth2 válido é necessária para a implementação do delegado de autenticação.

## <a name="prerequisites"></a>Pré-requisitos

- Concluída [instalação do SDK (MIP) e configuração](setup-configure-mip.md). Entre outras tarefas, terá de registar a sua aplicação de cliente no seu inquilino do Azure Active Directory (Azure AD). O Azure AD irá fornecer um ID de aplicação, também conhecido como ID de cliente, que é utilizada na sua lógica de aquisição do token.

Esse código não foi concebido para utilização em produção. Só podem ser utilizada para desenvolvimento e conceitos de autenticação de compreensão. 

## <a name="sampleauthacquiretoken"></a>sample::auth::AcquireToken()

### <a name="authh"></a>auth.h

Vamos criar uma única função chamada AcquireToken. Uma vez que o valor de retorno será codificada para este tutorial, vamos aceitar sem parâmetros e retornar uma cadeia de caracteres (o token).

```cpp
//auth.h
#include <string>

namespace sample {
  namespace auth {
    std::string AcquireToken();
  }
}
```

### <a name="authcpp"></a>auth.cpp

Nosso arquivo de origem devolve um valor de token que irá ser inserida num passo posterior.

```cpp
//auth.cpp
#include <string>
#include "auth.h"

namespace sample {
  namespace auth {
    string AcquireToken() {
      std::string mToken = "your token here";
      return mToken;
    }
  }
}
```

## <a name="mint-a-token"></a>E um token de menta

Por fim, mint um token para colocar na variável mToken. O exemplo a seguir mostra um script do PowerShell que pode ser utilizado para obter rapidamente o token OAuth2 através do ADAL e o PowerShell no Windows. Este token é concedida para o Centro de conformidade e de segurança do Office 365 ponto final apenas. Conseqüentemente, ações de proteção irão falhar, a menos que o URL de recurso é atualizado. 

### <a name="install-adalpshttpswwwpowershellgallerycompackagesadalps31942-from-ps-gallery"></a>Instale [ADAL.PS](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2) da Galeria de PS

Pode ignorar este passo se concluiu-lo anteriormente na [instalação do SDK (MIP) e configuração](setup-configure-mip.md).

```PowerShell
Install-Module -Name ADAL.PS
```

### <a name="use-get-adaltoken-to-obtain-the-access-token"></a>Utilize Get-ADALToken para obter o Token de acesso

```PowerShell
#Install the ADAL.PS package if it's not installed.
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps }

$authority = "https://login.windows.net/common/oauth2/authorize" 
#this is the security and compliance center endpoint
$resourceUrl = "https://syncservice.o365syncservice.com/"
#replace <application-id> and <redirect-uri>, with the Redirect URI and Application ID from your Azure AD application registration.
$clientId = "<application-id>"
$redirectUri = "<redirect-uri>"

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip
```

Copie o token da área de transferência para auth.cpp como o valor de `string mToken`, substituindo "seu token aqui" acima. Executar novamente o script pode ser necessário, dependendo do quanto as seguintes etapas guiarão.


