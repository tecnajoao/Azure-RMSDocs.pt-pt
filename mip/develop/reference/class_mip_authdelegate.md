---
title: classe mip::AuthDelegate
description: Documenta a classe mip::authdelegate da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: cf6ea43b36518f2eec74b9ed0f8682466aa6b64d
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56258016"
---
# <a name="class-mipauthdelegate"></a>classe mip::AuthDelegate 
Delegado para autenticação operações relacionadas com.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
bool pública AcquireOAuth2Token (const mip::Identity, identidade, const OAuth2Challenge & desafio, OAuth2Token & token)  |  Este método é chamado quando um token de autenticação é necessário para o motor de política com a identidade de determinado e o desafio de determinado. O cliente deve devolver se a aquisição de token foi concluída com êxito. Se tiver êxito, ele deve inicializar o objeto de token especificado.
  
## <a name="members"></a>Membros
  
### <a name="acquireoauth2token-function"></a>Função de AcquireOAuth2Token
Este método é chamado quando um token de autenticação é necessário para o motor de política com a identidade de determinado e o desafio de determinado. O cliente deve devolver se a aquisição de token foi concluída com êxito. Se tiver êxito, ele deve inicializar o objeto de token especificado.

Parâmetros:  
* **identity**: 


* **challenge**: 


* **token**:

