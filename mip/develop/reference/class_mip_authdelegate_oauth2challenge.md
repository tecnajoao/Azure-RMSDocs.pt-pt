---
title: classe mip::AuthDelegate::OAuth2Challenge
description: Documenta a classe mip::authdelegate da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 86834f0236319613df4a9ef3ab64c1ec7dc9b20e
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652358"
---
# <a name="class-mipauthdelegateoauth2challenge"></a>classe mip::AuthDelegate::OAuth2Challenge 
uma classe que contém todas as informações necessárias do aplicativo de chamada para gerar um token oauth2.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OAuth2Challenge pública (Std:: String const e autoridade, Std:: String const & recursos, Std:: String const e escopo)  |  Construir uma nova [OAuth2Challenge](class_mip_authdelegate_oauth2challenge.md) objeto.
public const std::string& GetAuthority() const  |  Obter a cadeia de autoridade.
public const std::string& GetResource() const  |  Obter a cadeia de recurso.
public const std::string& GetScope() const  |  Obter a cadeia de âmbito.
  
## <a name="members"></a>Membros
  
### <a name="oauth2challenge-function"></a>Função de OAuth2Challenge
Construir uma nova [OAuth2Challenge](class_mip_authdelegate_oauth2challenge.md) objeto.

Parâmetros:  
* **autoridade**: a autoridade tem de ser gerada no token. 


* **recurso**: o recurso o token está definido como. 


* **âmbito**: o âmbito do token está definido como.


  
### <a name="getauthority-function"></a>Função de GetAuthority
Obter a cadeia de autoridade.

  
**Devolve**: A cadeia de autoridade.
  
### <a name="getresource-function"></a>Função de GetResource
Obter a cadeia de recurso.

  
**Devolve**: A cadeia de recurso.
  
### <a name="getscope-function"></a>Função de GetScope
Obter a cadeia de âmbito.

  
**Devolve**: A cadeia de âmbito.