---
title: "Como as aplicações do Office e serviços suportam o Azure RMS do AIP"
description: "Como as aplicações do Office de utilizador final, tais como o Word e o Outlook e o Office serviços como o Exchange e SharePoint, pode utilizar o serviço Azure Rights Management AIP para ajudar a proteger os dados da sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ede24547a01bc38e528ce02dac9abe0ade396c2d
ms.sourcegitcommit: 6636defa6eca24360f15fb9ef93c2b82dc36cf76
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="how-office-applications-and-services-support-azure-rights-management"></a>Como as aplicações do Office e serviços suportam o Azure Rights Management 

>*Aplica-se a: Azure Information Protection, Office 365*

Serviços do Office e de aplicações do Office de utilizador final podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger os dados da sua organização. Estas aplicações do Office são o Word, o Excel, o PowerPoint e o Outlook. Os serviços do Office são o Exchange e o SharePoint. As configurações do Office que suportam o serviço Azure Rights Management, muitas vezes, utilizem o termo **direitos de informação (IRM) de gestão**.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Aplicações do Office: Word, Excel, PowerPoint, Outlook
Nativamente estas aplicações suportam o Azure Rights Management e permitir que os utilizadores protejam m documento guardado ou a uma mensagem de correio eletrónico a enviar. Os utilizadores podem aplicar modelos para aplicar a proteção. Em alternativa, para Word, Excel e PowerPoint, os utilizadores possam escolher definições personalizadas para acesso, os direitos e restrições de utilização. 

Por exemplo, os utilizadores podem configurar um documento do Word para que possam ser acedido apenas por pessoas na sua organização. Em alternativa, controlar se uma folha de cálculo do Excel pode ser editada, restrito ao acesso de leitura ou impedi-lo de ser impresso. Para ficheiros sensíveis ao tempo, uma hora de expiração pode ser configurada para quando o ficheiro já não pode ser acedido. Esta configuração pode ser efetuada diretamente pelos utilizadores ou ao aplicar um modelo. Para o Outlook, os utilizadores também podem escolher a opção **Não Reencaminhar** para ajudar a evitar a fuga de dados.

Para além de suporte nativo do Office para o Azure Rights Management, estas aplicações também suportam a barra do Azure Information Protection, que é instalada com o [cliente Azure Information Protection](../rms-client/aip-client.md). Esta barra apresenta as etiquetas que torna mais fácil para os utilizadores aplicar automaticamente a proteção de documentos e e-mails que contêm dados confidenciais.

Se estiver pronto para configurar as aplicações do Office e o cliente do Azure Information Protection:

- Para configurar as aplicações do Office, veja [Aplicações do Office: configuração para clientes](../deploy-use/configure-office-apps.md).

- Para instalar e configurar o cliente do Azure Information Protection, veja [Cliente do Azure Information Protection: instalação e configuração para clientes](../deploy-use/configure-client.md).

## <a name="exchange-online-and-exchange-server"></a>Exchange Online e Exchange Server
Quando utiliza o Exchange Online ou Exchange Server, pode configurar opções de gestão (IRM) de direitos de informação que suportam o Azure Rights Management. Esta configuração permite fornecer as seguintes soluções de proteção do Exchange:

-   **IRM do Exchange ActiveSync** para que os dispositivos móveis possam proteger e consumir mensagens de e-mail protegidas.

-   Suporte de proteção para por correio eletrónico **Outlook na web**, implementado da mesma forma para o cliente do Outlook. Esta configuração permite que os utilizadores a proteger as mensagens de e-mail, utilizando os modelos ou ao especificar opções individuais. Os utilizadores podem ler e utilizar mensagens de e-mail protegidas que lhes são enviadas.

