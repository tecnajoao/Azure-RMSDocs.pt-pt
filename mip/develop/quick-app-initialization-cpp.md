---
title: Início rápido – inicialização para clientes de proteção de informações da Microsoft (MIP) SDK C++
description: Um guia de início rápido que mostra como escrever a lógica de inicialização para um cliente de proteção de informações da Microsoft (MIP) SDK de aplicações.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 01/18/2019
ms.author: bryanla
ms.openlocfilehash: 2fb19aa5071fa13f9801de9e9ed1106717f5adf9
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651433"
---
# <a name="quickstart-client-application-initialization-c"></a>Início rápido: Inicialização de aplicações de cliente (C++)

Este guia de introdução mostra-lhe como implementar o padrão de inicialização do cliente, utilizado pelo SDK C++ MIP em tempo de execução. 

> [!NOTE]
> Os passos descritos neste guia de introdução são necessários para qualquer aplicativo de cliente que utiliza o ficheiro de MIP, política ou as APIs de proteção. Embora este início rápido demonstra a utilização das APIs de arquivo, esse mesmo padrão é aplicável a clientes que utilizam a política e as APIs de proteção. Conclua os inícios rápidos restantes em série, como cada um deles baseia-se na anterior, por este sendo a primeira.

## <a name="prerequisites"></a>Pré-requisitos

Se ainda não o fez, certifique-se de que para:

- Conclua os passos na [instalação do SDK de proteção de informações da Microsoft (MIP) e configuração](setup-configure-mip.md). Este "cliente inicialização de aplicações" Guia de introdução baseia-se na configuração e instalação correta do SDK.
- Opcionalmente:
  - Revisão [objetos de perfil e de motor](concept-profile-engine-cpp.md). Os objetos de perfil e de motor são conceitos de universais, necessários para os clientes que utilizam as APIs de MIP/políticas/proteção de ficheiros. 
  - Revisão [conceitos de autenticação](concept-authentication-cpp.md) para saber como a autenticação e autorização são implementados com o SDK e o aplicativo cliente.
  - Revisão [conceitos de observador](concept-async-observers.md) para saber mais sobre observadores e como eles são implementados. O SDK de MIP utiliza o padrão observer implementar notificações de eventos assíncronos.

## <a name="create-a-visual-studio-solution-and-project"></a>Criar uma solução do Visual Studio e o projeto

Primeiro, criar e configurar a solução do Visual Studio e o projeto, sobre a qual criar outros guias de introdução iniciais. 

