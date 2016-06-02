---
# required metadata

title: Como&#58; adicionar autenticação à sua aplicação | Azure RMS
description: Descreve as noções básicas da autenticação de utilizador para a sua aplicação com capacidade para RMS.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 200D9B23-F35D-4165-9AC4-C482A5CE1D28
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Como: adicionar autenticação à sua aplicação

Este tópico descreve as noções básicas da autenticação de utilizador para a sua aplicação com capacidade para RMS.

## O que é a autenticação de utilizador
A autenticação de utilizador é um passo essencial para estabelecer a comunicação entre a aplicação do dispositivo e a infraestrutura de RMS. Este processo de autenticação utiliza o protocolo OAuth 2.0 padrão que requer as seguintes informações acerca do utilizador atual e do seu pedido de autenticação; **authority**, **resource** e **userId**.

**Nota** O âmbito não é utilizado atualmente mas poderá ser e, por isso, está reservado para utilização futura.

 

**Chamada de retorno de autenticação de utilizador** – O SDK Microsoft Rights Management 4.2 utilizará a sua implementação de uma chamada de retorno de autenticação quando o utilizador não fornecer um token de acesso, quando o seu token de acesso necessitar de ser atualizado ou quando o token de acesso tiver expirado.

Cada uma das APIs do RMS da plataforma tem uma chamada de retorno que tem de implementar para ativar a autenticação do utilizador.

