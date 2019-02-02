---
title: classe mip::AuthDelegate
description: Documenta a classe mip::authdelegate da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: b6278d605dfbb9a9c4cf0cf1282a159c456c5561
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652001"
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

