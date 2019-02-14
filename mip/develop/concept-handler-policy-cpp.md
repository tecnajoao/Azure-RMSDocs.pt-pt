---
title: Conceitos - manipuladores de política no SDK do MIP.
description: Este artigo ajuda-o a compreender como os manipuladores de API de política são criadas e utilizadas para chamar operações.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 11/16/2018
ms.author: tommos
ms.openlocfilehash: cc35475086de76b869428c62cfc35e73fc3060db
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56258781"
---
# <a name="microsoft-information-protection-sdk---policy-handler-concepts"></a>SDK - conceitos de manipulador de política do Microsoft Information Protection

Na API de política, `mip::PolicyHandler` expõe operações utilizadas para ações de política de computação e submeter eventos de auditoria.

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

A primeira etapa necessária na obtenção de ações de política, é criar um `PolicyHandler` objeto. Essa classe implementa a funcionalidade necessária para obter a lista de ações, que terá de ter uma etiqueta específica. Ele também implementa a função para acionar um evento de auditoria.

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

## <a name="next-steps"></a>Próximos Passos

Agora que aprendeu sobre a criação de um manipulador de política:

- Saiba como [criar uma classe de estado de execução](concept-handler-policy-executionstate-cpp.md), que é utilizado para determinar as ações de computação.
- Transferir o [política amostras de API do GitHub e experimente a API de política](https://azure.microsoft.com/resources/samples/?sort=0&term=mipsdk+policyapi)
