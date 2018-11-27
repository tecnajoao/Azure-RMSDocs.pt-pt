---
title: Conceitos - usando o SDK do Microsoft Information Protection para gerar eventos de auditoria
description: Este artigo ajuda-o a compreender como utilizar o SDK do Microsoft Information Protection para computação.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: tommos
ms.openlocfilehash: 1cecbcc88434995c9807e1060dcf6296e33d2689
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304185"
---
# <a name="compute-an-action"></a>Uma ação de computação

Conforme detalhado anteriormente, as funções principais da API de política são:
- listar etiquetas disponíveis
- devolver um conjunto de ações que devem ser realizadas, com base no estado atual e pretendido

A última etapa do processo é fornecer um identificador de etiqueta e, opcionalmente, metadados sobre a etiqueta existente para o `ComputeActions()` função.

Código de exemplo para este artigo pode ser encontrado no GitHub.

* [mipsdk-policyapi-cpp-exemplo-básico](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic)

## <a name="compute-an-action-for-a-new-label"></a>Uma ação de computação para uma nova etiqueta

Computação a `mip::Actions` para uma nova etiqueta, pode ser obtido utilizando o `ExecutionStateImpl` definidos na [ExecutionState](concept-handler-policy-executionstate-cpp.md).

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c"; 
sample::policy::ExecutionStateOptions options;

// Set desired newLabelId in ExecutionStateOptions.
options.newLabelId = newLabelId;

// Initialize ExecutionStateImpl with options, create handler, call ComputeActions.
std::unique_ptr<ExecutionStateImpl> state(new ExecutionStateImpl(options));
auto handler = mEngine->CreatePolicyHandler(false); // Don't generate audit event.
auto actions = handler->ComputeActions(*state);
```

Escrever apenas o `mip::MetadataActions` devolvida como parte da `actions` apresenta:

```cpp
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled : true
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate : 2018-10-23T20:39:06-0800
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method : Standard
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name : Contoso FTEs (C)
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId : 94f6984e-8d31-4794-bdeb-3ac89ad2b660
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId : 2266fbe8-a0d9-44e8-bad8-00008f2a0915
Add: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits : 3
```

O `PolicyHandler` computa as ações e retorna um `std::vector` de `mip::Action`. Cabe-lhe para o desenvolvedor de aplicativos para aplicar esses metadados para o ficheiro ou a dados.

> [!NOTE]
> O exemplo acima apresenta apenas o `mip::MetadataAction` saída. Para obter um exemplo de exibição de tipos de ações adicionais, reveja os pacotes de exemplo com o [download de política API](https://aka.ms/mipsdkbins).

## <a name="compute-actions-with-an-existing-label"></a>Ações com uma etiqueta existente de computação

Ao utilizar a API de política, cabe à aplicação para ler os metadados do conteúdo. Estes metadados é fornecido para a API como parte do `mip::ExecutionState`. `ComputeActions()` pode processar operações mais complexas do que a aplicação de uma nova etiqueta a um documento sem etiqueta. O exemplo a seguir mostra a desatualização de uma etiqueta a partir de uma etiqueta mais confidencial, para uma etiqueta menos confidencial. Este processo é simulado por uma cadeia de caracteres separados por vírgulas dos metadados de leitura e fornecendo à API por meio de `mip::ExecutionState`.

> [!NOTE]
> O exemplo usa uma função de utilitário chamada `SplitString()`. Pode encontrar um exemplo [aqui](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic/blob/master/mipsdk-policyapi-cpp-sample-basic/utils.cpp)

```cpp
// Replace with valid label ID.
string newLabelId = "d7b93a40-4df3-47e4-b2fd-7862fc6b095c";

// Comma and Pipe Delimited Metadata.
string metadata = "MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled|true,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate|2018-10-23T21:53:31-0800,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method|Standard,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name|Contoso FTEs (C),MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId|94f6984e-8d31-4794-bdeb-3ac89ad2b660,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId|b56491d9-155f-40ff-866f-0000acd85c31,MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits|7";

// Create ExecutionStateOptions and set newLabelId.
sample::policy::ExecutionStateOptions options;
options.newLabelId = newLabelId;

// Split metadata string by commas, store in vector.
vector<string> metadataPairs = sample::utils::SplitString(metadata, ','); 

// Iterate through each string, splitting by the pipe.
// Add each key/value pair to ExecutionStateOptions metadata.
for (const string& metadataPair : metadataPairs) {
    vector<string> keyValue = sample::utils::SplitString(metadataPair, '|');
    options.metadata[keyValue[0]] = keyValue[1];
}

// Initialize ExecutionStateImpl with options, create handler, call ComputeActions
std::unique_ptr<ExecutionStateImpl> state(new ExecutionStateImpl(options));
auto handler = mEngine->CreatePolicyHandler(false); // Don't generate audit event.
auto actions = handler->ComputeActions(*state);
```

O exemplo acima poderá resultar em várias ações. Estas ações dependem as etiquetas fornecidas como entrada e a configuração de etiqueta. No mínimo, o resultado será uma única `mip::MetadataAction` que contém os dados para remover, via `GetMetadataToRemove()` e os dados para adicionar `GetMetadataToAdd()`.

```
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Enabled : true
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_SetDate : 2018-10-23T23:59:41-0800
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Method : Standard
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_Name : General
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_SiteId : 94f6984e-8d31-4794-bdeb-3ac89ad2b660
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_ActionId : 447a996b-28ea-482c-b0b5-000075bd4bb3
Add: MSIP_Label_d48d0e60-c766-40d6-96d3-53b2857fe775_ContentBits : 7
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Name
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Enabled
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SiteId
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_SetDate
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_Method
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ContentBits
Remove: MSIP_Label_d7b93a40-4df3-47e4-b2fd-7862fc6b095c_ActionId
```

## <a name="next-steps"></a>Passos Seguintes

- Saiba como [transmitir eventos de auditoria para análise de proteção de informações do Azure](concept-handler-policy-auditing-cpp.md)
- Transferir o [política amostras de API do GitHub e experimente a API de política](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)