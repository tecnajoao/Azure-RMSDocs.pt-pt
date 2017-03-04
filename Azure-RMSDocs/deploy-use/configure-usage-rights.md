---
title: "Configurar os direitos de utilização para o Azure Rights Management – AIP"
description: "Conheça os direitos específicos utilizados quando protege ficheiros ou e-mails com o serviço Azure Rights Management do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 34f77a0ff33a9a960e12bc53d62b38f4e6553c80
ms.lasthandoff: 02/24/2017


---

# <a name="configuring-usage-rights-for-azure-rights-management"></a>Configuração de direitos de utilização para o Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

Quando definir a proteção em ficheiros ou e-mails com o serviço Azure Rights Management do Azure Information Protection e não utilizar um modelo, terá de configurar os direitos de utilização. Além disso, quando configurar modelos personalizados para o Azure Rights Management, selecione os direitos de utilização que serão automaticamente aplicados quando o modelo for selecionado por utilizadores, administradores ou serviços configurados. Por exemplo, no portal clássico do Azure, pode selecionar funções que configuram um agrupamento de direitos de utilização lógico ou pode configurar os direitos individuais.

Utilize este artigo para o ajudar a configurar os direitos de utilização que pretende para a aplicação que está a utilizar e para compreender como estes direitos são interpretados pelas aplicações.

## <a name="usage-rights-and-descriptions"></a>Direitos de utilização e descrições
A tabela seguinte lista e descreve os direitos de utilização suportados pelo Rights Management e de que forma são utilizados e interpretados. São listados pelo **Nome comum**, que é, geralmente, a forma como poderá ver o direito de utilização apresentado ou referenciado, como uma versão mais amigável do valor de palavra única que é utilizado no código (o valor **Codificação na política**). A **Constante ou o Valor de API** é o nome do SDK para uma chamada à API MSIPC, utilizada quando escreve uma aplicação otimizada por RMS que verifica a existência de um direito de utilização ou adiciona um direito de utilização a uma política.