1. Abra o Visual Studio 2017, selecione o **arquivo** menu, **New**, **projeto**. Na **novo projeto** caixa de diálogo:
   - No painel esquerdo, sob **instalada**, **outras linguagens**, selecione **Visual C++**.
   - No painel central, selecione **aplicação de consola do Windows**
   - No painel inferior, o projeto de atualização **Name**, **localização**e o que contém **nome da solução** em conformidade.
   - Quando terminar, clique nas **OK** botão na parte inferior direita.

     [![Criação de solução do Visual Studio](media/quick-app-initialization-cpp/create-vs-solution.png)](media/quick-app-initialization-cpp/create-vs-solution.png#lightbox)

2. Adicione o pacote Nuget para a API de ficheiros do SDK MIP ao seu projeto:
   - Na **Explorador de soluções**, clique com o botão direito no nó do projeto (diretamente sob o nó superior/solução) e selecione **gerir pacotes NuGet...** :
   - Quando o **Gestor de pacotes NuGet** é aberto um separador na área de separadores de grupo do Editor:
     - Selecione **procurar**.
     - Introduza "Microsoft.InformationProtection" na caixa de pesquisa.
     - Selecione o pacote "Microsoft.InformationProtection.File".
     - Clique em "Instalar", em seguida, clique em "OK" quando o **pré-visualizar alterações** apresenta a caixa de diálogo de confirmação.
   
     [![Visual Studio adicionar o pacote NuGet](media/quick-app-initialization-cpp/add-nuget-package.png)](media/quick-app-initialization-cpp/add-nuget-package.png#lightbox)
 
## <a name="implement-an-observer-class-to-monitor-the-file-profile-and-engine-objects"></a>Implementar uma classe de observador para controlar os objetos de perfil e o mecanismo de ficheiro

Agora, crie uma implementação básica de uma classe de observador de perfil do ficheiro, ao expandir o SDK `mip::FileProfile::Observer` classe. O observador é instanciado e utilizado mais tarde, para monitorizar o carregamento do objeto de perfil do ficheiro e adicionar o objeto de motor para o perfil.

1. Adicione uma nova classe ao seu projeto, o que gera arquivos de cabeçalho /. h e de implementação /. cpp para:

   - Na **Explorador de soluções**, clique com botão direito no nó do projeto novamente, selecione **Add**, em seguida, selecione **classe**.
   - Sobre o **adicionar classe** caixa de diálogo:
     - Na **nome da classe** , insira "profile_observer". Tenha em atenção que tanto o **arquivo. h** e **arquivo. cpp** campos são automaticamente preenchidos, com base no nome que introduzir.
     - Quando terminar, clique nas **OK** botão.

     [![Visual Studio adicionar classe](media/quick-app-initialization-cpp/add-class.png)](media/quick-app-initialization-cpp/add-class.png#lightbox)

2. Depois de gerar os arquivos. h e. cpp para a classe, ambos os ficheiros são abertos no separadores de grupo do Editor. Agora, atualize cada ficheiro para implementar a sua nova classe de observador:

   - Atualizar "profile_observer.h", ao selecionar/eliminar gerada `profile_observer` classe. **Não** remover as diretivas de pré-processamento geradas pelo passo anterior (#pragma, #include). Em seguida, copiar/colar seguinte origem para o ficheiro, após qualquer diretivas de pré-processamento existentes:

     ```cpp
     #include <memory>
     #include "mip/file/file_profile.h"

     class ProfileObserver final : public mip::FileProfile::Observer {
     public:
          ProfileObserver() { }
          void OnLoadSuccess(const std::shared_ptr<mip::FileProfile>& profile, const std::shared_ptr<void>& context) override;
          void OnLoadFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
          void OnAddEngineSuccess(const std::shared_ptr<mip::FileEngine>& engine, const std::shared_ptr<void>& context) override;
          void OnAddEngineFailure(const std::exception_ptr& error, const std::shared_ptr<void>& context) override;
     };
     ```

   - Atualizar "profile_observer.cpp", ao selecionar/eliminar gerada `profile_observer` implementação da classe. **Não** remover as diretivas de pré-processamento geradas pelo passo anterior (#pragma, #include). Em seguida, copiar/colar seguinte origem para o ficheiro, após qualquer diretivas de pré-processamento existentes:

     ```cpp
     #include <future>

     using std::promise;
     using std::shared_ptr;
     using std::static_pointer_cast;
     using mip::FileEngine;
     using mip::FileProfile;

     void ProfileObserver::OnLoadSuccess(const shared_ptr<FileProfile>& profile, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileProfile>>>(context);
          promise->set_value(profile);
     }

     void ProfileObserver::OnLoadFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileProfile>>>(context);
          promise->set_exception(error);
     }

     void ProfileObserver::OnAddEngineSuccess(const shared_ptr<FileEngine>& engine, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileEngine>>>(context);
          promise->set_value(engine);
     }

     void ProfileObserver::OnAddEngineFailure(const std::exception_ptr& error, const shared_ptr<void>& context) {
          auto promise = static_pointer_cast<std::promise<shared_ptr<FileEngine>>>(context);
          promise->set_exception(error);
     }
     ```

3. Opcionalmente, utilize F6 (**compilar solução**) para executar um teste de compilação/de ligação da sua solução, para garantir que ela baseia-se com êxito antes de continuar.

## <a name="implement-an-authentication-delegate"></a>Implementar um delegado de autenticação

O SDK de MIP implementa a autenticação utilizando extensibility de classe, que fornece um mecanismo de partilhar o trabalho de autenticação com a aplicação de cliente. O cliente tem de adquirir um token de acesso de OAuth2 adequado e fornecer para o SDK de MIP em tempo de execução. 

Agora, criar uma implementação para um delegado de autenticação, ao expandir o SDK `mip::AuthDelegate` classe e substituindo/implementando o `mip::AuthDelegate::AcquireOAuth2Token()` função virtual pura. O delegado de autenticação é instanciado e mais tarde, utilizado pelo perfil de ficheiros e objetos do mecanismo de ficheiro.

1. Utilizar a funcionalidade de "Adicionar a classe" de Visual Studio mesmo que usamos passo #1 da secção anterior, adicione outra classe ao seu projeto. Desta vez, introduza "auth_delegate" a **nome da classe** campo. 

2. Agora, atualize cada ficheiro para implementar a sua nova classe de delegado de autenticação:

   - Atualizar "auth_delegate.h", ao substituir todos os gerado `auth_delegate` código com a seguinte origem de classe. **Não** remover as diretivas de pré-processamento geradas pelo passo anterior (#pragma, #include):

     ```cpp
     #include <string>
     #include "mip/common_types.h"

     class AuthDelegateImpl final : public mip::AuthDelegate {
     public:
          AuthDelegateImpl() = delete;        // Prevents default constructor
          
          AuthDelegateImpl(
            const std::string& appId)         // AppID for registered AAD app
            : mAppId(appId) {};

          bool AcquireOAuth2Token(            // Called by MIP SDK to get a token
            const mip::Identity& identity,    // Identity of the account to be authenticated, if known
            const OAuth2Challenge& challenge, // Authority (AAD tenant issuing token), and resource (API being accessed; "aud" claim).
            OAuth2Token& token) override;     // Token handed back to MIP SDK
     private:
          std::string mAppId;
          std::string mToken;
          std::string mAuthority;
          std::string mResource;
     };
     ```

   - Atualizar "auth_delegate.cpp", ao substituir todos os gerado `auth_delegate` implementação da classe com a seguinte origem. **Não** remover as diretivas de pré-processamento geradas pelo passo anterior (#pragma, #include). 

     > [!IMPORTANT]
     > O seguinte código de aquisição do token não é adequado para utilização em produção. Na produção, isso deve ser substituído por código dinamicamente recebe um token, usando:
     > - o appId e redirecionamento de resposta/URI especificado no seu registo de aplicação do Azure AD (resposta/URI de redirecionamento **tem** corresponde ao seu registo de aplicações)
     > - O URL de autoridade e de recursos transmitidos pelo SDK no `challenge` argumento (URL de recurso **tem** corresponde ao API/permissões seu registo de aplicações)
     > - Credenciais de utilizador/aplicação válido, em que a conta corresponde à `identity` argumento transmitido pelo SDK. Clientes de "nativos" OAuth2 devem solicitar credenciais de utilizador e utilizar o fluxo de "código de autorização". OAuth2 "clientes confidenciais" podem utilizar as suas próprias credenciais seguras com o fluxo de "credenciais de cliente" (como um serviço) ou solicitar credenciais de utilizador com o fluxo de "código de autorização" (por exemplo, uma aplicação web). 
     >
     > Aquisição de token OAuth2 é um protocolo complexo e normalmente feito usando uma biblioteca. Denomina-se TokenAcquireOAuth2Token() **apenas** pelo SDK MIP, conforme necessário.

     ```cpp
     #include <iostream>
     using std::cout;
     using std::cin;
     using std::string;

     bool AuthDelegateImpl::AcquireOAuth2Token(const mip::Identity& identity, const OAuth2Challenge& challenge, OAuth2Token& token) 
     {
          // Acquire a token manually, reuse previous token if same authority/resource. In production, replace with token acquisition code.
          string authority = challenge.GetAuthority();
          string resource = challenge.GetResource();
          if (mToken == "" || (authority != mAuthority || resource != mResource))
          {
              cout << "\nRun the PowerShell script to generate an access token using the following values, then copy/paste it below:\n";
              cout << "Set $authority to: " + authority + "\n";
              cout << "Set $resourceUrl to: " + resource + "\n";
              cout << "Sign in with user account: " + identity.GetEmail() + "\n";
              cout << "Enter access token: ";
              cin >> mToken;
              mAuthority = authority;
              mResource = resource;
              system("pause");
          }

          // Pass access token back to MIP SDK
          token.SetAccessToken(mToken);

          // True = successful token acquisition; False = failure
          return true;
     }
     ``` 
3. Opcionalmente, utilize F6 (**compilar solução**) para executar um teste de compilação/de ligação da sua solução, para garantir que ela baseia-se com êxito antes de continuar.

## <a name="implement-a-consent-delegate"></a>Implementar um delegado de consentimento

Agora, criar uma implementação para um delegado de consentimento, ao expandir o SDK `mip::ConsentDelegate` classe e substituindo/implementando o `mip::AuthDelegate::GetUserConsent()` função virtual pura. O delegado de consentimento é instanciado e mais tarde, utilizado pelo perfil de ficheiros e objetos do mecanismo de ficheiro.

1. Usando o mesmo recurso "Adicionar a classe" do Visual Studio utilizámos anteriormente, adicione outra classe ao seu projeto. Desta vez, introduza "consent_delegate" a **nome da classe** campo. 

2. Agora, atualize cada ficheiro para implementar a sua nova classe de delegado de consentimento:

   - Atualizar "consent_delegate.h", ao substituir todos os gerado `consent_delegate` código com a seguinte origem de classe. **Não** remover as diretivas de pré-processamento geradas pelo passo anterior (#pragma, #include):

     ```cpp
     #include "mip/common_types.h"
     #include <string>

     class ConsentDelegateImpl final : public mip::ConsentDelegate {
     public:
          ConsentDelegateImpl() = default;
          virtual mip::Consent GetUserConsent(const std::string& url) override;
     };
     ```

   - Atualizar "consent_delegate.cpp", ao substituir todos os gerado `consent_delegate` implementação da classe com a seguinte origem. **Não** remover as diretivas de pré-processamento geradas pelo passo anterior (#pragma, #include). 

     ```cpp
     #include <iostream>
     using mip::Consent;
     using std::string;

     Consent ConsentDelegateImpl::GetUserConsent(const string& url) 
     {
          // Accept the consent to connect to the url
          std::cout << "SDK will connect to: " << url << std::endl;
          return Consent::AcceptAlways;
     }
     ``` 
3. Opcionalmente, utilize F6 (**compilar solução**) para executar um teste de compilação/de ligação da sua solução, para garantir que ela baseia-se com êxito antes de continuar.

## <a name="construct-a-file-profile-and-engine"></a>Construir um perfil de ficheiros e de motor

Conforme mencionado, perfil e um mecanismo de objetos são necessários para clientes SDK usando APIs de MIP. Conclua a codificação parte deste início rápido, ao adicionar o código para instanciar os objetos de perfil e o mecanismo: 

1. Partir **Explorador de soluções**, abra o ficheiro. cpp no projeto que contém a implementação do `main()` método. Por predefinição para o mesmo nome que o projeto que contém ele, que especificou durante a criação do projeto.

2. Remover a implementação gerada de `main()`. **Não** remover diretivas de pré-processamento geradas pelo Visual Studio durante a criação do projeto (#pragma, #include). Acrescente o seguinte código após qualquer diretivas de pré-processamento:

   ```cpp
   #include "auth_delegate.h"
   #include "consent_delegate.h"
   #include "profile_observer.h"

   using std::promise;
   using std::future;
   using std::make_shared;
   using std::shared_ptr;
   using std::string;
   using std::cout;
   using mip::ApplicationInfo; 
   using mip::FileProfile;
   using mip::FileEngine;

   int main()
   {
     // Construct/initialize objects required by the application's profile object
     ApplicationInfo appInfo{"<application-id>",                    // ApplicationInfo object (App ID, name, version)
                 "<application-name>",
                 "<application-version>"};
     auto profileObserver = make_shared<ProfileObserver>();         // Observer object                  
     auto authDelegateImpl = make_shared<AuthDelegateImpl>(         // Authentication delegate object (App ID)
                 "<application-id>");
     auto consentDelegateImpl = make_shared<ConsentDelegateImpl>(); // Consent delegate object
 
     // Construct/initialize profile object
     FileProfile::Settings profileSettings("",    // Path for logging/telemetry/state
       true,                                      // true = use in-memory state storage (vs disk)
       authDelegateImpl,                            
       consentDelegateImpl,                     
       profileObserver,                         
       appInfo);                                    

     // Set up promise/future connection for async profile operations; load profile asynchronously
     auto profilePromise = make_shared<promise<shared_ptr<FileProfile>>>();
     auto profileFuture = profilePromise->get_future();
    try
    { 
        mip::FileProfile::LoadAsync(profileSettings, profilePromise);
    }
    catch (const std::exception& e)
    {
        cout << "An exception occurred... are the Settings and ApplicationInfo objects populated correctly?\n\n"
            << e.what() << "'\n";
        system("pause");
        return 1;

    }
    auto profile = profileFuture.get();

     // Construct/initialize engine object
     FileEngine::Settings engineSettings(
       mip::Identity("<engine-account>"),         // Engine identity (account used for authentication)
       "<engine-state>",                          // User-defined engine state      
       "en-US");                                  // Locale (default = en-US)

     // Set up promise/future connection for async engine operations; add engine to profile asynchronously
     auto enginePromise = make_shared<promise<shared_ptr<FileEngine>>>();
     auto engineFuture = enginePromise->get_future();
     profile->AddEngineAsync(engineSettings, enginePromise);
     std::shared_ptr<FileEngine> engine; 
     try
     {
       engine = engineFuture.get();             
     }
     catch (const std::exception& e)
     {
       cout << "An exception occurred... is the access token incorrect/expired?\n\n"
        << e.what() << "'\n";
       system("pause");
       return 1;
     }

   return 0;
   }
   ``` 

3. Substitua todos os valores de marcador de posição no código-fonte que acabou de colar, utilizar as constantes de cadeia de caracteres:

   | Marcador de posição | Valor | Exemplo |
   |:----------- |:----- |:--------|
   | \<application-id\> | O Azure AD Application ID (GUID) atribuído para a aplicação registada no [passo 2 de # de "definição de MIP SDK e configuração"](/information-protection/develop/setup-configure-mip#register-a-client-application-with-azure-active-directory) artigo. Substitua 2 instâncias. | `"0edbblll-8773-44de-b87c-b8c6276d41eb"` |
   | \<application-name\> | Um nome amigável definido pelo utilizador para a sua aplicação. Tem de conter carateres de ASCII válidos (excluindo ';') e o ideal é que corresponde ao nome da aplicação que utilizou no seu registo do Azure AD. | `"AppInitialization"` |
   | \<application-version\> | Informações de versão definido pelo utilizador para a sua aplicação. Tem de conter carateres de ASCII válidos (excluindo ';'). | `"1.1.0.0"` |
   | \<engine-account\> | A conta utilizada para de identidade o mecanismo. Quando se autentica com uma conta de utilizador durante a aquisição do token, este valor tem de corresponder. | `"user1@tenant.onmicrosoft.com"` |
   | \<engine-state\> | Estado definido pelo utilizador para ser associado com o motor. | `"My App State"` |


4. Agora fazer uma compilação final do aplicativo e resolva quaisquer erros. Seu código deve criar com êxito, mas não irá ainda funciona corretamente enquanto não concluir o próximo início rápido. Se executar o aplicativo, ver um resultado semelhante ao seguinte. Não terá um token de acesso para fornecer, até concluir o próximo início rápido.

   ```console
   Run the PowerShell script to generate an access token using the following values, then copy/paste it below:
   Set $authority to: https://login.windows.net/common/oauth2/authorize
   Set $resourceUrl to: https://syncservice.o365syncservice.com/
   Sign in with user account:
   Enter access token:
   ```

## <a name="next-steps"></a>Próximos Passos

Agora que seu código de inicialização estiver concluído, está pronto para o próximo início rápido, onde começará experimentar as APIs de arquivo MIP.

> [!div class="nextstepaction"]
> [Etiquetas de sensibilidade da lista](quick-file-list-labels-cpp.md)
