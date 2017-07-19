---
title: "Configurar aplicações para o Azure Rights Management – AIP"
description: "Instruções para os administradores configurarem aplicações e serviços para suportar o serviço de proteção do Azure Rights Management para o Azure Information Protection. Por exemplo, aplicações do Office como o Word 2013 e o Word 2010, bem como serviços como o Exchange Online (regras de transporte, prevenção de perda de dados, não reencaminhar e encriptação de mensagens) e o SharePoint Online (bibliotecas protegidas)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/26/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e3030aca9e7b93d93df583934b2a6ad2f0013903
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="configuring-applications-for-azure-rights-management"></a>Configurar aplicações para o Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

> [!NOTE]
> Estas informações destinam-se aos administradores de TI e consultores que tenham implementado o Azure Information Protection. Se estiver à procura de ajuda de utilizador e de informações sobre como utilizar a funcionalidade Rights Management para uma aplicação específica ou como abrir um ficheiro protegido por direitos, utilize a ajuda e as orientações incluídas na sua aplicação.
>
> Por exemplo, para aplicações do Office, clique no ícone Ajuda e introduza termos de pesquisa, como **Rights Management** ou **IRM**. Para o cliente do Azure Information Protection para o Windows, veja o [Guia do utilizador do cliente do Azure Information Protection](../rms-client/client-user-guide.md).

Depois de ter implementado o Azure Information Protection na sua organização, utilize as seguintes informações para configurar as aplicações, o cliente do Azure Information Protection e os serviços. Por exemplo, aplicações do Office como o Word 2016, Word 2013 e Word 2010. Bem como serviços como o Exchange Online (regras de transporte, prevenção de perda de dados, não reencaminhar e encriptação de mensagens) e o SharePoint Online (bibliotecas protegidas). Para obter informações sobre como estas aplicações e serviços suportam o serviço de proteção de dados do Azure Information Protection, veja [Como as aplicações suportam o serviço Azure Rights Management](../understand-explore/applications-support.md).

> [!IMPORTANT]
> Para obter informações sobre as versões suportadas e outros requisitos, consulte [Requisitos do Azure Rights Management](../get-started/requirements-azure-rms.md).

-   [Office 365: Configuração para clientes e serviços online](configure-office365.md)

    -   [Exchange Online: configuração de IRM](configure-office365.md#exchange-online-irm-configuration)

    -   [SharePoint Online e OneDrive para Empresas: configuração de IRM](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)

- [Aplicações do Office: configuração para clientes](configure-office-apps.md)

    -   [Office 2016 e Office 2013](configure-office-apps.md#office-2016-and-office-2013)

    -   [Office 2010](configure-office-apps.md#office-2010)

-   [Cliente do Azure Information Protection: instalação e configuração para clientes](configure-sharing-app.md)

-   [Aplicação de partilha Rights Management: instalação e configuração para clientes](configure-sharing-app.md)


Para configurar os servidores no local, como o Exchange Server e o SharePoint Server, consulte [Implementar o conector Azure Rights Management](deploy-rms-connector.md).

Além destas aplicações e serviços, existem outras aplicações que suportam as APIs de Rights Management. Esta categoria inclui aplicações de linha de negócio que são escritas internamente através do SDK Rights Management, bem como aplicações de fornecedores de software que são escritas através do SDK Rights Management. Para estas aplicações, siga as instruções fornecidas com a aplicação.

## <a name="next-steps"></a>Passos seguintes
Depois de configurar as suas aplicações para suportar o serviço Azure Rights Management, utilize o [Plano de implementação do Azure Information Protection](../plan-design/deployment-roadmap.md) para verificar se existem outros passos de configuração que queira realizar antes de implementar o Azure Information Protection para utilizadores e administradores. Caso contrário, as informações operacionais que se seguem podem ser-lhe úteis:

- [Verificar o serviço Azure Rights Management](verify.md)

- [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](help-users.md)

- [Registar e analisar o serviço Azure Rights Management](log-analyze-usage.md)

- [Operações para a sua chave de inquilino do Azure Information Protection](operations-tenant-key.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

