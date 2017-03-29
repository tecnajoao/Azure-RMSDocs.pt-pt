---
title: "FAQs sobre classificação e identificação – AIP"
description: "Tem uma pergunta específica sobre classificação e etiquetagem através do Azure Information Protection? Verifique se a resposta está aqui."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: 6af0a81b31fb0a2e5437428dc8373dd997b18406
ms.sourcegitcommit: f0402cf14506b4c61a156a2baf7e69b7b16883a1
translationtype: HT
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Perguntas mais frequentes sobre a classificação e a etiquetagem no Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Tem uma pergunta sobre o Azure Information Protection especificamente sobre classificação e etiquetagem?  Verifique se a resposta está aqui. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>O que posso fazer com as capacidades de classificação no Azure Information Protection?

Experimente o nosso tutorial de início rápido para ver isto em funcionamento em apenas alguns minutos: [tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md).

Procure anúncios no [Blogue Enterprise Mobility and Security](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) e no nosso [site Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) estiverem disponíveis funcionalidades e capacidades adicionais. Seguem-se algumas limitações da versão atual, que incluem o seguinte:

- Os nomes das etiquetas e descrições são suportados apenas num idioma.

- Não existe nenhum registo centralizado para classificação e etiquetagem.

- As condições para classificação automática têm de ser expressões ou padrões.

- A capacidade de etiquetagem das aplicações do Office não se encontra disponível para dispositivos móveis (iOS e Android) e computadores Mac nem nas aplicações Web do Office (Office Online).

- As funcionalidades de classificação e etiquetagem não foram integradas com o Exchange Online nem com o SharePoint Online.

- O SDK para parceiros e programadores ainda não inclui as funcionalidades de classificação e etiquetagem.

A versão de fevereiro veio colmatar muitas das limitações anteriores. Para obter mais informações, veja o [anúncio do blogue](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/).

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>É necessário ser um administrador global para configurar a classificação e etiquetas?

Para configurar a política do Azure Information Protection, tem de iniciar sessão no portal do Azure como um administrador global do Azure Active Directory.

Se selecionar a opção para instalar a política de demonstração quando instalar o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018), não precisa de iniciar sessão no portal para ver e experimentar a funcionalidade de etiquetagem. A política de demonstração instala localmente uma política predefinida para o Azure Information Protection. Por isso, pode tentar etiquetar documentos e e-mails, mas não poderá alterar ou adicionar novas etiquetas sem iniciar sessão no portal do Azure. 

## <a name="which-options-in-the-azure-portal-are-p1-or-p2"></a>Que opções no portal do Azure são P1 ou P2?

Para verificar quais as funcionalidades incluídas na subscrição do **Azure Information Protection Premium 1** (P1), em comparação com a subscrição do **Azure Information Protection Premium 2** (P2), veja a [lista de funcionalidades](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) do site do Azure Information Protection. No entanto, como guia geral, as funcionalidades avançadas, tal como classificação automática e tenha sua própria chave (HYOK), são específicas para a subscrição do Azure Information Protection Premium 2.

## <a name="can-a-file-have-more-than-one-classification"></a>Um ficheiro pode conter mais do que uma classificação?

Os utilizadores podem selecionar apenas uma etiqueta de cada vez para cada documento ou e-mail, o que habitualmente acaba por criar apenas uma classificação. No entanto, se os utilizadores selecionarem uma subetiqueta, esta aplica habitualmente duas etiquetas ao mesmo tempo; uma etiqueta principal e uma etiqueta secundária. Ao utilizar subetiquetas, um ficheiro pode ter duas classificações que indicam uma relação principal\subordinado e permitem um nível adicional de controlo.

Por exemplo, a etiqueta **Confidencial** pode conter subetiquetas como **Informações jurídicas** e **Finanças**. Pode aplicar diferentes marcas de classificação visual e diferentes modelos do Rights Management a estas subetiquetas. Um utilizador não pode selecionar a etiqueta **Confidencial**, mas apenas uma das respetivas subetiquetas, como **Informações jurídicas**. Como resultado, a etiqueta definida será **Confidencial\Informações jurídicas**. Os metadados do ficheiro em questão incluem uma propriedade de texto personalizado para **Confidencial**, uma propriedade de texto personalizado para **Informações jurídicas** e outra com ambos os valores (**Confidencial/Informações jurídicas**). 

Quando utilizar subetiquetas, não configure as marcas visuais, a proteção e as condições na etiqueta principal. Quando utilizar subetiquetas, configure esta definição apenas na subetiqueta. Se configurar estas definições na etiqueta principal e na respetiva subetiqueta, as definições da subetiqueta têm prioridade.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Quando um e-mail tem uma etiqueta, os anexos também recebem a mesma etiqueta automaticamente?

Não. Quando coloca uma etiqueta numa mensagem de e-mail com anexos, esses anexos não herdam a mesma etiqueta. Os anexos permanecem sem uma etiqueta ou retêm uma etiqueta aplicada separadamente. No entanto, se a etiqueta do e-mail aplicar proteção, essa proteção é aplicada aos anexos.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Qual a diferença entre a classificação do Azure Information Protection para e-mails e a classificação de mensagens do Exchange?

A classificação de mensagens do Exchange é uma funcionalidade mais antiga que pode classificar e-mails e é implementada independentemente da classificação do Azure Information Protection. Porém, pode integrar as duas soluções para que, quando os utilizadores classificarem um e-mail com a aplicação Web do Outlook e em algumas aplicações de e-mail móveis, a classificação do Azure Information Protection e as marcas de etiqueta correspondentes sejam adicionadas automaticamente. O Exchange adiciona a classificação e o cliente do Azure Information Protection aplica as definições de etiquetas correspondentes a essa classificação.

