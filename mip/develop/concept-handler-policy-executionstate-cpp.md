---
title: Conceitos - implementando ExecutionState no SDK do Microsoft Information Protection
description: Este artigo ajuda-o a compreender como utilizar o ExecutionState no SDK do Microsoft Information Protection para ações de computação e forneça os detalhes para um registo de auditoria.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: 71cc6f08e130fe4a97604924643d13fd341a5625
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304168"
---
# <a name="implement-executionstate"></a>Implementar ExecutionState

Passando informações para o SDK de MIP para computar uma ação que deve ser considerada, com base no estado atual e assim o desejar Estado, é implementada através de `mip::ExecutionState` classe. Como outras classes no SDK, o `ExecutionState` é uma classe abstrata e tem de ser implementado pelo programador.

> Para obter um exemplo completo de um `ExecutionState` implementação, reveja a origem de exemplo seguinte:
>
> * [execution_state_impl.h](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.h)
> * [execution_state_impl.cpp](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.cpp)

## <a name="mipexecutionstate-members"></a>Mip::ExecutionState membros

`ExecutionState` expõe os seguintes membros virtuais. Cada fornece algum contexto para o motor de política para devolver informações em que ações deve ser tomada pelo aplicativo. Além disso, estas informações podem ser utilizadas para fornecer informações de auditoria para a funcionalidade de relatórios do Azure Information Protection.


| Membro                                                                           | Devolve                                                                                                              |
|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `std::string GetNewLabelId()`                                                      | Devolve o ID de etiqueta a ser aplicado ao objeto.                                                                    |
| `mip::ContentState GetContentState()`                                              | Devolve o mip::ContentState do objeto.                                                                         |
| `std::pair<bool, std::string> IsDowngradeJustified()`                              | Devolve um std::pair expressar se a mudança para versão anterior é justificada e a justificação.                                 |
| `std::string GetContentIdentifier()`                                               | Devolve o identificador de conteúdo. Deve ser um identificador de legível por humanos, que indica a localização do objeto.   |
| `mip::ActionSource GetNewLabelActionSource()`                                      | Devolve o mip::ActionSource da etiqueta.                                                                          |
| `mip::AssignmentMethod GetNewLabelAssignmentMethod()`                              | Devolve o mip::AssignmentMethod da etiqueta                                                                        |
| `std::vector<std::pair<std::string, std::string>> GetNewLabelExtendedProperties()` | Devolve um Std:: vector de std::pairs de cadeias de caracteres que contém os metadados personalizados que serão aplicados ao documento. |
| `std::vector<std::pair<std::string, std::string>> GetContentMetadata()`            | Devolve um Std:: vector de std::pairs de cadeia de caracteres que contém os metadados de conteúdo atual.                               |
| `std::shared_ptr<mip::ProtectionDescriptor> GetProtectionDescriptor()`           | Retorna um ponteiro para um mip::ProtectionDescriptor                                                                     |
| `mip::ContentFormat GetContentFormat()`                                            | Devolve mip::ContentFormat                                                                                           |
| `mip::ActionType GetSupportedActions()`                                           | Devolve mip::ActionTypes para a etiqueta.                                                                              |

Cada um tem de ser substituído numa implementação de uma classe derivada de `mip::ExecutionState`. No aplicativo de exemplo ligado acima, este processo é realizado através da implementação de uma estrutura chamada `ExecutionStateOptions`e passando para o construtor da classe derivada.

Na [exemplo](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/execution_state_impl.h), uma estrutura chamada `ExecutionStateOptions` é definido como:

```cpp
struct ExecutionStateOptions {
    std::unordered_map<std::string, std::string> metadata;
    std::string newLabelId;
    std::string contentIdentifier;
    mip::ActionSource actionSource = mip::ActionSource::MANUAL;
    mip::ContentState contentState = mip::ContentState::REST;
    mip::AssignmentMethod assignmentMethod = mip::AssignmentMethod::STANDARD;
    bool isDowngradeJustified = false;
    std::string downgradeJustification;
    std::string templateId;
    mip::ContentFormat contentFormat = mip::ContentFormat::DEFAULT;
};
```

Cada propriedade é definida pelo aplicativo, em seguida, `ExecutionStateOptions` é passado para o construtor da classe derivada de `mip::ExecutionState`. Estas informações são utilizadas para determinar as ações de. Dados fornecidos no `mip::ExecutionState` também irão descobrir na análise de proteção de informações do Azure.

### <a name="next-steps"></a>Passos Seguintes

- Saiba como determinar [computação ações para uma etiqueta de nova ou existente](concept-handler-policy-computeactions-cpp.md), com base no estado atual e pretendido.
- Transferir o [política amostras de API do GitHub e experimente a API de política](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
