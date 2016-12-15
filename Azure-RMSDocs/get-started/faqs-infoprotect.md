---
title: "Perguntas mais frequentes sobre a classificação e a etiquetagem | Azure Information Protection"
description: "Tem alguma pergunta sobre a versão de pré-visualização do Azure Information Protection? Verifique se a resposta está aqui."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 23c437479c756f2a9335606e686f117d514a38f6
ms.openlocfilehash: ba67bb149b0128b068c86dcf849e2dd49edbf6a7


---

# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Perguntas mais frequentes sobre a classificação e a etiquetagem no Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Tem uma pergunta sobre o Azure Information Protection especificamente sobre classificação e etiquetagem?  Verifique se a resposta está aqui. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>O que posso fazer com as capacidades de classificação no Azure Information Protection?

O cliente do Azure Information Protection adiciona uma barra do Information Protection para aplicações do Microsoft Office que lhe permite ver e modificar etiquetas de classificação atribuídas a dados. A classificação pode ser efetuada manualmente, recomendada para si ou aplicada automaticamente. No que respeita às classificações que especificar, os dados podem ser protegidos com um serviço de Gestão de Direitos.  

As etiquetas de classificação e o comportamento são configurados no portal do Azure. Pode utilizar a política incorporada predefinida para avaliar rapidamente o Azure Information Protection ou personalizar por completo as suas políticas. Pode alterar as cores, os nomes e a ordem das etiquetas de classificação que os utilizadores veem. Também pode configurar descrições e marcas visuais de classificação como cabeçalho, rodapé ou uma marca d'água.

Experimente o nosso tutorial de início rápido para ver isto em funcionamento em apenas alguns minutos: [tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md).

A versão atual apresenta as seguintes limitações. Procure anúncios no [Blogue Enterprise Mobility and Security](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) e no nosso [site Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) quando estiverem disponíveis funcionalidades e capacidades adicionais:

- Os nomes das etiquetas e descrições são suportadas apenas num idioma.

- Não existe nenhum registo centralizado para classificação e etiquetagem.

- As condições para classificação automática têm de ser expressões ou padrões.

- As aplicações do Office para dispositivos móveis (iOS e Android), computadores Mac e aplicações Web do Office (Office Online) ainda não são suportadas.

- Não existe integração com o Exchange Online ou o SharePoint Online.

- O SDK para parceiros e programadores não está disponível.

