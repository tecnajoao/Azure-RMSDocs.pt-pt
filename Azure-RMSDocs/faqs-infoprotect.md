---
title: FAQs sobre classificação e identificação – AIP
description: Tem uma pergunta específica sobre classificação e etiquetagem através do Azure Information Protection? Verifique se a resposta está aqui.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/02/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: 34f64cc28762f8eb08089b188fbb40c7358e4807
ms.sourcegitcommit: 8da0aa8f9bb9f91375580a703682d23a81a441bf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58809986"
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Perguntas mais frequentes sobre a classificação e a etiquetagem no Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Tem uma pergunta sobre o Azure Information Protection especificamente sobre classificação e etiquetagem?  Verifique se a resposta está aqui. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>O que posso fazer com as capacidades de classificação no Azure Information Protection?

Experimente o nosso [editar a política e criar uma nova etiqueta](infoprotect-quick-start-tutorial.md) tutorial para ver isto em funcionamento em apenas alguns minutos.

Procure anúncios no [blogue Enterprise Mobility + Security](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity/label-name/Azure%20Information%20Protection) e no nosso [site do Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) para quando as funcionalidades adicionais e capacidades ficam disponíveis. Seguem-se algumas limitações da versão atual, que incluem o seguinte:

- Sem capacidade de etiquetagem nas aplicações web do Office (Office Online).

- As funcionalidades de classificação e etiquetagem não foram integradas com o Exchange Online nem com o SharePoint Online.

