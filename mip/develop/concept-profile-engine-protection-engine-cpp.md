---
title: Conceitos - o objeto de motor de API de proteção
description: Este artigo ajuda-o a compreender os conceitos em todo o objeto de motor de proteção, o que é criada durante a inicialização do aplicativo.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 9595d3a3b12af802720363e141e40608c6f5ba93
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56258415"
---
# <a name="microsoft-information-protection-sdk---protection-api-engine-concepts"></a>SDK - conceitos de motor de API de proteção do Microsoft Information Protection

## <a name="implementation-add-a-protection-engine"></a>Implementação: Adicionar um mecanismo de proteção

Na API do ficheiro, o `mip::ProtectionProfile` classe é a classe de raiz para todas as operações de SDK. Já ter criado o perfil, podemos agora adicionar um mecanismo para o perfil.

O exemplo a seguir demonstra como utilizar um mecanismo único para um único utilizador autenticado.

### <a name="implementation-create-protection-engine-settings"></a>Implementação: Criar definições de motor de proteção

Semelhante a um perfil, o mecanismo também requer um objeto de definições, `mip::ProtectionEngine::Settings`. Este objeto armazena o identificador exclusivo do motor, os dados de cliente personalizável que podem ser utilizados para depuração ou telemetria e, opcionalmente, a localidade.

Aqui vamos criar um `ProtectionEngine::Settings` objeto chamado *engineSettings*. 

```cpp
ProtectionEngine::Settings engineSettings("UniqueID", "");
```

**Nota**: Se utilizar este método para criar o objeto de definições de proteção, tem de definir manualmente o CloudEndpointBaseUrl como https://api.aadrm.com

Como melhor prática, o primeiro parâmetro, **id**, deve ser algo que permite que o mecanismo ligar facilmente para o utilizador associado, **ou** um `mip::Identity` objeto. Para inicializar as configurações com `mip::Identity`:

```cpp
ProtectionEngine::Settings engineSettings(mip::Identity("Bob@Contoso.com", "");
```

No entanto, geralmente, passa numa variável para identidade, em vez de embutir no código.

### <a name="implementation-add-the-protection-engine"></a>Implementação: Adicionar o mecanismo de proteção

Para adicionar o mecanismo, mas vamos voltar para o padrão de promessa/futuro usado para carregar o perfil. Em vez de criar a promessa de `mip::ProtectionProfile`, vamos utilizar `mip::ProtectionEngine`.

```cpp

  //auto profile will be std::shared_ptr<mip::ProtectionProfile>
  auto profile = profileFuture.get();

  //Create the ProtectionEngine::Settings object
  ProtectionEngine::Settings engineSettings("UniqueID", "");

  //Create a promise for std::shared_ptr<mip::ProtectionEngine>
  auto enginePromise = std::make_shared<std::promise<std::shared_ptr<mip::ProtectionEngine>>>();

  //Instantiate the future from the promise
  auto engineFuture = enginePromise->get_future();

  //Add the engine using AddEngineAsync, passing in the engine settings and the promise
  profile->AddEngineAsync(engineSettings, enginePromise);

  //get the future value and store in std::shared_ptr<mip::ProtectionEngine>
  auto engine = engineFuture.get();
```

O resultado final do código acima é que adicionamos com êxito um mecanismo para o usuário autenticado para o perfil.

## <a name="implementation-list-templates"></a>Implementação: Lista de modelos

Usando o mecanismo de foi adicionado, agora é possível listar todos os modelos de sensibilidade disponíveis para o utilizador autenticado ao chamar `engine->GetTemplatesAsync()`. 

`GetTemplatesAsync()` irá obter a lista de identificadores de modelos. O resultado é armazenado num vetor de `std::shared_ptr<std::string>`.

### <a name="implementation-listsensitivitytemplates"></a>Implementação: ListSensitivityTemplates()

```cpp
auto loadPromise = std::make_shared<std::promise<shared_ptr<vector<string>>>>();
std::future<std::shared_ptr<std::vector<std::string>>> loadFuture = loadPromise->get_future();
mEngine->GetTemplatesAsync(engineObserver, loadPromise);
auto templates = loadFuture.get();
```

### <a name="implementation-print-the-template-ids"></a>Implementação: Imprimir os Ids de modelo

```cpp
//Iterate through all template IDs in the vector
for (const auto& temp : *templates) {
  cout << "Template:" << "\n\tId: " << temp << endl;
}
```

Imprimir os nomes é uma forma fácil de mostrar o que nós, com êxito, obtido a política do serviço e tiveram a oportunidade de obter os modelos. Para aplicar o modelo, é necessário o identificador de modelo.

Mapeando modelos em etiquetas só pode ser feito através da política de API, examinando o resultado da `ComputeActions()`.

## <a name="next-steps"></a>Próximos Passos

Agora que o perfil é carregado, o mecanismo adicionado, e temos modelos, podemos adicionar um manipulador para começar a leitura, gravação ou remover modelos de ficheiros. Ver [conceitos de manipulador de proteção](concept-handler-protection-cpp.md).
