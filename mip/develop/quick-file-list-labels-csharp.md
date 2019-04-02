---
title: Início rápido - etiquetas de sensibilidade da lista de um inquilino de proteção de informações da Microsoft (MIP) com o SDK de MIP C# Wrapper
description: Um guia de introdução mostra-lhe como utilizar o SDK do Microsoft Information Protection C# wrapper para listar as etiquetas de sensibilidade no seu inquilino.
author: msmbaldwin
ms.service: information-protection
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.date: 01/04/2019
ms.author: mbaldwin
ms.openlocfilehash: 0b1b110fe3b2e96c258c7b94a3d356b9404d6e7e
ms.sourcegitcommit: 8da0aa8f9bb9f91375580a703682d23a81a441bf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58809748"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>Início rápido: List sensitivity labels (C#) (Listar etiquetas de confidencialidade [C#])

Este guia de introdução mostra-lhe como utilizar a API de ficheiros do SDK MIP para listar as etiquetas de sensibilidade configuradas para a sua organização.

## <a name="prerequisites"></a>Pré-requisitos

Se ainda não o fez, certifique-se de que concluir os seguintes pré-requisitos antes de continuar:

- Completa [início rápido: Inicialização de aplicações de cliente (C#)](quick-app-initialization-csharp.md) primeiro, que cria uma solução do Visual Studio de arranque. Este guia de introdução de "Lista de etiquetas de sensibilidade" baseia-se na anterior, para a criação adequada da solução starter.
- Opcionalmente: Revisão [etiquetas de classificação](concept-classification-labels.md) conceitos.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>Adicione lógica para listar as etiquetas de sensibilidade

Adicione lógica para listar as etiquetas de sensibilidade da sua organização, usando o objeto de motor de ficheiro. 

1. Abra a solução do Visual Studio que criou no anterior "Guia de início rápido: Inicialização de aplicações de cliente (C#) "artigo.

2. Usando **Explorador de soluções**, abra o ficheiro. CS no seu projeto que contém a implementação do `Main()` método. Por predefinição para o mesmo nome que o projeto que contém ele, que especificou durante a criação do projeto. 

3. Próximo ao final dos `Main()` corpo, abaixo da chave de fechamento `}` do `Main()` função (onde parou no início rápido anterior), insira o seguinte código:

  ```csharp
  // List sensitivity labels from fileEngine and display name and id  
  foreach(var label in fileEngine.SensitivityLabels)
  {
      Console.WriteLine(string.Format("{0} : {1}", label.Name, label.Id));

      if (label.Children.Count != 0)
      {
          foreach (var child in label.Children)
          {
              Console.WriteLine(string.Format("{0}{1} : {2}", "\t",child.Name, child.Id));
          }
      }
  }
  ``` 

## <a name="build-and-test-the-application"></a>Criar e testar a aplicação

Por fim, criar e testar a aplicação cliente. 

1. Utilize CTRL-SHIFT-B (**compilar solução**) para criar seu aplicativo de cliente. Não se tiver nenhum erro de compilação, use F5 (**iniciar a depuração**) para executar a sua aplicação.

2. Se o seu projeto baseia-se e é executada com êxito, o aplicativo *poderá* as chamadas do SDK de tempo do pedido de autenticação através da ADAL cada sua `AcquireToken()` método. Se já existirem credenciais em cache, não serão solicitadas para iniciar sessão e ver a lista de etiquetas. 

     [![Visual Studio adquirir o início de sessão token](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Também poderá ser necessário dar consentimento, para permitir que a aplicação aceder às APIs do MIP, ao ser executado sob a conta de início de sessão. Isto acontece quando o registo de aplicação do Azure AD não está previamente dar o seu consentimento (conforme descrito em "configuração de MIP SDK e configuração") ou está a iniciar sessão com uma conta de um inquilino diferente (que não seja aquele em que a aplicação fica registada). Basta clicar **Accept** para registar o seu consentimento.

     [![Consentimento do Visual Studio](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

3. Após a autenticação, a saída do console deve mostrar os rótulos de sensibilidade, semelhantes ao seguinte exemplo:

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
  ```

   > [!NOTE]
   > Copie e guarde o ID de um ou mais das etiquetas de sensibilidade (por exemplo, `f42a3342-8706-4288-bd31-ebb85995028z`), como irá usá-lo no próximo início rápido.

## <a name="troubleshooting"></a>Resolução de problemas

### <a name="problems-during-execution-of-c-application"></a>Problemas durante a execução do C# aplicação

| Resumo | Mensagem de erro | Solução |
|---------|---------------|----------|
| Token de acesso incorreto | *Ocorreu uma exceção... é o token de acesso incorreto/expirado? <br> <br>Chamada à API falhou: profile_add_engine_async falhou com o: [classe mip::PolicySyncException] Falha na aquisição de política, o pedido falhou com o código de estado http: 401, x-ms-diagnostics: [2000001; motivo = "submetida com o pedido de token de OAuth não é possível analisar."; error_category = "invalid_token"], correlationId: [35bc0023-3727-4eff-8062-000006d5d672]'<br><br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (processo 29924) foi terminado com o código de 0.<br> <br>Pressione qualquer tecla para fechar esta janela...* | Se seu projeto é compilado com êxito, mas ver um resultado semelhante à esquerda, provavelmente terá um token inválido ou expirou sua `AcquireOAuth2Token()` método. Volte ao [criar e testar o aplicativo](#build-and-test-the-application) e voltar a gerar a atualização de token, acesso `AcquireOAuth2Token()` novamente e reconstrução/teste novamente. Também pode examinar e verifique se o token e às declarações, utilizar o [jwt.ms](https://jwt.ms/) aplicativo web de página única. |
| Etiquetas de sensibilidade não estão configuradas | n/d | Se seu projeto é compilado com êxito, mas não tiver nenhuma saída na janela do console, certifique-se de que as etiquetas de sensibilidade da sua organização estão configuradas corretamente. Ver [MIP SDK instalação e configuração](setup-configure-mip.md), em "Definir definições de proteção e de taxonomia de etiquetas" para obter detalhes.  |

## <a name="next-steps"></a>Próximos Passos

Agora que aprendeu como listar as etiquetas de sensibilidade para a sua organização, experimente o próximo início rápido:

> [!div class="nextstepaction"]
> [Definir e obter uma etiqueta de sensibilidade](quick-file-set-get-label-csharp.md)
