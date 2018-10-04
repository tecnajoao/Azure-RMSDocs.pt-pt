---
title: Conceitos - observadores de API de proteção no SDK do MIP.
description: O SDK de MIP foi concebido para ser quase que totalmente assíncrono. Este artigo ajuda-o a compreender como os observadores de API de proteção são implementados e utilizados para assincronicidade.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: d7077678ba336b031f7a8f812a3c4e90d8c5b05a
ms.sourcegitcommit: d677088db8588fb2cc4a5d7dd296e76d0d9a2e9c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251714"
---
# <a name="microsoft-information-protection-sdk---protection-api-observers"></a>SDK - observadores de API de proteção do Microsoft Information Protection

A API de proteção contém três classes de observador. Membros de observador são virtuais e podem ser substituídos para lidar com retornos de chamada para operações assíncronas.

- [Perfil de proteção: `mip::ProtectionProfile::Observer`](reference/class_mip_ProtectionProfile_observer.md)
- [Motor de proteção: `mip::ProtectionEngine::Observer`](reference/class_mip_ProtectionEngine_observer.md)
- [Manipulador de proteção: `mip::ProtectionHandler::Observer`](reference/class_mip_Protectionhandler_observer.md)

Quando uma operação assíncrona for concluída, o `OnXxx()` denomina-se a função de membro correspondente para o resultado. Os exemplos são `OnLoadSuccess()`, `OnLoadFailure()`, e `OnAddEngineSuccess()` para `mip::ProtectionProfile::Observer`.

Os exemplos abaixo demonstram o padrão de promessa/futuro, o que também é utilizado por amostras do SDK e pode ser estendido para implementar o comportamento de retorno de chamada pretendido. 

## <a name="protection-protection-observer-implementation"></a>Implementação de observador de proteção de proteção

No exemplo a seguir, criamos uma classe, `ProtectionProfileObserverImpl` que é derivado de `mip::ProtectionProfile::Observer`. As funções de membro foram substituídas para usar o padrão de promessa/futuro usado em todo os exemplos.

### <a name="protectionprofileobserverimpl-class-declaration"></a>Declaração de classe ProtectionProfileObserverImpl

No cabeçalho, definimos `ProtectionProfileObserverImpl`, derivadas de `mip::ProtectionProfile::Observer`, em seguida, substituir cada uma das funções de membro.

```cpp
//ProtectionProfileObserverImpl.h
class ProtectionProfileObserverImpl final : public mip::ProtectionProfile::Observer {
public:
  ProtectionProfileObserverImpl() { }
  void OnLoadSuccess(const shared_ptr<mip::ProtectionProfile>& profile, const shared_ptr<void>& context) override;
  void OnLoadFailure(const exception_ptr& error, const shared_ptr<void>& context) override;
  void OnAddEngineSuccess(const shared_ptr<mip::ProtectionEngine>& engine, const shared_ptr<void>& context) override;
  void OnAddEngineError(const exception_ptr& error, const shared_ptr<void>& context) override;
};
```

### <a name="protectionprofileobserverimpl-implementation"></a>Implementação de ProtectionProfileObserverImpl

Na implementação em si, podemos simplesmente definir uma ação a tomar para cada função de membro de observador.

Cada membro aceita dois parâmetros. A primeira é um ponteiro compartilhado para a classe que estamos manipulando na função. `ProtectionObserver::OnLoadSuccess` Esperava-se receber uma `mip::ProtectionProtection`, `ProtectionObserver::OnAddEngineSuccess` esperaria `mip::ProtectionEngine`.

O segundo é um ponteiro compartilhado para o *contexto*. Em nossa implementação, o contexto é uma referência a um `std::promise`, transmitido como `shared_ptr<void>`. A primeira linha da função converte isso `std::promise`, em seguida, armazenados num objeto chamado `promise`.

Por fim, o futuro é feito pronto, definindo a `promise->set_value()` e passando o `mip::ProtectionProtection` objeto.

