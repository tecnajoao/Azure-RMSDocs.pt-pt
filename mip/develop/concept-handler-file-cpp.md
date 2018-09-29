---
title: Conceitos - manipuladores de arquivo no SDK do MIP.
description: Este artigo ajuda-o a compreender como os manipuladores de API de ficheiros são criadas e utilizadas para chamar operações.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6b2916a3937892353f4389a59b5e48356deda603
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453372"
---
# <a name="microsoft-information-protection-sdk---file-handler-concepts"></a>SDK - conceitos de manipulador de arquivo do Microsoft Information Protection

Na API de ficheiros do SDK do MIP, o `mip::FileHandler` expõe todas as diversas operações que podem ser utilizadas para ler e escrever as etiquetas ou proteção, num conjunto de tipos de ficheiro para o qual o suporte está incorporado. 

## <a name="supported-file-types"></a>Tipos de ficheiro suportados

- Formatos de arquivo do Office com base na OCP (Office 2010 e posterior)
- Formatos de arquivo legadas do Office (Office 2007)
- PDF
- Suporte PFILE genérico
- Ficheiros que suportam XMP do Adobe

## <a name="file-handler-functions"></a>Funções do manipulador de arquivo

`mip::FileHandler` expõe métodos para ler, escrever e remover etiquetas e informações sobre a proteção. Para obter a lista completa, consulte a [referência da API](reference/class_mip_filehandler.md).

Neste artigo, serão abordados os seguintes métodos:

- `GetLabelAsync()`
- `SetLabel()`
- `DeleteLabel()`
- `CommitAsync()`

## <a name="requirements"></a>Requisitos

Criar um `FileHandler` para trabalhar com um ficheiro específico, é necessário:

- A `FileProfile`
- A `FileEngine` adicionado para o `FileProfile`
- Uma classe que herda `mip::FileHandler::Observer`

## <a name="create-a-file-handler"></a>Criar um manipulador de arquivo

A primeira etapa necessária no gerenciamento de arquivos a API de ficheiros é criar um `FileHandler` objeto. Essa classe implementa toda a funcionalidade necessária para obter, definir, atualizar, eliminar e etiqueta de consolidação é alterado para ficheiros.

Criar a `FileHandler` é tão fácil quanto chamar o `FileEngine`do `CreateFileHandlerAsync` funcionar usando o padrão de promessa/futuro.

`CreateFileHandlerAsync` aceita três parâmetros: O caminho para o ficheiro que deve ser lidos ou modificado, o `mip::FileHandler::Observer` para notificações de eventos assíncronos e a promessa para o `FileHandler`.

**Nota:** a `mip::FileHandler::Observer` classe tem de ser implementada numa classe derivada como `CreateFileHandler` requer o `Observer` objeto. 

```cpp
auto createFileHandlerPromise = std::make_shared<std::promise<std::shared_ptr<mip::FileHandler>>>();
auto createFileHandlerFuture = createFileHandlerPromise->get_future();
fileEngine->CreateFileHandlerAsync(filePath, std::make_shared<FileHandlerObserver>(), createFileHandlerPromise);
auto handler = createFileHandlerFuture.get();
```

Depois de criar com êxito o `FileHandler` de objeto, operações de arquivo (get/set/delete/consolidação) podem ser executadas.

## <a name="read-a-label"></a>Ler uma etiqueta

### <a name="metadata-requirements"></a>Requisitos de metadados

Existem alguns requisitos para ler os metadados de um ficheiro e a tradução em para algo com êxito, podem ser usados em aplicativos.

- A etiqueta a leitura ainda tem de existir no serviço do Office 365. Se ele é eliminado por completo, o SDK irão falhar obter informações sobre essa etiqueta e irá devolver um erro.
- Os metadados do ficheiro tem de ser intactos. Esses metadados incluem:
  - Attribute1
  - Attribute2

### <a name="getlabelasync"></a>GetLabelAsync()

Ter criado o manipulador para apontar para um ficheiro específico, retornamos o padrão de promessa/futuro de forma assíncrona ler a etiqueta. A promessa é para um `mip::ContentLabel` objeto que contém todas as informações sobre a etiqueta aplicada.

Depois de instanciar o `promise` e `future` objetos, que Lemos a etiqueta chamando `handler->GetLabelAsync()` e fornecer o `promise` como o único parâmetro. Por fim, a etiqueta pode ser armazenada numa `mip::ContentLabel` objeto que estamos obterá do `future`.

