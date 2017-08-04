---
title: "Configurar os direitos de utilização para o Azure Rights Management – AIP"
description: "Conheça os direitos específicos utilizados quando protege ficheiros ou e-mails com o serviço Azure Rights Management do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 62ea1579b61b096e1f7fe6900d72b1b8077c9ff1
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2017
---
# <a name="configuring-usage-rights-for-azure-rights-management"></a>Configuração de direitos de utilização para o Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

Quando definir a proteção em ficheiros ou e-mails com o serviço Azure Rights Management do Azure Information Protection e não utilizar um modelo, terá de configurar os direitos de utilização. Além disso, quando configurar modelos ou as etiquetas para proteção do Azure Rights Management, selecione os direitos de utilização que serão, em seguida, ser automaticamente aplicados quando o modelo ou etiqueta está selecionada por utilizadores, administradores ou serviços configurados. Por exemplo, no portal do Azure, pode selecionar funções que configuram um agrupamento lógico de direitos de utilização, ou pode configurar os direitos individuais.

Utilize este artigo para o ajudar a configurar os direitos de utilização que pretende para a aplicação que está a utilizar e para compreender como estes direitos são interpretados pelas aplicações.

## <a name="usage-rights-and-descriptions"></a>Direitos de utilização e descrições
A tabela seguinte lista e descreve os direitos de utilização suportados pelo Rights Management e de que forma são utilizados e interpretados. São listados pelo **Nome comum**, que é, geralmente, a forma como poderá ver o direito de utilização apresentado ou referenciado, como uma versão mais amigável do valor de palavra única que é utilizado no código (o valor **Codificação na política**). 

A **Constante ou o Valor de API** é o nome do SDK para uma chamada à API MSIPC, utilizada quando escreve uma aplicação otimizada por RMS que verifica a existência de um direito de utilização ou adiciona um direito de utilização a uma política.


