---
title: Início rápido - etiquetas de sensibilidade da lista de um inquilino de proteção de informações da Microsoft (MIP) usando C++ MIP SDK
description: Um guia de introdução mostra-lhe como utilizar o SDK de C++ do Microsoft Information Protection para listar as etiquetas de sensibilidade no seu inquilino.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 939f5a00fa63af1d6b34ca30b3fd1820bfed2d5b
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453457"
---
# <a name="quickstart-list-sensitivity-labels-c"></a>Início rápido: Listar etiquetas de sensibilidade (C++)

Este guia de introdução mostra-lhe como utilizar a API de ficheiros de MIP, para listar as etiquetas de sensibilidade configuradas para a sua organização.

## <a name="prerequisites"></a>Pré-requisitos

Se ainda não o fez, certifique-se de que concluir os seguintes pré-requisitos antes de continuar:

- Concluída [início rápido: inicialização de aplicações de cliente (C++)](quick-app-initialization-cpp.md) primeiro, que cria uma solução do Visual Studio de arranque. O guia de introdução de "Lista de etiquetas de sensibilidade" baseia-se na anterior, para a criação adequada da solução starter.
- Opcionalmente,: Reveja [etiquetas de classificação](concept-classification-labels.md) conceitos.

## <a name="add-logic-to-list-the-sensitivity-labels"></a>Adicione lógica para listar as etiquetas de sensibilidade

Adicione lógica para listar as etiquetas de sensibilidade da sua organização, usando o objeto de motor de ficheiro. 

1. Abra a solução do Visual Studio que criou no anterior "Guia de início rápido: inicialização de aplicações de cliente (C++)" artigo.

2. Usando **Explorador de soluções**, abra o ficheiro. cpp no projeto que contém a implementação do `main()` método. Por predefinição para o mesmo nome que o projeto que contém ele, que especificou durante a criação do projeto. 

3. Adicione as seguintes `using` diretiva após `using mip::FileEngine;`, junto à parte superior do ficheiro:

   ```cpp
   using std::endl;
   ```

4. Em direção ao final do corpo de `main()`, abaixo da chave de fechamento `}` da `catch` bloco e acima a `return 0;` instruções (onde parou no início rápido anterior), insira o seguinte código:

   ```cpp
   // List sensitivity labels
   auto labels = engine->ListSensitivityLabels();
   for (const auto& label : labels)
   {
      cout << label->GetName() << " : " << label->GetId() << endl;

      for (const auto& child : label->GetChildren())
      {
        cout << "->  " << child->GetName() << " : " << child->GetId() << endl;
      }
   }
   system("pause");
   ``` 

## <a name="update-the-token-acquisition-logic-with-a-valid-access-token"></a>Atualizar a lógica de aquisição do token com um token de acesso válido

Conforme indicado nos comentários do código, uma chamada para sua `AcquireOAuth2Token()` método é acionado pela chamada para `engineFuture.get()` chamar `main()`. Tem de concluir a implementação do `AcquireOAuth2Token()` método, para fornecer o token de acesso para o SDK de MIP.

