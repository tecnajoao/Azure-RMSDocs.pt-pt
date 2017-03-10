---
title: FAQs sobre o Azure Information Protection
description: "Algumas perguntas mais frequentes sobre o Azure Information Protection e o respetivo serviço de proteção de dados, o Azure Rights Management (Azure RMS)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/24/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ebdbb045a60e30a78b8a5536415302e912995791
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Perguntas mais frequentes sobre o Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Tem uma pergunta sobre o Azure Information Protection ou o serviço Azure Rights Management (Azure RMS)? Verifique se a resposta está aqui.

Estas páginas de FAQ serão atualizadas regularmente e as novas adições serão indicadas nos anúncios mensais de atualizações de documentação no [Blogue do Enterprise Mobility and Security](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Qual é a diferença entre o Azure Information Protection e o Azure Rights Management?

O Azure Information Protection fornece classificação, etiquetagem e proteção para os documentos e e-mails de uma organização. A tecnologia de proteção utiliza o serviço Azure Rights Management, que agora faz parte do Azure Information Protection.

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>De que subscrição preciso para o Azure Information Protection e que funcionalidades estão incluídas?
Veja as [informações da subscrição](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) e a [lista de funcionalidades](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) no site do Azure Information Protection. 

Se tiver uma subscrição do Office 365 que inclui o Rights Management, transfira a [folha de dados de licenciamento do Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) a partir da página **Funcionalidades**.

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>O Azure Information Protection suporta cenários no local e híbridos?

Sim. Embora o Azure Information Protection seja uma solução baseada na cloud, o mesmo consegue classificar, etiquetar e proteger documentos e e-mails armazenados tanto no local como na cloud.

Se tiver servidores de ficheiros do Exchange Server, do SharePoint Server e do Windows, pode implementar o [conector do Rights Management](../deploy-use/deploy-rms-connector.md) para que estes servidores no local possam utilizar o serviço Azure Rights Management para proteger os seus e-mails e documentos. Também pode sincronizar e federar os seus controladores de domínio do Active Directory com o Azure AD para uma experiência de autenticação mais integrada para os utilizadores, por exemplo, ao utilizar o [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

O serviço Azure Rights Management gera e faz a gestão automática de certificados XrML conforme necessário, para não ter de utilizar um PKI no local. Para obter mais informações sobre como o Azure Rights Management utiliza certificados, veja a secção [Explicação passo a passo sobre como funciona o Azure RMS: primeira utilização, proteção de conteúdos, consumo de conteúdos](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) no artigo [Como funciona o Azure RMS?](../understand-explore/how-does-it-work.md).

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Já ouvi falar que uma nova versão irá estar disponível em breve para o Azure Information Protection. Quando será lançada?

A documentação técnica não contém informações sobre os lançamentos futuros. Para obter este tipo de informação e ter acesso aos anúncios de lançamento, leia o [Blogue Enterprise Mobility and Security](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services) e obtenha as atualizações mais recentes através de [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy) no Twitter. Se estiver interessado numa versão do Office, certifique-se de que vê também o [blogue do Office](https://blogs.office.com/).

## <a name="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas"></a>Onde posso encontrar informações de suporte para o Azure Information Protection, como informações legais, sobre conformidade e SLAs?

Veja [Informações de suporte e conformidade do Azure Information Protection](../understand-explore/compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Como posso comunicar um problema ou enviar feedback do Azure Information Protection?

Em alternativa, utilize os canais de suporte padrão ou [contacte o Suporte da Microsoft](information-support.md#to-contact-microsoft-support).

Para comentários como sugestões de melhorias ou novas funcionalidades: na aplicação do Office, no separador **Base** no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e comentários**. Na caixa de diálogo **Microsoft Azure Information Protection**, clique em **Enviar comentários**. Deste modo, envia um e-mail à equipa do Information Protection e anexa automaticamente os ficheiros de registo do seu PC. 

É também convidado a interagir com a nossa equipa de engenharia, no [site Yammer do Azure Information Protection](https://www.yammer.com/askipteam/). 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>O que posso fazer se a minha pergunta não constar aqui?

Em primeiro lugar, reveja as perguntas mais frequentes específicas sobre classificação e etiquetagem ou específicas sobre proteção de dados. O serviço Azure Rights Management (Azure RMS) fornece a tecnologia de proteção de dados do Azure Information Protection e o Azure RMS pode ser utilizado com ou sem classificação e etiquetagem: 

- [FAQs sobre a classificação e etiquetagem](faqs-infoprotect.md)

- [FAQs sobre a proteção de dados](faqs-rms.md)

Se não encontrar respostas às suas perguntas, utilize as ligações e os recursos indicados em [Informações e suporte do Azure Information Protection](information-support.md).

Além disso, existem FAQ criadas para utilizadores finais:

- [FAQ sobre a aplicação Azure Information Protection para iOS e Android](../rms-client/mobile-app-faq.md)

- [FAQ sobre a aplicação de partilha RMS para computadores Mac e Windows Phone](https://technet.microsoft.com/dn451248)

- [FAQ sobre a Aplicação de Partilha Rights Management para Windows](https://technet.microsoft.com/dn467883)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]

