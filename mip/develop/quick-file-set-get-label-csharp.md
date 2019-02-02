---
title: Início rápido - Set e get uma etiqueta de sensibilidade um ficheiro com o C# SDK de MIP
description: Um guia de introdução mostra-lhe como utilizar o Wrapper de .NET SDK de proteção de informações de Microsoft para definir e obter uma etiqueta de sensibilidade num ficheiro.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 01/09/2019
ms.author: bryanla
ms.openlocfilehash: 726f0cf5b3c087d21323b46c9b7748b545932428
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651967"
---
# <a name="quickstart-set-and-get-a-sensitivity-label-c"></a>Início rápido: Definir e obter uma etiqueta de sensibilidade (C#)

Este guia de introdução mostra como usar mais de APIs de arquivo MIP. Utilizar uma das etiquetas de sensibilidade listados no início rápido anterior, utilize um manipulador de arquivo para definir/obter o rótulo num arquivo. O arquivo de classe de manipulador expõe várias operações para definição/obter etiquetas ou proteção, para tipos de ficheiro suportados.

## <a name="prerequisites"></a>Pré-requisitos

Se ainda não o fez, certifique-se de que concluir os seguintes pré-requisitos antes de continuar:

- Completa [início rápido: Listar etiquetas de sensibilidade (C#)](quick-file-list-labels-csharp.md) primeiro, que cria uma solução do Visual Studio, de arranque para listar as etiquetas de sensibilidade da organização. Isso "Set e get uma etiqueta de sensibilidade" Guia de introdução baseia-se no anterior.
- Opcionalmente: Revisão [manipuladores de ficheiros no SDK do MIP](concept-handler-file-cpp.md) conceitos.

## <a name="add-logic-to-set-and-get-a-sensitivity-label"></a>Adicione lógica para definir e obter uma etiqueta de sensibilidade

Adicione lógica para definir e obter uma etiqueta de sensibilidade num ficheiro, usando o objeto de motor de ficheiro. 

1. Usando **Explorador de soluções**, abra o ficheiro. CS no seu projeto que contém a implementação do Main () ' método. Por predefinição para o mesmo nome que o projeto que contém ele, que especificou durante a criação do projeto. 

2. Próximo ao final dos `Main()` body, veja a seguir `Console.ReadKey()` e acima `}` (onde parou no início rápido anterior), insira o seguinte código:

   ```csharp
     //Set paths and label ID
     string inputFilePath = "<input-file-path>";
     string labelId = "<label-id>";
     string outputFilePath = "<output-file-path>";

     //Create a file handler for that file
     //Note: the 2nd inputFilePath is used to provide a human-readable content identifier for admin auditing. 
     var handler = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(inputFilePath, inputFilePath, ContentState.Rest, true)).Result;

     //Set Labeling Options
     LabelingOptions labelingOptions = new LabelingOptions()
     {
          ActionSource = ActionSource.Manual,
          AssignmentMethod = AssignmentMethod.Standard
     };

     // Set a label on input file
     handler.SetLabel(labelId, labelingOptions);

     // Commit changes, save as outputFilePath
     var result = Task.Run(async () => await handler.CommitAsync(outputFilePath)).Result;

     // Create a new handler to read the labeled file metadata
     var handlerModified = Task.Run(async () => await fileEngine.CreateFileHandlerAsync(outputFilePath, outputFilePath, ContentState.Rest, true)).Result;

     // Get the label from output file
     var contentLabel = handlerModified.Label;
     Console.WriteLine(string.Format("Getting the label committed to file: {0}", outputFilePath));
     Console.WriteLine(string.Format("File Label: {0} \r\nIsProtected: {1}", contentLabel.Label, contentLabel.IsProtectionAppliedFromLabel.ToString()));
     Console.WriteLine("Press a key to continue.");
     Console.ReadKey();
   ```

3. Substitua os valores de marcador de posição no código-fonte que acabou de colar, com os seguintes valores:

   | Marcador de posição | Valor |
   |:----------- |:----- |
   | \<input-file-path\> | O caminho completo para um teste de entrada ficheiro, por exemplo: `c:\\Test\\Test.docx`. |
   | \<label-id\> | Um ID de etiqueta de sensibilidade, copiados a partir da consola de saída no início rápido anterior, por exemplo: `f42a3342-8706-4288-bd31-ebb85995028z`. |
   | \<output-file-path\> | O caminho completo para o ficheiro de saída, que será uma cópia com nome do ficheiro de entrada, por exemplo: `c:\\Test\\Test_labeled.docx`. |

## <a name="build-and-test-the-application"></a>Criar e testar a aplicação

Criar e testar a aplicação cliente. 

1. Utilize CTRL-SHIFT-B (**compilar solução**) para criar seu aplicativo de cliente. Não se tiver nenhum erro de compilação, use F5 (**iniciar a depuração**) para executar a sua aplicação.

2. Se o seu projeto baseia-se e é executada com êxito, o aplicativo *poderá* as chamadas do SDK de tempo do pedido de autenticação através da ADAL cada sua `AcquireToken()` método. Se já existirem credenciais em cache, não será pedido para iniciar sessão e ver a lista de etiquetas, seguido as informações sobre a etiqueta aplicada e modificar o ficheiro.

  ```console   
  Personal : 73c47c6a-eb00-4a6a-8e19-efaada66dee6
  Public : 73254501-3d5b-4426-979a-657881dfcb1e
  General : da480625-e536-430a-9a9e-028d16a29c59
  Confidential : 569af77e-61ea-4deb-b7e6-79dc73653959
        Recipients Only (C) : d98c4267-727b-430e-a2d9-4181ca5265b0
        All Employees (C) : 2096f6a2-d2f7-48be-b329-b73aaa526e5d
        Anyone (not protected) (C) : 63a945ec-1131-420d-80da-2fedd15d3bc0
  Highly Confidential : 905845d6-b548-439c-9ce5-73b2e06be157
        Recipients Only : 05ee72d9-1a75-441f-94e2-dca5cacfe012
        All Employees : 922b06ef-044b-44a3-a8aa-df12509d1bfe
        Anyone (not protected) : c83fc820-961d-40d4-ba12-c63f72a970a3
  Press a key to continue.

   Applying Label ID 074e457c-5848-4542-9a6f-34a182080e7z to c:\Test\Test.docx
   Committing changes
   
   Label committed to file: c:\Test\Test_labeled.docx
   Press any key to continue . . .
  
   Getting the label committed to file: c:\Test\Test_labeled.docx
   Name: Confidential
   Id: 074e457c-5848-4542-9a6f-34a182080e7z
   Press any key to continue . . .
   ```

Pode verificar a aplicação da etiqueta, ao abrir o ficheiro de saída e inspecionar visualmente as definições de proteção de informações do documento.

> [!NOTE]
> Se estiver a etiquetagem um documento do Office, mas não estiver conectado com uma conta de inquilino do Azure Active Directory (AD) em que foi obtido o token de acesso (e rótulos de sensibilidade estão configurados), poderá ser solicitado para início de sessão antes de abrir o documento s popiskem. 
