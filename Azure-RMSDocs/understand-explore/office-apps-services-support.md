---
title: "Aplicações e serviços do Office com o Azure Information Protection"
description: "Como as aplicações do Office para o utilizador final (tais como o Word, Excel, PowerPoint e Outlook) e os serviços do Office (tais como o Exchange e SharePoint) podem utilizar o serviço Azure Rights Management para ajudar a proteger os dados da sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d812476d882525b1fd5686418151188e57afa80d
ms.sourcegitcommit: 724b0b5d7a3ab694643988148ca68c0eac769f1e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/21/2017
---
# <a name="office-applications-and-services"></a>Aplicações e serviços do Office

>*Aplica-se a: Azure Information Protection, Office 365*

As aplicações do Office para o utilizador final (tais como o Word, Excel, PowerPoint e Outlook) e os serviços do Office (tais como o Exchange e SharePoint) podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger os dados da sua organização.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Aplicações do Office: Word, Excel, PowerPoint, Outlook
Estas aplicações suportam nativamente Gestão de Direitos com a gestão de direitos de informação (IRM) e permitem que os utilizadores protejam um documento guardado ou a uma mensagem de e-mail a enviar. Os utilizadores podem aplicar modelos ou escolher definições personalizadas para as restrições de acesso, os direitos e as restrições de utilização no Word, Excel e PowerPoint. 

Por exemplo, os utilizadores podem configurar um documento do Word para que possa ser acedido apenas por pessoas na sua organização ou controlar se uma folha de cálculo do Excel pode ser editada, restringida para acesso só d leitura ou impedida de ser impressa. Para ficheiros sensíveis ao tempo, é possível configurar um prazo de expiração (diretamente pelos utilizadores ou ao aplicar um modelo) para indicar quando deixa de ser possível aceder ao ficheiro. Para o Outlook, os utilizadores também podem escolher a opção **Não Reencaminhar** para ajudar a evitar a fuga de dados, além de escolherem um modelo.

Para além do suporte IRM nativo, estas aplicações suportam a barra do Azure Information Protection que é instalada com o [cliente do Azure Information Protection](../rms-client/aip-client.md). Esta barra apresenta etiquetas para fazer com que seja mais fácil para os utilizadores aplicarem automaticamente a proteção do Rights Management a documentos e e-mails que contêm dados confidenciais.

Se estiver pronto para configurar as aplicações do Office e o cliente do Azure Information Protection:

- Para configurar as aplicações do Office, veja [Aplicações do Office: configuração para clientes](../deploy-use/configure-office-apps.md).

- Para instalar e configurar o cliente do Azure Information Protection, veja [Cliente do Azure Information Protection: instalação e configuração para clientes](../deploy-use/configure-client.md).

## <a name="exchange-online-and-exchange-server"></a>Exchange Online e Exchange Server
Quando utiliza o Exchange Online ou o Exchange Server, pode utilizar a integração de gestão de direitos de informação (IRM), que fornece soluções de proteção de informações adicionais:

-   **IRM do Exchange ActiveSync** para que os dispositivos móveis possam proteger e consumir mensagens de e-mail protegidas.

-   Suporte de RMS para o **Outlook Web App**, implementado da mesma forma para o cliente do Outlook para que os utilizadores possam proteger mensagens de e-mail por modelos ou ao especificar opções individuais e os utilizadores possam ler e utilizar mensagens de e-mail protegidas que lhes são enviadas.

-   **Regras de proteção** para clientes do Outlook que um administrador configura para aplicar automaticamente modelos de Gestão de Direitos a mensagens de e-mail para destinatários especificados. Por exemplo, quando os e-mails internos são enviados para o seu departamento jurídico, estes só podem ser lidos por membros do departamento jurídico e não podem ser reencaminhados. Os utilizadores veem a proteção aplicada à mensagem de e-mail antes de a enviar e, por predefinição, podem removê-la se decidirem que não é necessária. Os e-mails são encriptados antes de serem enviados. Para obter mais informações, consulte [Regras de Proteção do Outlook](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) e [Criar uma Regra de Proteção do Outlook](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) na biblioteca do Exchange.

