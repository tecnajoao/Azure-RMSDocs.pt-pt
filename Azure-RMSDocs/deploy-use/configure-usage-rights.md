---
# required metadata

title: Configuração de direitos de utilização para o Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuração de direitos de utilização para o Azure Rights Management

*Aplica-se a: Azure Rights Management, Office 365*

Quando definir a proteção em ficheiros ou e-mails com o Azure Rights Management (Azure RMS) e não utilizar um modelo, terá de configurar os direitos de utilização. Além disso, quando configurar modelos personalizados para o Azure RMS, selecione os direitos de utilização que serão automaticamente aplicados quando o modelo for selecionado por utilizadores, administradores ou serviços configurados. Por exemplo, no portal clássico do Azure, pode selecionar funções que configuram um agrupamento de direitos de utilização lógico ou pode configurar os direitos individuais.

Utilize este artigo para o ajudar a configurar os direitos de utilização que pretende para a aplicação que está a utilizar e para compreender como estes direitos são interpretados pelas aplicações.

## Direitos de utilização e descrições
As secções seguintes listam e descrevem os direitos de utilização suportados pelo Rights Management e de que forma são utilizados e interpretados. São listados pelo **Nome comum**, que é, geralmente, a forma como poderá ver o direito de utilização apresentado ou referenciado, como uma versão mais amigável do valor de palavra única que é utilizado no código (o valor **Codificação na política**). A **Constante ou o Valor de API** é o nome do SDK para uma chamada à API MSIPC, utilizada quando escreve uma aplicação otimizada por RMS que verifica a existência de um direito de utilização ou adiciona um direito de utilização a uma política.


### Editar Conteúdo, Editar

Permite ao utilizador modificar, reorganizar, formatar ou filtrar o conteúdo dentro da aplicação. Não concede o direito para guardar a cópia editada.

**Codificação na política**: DOCEDIT

**Direitos personalizados de implementação no Office**: como parte das opções *Alterar* e *Controlo Total*.**

**Nome no portal clássico do Azure**: *Editar Conteúdo*

**Nome em modelos de AD RMS**: *Editar*

**Constante ou valor de API**: *Não aplicável*

Nas aplicações do Office, este direito também permite que o utilizador guarde o documento.

---

### Guardar

Permite ao utilizador guardar o documento na sua localização atual.

**Codificação na política**: EDIT

**Direitos personalizados de implementação no Office**: como parte das opções *Alterar* e *Controlo Total*.

**Nome no portal clássico do Azure**: *Guardar Ficheiro*

**Nome em modelos de AD RMS**: *Guardar*

**Constante ou valor de API**: IPC_GENERIC_WRITEL"EDIT"

Nas aplicações do Office, este direito também permite que o utilizador modifique o documento.

---

### Comentário

Ativa a opção para adicionar anotações ou comentários ao conteúdo.

**Codificação na política**: COMMENT

**Direitos personalizados de implementação no Office**: não implementados.

**Nome no portal clássico do Azure**: não implementado.

**Nome nos modelos de AD RMS:** não implementado.

**Constante ou valor de API:** IPC_GENERIC_COMMENTL"COMMENT

Este direito está disponível no SDK, disponível como uma política ad hoc no módulo Proteção RMS para o Windows PowerShell e foi implementado em certas aplicações de fornecedores de software. No entanto, não é amplamente utilizado e atualmente não é suportado por aplicações do Office.

---

### Guardar Como, Exportar

Ativa a opção para guardar o conteúdo com um nome de ficheiro diferente (Guardar Como). Dependendo da aplicação, o ficheiro pode ser guardado sem proteção.

**Codificação na política:** EXPORT

**Direitos personalizados de implementação no Office:** como parte das opções *Alterar* e *Controlo Total*.

**Nome no portal clássico do Azure:** *Exportar Conteúdo (Guardar Como)*

**Nome em modelos de AD RMS:** *Exportar (Guardar Como)*

**Constante ou valor de API:** IPC_GENERIC_EXPORTL"EXPORT"

