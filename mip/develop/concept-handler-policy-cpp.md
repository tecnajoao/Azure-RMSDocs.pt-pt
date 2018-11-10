---
title: Conceitos - manipuladores de política no SDK do MIP.
description: Este artigo ajuda-o a compreender como os manipuladores de API de política são criadas e utilizadas para chamar operações.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: c1e150de6096e070f46232e77a4749081fe0bb9f
ms.sourcegitcommit: 05fdaf43f74013eecb5886b95b09dd5e00670753
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297919"
---
# <a name="microsoft-information-protection-sdk---policy-handler-concepts"></a>SDK - conceitos de manipulador de política do Microsoft Information Protection

Na API de política, `mip::PolicyHandler` expõe as várias operações que podem ser utilizadas para ações de política de computação e submeter eventos de auditoria.

## <a name="policy-handler-functions"></a>Funções do manipulador de política

`mip::PolicyHandler` expõe métodos para ler, escrever e remover etiquetas e informações sobre a proteção. Para obter a lista completa, consulte a [referência da API](reference/class_mip_PolicyHandler.md).

Neste artigo, serão abordados os seguintes métodos:

- `ComputeActions`
- `NotifyCommittedActions`

## <a name="requirements"></a>Requisitos

Criar um `PolicyHandler` requer:

- A `PolicyProfile`
- A `PolicyEngine` adicionado para o `PolicyProfile`
- Uma classe que herda `mip::PolicyHandler::Observer`

## <a name="create-a-policy-handler"></a>Criar um manipulador de política

A primeira etapa necessária na obtenção de ações de política, é criar um `PolicyHandler` objeto. Essa classe implementa a funcionalidade necessária para obter a lista de ações, que terá de ter uma etiqueta específica e a função para acionar um evento de auditoria.

Criar a `PolicyHandler` é tão fácil quanto chamar o `PolicyEngine`do `CreatePolicyHandlerAsync` funcionar usando o padrão de promessa/futuro.

`CreatePolicyHandlerAsync` aceita um único parâmetro: **isAuditDiscoveryEnabled**. Definir este valor como **true** se o aplicativo deve demonstrar eventos de heartbeat no log de auditoria.

> [!NOTE]
> O `mip::PolicyHandler::Observer` classe tem de ser implementada numa classe derivada como `CreatePolicyHandler` requer o `Observer` objeto. 

```cpp
auto createPolicyHandlerPromise = std::make_shared<std::promise<std::shared_ptr<mip::PolicyHandler>>>();
auto createPolicyHandlerFuture = createPolicyHandlerPromise->get_future();
PolicyEngine->CreatePolicyHandlerAsync(true);
auto handler = createPolicyHandlerFuture.get();
```

Depois de criar com êxito o `PolicyHandler` de objeto, ações podem ser computadas e auditar eventos de submetido.

# <a name="compute-an-action"></a>Uma ação de computação

Conforme detalhado anteriormente, as funções principais da API de política são:

- Liste as etiquetas disponíveis.
- Devolva o conjunto específico de ações que devem ser realizadas, com base no estado atual e pretendido. 

A última etapa do processo é fornecer um identificador de etiqueta e, opcionalmente, metadados sobre a etiqueta existente para o `ComputeActions()` função.

Código de exemplo para este artigo pode ser encontrado no GitHub.

* [mipsdk-policyapi-cpp-exemplo-básico](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-basic)

## <a name="compute-an-action-for-a-new-label"></a>Uma ação de computação para uma nova etiqueta

Computação a `mip::Actions` para uma nova etiqueta pode ser obtida utilizando o `ExecutionStateImpl` definido no [ExecutionState](concept-auditing-policy-executionstate-cpp.md) secção.

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

Ao utilizar a API de política, cabe à aplicação para ler os metadados do conteúdo. Estes metadados é fornecido para a API como parte do `mip::ExecutionState`. `ComputeActions()` pode processar operações mais complexas do que a aplicação de uma nova etiqueta a um documento sem etiqueta. O exemplo a seguir mostra a desatualização de uma etiqueta a partir de uma etiqueta mais confidencial para uma etiqueta menos confidencial, onde uma etiqueta já existe. Este processo é simulado por ler uma cadeia de caracteres separados por vírgulas de metadados e o fornecimento para a API via `mip::ExecutionState`.

> [!NOTE]
> O exemplo usa uma função de utilitário chamada `SplitString()`. Pode encontrar um exemplo [aqui](https://github.com/Azure-Samples/mipsdk-policyapi-cpp-sample-advanced/blob/master/mipsdk-policyapi-cpp-sample-advanced/utils.cpp)

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

* Em seguida, transferir o [política amostras de API do GitHub e experimente a API de política](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
* Saiba mais sobre como [transmitir eventos de auditoria para a análise de proteção de informações do Azure](concept-auditing-policy-cpp.md)