|Direita|Descrição|Implementação|
|-------------------------------|---------------------------|-----------------|
|Nome comum: **Editar Conteúdo, Editar** <br /><br />Codificação na política: **DOCEDIT**|Permite ao utilizador modificar, reorganizar, formatar ou filtrar o conteúdo dentro da aplicação. Não concede o direito para guardar a cópia editada.|Direitos personalizados do Office: como parte das opções **Alterar** e **Controlo Total**. <br /><br />Nome no portal clássico do Azure: **Editar Conteúdo**<br /><br />Nome em modelos do AD RMS: **Editar** <br /><br />Constante ou valor de API: não aplicável.|
|Nome comum: **Guardar** <br /><br />Codificação na política: **EDIT**|Permite ao utilizador guardar o documento na sua localização atual.<br /><br />Nas aplicações do Office, este direito também permite que o utilizador modifique o documento.|Direitos personalizados do Office: como parte das opções **Alterar** e **Controlo Total**. <br /><br />Nome no portal clássico do Azure: **Guardar Ficheiro**<br /><br />Nome em modelos do AD RMS: **Guardar** <br /><br />Valor ou constante de API: `IPC_GENERIC_WRITE L"EDIT"`|
|Nome comum: **Comentário** <br /><br />Codificação na política: **COMMENT**|Ativa a opção para adicionar anotações ou comentários ao conteúdo.<br /><br />Este direito está disponível no SDK, disponível como uma política ad hoc no módulo Proteção RMS para o Windows PowerShell e foi implementado em certas aplicações de fornecedores de software. No entanto, não é amplamente utilizado e atualmente não é suportado por aplicações do Office.|Direitos personalizados do Office: não implementados. <br /><br />Nome no portal clássico do Azure: não implementado.<br /><br />Nome nos modelos do AD RMS: não implementado. <br /><br />Valor ou constante de API: `IPC_GENERIC_COMMENT L"COMMENT`|
|Nome comum: **Guardar Como, Exportar** <br /><br />Codificação na política: **EXPORT**|Ativa a opção para guardar o conteúdo com um nome de ficheiro diferente (Guardar Como). Para documentos do Office e o cliente do Azure Information Protection, pode guardar o ficheiro sem proteção.<br /><br />Este direito também permite que o utilizador efetue outras opções de exportação em aplicações, tais como **Enviar para o OneNote**.|Direitos personalizados do Office: como parte das opções **Alterar** e **Controlo Total**. <br /><br />Nome no portal clássico do Azure: **Exportar Conteúdo (Guardar Como)**<br /><br />Nome em modelos do AD RMS: **Exportar (Guardar Como)** <br /><br />Valor ou constante de API: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Nome comum: **Reencaminhar** <br /><br />Codificação na política: **FORWARD**|Ativa a opção para reencaminhar uma mensagem de e-mail e para adicionar destinatários às linhas **Para** e **Cc**. Este direito não se aplica a documentos; apenas a mensagens de e-mail.<br /><br />Não permite que o reencaminhador conceda direitos a outros utilizadores como parte da ação de reencaminhar.|Direitos personalizados do Office: negados ao utilizar a política padrão **Não Reencaminhar**.<br /><br />Nome no portal clássico do Azure: **Reencaminhar**<br /><br />Nome em modelos do AD RMS: **Reencaminhar** <br /><br />Valor ou constante de API: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Nome comum: **Controlo Total** <br /><br />Codificação na política: **OWNER**|Concede todos os direitos ao documento e podem ser efetuadas todas as ações disponíveis.<br /><br />Inclui a capacidade para remover a proteção e voltar a proteger um documento.|Direitos personalizados do Office: como a opção personalizada **Controlo Total**.<br /><br />Nome no portal clássico do Azure: **Controlo Total**<br /><br />Nome em modelos do AD RMS: **Controlo Total** <br /><br />Valor ou constante de API: `IPC_GENERIC_ALL L"OWNER"`|
|Nome comum: **Imprimir** <br /><br />Codificação na política: **PRINT**|Ativa as opções para imprimir o conteúdo.|Direitos personalizados do Office: como a opção **Imprimir Conteúdo** em permissões personalizadas. Não é uma definição por destinatário.<br /><br />Nome no portal clássico do Azure: **Imprimir**<br /><br />Nome em modelos do AD RMS: **Imprimir** <br /><br />Valor ou constante de API: `IPC_GENERIC_PRINT L"PRINT"`|
|Nome comum: **Responder** <br /><br />Codificação na política: **REPLY**|Ativa a opção **Responder** num cliente de e-mail, sem permitir alterações nas linhas **Para** ou **Cc**.|Direitos personalizados do Office: não aplicável.<br /><br />Nome no portal clássico do Azure: **Responder**<br /><br />Nome em modelos do AD RMS: **Responder** <br /><br />Valor ou constante de API: `IPC_EMAIL_REPLY`|
|Nome comum: **Responder a Todos** <br /><br />Codificação na política: **REPLYALL**|Ativa a opção **Responder a Todos** num cliente de e-mail, mas não permite que o utilizador adicione destinatários às linhas **Para** ou **Cc**.|Direitos personalizados do Office: não aplicável.<br /><br />Nome no portal clássico do Azure: **Responder a Todos**<br /><br />Nome em modelos do AD RMS: **Responder a Todos** <br /><br />Valor ou constante de API: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Nome comum: **Ver, Abrir, Ler** <br /><br />Codificação na política: **VIEW**|Permite que o utilizador abra o documento e veja o conteúdo.|Direitos personalizados do Office: como a política personalizada **Ler**, opção **Ver**.<br /><br />Nome no portal clássico do Azure: **Ver**<br /><br />Nome em modelos do AD RMS: **Responder a Todos** <br /><br />Valor ou constante de API: `IPC_GENERIC_READ L"VIEW"`|
|Nome comum: **Copiar** <br /><br />Codificação na política: **EXTRACT**|Ativa opções para copiar dados (incluindo capturas de ecrã) do documento para o mesmo ou outro documento.<br /><br />Em certas aplicações, também permite que todo o documento seja guardado numa forma não protegida.|Direitos personalizados do Office: como a opção da política personalizada **Permitir que os utilizadores com acesso de Leitura copiem conteúdo**.<br /><br />Nome no portal clássico do Azure: **Copiar e Extrair Conteúdo**<br /><br />Nome em modelos do AD RMS: **Extrair** <br /><br />Valor ou constante de API: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Nome comum: **Permitir Macros** <br /><br />Codificação na política: **OBJMODEL**|Ativa a opção para executar macros ou efetuar outro acesso programático ou remoto ao conteúdo num documento.|Direitos personalizados do Office: como a opção da política personalizada **Permitir Acesso Programático**. Não é uma definição por destinatário.<br /><br />Nome no portal clássico do Azure: **Permitir Macros**<br /><br />Nome em modelos do AD RMS: **Permitir Macros** <br /><br />Constante ou valor de API: não implementado.|



## <a name="rights-included-in-permissions-levels"></a>Direitos incluídos nos níveis de permissões

Algumas aplicações agrupam os direitos de utilização em níveis de permissões, para facilitar a seleção de direitos de utilização que são normalmente utilizados em conjunto. Estes níveis de permissões ajudam a abstrair um nível de complexidade dos utilizadores, para que possam escolher opções baseadas em funções.  Por exemplo, **Revisor** e **Coautor**. Apesar de estas opções mostrarem frequentemente aos utilizadores um resumo dos direitos, podem não incluir todos os direitos listados na tabela anterior.

Utilize a tabela seguinte para obter uma lista destes níveis de permissões e uma lista completa dos direitos que contêm.

