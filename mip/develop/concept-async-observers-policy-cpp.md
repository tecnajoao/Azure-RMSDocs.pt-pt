---
title: Conceitos - observadores de política de API no SDK do MIP.
description: O SDK de MIP foi concebido para ser quase que totalmente assíncrono. Este artigo ajuda-o a compreender como os observadores de API de política são implementados e utilizados para assincronicidade.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: fbdb1e7d1bf6a99228e810dca4d9532c79849d48
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214263"
---
# <a name="policy-api-observers"></a>Observadores de política de API

O SDK da política de API contém uma classe de observador. Membros de observador são virtual e devem ser substituídos para lidar com retornos de chamada para operações assíncronas.

- [`mip::Profile::Observer`](reference/class_mip_Profile_observer.md)

Quando uma operação assíncrona for concluída, o `OnXxx()` denomina-se a função de membro correspondente para o resultado. Os exemplos são `OnLoadSuccess()`, `OnLoadFailure()`, e `OnAddEngineSuccess()` para `mip::Profile::Observer`.

Os exemplos abaixo demonstram o padrão de promessa/futuro, o que também é utilizado por amostras do SDK e pode ser estendido para implementar o comportamento de retorno de chamada pretendido. 

## <a name="profile-observer-implementation"></a>Implementação do observador de perfil

No exemplo a seguir, criamos uma classe, `ProfileObserver` que é derivado de `mip::Profile::Observer`. As funções de membro foram substituídas para usar o padrão de promessa/futuro usado em todo os exemplos.

**Tenha em atenção**: O abaixo exemplos apenas parcialmente são implementados e não incluem substituições para o `mip::ProfileEngine` relacionados com os observadores.

### <a name="profileobserverh"></a>profile_observer.h

No cabeçalho, definimos `ProfileObserver`, derivadas de `mip::Profile::Observer`, em seguida, substituir cada uma das funções de membro.

```cpp
class ProfileObserver final : public mip::Profile::Observer {
public:
ProfileObserver() { }
  void OnLoadSuccess(const std::shared_ptr<mip::Profile>& profile, const std::shared_ptr<void>& context) override;
  void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
  //TODO: Implement remaining members
};
```

### <a name="profileobservercpp"></a>profile_observer.cpp

Na implementação em si, definimos uma ação a tomar para cada função de membro de observador.

Cada membro aceita dois parâmetros. A primeira é um ponteiro compartilhado para a classe manipulado pela função. `ProfileObserver::OnLoadSuccess` Esperava-se receber um `mip::Profile`. `ProfileObserver::OnAddEngineSuccess` esperaria `mip::ProfileEngine`.

O segundo é um ponteiro compartilhado para o *contexto*. Em nossa implementação, o contexto é uma referência a um `std::promise`, transmitido como `shared_ptr<void>`. A primeira linha da função converte isso `std::promise`, em seguida, armazenados num objeto chamado `promise`.

Por fim, o futuro é feito pronto, definindo a `promise->set_value()` e passando o `mip::Profile` objeto.

```cpp
#include "profile_observer.h"
#include <future>

//Called when Profile is successfully loaded
void ProfileObserver::OnLoadSuccess(const std::shared_ptr<mip::Profile>& profile, const std::shared_ptr<void>& context) {
  //cast context to promise
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::Profile>>>(context);
  //set promise value to profile
  promise->set_value(profile);
}

//Called when Profile fails to load
void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::Profile>>>(context);
  promise->set_exception(error);
}

//TODO: Implement remaining observer members
```

Ao realizar qualquer operação assíncrona, a implementação de observador é passada para o construtor de definições ou a função async em si. 

## <a name="next-steps"></a>Passos Seguintes

[TBD - ligação para criar uma `mip::Profile`, carregar um `mip::ProfileEngine`e realizar operações de ficheiros com `mip::FileHandler`]()