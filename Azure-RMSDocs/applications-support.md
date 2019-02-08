---
title: Como as aplicações suportam o Azure Rights Management do AIP
description: Compreender como as aplicações de utilizador final (como as aplicações do Office, Word, Excel, PowerPoint e Outlook) e serviços (como o Exchange e o SharePoint) utilizados mais frequentemente podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger os documentos e e-mails da sua organização.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d8e1164d82304bcf28aa91d2e1708b10fd946ba3
ms.sourcegitcommit: 8558af7116f62414054feffa346aba197a1250d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2019
ms.locfileid: "55559806"
---
# <a name="how-applications-support-the-azure-rights-management-service"></a>Como as aplicações suportam o serviço Azure Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize as seguintes informações para ajudar a compreender como os utilizados mais frequentemente aplicações do utilizador final e serviços podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger documentos e e-mails da sua organização. Esses aplicativos incluem o Word, Excel, PowerPoint e Outlook. Os serviços incluem o Exchange e SharePoint.

> [!NOTE]
> Para saber que aplicações e versões são suportadas pelo serviço Azure Rights Management, consulte [Aplicações que suportam a proteção de dados do Azure Rights Management](./requirements-applications.md).

Em alguns casos, o serviço Azure Rights Management aplica automaticamente a proteção, de acordo com as políticas configuradas pelos administradores. Por exemplo, é este o caso com bibliotecas do SharePoint e regras de transporte do Exchange. Noutros casos, os utilizadores finais têm de aplicar a proteção próprios nas respetivas aplicações. Por exemplo, selecione os utilizadores, uma classificação de etiqueta, ou seja configurado para aplicar a proteção ou selecione um modelo ou selecionar opções específicas. Proteção aplicada pelos utilizadores é típica quando os utilizadores protegem um ficheiro a partilhar e também restringem o acesso ou utilização a utilizadores selecionados ou a utilizadores fora da organização.

Os modelos fazem com que seja mais fácil para os utilizadores (e administradores que configuram políticas) aplicar o nível correto de proteção e restringir o acesso a pessoas dentro da sua organização. Embora o serviço Azure Rights Management vem com dois modelos predefinidos, provavelmente quer criar modelos personalizados para reduzir as vezes em utilizadores e administradores necessário especificar opções individuais. Para obter mais informações sobre os modelos, consulte [configurando e gerenciando modelos do Azure Information Protection](configure-policy-templates.md).

Para os casos em que os utilizadores tem de aplicar a proteção, certifique-se de que lhes faculta instruções e orientações sobre como e quando deve fazê-lo. Certifique as instruções específicas da aplicação e das versões que utilizarem e como eles as utilizam. Também fornece orientações sobre quando e como os utilizadores devem aplicar a proteção adequada para a sua empresa. Para obter mais informações, consulte [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](help-users.md).

Para obter mais informações sobre como configurar estas aplicações para o serviço Azure Rights Management do Azure Information Protection, consulte [Configurar aplicações para o Azure Rights Management](configure-applications.md).

Os serviços de pesquisa podem ser integrados no Rights Management de diferentes formas. Por exemplo: 

- Exchange Online e Exchange Server utilizam a indexação do lado do serviço para que os e-mails protegidos de um utilizador sejam apresentados automaticamente nos respetivos resultados de pesquisa. 

- SharePoint Online e SharePoint Server aplicam-se proteção do Rights Management aos ficheiros apenas durante a transferência. Essa implementação significa que os resultados de indexação e pesquisa no SharePoint não são afetados por esta solução de proteção de documentos. No entanto, se tiver um documento que pretende armazenar no SharePoint e este documento não deve ser devolvido nos resultados da pesquisa, proteger o documento antes de o carregar para o SharePoint.

- Pesquisa de desktop do Windows utiliza um índice partilhado entre os diferentes utilizadores do dispositivo, por isso, a proteger os dados nos documentos protegidos, não indexa os ficheiros protegidos. Isso significa que embora os resultados da pesquisa não incluírem ficheiros que protegeu, pode ter a garantia de que os ficheiros que contêm dados confidenciais não são apresentados nos resultados de pesquisa para outros utilizadores que podem iniciar sessão no seu PC ou ligar ao seu PC. 

## <a name="next-steps"></a>Passos Seguintes

Saiba mais sobre como cada um dos aplicativos e serviços seguintes suporta o serviço Azure Rights Management:

-   [Aplicações e serviços do Office](office-apps-services-support.md)

-   [Servidores de ficheiros que executam o Windows Server e utilizam a Infraestrutura de Classificação de Ficheiros (FCI)](file-server-support.md)

-   [Outras aplicações que suportam as APIs de RMS](api-support.md)

