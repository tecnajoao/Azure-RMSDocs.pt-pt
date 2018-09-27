---
title: Conceitos - o objeto de motor de API de ficheiros
description: Este artigo ajuda-o a compreender os conceitos em todo o objeto de motor de arquivo, o que é criada durante a inicialização do aplicativo.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5a2e8702b1ace1df2e45224b9b0d76f4c7cb8c77
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47215171"
---
# <a name="file-api-engine"></a>Motor de API de ficheiros

O `mip::FileEngine` na API de ficheiros do SDK do MIP fornece uma interface para todas as operações que são executadas em nome de uma identidade especificada. Será adicionado um mecanismo para cada utilizador que inicia sessão para o aplicativo e todas as operações que o motor de execute será executada no contexto de identidade.

O `FileEngine` tem duas responsabilidades principais: listagem etiquetas para um usuário autenticado e a criação de manipuladores para realizar operações de ficheiros em nome do utilizador de ficheiros. 

- [`mip::FileEngine`](reference/class_mip_fileengine.md)
  - `ListSensitivityLabels()`: Obtém a lista de etiquetas para o mecanismo de carregá-lo.
  - `CreateFileHandler()`: Cria um `mip::FileHandler` para um ficheiro específico ou fluxo.

## <a name="add-a-file-engine"></a>Adicionar um mecanismo de ficheiro

Conforme explicado na [conceitos - motor]() página, um motor de pode ter dois Estados - `CREATED` ou `LOADED`. Se não for um desses dois Estados, não existe. Para criar e carregar um Estado, só é necessário fazer uma chamada única para `FileProfile::LoadAsync`. Se o motor de já existir no Estado em cache, será `LOADED`. Se não existir, será `CREATED` e `LOADED`. `CREATED` indica que o aplicativo tem todas as informações do serviço necessário para carregar o motor. `LOADED` indica que todas as estruturas de dados necessárias para aproveitar o mecanismo foram criadas na memória.

### <a name="create-file-engine-settings"></a>Criar definições de motor de ficheiro

Semelhante a um perfil, o mecanismo também requer um objeto de definições, `mip::FileEngine::Settings`. Este objeto armazena o identificador exclusivo do motor, os dados de cliente personalizável que podem ser utilizados para depuração ou telemetria e, opcionalmente, a localidade.

Aqui vamos criar um `FileEngine::Settings` objeto chamado *engineSettings*. 

```cpp
FileEngine::Settings engineSettings("UniqueID", "");
```

Como melhor prática, o primeiro parâmetro, `id`, deve ser algo que permite que o mecanismo ligar facilmente para o utilizador associado. Algo como endereço de correio eletrónico, UPN, ou GUID de objeto do AAD seria Certifique-se de que o ID é exclusivo e pode ser carregado de estado local sem chamar o serviço.

### <a name="add-the-file-engine"></a>Adicionar o mecanismo de ficheiro

Para adicionar o mecanismo, mas vamos voltar para o padrão de promessa/futuro usado para [o perfil de carga](). Em vez de criar a promessa de `mip::FileProfile`, é criado usando `mip::FileEngine`.

```cpp
  //auto profile will be std::shared_ptr<mip::FileProfile>
  auto profile = profileFuture.get();

  //Create the FileEngine::Settings object
  FileEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::FileEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::FileEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::FileEngine>
  auto engine = engineFuture.get();
```

O resultado final do código acima é que o mecanismo para o utilizador autenticado será adicionado ao perfil.

## <a name="list-sensitivity-labels"></a>Etiquetas de sensibilidade da lista

Usando o mecanismo de adicionados, é agora possível para listar todos da sensibilidade etiquetas disponível para o utilizador autenticado ao chamar `engine->ListSensitivityLabels()`.

`ListSensitivityLabels()` irá obter a lista de etiquetas e os atributos dessas etiquetas de um utilizador específico do serviço. O resultado é armazenado num vetor de `std::shared_ptr<mip::Label>`.

Leia mais [aqui]() no `mip::Label`.

### <a name="listsensitivitylabels"></a>ListSensitivityLabels()

```cpp
std::vector<shared_ptr<mip::Label>> labels = engine->ListSensitivityLabels();
```

Ou, simplificada:

```cpp
auto labels = engine->ListSensitivityLabels();
```

### <a name="print-the-labels-and-ids"></a>As etiquetas e as identificações de impressão

Imprimir os nomes é uma forma fácil de mostrar que nós, com êxito, obtido a política do serviço e conseguimos obter etiquetas. Para aplicar a etiqueta, é necessário o identificador de etiqueta. O código a seguir itera em todas as etiquetas, exibindo a `name` e o `id` para cada etiqueta principal e subordinada.

```cpp
//Iterate through all labels in the vector
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

## <a name="next-steps"></a>Passos Seguintes

Agora que o perfil é carregado, o mecanismo adicionado, e temos etiquetas, podemos adicionar um manipulador para começar a leitura, gravação ou remover etiquetas de ficheiros.

- [Criar um manipulador de arquivo]()

