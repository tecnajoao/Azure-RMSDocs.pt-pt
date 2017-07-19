---
title: "Como as aplicações suportam o Azure Rights Management – AIP"
description: "Compreender como as aplicações de utilizador final (como as aplicações do Office, Word, Excel, PowerPoint e Outlook) e serviços (como o Exchange e o SharePoint) utilizados mais frequentemente podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger os documentos e e-mails da sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/26/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: db9f67c5baeea678bf288f4f10237ff4517d905b
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="how-applications-support-the-azure-rights-management-service"></a>Como as aplicações suportam o serviço Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

Utilize as seguintes informações para o ajudar a compreender como as aplicações de utilizador final (como as aplicações do Office, Word, Excel, PowerPoint e Outlook) e serviços (como o Exchange e o SharePoint) utilizados mais frequentemente podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger os documentos e e-mails da sua organização. 
> [!NOTE]
> Para saber que aplicações e versões são suportadas pelo serviço Azure Rights Management, consulte [Aplicações que suportam a proteção de dados do Azure Rights Management](../get-started/requirements-applications.md).

Em alguns casos, o serviço Azure Rights Management aplica automaticamente a proteção, de acordo com as políticas configuradas pelos administradores. Por exemplo, é este o caso com bibliotecas do SharePoint e regras de transporte do Exchange. Noutros casos, os utilizadores finais têm de aplicar a proteção de informações pessoalmente a partir das suas aplicações, por exemplo, ao selecionar uma etiqueta de classificação que tenha sido configurada para aplicar um modelo, ao selecionar um modelo diretamente ou ao selecionar opções específicas. A proteção aplicada pelos utilizadores é típica quando os utilizadores protegem um ficheiro a partilhar e restringem o acesso ou utilização a utilizadores selecionados ou a utilizadores fora da organização.

Os modelos fazem com que seja mais fácil para os utilizadores (e administradores que configuram políticas) aplicar o nível correto de proteção e restringir o acesso a pessoas dentro da sua organização. Embora o serviço Azure Rights Management inclua dois modelos predefinidos, é provável que pretenda criar modelos personalizados para reduzir as vezes em que é necessário especificar opções individuais. Para obter mais informações, consulte [Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md).

Para os casos em que os utilizadores têm de aplicar a proteção de informações por si próprios, certifique-se de que lhes faculta instruções e orientações sobre como e quando devem efetuá-la. As instruções devem ser específicas da aplicação e das versões que utilizarem e de como as utilizam, e a orientação para quando e como a proteção de informações deve ser aplicada adequadamente na sua empresa. Para obter mais informações, consulte [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](../deploy-use/help-users.md).

Para obter mais informações sobre como configurar estas aplicações para o serviço Azure Rights Management do Azure Information Protection, consulte [Configurar aplicações para o Azure Rights Management](../deploy-use/configure-applications.md).

Os serviços de pesquisa podem ser integrados no Rights Management de diferentes formas. Por exemplo: 

- O Exchange Online e o Exchange Server utilizam a indexação do lado do serviço para que os e-mails protegidos por RMS de um utilizador sejam apresentados automaticamente nos respetivos resultados de pesquisa. 

- O SharePoint Online e o SharePoint Server aplicam a proteção Rights Management aos ficheiros apenas durante a transferência, o que significa que a indexação e os resultados da pesquisa no SharePoint não são afetados por esta solução de proteção de documentos. No entanto, se tiver um documento que pretende armazenar no SharePoint e não deva ser devolvido nos resultados da pesquisa, proteja o ficheiro por RMS antes de o carregar para o SharePoint.

- A pesquisa do ambiente de trabalho do Windows utiliza um índice partilhado entre os diferentes utilizadores do dispositivo, pelo que, para manter a segurança dos dados nos documentos protegidos, não indexa os ficheiros protegidos por RMS. Isto significa que, apesar de os resultados da pesquisa não incluírem ficheiros que tenha protegido, pode ter a certeza de que os ficheiros com dados confidenciais não serão apresentados nos resultados da pesquisa para outros utilizadores que possam iniciar sessão ou ligar-se ao seu PC. 



## <a name="next-steps"></a>Passos seguintes

Saiba mais sobre como cada um dos seguintes suporta o serviço Azure Rights Management:

-   [Aplicação de partilha RMS para Windows e plataformas móveis](sharing-app-support.md)

-   [Aplicações e serviços do Office](office-apps-services-support.md)

-   [Servidores de ficheiros que executam o Windows Server e utilizam a Infraestrutura de Classificação de Ficheiros (FCI)](file-server-support.md)

-   [Outras aplicações que suportam as APIs de RMS](api-support.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
