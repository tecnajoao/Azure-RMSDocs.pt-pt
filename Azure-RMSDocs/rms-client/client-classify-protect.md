---
title: Classificar e proteger com o Azure Information Protection
description: "Instruções sobre como classificar e proteger os seus documentos e e-mails."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 3db62d81976267155764abf7e45598628259710d
ms.lasthandoff: 02/24/2017


---

# <a name="classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Classificar e proteger um ficheiro ou e-mail com o Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8 e Windows 7 com SP1*

A forma mais fácil de classificar e proteger os seus documentos e e-mails é durante a criação ou edição nas aplicações de ambiente de trabalho do Office: **Word**, **Excel**, **PowerPoint** e **Outlook**. 

No entanto, também pode classificar e proteger ficheiros com o **Explorador de Ficheiros**, que suporta outros tipos de ficheiros e é uma forma conveniente de classificar e proteger vários ficheiros ao mesmo tempo. Este método suporta proteger documentos do Office, ficheiros PDF, ficheiros de texto e imagem e uma vasta gama de outros ficheiros. 

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>Partilhar um ficheiro de forma segura com pessoas fora da sua organização

Os ficheiros que estão protegidos são seguros para serem partilhados com outras pessoas. Por exemplo, anexe o ficheiro a um e-mail ou envie um convite a partir do site do SharePoint.