```cpp
//protection_observers.cpp

void ProtectionProfileObserverImpl::OnLoadSuccess(
  const shared_ptr<mip::ProtectionProfile>& profile,
  const shared_ptr<void>& context) {
  auto loadPromise = static_cast<promise<shared_ptr<mip::ProtectionProfile>>*>(context.get());
  loadPromise->set_value(profile);
};

void ProtectionProfileObserverImpl::OnLoadFailure(const exception_ptr& error, const shared_ptr<void>& context) {
  auto loadPromise = static_cast<promise<shared_ptr<mip::ProtectionProfile>>*>(context.get());
  loadPromise->set_exception(error);
};

void ProtectionProfileObserverImpl::OnAddEngineSuccess(
  const shared_ptr<mip::ProtectionEngine>& engine,
  const shared_ptr<void>& context) {
  auto addEnginePromise = static_cast<promise<shared_ptr<mip::ProtectionEngine>>*>(context.get());
  addEnginePromise->set_value(engine);
};

void ProtectionProfileObserverImpl::OnAddEngineError(
  const exception_ptr& error,
  const shared_ptr<void>& context) {
  auto addEnginePromise = static_cast<promise<shared_ptr<mip::ProtectionEngine>>*>(context.get());
  addEnginePromise->set_exception(error);
};
```

Quando vamos criar uma instância de qualquer classe do SDK ou utilizar uma função que realiza operações assíncronas, passaremos a implementação de observador para o construtor de definições ou a função async em si. Ao instanciar o `mip::ProtectionProfile::Settings` objeto, o construtor aceita `mip::ProtectionProfile::Observer` como um dos parâmetros. O exemplo abaixo mostra nossos personalizado `ProtectionProfileObserverImpl`, utilizado num `mip::ProtectionProfile::Settings` construtor.

## <a name="protectionhandler-observer-implementation"></a>Implementação de ProtectionHandler observador

O observador de proteção, semelhante `mip::ProtectionHandler` implementa uma `mip::ProtectionHandler::Observer` classe para lidar com notificações de eventos assíncronos durante operações de proteção. A implementação é semelhante ao que detalhados acima. `ProtectionHandlerObserverImpl` parcialmente definida abaixo. A implementação completa pode ser encontrada na nossa [repositório de exemplo do GitHub](https://azure.microsoft.com/resources/samples/?sort=0&term=mip+sdk).

### <a name="protectionhandlerobserverimpl-class-declaration"></a>Declaração de classe ProtectionHandlerObserverImpl

```cpp
//protection_observers.h

class ProtectionHandlerObserverImpl final : public mip::ProtectionHandler::Observer {
public:
  ProtectionHandlerObserverImpl() { }
  void OnCreateProtectionHandlerSuccess(const shared_ptr<mip::ProtectionHandler>& protectionHandler, const shared_ptr<void>& context) override;
  void OnCreateProtectionHandlerError(const exception_ptr& error, const shared_ptr<void>& context) override;
};
```

### <a name="protectionhandlerobserverimpl-partial-implementation"></a>Implementação de ProtectionHandlerObserverImpl parcial

Este exemplo é apenas as duas primeiras funções, mas as restantes funções usam um padrão semelhante para cada uma delas e, a `ProtectionObserver`.

```cpp
//protection_observers.cpp

void ProtectionHandlerObserverImpl::OnCreateProtectionHandlerSuccess(
  const shared_ptr<mip::ProtectionHandler>& protectionHandler,
  const shared_ptr<void>& context) {
  auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get());
  createProtectionHandlerPromise->set_value(protectionHandler);
};

void ProtectionHandlerObserverImpl::OnCreateProtectionHandlerError(
  const exception_ptr& error,
  const shared_ptr<void>& context) {
  auto createProtectionHandlerPromise = static_cast<promise<shared_ptr<mip::ProtectionHandler>>*>(context.get());
  createProtectionHandlerPromise->set_exception(error);
};
```