Este direito também permite que o utilizador efetue outras opções de exportação em aplicações, tais como *Enviar para o OneNote*.

---

### Reencaminhar

Ativa a opção para reencaminhar uma mensagem de e-mail e para adicionar destinatários às linhas *Para* e *Cc*.

**Codificação na política:** FORWARD

**Direitos personalizados de implementação no Office:** negados ao utilizar a política padrão *Não Reencaminhar*.

**Nome no portal clássico do Azure:** *Reencaminhar*

**Nome em modelos de AD RMS:** *Reencaminhar*

**Constante ou valor de API:** IPC_EMAIL_FORWARDL"FORWARD"

Não permite que o reencaminhador conceda direitos a outros utilizadores como parte da ação de reencaminhar.

---

### Controlo Total

Concede todos os direitos ao documento e podem ser efetuadas todas as ações disponíveis.

**Codificação na política:** OWNER

**Direitos personalizados de implementação no Office:** como a opção personalizada *Controlo Total*.

**Nome no portal clássico do Azure:** *Controlo Total*

**Nome em modelos de AD RMS:** *Controlo Total*

**Constante ou valor de API:** IPC_GENERIC_ALLL"OWNER"

Inclui a capacidade para remover a proteção.

---

### Imprimir

Ativa as opções para imprimir o conteúdo.

**Codificação na política:** PRINT

**Direitos personalizados de implementação no Office:** como a opção *Imprimir Conteúdo* em permissões personalizadas. Não é uma definição por destinatário.

**Nome no portal clássico do Azure:** *Imprimir*

**Nome em modelos de AD RMS** *Imprimir*

**Constante ou valor de API:** IPC_GENERIC_PRINTL"PRINT

---

### Responder

Ativa a opção Responder num cliente de e-mail, sem permitir alterações nas linhas *Para* ou *Cc*.

**Codificação na política:** REPLY

**Direitos personalizados de implementação no Office:** não aplicável

**Nome no portal clássico do Azure:** *Responder*

**Nome em modelos de AD RMS:** *Responder*

**Constante ou valor de API:** IPC_EMAIL_REPLY

---

### Responder a Todos

Ativa a opção *Responder a Todos* num cliente de e-mail, mas não permite que o utilizador adicione destinatários às linhas *Para* ou *Cc*.

**Codificação na política:** REPLYALL

**Direitos personalizados de implementação no Office:** não aplicável

**Nome no portal clássico do Azure:** *Responder a Todos*

**Nome em modelos de AD RMS:** *Responder a Todos*

**Constante ou valor de API:** IPC_EMAIL_REPLYALLL"REPLYALL"

---

### Ver, Abrir, Ler

Permite que o utilizador abra o documento e veja o conteúdo.

**Codificação na política:** VIEW

**Direitos personalizados de implementação no Office:** como a política personalizada *Ler*, opção *Ver*.

**Nome no portal clássico do Azure:** *Ver Conteúdo*

**Nome em modelos de AD RMS:** *Ver*

**Constante ou valor de API:** IPC_GENERIC_READL"VIEW"

---

### Ver Direitos

Permite que o utilizador veja a política que é aplicada ao documento.

**Codificação na política:** VIEWRIGHTSDATA

**Direitos personalizados de implementação no Office:** não implementados.

**Nome no portal clássico do Azure:** *Ver Direitos Atribuídos*

**Nome em modelos de AD RMS:** *Ver Direitos*

**Constante ou valor de API:** IPC_READ_RIGHTSL"VIEWRIGHTSDATA"

---

### Nome comum: Ver Direitos

Permite que o utilizador veja a política que é aplicada ao documento.

**Codificação na política:** VIEWRIGHTSDATA

**Direitos personalizados de implementação no Office:** não implementados.

**Nome no portal clássico do Azure:** *Ver Direitos Atribuídos*

**Nome em modelos de AD RMS:** *Ver Direitos*

**Constante ou valor de API:** IPC_READ_RIGHTSL"VIEWRIGHTSDATA"

Ignorado por algumas aplicações.

