---
title: classe ConsentDelegate
description: Referência para a classe ConsentDelegate
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 841049b1e6b369eb2f6a34d9701ed34eca028af6
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446367"
---
# <a name="class-consentdelegate"></a>classe ConsentDelegate 
Delegado, consentimento operações relacionadas com.
Este delegado é implementado por uma aplicação de cliente para saber quando uma notificação de pedido de consentimento deverá ser apresentada ao utilizador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público GetUserConsent(const std::string& url) consentimento  |  Chamado quando o SDK necessita de consentimento do utilizador para ligar a um ponto de extremidade de serviço.
  
## <a name="members"></a>Membros
  
### <a name="consent"></a>Consentimento
Chamado quando o SDK necessita de consentimento do utilizador para ligar a um ponto de extremidade de serviço.

Parâmetros:  
* **URL**: O URL para o qual o SDK necessita de consentimento do utilizador



  
**Devolve**: consentimento de uma enumeração com a decisão do usuário.
Quando o SDK pede consentimento do utilizador com este método, o aplicativo cliente deve apresentar o URL para o usuário. Aplicações de cliente devem fornecer alguns meios de obtenção de consentimento do utilizador e voltar a enumeração de consentimento apropriada que corresponde à decisão do usuário.