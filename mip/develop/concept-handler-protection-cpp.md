---
title: Conceitos - manipuladores de proteção no SDK do MIP.
description: Este artigo ajuda-o a compreender como os manipuladores de API de proteção são criados e usados para chamar operações.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: dd38b8e6c9deb45b4ce7df9ec3363ac8036a7ef4
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330190"
---
# <a name="microsoft-information-protection-sdk---protection-handler-concepts"></a>SDK - conceitos de manipulador de proteção do Microsoft Information Protection

Na API de proteção do SDK do MIP, o `mip::ProtectionHandler` expõe as funções para encriptar e desencriptar fluxos protegidos e buffers, realizar verificações de acesso, obter a licença de publicação e ao obter os atributos das informações protegidas. 

## <a name="requirements"></a>Requisitos

Criar um `ProtectionHandler` para trabalhar com um ficheiro específico, é necessário:

- A `ProtectionProfile`
- A `ProtectionEngine` adicionado para o `ProtectionProfile`
- Uma classe que herda `mip::ProtectionHandler::Observer`, semelhante ao padrão descrito [aqui]().
- A `mip::ProtectionDescriptor` ou licença de publicação

## <a name="create-a-protection-handler"></a>Criar um manipulador de proteção

`mip::ProtectionHandler` objeto seja construído, fornecendo um uma `ProtectionDescriptor` ou uma licença de publicação serializada para uma de duas `ProtectionEngine` funções. O descritor de proteção tem de ser gerado para a proteção de informações de texto sem formatação que já não tem uma licença de publicação. O **licença de publicação** será usado na desencriptação de conteúdo protegido por já ou quando proteger o conteúdo em que a licença já ter sido criada. Não é possível desencriptar o conteúdo protegido sem licença de publicação associada.

`mip::ProtectionEngine` expõe duas funções para a criação de um `ProtectionHandler`. Os parâmetros são os mesmos, com exceção do processador ou a licença de publicação como o primeiro parâmetro.

- `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync`
  - Requer um `ProtectionDescriptor` como o primeiro parâmetro.
- `mip::ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync`
  - Requer uma licença de publicação serializada, armazenada em `std::vector<unint8_t>` como o primeiro parâmetro.

### <a name="create-from-descriptor"></a>Criar a partir de descritor

Se proteger conteúdo que ainda não tenha sido protegido ou ao aplicar a nova proteção de conteúdo, que indica que foi desencriptado, um `mip::ProtectionDescriptor` tiver de ser criada. Depois de criada, é passado para `mip::ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync()` e o resultado é devolvido através da `mip::ProtectionHandler::Observer`.

```cpp
auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<ProtectionHandler>>>();
auto handlerFuture = handlerPromise->get_future();
auto observer = std::make_shared<ProtectionHandlerObserverImpl>();

//Refer to ProtectionDescriptor docs for details on creating the descriptor
auto descriptor = CreateProtectionDescriptor(); //Stub function

mEngine->CreateProtectionHandlerFromDescriptorAsync(
    descriptor,
    mip::ProtectionHandlerCreationOptions::None,
    observer,
    handlerPromise);

auto handler = handlerFuture.get();
```

Depois de criar com êxito o `ProtectionHandler` de objeto, operações de arquivo (get/set/delete/consolidação) podem ser executadas.

### <a name="create-from-publishing-license"></a>Criar a partir de licença de publicação

Este exemplo assume que a licença de publicação já foram lido de alguma fonte e armazenada em `std::vector<uint8_t> serializedPublishingLicense`.

```cpp

//TODO: Implement GetPublishingLicense()
//Snip implies that function reads PL from source file, database, stream, etc.
std::vector<uint8_t> serializedPublishingLicense = GetPublishingLicense(filePath);

auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<ProtectionHandler>>>();
auto handlerFuture = handlerPromise->get_future();

shared_ptr<ProtectionHandlerObserverImpl> handleObserver =
    std::make_shared<ProtectionHandlerObserverImpl>();

mEngine->CreateProtectionHandlerFromPublishingLicenseAsync(
    serializedPublishingLicense,
    mip::ProtectionHandlerCreationOptions::None,
    handleObserver,
    handlerPromise);

auto handler = handlerFuture.get();
```