Apesar de a aplicação Web do Outlook ainda não suportar nativamente a classificação e proteção do Azure Information Protection, pode utilizar esta mesma técnica para utilizar as suas etiquetas com este cliente de e-mail além do cliente Outlook de ambiente de trabalho.

Para obter esta solução: 

1. Utilize o cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) do Exchange PowerShell para criar classificações de mensagens com a propriedade Nome que mapeia os seus nomes de etiquetas na sua política do Azure Information Protection. 

2. Crie uma regra de transporte do Exchange para cada etiqueta: aplique a regra quando as propriedades da mensagem incluírem a classificação que configurou e modifique as propriedades das mensagens para definir um cabeçalho da mensagem. 

    Para o cabeçalho da mensagem, encontrará as informações a especificar ao inspecionar as propriedades de um ficheiro do Office que classificou com a etiqueta do Azure Information Protection. Identifique a propriedade do ficheiro com o formato **MSIP_Label_<GUID>_Enabled** e especifique esta cadeia para o cabeçalho da mensagem e, em seguida, especifique como **Verdadeiro** o valor do cabeçalho. Por exemplo, o cabeçalho da sua mensagem poderá ser semelhante a esta cadeia: **MSIP_Label_132616b8-f72d-5d1e-aec1-dfd89eb8c5b2_Enabled**


Posteriormente, acontecerá o seguinte quando os utilizadores utilizarem a aplicação de acesso Web do Outlook ou um cliente de dispositivo móvel que suporta a proteção da gestão de direitos: 

- Os utilizadores selecionam a classificação de mensagens do Exchange e enviam o e-mail.

- A regra do Exchange deteta a classificação do Exchange e modifica o cabeçalho da mensagem em conformidade para adicionar a classificação do Azure Information Protection.

- Quando os destinatários que executam o cliente do Azure Information Protection veem o e-mail no Outlook, verão a etiqueta do Azure Information Protection atribuída e quaisquer cabeçalhos, rodapés ou marcas de água de e-mail correspondentes. 

Se as suas etiquetas do Azure Information Protection aplicarem a proteção da gestão de direitos, adicione esta opção à configuração da regra ao selecionar a opção para modificar a segurança da mensagem, aplique a proteção de direitos e, em seguida, selecione a opção Não Reencaminhar ou modelo do RMS.

Também pode configurar as regras de transporte para proceder ao mapeamento inverso: quando uma etiqueta do Azure Information Protection é detetada, é definida uma classificação de mensagens do Exchange correspondente. Para efetuar este procedimento:

- Para cada etiqueta do Azure Information Protection, crie uma regra de transporte que seja aplicada quando o cabeçalho **msip_labels** incluir o nome da sua etiqueta (por exemplo, **Confidencial**) e aplique uma classificação de mensagens que mapeie esta etiqueta.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Como podem as soluções DLP e outras aplicações ser integradas com o Azure Information Protection?

Uma vez que o Azure Information Protection utiliza metadados persistentes para classificação, que incluem uma etiqueta de texto não encriptado, estas informações podem ser lidas por soluções DLP e outras aplicações. Nos ficheiros, estes metadados são armazenados em propriedades personalizadas; nos e-mails, estas informações estão indicadas nos cabeçalhos de e-mail.

## <a name="how-do-i-sign-in-as-a-different-user"></a>Como posso iniciar sessão como um utilizador diferente?

Num ambiente de produção, normalmente não precisa de iniciar sessão como um utilizador diferente quando está a utilizar o cliente do Azure Information Protection. No entanto, poderá ter de o fazer se tiver vários inquilinos. Por exemplo, tem um inquilino de teste além do inquilino do Office 365 ou do Azure que a sua organização utiliza.

Pode verificar com que conta tem sessão iniciada atualmente através da caixa de diálogo do **Microsoft Azure Information Protection**: abra uma aplicação do Office e, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e comentários**. O nome da sua conta é apresentado na secção **Estado do cliente**.

Especialmente quando estiver a utilizar uma conta de administrador, verifique o nome de domínio da conta com sessão iniciada que é apresentada. Por exemplo, se tiver uma conta de administrador em dois inquilinos diferentes, pode não perceber que tem sessão iniciada com o nome da conta certo, mas com o domínio errado. Um sinal de tal engano pode ser a impossibilidade de transferir a política do Azure Information Protection ou não ver as etiquetas ou o comportamento esperado.

Para iniciar sessão como um utilizador diferente, tem de editar o registo:

1. Com um editor de registo, navegue para **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP** e elimine o valor **TokenCache**.

2. Reinicie as aplicações do Office abertas e inicie sessão com a sua conta de utilizador diferente. Se não vir um pedido na aplicação do Office para iniciar sessão no serviço Azure Information Protection, volte à caixa de diálogo do **Microsoft Azure Information Protection** e clique em **Iniciar sessão** na secção **Estado do cliente** atualizada.

Além disso,

- Se estiver a utilizar o início de sessão único, terá de terminar sessão no Windows e iniciar sessão com outra conta de utilizador após editar o registo. O cliente do Azure Information Protection fará a autenticação automaticamente através da conta de utilizador com sessão iniciada.

- Se pretender reinicializar o ambiente do serviço Azure Rights Management (também conhecido como arranque do sistema), pode fazê-lo através da opção **Repor** da [ferramenta RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Se pretender eliminar a política do Azure Information Protection atualmente transferida, pode fazê-lo ao eliminar o ficheiro **Policy.msip** da pasta %localappdata%\Microsoft\MSIP.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]