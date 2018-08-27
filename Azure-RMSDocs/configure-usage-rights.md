---
title: Configurar os direitos de utilização para o Azure Rights Management – AIP
description: Conheça os direitos específicos utilizados quando protege ficheiros ou e-mails com o serviço Azure Rights Management do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/22/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9f7c9ef4e6a6eccc1f42fa60a78550f53d4a64b6
ms.sourcegitcommit: b2d5c77bf8a0271d8d23f170314c0f49c3a328b1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42920674"
---
# <a name="configuring-usage-rights-for-azure-rights-management"></a>Configuração de direitos de utilização para o Azure Rights Management

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Quando definir a proteção em ficheiros ou e-mails com o serviço Azure Rights Management do Azure Information Protection e não utilizar um modelo, terá de configurar os direitos de utilização. Além disso, quando configurar modelos ou etiquetas para a proteção Azure Rights Management, selecione os direitos de utilização que serão automaticamente aplicados quando o modelo ou a etiqueta é selecionada por utilizadores, administradores ou serviços configurados. Por exemplo, no portal do Azure, pode selecionar funções que configuram um agrupamento lógico de direitos de utilização, ou pode configurar os direitos individuais.

Utilize este artigo para o ajudar a configurar os direitos de utilização que pretende para a aplicação que está a utilizar e para compreender como estes direitos são interpretados pelas aplicações.

> [!NOTE] 
> Para ser completo, este artigo inclui valores a partir do portal clássico do Azure, que foram retiradas 08 de Janeiro de 2018.
>
> Para ajudar a migrar para o novo portal, consulte [tarefas que costumava realizar com o portal clássico do Azure](migrate-portal.md).

## <a name="usage-rights-and-descriptions"></a>Direitos de utilização e descrições
A tabela seguinte lista e descreve os direitos de utilização suportados pelo Rights Management e de que forma são utilizados e interpretados. São listados pelo respetivo **nome comum**, que normalmente é que possa ver a direito de utilização apresentado ou referenciado, como uma versão mais amigável do valor de palavra única que é utilizado no código (o **Encoding na política** valor). 

A **Constante ou o Valor de API** é o nome do SDK para uma chamada à API MSIPC, utilizada quando escreve uma aplicação otimizada por RMS que verifica a existência de um direito de utilização ou adiciona um direito de utilização a uma política.