-   **Regras de transporte** que um administrador configura para aplicar automaticamente modelos de Gestão de Direitos a mensagens de e-mail com base nas propriedades, tais como remetente, destinatário, assunto da mensagem e conteúdos. São semelhantes no conceito às regras de proteção, mas não permitem que os utilizadores removam a proteção, podem ser aplicadas ao Outlook Web Access e a mensagens de e-mail enviadas por dispositivos móveis e não encriptam as mensagens de e-mail antes de serem enviadas pelo cliente. Para obter mais informações, consulte [Criar uma Regra de Proteção de Transporte](https://technet.microsoft.com/library/dd302432.aspx) na biblioteca do Exchange.

-   **Políticas de prevenção de perda de dados (DLP)** que contêm conjuntos de condições para filtrar mensagens de e-mail e executar ações para ajudar a evitar a perda de dados para conteúdos sensíveis ou confidenciais (por exemplo, informações pessoais ou informações de cartão de crédito). As Sugestões de Política podem ser utilizadas quando são detetados dados confidenciais para alertar utilizadores de que poderão ter de aplicar a proteção de informações, com base nas informações na mensagem de e-mail. Para obter mais informações, veja [Data loss prevention](https://technet.microsoft.com/library/jj150527(v=exchg.160).aspx) (Prevenção de perda de dados) na biblioteca do Exchange.

-   **Encriptação de Mensagens do Office 365** que utiliza regras de transporte para enviar e-mails encriptados para pessoas fora da sua empresa e o e-mail é lido num browser com uma interface semelhante ao Outlook Web App. Pode personalizar o texto de exclusão de responsabilidade e o texto do cabeçalho nos e-mails encriptados da sua empresa e até adicionar o logótipo da empresa. Para obter mais informações, consulte [Encriptação de Mensagens do Office 365](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx) no Web site do Office.

Se utilizar o Exchange Server, pode utilizar as funcionalidades de proteção de informações com o serviço Azure Rights Management ao implementar o conector RMS, que atua como um reencaminhamento entre os servidores no local e o serviço Azure Rights Management.

Se estiver pronto para configurar o Exchange para a IRM:

- Para o Exchange Online, veja [Exchange Online: configuração da IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Para o Exchange no local, veja [Implementar o conector Azure Rights Management](../deploy-use/deploy-rms-connector.md).


## <a name="sharepoint-online-and-sharepoint-server"></a>SharePoint Online e SharePoint Server

Quando utiliza o SharePoint Online ou o SharePoint Server, pode proteger os seus documentos ao utilizar a gestão de direitos de informação (IRM). Esta configuração permite que os administradores protejam as listas ou bibliotecas para que quando um utilizador sai de um documento, o ficheiro descarregado fica protegido para que apenas pessoas autorizadas possam vê-lo e utilizá-lo de acordo com as políticas de proteção de informações que especificar. Por exemplo, o ficheiro poderá ser só de leitura, poderá desativar a cópia de texto, impedir guardar uma cópia local e evitar imprimir o ficheiro.

Por predefinição, a proteção é restrita à pessoa que transfere o documento. Mas pode alterar esta definição através de uma opção de configuração que expande a proteção a todos os utilizadores que têm acesso ao documento no SharePoint ou a um grupo que especificar.

Para as listas e bibliotecas do SharePoint, a proteção de informações é sempre configurada por um administrador, nunca por um utilizador final. Pode definir as permissões ao nível do site e essas permissões, por predefinição, são herdadas por qualquer lista ou biblioteca nesse site. Se utilizar o SharePoint Online, os utilizadores também podem configurar a respetiva biblioteca do OneDrive para Empresas de modo a utilizar a proteção IRM.

Para obter um controlo mais detalhado, pode configurar uma lista ou biblioteca no site para parar de herdar permissões da lista ou biblioteca principal. Em seguida, pode configurar permissões IRM nesse nível (lista ou biblioteca), onde estas passam a ser referidas como "permissões exclusivas". No entanto, as permissões estão sempre definidas ao nível do contentor, pelo que não pode definir permissões em ficheiros individuais. 

Primeiro, o serviço de IRM tem de estar ativado para o SharePoint. Em seguida, especifique as permissões IRM para uma biblioteca. No caso do SharePoint Online e do OneDrive para Empresas, os utilizadores também podem especificar as permissões IRM para a respetiva biblioteca do OneDrive para Empresas. O SharePoint não utiliza modelos de política de direitos, apesar de existirem definições de configuração do SharePoint que pode selecionar para corresponder a algumas definições que pode especificar nos modelos.

Se utilizar o SharePoint Server, pode utilizar esta proteção IRM ao implementar o conector Azure Rights Management. Este conector funciona como um reencaminhamento entre os seus servidores no local e o serviço cloud do Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Atualmente, existem algumas limitações ao utilizar a IRM do SharePoint:
> 
> - Não é possível utilizar os modelos predefinidos ou personalizados que gerir no portal clássico do Azure. 
> 
> - Os ficheiros que tenham uma extensão de nome de ficheiro .PPDF para ficheiros PDF protegidos não são suportados. Os ficheiros que têm uma extensão de nome de ficheiro .PDF e que foram protegidos nativamente pela Gestão de Direitos são suportados quando utiliza um leitor de PDF que suporta nativamente a Gestão de Direitos.


Quando utiliza a proteção IRM, o serviço Azure Rights Management aplica restrições de utilização e a encriptação de dados aos documentos quando são transferidos do SharePoint e não quando o documento é criado pela primeira vez no SharePoint ou carregado para a biblioteca. Para obter informações sobre como os documentos estão protegidos antes de serem transferidos, consulte [Encriptação de Dados no OneDrive para Empresas e no SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) da documentação do SharePoint.

Embora não seja nova, a seguinte publicação do blogue do Office tem informações adicionais que pode considerar úteis: [Novidades na Gestão de Direitos de Informação no SharePoint e no SharePoint Online](https://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

Se estiver pronto para configurar o SharePoint para a IRM:

- Para o SharePoint Online, veja [SharePoint Online e OneDrive para Empresas: configuração de IRM](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration).

- Para o SharePoint Server, consulte [Implementar o conector Azure Rights Management](../deploy-use/deploy-rms-connector.md).


## <a name="next-steps"></a>Próximos passos

Se tiver o Office 365, poderá interessar-lhe rever [File Protection Solutions in Office 365](https://technet.microsoft.com/library/dn919927.aspx#BKMK_O365fileprotect) (Soluções de Proteção de Ficheiros do Office 365), que indica as capacidades recomendadas para proteger ficheiros do Office 365.

Para ver como outras aplicações e serviços suportam o serviço Azure Rights Management do Azure Information Protection, consulte [Como as aplicações suportam o serviço Azure Rights Management](applications-support.md).

Se estiver pronto para começar a implementação, que inclui a configuração dessas aplicações e serviços, veja [Plano de implementação do Azure Information Protection](../plan-design/deployment-roadmap.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]