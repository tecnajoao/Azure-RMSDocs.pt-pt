---
title: "O que é o Azure Information Protection?"
description: "Uma descrição geral sobre o serviço Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
ms.openlocfilehash: ba39c332437e2710554d1e8f69c3f676f0d870db
ms.sourcegitcommit: faaab68064f365c977dfd1890f7c8b05a144a95c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2017
---
# <a name="what-is-azure-information-protection"></a>O que é o Azure Information Protection?

>*Aplica-se a: Azure Information Protection*

O Azure Information Protection é uma solução na cloud que ajuda uma organização a classificar, etiquetar e proteger os respetivos documentos e e-mails. Tal pode ser feito automaticamente por administradores que definem regras e condições, manualmente pelos utilizadores ou numa combinação em que os utilizadores recebem recomendações. 

A imagem seguinte mostra um exemplo do Azure Information Protection em ação. O administrador configurou regras para detetar dados confidenciais (neste caso, informações de cartão de crédito). Quando um utilizador guarda um documento do Word que contém informações de cartão de crédito, vê uma descrição personalizada que lhe recomenda que aplique uma etiqueta específica que o administrador configurou. Esta etiqueta classifica e, opcionalmente (consoante a configuração), protege o documento. 

![Exemplo de classificação recomendada para o Azure Information Protection](../media/info-protect-recommend-calloutsv2.png)

Após os seus conteúdos serem classificados (e, opcionalmente, protegidos), pode acompanhar e controlar a forma como são utilizados. Pode analisar fluxos de dados para obter estatísticas sobre a sua empresa, detetar comportamentos de risco e tomar medidas corretivas, controlar o acesso a documentos, evitar a fuga ou utilização indevida de dados e assim sucessivamente.

## <a name="how-labels-apply-classification"></a>Como as etiquetas aplicam a classificação

Pode utilizar etiquetas do Azure Information Protection para aplicar a classificação a documentos e e-mails. Quando o fizer, a classificação será sempre identificável, independentemente do local onde os dados são armazenados ou com quem são partilhados. As etiquetas incluem marcas visuais como cabeçalhos, rodapés ou marcas d'água. Os metadados são adicionados aos ficheiros e cabeçalhos de e-mail em texto não encriptado. O texto não encriptado garante que outros serviços (tais como soluções de prevenção de perda de dados) conseguem identificar a classificação e tomar as medidas adequadas. 

Por exemplo, a seguinte mensagem de e-mail foi classificada como "Geral". Esta etiqueta será adicionada como um rodapé à mensagem de e-mail. Este rodapé é um indicador visual para todos os destinatários a informar que o e-mail contém dados empresariais gerais que não deverão ser enviados para fora da organização. A etiqueta também é incorporada nos cabeçalhos de e-mail para que os serviços de e-mail consigam inspecionar este valor e criar uma entrada de auditoria ou impedir o e-mail de ser enviado para fora da organização.

![Exemplo de rodapé de e-mail e cabeçalhos que mostram a classificação do Azure Information Protection](../media/example-email-footerv2.png)


## <a name="how-data-is-protected"></a>Como os dados são protegidos

A tecnologia de proteção utiliza o *Azure Rights Management* (frequentemente abreviado para Azure RMS). Esta tecnologia está integrada com outros serviços e aplicações na cloud da Microsoft, como o Office 365 e o Azure Active Directory. Também pode ser utilizado com as suas próprias aplicações de linha de negócio e soluções de proteção de informações de fornecedores de software, sejam estas aplicações e soluções locais ou na cloud.

Esta tecnologia de proteção utiliza políticas de autorização, encriptação e identidade. De forma semelhante às etiquetas que são aplicadas, a proteção aplicada através do Rights Management mantém-se associada aos documentos e e-mails independentemente da sua localização, quer estejam dentro ou fora da sua organização, redes, servidores de ficheiros e aplicações. Esta solução de proteção de informações mantém o utilizador no controlo dos seus dados, mesmo quando são partilhados com outras pessoas.

Por exemplo, pode configurar um documento de relatório ou uma folha de cálculo de previsão de vendas para que só possa ser acedido por pessoas na sua organização e controlar se esse documento pode ser editado, restringi-lo para acesso só de leitura ou impedi-lo de ser impresso. Pode configurar os e-mails da mesma forma e, além disso, impedir que sejam encaminhados ou impedir a utilização da opção Responder a Todos. Estas tarefas de proteção podem ser simplificadas e dinamizadas ao utilizar *modelos de Rights Management*.

### <a name="rights-management-templates"></a>Modelos de gestão de direitos

Assim que a ativar o serviço Azure Rights Management, dois modelos predefinidos estão disponíveis para que restringe o acesso a dados para os utilizadores dentro da sua organização. Pode utilizar estes modelos para ajudar imediatamente a impedir a fuga de dados da sua organização. Também pode complementar estes modelos predefinidos ao configurar as suas próprias definições de proteção que se aplicam controlos mais restritivos.

