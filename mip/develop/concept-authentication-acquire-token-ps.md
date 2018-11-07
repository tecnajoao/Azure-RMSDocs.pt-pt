---
title: Conceitos - utilizar o PowerShell para adquirir um token de acesso.
description: Este artigo ajuda-o a compreender como utilizar o PowerShell para adquirir um token de acesso de OAuth2. Isso é necessária para a implementação do delegado de autenticação.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a5ce346d044a9a56d37777e569582087026c9ce6
ms.sourcegitcommit: fa0be701b85b1fba5e75428714bb4525dd739a93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223891"
---
# <a name="acquire-an-access-token-powershell"></a>Adquirir um token de acesso (PowerShell)

Este exemplo demonstra como chamar um script do PowerShell externo para obter um token OAuth2. Isso é necessária para a implementação do delegado de autenticação.

Esse código não se destina a utilização de produção, mas pode ser utilizado para desenvolvimento e noções básicas sobre conceitos de autenticação. 

## <a name="sampleauthacquiretoken"></a>exemplo:: auth::AcquireToken()

### <a name="authh"></a>auth.h

Vamos criar uma única função chamada AcquireToken. Uma vez que o valor de retorno será difícil codificado para este tutorial, vamos aceitar sem parâmetros e simplesmente retornar uma cadeia de caracteres (o token).

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

Nosso arquivo de origem devolve um valor de token que serão difíceis codificado num passo posterior.

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

Por fim, mint um token para colocar na variável mToken. O exemplo a seguir mostra um script do PowerShell que pode ser utilizado para obter rapidamente o token OAuth2 através do ADAL e o PowerShell no Windows. Este token é concedida para o Centro de conformidade e de segurança do Office 365 ponto final apenas. Conseqüentemente, ações de proteção irão falhar, a menos que o URL de recurso é atualizado. É recomendado para avançar para o [passos seguintes](#next-steps) secção se desejar testar com a etiquetagem e proteção neste momento.

### <a name="install-adalpshttpswwwpowershellgallerycompackagesadalps31942-from-ps-gallery"></a>Instale [ADAL.PS](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2) da Galeria de PS

```PowerShell
Install-Module -Name ADAL.PS
```

### <a name="use-get-adaltoken-to-obtain-the-access-token"></a>Utilize Get-ADALToken para obter o Token de acesso

```PowerShell
#Install the ADAL.PS package if it's not installed.
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps }

$authority = "https://login.windows.net/common/oauth2/authorize" 
#this is the security and compliance center endpoint
$resourceUrl = "https://dataservice.o365filtering.com"
#clientId and redirectUri are from the RMS Sharing Application. 
#Once custom app registration is supported, a custom id and uri will be required. 
$clientId = "0edbblll-8773-44de-b87c-b8c6276d41eb"
$redirectUri = "com.microsoft.rms-sharing-for-win://authorize"

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip
```

Copie o token da área de transferência para auth.cpp como o valor de `string mToken`, substituindo "seu token aqui" acima. Executar novamente o script pode ser necessário, dependendo do quanto as seguintes etapas guiarão.


