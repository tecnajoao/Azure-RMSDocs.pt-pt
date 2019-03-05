---
title: Conceitos - observadores no SDK do MIP.
description: O SDK de MIP foi concebido para ser quase que totalmente assíncrono. Este artigo ajuda-o a compreender como os observadores são implementados e utilizados para assincronicidade.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: e42b9996d737ace5b25988eb72fa02aa87230f13
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330870"
---
# <a name="microsoft-information-protection-sdk---observer-concepts"></a>SDK - conceitos do observador do Microsoft Information Protection

O SDK de MIP foi concebido para ser quase que totalmente assíncrono. Por exemplo, qualquer operação, resultando em e/s de rede ou um ficheiro é executada de forma assíncrona. Para processar as notificações de evento para esses eventos assíncronos, o SDK utiliza o [padrão observador](https://wikipedia.org/wiki/Observer_pattern). 

## <a name="implementation-overview"></a>Descrição geral de implementação

Ao construir um objeto que irá efetuar uma operação assíncrona, um `Observer` classe tem de ser implementada. Observadores irão receber os eventos de notificação relacionados com as várias operações assíncronas no SDK do MIP e fornecer o resultado para o chamador.

As funções em cada `Observer` classe são virtual e são substituídos para o padrão assíncrono preferencial. O SDK implementa o padrão de observador de notificação de evento via `std::promise` e `std::future`.

Cada classe específica observador contém um conjunto de funções de êxito e falha do erro, para o resultado de uma operação assíncrona. *Êxito* funções devolvem o objeto associado a operação. *Erro*/*falha* funções devolvem uma exceção que contém detalhes sobre por que a operação foi concluída com êxito.

Por exemplo, `FileProfile` suporta as seguintes duas operações: 

- Ele pode adicionar um novo mecanismo para o perfil através do `FileProfile::AddEngineAsync`. 
- Ele pode descarregar um motor do perfil por meio da `FileProfile::UnloadEngineAsync`.

Desde dois `Observer` funções estão implementadas por operação assíncrona, é possível pressupor que existem **quatro** `Observer` métodos associados `FileProfile`: 

- `FileProfileObserver::OnAddEngineSuccess()`
- `FileProfileObserver::OnAddEngineError()`
- `FileProfileObserver::OnUnloadEngineSuccess`
- `FileProfileObserver::OnUnloadEngineError()`. 

## <a name="mip-sdk-observer-classes"></a>Classes de observador MIP SDK

A API de ficheiros do SDK MIP contém dois observadores:

* `mip::FileProfile::Observer`
* `mip::FileHandler::Observer`

A API de política de SDK MIP tem apenas um único observador:

* `mip::Profile::Observer`

A API de proteção de SDK MIP tem três observadores:

* `mip::ProtectionProfile::Observer`
* `mip::ProtectionEngine::Observer`
* `mip::ProtectionHandler::Observer`

## <a name="next-steps"></a>Próximos Passos

Saiba mais sobre como os observadores são implementados e utilizados, por várias APIs:

* [Observadores de API de ficheiros (C++)](concept-async-observers-file-cpp.md)
* [Observadores de política de API (C++)](concept-async-observers-policy-cpp.md)
* [Observadores de API de proteção (C++)](concept-async-observers-protection-cpp.md)
