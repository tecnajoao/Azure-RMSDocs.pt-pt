---
title: Conceitos - auditoria na política SDK do Microsoft Information Protection API
description: Este artigo ajuda-o a compreender como utilizar o SDK do Microsoft Information Protection para submeter a API de política de auditoria de eventos para análise de proteção de informações do Azure.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/07/2018
ms.author: tommos
ms.openlocfilehash: c660a5f58acd87ff9047a21fea26cc2732667493
ms.sourcegitcommit: 05fdaf43f74013eecb5886b95b09dd5e00670753
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297916"
---
# <a name="auditing-in-the-mip-sdk"></a>Auditoria no SDK do MIP

O portal de administração do Azure Information Protection fornece acesso a relatórios de administrador. Estes relatórios fornecem visibilidade sobre as etiquetas que os utilizadores aplicam, manual ou automaticamente, em todas as aplicações que integraram o SDK de MIP. Parceiros de desenvolvimento, aproveitando o SDK podem facilmente ativar esta funcionalidade, permitindo que informações a partir das suas aplicações à tona nos relatórios do cliente.

## <a name="event-types"></a>Tipos de eventos

Existem três tipos de eventos que podem ser submetidos através do SDK para análise de proteção de informações do Azure. **Eventos de heartbeat**, **eventos de deteção**, e **eventos de alteração**

### <a name="heartbeat-events"></a>Eventos de heartbeat

Eventos de heartbeat são gerados automaticamente para qualquer aplicativo que integrou a API de política. Eventos de heartbeat incluem:

* TenantId
* Hora de geração
* Nome Principal de Utilizador
* Nome da máquina em que a auditoria foi gerada
* Nome do processo
* Platform
* ID da aplicação - corresponde com o Azure AD ID da aplicação.

Esses eventos são úteis na deteção de aplicações em toda a empresa que estão a utilizar o SDK do Microsoft Information Protection.

### <a name="discovery-events"></a>Eventos de deteção

Eventos de deteção fornecem informações sobre etiquetadas as informações de leitura ou consumidas pela política de API. Estes eventos são úteis de superfície os dispositivos, localização e utilizadores que acedem a informações em toda a organização.

Eventos de deteção gerados na API de política ao definir um sinalizador booleano, ao criar o `mip::PolicyHandler` objeto por meio do `mip::PolicyEngine`. No exemplo abaixo, o valor para **isAuditDiscoveryEnabled** está definido como true. Quando `mip::ExecutionState` é passado para `ComputeActions()` ou `GetSensitivityLabel()` (com metadados informações e conteúdos de identificador existente), essas informações de deteção irão ser submetidas à análise de proteção de informações do Azure.

A auditoria de deteção é gerada quando o aplicativo chama `ComputeActions()` ou `GetSensitivityLabel()` e fornece `mip::ExecutionState`. Este evento é gerado apenas uma vez por processador.

Reveja o `mip::ExecutionState` documentação de conceitos para obter mais detalhes sobre o estado de execução.

```cpp
// Create PolicyHandler, passing in true for isAuditDiscoveryEnabled
auto handler = mEngine->CreatePolicyHandler(true);

// Returns vector of mip::Action and generates discovery event.
auto actions = handler->ComputeActions(*state);

//Or, get the label for a given state
auto label = handler->GetSensitivityLabel(*state);
```

Na prática, **isAuditDiscoveryEnabled** deve ser `true` durante `mip::PolicyHandler` construção, para permitir informações de acesso do ficheiro a ser aplicada à análise de proteção de informações do Azure.

## <a name="change-event"></a>Evento de alteração

Eventos de alteração de fornecem informações sobre o ficheiro, a etiqueta que foi aplicada ou alterada e qualquer justificativas fornecidas pelo usuário. Eventos de alteração são gerados chamando `NotifyCommittedActions()` sobre o `mip::PolicyHandler`. A chamada é feita após uma alteração ter sido com êxito empenhada num arquivo, passando o `mip::ExecutionState` que foi utilizada para calcular as ações.

> Se a aplicação não conseguir chamar essa função, não existem eventos serão encaminhado para análise de proteção de informações do Azure.

```cpp
handler->NotifyCommittedActions(*state);
```

## <a name="audit-dashboard"></a>Dashboard de auditoria

Eventos enviados para o pipeline de auditoria do Azure Information Protection irão descobrir nos relatórios em https://portal.azure.com. Análise de proteção de informações do Azure está em pré-visualização pública e funcionalidades estão sujeitos a alterações.

## <a name="next-steps"></a>Passos Seguintes

Consulte a [pré-visualizar o blogue de anúncio na Comunidade tecnológica](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854) para obter mais detalhes sobre a experiência de auditoria no Azure Information Protection.

