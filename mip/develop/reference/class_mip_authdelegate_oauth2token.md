---
title: classe mip::AuthDelegate::OAuth2Token
description: Documenta a classe mip::authdelegate da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 7ce9e336edfeeee07725b30c4d76c3b3c2073bc6
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652052"
---
# <a name="class-mipauthdelegateoauth2token"></a>classe mip::AuthDelegate::OAuth2Token 
Uma classe de definir a forma como o SDK de MIP espera que o token oauth2 a serem passados de volta para o SDK.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OAuth2Token() pública  |  Construir uma nova [OAuth2Token](class_mip_authdelegate_oauth2token.md) objeto.
OAuth2Token pública (const Std:: String & accessToken)  |  Construir uma nova [OAuth2Token](class_mip_authdelegate_oauth2token.md) objeto a partir de um accessToken.
public const std::string& GetAccessToken() const  |  Obter a cadeia de token de acesso.
public void SetAccessToken(const std::string& accessToken)  |  Defina a cadeia de Token de acesso.
  
## <a name="members"></a>Membros
  
### <a name="oauth2token-function"></a>Função de OAuth2Token
Construir uma nova [OAuth2Token](class_mip_authdelegate_oauth2token.md) objeto.
  
### <a name="oauth2token-function"></a>Função de OAuth2Token
Construir uma nova [OAuth2Token](class_mip_authdelegate_oauth2token.md) objeto a partir de um accessToken.

Parâmetros:  
* **accessToken**: O token de acesso real passado para o SDK.


  
### <a name="getaccesstoken-function"></a>GetAccessToken função
Obter a cadeia de token de acesso.

  
**Devolve**: A cadeia de token de acesso.
  
### <a name="setaccesstoken-function"></a>Função de SetAccessToken
Defina a cadeia de Token de acesso.

Parâmetros:  
* **accessToken**: a cadeia de caracteres de token de acesso.

