---
title: Conceitos - a auditoria no ficheiro SDK de proteção de informações da Microsoft API
description: Este artigo ajuda-o a compreender como utilizar o SDK do Microsoft Information Protection para submeter a API de ficheiros a auditoria de eventos para análise de proteção de informações do Azure.
services: information-protection
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: tommos
ms.openlocfilehash: bd04d9aa2edd6be01ae9e912d7ddbf936d6dd4df
ms.sourcegitcommit: 05fdaf43f74013eecb5886b95b09dd5e00670753
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297905"
---
# <a name="auditing-in-the-mip-sdk-file-api"></a>A API de ficheiros do SDK de MIP de auditoria

O portal de administração do Azure Information Protection fornece acesso a relatórios de administrador. Estes relatórios fornecem visibilidade para os utilizadores que as etiquetas são aplicar, manualmente ou automaticamente, em todas as aplicações de quaisquer serviços que integraram o SDK de MIP. Parceiros de desenvolvimento com o SDK facilmente podem ativar esta funcionalidade para que as informações a partir das suas aplicações irão descobrir nos relatórios do cliente.

## <a name="event-types"></a>Tipos de eventos

Existem três tipos de eventos que podem ser submetidos através do SDK para análise de proteção de informações do Azure. **Eventos de heartbeat**, **eventos de deteção**, e **eventos de alteração**

### <a name="heartbeat-events"></a>Eventos de heartbeat

Eventos de heartbeat são gerados automaticamente para qualquer aplicativo que integrou a API de ficheiros. Eventos de heartbeat incluem:

* TenantId
* Hora de geração
* Nome Principal de Utilizador
* Nome da máquina em que a auditoria foi gerada
* Nome do processo
* Platform
* ID da aplicação - corresponde com o Azure AD ID da aplicação.

Esses eventos são úteis na deteção de aplicações em toda a empresa que estão a utilizar o SDK do Microsoft Information Protection.

### <a name="discovery-events"></a>Eventos de deteção

Eventos de deteção fornecem informações sobre a informação etiquetada ler ou consumida pela API de ficheiros. Estes eventos são úteis de superfície os dispositivos, localização e utilizadores que acedem a informações em toda a organização.

Esses eventos são submetidos para o Azure Information Protection Analytics definindo a `AuditDiscoveryEnabled` parâmetro como true quando criar um novo `mip::FileHandler`. Além disso, é fornecido um identificador de conteúdo que identifica o ficheiro em algum formato legível por humanos. É recomendado a utilizar o caminho do ficheiro para este identificador.

O exemplo abaixo cria um novo `mip::FileHandler` com deteção de auditoria ativada. O `CreateFileHandler()` método é chamado na `mip::FileEngine` e `AuditDiscoveryEnabled` definido como true. Uma vez o `FileHanlder` lê o rótulo, uma auditoria de deteção é gerada.

```cpp
// Create FileHandler with discovery enabled
auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
auto handlerFuture = handlerPromise->get_future();
fileEngine->CreateFileHandlerAsync(filePath, contentId, mip::ContentState::REST, true /*AuditDiscoveryEnabled*/, make_shared<FileHandlerObserver>(), createFileHandlerPromise);
auto handler = handlerFuture.get();

// Read label. This generates the discovery audit.
auto label = handler->GetLabel();
```

### <a name="change-events"></a>Eventos de alteração

Eventos de alteração de fornecem informações sobre o ficheiro, a etiqueta que foi aplicada ou alterada e qualquer justificativas fornecidas pelo usuário. Eventos de alteração são gerados chamando `NotifyCommitSuccessful()` sobre o `mip::FileHandler`, após uma alteração ter sido confirmada com êxito um ficheiro.

```cpp
// Create labeling options, set label
string contentId = "C:\users\myuser\Documents\MyPlan.docx";
mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED, mip::ActionSource::MANUAL);
handler->SetLabel(labelId, labelingOptions);
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();

// CommitAsync() returns a bool. If the change was successful, call NotifyCommitSuccessful().
fileHandler->CommitAsync(outputFile, commitPromise);
if(commitFuture.get()) {

    // Submit audit event.
    handler->NotifyCommitSuccessful(contentId);
}
```

## <a name="audit-dashboard"></a>Dashboard de auditoria

Eventos enviados para o pipeline de auditoria do Azure Information Protection irão descobrir nos relatórios em https://portal.azure.com. Análise de proteção de informações do Azure está em pré-visualização pública e funcionalidades estão sujeitos a alterações.

## <a name="next-steps"></a>Passos Seguintes

Para obter mais detalhes sobre a experiência de auditoria no Azure Information Protection, veja a [pré-visualizar o blogue de anúncio na Comunidade tecnológica](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854).
