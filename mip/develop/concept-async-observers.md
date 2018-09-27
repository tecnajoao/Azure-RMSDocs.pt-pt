---
title: Conceitos - observadores no SDK do MIP.
description: O SDK de MIP foi concebido para ser quase que totalmente assíncrono. Este artigo ajuda-o a compreender como os observadores são implementados e utilizados para assincronicidade.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e8014e24917bfcae4d7974881007ec0c4e95fc19
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214322"
---
# <a name="observers-in-the-mip-sdk"></a>Observadores no SDK do MIP

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

## <a name="next-steps-tbd"></a>Próximas etapas (TBD)

Saiba mais sobre como os observadores são implementados e utilizados, por várias APIs:

* [Observadores de API de ficheiros (C++)](concept-async-observers-file-cpp.md)
* [Observadores de política de API (C++)](concept-async-observers-policy-cpp.md)
* [Observadores de API de proteção (C++)](concept-async-observers-protection-cpp.md)
