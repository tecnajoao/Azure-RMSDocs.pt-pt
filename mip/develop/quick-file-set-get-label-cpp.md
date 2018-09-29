---
title: Início rápido - Set e get uma etiqueta de sensibilidade num arquivo usando o C++ MIP SDK
description: Um guia de introdução mostra-lhe como utilizar o SDK de C++ do Microsoft Information Protection para definir e obter uma etiqueta de sensibilidade num ficheiro.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: d1e159e2276f5dc76a180711a81e3d0a182eb29e
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453406"
---
# <a name="quickstart-set-and-get-a-sensitivity-label-c"></a>Guia de introdução: Definir e obter uma etiqueta de sensibilidade (C++)

Este guia de introdução mostra como usar mais de APIs de arquivo MIP. Utilizar uma das etiquetas de sensibilidade listados no início rápido anterior, utilize um manipulador de arquivo para definir/obter o rótulo num arquivo. O arquivo de classe de manipulador expõe várias operações para definição/obter etiquetas ou proteção, para tipos de ficheiro suportados.

## <a name="prerequisites"></a>Pré-requisitos

Se ainda não o fez, certifique-se de que concluir os seguintes pré-requisitos antes de continuar:

- Concluída [início rápido: listar etiquetas de sensibilidade (C++)](quick-file-list-labels-cpp.md) primeiro, que cria uma solução do Visual Studio, de arranque para listar as etiquetas de sensibilidade da organização. Este início rápido se baseia no anterior.
- Opcionalmente,: Reveja [manipuladores de ficheiros no SDK do MIP](concept-handler-file-cpp.md) conceitos.