|Nível de Permissões|Aplicações|Direitos incluídos (nome comum)|
|---------------------|----------------|---------------------------------|
|Visualizador|Portal clássico do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, Abrir, Ler; Responder; Responder a Todos|
|Revisor|Portal clássico do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, Abrir, Ler; Guardar; Editar Conteúdo, Editar; Responder [[1]](#footnote-1); Responder a Todos [[1]](#footnote-1); Reencaminhar [[1]](#footnote-1)|
|Coautor|Portal clássico do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, Abrir, Ler; Guardar; Editar Conteúdo, Editar; Copiar; Ver Direitos; Permitir Macros; Guardar Como, Exportar [[2]](#footnote-2); Imprimir; Responder [[1]](#footnote-1); Responder a Todos [[1]](#footnote-1); Reencaminhar [[1]](#footnote-1)|
|Coproprietário|Portal clássico do Azure<br /><br />Aplicação de partilha Rights Management para Windows<br /><br />Cliente do Azure Information Protection para Windows|Ver, Abrir, Ler; Guardar; Editar Conteúdo, Editar; Copiar; Ver Direitos; Permitir Macros; Guardar Como, Exportar; Imprimir; Responder [[1]](#footnote-1); Responder a Todos [[1]](#footnote-1); Reencaminhar [[1]](#footnote-1) Controlo Total|

----

###### <a name="footnote-1"></a>Nota de rodapé 1
Não aplicável ao cliente do Azure Information Protection para Windows ou à aplicação de partilha Rights Management para Windows.

###### <a name="footnote-2"></a>Nota de rodapé 2
Não incluído no cliente do Azure Information Protection para Windows. Neste cliente, o direito de utilização de Exportação inclui a capacidade para remover a proteção.


## <a name="rights-included-in-the-default-templates"></a>Direitos incluídos nos modelos predefinidos
Os direitos incluídos com os modelos predefinidos são os seguintes:

|Nome a Apresentar|Direitos incluídos (nome comum)|
|----------------|---------------------------------|
|&lt;*nome da organização*&gt; *– Apenas Visualização Confidencial*|Ver, Abrir, Ler|
|&lt;*nome da organização*&gt; *– Confidencial*|Ver, Abrir, Ler; Guardar; Editar Conteúdos, Editar; Ver Direitos; Permitir Macros; Reencaminhar; Responder; Responder a Todos|

## <a name="do-not-forward-option-for-emails"></a>Opção Não Reencaminhar para e-mails

Os clientes e serviços do Exchange (por exemplo, o cliente Outlook, a aplicação Outlook Web Access e as regras de transporte do Exchange) têm uma opção de proteção dos direitos de informação para e-mails adicional: **Não Reencaminhar**. 

Embora esta opção seja apresentada ao utilizadores (e os administradores do Exchange) como se fosse um modelo de Gestão de Direitos predefinido que podem selecionar, **Não Reencaminhar** não é um modelo. Isto explica por que motivo não o vê no portal clássico do Azure quando vê e gere modelos para o Azure Rights Management. Em vez disso, a opção **Não Reencaminhar** é um conjunto de direitos aplicados dinamicamente por utilizadores aos seus destinatários de e-mail.

Quando a opção **Não Reencaminhar** é aplicada a um e-mail, os destinatários não podem reencaminhá-lo, imprimi-lo, copiá-lo ou guardar anexos ou guardar com um nome diferente. Por exemplo, no cliente Outlook, o botão Reencaminhar não está disponível, as opções de menu **Guardar Como**, **Guardar Anexo** e **Imprimir** não estão disponíveis e não é possível adicionar ou alterar os destinatários nas caixas **Para**, **Cc** ou **Bcc**.

Existe uma diferença importante entre aplicar a opção **Não Reencaminhar** e aplicar um modelo que não conceda o direito de Reencaminhar a um e-mail: a opção **Não Reencaminhar** utiliza uma lista dinâmica de utilizadores autorizados que se baseia nos destinatários escolhidos pelo utilizador do e-mail original; enquanto os direitos no modelo têm uma lista estática de utilizadores autorizados especificados anteriormente pelo administrador. Qual a diferença? Vejamos um exemplo: 

Um utilizador pretende enviar algumas informações por e-mail a pessoas específicas no departamento de Marketing que não devem ser partilhadas com outras pessoas. Deverá proteger o e-mail com um modelo que restringe direitos (ver, responder e guardar) para o departamento de Marketing?  Ou deverá escolher a opção **Não Reencaminhar**? Ambas as escolhas impedem os destinatários de reencaminhar o e-mail. 

- Se aplicar o modelo, os destinatários continuam a poder partilhar as informações com outras pessoas no departamento de marketing. Por exemplo, um destinatário poderia utilizar o Explorador para arrastar e largar o e-mail numa localização partilhada ou numa unidade USB. Assim, qualquer pessoa do departamento de marketing (e o proprietário do e-mail) com acesso a esta localização pode ver as informações do e-mail.
 
- Se aplicar a opção **Não Reencaminhar**, os destinatários não conseguirão partilhar as informações com qualquer pessoa do outro departamento de marketing movendo o e-mail para outra localização. Neste cenário, apenas os destinatários originais (e o proprietário do e-mail) poderão ver as informações do e-mail.

> [!NOTE] 
> Utilize **Não Reencaminhar** quando for importante que restringir o acesso às informações do e-mail apenas os destinatários escolhidos pelo remetente. Utilize um modelo para e-mails para restringir os direitos a um grupo de pessoas especificadas anteriormente pelo administrador, independentemente dos destinatários escolhidos pelo remetente.




## <a name="see-also"></a>Consulte Também
[Configurar modelos personalizados para o serviço Azure Rights Management](configure-custom-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


