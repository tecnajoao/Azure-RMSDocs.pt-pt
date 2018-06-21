---
title: Procedimentos para ativar a aplicação do serviço para que funcione com o RMS baseado na nuvem | Azure RMS
description: Este tópico descreve os passos para configurar a aplicação do serviço para utilizar o Azure Rights Management.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: EA1457D1-282F-4CF3-A23C-46793D2C2F32
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 6c1500b13a0c7ddabd3a01deb08c81fa3d4d72c7
ms.sourcegitcommit: 8e622a93ff8d07a180e3be6e8b14748354e640bd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/29/2018
ms.locfileid: "30259000"
---
# <a name="how-to-enable-your-service-application-to-work-with-cloud-based-rms"></a>Procedimentos: permitir que a aplicação de serviço funcione com o RMS baseado na nuvem

Este tópico descreve os passos para configurar a aplicação do serviço para utilizar o Azure Rights Management. Para obter mais informações, consulte [Introdução ao Azure Rights Management](https://technet.microsoft.com/library/jj585016.aspx).

**Importante**  
Para utilizar a aplicação de serviço SDK Rights Management Services 2.1 com o Azure RMS, terá de criar os seus inquilinos. Para obter mais informações, consulte [Requisitos do Azure RMS: Subscrições na nuvem que suportam o Azure RMS](../get-started/requirements-subscriptions.md)

## <a name="prerequisites"></a>Pré-requisitos

-   O SDK RMS 2.1 tem de estar instalado e configurado. Para obter mais informações, consulte [Introdução ao SDK RMS 2.1](getting-started-with-ad-rms-2-0.md).
-   Tem de [criar uma identidade do serviço através do ACS](https://msdn.microsoft.com/library/gg185924.aspx) ao utilizar a opção de chave simétrica ou através de outros meios e registar as informações da chave a partir desse processo.

## <a name="connecting-to-the-azure-rights-management-service"></a>Ligar ao Serviço Azure Rights Management

-   Chame [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx).
-   Defina [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx).

        C++
        int mode = IPC_API_MODE_SERVER;
        IpcSetGlobalProperty(IPC_EI_API_MODE, &(mode));


  **Nota:** para obter mais informações, consulte [Definir o modo de segurança de API](setting-the-api-security-mode-api-mode.md)

     
-   Os seguintes passos são a configuração para a criação de uma instância de uma estrutura [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx) com o membro *pcCredential* ([IPC\_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx)) preenchido com as informações de ligação do serviço Azure Rights Management.
-   Utilize as informações da criação da identidade do serviço de chave simétrica (consulte os pré-requisitos listados anteriormente neste tópico) para definir os parâmetros *wszServicePrincipal*, *wszBposTenantId* e *cbKey* quando cria uma instância de uma estrutura [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx).

**Nota:** devido a uma condição existente no nosso serviço de deteção, se não estiver na América do Norte, as credenciais da chave simétrica não serão aceites a partir de outras regiões; como tal, tem de especificar os URLs do inquilino diretamente. Isto é feito através do parâmetro *pConnectionInfo*, tipo [IPC\_CONNECTION\_INFO](https://msdn.microsoft.com/library/hh535274.aspx), nas funções [IpcGetTemplateList](https://msdn.microsoft.com/library/hh535267.aspx) ou [IpcGetTemplateIssuerList](https://msdn.microsoft.com/library/hh535266.aspx).

## <a name="generate-a-symmetric-key-and-collect-the-needed-information"></a>Gerar uma chave simétrica e recolher as informações necessárias

### <a name="instructions-to-generate-a-symmetric-key"></a>Instruções para gerar uma chave simétrica

-   Instalar o [Assistente de Início de Sessão Online da Microsoft](http://go.microsoft.com/fwlink/p/?LinkID=286152)
-   Instalar o [Módulo do Powershell do Azure AD](https://bposast.vo.msecnd.net/MSOPMW/8073.4/amd64/AdministrationConfig-en.msi).

**Nota:** tem de ser um administrador inquilino para utilizar cmdlets do Powershell.

- Inicie o Powershell e execute os seguintes comandos para gerar uma chave

    `Import-Module MSOnline`

    `Connect-MsolService` (introduza as credenciais de administrador)

    `New-MsolServicePrincipal` (introduza um nome a apresentar)

- Depois de gerar uma chave simétrica, transmitirá informações sobre a chave, incluindo a própria chave, e um *AppPrincipalId*.

      The following symmetric key was created as one was not supplied
      ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

      DisplayName : RMSTestApp
      ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963}
      ObjectId : 0ee53770-ec86-409e-8939-6d8239880518
      AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963


### <a name="instructions-to-find-out-tenantbposid-and-urls"></a>Instruções para descobrir **TenantBposId** e **Urls**

-   Instalar o [Módulo do powershell do Azure RMS](https://technet.microsoft.com/library/jj585012.aspx).
-   Inicie o Powershell e execute os seguintes comandos para obter a configuração do RMS do inquilino.

    `Import-Module aadrm`

    `Connect-AadrmService` (introduza as credenciais de administrador)

    `Get-AadrmConfiguration`


- Crie uma instância de [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx) e defina alguns membros.

      // Create a key structure.
      IPC_CREDENTIAL_SYMMETRIC_KEY symKey = {0};

      // Set each member with information from service creation.
      symKey.wszBase64Key = "your service principal key";
      symKey.wszAppPrincipalId = "your app principal identifier";
      symKey.wszBposTenantId = "your tenant identifier";


Para mais informações, consulte [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx).

-   Crie uma instância de uma estrutura [IPC\_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx) que contém a instância [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx).

**Nota:** os membros *connectionInfo* são definidos com URLs a partir da chamada anterior para `Get-AadrmConfiguration` e são indicados aqui com esses nomes de campo.

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

### <a name="identify-a-template-and-then-encrypt"></a>Identificar um modelo e encriptar

-   Selecione um modelo a utilizar para a encriptação.
    Chame [IpcGetTemplateList](https://msdn.microsoft.com/library/hh535267.aspx) passando na mesma instância de [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx).


    PCIPC_TIL pTemplates = NULL; IPC_TEMPLATE_ISSUER templateIssuer = (pTemplateIssuerList->aTi)[0];

    hr = IpcGetTemplateList(&(templateIssuer.connectionInfo),        IPC_GTL_FLAG_FORCE_DOWNLOAD,        0,        &promptCtx,        NULL,        &pTemplates);


-   Com o modelo anterior deste tópico, chame [IpcfEncrcyptFile](https://msdn.microsoft.com/library/dn133059.aspx), passando na mesma instância de [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx).

Utilização de exemplo de [IpcfEncrcyptFile](https://msdn.microsoft.com/library/dn133059.aspx):

    LPCWSTR wszContentTemplateId = pTemplates->aTi[0].wszID;
    hr = IpcfEncryptFile(wszInputFilePath,
           wszContentTemplateId,
           IPCF_EF_TEMPLATE_ID,
           IPC_EF_FLAG_KEY_NO_PERSIST,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Utilização de exemplo de [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx):

    hr = IpcfDecryptFile(wszInputFilePath,
           IPCF_DF_FLAG_DEFAULT,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Concluiu os passos necessários para permitir que a sua aplicação utilize o Azure Rights Management.

## <a name="related-topics"></a>Tópicos relacionados

* [Introdução ao Azure Rights Management](https://technet.microsoft.com/library/jj585016.aspx)
* [Introdução ao SDK RMS 2.1](getting-started-with-ad-rms-2-0.md)
* [Criar uma identidade do serviço através do ACS](https://msdn.microsoft.com/library/gg185924.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)
* [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx)
* [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx)
* [IPC\_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx)
* [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx)
* [IpcGetTemplateIssuerList](https://msdn.microsoft.com/library/hh535266.aspx)
* [IpcGetTemplateList](https://msdn.microsoft.com/library/hh535267.aspx)
* [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx)
* [IpcfEncrcyptFile](https://msdn.microsoft.com/library/dn133059.aspx)
* [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)
* [IpcCreateLicenseFromTemplateID](https://msdn.microsoft.com/library/hh535257.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]