Algumas das limitações listadas anteriormente estão agora disponíveis na pré-visualização. Para obter mais informações, veja o anúncio de mensagem de blogue: [Azure Information Protection December preview now available (Pré-visualização de Dezembro do Azure Information Protection já disponível)](https://blogs.technet.microsoft.com/enterprisemobility/2016/12/07/azure-information-protection-december-preview-now-available/).


## <a name="do-i-need-to-be-a-global-admin-to-try-azure-information-protection"></a>É necessário ser um administrador global para experimentar o Azure Information Protection?

Para configurar a política do Azure Information Protection, tem de iniciar sessão no portal do Azure como um administrador global do Azure Active Directory.

No entanto, se selecionar a opção para instalar a política de demonstração quando instalar o [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018), não precisa de iniciar sessão no portal para ver e experimentar a funcionalidade de etiquetagem. A política de demonstração instala localmente a política predefinida do Azure Information Protection, pelo que pode tentar etiquetar documentos e e-mails, mas não pode alterar ou adicionar novas etiquetas sem iniciar sessão no portal do Azure. 

## <a name="which-options-in-the-azure-portal-are-p1-or-p2"></a>Que opções no portal do Azure são P1 ou P2?

Para verificar quais as funcionalidades incluídas na subscrição do **Azure Information Protection Premium 1** (P1), em comparação com a subscrição do **Azure Information Protection Premium 2** (P2), consulte a [lista de funcionalidades](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) do site do Azure Information Protection. No entanto, como guia geral, as funcionalidades avançadas, tal como classificação automática e tenha sua própria chave (HYOK), são específicas para a subscrição do Azure Information Protection Premium 2.

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>O Azure Information Protection suporta cenários no local e híbridos?

O Azure Information Protection é uma solução baseada na nuvem. Se estiver interessado em implementar o Azure Information Protection num cenário híbrido, contacte a equipa do Information Protection, enviando um e-mail para askipteam@microsoft.com.

## <a name="how-do-computers-get-the-policy-information-from-azure-information-protection-and-how-often-is-it-refreshed"></a>Como é que os computadores obtêm informações de política do Azure Information Protection e com que frequência são atualizados?

Sempre que um utilizador abre uma aplicação do Office, o cliente do Azure Information Protection verifica se existe uma versão posterior da política do Azure Information Protection. Além disso, as aplicações do Office são verificadas a cada 24 horas. Se houver uma versão posterior, o cliente transfere-a utilizando uma ligação HTTPS para proteger os dados. 

Se várias instâncias da aplicação Office forem carregadas quando uma nova política do Azure Information Protection é publicada, deve fechar todas as instâncias para obter a versão mais recente da política. Por exemplo, se tiver dois documentos do Word abertos e pretende testar a política do Azure Information Protection num único documento: feche ambos documentos do Word e reabra o documento que pretende utilizar com a política mais recente.

## <a name="where-can-files-be-stored-to-use-azure-information-protection"></a>Onde podem ser armazenados os ficheiros para utilizar o Azure Information Protection? 

Uma vez que o Azure Information Protection aplica etiquetas persistentes e proteção a ficheiros e e-mails, é irrelevante o local onde os ficheiros são armazenados.

## <a name="can-i-classify-only-new-data-or-can-i-also-classify-existing-data"></a>Posso classificar apenas novos dados ou posso também classificar dados existentes?

As ações de política do Azure Information Protection entram em vigor quando os documentos são guardados e os e-mails são enviados, tanto para novo conteúdo como para alterações a conteúdo existente. 

## <a name="can-i-use-azure-information-protection-for-classification-only-without-enforcing-encryption-and-restricting-usage-rights"></a>Posso utilizar o Azure Information Protection apenas para classificação, sem impor encriptação e restringir direitos de utilização?

Sim. Pode configurar uma política do Azure Information Protection que aplique apenas uma etiqueta. Na verdade, esperamos que seja este o caso da maior parte das redes de implementação em que é necessário proteger apenas um subconjunto de documentos ou e-mails que necessitam da gestão de dados especiais.

## <a name="how-does-automatic-classification-work"></a>Como funciona a classificação automática?

No portal do Azure, pode utilizar padrões predefinidos, como "Números de cartão de crédito" ou "Número de Segurança Social dos E.U.A.". Em alternativa, pode definir uma cadeia personalizada ou um padrão como condição para classificação automática.

Irá ver um exemplo desta situação no [Tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md). 

A precisão da classificação depende da forma como configurar a regra de classificação, que se baseia em condições. Atualmente, as condições suportam padrões de texto e expressões regulares. Para obter uma explicação sobre cada uma das opções disponíveis durante a pré-visualização, com algumas sugestões de exemplos para testar, consulte [Como configurar condições para classificação automática e recomendada para o Azure Information Protection](../deploy-use/configure-policy-classification.md). A deteção é executada quando o documento é guardado ou um e-mail é enviado.

Para a melhor experiência de utilizador e para assegurar a continuidade do negócio, recomendamos que comece por ações de recomendação do utilizador em vez de ações totalmente automáticas. Isto permite aos utilizadores aceitar a ação de etiquetagem ou proteção ou substituir estas sugestões.   

## <a name="can-azure-information-protection-prompt-users-to-classify-files-themselves-rather-than-use-automatic-classification"></a>O Azure Information Protection pode pedir aos utilizadores para classificar ficheiros em vez de utilizar a classificação automática? 

Sim. Utilize o portal do Azure para configurar se pretende utilizar a classificação automática ou fazer uma recomendação aos utilizadores, definindo a opção **Selecione a forma como esta etiqueta é aplicada: automaticamente ou recomendada para o utilizador** como **Recomendada**.

Irá ver um exemplo desta situação no [Tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md).  

## <a name="can-i-force-all-documents-to-be-classified"></a>Posso impor a classificação de todos os documentos?

Sim. Se necessitar que os utilizadores classifiquem todos os ficheiros que guardam, no portal do Azure, defina a opção **Todos os documentos e e-mails têm de ter uma etiqueta** como **Ligado**. 

## <a name="can-i-remove-classification-from-a-file"></a>Posso remover a classificação de um ficheiro?

Sim. Para remover a classificação de um ficheiro, abra-o na aplicação do Office, clique no ícone **Editar etiqueta** na barra do Information Protection, clique no ícone **Remover etiqueta** e, em seguida, clique em **OK** para confirmar a ação. 


## <a name="can-i-prompt-users-to-justify-why-they-are-changing-the-classification-level"></a>Posso solicitar aos utilizadores que indiquem a razão pela qual pretendem alterar o nível de classificação?

Sim. Para se certificar de que os utilizadores justificam as suas alterações de classificação, no portal do Azure, defina a opção **Os utilizadores têm de fornecer uma justificação para reduzir a etiqueta de classificação, remover uma etiqueta ou remover a proteção** como **Ativado**. Ao fazerem-no, a ação e a justificação são registadas no registo de eventos do Windows local: **Aplicações e Registos de Serviços** > **Proteção do Microsoft Azure Information Protection**.

## <a name="how-can-i-automatically-protect-the-content-after-its-been-classified"></a>Como posso proteger automaticamente o conteúdo depois de ter sido classificado?

No portal do Azure, pode selecionar um modelo de Rights Management para proteger automaticamente os conteúdos, de acordo com o nível de classificação que especificar.

Irá ver um exemplo desta situação no [Tutorial de início rápido do Azure Information Protection](infoprotect-quick-start-tutorial.md). Para mais informações, consulte [Como configurar uma etiqueta para aplicar proteção a Gestão de Direitos](../deploy-use/configure-policy-protection.md).

## <a name="can-a-file-be-classified-with-two-different-classifications"></a>Um ficheiro pode ser classificado com duas classificações diferentes?

Se necessário, pode criar subetiquetas que melhor descrevam subcategorias para uma etiqueta de sensibilidade específica. Por exemplo, a etiqueta principal **Segredo** pode conter subetiquetas como **Segredo \ Legal** e **Segredo \ Finanças**. Em seguida, pode aplicar marcações visuais de classificação diferentes e modelos de Gestão de Direitos diferentes a subetiquetas diferentes.

Embora possa definir marcações visuais, proteção e condições em ambos os níveis, quando utiliza subníveis, configure estas definições apenas no subnível. Se configurar as mesmas definições na etiqueta principal e no respetivo subnível, as definições do subnível têm precedência.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Quando um e-mail tem uma etiqueta, os anexos também recebem a mesma etiqueta automaticamente?

Não. Quando coloca uma etiqueta numa mensagem de e-mail com anexos, esses anexos não herdam a mesma etiqueta. Os anexos permanecem sem uma etiqueta ou retêm uma etiqueta aplicada separadamente. No entanto, se a etiqueta do e-mail aplicar proteção, essa proteção é aplicada aos anexos.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Qual a diferença entre a classificação do Azure Information Protection para e-mails e a classificação de mensagens do Exchange?

A classificação de mensagens do Exchange é uma funcionalidade mais antiga que pode classificar e-mails e é implementada independentemente da classificação do Azure Information Protection. Porém, pode integrar as duas soluções para que, quando os utilizadores classificarem um e-mail com a aplicação Web do Outlook e em algumas aplicações de e-mail móveis, a classificação do Azure Information Protection e as marcas de etiqueta correspondentes sejam adicionadas automaticamente. O Exchange adiciona a classificação e a versão de pré-visualização do cliente do Azure Information Protection aplica as definições de etiquetas correspondentes para essa classificação.

Apesar de a aplicação Web do Outlook ainda não suportar nativamente a classificação e proteção do Azure Information Protection, pode utilizar esta mesma técnica para utilizar as suas etiquetas com este cliente de e-mail além do cliente Outlook de ambiente de trabalho.

Para obter esta solução: 

1. Utilize o cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) do Exchange PowerShell para criar classificações de mensagens com a propriedade Nome que mapeia os seus nomes de etiquetas na sua política do Azure Information Protection. 