---

### Alterar Direitos

Permite que o utilizador altere a política que é aplicada ao documento. Inclui a remoção da proteção.

**Codificação na política**: EDITRIGHTSDATA

**Direitos personalizados de implementação no Office:** não implementados.

**Nome no portal clássico do Azure:** *Alterar Direitos*

**Nome em modelos de AD RMS:** *Editar Direitos*

**Constante ou valor de API:** IPC_WRITE_RIGHTSL"EDITRIGHTSDATA"

---

### Permitir Macros

Ativa a opção para executar macros ou efetuar outro acesso programático ou remoto ao conteúdo num documento.

**Codificação na política:** OBJMODEL

**Direitos personalizados de implementação no Office:** como a opção da política personalizada *Permitir Acesso Programático*. Não é uma definição por destinatário.

**Nome no portal clássico do Azure:** *Permitir Macros*

**Nome em modelos de AD RMS:** *Permitir Macros*

**Constante ou valor de API:** Não aplicável


## Direitos incluídos nos níveis de permissões

Algumas aplicações agrupam os direitos de utilização em níveis de permissões, para facilitar a seleção de direitos de utilização que são normalmente utilizados em conjunto. Estes níveis de permissões ajudam a abstrair um nível de complexidade dos utilizadores, para que possam escolher opções baseadas em funções.  Por exemplo, **Revisor** e **Coautor**. Apesar de estas opções mostrarem frequentemente aos utilizadores um resumo dos direitos, podem não incluir todos os direitos listados na tabela anterior.

Utilize a tabela seguinte para obter uma lista destes níveis de permissões e uma lista completa dos direitos que contêm.

|Nível de Permissões|Aplicações|Direitos incluídos (nome comum)|
|---------------------|----------------|---------------------------------|
|Visualizador|Portal clássico do Azure<br /><br />Aplicação de partilha Rights Management para Windows|Ver, Abrir, Ler; Responder; Responder a Todos|
|Revisor|Portal clássico do Azure<br /><br />Aplicação de partilha Rights Management para Windows|Ver, Abrir, Ler; Guardar; Editar Conteúdo, Editar; Responder [[1]](#footnote-1); Responder a Todos [[1]](#footnote-1); Reencaminhar [[1]](#footnote-1)|
|Coautor|Portal clássico do Azure<br /><br />Aplicação de partilha Rights Management para Windows|Ver, Abrir, Ler; Guardar; Editar Conteúdo, Editar; Copiar; Ver Direitos; Alterar Direitos; Permitir Macros; Guardar Como, Exportar; Imprimir; Responder [[1]](#footnote-1); Responder a Todos [[1]](#footnote-1); Reencaminhar [[1]](#footnote-1)|
|Coproprietário|Portal clássico do Azure<br /><br />Aplicação de partilha Rights Management para Windows|Ver, Abrir, Ler; Guardar; Editar Conteúdo, Editar; Copiar; Ver Direitos; Alterar Direitos; Permitir Macros; Guardar Como, Exportar; Imprimir; Responder [[1]](#footnote-1); Responder a Todos [[1]](#footnote-1); Reencaminhar [[1]](#footnote-1); Controlo Total|

----

###### Nota de rodapé 1
Não aplicável à aplicação de partilha Rights Management para o Windows.

## Direitos incluídos nos modelos predefinidos
Os direitos incluídos com os modelos predefinidos são os seguintes:

|Nome a Apresentar|Direitos incluídos (nome comum)|
|----------------|---------------------------------|
|&lt;*nome da organização*&gt; *– Apenas Visualização Confidencial*|Ver, Abrir, Ler|
|&lt;*nome da organização*&gt; *– Confidencial*|Ver, Abrir, Ler; Guardar; Editar Conteúdos, Editar; Ver Direitos; Permitir Macros; Reencaminhar; Responder; Responder a Todos|

## Consulte Também
[Configurar modelos personalizados para o Azure Rights Management](configure-custom-templates.md)



<!--HONumber=Apr16_HO4-->