|Direita|Descrição|Implementação|
|-------------------------------|---------------------------|-----------------|
|Nome comum: **Editar Conteúdo, Editar** <br /><br />Codificação na política: **DOCEDIT**|Permite ao utilizador modificar, reorganizar, formatar ou filtrar o conteúdo dentro da aplicação. Não concede o direito para guardar a cópia editada.|Direitos personalizados do Office: como parte das opções **Alterar** e **Controlo Total**. <br /><br />Nome no portal clássico do Azure: **Editar Conteúdo**<br /><br />Nome no portal do Azure: incluído em **Editar e guardar**<br /><br />Nome em modelos do AD RMS: **Editar** <br /><br />Constante ou valor de API: não aplicável.|
|Nome comum: **Guardar** <br /><br />Codificação na política: **EDIT**|Permite ao utilizador guardar o documento na sua localização atual.<br /><br />Nas aplicações do Office, este direito também permite que o utilizador modifique o documento.|Direitos personalizados do Office: como parte das opções **Alterar** e **Controlo Total**. <br /><br />Nome no portal clássico do Azure: **Guardar Ficheiro**<br /><br />Nome no portal do Azure: incluído em **Editar e guardar**<br /><br />Nome em modelos do AD RMS: **Guardar** <br /><br />Valor ou constante de API: `IPC_GENERIC_WRITE L"EDIT"`|
|Nome comum: **Comentário** <br /><br />Codificação na política: **COMMENT**|Ativa a opção para adicionar anotações ou comentários ao conteúdo.<br /><br />Este direito está disponível no SDK, disponível como uma política ad hoc no módulo AzureInformationProtection e Proteção RMS para o Windows PowerShell e foi implementado em certas aplicações de fornecedores de software. No entanto, não é amplamente utilizado e atualmente não é suportado por aplicações do Office.|Direitos personalizados do Office: não implementados. <br /><br />Nome no portal clássico do Azure: não implementado.<br /><br />Nome no portal do Azure: não implementado.<br /><br />Nome nos modelos do AD RMS: não implementado. <br /><br />Valor ou constante de API: `IPC_GENERIC_COMMENT L"COMMENT`|
|Nome comum: **Guardar Como, Exportar** <br /><br />Codificação na política: **EXPORT**|Ativa a opção para guardar o conteúdo com um nome de ficheiro diferente (Guardar Como). Para documentos do Office e o cliente do Azure Information Protection, pode guardar o ficheiro sem proteção.<br /><br />Este direito também permite que o utilizador efetue outras opções de exportação em aplicações, tais como **Enviar para o OneNote**.<br /><br /> Nota: se este direito não for concedido, as aplicações do Office permitirão que os utilizadores guardem um documento com um novo nome se o formato de ficheiro selecionado suportar nativamente a proteção do Rights Management.|Direitos personalizados do Office: como parte das opções **Alterar** e **Controlo Total**. <br /><br />Nome no portal clássico do Azure: **Exportar Conteúdo (Guardar Como)** <br /><br />Nome no portal do Azure: incluído em **Controlo total**<br /><br />Nome em modelos do AD RMS: **Exportar (Guardar Como)** <br /><br />Valor ou constante de API: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Nome comum: **Reencaminhar** <br /><br />Codificação na política: **FORWARD**|Ativa a opção para reencaminhar uma mensagem de e-mail e para adicionar destinatários às linhas **Para** e **Cc**. Este direito não se aplica a documentos; apenas a mensagens de e-mail.<br /><br />Não permite que o reencaminhador conceda direitos a outros utilizadores como parte da ação de reencaminhar. <br /><br />Quando conceder este direito, também concede o direito **Editar Conteúdo, Editar** (nome comum) para garantir que o e-mail original é enviado como parte da mensagem de e-mail reencaminhada e não como anexo. Este direito também é necessário quando envia um e-mail para outra organização que utilize o cliente do Outlook ou Outlook Web App.|Direitos personalizados do Office: negados ao utilizar a política padrão **Não Reencaminhar**.<br /><br />Nome no portal clássico do Azure: **Reencaminhar**<br /><br />Nome no portal do Azure: **Reencaminhar**<br /><br />Nome em modelos do AD RMS: **Reencaminhar** <br /><br />Valor ou constante de API: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Nome comum: **Controlo Total** <br /><br />Codificação na política: **OWNER**|Concede todos os direitos ao documento e podem ser efetuadas todas as ações disponíveis.<br /><br />Inclui a capacidade para remover a proteção e voltar a proteger um documento. <br /><br />Tenha em atenção que este direito de utilização não é igual ao [proprietário do Rights Management](#rights-management-issuer-and-rights-management-owner).|Direitos personalizados do Office: como a opção personalizada **Controlo Total**.<br /><br />Nome no portal clássico do Azure: **Controlo Total**<br /><br />Nome no portal do Azure: **Controlo total**<br /><br />Nome em modelos do AD RMS: **Controlo Total** <br /><br />Valor ou constante de API: `IPC_GENERIC_ALL L"OWNER"`|
|Nome comum: **Imprimir** <br /><br />Codificação na política: **PRINT**|Ativa as opções para imprimir o conteúdo.|Direitos personalizados do Office: como a opção **Imprimir Conteúdo** em permissões personalizadas. Não é uma definição por destinatário.<br /><br />Nome no portal clássico do Azure: **Imprimir**<br /><br />Nome no portal do Azure: **Imprimir**<br /><br />Nome em modelos do AD RMS: **Imprimir** <br /><br />Valor ou constante de API: `IPC_GENERIC_PRINT L"PRINT"`|
|Nome comum: **Responder** <br /><br />Codificação na política: **REPLY**|Ativa a opção **Responder** num cliente de e-mail, sem permitir alterações nas linhas **Para** ou **Cc**.<br /><br />Quando conceder este direito, também concede o direito **Editar Conteúdo, Editar** (nome comum) para garantir que o e-mail original é enviado como parte da mensagem de e-mail reencaminhada e não como anexo. Este direito também é necessário quando envia um e-mail para outra organização que utilize o cliente do Outlook ou Outlook Web App.|Direitos personalizados do Office: não aplicável.<br /><br />Nome no portal clássico do Azure: **Responder**<br /><br />Nome em modelos do AD RMS: **Responder** <br /><br />Valor ou constante de API: `IPC_EMAIL_REPLY`|
|Nome comum: **Responder a Todos** <br /><br />Codificação na política: **REPLYALL**|Ativa a opção **Responder a Todos** num cliente de e-mail, mas não permite que o utilizador adicione destinatários às linhas **Para** ou **Cc**.<br /><br />Quando conceder este direito, também concede o direito **Editar Conteúdo, Editar** (nome comum) para garantir que o e-mail original é enviado como parte da mensagem de e-mail reencaminhada e não como anexo. Este direito também é necessário quando envia um e-mail para outra organização que utilize o cliente do Outlook ou Outlook Web App.|Direitos personalizados do Office: não aplicável.<br /><br />Nome no portal clássico do Azure: **Responder a Todos**<br /><br />Nome no portal do Azure: **Responder a todos**<br /><br />Nome em modelos do AD RMS: **Responder a Todos** <br /><br />Valor ou constante de API: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Nome comum: **Ver, Abrir, Ler** <br /><br />Codificação na política: **VIEW**|Permite que o utilizador abra o documento e veja o conteúdo.|Direitos personalizados do Office: como a política personalizada **Ler**, opção **Ver**.<br /><br />Nome no portal clássico do Azure: **Ver**<br /><br />Nome no portal do Azure: **Ver conteúdo**<br /><br />Nome em modelos do AD RMS: **Responder a Todos** <br /><br />Valor ou constante de API: `IPC_GENERIC_READ L"VIEW"`|
|Nome comum: **Copiar** <br /><br />Codificação na política: **EXTRACT**|Ativa opções para copiar dados (incluindo capturas de ecrã) do documento para o mesmo ou outro documento.<br /><br />Em certas aplicações, também permite que todo o documento seja guardado numa forma não protegida.|Direitos personalizados do Office: como a opção da política personalizada **Permitir que os utilizadores com acesso de Leitura copiem conteúdo**.<br /><br />Nome no portal clássico do Azure: **Copiar e Extrair Conteúdo**<br /><br />Nome no portal do Azure: **Copiar e extrair conteúdo**<br /><br />Nome em modelos do AD RMS: **Extrair** <br /><br />Valor ou constante de API: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Nome comum: **Permitir Macros** <br /><br />Codificação na política: **OBJMODEL**|Ativa a opção para executar macros ou efetuar outro acesso programático ou remoto ao conteúdo num documento.|Direitos personalizados do Office: como a opção da política personalizada **Permitir Acesso Programático**. Não é uma definição por destinatário.<br /><br />Nome no portal clássico do Azure: **Permitir Macros**<br /><br />Nome no portal do Azure: incluído em todos os direitos que pode selecionar uma vez que este direito é necessário para a barra do Azure Information Protection nas aplicações do Office.<br /><br />Nome em modelos do AD RMS: **Permitir Macros** <br /><br />Constante ou valor de API: não implementado.|

## <a name="rights-included-in-permissions-levels"></a>Direitos incluídos nos níveis de permissões

Algumas aplicações agrupam os direitos de utilização em níveis de permissões, para facilitar a seleção de direitos de utilização que são normalmente utilizados em conjunto. Estes níveis de permissões ajudam a abstrair um nível de complexidade dos utilizadores, para que possam escolher opções baseadas em funções.  Por exemplo, **Revisor** e **Coautor**. Apesar de estas opções mostrarem frequentemente aos utilizadores um resumo dos direitos, podem não incluir todos os direitos listados na tabela anterior.

Utilize a tabela seguinte para obter uma lista destes níveis de permissões e uma lista completa dos direitos que contêm.

|Nível de Permissões|Aplicações|Direitos incluídos (nome comum)|
|---------------------|----------------|---------------------------------|
|Visualizador|Portal clássico do Azure <br /><br />Portal do Azure<br /><br /> Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, Abrir, Ler; Responder; Responder a Todos; Permitir Macros [[1]](#footnote-1)<br /><br />Nota: para e-mails utilize Revisor, em vez deste nível de permissão, para garantir que a resposta é recebida como uma mensagem de e-mail e não como um anexo. O Revisor também é necessário quando envia um e-mail para outra organização que utilize o cliente do Outlook ou Outlook Web App.|
|Revisor|Portal clássico do Azure <br /><br />Portal do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, Abrir, Ler; Guardar; Editar Conteúdo, Editar; Responder: Responder a Todos [[2]](#footnote-2); Reencaminhar [[2]](#footnote-2); Permitir Macros [[1]](#footnote-1)|
|Coautor|Portal clássico do Azure <br /><br />Portal do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, Abrir, Ler; Guardar; Editar Conteúdo, Editar; Copiar; Ver Direitos; Permitir Macros; Guardar Como, Exportar [[3]](#footnote-3); Imprimir; Responder [[2]](#footnote-2); Responder a Todos [[2]](#footnote-2); Reencaminhar [[2]](#footnote-2)|
|Coproprietário|Portal clássico do Azure <br /><br />Portal do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, Abrir, Ler; Guardar; Editar Conteúdo, Editar; Copiar; Ver Direitos; Permitir Macros; Guardar Como, Exportar; Imprimir; Responder [[2]](#footnote-2); Responder a Todos [[2]](#footnote-2); Reencaminhar [[2]](#footnote-2); Controlo Total|

----

###### <a name="footnote-1"></a>Nota de rodapé 1

Para o Cliente do Azure Information Protection para Windows, este direito é atualmente exigido para a barra do Information Protection nas aplicações do Office.

###### <a name="footnote-2"></a>Nota de rodapé 2
Não aplicável ao cliente do Azure Information Protection para Windows ou à aplicação de partilha Rights Management para Windows.

###### <a name="footnote-3"></a>Nota de rodapé 3
Não incluído no cliente do Azure Information Protection para Windows. Neste cliente, o direito de utilização de Exportação inclui a capacidade para remover a proteção.


## <a name="rights-included-in-the-default-templates"></a>Direitos incluídos nos modelos predefinidos
Os direitos incluídos com os modelos predefinidos são os seguintes:

|Nome a Apresentar|Direitos incluídos (nome comum)|
|----------------|---------------------------------|
|&lt;*nome da organização*&gt; *– Apenas Visualização Confidencial* <br /><br />ou<br /><br /> *Altamente Confidencial\Todos os Funcionários*|Ver, Abrir, Ler|
|&lt;*nome da organização*&gt; *– Confidencial* <br /><br />ou <br /><br />*Confidencial\Todos os Funcionários*|Ver, Abrir, Ler; Guardar; Editar Conteúdos, Editar; Ver Direitos; Permitir Macros; Reencaminhar; Responder; Responder a Todos|

## <a name="do-not-forward-option-for-emails"></a>Opção Não Reencaminhar para e-mails

Os clientes e serviços do Exchange (por exemplo, o cliente Outlook, a aplicação Outlook Web Access e as regras de transporte do Exchange) têm uma opção de proteção dos direitos de informação para e-mails adicional: **Não Reencaminhar**. 

Embora esta opção seja apresentada aos utilizadores (e os administradores do Exchange) como se fosse um modelo de Gestão de Direitos predefinido que podem selecionar, **Não Reencaminhar** não é um modelo. Isto explica por que motivo não pode vir no portal do Azure quando visualiza e gere modelos para o Azure Rights Management. Em vez disso, a opção **Não Reencaminhar** é um conjunto de direitos aplicados dinamicamente por utilizadores aos seus destinatários de e-mail.

Quando a opção **Não Reencaminhar** é aplicada a um e-mail, os destinatários não podem reencaminhá-lo, imprimi-lo, copiá-lo ou guardar anexos ou guardar com um nome diferente. Por exemplo, no cliente Outlook, o botão Reencaminhar não está disponível, as opções de menu **Guardar Como**, **Guardar Anexo** e **Imprimir** não estão disponíveis e não é possível adicionar ou alterar os destinatários nas caixas **Para**, **Cc** ou **Bcc**.

Existe uma diferença importante entre aplicar a opção **Não Reencaminhar** e aplicar um modelo que não conceda o direito de Reencaminhar a um e-mail: a opção **Não Reencaminhar** utiliza uma lista dinâmica de utilizadores autorizados que se baseia nos destinatários escolhidos pelo utilizador do e-mail original; enquanto os direitos no modelo têm uma lista estática de utilizadores autorizados especificados anteriormente pelo administrador. Qual a diferença? Vejamos um exemplo: 

Um utilizador pretende enviar algumas informações por e-mail a pessoas específicas no departamento de Marketing que não devem ser partilhadas com outras pessoas. Deverá proteger o e-mail com um modelo que restringe direitos (ver, responder e guardar) para o departamento de Marketing?  Ou deverá escolher a opção **Não Reencaminhar**? Ambas as escolhas impedem os destinatários de reencaminhar o e-mail. 

- Se aplicar o modelo, os destinatários continuam a poder partilhar as informações com outras pessoas no departamento de marketing. Por exemplo, um destinatário poderia utilizar o Explorador para arrastar e largar o e-mail numa localização partilhada ou numa unidade USB. Assim, qualquer pessoa do departamento de marketing (e o proprietário do e-mail) com acesso a esta localização pode ver as informações do e-mail.
 
- Se aplicar a opção **Não Reencaminhar**, os destinatários não conseguirão partilhar as informações com qualquer pessoa do outro departamento de marketing movendo o e-mail para outra localização. Neste cenário, apenas os destinatários originais (e o proprietário do e-mail) poderão ver as informações do e-mail.

> [!NOTE] 
> Utilize **Não Reencaminhar** quando for importante que restringir o acesso às informações do e-mail apenas os destinatários escolhidos pelo remetente. Utilize um modelo para e-mails para restringir os direitos a um grupo de pessoas especificadas anteriormente pelo administrador, independentemente dos destinatários escolhidos pelo remetente.

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

Por exemplo, o utilizador que criou o documento pode imprimi-lo, apesar de agora estar protegido com um modelo que não inclui o direito de utilização Imprimir. O mesmo utilizador pode sempre aceder ao seu documento, independentemente da definição de acesso offline ou da data de expiração que possa ter sido configurada nesse modelo. Além disso, como o proprietário do Rights Management tem o direito Controlo Total, este utilizador também pode proteger novamente o documento para conceder acesso a utilizadores adicionais (nessa altura o utilizador, para além de proprietário, também passa a ser emissor do Rights Management) e até remover a proteção. No entanto, apenas o emissor do Rights Management pode controlar e revogar um documento.

O proprietário do Rights Management de um documento ou e-mail é registado no campo **owner-email** nos [registos de utilização](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs).

Tenha em atenção que o proprietário do Rights Management é independente do Proprietário do sistema de ficheiros do Windows. Normalmente são iguais, mas podem ser diferentes, mesmo se não utilizar SDKs ou o PowerShell.

## <a name="see-also"></a>Consulte Também
[Configurar e gerir modelos do Azure Information Protection](configure-policy-templates.md))

[Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](configure-super-users.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

