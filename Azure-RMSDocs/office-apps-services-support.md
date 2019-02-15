---
title: Como aplicações do Office e serviços suportam o Azure RMS do AIP
description: Como os aplicativos do Office de utilizador final, como o Word e o Outlook e o Office serviços como o Exchange e SharePoint, pode utilizar o serviço Azure Rights Management do AIP para ajudar a proteger dados da sua organização.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 10/13/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 71f5afc3f65713f62607717d5459080aa11bedf2
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256758"
---
# <a name="how-office-applications-and-services-support-azure-rights-management"></a>Como aplicativos do Office e serviços suportam o Azure Rights Management 

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Aplicações do Office de utilizador final e os serviços do Office podem utilizar o serviço Azure Rights Management do Azure Information Protection para ajudar a proteger dados da sua organização. Estas aplicações do Office são o Word, o Excel, o PowerPoint e o Outlook. Os serviços do Office são o Exchange e o SharePoint. As configurações do Office que suportam o serviço Azure Rights Management, muitas vezes, usam o termo **direitos de informação (IRM) de gestão**.

## <a name="office-applications-word-excel-powerpoint-outlook"></a>Aplicativos do Office: Word, Excel, PowerPoint, Outlook
Estas aplicações suportam o Azure Rights Management de forma nativa e permitir que os utilizadores protejam um documento guardado ou a uma mensagem de e-mail a enviar. Os utilizadores podem aplicar [modelos](configure-policy-templates.md) para aplicar a proteção. Em alternativa, para Word, Excel e PowerPoint, os usuários podem escolher definições personalizadas para acesso, os direitos e restrições de utilização.

Por exemplo, os utilizadores podem configurar um documento do Word para que possam ser acedido apenas por pessoas na sua organização. Em alternativa, controlar se uma planilha do Excel pode ser editada, restrito ao acesso de leitura ou impedi-lo de que está a ser impresso. Para ficheiros sensíveis ao tempo, um prazo de expiração pode ser configurado para quando já não é possível aceder ao ficheiro. Esta configuração pode ser feita diretamente pelos utilizadores ou ao aplicar um modelo de proteção. Para o Outlook, os utilizadores também podem escolher a opção **Não Reencaminhar** para ajudar a evitar a fuga de dados.

Além de suporte nativo do Office para o Azure Rights Management, estas aplicações também suportam a barra do Azure Information Protection que é instalada com o [cliente Azure Information Protection](./rms-client/aip-client.md). Esta barra apresenta etiquetas que torna mais fácil para os utilizadores aplicarem automaticamente a proteção para documentos e e-mails que contêm dados confidenciais.

Se estiver pronto para configurar as aplicações do Office e o cliente do Azure Information Protection:

- Para configurar aplicações do Office, consulte [aplicações do Office: Configuração para clientes](configure-office-apps.md).

- Para instalar e configurar o cliente do Azure Information Protection, consulte [cliente Azure Information Protection: Instalação e configuração para clientes](configure-client.md).

## <a name="exchange-online-and-exchange-server"></a>Exchange Online e Exchange Server
Quando utiliza o Exchange Online ou o Exchange Server, pode configurar opções para o Azure Information Protection. Esta configuração permite fornecer as seguintes soluções de proteção do Exchange:

-   **IRM do Exchange ActiveSync** para que os dispositivos móveis possam proteger e consumir mensagens de e-mail protegidas.

-   O suporte para proteção de e-mail **Outlook na web**, que é implementado da mesma forma para o cliente do Outlook. Esta configuração permite que os utilizadores a proteger mensagens de e-mail ao utilizar modelos de proteção ou de opções. Os utilizadores podem ler e utilizar mensagens de e-mail protegidas que lhes são enviadas.

-   **Regras de proteção** para clientes do Outlook que um administrador configura para aplicar automaticamente modelos de proteção e as opções para enviar um e-mail mensagens para destinatários especificados. Por exemplo, quando os e-mails internos são enviados para o seu departamento jurídico, estes só podem ser lidos por membros do departamento jurídico e não podem ser reencaminhados. Os utilizadores veem a proteção aplicada à mensagem de e-mail antes de a enviar e, por predefinição, podem removê-la se decidirem que não é necessária. Os e-mails são encriptados antes de serem enviados. Para obter mais informações, consulte [Regras de Proteção do Outlook](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) e [Criar uma Regra de Proteção do Outlook](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) na biblioteca do Exchange.

