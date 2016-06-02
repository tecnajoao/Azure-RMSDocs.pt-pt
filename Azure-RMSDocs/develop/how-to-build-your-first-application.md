---
# required metadata

title: IPCHelloWorld – uma aplicação de exemplo | Azure RMS
description: Este tópico contém instruções para criar uma aplicação com capacidade para direitos.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 581451A2-9558-4D0D-9D01-BEAB282C5A83
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# IPCHelloWorld – uma aplicação de exemplo

Este tópico contém instruções para criar uma aplicação com capacidade para direitos.

Esta aplicação IPCHelloWorld simples descreve os conceitos básicos e o código de uma aplicação com capacidade para direitos.

Transfira a aplicação de amostra, [Webinar\_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440), a partir do Microsoft Connect. Os itens transferíveis restantes no site estão integrados aqui para sua comodidade.

**Nota** o projeto IPCHelloWorld já está configurado para o SDK Rights Management Services 2.1. Para obter informações sobre como configurar um novo projeto para utilizar o SDK RMS 2.1, consulte [Configurar o Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md).

 
As secções seguintes abrangem os principais passos e conhecimentos necessários relativos à aplicação.

## Carregar o MSIPC.dll

Antes de poder chamar quaisquer funções do SDK RMS 2.1, tem primeiro de chamar a função [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) para carregar o MSIPC.dll.



    hr = IpcInitialize();

    if (FAILED(hr))
    {
      wprintf(L"Failed to initialize MSIPC. Are you sure the runtime is installed?\n");
      goto exit;
    }



## Enumerar modelos

Um modelo de RMS define a política utilizada para proteger os dados, ou seja, define os utilizadores que têm permissão para aceder aos dados e respetivos direitos. Os modelos de RMS estão instalados no servidor RMS.

O recorte de código seguinte enumera os modelos de RMS disponíveis no servidor RMS predefinido.



    hr = IpcGetTemplateList(NULL, 0, 0, NULL, NULL, &pcTil);

    if (FAILED(hr))
    {
      DisplayError(L"IpcGetTemplateList failed", hr);
      goto exit;
    }



Esta chamada irá obter modelos de RMS instalados no servidor predefinido e carregar os resultados na estrutura [**IPC\_TIL**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) indicada pela variável *pcTil* e, em seguida, apresentar os modelos de apresentação.



    if (0 == pcTil->cTi)
    {
      wprintf(L"* No templates configured for your RMS server * \n\n");
      wprintf(L"\\------------------------------------------------------\n\n");
      goto exit;
    }

    for (DWORD dw = 0; dw < pcTil->cTi; dw++)
    {
      wprintf(L"Template #%d:\n", dw);
      wprintf(L"    Name:         %s\n", pcTil->aTi[dw].wszName);
      wprintf(L"    Issued by:    %s\n", pcTil->aTi[dw].wszIssuerDisplayName);
      wprintf(L"    Description:  %s\n", pcTil->aTi[dw].wszDescription);
      wprintf(L"\n");
    }



## Serializar uma Licença

Antes de poder proteger quaisquer dados, precisa de serializar uma licença e obter uma chave de conteúdo. A chave de conteúdo é utilizada para encriptar os dados confidenciais. Normalmente, a licença serializada está ligada aos dados encriptados e é utilizada pelo consumidor dos dados protegidos. O consumidor terá de chamar a função [**IpcGetKey**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey) através da licença serializada para obter a chave de conteúdo para desencriptar o conteúdo e para obter a política associada ao conteúdo.

Com vista à simplicidade, utilize o primeiro modelo de RMS devolvido por [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) para serializar uma licença.

Normalmente, deve utilizar uma caixa de diálogo de interface de utilizador para permitir ao utilizador selecionar o modelo pretendido.



    hr = IpcSerializeLicense((LPCVOID)pcTil->aTi[0].wszID, IPC_SL_TEMPLATE_ID,
    0, NULL, &hContentKey, &pSerializedLicense);

    if (FAILED(hr))
    {
      DisplayError(L"IpcSerializeLicense failed", hr);
      goto exit;
    }



Depois de o fazer, obtém a chave de conteúdo, *hContentKey*, e a licença serializada, *pSerializedLicense*, de que precisa para anexar aos dados protegidos.

## Proteger Dados

Agora, está pronto para encriptar os dados confidenciais através da função [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt). Em primeiro lugar, tem de perguntar à função **IpcEncrypt** qual vai ser o tamanho dos dados encriptados.



    cbText = (DWORD)(sizeof(WCHAR)*(wcslen(wszText)+1));
    hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
    NULL, 0, &cbEncrypted);

    if (FAILED(hr)) {
      DisplayError(L"IpcEncrypt failed", hr);
      goto exit;
    }



Aqui, *wszText* contém o texto simples que vai proteger. A função [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt) devolve o tamanho dos dados encriptados no parâmetro *cbEncrypted*.

Agora, atribua memória para os dados encriptados.



    pbEncrypted = (PBYTE)LocalAlloc(LPTR, cbEncrypted);

    if (NULL == pbEncrypted) {
      wprintf(L"Out of memory\n");
      goto exit;
    }


Por fim, pode efetuar a encriptação real.



    hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
    pbEncrypted, cbEncrypted, &cbEncrypted);

    if (FAILED(hr)) {
      DisplayError(L"IpcEncrypt failed", hr);
      goto exit;
    }


Após este passo, tem os dados encriptados, *pbEncrypted*, e a licença serializada, *pSerializedLicense*, que será utilizada pelos consumidores para desencriptar os dados.

## Processamento de Erros

Nesta aplicação de exemplo, a função **DisplayError** está a ser utilizada para processar erros.



    void DisplayError(LPCWSTR wszErrorInfo, HRESULT hrError)
    {
        LPCWSTR wszErrorMessageText = NULL;

        if (SUCCEEDED(IpcGetErrorMessageText(hrError, 0, &wszErrorMessageText))) {
          wprintf(L"%s: 0x%08X (%s)\n", wszErrorInfo, hrError, wszErrorMessageText);
        }
        else {
          wprintf(L"%s: 0x%08X\n", wszErrorInfo, hrError);
        }
    }   


A função **DisplayError** utiliza a função [**IpcGetErrorMessageText**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext) para obter a mensagem de erro do código de erro correspondente e imprime-a para a saída padrão.

## Limpeza

Antes de terminar, também tem de libertar todos os recursos atribuídos.



    if (NULL != pbEncrypted) {
      LocalFree((HLOCAL)pbEncrypted);
    }

    if (NULL != pSerializedLicense) {
      IpcFreeMemory((LPVOID)pSerializedLicense);
    }

    if (NULL != hContentKey) {
      IpcCloseHandle((IPC_HANDLE)hContentKey);
    }

    if (NULL != pcTil) {
      IpcFreeMemory((LPVOID)pcTil);
    }


## Tópicos relacionados

* [Notas do programador](developer-notes.md)
* [Configurar o Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)
* [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt)
* [**IpcGetErrorMessageText**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext)
* [**IpcGetKey**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [**IPC\_TIL**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [Webinar\_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)
 

 


<!--HONumber=Apr16_HO4-->

