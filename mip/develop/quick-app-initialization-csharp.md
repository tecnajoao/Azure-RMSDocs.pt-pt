---
title: Início rápido – inicialização para o Microsoft Information Protection (MIP) SDK C# clientes
description: Um guia de início rápido que mostra como escrever a lógica de inicialização para um Microsoft Information Protection (MIP) SDK C# aplicações cliente.
author: tommoser
ms.service: information-protection
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.date: 01/04/2019
ms.author: tommos
ms.openlocfilehash: 17c7bb1bd887b4009f450cb5bbf75900587de4f1
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252101"
---
# <a name="quickstart-client-application-initialization-c"></a>Início rápido: Inicialização de aplicações de cliente (C#)

Este início rápido mostram-lhe como implementar o padrão de inicialização do cliente, utilizado pelo wrapper de MIP SDK .NET em tempo de execução.

> [!NOTE]
> Os passos descritos neste guia de introdução são necessários para qualquer aplicativo de cliente que utiliza o wrapper de .NET de MIP ficheiro ou APIs de política. A API de proteção ainda não está disponível. Embora este início rápido demonstra a utilização das APIs de arquivo, esse mesmo padrão é aplicável a clientes que utilizam a política e as APIs de proteção. Inícios rápidos de futuros devem ser feitos em série, como cada um deles baseia-se na anterior, por este sendo a primeira.

## <a name="prerequisites"></a>Pré-requisitos

Se ainda não o fez, certifique-se de que para:

- Conclua os passos na [instalação do SDK de proteção de informações da Microsoft (MIP) e configuração](setup-configure-mip.md). Este "cliente inicialização de aplicações" Guia de introdução baseia-se na configuração e instalação correta do SDK.
- Opcionalmente:
  - Revisão [objetos de perfil e de motor](concept-profile-engine-cpp.md). Os objetos de perfil e de motor são conceitos de universais, necessários para os clientes que utilizam as APIs de MIP/políticas/proteção de ficheiros. 
  - Revisão [conceitos de autenticação](concept-authentication-cpp.md) para saber como a autenticação e autorização são implementadas pela aplicação cliente e do SDK.

## <a name="create-a-visual-studio-solution-and-project"></a>Criar uma solução do Visual Studio e o projeto

Primeiro, criar e configurar a solução do Visual Studio e o projeto, sobre a qual irão criar os inícios rápidos iniciais.

