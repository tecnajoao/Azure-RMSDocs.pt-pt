---
title: "O que é o Azure Information Protection? | Azure Information Protection"
description: "Uma descrição geral sobre o serviço Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
translationtype: Human Translation
ms.sourcegitcommit: c8ffebad1130c8ba084c0feb83aa3ec54692ad54
ms.openlocfilehash: c0ea97dc29855ad46271dac251c804ca602cee69


---

# <a name="what-is-azure-information-protection"></a>O que é o Azure Information Protection?

>*Aplica-se a: Azure Information Protection*

O Azure Information Protection é uma solução na nuvem que ajuda uma organização a classificar, etiquetar e proteger os respetivos documentos e e-mails. Tal pode ser feito automaticamente por administradores que definem regras e condições, manualmente pelos utilizadores ou numa combinação em que os utilizadores recebem recomendações. 

A imagem seguinte mostra um exemplo do Azure Information Protection em ação. O administrador configurou regras para detetar dados confidenciais (neste caso, informações de cartão de crédito). Quando um utilizador guarda um documento do Word que contém informações de cartão de crédito, vê uma descrição personalizada que lhe recomenda que aplique uma etiqueta específica que o administrador configurou, que classifica e, opcionalmente, protege o documento. 

![Exemplo de classificação recomendada para o Azure Information Protection](../media/info-protect-recommend-callouts.png)

Após os seus conteúdos serem classificados (e, opcionalmente, protegidos), pode acompanhar e controlar a forma como são utilizados. Pode analisar fluxos de dados para obter estatísticas sobre a sua empresa, detetar comportamentos de risco e tomar medidas corretivas, controlar o acesso a documentos, evitar a fuga ou utilização indevida de dados e assim sucessivamente.

## <a name="how-labels-apply-classification"></a>Como as etiquetas aplicam a classificação

Pode utilizar etiquetas do Azure Information Protection para aplicar a classificação a documentos e e-mails. Quando o fizer, a classificação será sempre identificável, independentemente do local onde os dados são armazenados ou com quem são partilhados. As etiquetas persistentes incluem marcas visuais, tais como um cabeçalho, rodapé ou uma marca d'água. São adicionados metadados a ficheiros e cabeçalhos de e-mail em texto simples para que outros serviços (tais como soluções de prevenção de perda de dados) possam identificar a classificação e tomar as medidas adequadas. 

Por exemplo, a seguinte mensagem de e-mail foi classificada como "Interna". Esta etiqueta é adicionada em rodapé à mensagem de e-mail e serve como indicador visual para informar todos os destinatários de que a mesma se destina a utilização interna e não deve ser enviada para fora da organização. Esta etiqueta também é incorporada nos cabeçalhos de e-mail para que os serviços de e-mail possam inspecionar este valor e criar uma entrada de auditoria ou impedir o e-mail de ser enviado para fora da organização.

![Exemplo de rodapé de e-mail e cabeçalhos que mostram a classificação do Azure Information Protection](../media/example-email-footer-header.png)


## <a name="how-data-is-protected"></a>Como os dados são protegidos

A tecnologia de proteção utiliza o *Azure Rights Management* (frequentemente abreviado para Azure RMS). Esta tecnologia está integrada com outros serviços e aplicações na nuvem da Microsoft, como o Office 365 e o Azure Active Directory. Também pode ser utilizado com as suas próprias aplicações de linha de negócio e soluções de proteção de informações de fornecedores de software, sejam estas aplicações e soluções locais ou na nuvem.

Esta tecnologia de proteção utiliza políticas de autorização, encriptação e identidade. Tal como nas etiquetas persistentes, a proteção que é aplicada ao utilizar o Rights Management mantém-se com os documentos e e-mails, independentemente da localização: dentro ou fora da sua organização, redes, servidores de ficheiros e aplicações. Esta solução de proteção de informações mantém o utilizador no controlo dos seus dados, mesmo quando são partilhados com outras pessoas.

Por exemplo, pode configurar um documento de relatório ou uma folha de cálculo de previsão de vendas para que só possa ser acedido por pessoas na sua organização e controlar se esse documento pode ser editado, restringi-lo para acesso só de leitura ou impedi-lo de ser impresso. Pode configurar os e-mails da mesma forma e, além disso, impedir que sejam encaminhados ou impedir a utilização da opção Responder a Todos. Estas tarefas de proteção podem ser simplificadas e dinamizadas ao utilizar *modelos de gestão de direitos*.