> [!NOTE]
> **Agora em pré-visualização**:
> - Centralizada de relatórios para classificação e etiquetagem. Para obter mais informações, consulte [centralização de relatórios do Azure Information Protection](reports-aip.md).
>
>**Lançada recentemente**:
> - Capacidade de etiquetagem incorporadas para aplicações do Office para dispositivos móveis (iOS e Android) e computadores Mac. Para obter mais informações, consulte [aplicar etiquetas de sensibilidade aos seus documentos e e-mail do Office](https://aka.ms/officemipdocs).

Pedir novas funcionalidades e votar nos pedidos, visite o [site do UserVoice](https://msip.uservoice.com/) do Azure Information Protection.

## <a name="which-preview-client-do-i-install-for-testing-new-functionality"></a>O cliente de pré-visualização instalar nova funcionalidade de teste?

Atualmente, existem dois clientes de pré-visualização para Windows: 

- O **cliente Azure Information Protection** que transfere etiquetas e as definições de política a partir do portal do Azure. Este cliente tem por base a versão de disponibilidade geral do cliente.

- O **do Azure Information Protection unified cliente etiquetagem** que downloads a etiquetas e as definições de política de um dos centros de administração: A segurança do Office 365 e Centro de conformidade, o Centro de segurança do Microsoft 365 ou o Centro de conformidade do Microsoft 365. Este cliente está em pré-visualização segundo.

Recomendamos que teste com o cliente de etiquetagem unificado do Azure Information Protection se a sua atual conjunto de recursos e funcionalidade de cumprem os requisitos comerciais. Se não, ou se tiver configurado as etiquetas no portal do Azure que ainda não ainda [migrados para a loja de etiquetagem unificada](configure-policy-migrate-labels.md), utilizar o cliente do Azure Information Protection.

Para obter mais informações, incluindo uma tabela de comparação de funções e funcionalidades, consulte [escolher qual cliente Azure Information Protection para utilizar](./rms-client/use-client.md#choose-which-azure-information-protection-client-to-use).

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>É necessário ser um administrador global para configurar a classificação e etiquetas?

Com a função de administrador do Information Protection recém-lançado, este é agora às suas perguntas na página de FAQ principal: [Precisa de ser um administrador global para configurar o Azure Information Protection, ou posso delegar noutros administradores?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

Se selecionar a opção para instalar a política de demonstração quando instalar o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018), não precisa de iniciar sessão no portal para ver e experimentar a funcionalidade de etiquetagem. Localmente a política de demonstração instala uma política predefinida do Azure Information Protection, para que pode tentar Etiquetar documentos e e-mails, mas não é possível alterar ou adicionar novas etiquetas sem iniciar sessão no portal do Azure. 

## <a name="can-a-file-have-more-than-one-classification"></a>Um ficheiro pode conter mais do que uma classificação?

Os utilizadores podem selecionar apenas uma etiqueta de cada vez para cada documento ou e-mail, o que habitualmente acaba por criar apenas uma classificação. No entanto, se os utilizadores selecionarem uma subetiqueta, esta aplica habitualmente duas etiquetas ao mesmo tempo; uma etiqueta principal e uma etiqueta secundária. Ao utilizar subetiquetas, um ficheiro pode ter duas classificações que indicam uma relação principal\subordinado e permitem um nível adicional de controle.

Por exemplo, a etiqueta **confidencial** pode conter subetiquetas como **legais** e **Finanças**. Pode aplicar marcações visuais de classificação diferentes e diferentes modelos do Rights Management a estas subetiquetas. Não é possível selecionar um utilizador a **confidencial** etiqueta por si só, mas apenas uma das suas subetiquetas, tal como **legais**. Como resultado, a etiqueta definida será **Confidencial\Informações jurídicas**. Os metadados do ficheiro em questão incluem uma propriedade de texto personalizado para **Confidencial**, uma propriedade de texto personalizado para **Informações jurídicas** e outra com ambos os valores (**Confidencial/Informações jurídicas**). 

Quando utilizar subetiquetas, não configure marcas visuais, proteção e as condições na etiqueta principal. Quando utiliza subníveis, configure esta definição em apenas a subetiqueta. Se configurar estas definições na etiqueta principal e na respetiva subetiqueta, as definições da subetiqueta têm prioridade.

## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>Como posso impedir alguém da remover ou alterar uma etiqueta?

Embora haja uma [definição de política](configure-policy-settings.md) requer que os utilizadores para o estado por que motivo está a reduzir uma etiqueta de classificação, remover uma etiqueta ou remover a proteção, esta definição não impede que estas ações. Para impedir que os utilizadores de remover ou alterar uma etiqueta, o conteúdo já deve ser protegido e as permissões de proteção não conceder ao utilizador a exportação ou controlo total [direito de utilização](configure-usage-rights.md). 

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Quando um e-mail tem uma etiqueta, os anexos também recebem a mesma etiqueta automaticamente?

Não. Quando coloca uma etiqueta numa mensagem de e-mail com anexos, esses anexos não herdam a mesma etiqueta. Os anexos permanecem sem uma etiqueta ou retêm uma etiqueta aplicada separadamente. No entanto, se a etiqueta do e-mail aplicar proteção, essa proteção é aplicada aos anexos do Office.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Como podem as soluções DLP e outras aplicações ser integradas com o Azure Information Protection?

Porque o Azure Information Protection utiliza metadados persistentes para classificação, que incluem uma etiqueta de texto não encriptado, estas informações podem ser lidos por soluções DLP e outras aplicações. 

Para obter mais informações sobre estes metadados, consulte [Etiquetar informações armazenadas em e-mails e documentos](configure-policy.md#label-information-stored-in-emails-and-documents).

Para obter exemplos de como utilizar estes metadados com as regras de fluxo de correio Exchange Online, consulte [configurar o Exchange Online regras de fluxo de correio etiquetas do Azure Information Protection](configure-exo-rules.md).

## <a name="can-i-create-a-document-template-that-automatically-includes-the-classification"></a>Pode criar um modelo de documento que inclui a classificação automaticamente?

Sim. Pode configurar uma etiqueta para [aplicam-se de um cabeçalho ou rodapé que inclui o nome de etiqueta](configure-policy-markings.md). Mas se de que não cumprem os requisitos, pode criar um modelo de documento com a formatação que pretende e adicionar a classificação como um código de campo. 

Por exemplo, poderá ter uma tabela no cabeçalho do documento que exibe a classificação. Em alternativa, utilizar palavras específicas utilizadas para obter uma introdução que faz referência a classificação do documento.

Para adicionar este código de campo no seu documento:

1. Etiquetar o documento e salvá-lo. Esta ação cria novos campos de metadados que agora pode utilizar para o seu código de campo.

2. No documento, posicione o cursor em que pretende adicionar a classificação a etiqueta e, em seguida, a partir da **inserir** separador, selecione **texto** > **partes rápidas**  >  **Campo**.

3. Na **campo** caixa de diálogo, da **categorias** menu pendente, selecione **informações do documento**. Em seguida, a partir da **nomes de campos** lista pendente, selecione **DocProperty**.

4. Partir do **propriedade** menu pendente, selecione **sensibilidade**e selecione **OK**.

Classificação da etiqueta atual é apresentada no documento e este valor será atualizado automaticamente sempre que abrir o documento ou utiliza o modelo. Portanto, se a etiqueta for alterado, a classificação que é apresentada para esse código de campo é atualizada automaticamente no documento.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Qual a diferença entre a classificação do Azure Information Protection para e-mails e a classificação de mensagens do Exchange?

A classificação de mensagens do Exchange é uma funcionalidade mais antiga que pode classificar e-mails e é implementada independentemente da classificação do Azure Information Protection. 

Porém, pode integrar as duas soluções para que, quando os utilizadores classificarem um e-mail com o Outlook na Web e em algumas aplicações de correio móveis, a classificação do Azure Information Protection e as marcas de etiqueta correspondentes sejam adicionadas automaticamente. 

Pode utilizar esta mesma técnica para utilizar as etiquetas com o Outlook na Web e estas aplicações de correio móvel.

Para obter os passos de configuração, veja [Integrar a classificação de mensagem do Exchange com o Azure Information Protection para uma solução de etiquetagem do dispositivo móvel](./rms-client/client-admin-guide-customizations.md#integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution). 



