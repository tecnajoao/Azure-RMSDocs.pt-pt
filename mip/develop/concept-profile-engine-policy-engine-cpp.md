---
title: Conceitos - o objeto de motor de política de API
description: Este artigo ajuda-o a compreender os conceitos em todo o objeto de motor de política, o que é criada durante a inicialização do aplicativo.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 9aac5fb0e010c8c73776c3e62ba9e98bdeff77d2
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252780"
---
# <a name="microsoft-information-protection-sdk---policy-api-engine-concepts"></a>SDK - conceitos de motor de política de API do Microsoft Information Protection

`mip::PolicyEngine` implementa todas as operações que podem realizar a API de política, com exceção de carregar o perfil. 

## <a name="implementation-add-a-policy-engine"></a>Implementação: Adicionar um motor de política

### <a name="implementation-create-policy-engine-settings"></a>Implementação: Criar definições de motor de política

Semelhante a um perfil, o mecanismo também requer um objeto de definições, `mip::PolicyEngine::Settings`. Este objeto armazena o identificador exclusivo do motor, os dados de cliente personalizável que podem ser utilizados para depuração ou telemetria e, opcionalmente, a localidade.

Aqui vamos criar um `PolicyEngine::Settings` objeto chamado *engineSettings*.

```cpp
PolicyEngine::Settings engineSettings("UniqueID", "");
```

Como melhor prática, o primeiro parâmetro, **id**, deve ser algo que permite que o mecanismo ligar facilmente para o utilizador associado, preferencialmente, o nome principal de utilizador.

### <a name="implementation-add-the-policy-engine"></a>Implementação: Adicionar o motor de política

Para adicionar o mecanismo, mas vamos voltar para o padrão de promessa/futuro usado para carregar o perfil. Em vez de criar a promessa de `mip::Profile`, vamos utilizar `mip::PolicyEngine`.

```cpp

  //auto profile will be std::shared_ptr<mip::Profile>
  auto profile = profileFuture.get();

  //Create the PolicyEngine::Settings object
  PolicyEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::PolicyEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::PolicyEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::PolicyEngine>
  auto engine = engineFuture.get();
```

O resultado final do código acima é que adicionamos com êxito um mecanismo para o usuário autenticado para o perfil.

## <a name="implementation-list-sensitivity-labels"></a>Implementação: Etiquetas de sensibilidade da lista

Usando o mecanismo de adicionados, é agora possível para listar todos da sensibilidade etiquetas disponível para o utilizador autenticado ao chamar `engine->ListSensitivityLabels()`.

`ListSensitivityLabels()` irá obter a lista de etiquetas e os atributos dessas etiquetas de um utilizador específico do serviço. O resultado é armazenado num vetor de `std::shared_ptr<mip::Label>`.

### <a name="implementation-listsensitivitylabels"></a>Implementação: ListSensitivityLabels()

```cpp
std::vector<shared_ptr<mip::Label>> labels = engine->ListSensitivityLabels();
```

### <a name="implementation-print-the-labels"></a>Implementação: As etiquetas de impressão

```cpp
//Iterate through all labels in the vector
for (const auto& label : labels) {
  //print the label name
  cout << label->GetName() << endl;
  //Iterate through all child labels
  for (const auto& child : label->GetChildren()) {
    //Print the label with some formatting
    cout << "->  " << child->GetName() << endl;
  }
}
```

Imprimir os nomes é uma forma fácil de mostrar que nós, com êxito, obtido a política do serviço e conseguimos obter etiquetas. Para aplicar a etiqueta, é necessário o identificador de etiqueta. Modificar o recorte de acima para devolver o ID de etiqueta resulta em:

```cpp
for (const auto& label : labels) {
  //Print label name and GUID
  cout << label->GetName() << " : " << label->GetId() << endl;

  //Print child label name and GUID
  for (const auto& child : label->GetChildren()) {    
    cout << "->  " << child->GetName() <<  " : " << child->GetId() << endl;
  }
}
```

A coleção de `mip::Label` devolvido pelo `GetSensitivityLabels()` pode ser utilizado para apresentar todas as etiquetas disponíveis ao utilizador e, em seguida, quando selecionado, utilize o ID para aplicar etiquetas a um ficheiro.