-   **Regras de proteção** para clientes do Outlook que um administrador configura para aplicar automaticamente modelos de proteção de e-mail mensagens para os destinatários especificados. Por exemplo, quando os e-mails internos são enviados para o seu departamento jurídico, estes só podem ser lidos por membros do departamento jurídico e não podem ser reencaminhados. Os utilizadores veem a proteção aplicada à mensagem de e-mail antes de a enviar e, por predefinição, podem removê-la se decidirem que não é necessária. Os e-mails são encriptados antes de serem enviados. Para obter mais informações, consulte [Regras de Proteção do Outlook](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) e [Criar uma Regra de Proteção do Outlook](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) na biblioteca do Exchange.

-   **Regras de transporte** que um administrador configura para aplicar automaticamente modelos de proteção de e-mail mensagens. Estas regras são baseadas em propriedades, tais como remetente, destinatário, assunto da mensagem e conteúdo. Estas regras são semelhantes no conceito às regras de proteção, mas não permitem que os utilizadores que remova a proteção. As regras podem ser aplicadas ao Outlook na web e e-mails que são enviados por dispositivos móveis. Além disso, estas regras não encriptam as mensagens de e-mail antes de serem enviados do cliente. Para obter mais informações, consulte [Criar uma Regra de Proteção de Transporte](https://technet.microsoft.com/library/dd302432.aspx) na biblioteca do Exchange.

-   **Políticas de prevenção (DLP) de perda de dados** que contêm conjuntos de condições para filtrar as mensagens de e-mail e tomar ações para ajudar a evitar perda de dados para conteúdos sensíveis ou confidenciais. Exemplos de conteúdos sensíveis ou confidenciais incluem informações pessoais informações ou cartão de crédito. As sugestões de política podem ser utilizadas quando são detetados dados confidenciais, para alertar utilizadores que poderão ter para aplicar a proteção. Para obter mais informações, consulte [prevenção de perda de dados] (https://technet.microsoft.com/library/jj150527(v=exchg.160\).aspx) na biblioteca do Exchange.

-   **Encriptação de mensagens do Office 365** que utiliza regras de transporte para enviar e-mails encriptados para pessoas fora da sua empresa e o e-mail é lido num browser com uma interface semelhante ao Outlook na web. Pode personalizar o texto de exclusão de responsabilidade e o texto do cabeçalho nos e-mails encriptados da sua empresa e até adicionar o logótipo da empresa. Para obter mais informações, consulte [Encriptação de Mensagens do Office 365](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx) no Web site do Office.

Se utilizar o Exchange no local, pode utilizar as funcionalidades IRM com o serviço Azure Rights Management ao implementar o conetor Azure Rights Management. Este conector funciona como um reencaminhamento entre os servidores no local e o serviço Azure Rights Management.

Se estiver pronto para configurar o Exchange para a IRM:

- Para o Exchange Online, veja [Exchange Online: configuração da IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Para o Exchange no local, veja [Implementar o conector Azure Rights Management](../deploy-use/deploy-rms-connector.md).


## <a name="sharepoint-online-and-sharepoint-server"></a>SharePoint Online e SharePoint Server

Quando utiliza o SharePoint Online ou o SharePoint Server, pode proteger documentos ao utilizar a funcionalidade de gestão (IRM) de direitos de informações do SharePoint. Esta permite funcionalidade administradores protegerem as listas ou bibliotecas para que quando um utilizador verificações Escalamento um documento, o ficheiro transferido é protegido para que apenas as pessoas autorizadas podem ver e utilizar o ficheiro de acordo com as políticas de proteção de informações que especificou. Por exemplo, o ficheiro poderá ser só de leitura, poderá desativar a cópia de texto, impedir guardar uma cópia local e evitar imprimir o ficheiro.

Documentos do Word, o PowerPoint, o Excel e o PDF suportam esta proteção IRM do SharePoint. Por predefinição, a proteção é restrita à pessoa que transfere o documento. Pode alterar esta predefinição com uma opção de configuração que expande a proteção em todos os utilizadores que têm acesso a documentos do SharePoint, ou a um grupo que especificar.

Para o SharePoint listas e bibliotecas, esta proteção é sempre configurada por um administrador, nunca um utilizador final. Pode definir as permissões ao nível do site e essas permissões, por predefinição, são herdadas por qualquer lista ou biblioteca nesse site. Se utilizar o SharePoint Online, os utilizadores também podem configurar a respetiva biblioteca do OneDrive para Empresas de modo a utilizar a proteção IRM.

Para obter um controlo mais detalhado, pode configurar uma lista ou biblioteca no site para parar de herdar permissões da lista ou biblioteca principal. Em seguida, pode configurar permissões IRM nesse nível (lista ou biblioteca), onde estas passam a ser referidas como "permissões exclusivas". No entanto, as permissões estão sempre definidas ao nível do contentor, pelo que não pode definir permissões em ficheiros individuais. 

Primeiro, o serviço de IRM tem de estar ativado para o SharePoint. Em seguida, especifique as permissões IRM para uma biblioteca. No caso do SharePoint Online e do OneDrive para Empresas, os utilizadores também podem especificar as permissões IRM para a respetiva biblioteca do OneDrive para Empresas. O SharePoint não utiliza modelos de política de direitos, apesar de existirem definições de configuração do SharePoint que pode selecionar para corresponder a algumas definições que pode especificar nos modelos.

Se utilizar o SharePoint Server, pode utilizar esta proteção IRM ao implementar o conector Azure Rights Management. Este conector funciona como um reencaminhamento entre os seus servidores no local e o serviço cloud do Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Atualmente, existem algumas limitações ao utilizar a IRM do SharePoint:
> 
> - Não pode utilizar os modelos predefinidos ou personalizados que gerir no portal do Azure. 
> 
> - Os ficheiros que tenham uma extensão de nome de ficheiro. ppdf para ficheiros PDF protegidos não são suportados. Os ficheiros que tenham a extensão de nome de ficheiro. pdf e que foram protegidos nativamente pela Rights Management são suportados quando utiliza um leitor de PDF que suporta nativamente o Rights Management.
> 
> - Não é suportada a criação de conteúdos conjunta. Porque tem de verificar e transferir um documento numa biblioteca protegida IRM, uma pessoa pode editá-lo a uma hora.

Para bibliotecas que não são IRM protegida, se proteger um ficheiro que carregar, em seguida, SharePoint ou OneDrive, o seguinte não funcionará com este ficheiro: criação conjunta, Office Online, pesquisa, pré-visualização do documento, miniatura, deteção de dados Eletrónicos e prevenção de perda de dados (DLP).

Quando utiliza a proteção IRM do SharePoint, o serviço Azure Rights Management aplica restrições de utilização e a encriptação de dados aos documentos quando são transferidos do SharePoint e não quando o documento é criado inicialmente no SharePoint ou carregado para a biblioteca. Para obter informações sobre como os documentos estão protegidos antes de serem transferidos, veja [Encriptação de Dados no OneDrive para Empresas e no SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) da documentação do SharePoint.

Embora não seja nova, a seguinte publicação do blogue do Office tem informações adicionais que pode considerar úteis: [Novidades na Gestão de Direitos de Informação no SharePoint e no SharePoint Online](https://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

Se estiver pronto para configurar o SharePoint para a IRM:

- Para o SharePoint Online, veja [SharePoint Online e OneDrive para Empresas: configuração de IRM](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration).

- Para o SharePoint Server, veja [Implementar o conector Azure Rights Management](../deploy-use/deploy-rms-connector.md).


## <a name="next-steps"></a>Próximos passos

Se tiver o Office 365, poderá interessar-lhe rever [File Protection Solutions in Office 365](https://technet.microsoft.com/library/dn919927.aspx#BKMK_O365fileprotect) (Soluções de Proteção de Ficheiros do Office 365), que indica as capacidades recomendadas para proteger ficheiros do Office 365.

Para ver como outras aplicações e serviços suportam o serviço Azure Rights Management do Azure Information Protection, consulte [Como as aplicações suportam o serviço Azure Rights Management](applications-support.md).

Se estiver pronto para começar a implementação, que inclui a configuração dessas aplicações e serviços, veja [Plano de implementação do Azure Information Protection](../plan-design/deployment-roadmap.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]