1. Gere um token de teste usando o seguinte script do PowerShell. O script utiliza o `Get-ADALToken` cmdlet do módulo ADAL.PS instalou anteriormente, no MIP SDK instalação e configuração. 

   - Crie um ficheiro de Script do PowerShell (extensão. ps1) e copie/cole o seguinte script para o ficheiro:

     ```powershell
     $authority = 'https://login.windows.net/common/oauth2/authorize'  # Enforced by MIP SDK
     $resourceUrl = 'https://syncservice.o365syncservice.com/'         # Enforced by MIP SDK; matches the URL of the "Microsoft Information Protection Sync Service" resource/API requested by the Azure AD app registration
     $appId = '0edbblll-8773-44de-b87c-b8c6276d41eb'                   # App ID of the Azure AD app registration
     $redirectUri = 'bltest://authorize'                               # Must match the redirect URI of the Azure AD app registration
     $response = Get-ADALToken -Resource $resourceUrl -ClientId $appId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:RefreshSession 
     $response.AccessToken | clip                                      # Copies the access token text to the clipboard
     ```

   - Atualização do `$appId` e `redirectUri` variáveis, de acordo com os valores especificados no seu registo de aplicação do Azure AD.
   - Guarde o ficheiro de script e, em seguida, executá-lo com o PowerShell. O `Get-ADALToken` cmdlet aciona um prompt de autenticação do Azure AD, semelhante ao seguinte exemplo. Após o início de sessão com êxito, o token de acesso será colocado na área de transferência.

     [![Visual Studio adquirir o início de sessão token](media/quick-file-list-labels-cpp/acquire-token-sign-in.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in.png#lightbox)

   - Também poderá ser necessário dar consentimento, para permitir que a aplicação aceder às APIs do MIP, ao ser executado sob a conta de início de sessão. Isto acontece quando o registo de aplicação do Azure AD não está previamente dar o seu consentimento (conforme descrito em "configuração de MIP SDK e configuração") ou está a iniciar sessão com uma conta de um inquilino diferente (que não seja aquele em que a aplicação fica registada). Basta clicar **Accept** para registar o seu consentimento.

     [![Consentimento do Visual Studio](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png)](media/quick-file-list-labels-cpp/acquire-token-sign-in-consent.png#lightbox)

2. Imediatamente depois de concluir o passo #1 acima, retornar ao Visual Studio e utilizar **Explorador de soluções** para abrir o "auth_delegate.cpp". Desloque para baixo para sua `AcquireOAuth2Token()` implementação e encontrar a seguinte linha de código. Substitua o `<access-token>` marcador de posição, com o token colocado na área de transferência no passo anterior. O token deve ser uma cadeia longa, num formato semelhante a `eyJ0eXAiOi ...`.

   ```cpp
   string accessToken = "<access-token>";
   ``` 

## <a name="build-and-test-the-application"></a>Criar e testar a aplicação

Por fim, criar e testar a aplicação cliente. Se seu projeto baseia-se e é executada com êxito, deverá ver um resultado na janela da consola, semelhante ao seguinte exemplo:

```cmd
Non-Business : 87ba5c36-17cf-14793-bbc2-bd5b3a9f95cz
Public : 83867195-f2b8-2ac2-b0b6-6bb73cb33afz
General : f42a3342-8706-4288-bd31-ebb85995028z
Confidential : 074e457c-5848-4542-9a6f-34a182080e7z
Highly Confidential : f55c2dea-db0f-47cd-8520-a52e1590fb6z

Press any key to continue . . .
```

> [!NOTE]
> Copie e guarde o ID de um ou mais das etiquetas de sensibilidade (por exemplo, `f42a3342-8706-4288-bd31-ebb85995028z`), como irá usá-lo no próximo início rápido.

## <a name="troubleshooting"></a>Resolução de Problemas

### <a name="problems-during-execution-of-powershell-script"></a>Problemas durante a execução do script do PowerShell 

| Resumo | Mensagem de erro | Solução |
|---------|---------------|----------|
| Incorreto URI de redirecionamento no registo de aplicação ou script do PowerShell (AADSTS50011) |*AADSTS50011: Resposta de url especificado no pedido não coincide com os urls de resposta configurados para a aplicação: 'ac6348d6-0d2f-4786-af33-07ad46e69bfc'.* | Verifique se o redirecionamento do URI a ser utilizado, concluindo um dos seguintes passos:<br><br><li>Atualize o URI de redirecionamento na configuração da sua aplicação do Azure AD, de acordo com o script do PowerShell. Ver [MIP SDK instalação e configuração](setup-configure-mip.md#register-a-client-application-with-azure-active-directory) para verificar que configurou corretamente a propriedade de URI de redirecionamento.<br><li>Atualização do `redirectUri` variáveis no script do PowerShell, de acordo com o registo de aplicação. |
| Início de sessão conta incorreta (AADSTS50020) | *AADSTS50020: Conta de utilizador 'user@domain.com"de provedor de identidade"https://sts.windows.net/72f988bl-86f1-41af-91ab-2d7cd011db47/' não existe no inquilino 'Nome da organização' e não é possível acessar o aplicativo "0edbblll-8773-44de-b87c-b8c6276d41eb" nesse inquilino.* | Execute um dos seguintes passos:<br><br><li>Volte a executar o script do PowerShell, mas não se esqueça de utilizar uma conta a partir do mesmo inquilino onde a sua aplicação do Azure AD está registrada.<br><li>Se a sua conta de início de sessão foi correta, a sessão de anfitrião do PowerShell já pode ser autenticada com uma conta diferente. Neste caso, saída, em seguida, reabra o host do script, em seguida, tente executá-lo novamente.<br><li>Se estiver a utilizar este guia de introdução com uma aplicação web (em vez de nativo) e tem de iniciar sessão com uma conta de um inquilino diferente, certifique-se de que o registo de aplicação do Azure AD está ativado para a utilização do multi-inquilino. Pode verificar através da funcionalidade de "Editar manifesto" do registo de aplicação e certifique-se de que especifica `"availableToOtherTenants": true,`. |
| Permissões incorretas no registo de aplicação (AADSTS65005) | *AADSTS65005: Recurso é inválida. O cliente pediu acesso a um recurso que não está listado nas permissões pedidas no registo de aplicação do cliente. ID de aplicação de cliente: 0edbblll-8773-44de-b87c-b8c6276d41eb. Valor do recurso do pedido: https://syncservice.o365syncservice.com/. ID de aplicação de recurso: 870c4f2e-85b6 - 4d 43-bdda-6ed9a579b725. Lista de recursos válidos do registo de aplicações: 00000002-0000-0000-c000-000000000000.* | Atualize as solicitações de permissão na configuração da sua aplicação do Azure AD. Ver [MIP SDK instalação e configuração](setup-configure-mip.md#register-a-client-application-with-azure-active-directory) para verificar que configurou corretamente os pedidos de permissão no seu registo de aplicação. |

### <a name="problems-during-execution-of-c-application"></a>Problemas durante a execução do aplicativo em C++

| Resumo | Mensagem de erro | Solução |
|---------|---------------|----------|
| Token de acesso incorreto | *Ocorreu uma exceção... é o token de acesso incorreto/expirado? <br> <br>Chamada à API falhou: profile_add_engine_async falhou com o: [classe mip::PolicySyncException] Falha na aquisição de política, o pedido falhou com o código de estado http: 401, x-ms-diagnostics: [2000001; motivo = "OAuth token submetido com Não é possível analisar o pedido. "; error_category = "invalid_token"], correlationId: [35bc0023-3727-4eff-8062-000006d5d672]'<br><br>C:\VSProjects\MipDev\Quickstarts\AppInitialization\x64\Debug\AppInitialization.exe (processo 29924) foi terminado com o código de 0.<br> <br>Pressione qualquer tecla para fechar esta janela...* | Se seu projeto é compilado com êxito, mas ver um resultado semelhante à esquerda, provavelmente terá um token inválido ou expirou sua `AcquireOAuth2Token()` método. Volte ao [a lógica de aquisição do token de atualização](#update-the-token-acquisition-logic-with-a-valid-access-token) e voltar a gerar a atualização de token, acesso `AcquireOAuth2Token()` novamente e reconstrução/teste novamente. Também pode examinar e verifique se o token e às declarações, utilizar o [jwt.ms](https://jwt.ms/) aplicativo web de página única. |
| Etiquetas de sensibilidade não estão configuradas | n/d | Se seu projeto é compilado com êxito, mas não tiver nenhuma saída na janela do console, certifique-se de que as etiquetas de sensibilidade da sua organização estão configuradas corretamente. Ver [MIP SDK instalação e configuração](setup-configure-mip.md), em "Definir definições de proteção e de taxonomia de etiquetas" para obter detalhes.  |

## <a name="next-steps"></a>Passos Seguintes

Agora que aprendeu como listar as etiquetas de sensibilidade para a sua organização, experimente o próximo início rápido:

> [!div class="nextstepaction"]
> [Definir e obter uma etiqueta de sensibilidade](quick-file-set-get-label-cpp.md)