Modelos podem ser parte da configuração de uma etiqueta. Quando esse etiqueta é aplicada a uma documento ou mensagem de e-mail, os dados são classificados e automaticamente protegidos. Os modelos também podem ser selecionados por utilizadores ou administradores em produtos e serviços que suportam a tecnologia Azure Rights Management.

Este exemplo mostra como pode selecionar um modelo para uma etiqueta ao configurar a política do Azure Information Protection a partir do portal do Azure:

![Exemplo de seleção de modelos no portal do Azure](../media/info-protect-template-callout.png)

Estes modelos podem ser selecionados a partir do centro de administração do Exchange. Por exemplo, pode configurar as regras de fluxo de correio do Exchange Online para utilizar estes modelos, uma vez que o Exchange suporta a tecnologia Azure Rights Management:

![Exemplo de seleção de modelos para o Exchange Online](../media/templates-exchangeonline-callouts.png)

Para obter mais informações sobre a proteção do Azure Rights Management, veja [O que é o Azure Rights Management?](what-is-azure-rms.md)

## <a name="integration-with-end-user-workflows"></a>Integração com fluxos de trabalho de utilizador final

O Azure Information Protection integra-se com os fluxos de trabalho existentes de utilizadores finais quando o cliente do Azure Information Protection é instalado. Este cliente instala a barra do Information Protection em aplicações do Office, conforme vimos na primeira imagem que mostrava esta barra no Word. Esta barra do Information Protection é adicionada ao Excel, PowerPoint e Outlook. Por exemplo:

![Exemplo de barra do Azure Information Protection no Excel](../media/excel2016-infoprotect-barv2.png)

Esta barra do Information Protection torna mais fácil para os utilizadores finais selecionar etiquetas para a classificação correta. Se necessário, as etiquetas também podem ser aplicadas automaticamente de modo a reduzir o trabalho que os utilizadores teriam com essa tarefa ou para estarem em conformidade com as políticas da sua empresa.

Para classificar e proteger tipos de ficheiro adicionais e para suportar vários ficheiros ao mesmo tempo, os utilizadores podem clicar com o botão direito do rato nos ficheiros ou numa pasta do Explorador de Ficheiros do Windows:

![No Explorador de Ficheiros, clique com o botão direito do rato em Classificar e proteger ao utilizar o Azure Information Protection](../media/right-click-classify-protect-folder.png)

Quando os utilizadores selecionam a opção de menu **Classificar e proteger** no Explorador de Ficheiros, podem selecionar uma etiqueta tal como quando utilizam a barra do Information Protection nas suas aplicações de ambiente de trabalho do Office. Também podem definir as suas próprias permissões personalizadas, se necessário.

Os utilizadores avançados (e os administradores) podem considerar a utilização dos comandos do PowerShell mais eficiente para gerir e definir a classificação e a proteção de vários ficheiros. Os comandos do PowerShell para realizar este procedimento são incluídos automaticamente com o cliente, embora também possa instalar o módulo do PowerShell separadamente.

Depois de proteger um documento, os utilizadores e os administradores podem utilizar um site de controlo de documentos para saber quem acede aos documentos e quando. Se suspeitarem que há uma utilização indevida, podem também revogar o acesso aos documentos:

![Ícone Revogar acesso no site de controlo de documentos](../media/tracking-site-revoke-access-icon.png)


## <a name="resources-for-azure-information-protection"></a>Recursos para o Azure Information Protection

- Versão de avaliação gratuita: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- Transferir o cliente: [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- FAQ: [Perguntas mais frequentes sobre o Azure Information Protection](../get-started/faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)

- Vídeo: "Top 5 Tips for Information Protection (As Cinco Sugestões Principais para Proteger Informações)"

    <iframe width="560" height="315" src="https://www.youtube.com/embed/GWcnZFMPcnE" frameborder="0" allowfullscreen></iframe>

Além disso, **Microsoft Ignite 2017** tem demasiadas sessões para o Azure Information Protection, que será disponibilizada a pedido. Pode [pesquisar e localizar](https://myignite.microsoft.com/videos?q=%2522azure%2520information%2520protection%2522) estas sessões no Web site do Ignite à medida que ficam disponíveis. Para obter um resumo dos anúncios, consulte [Novidades do Azure Information Protection @ Ignite 2017](https://blogs.technet.microsoft.com/enterprisemobility/2017/09/27/whats-new-in-azure-information-protection-ignite-2017/).


## <a name="next-steps"></a>Próximos passos

Leia a publicação do blogue [Azure Information Protection: Ready, set, protect! (Azure Information Protection: deixar tudo a postos para proteger informações)](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/21/azure-information-protection-ready-set-protect/)

Configure e veja o Azure Information Protection, com o nosso [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md) em 5 passos.

Será que conhece o Azure Information Protection ou o Azure Rights Management por outro nome? Veja a [nossa lista de termos alternativos para o serviço](azure-rms-aka.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]