```cpp
auto loadPromise = std::make_shared<std::promise<std::shared_ptr<mip::ContentLabel>>>();
auto loadFuture = loadPromise->get_future();
handler->GetLabelAsync(loadPromise);
auto label = loadFuture.get();
```

Etiqueta de dados podem ser lidos do `label` de objeto e passado para qualquer outro componente ou funcionalidade do aplicativo.

***

## <a name="set-a-label"></a>Definir uma etiqueta

Definição de uma etiqueta é um processo de duas partes. Em primeiro lugar, ter criado um manipulador que aponta para o ficheiro em questão, a etiqueta pode ser definida chamando `FileHandler->SetLabel()` com alguns parâmetros.

```cpp
handler->SetLabel(label->GetId(), mip::LabelingOptions{ mip::AssignmentMethod::PRIVILEGED, "" });
```

Os parâmetros a primeira é simplesmente o identificador de etiqueta de `ListLabelsAsync()`. Este valor pode ser armazenado numa variável dedicada ou ao ler `mip::Label->GetId()`.

O exemplo acima assume armazenamos desejada `mip::Label` num objeto chamado `label`.

### <a name="labeling-options"></a>Opções de etiquetagem

O segundo parâmetro necessário para definir a etiqueta é um `mip::LabelingOptions` objeto que criamos inline ao chamar o `SetLabel()` função. Também poderia ser criado antes do tempo.

`LabelingOptions` Especifica informações adicionais sobre a etiqueta, como o `AssignmentMethod` e a justificação para uma ação.

- `mip::AssignmentMethod` é simplesmente um enumerador que tem três valores: `STANDARD`, `PRIVILEGED`, ou `AUTO`. Reveja o `mip::AssignmentMethod` referência para obter mais detalhes.
- A justificação é necessária apenas se a política de serviço exigir *e* quando reduzirem o *existente* sensibilidade de um ficheiro.

```cpp
auto labelingOptions = mip::LabelingOptions();
labelingOptions.SetMethod(mip::AssignmentMethod::STANDARD);
labelingOptions.SetJustificationMessage("Because I made an educated decision based upon the contents of this file.");
```

E agora em vez de criar etiquetas inline de opções, ele pode ser passado para o `SetLabel()` função.

```cpp
handler->SetLabel(label->GetId(), labelingOptions);
```

Agora após definir a etiqueta do ficheiro referenciado pelo manipulador, ainda há mais uma etapa para confirmar a alteração e gravar um arquivo de disco ou criar um fluxo de saída.

### <a name="commit-changes"></a>Confirmar alterações

É a etapa final na consolidação qualquer alteração num arquivo no SDK do MIP **consolidação** a alteração. Isto é feito usando o `FileHandler->CommitAsync()` função. 

Para implementar a função de compromisso, retornamos à promessa/futuro, criando uma promessa de um `bool`. O `CommitAsync()` função retornará true se a operação foi concluída com êxito ou FALSO se ele falhar por qualquer motivo. 

Depois de criar o `promise` e `future`, `CommitAsync()` é chamado e foram fornecidos dois parâmetros: O caminho do ficheiro de saída (`std::string`) e a promessa. Por último, o resultado é obtido ao obter o valor da `future` objeto.

```cpp
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();
handler->CommitAsync(outputFile, commitPromise);
auto wasCommitted = commitFuture.get();
```

**Importante:** o `FileHandler` não irá atualizar ou substituir ficheiros existentes. Cabe ao desenvolvedor implementar **substituindo** o ficheiro que está a ser etiquetado. 

Se uma etiqueta para a escrever **FileA.docx**, uma cópia do ficheiro **FileB.docx**, será criado com a etiqueta aplicada. Código deve ser escrito para a mudança de nome/remover **FileA.docx** e mude o nome **FileB.docx**.

***

## <a name="delete-a-label"></a>Eliminar uma etiqueta

```cpp
auto handler = mEngine->CreateFileHandler(filePath, std::make_shared<FileHandlerObserverImpl>());
handler->DeleteLabel(mip::AssignmentMethod::PRIVILEGED, "Label unnecessary.");
auto commitPromise = std::make_shared<std::promise<bool>>();
auto commitFuture = commitPromise->get_future();
handler->CommitAsync(outputFile, commitPromise);
```
