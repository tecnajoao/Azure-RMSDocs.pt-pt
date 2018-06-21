---
title: Como as aplicações suportam o Azure Rights Management a partir AIP
description: Compreender como as aplicações de utilizador final (como as aplicações do Office, Word, Excel, PowerPoint e Outlook) e serviços (como o Exchange e o SharePoint) utilizados mais frequentemente podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger os documentos e e-mails da sua organização.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: af3d103908aff785d48f70cc1cf89a7b9d17643e
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
ms.locfileid: "30207823"
---
# <a name="how-applications-support-the-azure-rights-management-service"></a>Como as aplicações suportam o serviço Azure Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize as seguintes informações para ajudar a compreender a forma como os utilizados mais frequentemente aplicações do utilizador final e os serviços podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger documentos e e-mails da sua organização. Estas aplicações incluem o Word, Excel, PowerPoint e Outlook. Os serviços incluem o Exchange e SharePoint.

> [!NOTE]
> Para saber que aplicações e versões são suportadas pelo serviço Azure Rights Management, consulte [Aplicações que suportam a proteção de dados do Azure Rights Management](../get-started/requirements-applications.md).

Em alguns casos, o serviço Azure Rights Management aplica automaticamente a proteção, de acordo com as políticas configuradas pelos administradores. Por exemplo, é este o caso com bibliotecas do SharePoint e regras de transporte do Exchange. Noutros casos, os utilizadores finais têm de aplicar a proteção próprios partir das suas aplicações. Por exemplo, selecione os utilizadores uma classificação de etiqueta que está configurado para aplicar a proteção, ou selecione um modelo ou selecione opções específicas. Proteção é aplicada por utilizadores é típica quando os utilizadores protegem um ficheiro para partilhar e também restringem o acesso ou utilização a utilizadores selecionados ou a utilizadores fora da organização.

Os modelos fazem com que seja mais fácil para os utilizadores (e administradores que configuram políticas) aplicar o nível correto de proteção e restringir o acesso a pessoas dentro da sua organização. Embora o serviço Azure Rights Management é fornecido com dois modelos predefinidos, provavelmente pretende criar modelos personalizados para reduzir o número de vezes quando os utilizadores e administradores tem de especificar opções individuais. Para obter mais informações sobre modelos, consulte [configurar e gerir modelos do Azure Information Protection](../deploy-use/configure-policy-templates.md).

Para os casos em que os utilizadores tem de aplicar a proteção, lembre-se de que lhes fornecer instruções e orientações sobre como e quando deve efetuar este procedimento. Efetue as instruções específicas da aplicação e das versões que utilizarem e como utilizam. Também fornecem orientações para quando e como os utilizadores devem aplicar a proteção que é adequada para a sua empresa. Para obter mais informações, consulte [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](../deploy-use/help-users.md).

Para obter mais informações sobre como configurar estas aplicações para o serviço Azure Rights Management do Azure Information Protection, consulte [Configurar aplicações para o Azure Rights Management](../deploy-use/configure-applications.md).

Os serviços de pesquisa podem ser integrados no Rights Management de diferentes formas. Por exemplo: 

- Exchange Online e Exchange Server utilizam a indexação do lado do serviço para que os e-mails protegidos de um utilizador sejam apresentados automaticamente nos respetivos resultados de pesquisa. 

- SharePoint Online e SharePoint Server aplicam proteção Rights Management a ficheiros apenas durante a transferência. Esta implementação significa que os resultados de pesquisa e indexação do SharePoint não são afetados por esta solução de proteção do documento. No entanto, se tiver um documento que pretende armazenar no SharePoint e este documento não deve ser devolvido nos resultados da pesquisa, proteja o documento antes de carregar para o SharePoint.

- Pesquisa de ambiente de trabalho do Windows utiliza um índice partilhado entre os diferentes utilizadores do dispositivo, por isso, para manter os dados nos documentos protegidos segura, não indexa os ficheiros protegidos. Isto significa que apesar dos resultados da pesquisa não incluírem ficheiros que protegeu, pode ter a certeza de que os ficheiros que contêm confidenciais dados não são ser apresentados nos resultados de pesquisa para outros utilizadores que podem iniciar sessão PC ou ligar ao seu PC. 

## <a name="next-steps"></a>Próximos passos

Saiba mais acerca de como cada uma das seguintes aplicações e serviços suportam o serviço Azure Rights Management:

-   [Aplicação de partilha RMS para Windows e plataformas móveis](sharing-app-support.md)

-   [Aplicações e serviços do Office](office-apps-services-support.md)

-   [Servidores de ficheiros que executam o Windows Server e utilizam a Infraestrutura de Classificação de Ficheiros (FCI)](file-server-support.md)

-   [Outras aplicações que suportam as APIs de RMS](api-support.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