-   A API do Android utiliza as interfaces [**AuthenticationRequestCallback**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_authenticationrequestcallback_interface_java) e [**AuthenticationCompletionCallback**](/rights-management/sdk/4.2/api/android/authenticationcompletioncallback#msipcthin2_authenticationcompletioncallback_interface_java).
-   A API do iOS/OS X utiliza o protocolo [**MSAuthenticationCallback**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msauthenticationcallback_protocol_objc).
-   A API do WinPhone utiliza a interface [**IAuthenticationCallback**](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement#msipcthin2_iauthenticationcallback).
-   A API do Linux utiliza a interface [IAuthenticationCallback](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1IAuthenticationCallback.html).

## Qual biblioteca utilizar para a autenticação

Para poder implementar a sua chamada de retorno de autenticação, terá de transferir uma biblioteca adequada e configurar o ambiente de desenvolvimento para utilizá-la. Poderá encontrar no GitHub, as bibliotecas ADAL para estas plataformas. Cada um dos seguintes recursos contém orientações sobre a configuração do ambiente e a utilização da biblioteca.

-   [Windows Azure Active Directory Authentication Library (ADAL) para iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Windows Azure Active Directory Authentication Library (ADAL) para Mac](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Windows Azure Active Directory Authentication Library (ADAL) para Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)
-   [Windows Azure Active Directory Authentication Library (ADAL) para dotnet](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)
-   Para o SDK Linux, a biblioteca ADAL é compactada com a origem do SDK, disponível através do [Github](https://github.com/AzureAD/rms-sdk-for-cpp).

**Nota** Recomendamos que utilize uma das bibliotecas Active Directory Authentication Library (ADAL) acima, embora possa utilizar outras bibliotecas de autenticação.

## Entradas de autenticação com Azure Active Director Authentication Library (ADAL)

A ADAL requer vários parâmetros para autenticar com êxito um utilizador no Azure RMS (ou AD RMS). Estes são os parâmetros OAuth 2.0 padrão que normalmente são necessários em qualquer aplicação Azure AD, tal como em aplicações com capacidade para RMS. Pode encontrar as diretrizes atuais para a utilização da ADAL no ficheiro LEIA-ME dos repositórios do Github correspondentes, listados anteriormente.

Estes parâmetros e diretrizes são necessários para os fluxos de trabalho do RMS:

-   **Autoridade** – o URL para o ponto final de autenticação, normalmente AAD ou ADFS. Este parâmetro é fornecido para a sua aplicação através da chamada de retorno de autenticação do SDK RMS.
-   **Recurso** – o URL/URI da aplicação de serviço à qual está a tentar aceder, normalmente, o Azure RMS ou o AD RMS. Este parâmetro é fornecido para a sua aplicação através da chamada de retorno de autenticação do SDK RMS.
-   **ID de Utilizador** – o UPN, normalmente o endereço de e-mail do utilizador que pretende aceder à aplicação. Este parâmetro pode estar vazio se o utilizador ainda não for conhecido e também é utilizado para colocar em cache o token de utilizador ou pedir um token a partir da cache. Isto também é geralmente utilizado como uma “sugestão” para consultar o utilizador.
-   **ID de Cliente** – a ID da aplicação de cliente. Tem de ser uma ID da aplicação válida do Azure AD. Para obter mais informações, consulte Como: obter uma ID da Aplicação Azure.
-   **URI de Redirecionamento** – fornece a biblioteca de autenticação com um destino URI para o código de autenticação. Tenha em atenção que são necessários formatos específicos para iOS e Android (explicados nos ficheiros LEIA-ME dos repositórios de GitHub correspondentes da ADAL).

    Android: `msauth://packagename/Base64UrlencodedSignature`

    iOS. `<app-scheme>://<bundle-id>`

**Nota** Se a aplicação não seguir estas diretrizes, é provável que os fluxos de trabalho do Azure RMS e do Azure AD falhem e não sejam suportados pela Microsoft.com. Além disso, o Contrato de Licença de Rights Management (RMLA) pode ser violado se uma ID de Cliente inválida for utilizada numa aplicação de produção.

## Qual deverá ser o aspeto de uma implementação de chamada de retorno de autenticação

**Exemplos de Código de Autenticação** – Este SDK tem o código de exemplo que mostra a utilização de chamadas de retorno de autenticação. Para comodidade do utilizador, estes exemplos de código são representados aqui, bem como em cada um dos seguintes tópicos relacionados.

**Autenticação de utilizador do Android** – para obter mais informações, consulte [Exemplos de código do Android](android-code.md), **Passo 2** do primeiro cenário, “Consumir um ficheiro protegido por RMS”.


    class MsipcAuthenticationCallback implements AuthenticationRequestCallback
    {
    ...

    @Override
    public void getToken(Map<String, String> authenticationParametersMap,
                         final AuthenticationCompletionCallback authenticationCompletionCallbackToMsipc)
    {
        String authority = authenticationParametersMap.get("oauth2.authority");
        String resource = authenticationParametersMap.get("oauth2.resource");
        String userId = authenticationParametersMap.get("userId");
        mClientId = “12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”; // get your registered Azure AD application ID here
        mRedirectUri = “urn:ietf:wg:oauth:2.0:oob”;
        final String userHint = (userId == null)? "" : userId;
        AuthenticationContext authenticationContext = App.getInstance().getAuthenticationContext();
        if (authenticationContext == null || !authenticationContext.getAuthority().equalsIgnoreCase(authority))
        {
            try
            {
                authenticationContext = new AuthenticationContext(App.getInstance().getApplicationContext(), authority, …);
                App.getInstance().setAuthenticationContext(authenticationContext);
            }
            catch (NoSuchAlgorithmException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
            catch (NoSuchPaddingException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
       }
        App.getInstance().getAuthenticationContext().acquireToken(mParentActivity, resource, mClientId, mRedirectURI, userId, mPromptBehavior,
                       "&USERNAME=" + userHint, new AuthenticationCallback<AuthenticationResult>()
                        {
                            @Override
                            public void onError(Exception exc)
                            {
                                …
                                if (exc instanceof AuthenticationCancelError)
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onCancel();
                                }
                                else
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onFailure();
                                }
                            }

                            @Override
                            public void onSuccess(AuthenticationResult result)
                            {
                                …
                                if (result == null || result.getAccessToken() == null
                                        || result.getAccessToken().isEmpty())
                                {
                                     …
                                }
                                else
                                {
                                    // request is successful
                                    …
                                    authenticationCompletionCallbackToMsipc.onSuccess(result.getAccessToken());
                                }
                            }
                        });
                         }


**Autenticação de utilizador do iOS/OS X** – para obter mais informações, consulte [Exemplos de código do iOS/OS X](ios-os-x-code-examples.md),

**Passo 2** do primeiro cenário, “Consumir um ficheiro protegido por RMS”.


    // AuthenticationCallback holds the necessary information to retrieve an access token.
    @interface MsipcAuthenticationCallback : NSObject<MSAuthenticationCallback>

    @end

    @implementation MsipcAuthenticationCallback

    - (void)accessTokenWithAuthenticationParameters:
         (MSAuthenticationParameters *)authenticationParameters
                                completionBlock:
         (void(^)(NSString *accessToken, NSError *error))completionBlock
    {
    ADAuthenticationError *error;
    ADAuthenticationContext* context = [ADAuthenticationContext authenticationContextWithAuthority:authenticationParameters.authority error:&error];

    NSString *appClientId = @”12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”;

    // get your registered Azure AD application ID here

    NSURL *redirectURI = [NSURL URLWithString:@”ms-sample://com.microsoft.sampleapp”];

    // get your <app-scheme>://<bundle-id> here
    // Retrieve token using ADAL
    [context acquireTokenWithResource:authenticationParameters.resource
                             clientId:appClientId
                          redirectUri:redirectURI
                               userId:authenticationParameters.userId
                      completionBlock:^(ADAuthenticationResult *result)
                      {
                          if (result.status != AD_SUCCEEDED)
                          {
                              NSLog(@"Auth Failed");
                              completionBlock(nil, result.error);
                          }
                          else
                          {
                              completionBlock(result.accessToken, result.error);
                          }
                      }

        ];
    }



**Autenticação de utilizador do Linux / C++** – para obter mais informações, consulte [Exemplos de código do Linux](linux-c-code-examples.md).



    // Class Header
    class AuthCallback : public IAuthenticationCallback {
    private:

      std::shared_ptr<rmsauth::FileCache> FileCachePtr;
      std::string clientId_;
      std::string redirectUrl_;

      public:

      AuthCallback(const std::string& clientId,
               const std::string& redirectUrl);
      virtual std::string GetToken(shared_ptr<AuthenticationParameters>& ap) override;
    };

    class ConsentCallback : public IConsentCallback {
      public:

      virtual ConsentList Consents(ConsentList& consents) override;
    };

    // Class Implementation
    AuthCallback::AuthCallback(const string& clientId, const string& redirectUrl)
    : clientId_(clientId), redirectUrl_(redirectUrl) {
      FileCachePtr = std::make_shared<FileCache>();
    }

    string AuthCallback::GetToken(shared_ptr<AuthenticationParameters>& ap)
    {
      string redirect =
      ap->Scope().empty() ? redirectUrl_ : ap->Scope();

      try
      {
        if (redirect.empty()) {
        throw rmscore::exceptions::RMSInvalidArgumentException(
              "redirect Url is empty");
      }

      if (clientId_.empty()) {
      throw rmscore::exceptions::RMSInvalidArgumentException("client Id is empty");
      }

      AuthenticationContext authContext(
        ap->Authority(), AuthorityValidationType::False, FileCachePtr);

      auto result = authContext.acquireToken(ap->Resource(),
                                           clientId_, redirect,
                                           PromptBehavior::Auto,
                                           ap->UserId());
      return result->accessToken();
      }

      catch (const rmsauth::Exception& ex)
      {
        // out logs
        throw;
      }
    }



 

 


<!--HONumber=Apr16_HO4-->

