---
# required metadata

title: Permitir que a aplicação do serviço funcione com o RMS baseado na nuvem | Azure RMS
description: Este tópico descreve os passos para configurar a aplicação do serviço para utilizar o Azure Rights Management.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EA1457D1-282F-4CF3-A23C-46793D2C2F32
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Permitir que a aplicação do serviço funcione com o RMS baseado na nuvem

Este tópico descreve os passos para configurar a aplicação do serviço para utilizar o Azure Rights Management. Para obter mais informações, consulte [Introdução ao Azure Rights Management](https://technet.microsoft.com/en-us/library/jj585016.aspx).

**Importante**  
Recomenda-se que teste primeiro a aplicação SDK Rights Management Services 2.1 com o ambiente de pré-produção do RMS num Servidor RMS. Em seguida, se pretender que o cliente tenha a capacidade de utilizar a aplicação com o Serviço Azure RMS, passe para o teste nesse ambiente.

Para utilizar a aplicação do serviço SDK RMS 2.1 com o Azure RMS, terá de solicitar um Inquilino do Azure RMS, se ainda não tiver um. Envie um e-mail para <rmcstbeta@microsoft.com> com o seu pedido de inquilino.

## Pré-requisitos

-   O SDK RMS 2.1 tem de estar instalado e configurado. Para obter mais informações, consulte [Introdução ao SDK RMS 2.1](getting-started-with-ad-rms-2-0.md).
-   Tem de [criar uma identidade do serviço através do ACS](https://msdn.microsoft.com/en-us/library/gg185924.aspx) ao utilizar a opção de chave simétrica ou através de outros meios e registar as informações da chave a partir desse processo.

## Ligar ao Serviço Azure Rights Management

-   Chame [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize).
-   Defina [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty).


    int mode = IPC_API_MODE_SERVER;
    IpcSetGlobalProperty(IPC_EI_API_MODE, &(mode));


**Nota** Para obter mais informações, consulte [Definir o modo de segurança de API](setting-the-api-security-mode-api-mode.md)

     

-   Os seguintes passos são a configuração para a criação de uma instância de uma estrutura [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx) com o membro **pcCredential** ([**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)) preenchido com as informações de ligação do Serviço Azure Rights Management.
-   Utilize as informações da criação da identidade do serviço de chave simétrica (consulte os pré-requisitos listados anteriormente neste tópico) para definir os parâmetros **wszServicePrincipal**, **wszBposTenantId** e **cbKey** quando cria uma instância de uma estrutura [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key).

**Nota** Devido a uma condição existente no nosso serviço de deteção, se não estiver na América do Norte, as credenciais da chave simétrica não serão aceites a partir de outras regiões, como tal, tem de especificar os URLs do inquilino diretamente. Isto é feito através do parâmetro [**IPC\_CONNECTION\_INFO**](/rights-management/sdk/2.1/api/win/ipc_connection_info#msipc_ipc_connection_info) de [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) ou [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist).

## Gerar uma chave simétrica e recolher as informações necessárias

### Instruções para gerar uma chave simétrica

-   Instalar o [Assistente de Início de Sessão Online da Microsoft](http://go.microsoft.com/fwlink/p/?LinkID=286152)
-   Instalar o [Módulo do Powershell do Azure AD](https://bposast.vo.msecnd.net/MSOPMW/8073.4/amd64/AdministrationConfig-en.msi).

**Nota** Tem de ser um administrador inquilino para utilizar cmdlets do Powershell.


-   Inicie o Powershell e execute os seguintes comandos para gerar uma chave
            `Import-Module MSOnline`
            `Connect-MsolService` (introduza as credenciais de administrador)
            `New-MsolServicePrincipal` (introduza um nome a apresentar)
-   Depois de gerar uma chave simétrica, transmitirá informações sobre a chave, incluindo a própria chave, e **AppPrincipalId**.



    The following symmetric key was created as one was not supplied
    ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

    DisplayName : RMSTestApp
    ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963}
    ObjectId : 0ee53770-ec86-409e-8939-6d8239880518
    AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963



### Instruções para descobrir **TenantBposId** e **Urls**

-   Instalar o [Módulo do powershell do Azure RMS](https://technet.microsoft.com/en-us/library/jj585012.aspx).
-   Inicie o Powershell e execute os seguintes comandos para obter a configuração do RMS do inquilino.

    `Import-Module aadrm`

    `Connect-AadrmService` (introduza as credenciais de administrador)

    `Get-AadrmConfiguration`


-   Crie uma instância de [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) e defina alguns membros.

    // Crie uma estrutura chave.
    IPC_CREDENTIAL_SYMMETRIC_KEY symKey = {0};

    // Defina cada membro com informações da criação do serviço.
    symKey.wszBase64Key = "a chave principal do serviço";
    symKey.wszAppPrincipalId = "o identificador principal da aplicação";
    symKey.wszBposTenantId = "o identificador de inquilino";


Para obter mais informações, consulte [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key).

-   Crie uma instância de uma estrutura [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential) que contém a instância [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key).

**Nota** Os membros *conectionInfo* estão definidos com URLs da chamada anterior para `Get-AadrmConfiguration` e estão indicados aqui com esses nomes de campo.

    // Create a credential structure.
    IPC_CREDENTIAL cred = {0};

    IPC_CONNECTION_INFO connectionInfo = {0};
    connectionInfo.wszIntranetUrl = LicensingIntranetDistributionPointUrl;
    connectionInfo.wszExtranetUrl = LicensingExtranetDistributionPointUrl;

    // Set each member.
    cred.dwType = IPC_CREDENTIAL_TYPE_SYMMETRIC_KEY;
    cred.pcCertContext = (PCCERT_CONTEXT)&symKey;

    // Create your prompt control.
    IPC_PROMPT_CTX promptCtx = {0};

    // Set each member.
    promptCtx.cbSize = sizeof(IPC_PROMPT_CTX);
    promptCtx.hwndParent = NULL;
    promptCtx.dwflags = IPC_PROMPT_FLAG_SILENT;
    promptCtx.hCancelEvent = NULL;
    promptCtx.pcCredential = &cred;

### Identificar um modelo e encriptar

-   Selecione um modelo a utilizar para a encriptação.
    Chame [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) passando na mesma instância de [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx).


    PCIPC_TIL pTemplates = NULL;
    IPC_TEMPLATE_ISSUER templateIssuer = (pTemplateIssuerList->aTi)[0];

    hr = IpcGetTemplateList(&(templateIssuer.connectionInfo),
           IPC_GTL_FLAG_FORCE_DOWNLOAD,
           0,
           &promptCtx,
           NULL,
           &pTemplates);


-   Com o modelo anterior deste tópico, chame [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile), passando na mesma instância de [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx).

Utilização de exemplo de [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile):

    LPCWSTR wszContentTemplateId = pTemplates->aTi[0].wszID;
    hr = IpcfEncryptFile(wszInputFilePath,
           wszContentTemplateId,
           IPCF_EF_TEMPLATE_ID,
           IPC_EF_FLAG_KEY_NO_PERSIST,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Utilização de exemplo de [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile):

    hr = IpcfDecryptFile(wszInputFilePath,
           IPCF_DF_FLAG_DEFAULT,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Concluiu os passos necessários para permitir que a sua aplicação utilize o Azure Rights Management.

## Tópicos relacionados

* [Conceitos do programador](ad-rms-concepts-nav.md)
* [Introdução ao Azure Rights Management](https://technet.microsoft.com/en-us/library/jj585016.aspx)
* [Introdução ao SDK RMS 2.1](getting-started-with-ad-rms-2-0.md)
* [Criar uma identidade do serviço através do ACS](https://msdn.microsoft.com/en-us/library/gg185924.aspx)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
* [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx)
* [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)
* [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key)
* [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)
* [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile)
* [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcCreateLicenseFromTemplateID**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromtemplateid)
 

 


<!--HONumber=Apr16_HO4-->

