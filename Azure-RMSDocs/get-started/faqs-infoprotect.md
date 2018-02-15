---
title: "FAQs sobre classificação e identificação – AIP"
description: "Tem uma pergunta específica sobre classificação e etiquetagem através do Azure Information Protection? Verifique se a resposta está aqui."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: b9885f020f78bd20bec39c8c1ede2018d6254a7b
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2018
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Perguntas mais frequentes sobre a classificação e a etiquetagem no Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Tem uma pergunta sobre o Azure Information Protection especificamente sobre classificação e etiquetagem?  Verifique se a resposta está aqui. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>O que posso fazer com as capacidades de classificação no Azure Information Protection?

Experimente o nosso tutorial de início rápido para ver isto em funcionamento em apenas alguns minutos: [tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md).

Procure anúncios no [Blogue Enterprise Mobility and Security](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-information-protection) e no nosso [site Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) estiverem disponíveis funcionalidades e capacidades adicionais. Seguem-se algumas limitações da versão atual, que incluem o seguinte:

- Não existe nenhum registo centralizado para classificação e etiquetagem.

- Nenhuma capacidade etiquetas em aplicações do Office para computadores Mac e dispositivos móveis (iOS e Android) ou as aplicações web do Office (Office Online).

- As funcionalidades de classificação e etiquetagem não foram integradas com o Exchange Online nem com o SharePoint Online.

Pedir novas funcionalidades e votar em pedidos, visitando o [site voz do utilizador](https://msip.uservoice.com/) para o Azure Information Protection.

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>É necessário ser um administrador global para configurar a classificação e etiquetas?

Com a função de administrador de proteção de informações introduzidas recentemente, esta questão está agora respondida na página de FAQ principal: [tem de ser um administrador global para configurar o Azure Information Protection ou posso delegar noutros administradores?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

Se selecionar a opção para instalar a política de demonstração quando instalar o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018), não precisa de iniciar sessão no portal para ver e experimentar a funcionalidade de etiquetagem. Localmente a política de demonstração instala uma política predefinida para o Azure Information Protection, que pode tentar Etiquetar documentos e e-mails, mas não é possível alterar ou adicionar novas etiquetas sem iniciar sessão no portal do Azure. 

## <a name="which-options-in-the-azure-portal-are-p2"></a>Que opções no portal do Azure são P2?

As opções no portal do Azure que necessitam de uma subscrição do **Azure Information Protection Premium 2** (P2) agora incluem uma mensagem de pop-up com informações para as identificar. Para obter mais informações sobre as funcionalidades que estão incluídas nas subscrições P1 e P2, veja a [lista de funcionalidades](https://www.microsoft.com/cloud-platform/azure-information-protection-features) do site do Azure Information Protection.

## <a name="can-a-file-have-more-than-one-classification"></a>Um ficheiro pode conter mais do que uma classificação?

Os utilizadores podem selecionar apenas uma etiqueta de cada vez para cada documento ou e-mail, o que habitualmente acaba por criar apenas uma classificação. No entanto, se os utilizadores selecionarem um sublabel, isto, na verdade, aplica-se duas etiquetas em simultâneo; uma etiqueta principal e uma etiqueta secundária. Ao utilizar sublabels, um ficheiro pode ter duas classificações denotam uma relação de parent\child para um nível adicional de controlo.

Por exemplo, a etiqueta **confidencial** pode conter sublabels como **legais** e **financeiro**. Pode aplicar marcações visuais de classificação diferentes e modelos de Rights Management diferentes a estes sublabels. Não é possível selecionar um utilizador a **confidencial** etiqueta autonomamente; apenas um dos respetivos sublabels, tais como **legais**. Como resultado, a etiqueta definida será **Confidencial\Informações jurídicas**. Os metadados do ficheiro em questão incluem uma propriedade de texto personalizado para **Confidencial**, uma propriedade de texto personalizado para **Informações jurídicas** e outra com ambos os valores (**Confidencial/Informações jurídicas**). 

Quando utilizar sublabels, não configure marcas visuais, proteção e condições em que a etiqueta principal. Quando utiliza subníveis, configure estas definições no sublabel apenas. Se configurar estas definições na etiqueta principal e o respetivo sublabel, as definições no sublabel precedência.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Quando um e-mail tem uma etiqueta, os anexos também recebem a mesma etiqueta automaticamente?

Não. Quando coloca uma etiqueta numa mensagem de e-mail com anexos, esses anexos não herdam a mesma etiqueta. Os anexos permanecem sem uma etiqueta ou retêm uma etiqueta aplicada separadamente. No entanto, se a etiqueta do e-mail aplicar proteção, essa proteção é aplicada aos anexos.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Como podem as soluções DLP e outras aplicações ser integradas com o Azure Information Protection?

Uma vez que o Azure Information Protection utiliza metadados persistentes para classificação, que incluem uma etiqueta de texto não encriptado, estas informações podem ser lidas por soluções DLP e outras aplicações. 

- Para documentos do Word (. doc e. docx), folhas de cálculo do Excel (xls e ou), apresentações do PowerPoint (.ppt e .pptx) e documentos PDF (. pdf), estes metadados são armazenados na propriedade personalizada seguinte: **MSIP_Label_\<GUID > _ Ativado = True**  

- Nos e-mails, estas informações são armazenadas no cabeçalho de x: **msip_labels: MSIP_Label_\<GUID > _Enabled = True;**  

Para identificar o GUID para uma etiqueta, localize o valor de ID da etiqueta no painel de etiqueta, ao ver ou configurar a política do Azure Information Protection no portal do Azure. Para os ficheiros que tenham etiquetas aplicadas, também pode executar o [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) cmdlet do PowerShell para identificar o GUID (MainLabelId ou SubLabelId). Quando uma etiqueta tem sublabels, especifique sempre o GUID de apenas um sublabel e não a etiqueta principal.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Qual a diferença entre a classificação do Azure Information Protection para e-mails e a classificação de mensagens do Exchange?

A classificação de mensagens do Exchange é uma funcionalidade mais antiga que pode classificar e-mails e é implementada independentemente da classificação do Azure Information Protection. 

Porém, pode integrar as duas soluções para que, quando os utilizadores classificarem um e-mail com o Outlook na Web e em algumas aplicações de correio móveis, a classificação do Azure Information Protection e as marcas de etiqueta correspondentes sejam adicionadas automaticamente. 

Pode utilizar esta mesma técnica para utilizar as etiquetas com o Outlook na Web e estas aplicações de correio móvel.

Para obter os passos de configuração, veja [Integrar a classificação de mensagem do Exchange com o Azure Information Protection para uma solução de etiquetagem do dispositivo móvel](../rms-client/client-admin-guide-customizations.md#integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution). 



[!INCLUDE[Commenting house rules](../includes/houserules.md)]