|Direito de utilização|Descrição|Implementação|
|-------------------------------|---------------------------|-----------------|
|Nome comum: **Editar Conteúdo, Editar** <br /><br />Codificação na política: **DOCEDIT**|Permite ao utilizador modificar, reorganizar, formato, ou ordenar o conteúdo dentro do aplicativo. Não concede o direito para guardar a cópia editada.<br /><br />No Word, a menos que tenha do Office 365 ProPlus com uma versão mínima do [1807](https://docs.microsoft.com/officeupdates/monthly-channel-2018#version-1807-july-25), este direito não é suficiente para ativar ou desativar **controlar alterações**, ou para utilizar todos o registo de alterações recursos como um revisor. Em vez disso, para utilizar todas as alterações de faixa de opções exige o seguinte à direita: **controlo total**. |Direitos personalizados do Office: como parte das opções **Alterar** e **Controlo Total**. <br /><br />Nome no portal clássico do Azure: **Editar Conteúdo**<br /><br />Nome no portal do Azure: **editar conteúdo, editar (DOCEDIT)**<br /><br />Nome em modelos do AD RMS: **Editar** <br /><br />Constante ou valor de API: não aplicável.|
|Nome comum: **Guardar** <br /><br />Codificação na política: **EDIT**|Permite ao utilizador salvar o documento para a localização atual.<br /><br />Em aplicativos do Office, este direito também permite ao usuário modificar o documento e guarde-o para uma nova localização e um novo nome se o formato de ficheiro selecionado suportar nativamente a proteção do Rights Management. A restrição de formato do ficheiro garante que a proteção original não é possível remover o ficheiro.|Direitos personalizados do Office: como parte das opções **Alterar** e **Controlo Total**. <br /><br />Nome no portal clássico do Azure: **Guardar Ficheiro**<br /><br />Nome no portal do Azure: **guardar (editar)**<br /><br />Nome em modelos do AD RMS: **Guardar** <br /><br />Valor ou constante de API: `IPC_GENERIC_WRITE L"EDIT"`|
|Nome comum: **Comentário** <br /><br />Codificação na política: **COMMENT**|Ativa a opção para adicionar anotações ou comentários ao conteúdo.<br /><br />Este direito está disponível no SDK, disponível como uma política ad hoc no módulo AzureInformationProtection e Proteção RMS para o Windows PowerShell e foi implementado em certas aplicações de fornecedores de software. No entanto, não é amplamente utilizado e atualmente não é suportado por aplicações do Office.|Direitos personalizados do Office: não implementados. <br /><br />Nome no portal clássico do Azure: não implementado.<br /><br />Nome no portal do Azure: não implementado.<br /><br />Nome nos modelos do AD RMS: não implementado. <br /><br />Valor ou constante de API: `IPC_GENERIC_COMMENT L"COMMENT`|
|Nome comum: **Guardar Como, Exportar** <br /><br />Codificação na política: **EXPORT**|Ativa a opção para guardar o conteúdo com um nome de ficheiro diferente (Guardar Como). <br /><br />Para documentos do Office e o cliente do Azure Information Protection, o ficheiro pode ser guardado sem proteção e também voltar a proteger com permissões e as novas definições. Estes das ações permitidas significam que um utilizador que tenha este direito, pode alterar ou remover uma etiqueta do Azure Information Protection a partir de um documento protegido ou e-mail. <br /><br />Este direito também permite que o utilizador efetue outras opções de exportação em aplicações, tais como **Enviar para o OneNote**.<br /><br /> Nota: se este direito não for concedido, as aplicações do Office permitirão que os utilizadores guardem um documento com um novo nome se o formato de ficheiro selecionado suportar nativamente a proteção do Rights Management.|Direitos personalizados do Office: como parte das opções **Alterar** e **Controlo Total**. <br /><br />Nome no portal clássico do Azure: **Exportar Conteúdo (Guardar Como)** <br /><br />Nome no portal do Azure: **guardar como, exportar (EXPORTAR)**<br /><br />Nome em modelos do AD RMS: **Exportar (Guardar Como)** <br /><br />Valor ou constante de API: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Nome comum: **Reencaminhar** <br /><br />Codificação na política: **FORWARD**|Ativa a opção para reencaminhar uma mensagem de e-mail e para adicionar destinatários às linhas **Para** e **Cc**. Este direito não se aplica a documentos; apenas a mensagens de e-mail.<br /><br />Não permite que o reencaminhador conceda direitos a outros utilizadores como parte da ação de reencaminhar. <br /><br />Quando conceder este direito, também concede o direito **Editar Conteúdo, Editar** (nome comum) para garantir que o e-mail original é enviado como parte da mensagem de e-mail reencaminhada e não como anexo. Este direito também é necessário quando envia um e-mail para outra organização que utilize o cliente do Outlook ou Outlook Web App. Ou, para utilizadores na sua organização que estão excluídos com o Azure Rights Management service uma vez que implementou [controlos de inclusão](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|Direitos personalizados do Office: negados ao utilizar a política padrão **Não Reencaminhar**.<br /><br />Nome no portal clássico do Azure: **Reencaminhar**<br /><br />Nome no portal do Azure: **reencaminhar (encaminhamento)**<br /><br />Nome em modelos do AD RMS: **Reencaminhar** <br /><br />Valor ou constante de API: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Nome comum: **Controlo Total** <br /><br />Codificação na política: **OWNER**|Concede todos os direitos ao documento e podem ser efetuadas todas as ações disponíveis.<br /><br />Inclui a capacidade de remover a proteção e voltar a proteger um documento. <br /><br />Tenha em atenção que este direito de utilização não é igual ao [proprietário do Rights Management](#rights-management-issuer-and-rights-management-owner).|Direitos personalizados do Office: como a opção personalizada **Controlo Total**.<br /><br />Nome no portal clássico do Azure: **Controlo Total**<br /><br />Nome no portal do Azure: **controlo total (proprietário)**<br /><br />Nome em modelos do AD RMS: **Controlo Total** <br /><br />Valor ou constante de API: `IPC_GENERIC_ALL L"OWNER"`|
|Nome comum: **Imprimir** <br /><br />Encoding na política: **PRINT**|Ativa as opções para imprimir o conteúdo.|Direitos personalizados do Office: como a opção **Imprimir Conteúdo** em permissões personalizadas. Não é uma definição por destinatário.<br /><br />Nome no portal clássico do Azure: **Imprimir**<br /><br />Nome no portal do Azure: **imprimir (imprimir)**<br /><br />Nome em modelos do AD RMS: **Imprimir** <br /><br />Valor ou constante de API: `IPC_GENERIC_PRINT L"PRINT"`|
|Nome comum: **Responder** <br /><br />Codificação na política: **REPLY**|Ativa a opção **Responder** num cliente de e-mail, sem permitir alterações nas linhas **Para** ou **Cc**.<br /><br />Quando conceder este direito, também concede o direito **Editar Conteúdo, Editar** (nome comum) para garantir que o e-mail original é enviado como parte da mensagem de e-mail reencaminhada e não como anexo. Este direito também é necessário quando envia um e-mail para outra organização que utilize o cliente do Outlook ou Outlook Web App. Ou, para utilizadores na sua organização que estão excluídos com o Azure Rights Management service uma vez que implementou [controlos de inclusão](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|Direitos personalizados do Office: não aplicável.<br /><br />Nome no portal clássico do Azure: **Responder**<br /><br />Nome no portal clássico do Azure: **responder (RESPONDER)**<br /><br />Nome em modelos do AD RMS: **Responder** <br /><br />Valor ou constante de API: `IPC_EMAIL_REPLY`|
|Nome comum: **Responder a Todos** <br /><br />Codificação na política: **REPLYALL**|Ativa a opção **Responder a Todos** num cliente de e-mail, mas não permite que o utilizador adicione destinatários às linhas **Para** ou **Cc**.<br /><br />Quando conceder este direito, também concede o direito **Editar Conteúdo, Editar** (nome comum) para garantir que o e-mail original é enviado como parte da mensagem de e-mail reencaminhada e não como anexo. Este direito também é necessário quando envia um e-mail para outra organização que utilize o cliente do Outlook ou Outlook Web App. Ou, para utilizadores na sua organização que estão excluídos com o Azure Rights Management service uma vez que implementou [controlos de inclusão](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|Direitos personalizados do Office: não aplicável.<br /><br />Nome no portal clássico do Azure: **Responder a Todos**<br /><br />Nome no portal do Azure: **responder a todos (RESPONDER a todos)**<br /><br />Nome em modelos do AD RMS: **Responder a Todos** <br /><br />Valor ou constante de API: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Nome comum: **Ver, Abrir, Ler** <br /><br />Codificação na política: **VIEW**|Permite que o utilizador abra o documento e veja o conteúdo.<br /><br /> No Excel, este direito não é suficiente para classificar dados, o que requer o seguinte à direita: **editar conteúdo, editar**. Para filtrar dados no Excel, tem dos dois direitos seguintes: **editar conteúdo, editar** e **cópia**.|Direitos personalizados do Office: como a política personalizada **Ler**, opção **Ver**.<br /><br />Nome no portal clássico do Azure: **Ver**<br /><br />Nome no portal do Azure: **ver, abrir, ler (visualizar)**<br /><br />Nome em modelos AD RMS: **leitura** <br /><br />Valor ou constante de API: `IPC_GENERIC_READ L"VIEW"`|
|Nome comum: **Copiar** <br /><br />Codificação na política: **EXTRACT**|Ativa opções para copiar dados (incluindo capturas de ecrã) do documento para o mesmo ou outro documento.<br /><br />Em alguns aplicativos, também permite que todo o documento ser guardado numa forma não protegida.<br /><br />Skype para empresas e aplicativos de compartilhamento de tela semelhantes, o apresentador tem de ter este direito para apresentar com êxito um documento protegido. Se o apresentador não tem este direito, os participantes não podem ver o documento e apresenta como blacked a eles.|Direitos personalizados do Office: como a opção da política personalizada **Permitir que os utilizadores com acesso de Leitura copiem conteúdo**.<br /><br />Nome no portal clássico do Azure: **Copiar e Extrair Conteúdo**<br /><br />Nome no portal do Azure: **copiar (EXTRAIR)**<br /><br />Nome em modelos do AD RMS: **Extrair** <br /><br />Valor ou constante de API: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Nome comum: **ver direitos** <br /><br />Encoding na política: **VIEWRIGHTSDATA**|Permite que o utilizador veja a política que é aplicada ao documento.|Direitos personalizados do Office: não implementados.<br /><br />Nome no portal clássico do Azure: **ver direitos atribuídos**<br /><br />Nome no portal do Azure: **vista de direitos (VIEWRIGHTSDATA)**.<br /><br />Nome em modelos AD RMS: **ver direitos** <br /><br />Valor ou constante de API: `IPC_READ_RIGHTS L"VIEWRIGHTSDATA"`|
|Nome comum: **alterar direitos** <br /><br />Encoding na política: **EDITRIGHTSDATA**|Permite que o utilizador altere a política que é aplicada ao documento. Inclui a remoção da proteção.|Direitos personalizados do Office: não implementados.<br /><br />Nome no portal clássico do Azure: **alterar direitos**<br /><br />Nome no portal do Azure: **Editar direitos (EDITRIGHTSDATA)**.<br /><br />Nome em modelos AD RMS: **Editar direitos** <br /><br />Valor ou constante de API: `PC_WRITE_RIGHTS L"EDITRIGHTSDATA"`|
|Nome comum: **Permitir Macros** <br /><br />Codificação na política: **OBJMODEL**|Ativa a opção para executar macros ou efetuar outro acesso programático ou remoto ao conteúdo num documento.|Direitos personalizados do Office: como a opção da política personalizada **Permitir Acesso Programático**. Não é uma definição por destinatário.<br /><br />Nome no portal clássico do Azure: **Permitir Macros**<br /><br />Nome no portal do Azure: **Permitir Macros (OBJMODEL)**<br /><br />Nome em modelos do AD RMS: **Permitir Macros** <br /><br />Constante ou valor de API: não implementado.|

## <a name="rights-included-in-permissions-levels"></a>Direitos incluídos nos níveis de permissões

Algumas aplicações agrupam os direitos de utilização em níveis de permissões, para facilitar a seleção de direitos de utilização que são normalmente utilizados em conjunto. Estes níveis de permissões ajudam a abstrair um nível de complexidade dos utilizadores, para que possam escolher opções baseadas em funções.  Por exemplo, **Revisor** e **Coautor**. Apesar de estas opções mostrarem frequentemente aos utilizadores um resumo dos direitos, podem não incluir todos os direitos listados na tabela anterior.

Utilize a tabela seguinte para obter uma lista destes níveis de permissões e uma lista completa dos direitos de utilização que contêm. Os direitos de utilização são apresentados pela respetiva [nome comum](#usage-rights-and-descriptions).

|nível de permissões|Aplicações|Direitos de utilização incluídos|
|---------------------|----------------|---------------------------------|
|Visualizador|Portal clássico do Azure <br /><br />Portal do Azure<br /><br /> Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, abrir, ler; Ver direitos; Resposta [[1]](#footnote-1); Responder a todos [[1]](#footnote-1); Permitir Macros [[2]](#footnote-2)<br /><br />Nota: para e-mails utilize Revisor, em vez deste nível de permissão, para garantir que a resposta é recebida como uma mensagem de e-mail e não como um anexo. O Revisor também é necessário quando envia um e-mail para outra organização que utilize o cliente do Outlook ou Outlook Web App. Ou, para utilizadores na sua organização que estão excluídos com o Azure Rights Management service uma vez que implementou [controlos de inclusão](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy).|
|Revisor|Portal clássico do Azure <br /><br />Portal do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, abrir, ler; Guardar; Editar conteúdo, editar; Ver direitos; Resposta: Responder a todos [[3]](#footnote-3); Para a frente [[3]](#footnote-3); Permitir Macros [[2]](#footnote-2)|
|Coautor|Portal clássico do Azure <br /><br />Portal do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, abrir, ler; Guardar; Editar conteúdo, editar; Copiem; Ver direitos; Permitir Macros; Guardar como, exportar [[4]](#footnote-4); Imprimir; Resposta [[3]](#footnote-3); Responder a todos [[3]](#footnote-3); Reencaminhar [[3]](#footnote-3)|
|Coproprietário|Portal clássico do Azure <br /><br />Portal do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, abrir, ler; Guardar; Editar conteúdo, editar; Copiem; Ver direitos; Alterar direitos; Permitir Macros; Guardar como, exportar; Imprimir; Resposta [[3]](#footnote-3); Responder a todos [[3]](#footnote-3); Para a frente [[3]](#footnote-3); Controlo total|

----

###### <a name="footnote-1"></a>Nota de rodapé 1

Não incluído no portal do Azure.

###### <a name="footnote-2"></a>Nota de rodapé 2

Para o Cliente do Azure Information Protection para Windows, este direito é atualmente exigido para a barra do Information Protection nas aplicações do Office.

###### <a name="footnote-3"></a>Nota de rodapé 3
Não aplicável ao cliente do Azure Information Protection para Windows ou à aplicação de partilha Rights Management para Windows.

###### <a name="footnote-4"></a>Nota de rodapé 4
Não incluído no portal do Azure ou o cliente do Azure Information Protection para Windows.

## <a name="rights-included-in-the-default-templates"></a>Direitos incluídos nos modelos predefinidos
A tabela seguinte lista os direitos de utilização que são incluídos quando os modelos predefinidos são criados. Os direitos de utilização são apresentados pela respetiva [nome comum](#usage-rights-and-descriptions).

Estes modelos predefinidos são criados quando a sua subscrição foi comprada e os nomes e os direitos de utilização podem ser [alterado](configure-policy-templates.md) no portal do Azure. 

|Nome a apresentar do modelo|Direitos de utilização de 6 de Outubro de 2017 até à data atual|Direitos de utilização antes de 6 de Outubro de 2017|
|----------------|--------------------|----------|
|\<*nome da organização >-apenas visualização confidencial* <br /><br />ou<br /><br /> *Altamente Confidencial\Todos os Funcionários*|Ver, abrir, ler; Copiem; Ver direitos; Permitir Macros; Imprimir; Reencaminhar; Responder; Responder a todos; Guardar; Editar conteúdo, editar|Ver, Abrir, Ler|
|\<*nome da organização > – confidencial* <br /><br />ou <br /><br />*Confidencial\Todos os Funcionários*|Ver, abrir, ler; Guardar como, exportar; Copiem; Ver direitos; Alterar direitos; Permitir Macros; Imprimir; Reencaminhar; Responder; Responder a todos; Guardar; Editar conteúdo, editar; Controlo total|Ver, abrir, ler; Guardar como, exportar; Editar conteúdo, editar; Ver direitos; Permitir Macros; Reencaminhar; Responder; Responder a todos|

## <a name="do-not-forward-option-for-emails"></a>Opção Não Reencaminhar para e-mails

Clientes do Exchange e serviços (por exemplo, o cliente do Outlook, a aplicação Outlook Web Access e as regras de fluxo de correio do Exchange) têm uma opção de proteção de direitos de informação adicional para e-mails: **não reencaminhar**. 

Embora esta opção seja apresentada aos utilizadores (e os administradores do Exchange) como se fosse um modelo de Gestão de Direitos predefinido que podem selecionar, **Não Reencaminhar** não é um modelo. Isto explica por que não é possível vê-lo no portal do Azure quando visualizar e gerir modelos de proteção. Em vez disso, o **não reencaminhar** opção é um conjunto de direitos de utilização que é aplicado dinamicamente por utilizadores aos seus destinatários de e-mail.

Quando o **não reencaminhar** opção é aplicada a um e-mail, o e-mail é encriptada e os destinatários têm de ser autenticados. Em seguida, os destinatários não podem reencaminhá-lo, imprimi-lo ou copiá-los. Por exemplo, no cliente do Outlook, o botão reencaminhar não está disponível, o **guardar como** e **impressão** não estão disponíveis opções de menu, e não é possível adicionar ou alterar os destinatários no **para**, **Cc**, ou **Bcc** caixas.

Desprotegido [documentos do Office](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) que estão anexados à mensagem de e-mail automaticamente herdam as mesmas restrições. Os direitos de uso aplicadas a estes documentos **editar conteúdo, editar**; **Guardar**; **Ver, abrir, ler**; e **Permitir Macros**. Se pretender que os direitos de utilização diferentes para um anexo ou o anexo não é um documento do Office que suporte esta proteção herdada, proteja o ficheiro antes de ligá-los para o e-mail. Em seguida, pode atribuir os direitos de utilização específico que necessita para o ficheiro. 

### <a name="difference-between-do-not-forward-and-not-granting-the-forward-usage-right"></a>Diferença entre não reencaminhar e não conceder o direito de utilização de encaminhamento

Há uma distinção importante entre aplicar a **não reencaminhar** opção e aplicar um modelo que não conceda a **reencaminhar** utilização diretamente para uma mensagem de e-mail: O **não reencaminhar** opção utiliza uma lista dinâmica de utilizadores autorizados que se baseia nos destinatários escolhidos do utilizador do e-mail original; ao passo que os direitos no modelo tem uma lista estática de utilizadores autorizados especificados anteriormente o administrador. Qual a diferença? Vejamos um exemplo: 

Um utilizador pretende enviar algumas informações por e-mail a pessoas específicas no departamento de Marketing que não devem ser partilhadas com outras pessoas. Deverá proteger o e-mail com um modelo que restringe direitos (ver, responder e guardar) para o departamento de Marketing?  Ou deverá escolher a opção **Não Reencaminhar**? Ambas as escolhas impedem os destinatários de reencaminhar o e-mail. 

- Se aplicar o modelo, os destinatários continuam a poder partilhar as informações com outras pessoas no departamento de marketing. Por exemplo, um destinatário poderia utilizar o Explorador para arrastar e largar o e-mail numa localização partilhada ou numa unidade USB. Assim, qualquer pessoa do departamento de marketing (e o proprietário do e-mail) com acesso a esta localização pode ver as informações do e-mail.
 
- Se aplicar a opção **Não Reencaminhar**, os destinatários não conseguirão partilhar as informações com qualquer pessoa do outro departamento de marketing movendo o e-mail para outra localização. Neste cenário, apenas os destinatários originais (e o proprietário do e-mail) poderão ver as informações do e-mail.

> [!NOTE] 
> Utilize **Não Reencaminhar** quando for importante que restringir o acesso às informações do e-mail apenas os destinatários escolhidos pelo remetente. Utilize um modelo para e-mails para restringir os direitos a um grupo de pessoas especificadas anteriormente pelo administrador, independentemente dos destinatários escolhidos pelo remetente.

## <a name="encrypt-only-option-for-emails"></a>Opção de criptografar apenas para e-mails

Quando o Exchange Online usa os novos recursos para encriptação de mensagens do Office 365, uma nova opção de e-mail torna-se disponíveis: **só de criptografar**.

Esta opção está a ser implementada para inquilinos que utilizam o Exchange Online, inicialmente apenas para o Outlook na web e como outra opção de proteção de direitos para uma regra de fluxo de correio. Para obter mais informações, consulte o seguinte anúncio de mensagem de blogue da equipa do Office: [criptografar apenas serem implementadas na encriptação de mensagens do Office 365](https://aka.ms/omefeb2018).

Quando esta opção estiver selecionada, o e-mail é encriptada e os destinatários têm de ser autenticados. Em seguida, os destinatários têm todos os direitos de utilização, exceto **guardar como, exportar** e **controlo total**. Esta combinação de direitos de utilização significa que os destinatários têm sem restrições, exceto pelo fato de não é possível remover a proteção. Por exemplo, um destinatário pode copiar a partir do e-mail, imprimi-lo e reencaminhá-lo. 

Da mesma forma, por predefinição, desprotegidos [documentos do Office](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) que estão anexados à mensagem de e-mail herdam as mesmas permissões. Esses documentos são automaticamente protegidos e quando são transferidos, pode podem ser guardadas, editados, copiados e impressas a partir de aplicações do Office pelos destinatários. Quando o documento é salvo por um destinatário, podem ser guardado para um novo nome e até mesmo um formato diferente. No entanto, apenas os formatos de ficheiro que suportam a proteção estão disponíveis para que o documento não é possível guardar sem a proteção original. Se pretender que os direitos de utilização diferentes para um anexo ou o anexo não é um documento do Office que suporte esta proteção herdada, proteja o ficheiro antes de ligá-los para o e-mail. Em seguida, pode atribuir os direitos de utilização específico que necessita para o ficheiro.

Em alternativa, pode alterar essa herança de proteção de documentos, utilizando qualquer um dos seguintes parâmetros de configuração que definiu com o [PowerShell do Exchange Online](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps) comando, **Set-IRMConfiguration** . Quando não precisa manter a proteção original para o documento depois do utilizador é autenticado, utilize estas opções:

- Para remover a proteção do documento para todos os destinatários: `Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true`. Quando esses destinatários abrem a mensagem de e-mail, o documento não está protegido.

- Para remover a proteção do documento apenas para os destinatários que visualizar o documento no browser (normalmente, uma vez que ele é enviado para um endereço do fornecedor de redes sociais, como o Gmail): `Set-IRMConfiguration -DecryptAttachmentFromPortal $true`. Quando esses destinatários transferir o documento, a proteção é removida.

Para obter mais informações sobre como remover a proteção apenas para os destinatários que visualizar o documento no browser, consulte a postagem no blog Office [controlo de administração para anexos já está disponíveis na encriptação de mensagens do Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007). Se precisar de um documento anexado para manter a proteção original, consulte [proteger colaboração de documentos utilizando o Azure Information Protection](secure-collaboration-documents.md).

## <a name="rights-management-issuer-and-rights-management-owner"></a>Emissor e proprietário do Rights Management

Quando um documento ou e-mail é protegido com o serviço Azure Rights Management, a conta que protege esses conteúdos torna-se automaticamente o emissor dos mesmos. Esta conta é registada no campo **issuer** nos [registos de utilização](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs). 

Ao emissor do Rights Management é sempre concedido o direito de utilização Controlo Total para o documento ou e-mail e além disso:

- Se as definições de proteção incluírem uma data de expiração, o emissor do Rights Management ainda pode abrir e editar o documento ou e-mail após essa data.

- O emissor do Rights Management pode aceder sempre ao documento ou e-mail offline.

- O emissor do Rights Management ainda pode abrir um documento após o mesmo ser revogado. 

Por predefinição, esta conta também é o **proprietário do Rights Management** para esses conteúdos, o que acontece quando o utilizador que criou o documento ou e-mail inicia a proteção. No entanto, estes são alguns cenários em que um administrador ou serviço pode proteger conteúdos em nome dos utilizadores. Por exemplo:

- Um administrador pode proteger ficheiros em massa numa partilha de ficheiros: a conta de administrador no Azure AD protege os documentos dos utilizadores.

- O conector Rights Management protege os documentos do Office numa pasta do Windows Server: a conta principal do serviço no Azure AD que é criada para o conector RMS protege os documentos dos utilizadores.

Nestes cenários, o emissor do Rights Management pode atribuir o proprietário do Rights Management a outra conta ao utilizar os SDKs do Azure Information Protection ou o PowerShell. Por exemplo, quando utiliza o cmdlet do PowerShell [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) com o cliente do Azure Information Protection, pode especificar o parâmetro **OwnerEmail** para atribuir o proprietário do Rights Management a outra conta. 

Quando o emissor do Rights Management efetua a proteção em nome dos utilizadores, a atribuição do proprietário do Rights Management garante que o documento original ou o proprietário do e-mail tem o mesmo nível de controlo sob os seus conteúdos protegidos, como se tivessem sido os próprios a iniciar a proteção. 

Por exemplo, o utilizador que criou o documento pode imprimi-lo, apesar de agora estar protegido com um modelo que não inclui o direito de utilização Imprimir. O mesmo utilizador pode sempre aceder ao seu documento, independentemente da definição de acesso offline ou da data de expiração que possa ter sido configurada nesse modelo. Além disso, como o proprietário do Rights Management tem o direito de utilização controlo total, este utilizador pode também voltar a proteger o documento para conceder acesso (altura em que o usuário, em seguida, torna-se o emissor do Rights Management, bem como o proprietário do Rights Management), utilizadores adicionais e este utilizador pode até mesmo remover a proteção. No entanto, apenas o emissor do Rights Management pode controlar e revogar um documento.

O proprietário do Rights Management de um documento ou e-mail é registado no campo **owner-email** nos [registos de utilização](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs).

Tenha em atenção que o proprietário do Rights Management é independente do Proprietário do sistema de ficheiros do Windows. Normalmente são iguais, mas podem ser diferentes, mesmo se não utilizar SDKs ou o PowerShell.

## <a name="rights-management-use-license"></a>Licença de utilização do Rights Management

Quando um utilizador abre um documento ou e-mail que tenha sido protegido pelo Azure Rights Management, uma licença de utilização do Rights Management para esse conteúdo é concedida ao utilizador. Esta licença de utilização é um certificado que contém os direitos de utilização do utilizador para o documento ou mensagem de e-mail e a chave de encriptação que foi utilizada para encriptar o conteúdo. A licença de utilização também contém uma data de expiração se isso tiver sido definido, e quanto a licença de utilização do é válida.

Um utilizador tem de ter uma licença de uso válidos para abrir o conteúdo, além do respetivo certificado de conta de direitos (RAC), que é um certificado que tenha concedido quando o [ambiente do utilizador é inicializado](how-does-it-work.md#initializing-the-user-environment) e, em seguida, renovada de 31 dias.

Durante o período de licença de utilização, o utilizador não é reautenticar ou reauthorized para o conteúdo. Isso permite que o usuário continue e abra o documento protegido ou o e-mail sem uma ligação à Internet. Quando o período de validade de licença de utilização expira, da próxima vez que o usuário acessa o documento protegido ou o e-mail, o utilizador tem de ser reautenticar e reauthorized. 

Quando os documentos e e-mails estão protegidos com uma etiqueta ou um modelo que define as definições de proteção, pode alterar estas definições na etiqueta ou modelo sem ter de voltar a proteger o conteúdo. Se o usuário já acessa o conteúdo, as alterações entrem em vigor após a expiração de sua licença de utilização. No entanto, quando os utilizadores aplicar permissões personalizadas (também conhecido como uma política de direitos do ad-hoc) e estas permissões precisam alterar depois do documento ou correio eletrónico está protegido, que o conteúdo deve ser protegido novamente com as novas permissões. Permissões personalizadas para uma mensagem de e-mail são implementadas com a opção não reencaminhar.

A predefinição utilizar validade de licença período para um inquilino é 30 dias e pode configurar este valor utilizando o cmdlet do PowerShell, [Set-AadrmMaxUseLicenseValidityTime](/powershell/module/aadrm/set-aadrmmaxuselicensevaliditytime). Pode configurar uma definição mais restritiva para quando a proteção é aplicada ao utilizar um modelo ou a etiqueta:

- Quando configurar uma etiqueta ou um modelo no portal do Azure, o período de validade de licença de utilização tem seu valor a partir da **permitir que a definição de acesso offline**. 
    
    Para obter mais informações e orientações para configurar esta definição no portal do Azure, consulte a [informações sobre as definições de proteção](configure-policy-protection.md#information-about-the-protection-settings) tabela das instruções de como configurar uma etiqueta para proteção do Rights Management.

- Quando configurar um modelo com o PowerShell, o período de validade de licença de utilização tem seu valor a partir da *LicenseValidityDuration* parâmetro na [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) e [ Adicionar-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate) cmdlets.
    
    Para obter mais informações e orientações para configurar esta definição com o PowerShell, consulte a ajuda de cada cmdlet.

## <a name="see-also"></a>Consulte Também
[Configurar e gerir modelos do Azure Information Protection](configure-policy-templates.md)

[Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](configure-super-users.md)


