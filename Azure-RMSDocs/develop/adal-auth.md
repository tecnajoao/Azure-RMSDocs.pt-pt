---
# required metadata

title: Autenticação ADAL para a aplicação com suporte RMS | Azure RMS
description: Descreve o processo para a autenticação com a ADAL
keywords: authentication, RMS, ADAL
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Este conteúdo do SDK não está atualizado. Durante um curto período de tempo, pode encontrar a [versão atual](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) da documentação no MSDN. **
# Autenticação ADAL para a aplicação com suporte RMS

A autenticação com o Azure RMS da sua aplicação através da Azure ADAL já faz parte do cliente RMS 2.1.

Ao atualizar a aplicação para utilizar a autenticação ADAL em vez do Assistente de Início de Sessão Online da Microsoft, o utilizador e os seus clientes poderão:

- Utilizar a autenticação multifator
- Instalar o cliente RMS 2.1 sem necessidade de privilégios administrativos no computador
- Certificar a aplicação para o Windows 10

## Duas abordagens para autenticação

Este tópico contém duas abordagens para autenticação com os exemplos de código correspondentes.

- **Autenticação interna** – Autenticação OAuth gerida pelo SDK RMS. Utilize esta abordagem se pretender que o cliente RMS apresente um pedido de autenticação ADAL quando a autenticação for necessária. Para obter detalhes sobre como configurar a sua aplicação, consulte a secção “Autenticação interna”.

> [!NOTE] Se a sua aplicação utilizar atualmente o SDK AD RMS 2.1 com o assistente de início de sessão, recomendamos que utilize o método de autenticação interno como o caminho de migração da sua aplicação.

- **Autenticação externa** – Autenticação OAuth gerida pela sua aplicação. Utilize esta abordagem se pretender que a aplicação efetue a gestão da sua própria autenticação OAuth. Com esta abordagem, o cliente RMS irá exercer uma chamada de retorno definida pela aplicação quando a autenticação for necessária. Para obter um exemplo detalhado, consulte “Autenticação externa” no final deste tópico.

> [!NOTE] A autenticação externa não implica a capacidade de alterar os utilizadores. O cliente RMS utiliza sempre o utilizador predefinido de um inquilino do RMS especificado.

### Autenticação interna

Será necessário o seguinte:

- Uma [subscrição do Microsoft Azure](https://azure.microsoft.com/en-us/) (uma avaliação gratuita é suficiente):
- Uma subscrição do Microsoft Azure Rights Management (uma conta [RMS para Indivíduos](https://technet.microsoft.com/en-us/library/dn592127.aspx) gratuita é suficiente).

> [!NOTE] Pergunte ao seu Administrador de TI se possui ou não uma subscrição do Microsoft Azure Rights Management e, em seguida, peça ao Administrador de TI para realizar os passos abaixo. Se a sua organização não tiver uma subscrição, deve pedir ao seu administrador de TI para criar uma. Além disso, o Administrador de TI deve subscrever com uma conta Escolar ou Profissional, em vez de uma conta Microsoft (ou seja, Hotmail).

Após a inscrição no Microsoft Azure:

- Inicie sessão no [Portal de Gestão do Azure](https://manage.windowsazure.com) para a organização que utiliza uma conta com privilégios administrativos.

![Início de sessão no Azure](../media/AzurePortalLogin.png)

- Navegue para baixo até à aplicação do **Active Directory**, no lado esquerdo do portal.

![Selecionar Active Directory](../media/AzureADPick.png)

- Se ainda não tiver criado um diretório, escolha o botão **Novo**, situado no canto inferior esquerdo do portal.

![Selecionar NOVO](../media/AzureNewBtn.png)

- Selecione o separador **Rights Management** e certifique-se de que o **Estado do Rights Management** é **Ativo**, **Desconhecido** ou **Não Autorizado**. Se o estado for **Inativo**, escolha o botão **Ativar** ,na parte inferior central do portal, e confirme a seleção.

![Escolher ATIVAR](../media/RMTab.png)

- Agora, crie uma nova *Aplicação Nativa* no diretório ao selecionar o diretório e ao escolher Aplicações.

![Selecionar APLICAÇÕES](../media/CreateNativeApp.png)

- Em seguida, escolha o botão **ADICIONAR**, situado na parte inferior central do portal.

![Selecionar ADICIONAR](../media/AddAppBtn.png)

- Na linha de comandos, escolha **Adicionar uma aplicação que a minha organização está a desenvolver**.

![Selecionar Adicionar uma aplicação que a minha organização está a desenvolver](../media/AddAnAppPick.png)

- Atribua um nome à aplicação ao selecionar **APLICAÇÃO CLIENTE NATIVA** e escolher o botão **Seguinte**.

![Atribuir um nome à aplicação](../media/TellUsInput.png)

- Adicione um URI de redirecionamento e selecione seguinte. O URI redirecionamento tem de ser um URI válido e exclusivo para o seu diretório. Por exemplo, pode utilizar algo como `com.mycompany.myapplication://authorize`.

![Adicionar URI de redirecionamento](../media/RedirectURI.png)

- Selecione a aplicação no diretório e escolha **CONFIGURAR**.

![Escolher CONFIGURAR](../media/ConfigYourApp.png)

>[!NOTE] Copie a **ID DE CLIENTE** e o **URI DE REDIRECIONAMENTO** e armazene-os para utilização futura quando configurar o cliente RMS.

- Navegue até à parte inferior das definições da aplicação e escolha o botão **Adicionar aplicação** em **permissões para outras aplicações**.

![Selecionar Adicionar aplicação](../media/PermissionsToOtherBtn.png)

- Agora, adicione este GUID `00000012-0000-0000-c000-000000000000` à caixa de edição **QUE INICIE COM** e selecione o botão de verificação.

![Adicionar GUID](../media/AddGUID.png)

- Selecione o sinal de adição (+) junto a **Microsoft Rights Management**.

![Selecionar o botão +](../media/ChoosePlusBtn.png)

- Agora, selecione a marca de verificação situada no canto inferior esquerdo da caixa de diálogo.

![Escolher a marca de verificação](../media/ChooseCheck.png)

- Está agora preparado para adicionar uma dependência à sua aplicação do Azure RMS. Para adicionar a dependência, selecione a nova entrada do **Microsoft Rights Management Services** em **permissões para outras aplicações** e escolha a caixa de verificação **Criar e aceder a conteúdo protegido para utilizadores** na pasta de depósito **Permissões delegadas:**.

![Permissões de configuração](../media/AddDependency.png)

- Guarde a aplicação para manter as alterações ao escolher o ícone **GUARDAR**, situado na parte inferior central do portal.

![Selecionar GUARDAR](../media/SaveApplication.png)

- Agora está pronto para configurar a sua aplicação para utilizar a autenticação ADAL interna fornecida pelo SDK RMS 2.1. Para configurar o cliente RMS, adicione uma chamada a [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/IpcSetGlobalProperty) imediatamente após chamar [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize) para configurar o cliente RMS. Utilize o seguinte fragmento de código como um exemplo.


    IpcInitialize();

    IPC_AAD_APPLICATION_ID applicationId = { 0 };   applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);   applicationId.wszClientId = L"GUID-provided-by-AAD-for-your-app-(no-brackets)";   applicationId.wszRedirectUri = L"RedirectionUriWeProvidedAADForOurApp://authorize";

    HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &amp;applicationId);

    if (FAILED(hr)) {    //Handle the error   }

### Autenticação externa

- Utilize este código como um exemplo de como gerir os seus próprios tokens de autenticação.


    extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST&amp; Parameters, __out wstring wstrToken) throw();

    HRESULT GetLicenseKey(PCIPC_BUFFER pvLicense, __in LPVOID pContextForAdal, __out IPC_KEY_HANDLE &amp;hKey) { IPC_OAUTH2_CALLBACK pfGetADALToken =         [](LPVOID pvContext, PIPC_NAME_VALUE_LIST pParameters, IPC_AUTH_TOKEN_HANDLE* phAuthToken) -&gt; HRESULT { wstring wstrToken; HRESULT hr = GetADALToken(pvContext, *pParameters, wstrToken); return SUCCEEDED(hr) ? IpcCreateOAuth2Token(wstrToken.c_str(), OUT phAuthToken) : hr; };

      IPC_OAUTH2_CALLBACK_INFO callbackCredentialContext =
      {
          sizeof(IPC_OAUTH2_CALLBACK_INFO),
          pfGetADALToken,
          pContextForAdal
      };

      IPC_CREDENTIAL credentialContext =
      {
          IPC_CREDENTIAL_TYPE_OAUTH2,
          NULL
      };
      credentialContext.pcOAuth2 = &amp;callbackCredentialContext;

      IPC_PROMPT_CTX promptContext =
      {
        sizeof(IPC_PROMPT_CTX),
        NULL,
        IPC_PROMPT_FLAG_SILENT | IPC_PROMPT_FLAG_HAS_USER_CONSENT,
        NULL,
        &amp;credentialContext
      };

      hKey = 0L;
      return IpcGetKey(pvLicense, 0, &amp;promptContext, NULL, &amp;hKey);
  }

### Tópicos relacionados
- [Tipos de dados](/rights-management/sdk/2.1/api/win/Data%20types)
- [Propriedades de ambiente](/rights-management/sdk/2.1/api/win/Environment%20properties)
- [IpcCreateOAuth2Token](/rights-management/sdk/2.1/api/win/IpcCreateOAuth2Token)
- [IpcGetKey](/rights-management/sdk/2.1/api/win/IpcGetKey)
- [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize)
- [IPC_CREDENTIAL](/rights-management/sdk/2.1/api/win/IPC\_CREDENTIAL)
- [IPC_NAME_VALUE_LIST](/rights-management/sdk/2.1/api/win/IPC\_NAME\_VALUE\_LIST)
- [IPC_OAUTH2_CALLBACK_INFO](/rights-management/sdk/2.1/api/win/IPC\_OAUTH2\_CALLBACK\_INFO)
- [IPC_PROMPT_CTX](/rights-management/sdk/2.1/api/win/IPC\_PROMPT\_CTX)
- [IPC_AAD_APPLICATION_ID](/rights-management/sdk/2.1/api/win/IPC\_AAD\_APPLICATION\_ID)


<!--HONumber=Jun16_HO1-->