2. Crie uma regra de transporte do Exchange para cada etiqueta: aplique a regra quando as propriedades da mensagem incluírem a classificação que configurou e modifique as propriedades das mensagens para definir um cabeçalho da mensagem. 

    Para o cabeçalho da mensagem, encontrará as informações a especificar ao inspecionar as propriedades de um ficheiro do Office que classificou com a etiqueta do Azure Information Protection. Identifique a propriedade do ficheiro com o formato **MSIP_Label_<GUID>_Enabled** e especifique esta cadeia para o cabeçalho da mensagem e, em seguida, especifique como **Verdadeiro** o valor do cabeçalho. Por exemplo, o cabeçalho da sua mensagem poderá ser semelhante a esta cadeia: **MSIP_Label_132616b8-f72d-5d1e-aec1-dfd89eb8c5b2_Enabled**


Posteriormente, acontecerá o seguinte quando os utilizadores utilizarem a aplicação de acesso Web do Outlook ou um cliente de dispositivo móvel que suporta a proteção da gestão de direitos: 

- Os utilizadores selecionam a classificação de mensagens do Exchange e enviam o e-mail.

- A regra do Exchange deteta a classificação do Exchange e modifica o cabeçalho da mensagem em conformidade para adicionar a classificação do Azure Information Protection.

- Quando os destinatários a executar a versão de pré-visualização do cliente do Azure Information Protection veem o e-mail no Outlook, verão a etiqueta do Azure Information Protection atribuída e quaisquer cabeçalhos, rodapés ou marcas d'água de e-mail correspondentes. 

