---
title: "Aplicações e serviços do Office com o Azure Information Protection"
description: "Como as aplicações do Office para o utilizador final (tais como o Word, Excel, PowerPoint e Outlook) e os serviços do Office (tais como o Exchange e SharePoint) podem utilizar o serviço Azure Rights Management para ajudar a proteger os dados da sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 3e77cebd642b2b9e983f5cbc81e43e1cc437dc5d
ms.lasthandoff: 02/24/2017


---


# <a name="office-applications-and-services"></a>Aplicações e serviços do Office

>*Aplica-se a: Azure Information Protection, Office 365*

As aplicações do Office para o utilizador final (tais como o Word, Excel, PowerPoint e Outlook) e os serviços do Office (tais como o Exchange e SharePoint) podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger os dados da sua organização.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Aplicações do Office: Word, Excel, PowerPoint, Outlook
Estas aplicações suportam nativamente Gestão de Direitos com a gestão de direitos de informação (IRM) e permitem que os utilizadores protejam um documento guardado ou a uma mensagem de e-mail a enviar. Os utilizadores podem aplicar modelos ou escolher definições muito personalizadas para as restrições de acesso, os direitos e as restrições de utilização no Word, Excel e PowerPoint. 

Por exemplo, os utilizadores podem configurar um documento do Word para que possa ser acedido apenas por pessoas na sua organização ou controlar se uma folha de cálculo do Excel pode ser editada, restringida para acesso só d leitura ou impedida de ser impressa. Para ficheiros sensíveis ao tempo, é possível configurar um prazo de expiração (diretamente pelos utilizadores ou ao aplicar um modelo) para indicar quando deixa de ser possível aceder ao ficheiro. Para o Outlook, os utilizadores também podem escolher a opção **Não Reencaminhar** para ajudar a evitar a fuga de dados, além de escolherem um modelo.

Para além do suporte IRM nativo, estas aplicações suportam a barra do Azure Information Protection que é instalada com o [cliente do Azure Information Protection](../rms-client/aip-client.md ). Esta barra apresenta etiquetas para fazer com que seja mais fácil para os utilizadores aplicarem automaticamente a proteção do Rights Management a documentos e e-mails que contêm dados confidenciais.

## <a name="exchange-online-and-exchange-server"></a>Exchange Online e Exchange Server
Quando utiliza o Exchange Online ou o Exchange Server, pode utilizar a integração de gestão de direitos de informação (IRM), que fornece soluções de proteção de informações adicionais:

-   **IRM do Exchange ActiveSync** para que os dispositivos móveis possam proteger e consumir mensagens de e-mail protegidas.

-   Suporte de RMS para o **Outlook Web App**, implementado da mesma forma para o cliente do Outlook para que os utilizadores possam proteger mensagens de e-mail por modelos ou ao especificar opções individuais e os utilizadores possam ler e utilizar mensagens de e-mail protegidas que lhes são enviadas.

-   **Regras de proteção** para clientes do Outlook que um administrador configura para aplicar automaticamente modelos de Gestão de Direitos a mensagens de e-mail para destinatários especificados. Por exemplo, quando os e-mails internos são enviados para o seu departamento jurídico, estes só podem ser lidos por membros do departamento jurídico e não podem ser reencaminhados. Os utilizadores veem a proteção aplicada à mensagem de e-mail antes de a enviar e, por predefinição, podem removê-la se decidirem que não é necessária. Os e-mails são encriptados antes de serem enviados. Para obter mais informações, consulte [Regras de Proteção do Outlook](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) e [Criar uma Regra de Proteção do Outlook](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) na biblioteca do Exchange.

