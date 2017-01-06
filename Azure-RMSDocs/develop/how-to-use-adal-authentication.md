---
title: "Autenticação ADAL para a aplicação com suporte RMS | Azure RMS"
description: "Descreve o processo para a autenticação com a ADAL"
keywords: "autenticação, RMS, ADAL"
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 0e138ec62a16b52fd5657037988d8a9b8daa754f


---

# <a name="how-to-use-adal-authentication"></a>Procedimentos: utilizar a autenticação ADAL

Autenticação com o Azure RMS para a sua aplicação com o ADAL (Azure Active Directory Authentication Library).

Ao atualizar a aplicação para utilizar a autenticação ADAL em vez do Assistente de Início de Sessão Online da Microsoft, o utilizador e os seus clientes poderão:

- Utilizar a autenticação multifator
- Instalar o cliente RMS 2.1 sem necessidade de privilégios administrativos no computador
- Certificar a aplicação para o Windows 10

## <a name="two-approaches-to-authentication"></a>Duas abordagens para autenticação

Este tópico contém duas abordagens para autenticação com os exemplos de código correspondentes.

- **Autenticação interna** – Autenticação OAuth gerida pelo SDK RMS.

  Utilize esta abordagem se pretender que o cliente RMS apresente um pedido de autenticação ADAL quando a autenticação for necessária. Para obter detalhes sobre como configurar a sua aplicação, consulte a secção “Autenticação interna”.

  > [!Note]
  > Se a sua aplicação utilizar atualmente o SDK AD RMS 2.1 com o assistente de início de sessão, recomendamos que utilize o método de autenticação interno como o caminho de migração da sua aplicação.

- **Autenticação externa** – Autenticação OAuth gerida pela sua aplicação.

  Utilize esta abordagem se pretender que a aplicação efetue a gestão da sua própria autenticação OAuth. Com esta abordagem, o cliente RMS irá exercer uma chamada de retorno definida pela aplicação quando a autenticação for necessária. Para obter um exemplo detalhado, consulte “Autenticação externa” no final deste tópico.

  > [!Note]
  > A autenticação externa não implica a capacidade de alterar os utilizadores. O cliente RMS utiliza sempre o utilizador predefinido de um inquilino do RMS especificado.

## <a name="internal-authentication"></a>Autenticação interna

1. Siga os passos da configuração do Azure em [Configurar o Azure RMS para autenticação ADAL](adal-auth.md) e, em seguida, volte ao passo de inicialização de aplicação seguinte.
2. Agora está pronto para configurar a sua aplicação para utilizar a autenticação ADAL interna fornecida pelo SDK RMS 2.1.

Para configurar o cliente RMS, adicione uma chamada para [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) imediatamente após chamar [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx) para configurar o cliente RMS. Utilize o seguinte fragmento de código como um exemplo.

      C++
      IpcInitialize();

      IPC_AAD_APPLICATION_ID applicationId = { 0 };
      applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);
      applicationId.wszClientId = L"GUID-provided-by-AAD-for-your-app-(no-brackets)";
      applicationId.wszRedirectUri = L"RedirectionUriWeProvidedAADForOurApp://authorize";
      HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &applicationId);
      if (FAILED(hr)) {
        //Handle the error
      }

## <a name="external-authentication"></a>Autenticação Externa

Utilize este código como um exemplo de como gerir os seus próprios tokens de autenticação.
C++ extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST& Parameters, __out wstring wstrToken) throw();

      HRESULT GetLicenseKey(PCIPC_BUFFER pvLicense, __in LPVOID pContextForAdal, __out IPC_KEY_HANDLE &hKey)
      {
          IPC_OAUTH2_CALLBACK pfGetADALToken =
          [](LPVOID pvContext, PIPC_NAME_VALUE_LIST pParameters, IPC_AUTH_TOKEN_HANDLE* phAuthToken) -> HRESULT
          {
              wstring wstrToken;
              HRESULT hr = GetADALToken(pvContext, *pParameters, wstrToken);
              return SUCCEEDED(hr) ? IpcCreateOAuth2Token(wstrToken.c_str(), OUT phAuthToken) : hr;
          };

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
          credentialContext.pcOAuth2 = &callbackCredentialContext;

          IPC_PROMPT_CTX promptContext =
          {
              sizeof(IPC_PROMPT_CTX),
              NULL,
              IPC_PROMPT_FLAG_SILENT | IPC_PROMPT_FLAG_HAS_USER_CONSENT,
              NULL,
              &credentialContext
          };

          hKey = 0L;
          return IpcGetKey(pvLicense, 0, &promptContext, NULL, &hKey);
      }

## <a name="related-topics"></a>Tópicos relacionados

- [Tipos de dados](https://msdn.microsoft.com/library/hh535288.aspx)
- [Propriedades de ambiente](https://msdn.microsoft.com/library/hh535247.aspx)
- [IpcCreateOAuth2Token](https://msdn.microsoft.com/library/mt661866.aspx)
- [IpcGetKey](https://msdn.microsoft.com/library/hh535263.aspx)
- [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx)
- [IPC_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx)
- [IPC_NAME_VALUE_LIST](https://msdn.microsoft.com/library/hh535277.aspx)
- [IPC_OAUTH2_CALLBACK_INFO](https://msdn.microsoft.com/library/mt661868.aspx)
- [IPC_PROMPT_CTX](https://msdn.microsoft.com/library/hh535278.aspx)
- [IPC_AAD_APPLICATION_ID](https://msdn.microsoft.com/library/mt661867.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


