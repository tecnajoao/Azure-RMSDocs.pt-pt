---
# required metadata

title: Como é que as aplicações suportam o Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Como é que as aplicações suportam o Azure Rights Management

*Aplica-se a: Azure Rights Management, Office 365*

Utilize as informações que se seguem para compreender melhor como as aplicações de utilizador final (como as aplicações do Office, Word, Excel, PowerPoint e Outlook) e serviços (como o Exchange e o SharePoint) utilizados mais frequentemente podem utilizar o Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] para ajudar a proteger dados da sua organização. 
> [!NOTE]
> Para verificar as aplicações e versões que o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) suporta, consulte [Requisitos do Azure Rights Management](../get-started/requirements-azure-rms.md).

Em certos casos, a proteção de informações é aplicada automaticamente, de acordo com as políticas que configurar. Por exemplo, é este o caso com bibliotecas do SharePoint, ficheiros classificados e regras de transporte do Exchange. Noutros casos, os utilizadores têm de aplicar proteção de informações por si próprios nas respetivas aplicações, seja ao selecionar um modelo ou ao selecionar opções específicas. Por exemplo, é este o caso quando os utilizadores partilham um ficheiro por e-mail ou protegem um ficheiro no local ao restringir o acesso ou a utilização a utilizadores selecionados ou a utilizadores fora da organização.

Os modelos fazem com que seja mais fácil para os utilizadores (e administradores que configuram políticas) aplicar o nível correto de proteção e restringir o acesso a pessoas dentro da sua organização. Embora o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] inclua dois modelos predefinidos, é provável que pretenda criar modelos personalizados para reduzir as vezes em que é necessário especificar opções individuais. Para obter mais informações, consulte [Configurar modelos personalizados para o Azure Rights Management](../deploy-use/configure-custom-templates.md).

Para os casos em que os utilizadores têm de aplicar a proteção de informações por si próprios, certifique-se de que lhes faculta instruções e orientações sobre como e quando devem efetuá-la. As instruções devem ser específicas da aplicação e das versões que utilizarem e de como as utilizam, e a orientação para quando e como a proteção de informações deve ser aplicada adequadamente na sua empresa. Para obter mais informações, consulte [Ajudar os utilizadores a proteger ficheiros ao utilizar o Azure Rights Management](../deploy-use/help-users.md).

Para obter informações acerca de como configurar estas aplicações para o Azure RMS, consulte [Configurar aplicações para o Azure Rights Management](../deploy-use/configure-applications.md).

> [!TIP]
> Para exemplos e capturas de ecrã das aplicações a utilizar o Azure RMS, consulte [O Azure RMS em ação: conteúdo visto pelos administradores e utilizadores](what-admins-users-see.md).

## Passos seguintes

Saiba mais acerca de como cada um dos seguintes suporta o Azure RMS:

-   [Aplicação de partilha RMS para Windows e plataformas móveis](sharing-app-support.md)

-   [Aplicações e serviços do Office](office-apps-services-support.md)

-   [Servidores de ficheiros que executam o Windows Server e utilizam a Infraestrutura de Classificação de Ficheiros (FCI)](file-server-support.md)

-   [Outras aplicações que suportam as APIs de RMS](api-support.md)



<!--HONumber=Apr16_HO4-->

