---
title: Conceitos - observadores de API de ficheiros no SDK do MIP.
description: O SDK de MIP foi concebido para ser quase que totalmente assíncrono. Este artigo ajuda-o a compreender como os observadores de API de ficheiros são implementados e utilizados para assincronicidade.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 94389d552d4d42a2cedcacab76b1c98fcca9893c
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214291"
---
# <a name="file-api-observers"></a>Observadores de API de ficheiros

A API de ficheiros contém duas classes de observador. Membros de observador são virtuais e podem ser substituídos para lidar com retornos de chamada do evento.

- [`mip::FileProfile::Observer`](reference/class_mip_fileprofile_observer.md)
- [`mip::FileHandler::Observer`](reference/class_mip_filehandler_observer.md)

Quando uma operação assíncrona for concluída, o `OnXxx()` denomina-se a função de membro correspondente para o resultado. Os exemplos são `OnLoadSuccess()`, `OnLoadFailure()`, e `OnAddEngineSuccess()` para `mip::FileProfile::Observer`.

Os exemplos abaixo demonstram o padrão de promessa/futuro, o que também é utilizado por amostras do SDK e pode ser estendido para implementar o comportamento de retorno de chamada pretendido. 

## <a name="file-profile-observer-implementation"></a>Implementação do observador de perfil de ficheiros

No exemplo a seguir, criamos uma classe, `ProfileObserver` que é derivado de `mip::FileProfile::Observer`. As funções de membro foram substituídas para usar o padrão de promessa/futuro usado em todo os exemplos.

**Tenha em atenção**: O abaixo exemplos apenas parcialmente são implementados e não incluem substituições para o `mip::FileEngine` relacionados com os observadores.

### <a name="profileobserverh"></a>profile_observer.h

No cabeçalho, definimos `ProfileObserver`, derivadas de `mip::FileProfile::Observer`, em seguida, substituir cada uma das funções de membro.

```cpp
class ProfileObserver final : public mip::FileProfile::Observer {
public:
ProfileObserver() { }
  void OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) override;
  void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
  //TODO: Implement mip::FileEngine related observers.
};
```

### <a name="profileobservercpp"></a>profile_observer.cpp

Na implementação em si, definimos uma ação a tomar para cada função de membro de observador.

Cada membro aceita dois parâmetros. A primeira é um ponteiro compartilhado para a classe que estamos manipulando na função. `ProfileObserver::OnLoadSuccess` Esperava-se receber um `mip::FileProfile`. `ProfileObserver::OnAddEngineSuccess` esperaria `mip::FileEngine`.

O segundo é um ponteiro compartilhado para o *contexto*. Em nossa implementação, o contexto é uma referência a um `std::promise`, passados por referência como `std::shared_ptr<void>`. A primeira linha da função converte isso `std::promise`, em seguida, armazenados num objeto chamado `promise`.

Por fim, o futuro é feito pronto, definindo a `promise->set_value()` e passando o `mip::FileProfile` objeto.

```cpp
#include "profile_observer.h"
#include <future>

//Called when FileProfile is successfully loaded
void ProfileObserver::OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) {
  //cast context to promise
  auto promise = 
  std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileProfile>>>(context);
  //set promise value to profile
  promise->set_value(profile);
}

//Called when FileProfile fails to load
void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
  auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileProfile>>>(context);
  promise->set_exception(error);
}

//TODO: Implement mip::FileEngine related observers.
```

Quando vamos criar uma instância de qualquer classe do SDK ou utilizar uma função que realiza operações assíncronas, passaremos a implementação de observador para o construtor de definições ou a função async em si. Ao instanciar o `mip::FileProfile::Settings` objeto, o construtor aceita `mip::FileProfile::Observer` como um dos parâmetros. O exemplo abaixo mostra nossos personalizado `ProfileObserver`, utilizado num `mip::FileProfile::Settings` construtor.

## <a name="filehandler-observer-implementation"></a>Implementação de FileHandler observador

O observador de perfil, semelhante a `mip::FileHandler` implementa uma `mip::FileHandler::Observers` classe para lidar com notificações de eventos assíncronos durante operações de arquivo. A implementação é semelhante ao que detalhados acima. `FileHandlerObserver` parcialmente definida abaixo. A implementação completa pode ser encontrada na nossa [repositório de exemplo do GitHub](). LISTA DE TAREFAS: LIGAÇÃO

### <a name="filehandlerobserverh"></a>file_handler_observer.h

```cpp
#include "mip/file/file_handler.h"

class FileHandlerObserver final : public mip::FileHandler::Observer {
public:
  void OnCreateFileHandlerSuccess(
      const std::shared_ptr<mip::FileHandler>& fileHandler,
      const std::shared_ptr<void>& context) override;

  void OnCreateFileHandlerFailure(
      const std::exception_ptr& error,
      const std::shared_ptr<void>& context) override;

  //TODO: override remaining member functions inherited from mip::FileHandler::Observer
};
```

### <a name="filehandlerobservercpp"></a>file_handler_observer.cpp

Este exemplo é apenas as duas primeiras funções, mas as restantes funções usam um padrão semelhante para cada uma delas e, a `ProfileObserver`.

```cpp
#include "file_handler_observer.h"

void FileHandlerObserver::OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) {
    auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
    promise->set_value(fileHandler);
}

void FileHandlerObserver::OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) {
    auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
    promise->set_exception(error);
}

//TODO: override remaining member functions inherited from mip::FileHandler::Observer
```

## <a name="next-steps"></a>Passos Seguintes

[TBD - ligação para criar uma `mip::FileProfile`, carregar um `mip::FileEngine`e executar operações de arquivo com `mip::FileHandler`.]()
