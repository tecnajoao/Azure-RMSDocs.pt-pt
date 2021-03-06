---
title: Configurar aplicações para o Azure Rights Management – AIP
description: Instruções para os administradores configurarem aplicações e serviços para suportar o serviço de proteção do Azure Rights Management para o Azure Information Protection. Por exemplo, aplicações do Office como o Word 2013 e o Word 2010, bem como serviços como o Exchange Online (regras de transporte, prevenção de perda de dados, não reencaminhar e encriptação de mensagens) e o SharePoint Online (bibliotecas protegidas).
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0568eea52d7c426a8a96b365df5eb307acb9825c
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252355"
---
# <a name="configuring-applications-for-azure-rights-management"></a>Configurar aplicações para o Azure Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!NOTE]
> Estas informações destinam-se aos administradores de TI e consultores que tenham implementado o Azure Information Protection. Se estiver à procura de ajuda de utilizador e de informações sobre como utilizar a funcionalidade Rights Management para uma aplicação específica ou como abrir um ficheiro protegido por direitos, utilize a ajuda e as orientações incluídas na sua aplicação.
>
> Por exemplo, para aplicações do Office, clique no ícone Ajuda e introduza termos de pesquisa, como **Rights Management** ou **IRM**. Para o cliente do Azure Information Protection para o Windows, veja o [Guia do utilizador do cliente do Azure Information Protection](./rms-client/client-user-guide.md).

Depois de ter implementado o Azure Information Protection na sua organização, utilize as seguintes informações para configurar as aplicações, o cliente do Azure Information Protection e os serviços. Por exemplo, aplicações do Office como o Word 2016, Word 2013 e Word 2010. Bem como serviços como o Exchange Online (regras de transporte, prevenção de perda de dados, não reencaminhar e encriptação de mensagens) e o SharePoint Online (bibliotecas protegidas). Para obter informações sobre como estas aplicações e serviços suportam o serviço de proteção de dados do Azure Information Protection, veja [Como as aplicações suportam o serviço Azure Rights Management](applications-support.md).

> [!IMPORTANT]
> Para obter informações sobre as versões suportadas e outros requisitos, consulte [Requisitos do Azure Rights Management](requirements.md).

-   [Office 365: Configuração para clientes e serviços online](configure-office365.md)

    -   [Exchange Online: Configuração de IRM](configure-office365.md#exchangeonline-irm-configuration)

    -   [SharePoint Online e OneDrive para empresas: Configuração de IRM](configure-office365.md#sharepointonline-and-onedrive-for-business-irm-configuration)

- [Aplicativos do Office: Configuração para clientes](configure-office-apps.md)

    -   [Office 2016 ou Office 2013](configure-office-apps.md#office2016-and-office-2013)

    -   [Office 2010](configure-office-apps.md#office2010)

-   [Cliente do Azure Information Protection: Instalação e configuração para clientes](configure-client.md)

Para configurar os servidores no local, como o Exchange Server e o SharePoint Server, consulte [Implementar o conector Azure Rights Management](deploy-rms-connector.md).

Além destas aplicações e serviços, existem outras aplicações que suportam as APIs de Rights Management. Esta categoria inclui aplicações de linha de negócio que são escritas internamente através do SDK Rights Management, bem como aplicações de fornecedores de software que são escritas através do SDK Rights Management. Para estas aplicações, siga as instruções fornecidas com a aplicação.

## <a name="next-steps"></a>Passos Seguintes
Depois de configurar as suas aplicações para suportar o serviço Azure Rights Management, utilize o [Plano de implementação do Azure Information Protection](deployment-roadmap.md) para verificar se existem outros passos de configuração que queira realizar antes de implementar o Azure Information Protection para utilizadores e administradores. Caso contrário, as informações operacionais que se seguem podem ser-lhe úteis:

- [Verificar o serviço Azure Rights Management](verify.md)

- [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](help-users.md)

- [Registar e analisar o serviço Azure Rights Management](log-analyze-usage.md)

- [Operações para a sua chave de inquilino do Azure Information Protection](operations-tenant-key.md)