1. Abra o Visual Studio 2017, selecione o **arquivo** menu, **New**, **projeto**. Na **novo projeto** caixa de diálogo:
   - No painel esquerdo, sob **instalada**, **Visual C#** , selecione **Windows Desktop**.
   - No painel central, selecione **aplicação de consola (.NET Framework)**
   - No painel inferior, o projeto de atualização **Name**, **localização**e o que contém **nome da solução** em conformidade.
   - Quando terminar, clique nas **OK** botão na parte inferior direita. 

     [![Criação de solução do Visual Studio](media/quick-app-initialization-csharp/create-vs-solution.png)](media/quick-app-initialization-csharp/create-vs-solution.png#lightbox)

2. Adicione o pacote Nuget para a API de ficheiros do SDK MIP ao seu projeto:
   - Na **Explorador de soluções**, clique com o botão direito do rato no nó do projeto (diretamente sob o nó superior/solução) e selecione **gerir pacotes NuGet...** :
   - Quando o **Gestor de pacotes NuGet** é aberto um separador na área de separadores de grupo do Editor:
     - Selecione **procurar**.
     - Introduza "Microsoft.InformationProtection" na caixa de pesquisa.
     - Selecione o pacote "Microsoft.InformationProtection.File".
     - Clique em "Instalar", em seguida, clique em "OK" quando o **pré-visualizar alterações** apresenta a caixa de diálogo de confirmação.

3. Repita os passos acima para adicionar o pacote de API de ficheiros do SDK MIP, mas em vez disso, adicione "ActiveDirectory" para a aplicação.

## <a name="implement-an-authentication-delegate"></a>Implementar um delegado de autenticação

O SDK de MIP implementa a autenticação utilizando extensibility de classe, que fornece um mecanismo de partilhar o trabalho de autenticação com a aplicação de cliente. O cliente tem de adquirir um token de acesso de OAuth2 adequado e fornecer para o SDK de MIP em tempo de execução.

Agora, criar uma implementação para um delegado de autenticação, ao expandir o SDK `Microsoft.InformationProtection.IAuthDelegate` interface e substituindo/implementando o `IAuthDelegate.AcquireToken()` função virtual. O delegado de autenticação é instanciado e utilizado mais tarde, o `FileProfile` e `FileEngine` objetos.

1. Com o botão direito no nome do projeto no Visual Studio, selecione **Add** , em seguida, **classe**.
2. Introduza "AuthDelegateImplementation" a **nome** campo. Clique em **Adicionar**.
3. Adicione instruções "using" para o Active Directory Authentication Library (ADAL) e a biblioteca de MIP:

     ```csharp
     using Microsoft.InformationProtection;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     ```

4. Definir `AuthDelegateImplementation` herdar `Microsoft.InformationProtection.IAuthDelegate` e na implementação de uma variável particular de `Microsoft.InformationProtection.ApplicationInfo` e um construtor que aceita o mesmo tipo.

     ```csharp
     public class AuthDelegateImplementation : IAuthDelegate
     {
        private ApplicationInfo _appInfo;
        private string redirectUri = "mip-sdk-app://authorize";
        public AuthDelegateImplementation(ApplicationInfo appInfo)
        {
            _appInfo = appInfo;
        }
     }
     ```

O `ApplicationInfo` objeto contém duas propriedades. O `_appInfo.ApplicationId` vão ser utilizados no `AuthDelegateImplementation` classe para fornecer o ID de cliente para a biblioteca de autenticação.

5. Adicionar o `public string AcquireToken()` classe. Essa classe deve aceitar `Microsoft.InformationProtection.Identity`e duas cadeias de caracteres: autoridade e de recursos. Estas variáveis de cadeia de caracteres serão passados para a biblioteca de autenticação pela API e não devem ser manipulados. Edição pode resultar numa falha ao autenticar.

     ```csharp
     public string AcquireToken(Identity identity, string authority, string resource)
     {
          AuthenticationContext authContext = new AuthenticationContext(authority);
          var result = authContext.AcquireTokenAsync(resource, _appInfo.ApplicationId, new Uri(redirectUri), new PlatformParameters(PromptBehavior.Auto, null), UserIdentifier.AnyUser).Result;
          return result.AccessToken;
     }
     ```

## <a name="implement-a-consent-delegate"></a>Implementar um delegado de consentimento

Agora, criar uma implementação para um delegado de consentimento, ao expandir o SDK `Microsoft.InformationProtection.IConsentDelegate` interface e substituindo/implementar `GetUserConsent()`. O delegado de consentimento é instanciado e mais tarde, utilizado pelo perfil de ficheiros e objetos do mecanismo de ficheiro. O delegado de consentimento é fornecido com o endereço do serviço do utilizador tem de dar consentimento para utilizar no `url` parâmetro. O delegado em geral, deve fornecer um fluxo que permite ao utilizador aceitar ou rejeitar para dar consentimento para acessar o serviço. Para este início rápido embutir no código `Consent.Accept`.

1. Usando o mesmo recurso "Adicionar a classe" do Visual Studio utilizámos anteriormente, adicione outra classe ao seu projeto. Desta vez, introduza "ConsentDelegateImplementation" a **nome da classe** campo. 

2. Atualizar agora **ConsentDelegateImpl.cs** para implementar a sua nova classe de delegado de consentimento. Adicionar a utilizar a instrução para `Microsoft.InformationProtection` e defina a classe a herdar `IConsentDelegate`.

     ```csharp
     class ConsentDelegateImplementation : IConsentDelegate
     {
          public Consent GetUserConsent(string url)
          {
               return Consent.Accept;
          }
     }
     ```

3. Opcionalmente, tente criar a solução para garantir que ele seja compilado sem erros.

## <a name="initialize-the-mip-sdk-managed-wrapper"></a>Inicializar o invólucro gerenciado MIP SDK

1. Partir **Explorador de soluções**, abra o ficheiro. CS no seu projeto que contém a implementação do `Main()` método. Por predefinição para o mesmo nome que o projeto que contém ele, que especificou durante a criação do projeto.

2. Remover a implementação gerada de `main()`. 

3. O invólucro gerenciado inclui uma classe estática, `Microsoft.InformationProtection.MIP` utilizado para a inicialização, a carregar perfis e libertar recursos. Para inicializar o wrapper para operações de API de ficheiros, chame MIP. Initialize, passando `MipComponent.File` para carregar as bibliotecas necessárias para operações de ficheiros. 

4. Na `Main()` no *Program.cs* adicione o seguinte, substituindo **\<id de aplicação\>** com o ID do registo de aplicação do Azure AD criada anteriormente.

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.InformationProtection;
using Microsoft.InformationProtection.File;

namespace mip_sdk_dotnet_quickstart
{
    class Program
    {
        private const string clientId = "<application-id>";
        private const string appName = "<friendly-name>";

        static void Main(string[] args)
        {
            //Initialize Wrapper for File API operations 
            MIP.Initialize(MipComponent.File);
        }
    }
}
```

## <a name="construct-a-file-profile-and-engine"></a>Construir um perfil de ficheiros e de motor

Conforme mencionado, perfil e um mecanismo de objetos são necessários para clientes SDK usando APIs de MIP. Conclua a codificação parte deste início rápido, ao adicionar o código para carregar as DLLs nativas, em seguida, instancio os objetos de perfil e de motor.

   ```csharp
using System;
using System.Threading.Tasks;
using Microsoft.InformationProtection;
using Microsoft.InformationProtection.File;

namespace mip_sdk_dotnet_quickstart
{
     class Program
     {
          private const string clientId = "<application-id>";
          private const string appName = "<friendly-name>";

          static void Main(string[] args)
          {
               //Initialize Wrapper for File API operations
               MIP.Initialize(MipComponent.File);

               //Create ApplicationInfo, setting the clientID from Azure AD App Registration as the ApplicationId
               ApplicationInfo appInfo = new ApplicationInfo()
               {
                    ApplicationId = clientId,
                    ApplicationName = appName,
                    ApplicationVersion = "1.0.0"
               };

               //Instatiate the AuthDelegateImpl object, passing in AppInfo. 
               AuthDelegateImplementation authDelegate = new AuthDelegateImplementation(appInfo);

               //Initialize and instantiate the File Profile
               //Create the FileProfileSettings object
               var profileSettings = new FileProfileSettings("mip_data", false, authDelegate, new ConsentDelegateImplementation(), appInfo, LogLevel.Trace);

               //Load the Profile async and wait for the result
               var fileProfile = Task.Run(async () => await MIP.LoadFileProfileAsync(profileSettings)).Result;

               //Create a FileEngineSettings object, then use that to add an engine to the profile
               var engineSettings = new FileEngineSettings("user1@tenant.com", "", "en-US");
               engineSettings.Identity = new Identity("user1@tenant.com");
               var fileEngine = Task.Run(async () => await fileProfile.AddEngineAsync(engineSettings)).Result;
          }
     }
}
``` 

3. Substitua os valores de marcador de posição no código-fonte que colou, com os seguintes valores:

   | Marcador de posição | Valor | Exemplo |
   |:----------- |:----- |:--------|
   | \<application-id\> | O ID da aplicação do Azure AD atribuída à aplicação registado em "configuração de MIP SDK e configuração" (2 instâncias).  | 0edbblll-8773-44de-b87c-b8c6276d41eb |
   | \<friendly-name\> | Um nome amigável definido pelo utilizador para a sua aplicação. | AppInitialization |


4. Agora fazer uma compilação final do aplicativo e resolva quaisquer erros. Seu código deve criar com êxito.

## <a name="next-steps"></a>Próximos Passos

Agora que seu código de inicialização estiver concluído, está pronto para o próximo início rápido, onde começará experimentar as APIs de arquivo MIP.

> [!div class="nextstepaction"]
> [Etiquetas de sensibilidade da lista](quick-file-list-labels-csharp.md)