-   **As regras de fluxo de correio** que um administrador configura para aplicar automaticamente modelos de proteção ou opções para mensagens de e-mail. Estas regras são baseadas em propriedades, tais como remetente, destinatário, assunto da mensagem e conteúdo. Estas regras são semelhantes em conceito às regras de proteção, mas não a permitir que os utilizadores remover a proteção porque a proteção é definida pelo serviço do Exchange em vez do cliente. Porque a proteção é definida pelo serviço, não importa qual sistema de operativo ou dispositivos que os utilizadores têm. Para obter mais informações, consulte [(regras de transporte) as regras de fluxo de correio no Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) e [criar uma regra de proteção de transporte](https://technet.microsoft.com/library/dd302432.aspx) para o Exchange no local.

-   **Políticas de prevenção (DLP) de perda de dados** que contêm conjuntos de condições para filtrar mensagens de e-mail e tomar as medidas, para ajudar a evitar perda de dados para conteúdos sensíveis ou confidenciais. Uma das ações que pode especificar é aplicar encriptação Protection, ao especificar um dos modelos de proteção ou opções. Sugestões de política podem ser utilizados quando são detetados dados confidenciais, para alertar os usuários que poderão ter de aplicar a proteção. Para obter mais informações, consulte [prevenção de perda de dados](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) na documentação do Exchange Online.

-   **Encriptação de mensagens do Office 365** que suporta o envio de uma mensagem de e-mail protegidas e protegido os documentos do Office como anexos de qualquer endereço de e-mail em qualquer dispositivo. Para contas de utilizador que não utilizem o Azure AD, uma experiência web suporta fornecedores de identidade social ou um código de acesso único. Para obter mais informações, consulte [configurar novas capacidades de encriptação de mensagens do Office 365 criadas com base no Azure Information Protection](/office365/securitycompliance/set-up-new-message-encryption-capabilities) na documentação do Office 365. Para ajudar a encontrar informações adicionais que estejam relacionados com esta configuração, consulte [encriptação de mensagens do Office 365](https://docs.microsoft.com/office365/securitycompliance/ome).

Se utilizar o Exchange no local, pode utilizar as funcionalidades IRM com o serviço Azure Rights Management ao implementar o conector Azure Rights Management. Este conector funciona como um reencaminhamento entre os servidores no local e o serviço Azure Rights Management.

Para obter mais informações sobre os modelos de proteção, consulte [configurando e gerenciando modelos do Azure Information Protection](configure-policy-templates.md).

Para obter mais informações sobre o e-mail de opções que pode utilizar para proteger mensagens de correio eletrónico, consulte [opção não reencaminhar para e-mails](configure-usage-rights.md#do-not-forward-option-for-emails) e [opção de criptografar apenas para e-mails](configure-usage-rights.md#encrypt-only-option-for-emails).

Se estiver pronto para configurar o Exchange para proteger mensagens de correio eletrónico:

- Para o Exchange Online, consulte [Exchange Online: Configuração de IRM](configure-office365.md#exchangeonline-irm-configuration).

- Para o Exchange no local, veja [Implementar o conector Azure Rights Management](deploy-rms-connector.md).


## <a name="sharepoint-online-and-sharepoint-server"></a>SharePoint Online e SharePoint Server

Quando utiliza o SharePoint Online ou o SharePoint Server, pode proteger documentos ao utilizar a funcionalidade de gestão (IRM) de direitos de informações do SharePoint. Esta funcionalidade permite-os administradores protejam as listas ou bibliotecas para que quando um utilizador dá um documento, o ficheiro transferido é protegido para que apenas as pessoas autorizadas possam ver e utilizar o ficheiro de acordo com as políticas de proteção de informações que especificar. Por exemplo, o ficheiro poderá ser só de leitura, poderá desativar a cópia de texto, impedir guardar uma cópia local e evitar imprimir o ficheiro.

Documentos do Word, PowerPoint, Excel e PDF suportam esta proteção IRM do SharePoint. Por predefinição, a proteção é restrita à pessoa que transfere o documento. Pode alterar esta predefinição com uma opção de configuração com o nome **permitir proteção de grupo**, que expande a proteção a um grupo que especificar. Por exemplo, pode especificar um grupo que tenha permissão para editar documentos na biblioteca para que o mesmo grupo de utilizadores possa editar o documento fora do SharePoint, independentemente de qual usuário transferido o documento. Em alternativa, pode especificar um grupo que não é concedido permissões no SharePoint, mas os utilizadores nesta necessidade de grupo para aceder ao documento fora do SharePoint. 

Para listas do SharePoint e bibliotecas, esta proteção é sempre configurada por um administrador, nunca por um utilizador final. Pode definir as permissões ao nível do site e essas permissões, por predefinição, são herdadas por qualquer lista ou biblioteca nesse site. Se utilizar o SharePoint Online, os utilizadores também podem configurar a respetiva biblioteca do OneDrive para Empresas de modo a utilizar a proteção IRM.

Para obter um controlo mais detalhado, pode configurar uma lista ou biblioteca no site para parar de herdar permissões da lista ou biblioteca principal. Em seguida, pode configurar permissões IRM nesse nível (lista ou biblioteca), onde estas passam a ser referidas como "permissões exclusivas". No entanto, as permissões estão sempre definidas ao nível do contentor, pelo que não pode definir permissões em ficheiros individuais. 

Primeiro, o serviço de IRM tem de estar ativado para o SharePoint. Em seguida, especifique as permissões IRM para uma biblioteca. No caso do SharePoint Online e do OneDrive para Empresas, os utilizadores também podem especificar as permissões IRM para a respetiva biblioteca do OneDrive para Empresas. O SharePoint não utiliza modelos de política de direitos, apesar de existirem definições de configuração do SharePoint que pode selecionar para corresponder a algumas definições que pode especificar nos modelos.

Se utilizar o SharePoint Server, pode utilizar esta proteção IRM ao implementar o conector Azure Rights Management. Este conector funciona como um reencaminhamento entre os seus servidores no local e o serviço cloud do Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](deploy-rms-connector.md).

> [!NOTE]
> Atualmente, existem algumas limitações ao utilizar a IRM do SharePoint:
> 
> - Não é possível utilizar os modelos predefinidos ou proteção personalizada que gerir no portal do Azure. 
> 
> - Ficheiros que tenham uma extensão de nome de ficheiro. ppdf para ficheiros PDF protegidos não são suportados. Para obter mais informações sobre a visualização de documentos PDF protegidos, consulte [leitores de PDF protegido para o Microsoft Information Protection](./rms-client/protected-pdf-readers.md).
> 
> - Coautoria, quando mais de uma pessoa edita um documento ao mesmo tempo, não é suportada. Para editar um documento numa biblioteca protegido por IRM, deve primeiro veja o documento e transferi-lo e, em seguida, editá-lo na aplicação do Office. Conseqüentemente, apenas uma pessoa pode editar o documento de cada vez.

Para bibliotecas que não estão protegidos por IRM, se proteger um ficheiro que, em seguida, carrega para o SharePoint ou o OneDrive, o seguinte não funcionam com esse arquivo: Coautoria, Office Online, pesquisa, pré-visualização do documento, miniatura, deteção de dados Eletrónicos e prevenção de perda de dados (DLP).

Quando utiliza a proteção IRM do SharePoint, o serviço Azure Rights Management aplica restrições de utilização e a encriptação de dados aos documentos quando são transferidos do SharePoint e não quando o documento é criado inicialmente no SharePoint ou carregado para a biblioteca. Para obter informações sobre como os documentos estão protegidos antes de serem transferidos, veja [Encriptação de Dados no OneDrive para Empresas e no SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) da documentação do SharePoint.

Apesar de já não é novo, a seguinte publicação do blogue do Office 365 tem algumas informações adicionais que poderão ser úteis: [O que há de novo no gerenciamento de direitos de informação no SharePoint e o SharePoint Online](https://www.microsoft.com/en-us/microsoft-365/blog/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

Se estiver pronto para configurar o SharePoint para a IRM:

- Para o SharePoint Online, consulte [SharePoint Online e OneDrive para empresas: Configuração de IRM](configure-office365.md#sharepointonline-and-onedrive-for-business-irm-configuration).

- Para o SharePoint Server, veja [Implementar o conector Azure Rights Management](deploy-rms-connector.md).


## <a name="next-steps"></a>Passos Seguintes

Se tiver o Office 365, poderá interessar-lhe rever [File Protection Solutions in Office 365](/office365/enterprise/microsoft-cloud-it-architecture-resources#BKMK_O365fileprotect) (Soluções de Proteção de Ficheiros do Office 365), que indica as capacidades recomendadas para proteger ficheiros do Office 365.

Para ver como outras aplicações e serviços suportam o serviço Azure Rights Management do Azure Information Protection, consulte [Como as aplicações suportam o serviço Azure Rights Management](applications-support.md).

Se estiver pronto para começar a implementação, que inclui a configuração dessas aplicações e serviços, veja [Plano de implementação do Azure Information Protection](deployment-roadmap.md).