Se partilha regularmente ficheiros com pessoas fora da sua organização, o administrador poderá ter configurado uma etiqueta para si que define uma proteção que permite que estas pessoas os possam ler. Em alternativa, pode utilizar o [Explorador de Ficheiros para definir permissões personalizadas](#using-file-explorer-to-classify-and-protect-files) para um ficheiro antes de o partilhar. 

Se definiu as suas próprias permissões personalizadas e o ficheiro já está protegido para utilização interna, primeiro faça uma cópia do mesmo. Utilize esta cópia para definir as permissões personalizadas.  

Quando o ficheiro está protegido com as permissões personalizadas, utilize o seu mecanismo de partilha padrão para partilhar o ficheiro. Se esta for a primeira vez que estas pessoas com as quais está a partilhar receberam um ficheiro protegido, poderão precisar de instruções para o visualizar. Para estas pessoas, pode copiar e colar a seguinte mensagem: **Protegi este ficheiro com o Microsoft Azure Information Protection. Para a primeira utilização, veja estas [instruções](https://aka.ms/rms-signup).**


## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Utilizar aplicações do Office para classificar e proteger os seus documentos e e-mails

Utilize a barra do Azure Information Protection e selecione uma das etiquetas que tenha sido configurada para si. 

Por exemplo, a imagem seguinte mostra que o documento ainda não foi etiquetado porque a **Sensibilidade** indica **Não definido**. Para definir uma etiqueta, tal como “Interno”, clique em **Interno**. Se não estiver certo sobre que etiqueta aplicar ao e-mail ou documento atual, utilize as descrições de etiquetas para saber mais sobre cada etiqueta e quando a aplicar.

![Exemplo de barra do Azure Information Protection](../media/info-protect-bar-not-set-callout.png)

Se uma etiqueta já estiver aplicada ao documento e pretender alterá-la, poderá selecionar uma diferente. Se as etiquetas não forem apresentadas na barra, clique primeiro no ícone **Editar Etiqueta**, junto ao valor da etiqueta atual.

Além de selecionar etiquetas manualmente, as etiquetas também podem ser aplicadas das seguintes formas:

- O administrador configurou uma etiqueta predefinida, que pode manter ou alterar.

- O administrador configurou pedidos recomendados para selecionar uma etiqueta específica quando são detetados dados confidenciais. Pode aceitar a recomendação (e a etiqueta é aplicada) ou rejeitá-la (não é aplicada a etiqueta recomendada).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Exceções para a barra do Azure Information Protection 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Não vê esta barra do Information Protection nas suas aplicações do Office?

- Poderá não ter o cliente do Azure Information Protection [instalado](install-client-app.md) ou o cliente está em execução no [modo apenas de proteção](client-protection-only-mode.md).
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>A etiqueta que pretende ver não é apresentada na barra? 

- Se o administrador tiver configurado recentemente uma nova etiqueta para si, experimente fechar todas as instâncias da sua aplicação do Office e voltar a abrir-la. Esta ação verifica se as suas etiquetas sofreram alguma alteração.

- Se a etiqueta em falta aplicar proteção, poderá ter uma edição do Office que não suporta a aplicação da proteção Rights Management. Para verificar, clique em **Proteger** > **Ajuda e comentários** e verifique se tem uma mensagem na secção **Estado do cliente** que diz **Este cliente não está licenciado para o Office Professional Plus.** 

- A etiqueta pode estar numa política de âmbito que não inclui a sua conta. Contacte o suporte técnico ou o administrador.

### <a name="keyboard-shortcuts-for-the-azure-information-protection-bar"></a>Atalhos de teclado da barra Azure Information Protection

Para aceder à barra Azure Information Protection através de atalhos de teclado, utilize a seguinte combinação de teclas:

- Prima **Ctrl** + **Shift** + **~** 

Em seguida, utilize a tecla de Tabulação para selecionar as etiquetas e outros controlos na barra (o ícone **Ocultar Etiquetas** e o ícone **Eliminar Etiqueta**) e a tecla Enter para os selecionar.

## <a name="using-file-explorer-to-classify-and-protect-files"></a>Utilizar o Explorador de Ficheiros para classificar e proteger ficheiros

Quando utiliza o Explorador de Ficheiros, pode rapidamente classificar e proteger um ficheiro único, vários ficheiros ou uma pasta. 

Quando seleciona uma pasta, todos os ficheiros nessa pasta e eventuais subpastas são automaticamente selecionados para as opções de proteção e classificação que definiu. No entanto, os novos ficheiros que criar nessa pasta ou subpastas não são configurados automaticamente com essas opções.

Quando utiliza o Explorador de Ficheiros para classificar e proteger os ficheiros, se uma ou mais etiquetas aparecerem escurecidas, os ficheiros que selecionou não suportará a classificação. No caso desses ficheiros, poderá selecionar uma etiqueta apenas se o administrador tiver configurado a etiqueta para aplicar proteção. Em alternativa, pode especificar as suas próprias definições de proteção. 

Alguns ficheiros são automaticamente excluídos da classificação e da proteção, uma vez que alterá-los poderá interromper a execução do PC. Embora possa selecionar estes ficheiros, eles são ignorados como uma pasta ou ficheiro excluídos. Alguns exemplos incluem ficheiros executáveis e a pasta do Windows.

O guia do administrador contém uma lista completa dos tipos de ficheiro suportados e os ficheiros e pastas que estão automaticamente excluídos: [Tipos de ficheiro suportados pelo cliente do Azure Information Protection](client-admin-guide-file-types.md).


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>Para classificar e proteger ficheiros com o Explorador de Ficheiros

1. No Explorador de Ficheiros, selecione o ficheiro, vários ficheiros ou uma pasta. Clique com o botão direito do rato e selecione **Classificar e proteger**. Por exemplo:
    
    ![No Explorador de Ficheiros, clique com o botão direito do rato em Classificar e proteger ao utilizar o Azure Information Protection](../media/right-click-classify-protect-folder.png)

2. Na caixa de diálogo **Classificar e proteger – Azure Information Protection**, utilize as etiquetas como faria numa aplicação do Office, o que define a classificação e a proteção, conforme definido pelo seu administrador. 

    - Se nenhuma das etiquetas puder ser selecionada (aparecem escurecidas): o ficheiro selecionado não suportará a classificação, mas poderá protegê-lo com permissões personalizadas (passo 3). Por exemplo:

    ![Não há etiquetas disponíveis na caixa de diálogo Classificar e proteger – Azure Information Protection**](../media/info-protect-dialog-labels-dimmed.png)
    
    - Se não vir etiquetas, mas vir uma opção para a **Proteção predefinida da empresa** nesta caixa de diálogo: o cliente está em execução no [modo apenas de proteção](client-protection-only-mode.md). Selecione um modelo para aplicar a proteção que o administrador tiver configurado para si ou selecione **Permissões personalizadas** para especificar as suas próprias definições de proteção e avance para o passo 4.
    
    ![Não há etiquetas na caixa de diálogo Classificar e proteger – Azure Information Protection**](../media/info-protect-dialog-labels-protection-only.png)
    
3. Se quiser especificar as suas próprias definições de proteção em vez de utilizar as definições de proteção que o administrador possa ter incluído com a etiqueta escolhida, selecione **Proteger com permissões personalizadas**.
    
    Todas as permissões personalizadas que especificar substituem as definições de proteção que o administrador possa ter definido para a etiqueta escolhida em vez de as complementarem.  

4. Se selecionar a opção de permissões personalizadas, especifique o seguinte:

    - **Selecionar permissões**: selecione o nível de acesso que pretende que as pessoas tenham quando protege o ficheiro ou ficheiros selecionados.
    
    - **Selecionar utilizadores**: especifique as pessoas que devem ter as permissões que selecionou para o seu ficheiro ou ficheiros. Pode utilizar o livro de endereços para pesquisar e selecionar as pessoas e os grupos na sua organização. Para pessoas noutra organização, tem de especificar o endereço de e-mail completo. Verifique que utiliza um endereço de e-mail profissional, uma vez que os endereços de e-mail pessoais não são atualmente suportados.
        
    - **Expirar acesso**: selecione esta opção apenas para ficheiros sensíveis ao tempo para que as pessoas que especificou não consigam abrir o ficheiro ou ficheiros selecionados após uma data especificada. Ainda poderá abrir o ficheiro original, mas, após a meia-noite (o seu fuso horário atual), no dia que selecionou, as pessoas especificadas não poderão abrir o ficheiro.

5. Clique em **Aplicar** e aguarde pela mensagem **Trabalho concluído** para ver os resultados. Em seguida, clique em **Fechar**.

O ficheiro ou ficheiros selecionados estão agora classificados e protegidos, de acordo com as suas seleções. Em alguns casos (quando a adição de proteção altera a extensão de nome de ficheiro), o ficheiro original no Explorador de Ficheiros é substituído por um novo ficheiro que tem o ícone de cadeado do Azure Information Protection. Por exemplo:

![Ficheiro protegido com o ícone de cadeado do Azure Information Protection](../media/Pfile.png)

Se mudar de ideias sobre a classificação e proteção, ou precisar de modificar as definições posteriormente, repita simplesmente este processo com as suas novas definições.

A classificação e proteção que especificou permanecem com o ficheiro, mesmo que o envie por e-mail ou o guarde noutra localização. Se tiver protegido o ficheiro, pode controlar a forma como as pessoas estão a utilizá-lo e, se necessário, revogar o acesso ao mesmo. Para obter mais informações, veja [Controlar e revogar os documentos protegidos quando utiliza o Azure Information Protection](client-track-revoke.md). 


## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

-   [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

