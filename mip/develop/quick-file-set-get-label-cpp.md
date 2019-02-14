---
title: Início rápido - Set e get uma etiqueta de sensibilidade num arquivo usando o C++ MIP SDK
description: Um guia de introdução mostra-lhe como utilizar o SDK de C++ do Microsoft Information Protection para definir e obter uma etiqueta de sensibilidade num ficheiro.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.date: 01/18/2019
ms.author: bryanla
ms.openlocfilehash: 45263bc2a8f77f73f318b2c8df94f21e785e0f40
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256690"
---
# <a name="quickstart-set-and-get-a-sensitivity-label-c"></a>Início rápido: Definir e obter uma etiqueta de sensibilidade (C++)

Este guia de introdução mostra como usar mais de APIs de arquivo MIP. Utilizar uma das etiquetas de sensibilidade listados no início rápido anterior, utilize um manipulador de arquivo para definir/obter o rótulo num arquivo. O arquivo de classe de manipulador expõe várias operações para definição/obter etiquetas ou proteção, para tipos de ficheiro suportados.

## <a name="prerequisites"></a>Pré-requisitos

Se ainda não o fez, certifique-se de que concluir os seguintes pré-requisitos antes de continuar:

- Completa [início rápido: Listar etiquetas de sensibilidade (C++)](quick-file-list-labels-cpp.md) primeiro, que cria uma solução do Visual Studio, de arranque para listar as etiquetas de sensibilidade da organização. Isso "Set e get uma etiqueta de sensibilidade" Guia de introdução baseia-se no anterior.
- Opcionalmente: Revisão [manipuladores de ficheiros no SDK do MIP](concept-handler-file-cpp.md) conceitos.

## <a name="implement-an-observer-class-to-monitor-the-file-handler-object"></a>Implementar uma classe de observador para monitorizar o objeto do manipulador de arquivo

Semelhante para o observador é implementada (para o perfil de ficheiros e o mecanismo) na inicialização do aplicativo início rápido, agora implementa uma classe de observador para um objeto de manipulador de arquivo.

Criar uma implementação básica de um observador do manipulador de arquivo, ao expandir o SDK `mip::FileHandler::Observer` classe. O observador é instanciado e utilizado mais tarde, para monitorizar as operações de manipulador de arquivo.

1. Abra a solução do Visual Studio qual trabalhou num anterior "Guia de início rápido: Listar etiquetas de sensibilidade (C++) "artigo.

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
3. Próximo ao final dos `main()` body, veja a seguir `system("pause");` e acima `return 0;` (onde parou no início rápido anterior), insira o seguinte código:

   ```cpp
   // Set up async FileHandler for input file operations
   string filePathIn = "<input-file-path>";
   string contentIdentifier = "<content-identifier>";
   std::shared_ptr<FileHandler> handler;
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(
             filePathIn, 
             contentIdentifier,
             mip::ContentState::REST, 
             true, 
             std::make_shared<FileHandlerObserver>(), 
             handlerPromise);
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
            cout << "\nLabel committed to file: " << filePathOut << endl;
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
   contentIdentifier = "<content-identifier>";
   try
   {
        auto handlerPromise = std::make_shared<std::promise<std::shared_ptr<FileHandler>>>();
        auto handlerFuture = handlerPromise->get_future();
        engine->CreateFileHandlerAsync(
             filePathOut, 
             contentIdentifier,
             mip::ContentState::REST,
             true,
             std::make_shared<FileHandlerObserver>(),
             handlerPromise);

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
        cout << "\nGetting the label committed to file: " << filePathOut << endl;
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

4. Substitua os valores de marcador de posição no código-fonte que que acabou de colar na como a seguir, utilizar as constantes de cadeia de caracteres:

   | Marcador de posição | Valor |
   |:----------- |:----- |
   | \<input-file-path\> | O caminho completo para um teste de entrada ficheiro, por exemplo: `"c:\\Test\\Test.docx"`. |
   | \<content-identifier\> | Um identificador legível por humanos para o conteúdo. Por exemplo: <ul><li>para um ficheiro, considere path\filename: `"c:\Test\Test.docx"`</li><li>para uma mensagem de e-mail, considere o assunto: remetente: `"RE: Audit design:user1@contoso.com"`</li></ul> |
   | \<label-id\> | Um ID de etiqueta de sensibilidade, copiados a partir da consola de saída no início rápido anterior, por exemplo: `"f42a3342-8706-4288-bd31-ebb85995028z"`. |
   | \<output-file-path\> | O caminho completo para o ficheiro de saída, que será uma cópia com nome do ficheiro de entrada, por exemplo: `"c:\\Test\\Test_labeled.docx"`. |

## <a name="build-and-test-the-application"></a>Criar e testar a aplicação

Criar e testar a aplicação cliente. 

1. Utilizar F6 (**compilar solução**) para criar seu aplicativo de cliente. Não se tiver nenhum erro de compilação, use F5 (**iniciar a depuração**) para executar a sua aplicação.

2. Se seu projeto é compilado e é executada com êxito, o aplicativo solicita um token de acesso, cada vez que as chamadas SDK sua `AcquireOAuth2Token()` método. Como fez anteriormente a "Lista de etiquetas de sensibilidade" início rápido, execute o script do PowerShell para adquirir o token de cada vez, utilizando os valores fornecidos para $authority e $resourceUrl. 

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Sensitivity labels for your organization:
   Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
   Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
   General : f42a3342-8706-4288-bd31-ebb85995028z
   Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
   Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z
   Press any key to continue . . .

   Applying Label ID 074e457c-5848-4542-9a6f-34a182080e7z to c:\Test\Test.docx
   Committing changes

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Label committed to file: c:\Test\Test_labeled.docx
   Press any key to continue . . .

   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/94f69844-8d34-4794-bde4-3ac89ad2b664/oauth2/authorize
   Set $resourceUrl to: https://aadrm.com
   Sign in with user account: user1@tenant.onmicrosoft.com
   Enter access token: <paste-access-token-here>
   Press any key to continue . . .

   Getting the label committed to file: c:\Test\Test_labeled.docx
   Name: Confidential
   Id: 074e457c-5848-4542-9a6f-34a182080e7z
   Press any key to continue . . .
   ```

Pode verificar a aplicação da etiqueta, ao abrir o ficheiro de saída e inspecionar visualmente as definições de proteção de informações do documento.

> [!NOTE]
> Se estiver a etiquetagem um documento do Office, mas não estiver conectado com uma conta de inquilino do Azure Active Directory (AD) em que foi obtido o token de acesso (e rótulos de sensibilidade estão configurados), poderá ser solicitado para início de sessão antes de abrir o documento s popiskem. 