Se as suas etiquetas do Azure Information Protection aplicarem a proteção da gestão de direitos, adicione esta opção à configuração da regra ao selecionar a opção para modificar a segurança da mensagem, aplique a proteção de direitos e, em seguida, selecione a opção Não Reencaminhar ou modelo do RMS.


## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Como podem as soluções DLP e outras aplicações ser integradas com o Azure Information Protection?

Uma vez que o Azure Information Protection utiliza metadados persistentes para classificação, que incluem uma etiqueta de texto não encriptado, estas informações podem ser lidas por soluções DLP e outras aplicações. Nos ficheiros, estes metadados são armazenados em propriedades personalizadas; nos e-mails, estas informações estão indicadas nos cabeçalhos de e-mail.

## <a name="how-does-document-tracking-and-revocation-work-for-azure-information-protection"></a>Como funciona o controlo de documentos e a revogação em relação ao Azure Information Protection?

O controlo de documentos relativo a ficheiros que classifica e protege com o Azure Information Protection funciona com a proteção do Azure Rights Management e a aplicação de partilha RMS. Também pode aceder ao site de controlo de documentos utilizando o cliente do Azure Information Protection (versão 1.0.233 ou posterior): 

- Numa aplicação do Office, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em  > **Controlar utilização**. 

Para obter mais informações, veja [Controlar e revogar os documentos quando utiliza a aplicação de partilha RMS](../rms-client/sharing-app-track-revoke.md).

## <a name="can-i-control-which-users-can-use-azure-information-protection-to-classify-and-protect-content"></a>Posso controlar que utilizadores podem utilizar o Azure Information Protection para classificar e proteger conteúdo?

Pode restringir os utilizadores que classificam e protegem os dados ao controlar a distribuição do cliente do Azure Information Protection. Adicione novas etiquetas apenas para utilizadores especificados quando configura uma [política de âmbito](../deploy-use\configure-policy-scope.md). 

Os ficheiros e e-mails classificados pelo Azure Information Protection podem ser consumidos ou editados por qualquer utilizador, com ou sem o cliente do Azure Information Protection instalado. 

## <a name="how-do-i-sign-in-as-a-different-user"></a>Como posso iniciar sessão como um utilizador diferente?

Num ambiente de produção, normalmente não precisa de iniciar sessão como um utilizador diferente quando está a utilizar o cliente do Azure Information Protection. No entanto, poderá ter de o fazer se tiver vários inquilinos. Por exemplo, tem um inquilino de teste além do inquilino do Office 365 ou do Azure que a sua organização utiliza.

Pode verificar com que conta tem sessão iniciada atualmente através da caixa de diálogo do **Microsoft Azure Information Protection**: abra uma aplicação do Office e, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e comentários**. O nome da sua conta é apresentado na secção **Estado do cliente**.

Especialmente quando estiver a utilizar uma conta de administrador, verifique o nome de domínio da conta com sessão iniciada que é apresentada. Por exemplo, se tiver uma conta de administrador em dois inquilinos diferentes, pode não perceber que tem sessão iniciada com o nome da conta certo, mas com o domínio errado. Um sinal de tal engano pode ser a impossibilidade de transferir a política do Azure Information Protection ou não ver as etiquetas ou o comportamento esperados.

Para iniciar sessão como um utilizador diferente, tem de editar o registo:

1. Com um editor de registo, navegue para **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP** e elimine a chave **TokenCache**.

2. Reinicie as aplicações do Office abertas e inicie sessão com a sua conta de utilizador diferente. Se não vir um pedido na aplicação do Office para iniciar sessão no serviço Azure Information Protection, volte à caixa de diálogo do **Microsoft Azure Information Protection** e clique em **Iniciar sessão** na secção **Estado do cliente** atualizada.

Além disso,

- Se pretender reinicializar o ambiente do serviço Azure Rights Management (também conhecido como arranque do sistema), pode fazê-lo através da opção **Repor** da [ferramenta RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Se pretender eliminar a política do Azure Information Protection atualmente transferida, pode fazê-lo ao eliminar o ficheiro **Policy.msip** da pasta %localappdata%\Microsoft\MSIP.

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Como posso comunicar um problema ou enviar feedback do Azure Information Protection?

Se tiver um problema com o Azure Information Protection e estiver a utilizar a versão atual do cliente: na aplicação do Office, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e feedback**. Na caixa de diálogo **Microsoft Azure Information Protection**, clique em **Enviar comentários**. Esta ação envia um e-mail à equipa do Information Protection e anexa automaticamente os ficheiros de registo do seu PC para ajudar a diagnosticar o problema. 

Se tiver questões ou comentários, utilize o [site Yammer do Azure Information Protection](https://www.yammer.com/askipteam/). 


<!--HONumber=Dec16_HO1-->


