---
title: classe mip::AuthDelegate
description: Documenta a classe mip::authdelegate da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: bcc38bf4b55ca99cf926138279223a4140f7bbf4
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330615"
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