### <a name="rights-management-templates"></a>Modelos de gestão de direitos

Quando ativar o serviço Azure Rights Management, serão criados dois modelos predefinidos que restringem o acesso aos dados a utilizadores na sua organização. Pode utilizar estes modelos para ajudar imediatamente a impedir a fuga de dados da sua organização. Também pode complementar estes modelos predefinidos ao configurar os seus próprios modelos personalizados que apliquem controlos mais restritivos.

Estes modelos podem fazer parte da configuração de uma etiqueta, para que, quando uma etiqueta específica for aplicada a um documento (ou mensagem de e-mail), os dados sejam classificados e protegidos automaticamente. Os modelos também podem ser selecionados por utilizadores ou administradores em produtos e serviços que suportam a tecnologia Azure Rights Management.

Este exemplo mostra como pode selecionar um modelo para uma etiqueta ao configurar a política do Azure Information Protection a partir do portal do Azure:

![Exemplo de seleção de modelos no portal do Azure](../media/templates-infoprotection-callouts.png)

Os mesmos modelos podem ser selecionados no centro de administração do Exchange para configurar as regras de fluxo de correio do Exchange Online, que suportam a tecnologia do Azure Rights Management:

![Exemplo de seleção de modelos para o Exchange Online](../media/templates-exchangeonline-callouts.png)

Para obter mais informações sobre a proteção do Azure Rights Management, consulte [O que é o Azure Rights Management?](what-is-azure-rms.md)

## <a name="integration-with-end-user-workflows"></a>Integração com fluxos de trabalho de utilizador final

O Azure Information Protection integra-se com os fluxos de trabalho existentes de utilizadores finais quando o cliente do Azure Information Protection é instalado. Este cliente instala a barra do Information Protection para aplicações do Office, conforme vimos na primeira imagem. A mesma barra é adicionada ao Excel, PowerPoint e Outlook. Por exemplo:

![Exemplo de barra do Azure Information Protection no Excel](../media/excel2013-infoprotect-bar2.png)

Esta barra do Information Protection facilita aos utilizadores finais a seleção de etiquetas para uma classificação correta. Se for necessário, estas etiquetas também podem proteger automaticamente documentos e e-mails.

Quando os utilizadores partilharem os respetivos documentos protegidos por e-mail, podem utilizar um site de controlo de documentos para saber quem acede aos documentos e quando. Se suspeitarem que há uma utilização indevida, podem também revogar o acesso aos documentos.


## <a name="resources-for-azure-information-protection"></a>Recursos para o Azure Information Protection

- Anúncio: [o Azure Information Protection está agora Disponível Globalmente](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/04/azure-information-protection-is-now-generally-available/)

- Versão de avaliação gratuita: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- Transferir o cliente: [cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- FAQ: [Perguntas mais frequentes sobre o Azure Information Protection](../get-started/faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)

- Descrição geral em vídeo

    <iframe width="560" height="315" src="https://www.youtube.com/embed/N9Ip0m6d3G0" frameborder="0" allowfullscreen></iframe>

    Além disso, o Microsoft Ignite 2016 oferece muitas sessões a pedido para Azure Information Protection:

    - [BRK2127: adotar uma solução condicionada por identidade abrangente para proteger e partilhar dados de forma segura](https://myignite.microsoft.com/videos?q=BRK2127)
    
    - [THR2107: colaborar com segurança ao utilizar o Azure Information Protection](https://myignite.microsoft.com/videos?q=THR2107)
    
    - [THR2108: garantir proteção abrangente dos seus dados com o Azure Information Protection](https://myignite.microsoft.com/videos?q=THR2108)
    
    - [BRK3095: saber como a classificação, etiquetagem e proteção proporcionam uma proteção de dados persistente](https://myignite.microsoft.com/videos?q=BRK3095)
    
    - [BRK2128: enviar e-mails seguros a qualquer pessoa com a tecnologia do Microsoft Office 365 e do Azure Information Protection](https://myignite.microsoft.com/videos?q=BRK2128)


## <a name="next-steps"></a>Passos seguintes

Configure e veja o Azure Information Protection, com o nosso [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md) em 5 passos.

Conhece o Azure Information Protection ou Azure Rights Management por outro nome? Consulte a [nossa lista de termos alternativos para o serviço](azure-rms-aka.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


