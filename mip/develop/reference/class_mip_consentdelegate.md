---
title: classe mip::ConsentDelegate
description: Documenta a classe mip::consentdelegate da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 3eed60a06d2dda22f3ed037b1f30e3c5a0f2c699
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651865"
---
# <a name="class-mipconsentdelegate"></a>classe mip::ConsentDelegate 
Delegado, consentimento operações relacionadas com.
Este delegado é implementado por uma aplicação de cliente para saber quando uma notificação de pedido de consentimento deverá ser apresentada ao utilizador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public Consent GetUserConsent(const std::string& url)  |  Chamado quando o SDK necessita de consentimento do utilizador para ligar a um ponto de extremidade de serviço.
  
## <a name="members"></a>Membros
  
### <a name="getuserconsent-function"></a>Função de GetUserConsent
Chamado quando o SDK necessita de consentimento do utilizador para ligar a um ponto de extremidade de serviço.

Parâmetros:  
* **url**: O URL para o qual o SDK necessita de consentimento do utilizador



  
**Devolve**: Uma enumeração de consentimento com a decisão do usuário.
Quando o SDK pede consentimento do utilizador com este método, o aplicativo cliente deve apresentar o URL para o usuário. Aplicações de cliente devem fornecer alguns meios de obtenção de consentimento do utilizador e voltar a enumeração de consentimento apropriada que corresponde à decisão do usuário.