> [!IMPORTANT]
> Se passar muito tempo entre a conclusão do início rápido anterior "Etiquetas de sensibilidade da lista" e neste procedimento, irá expirar o token estático criado no primeiro. Se assim, precisará gerar um novo token e a atualização sua `AcquireOAuth2Token()` novamente a implementação. Ver [atualizar a lógica de aquisição do token com um token de acesso válido](quick-file-list-labels-cpp.md#update-the-token-acquisition-logic-with-a-valid-access-token) para obter mais detalhes.

## <a name="implement-an-observer-class-to-monitor-the-file-handler-object"></a>Implementar uma classe de observador para monitorizar o objeto do manipulador de arquivo

Semelhante para o observador é implementada (para o perfil de ficheiros e o mecanismo) na inicialização do aplicativo início rápido, agora implementa uma classe de observador para um objeto de manipulador de arquivo.

Criar uma implementação básica para uma classe de observador, ao expandir o SDK `mip::FileHandler::Observer` classe. O observador é instanciado e utilizado mais tarde, para monitorizar as operações de manipulador de arquivo.

1. Abra a solução do Visual Studio qual trabalhou num anterior "Guia de início rápido: listar etiquetas de sensibilidade (C++)" artigo.

2. Adicione uma nova classe ao seu projeto, o que gera arquivos de cabeçalho /. h e de implementação /. cpp para:

   - Na **Explorador de soluções**, clique com botão direito no nó do projeto novamente, selecione **Add**, em seguida, selecione **classe**.
   - Sobre o **adicionar classe** caixa de diálogo:
     - Na **nome da classe** , insira "filehandler_observer". Tenha em atenção que tanto o **arquivo. h** e **arquivo. cpp** campos são automaticamente preenchidos, com base no nome que introduzir.
     - Quando terminar, clique nas **OK** botão.

3. Depois de gerar os arquivos. h e. cpp para a classe, ambos os ficheiros são abertos no separadores de grupo do Editor. Agora, atualize cada ficheiro para implementar a sua nova classe de observador:

   - Atualizar "filehandler_observer.h", ao selecionar/eliminar gerada `filehandler_observer` classe. **Não** remover as diretivas de pré-processamento geradas pelo passo anterior (#pragma, #include). Em seguida, copiar/colar seguinte origem para o ficheiro, após qualquer diretivas de pré-processamento existentes:

     ```cpp
     #include <memory>
     #include "mip/file/file_engine.h"
     #include "mip/file/file_handler.h"

     class FileHandlerObserver final : public mip::FileHandler::Observer {
     public:
        FileHandlerObserver() { }
        // Observer implementation
        void OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) override;
        void OnCreateFileHandlerFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
        void OnCommitSuccess(bool committed, const std::shared_ptr<void>& context) override;
        void OnCommitFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;       
     };
     ```

   - Atualizar "filehandler_observer.cpp", ao selecionar/eliminar gerada `filehandler_observer` implementação da classe. **Não** remover as diretivas de pré-processamento geradas pelo passo anterior (#pragma, #include). Em seguida, copiar/colar seguinte origem para o ficheiro, após qualquer diretivas de pré-processamento existentes:

     ```cpp
     void FileHandlerObserver::OnCreateFileHandlerSuccess(const std::shared_ptr<mip::FileHandler>& fileHandler, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
        promise->set_value(fileHandler);
     }

     void FileHandlerObserver::OnCreateFileHandlerFailure(const std::exception_ptr & error, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<std::shared_ptr<mip::FileHandler>>>(context);
        promise->set_exception(error);
     }

     void FileHandlerObserver::OnCommitSuccess(bool committed, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<bool>>(context);
        promise->set_value(committed);
     }

     void FileHandlerObserver::OnCommitFailure(const std::exception_ptr & error, const std::shared_ptr<void>& context) {
        auto promise = std::static_pointer_cast<std::promise<bool>>(context);
        promise->set_exception(error);
     }
     ```

4. Opcionalmente, utilize F6 (**compilar solução**) para executar um teste de compilação/de ligação da sua solução, para garantir que ela baseia-se com êxito antes de continuar.

## <a name="add-logic-to-set-and-get-a-sensitivity-label"></a>Adicione lógica para definir e obter uma etiqueta de sensibilidade

Adicione lógica para definir e obter uma etiqueta de sensibilidade num ficheiro, usando o objeto de motor de ficheiro. 

1. Usando **Explorador de soluções**, abra o ficheiro. cpp no projeto que contém a implementação do `main()` método. Por predefinição para o mesmo nome que o projeto que contém ele, que especificou durante a criação do projeto. 

2. Adicione as seguintes `#include` e `using` diretivas, abaixo as diretivas existentes correspondentes, na parte superior do ficheiro:

   ```cpp
   #include "filehandler_observer.h" 
   #include "mip/file/file_handler.h" 

   using mip::FileHandler;
   ```
3. Em direção ao final do corpo de `main()`, a seguir a `system("pause");`e acima a `return 0;` instruções (onde parou no início rápido anterior), insira o seguinte código:

   ```cpp
   // Set up async FileHandler for input file operations
   string filePathIn = "<input-file-path>";
   std::shared_ptr<FileHandler> handler;
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(filePathIn, mip::ContentState::REST, std::make_shared<FileHandlerObserver>(), handlerPromise);
        handler = handlerFuture.get();
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid input file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Set a label on input file
   try
   {
        string labelId = "<label-id>";
        cout << "\nApplying Label ID " << labelId << " to " << filePathIn << endl;
        mip::LabelingOptions labelingOptions(mip::AssignmentMethod::PRIVILEGED, mip::ActionSource::MANUAL);
        handler->SetLabel(labelId, labelingOptions);
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Commit changes, save as a different/output file
   string filePathOut = "<output-file-path>";
   try
   {
        cout << "Committing changes" << endl;
        auto commitPromise = std::make_shared<std::promise<bool>>();
        auto commitFuture = commitPromise->get_future();
        handler->CommitAsync(filePathOut, commitPromise);
        if (commitFuture.get()) {
            cout << "Label committed to file: " << filePathOut << endl;
        }
        else {
            cout << "Failed to label: " + filePathOut << endl;
            return 1;
        }
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid commit file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }
   system("pause");

   // Set up async FileHandler for output file operations
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(filePathOut, mip::ContentState::REST, std::make_shared<FileHandlerObserver>(), handlerPromise);
        handler = handlerFuture.get();
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid output file path?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }

   // Get the label from output file
   try
   {
        cout << "\nGetting label committed to file: " << filePathOut << endl;
        auto label = handler->GetLabel();
        cout << "Name: " + label->GetLabel()->GetName() << endl;
        cout << "Id: " + label->GetLabel()->GetId() << endl;
   }
   catch (const std::exception& e)
   {
        cout << "An exception occurred... did you specify a valid label ID?\n\n" << e.what() << "'\n";
        system("pause");
        return 1;
   }
   system("pause");
   ```

4. Substitua os valores de marcador de posição no código-fonte que acabou de colar, com os seguintes valores:

   | Marcador de posição | Valor |
   |:----------- |:----- |
   | \<caminho de ficheiro de entrada\> | O caminho completo para um teste de entrada ficheiro, por exemplo: `c:\\Test\\Test.docx`. |
   | \<id da etiqueta\> | Um ID de etiqueta de sensibilidade, copiados a partir da consola de saída no início rápido anterior, por exemplo: `f42a3342-8706-4288-bd31-ebb85995028z`. |
   | \<caminho de ficheiro de saída\> | O caminho completo para o ficheiro de saída, que será uma cópia com nome do ficheiro de entrada, por exemplo: `c:\\Test\\Test_labeled.docx`. |

## <a name="build-and-test-the-application"></a>Criar e testar a aplicação

Criar e testar a aplicação cliente. Se seu projeto baseia-se e é executada com êxito, deverá ver um resultado na janela da consola, semelhante ao seguinte exemplo: 

```cmd
Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
General : f42a3342-8706-4288-bd31-ebb85995028z
Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z
Press any key to continue . . .

Applying Label ID f42a3342-8706-4288-bd31-ebb85995028z to c:\Test\Test.docx
Committing changes
Label committed to file: c:\Test\Test_labeled.docx
Press any key to continue . . .

Getting label committed to file: c:\Test\Test_labeled.docx
Name: General
Id: f42a3342-8706-4288-bd31-ebb85995028z
Press any key to continue . . .
```

Pode verificar a aplicação da etiqueta, ao abrir o documento e inspecionar visualmente as definições de proteção de informações do documento.

> [!NOTE]
> Se estiver a etiquetagem um documento do Office, mas não estiver conectado com uma conta de inquilino do Azure Active Directory (AD) em que foi obtido o token de acesso (e rótulos de sensibilidade estão configurados), poderá ser solicitado para início de sessão antes de abrir o documento s popiskem. 