-   **Regras de transporte** que um administrador configura para aplicar automaticamente modelos de Gestão de Direitos a mensagens de e-mail com base nas propriedades, tais como remetente, destinatário, assunto da mensagem e conteúdos. São semelhantes no conceito às regras de proteção, mas não permitem que os utilizadores removam a proteção, podem ser aplicadas ao Outlook Web Access e a mensagens de e-mail enviadas por dispositivos móveis e não encriptam as mensagens de e-mail antes de serem enviadas pelo cliente. Para obter mais informações, consulte [Criar uma Regra de Proteção de Transporte](https://technet.microsoft.com/library/dd302432.aspx) na biblioteca do Exchange.

-   **Políticas de prevenção de perda de dados (DLP)** que contêm conjuntos de condições para filtrar mensagens de e-mail e executar ações para ajudar a evitar a perda de dados para conteúdos sensíveis ou confidenciais (por exemplo, informações pessoais ou informações de cartão de crédito). As Sugestões de Política podem ser utilizadas quando são detetados dados confidenciais para alertar utilizadores de que poderão ter de aplicar a proteção de informações, com base nas informações na mensagem de e-mail. Para obter mais informações, consulte [Prevenção de Perda de Dados](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) na biblioteca do Exchange.

-   **Encriptação de Mensagens do Office 365** que utiliza regras de transporte para enviar e-mails encriptados para pessoas fora da sua empresa e o e-mail é lido num browser com uma interface semelhante ao Outlook Web App. Pode personalizar o texto de exclusão de responsabilidade e o texto do cabeçalho nos e-mails encriptados da sua empresa e até adicionar o logótipo da empresa. Para obter mais informações, consulte [Encriptação de Mensagens do Office 365](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx) no Web site do Office.

Se utilizar o Exchange Server, pode utilizar as funcionalidades de proteção de informações com o serviço Azure Rights Management ao implementar o conector RMS, que atua como um reencaminhamento entre os servidores no local e o serviço Azure Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).

## <a name="sharepoint-online-and-sharepoint-server"></a>SharePoint Online e SharePoint Server
Quando utiliza o SharePoint Online ou o SharePoint Server, pode utilizar a integração de gestão de direitos de informação (IRM), que permite aos administradores protegerem as listas ou bibliotecas para que quando um utilizador sai de um documento, o ficheiro fique protegido para que apenas pessoal autorizado possa vê-lo e utilizá-lo de acordo com as políticas de proteção de informações que especificar. Por exemplo, o ficheiro poderá ser só de leitura, poderá desativar a cópia de texto, impedir guardar uma cópia local e evitar imprimir o ficheiro.

Para listas e bibliotecas, a proteção de informações é sempre aplicada por um administrador, nunca por um utilizador final. E é aplicado ao nível das listas ou bibliotecas para todos os documentos no contentor, em vez de em ficheiros individuais.  Se utilizar o SharePoint Online, os utilizadores também podem aplicar a IRM à respetiva biblioteca do OneDrive para empresas.

Primeiro, o serviço de IRM tem de estar ativado para o SharePoint. Em seguida, especifique a Gestão de Direitos de Informação para uma biblioteca. No caso do SharePoint Online e do OneDrive para Empresas, os utilizadores também podem especificar a Gestão de Direitos de Informação para a respetiva biblioteca do OneDrive para Empresas. O SharePoint não utiliza modelos de política de direitos, apesar de existirem configurações do SharePoint que pode selecionar que estritamente correspondem às definições que pode especificar nos modelos.

Se utilizar o SharePoint Server, pode utilizar as funcionalidades de proteção de informações com o serviço Azure Rights Management ao implementar o conector RMS, que atua como um reencaminhamento entre os servidores no local e o serviço de Gestão de Direitos na cloud. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Atualmente, existem algumas limitações ao utilizar a IRM com o SharePoint:
> 
> - Não é possível utilizar os modelos predefinidos ou personalizados que gerir no portal clássico do Azure.
> - Os ficheiros que tenham uma extensão de nome de ficheiro .PPDF para ficheiros PDF protegidos não são suportados. Os ficheiros que têm uma extensão de nome de ficheiro .PDF e que foram protegidos nativamente pela Gestão de Direitos são suportados quando utiliza um leitor de PDF que suporta nativamente a Gestão de Direitos.


O Azure Rights Management aplica restrições de utilização e a encriptação de dados aos documentos quando são transferidos do SharePoint e não quando o documento é criado pela primeira vez no SharePoint ou carregado para a biblioteca. Para obter informações sobre como os documentos estão protegidos antes de serem transferidos, consulte [Encriptação de Dados no OneDrive para Empresas e no SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) da documentação do SharePoint.

Para mais informações sobre como utilizar o serviço Azure Rights Management com o SharePoint, consulte a seguinte mensagem do blogue do Office: [What’s New with Information Rights Management in SharePoint and SharePoint Online (Novidades na Gestão de Direitos de Informação no SharePoint e no SharePoint Online – em inglês)](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## <a name="next-steps"></a>Passos seguintes

Para ver como outras aplicações e serviços suportam o serviço Azure Rights Management do Azure Information Protection, consulte [Como as aplicações suportam o serviço Azure Rights Management](applications-support.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
