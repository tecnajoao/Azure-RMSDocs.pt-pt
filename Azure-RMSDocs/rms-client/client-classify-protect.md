---
title: Classificar e proteger ficheiros e e-mails ao utilizar o Azure Information Protection
description: Instruções sobre como classificar e proteger os seus documentos e e-mails.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 01/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: f8ad7f4e9243e7f6b2be306681ba11d18cc9394b
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56253957"
---
# <a name="user-guide-classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Guia de utilizador: Classificar e proteger um ficheiro ou e-mail com o Azure Information Protection

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

> [!NOTE]
> Utilize estas instruções para o ajudar a classificar e proteger os seus documentos e e-mails. Se precisar apenas para classificar e proteger os seus documentos e e-mails não, consulte a [instruções de só de classificar](client-classify.md). Se não tiver a certeza de qual conjunto de instruções para utilizar, contacte o administrador ou suporte técnico.

A forma mais fácil de classificar e proteger os seus documentos e e-mails é durante a criação ou edição dos mesmos nas suas aplicações de ambiente de trabalho do Office: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

No entanto, também pode classificar e proteger ficheiros ao utilizar **Explorador de ficheiros**. Este método suporta tipos de ficheiro adicionais e é uma maneira conveniente de classificar e proteger vários ficheiros ao mesmo tempo. Este método suporta proteger documentos do Office, ficheiros PDF, ficheiros de texto e imagem e uma vasta gama de outros ficheiros. 

Se a etiqueta aplicar proteção a um documento, o documento protegido não é adequado para serem salvos no SharePoint ou o OneDrive. Estas localizações não suportam o seguinte procedimento para ficheiros protegidos: Coautoria, Office Online, pesquisa, pré-visualização do documento, miniatura e deteção de dados eletrónicos. 

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>Partilhar um ficheiro de forma segura com pessoas fora da sua organização

Os ficheiros que estão protegidos são seguros para serem partilhados com outras pessoas. Por exemplo, anexe um documento protegido, a um e-mail.

Antes de partilhar ficheiros com pessoas fora da sua organização, contacte o suporte técnico ou o administrador como proteger ficheiros para utilizadores externos.

Por exemplo, se sua organização comunica regularmente com pessoas noutra organização, o administrador poderá ter configurado as etiquetas que define a proteção, de modo a que estas pessoas podem ler e utilizar documentos protegidos. Em seguida, selecione estas etiquetas para classificar e proteger os documentos para partilhar.

Em alternativa, se tiverem dos utilizadores externos [contas de empresa-empresa (B2B)](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) criado para eles, pode usar sua [aplicação do Office para definir permissões personalizadas](#set-custom-permissions-for-a-document) ou utilize [Explorador de ficheiros para definir permissões personalizadas](#using-file-explorer-to-classify-and-protect-files) para um documento antes de o partilhar. Se definir suas próprias permissões personalizadas e o documento já está protegido para utilização interna, primeiro, faça uma cópia do mesmo para manter as permissões originais. Em seguida, utilize a cópia para definir as permissões personalizadas.


## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Utilizar aplicações do Office para classificar e proteger os seus documentos e e-mails

Utilize a barra do Azure Information Protection ou o **Protect** botão da faixa de opções para selecionar uma das etiquetas que tenha sido configurada por si. 

Por exemplo, a imagem seguinte mostra que o documento ainda não foi etiquetado porque o **sensibilidade** mostra **nenastaveno** na barra do Azure Information Protection. Para definir uma etiqueta, tal como "Geral", clique em **gerais**. Se não estiver certo sobre que etiqueta aplicar ao e-mail ou documento atual, utilize as descrições de etiquetas para saber mais sobre cada etiqueta e quando a aplicar. 

![Exemplo de barra do Azure Information Protection](../media/info-protect-bar-not-set-callout.png)

Se uma etiqueta já estiver aplicada ao documento e pretender alterá-la, poderá selecionar uma diferente. Se as etiquetas não forem apresentadas na barra, clique primeiro no ícone **Editar Etiqueta**, junto ao valor da etiqueta atual.

Além de selecionar etiquetas manualmente, as etiquetas também podem ser aplicadas das seguintes formas:

- O administrador configurou uma etiqueta predefinida, que pode manter ou alterar.

- O administrador configurou pedidos recomendados para selecionar uma etiqueta específica quando são detetados dados confidenciais. Pode aceitar a recomendação (e a etiqueta é aplicada) ou rejeitá-la (não é aplicada a etiqueta recomendada).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Exceções para a barra do Azure Information Protection 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Não vê esta barra do Information Protection nas suas aplicações do Office?

Motivos possíveis:

- Não tem o cliente do Azure Information Protection [instalado](install-client-app.md).

- Ter o cliente instalado, mas o administrador tiver configurado uma definição que não exibe a barra. Em vez disso, selecione as etiquetas do **proteger** no botão, o **ficheiro** separador do Friso do Office. 

- O cliente está em execução [modo apenas de proteção](client-protection-only-mode.md).
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed"></a>É a etiqueta que pretende ver não apresentada? 

Motivos possíveis:

- Se o administrador tiver configurado recentemente uma nova etiqueta para si, experimente fechar todas as instâncias da sua aplicação do Office e voltar a abrir-la. Esta ação verifica se as suas etiquetas sofreram alguma alteração.

- Se a etiqueta em falta aplicar proteção, poderá ter uma edição do Office que não suporta a aplicação da proteção Rights Management. Para verificar, clique em **Protect** > **ajuda e Feedback**. Na caixa de diálogo, verifique se tem uma mensagem na **estado do cliente** secção que diz **este cliente não está licenciado para o Office Professional Plus.** 
    
    Não é necessário Office Professional Plus se tiver aplicações do Office do Microsoft 365 empresas ou do Office 365 empresas quando o utilizador tem atribuída uma licença do Azure Rights Management (também conhecido como Azure Information Protection para o Office 365).

- A etiqueta pode estar numa política de âmbito que não inclui a sua conta. Contacte o suporte técnico ou o administrador.

### <a name="set-custom-permissions-for-a-document"></a>Definir permissões personalizadas num documento

Se permitido pelo seu administrador, pode especificar as suas próprias definições de proteção para documentos em vez de utilizar as definições de proteção que o administrador possa ter incluído com a etiqueta escolhida. Esta opção é específica para documentos e não está disponível com o Outlook.

1. No separador **Base**, no grupo **Proteção**, clique em **Proteger** > **Permissões Personalizadas**:

    ![Opção Permissões Personalizadas](../media/custom-permissions-callout.png)
    
    Se não vir **permissões personalizadas**, o administrador não permite que utilize esta opção.
    
    Tenha em atenção que todas as permissões personalizadas que especificar substituem as definições de proteção que o administrador possa ter definido para a etiqueta escolhida em vez de as complementarem.  

2. Na caixa de diálogo **Microsoft Azure Information Protection**, especifique o seguinte:

    - **Proteger com permissões personalizadas**: Certifique-se de que esta opção está selecionada para que possa especificar e aplicar as suas permissões personalizadas. Desmarque esta opção para remover quaisquer permissões personalizadas.
    
    - **Selecionar permissões**: Se pretender proteger o ficheiro para que só pode acessá-lo, selecione **apenas para mim**. Caso contrário, selecione o nível de acesso que pretende que as pessoas tenham.
    
    - **Selecionar utilizadores, grupos ou organizações**: Especifique as pessoas que devem ter as permissões que selecionou para o ficheiro ou ficheiros. Escreva o endereço de e-mail completo dessas pessoas, um endereço de e-mail de grupo ou um nome de domínio da organização para todos os utilizadores nessa organização. 
        
        Também pode utilizar o ícone de livro de endereços para selecionar utilizadores ou grupos do livro de endereços do Outlook.
    
    - **Expirar acesso**: Selecione esta opção apenas para ficheiros sensíveis ao tempo para que as pessoas que especificou não poderão abrir o ficheiro ou ficheiros selecionados após uma data que definir. Ainda poderá abrir o ficheiro original, mas após a meia-noite (seu fuso horário atual), no dia em que definir, as pessoas que especificou não poderão abrir o ficheiro.

5. Clique em **Aplicar** e espere pela mensagem **Permissões personalizadas aplicadas**. Em seguida, clique em **Fechar**.

### <a name="safely-sharing-by-email"></a>Compartilhando com segurança por e-mail

Ao partilhar documentos do Office por e-mail, pode anexar o documento a uma mensagem de e-mail que protege, e o documento está protegido automaticamente com as mesmas restrições que se aplicam à mensagem de e-mail. 

No entanto, recomendamos que primeiro a proteger o documento e, em seguida, anexá-lo para o e-mail. Proteger o e-mail também se a mensagem de e-mail contiver informações confidenciais. Dois benefícios de proteger o documento, antes que o anexa a um e-mail:

- Pode controlar e se for necessário, revogar o documento depois que tenha enviado por e-mail-lo.

- Pode aplicar permissões diferentes para o documento que a mensagem de e-mail.

## <a name="using-file-explorer-to-classify-and-protect-files"></a>Utilizar o Explorador de Ficheiros para classificar e proteger ficheiros

Quando utiliza o Explorador de Ficheiros, pode rapidamente classificar e proteger um ficheiro único, vários ficheiros ou uma pasta. 

Quando seleciona uma pasta, todos os ficheiros nessa pasta e eventuais subpastas são automaticamente selecionados para as opções de proteção e classificação que definiu. No entanto, os novos ficheiros que criar nessa pasta ou subpastas não são configurados automaticamente com essas opções.

Quando utiliza o Explorador de Ficheiros para classificar e proteger os ficheiros, se uma ou mais etiquetas aparecerem escurecidas, os ficheiros que selecionou não suportará a classificação. No caso desses ficheiros, poderá selecionar uma etiqueta apenas se o administrador tiver configurado a etiqueta para aplicar proteção. Em alternativa, pode especificar as suas próprias definições de proteção. 

Alguns ficheiros são automaticamente excluídos da classificação e da proteção, uma vez que alterá-los poderá interromper a execução do PC. Embora possa selecionar estes ficheiros, eles são ignorados como uma pasta ou ficheiro excluídos. Alguns exemplos incluem ficheiros executáveis e a pasta do Windows.

Guia do administrador contém uma lista completa dos tipos de ficheiro suportados e os ficheiros e pastas que são automaticamente excluídas: [Tipos de ficheiro suportados pelo cliente do Azure Information Protection](client-admin-guide-file-types.md).


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>Para classificar e proteger ficheiros com o Explorador de Ficheiros

1. No Explorador de Ficheiros, selecione o ficheiro, vários ficheiros ou uma pasta. Clique com o botão direito do rato e selecione **Classificar e proteger**. Por exemplo:
    
    ![No Explorador de Ficheiros, clique com o botão direito do rato em Classificar e proteger ao utilizar o Azure Information Protection](../media/right-click-classify-protect-folder.png)

2. Na caixa de diálogo **Classificar e proteger – Azure Information Protection**, utilize as etiquetas como faria numa aplicação do Office, o que define a classificação e a proteção, conforme definido pelo seu administrador. 

   - Se nenhuma das etiquetas pode ser selecionada (aparecem escurecidas): O ficheiro selecionado não suportará a classificação, mas poderá protegê-lo com permissões personalizadas (etapa 3). Por exemplo:

     ![Não há etiquetas disponíveis na caixa de diálogo Classificar e proteger – Azure Information Protection**](../media/info-protect-dialog-labels-dimmed.png)
    
   - Se não vir etiquetas, mas uma opção para **proteção predefinida da empresa** nessa caixa de diálogo: O cliente está em execução [modo apenas de proteção](client-protection-only-mode.md). Selecione um modelo para aplicar a proteção que o administrador tiver configurado para si ou selecione **Permissões personalizadas** para especificar as suas próprias definições de proteção e avance para o passo 4.
    
     ![Não há etiquetas na caixa de diálogo Classificar e proteger – Azure Information Protection**](../media/info-protect-dialog-labels-protection-only.png)
    
3. Se permitido pelo seu administrador, pode especificar as suas próprias definições de proteção em vez de utilizar as definições de proteção que o administrador possa ter incluído com a etiqueta escolhida. Para tal, selecione **proteger com permissões personalizadas**.
    
    Se não vir **proteger com permissões personalizadas**, o administrador não permite que utilize esta opção.
    
    Todas as permissões personalizadas que especificar substituem as definições de proteção que o administrador possa ter definido para a etiqueta escolhida em vez de as complementarem.  

4. Se selecionar a opção de permissões personalizadas, especifique o seguinte:

   - **Selecionar permissões**: Selecione o nível de acesso que pretende que as pessoas tenham quando protege o ficheiro ou ficheiros selecionados.
    
   - **Selecionar utilizadores, grupos ou organizações**: Especifique as pessoas que devem ter as permissões que selecionou para o ficheiro ou ficheiros. Escreva o endereço de e-mail completo dessas pessoas, um endereço de e-mail de grupo ou um nome de domínio da organização para todos os utilizadores nessa organização. 
    
     Em alternativa, pode utilizar o ícone de livro de endereços para selecionar utilizadores ou grupos do livro de endereços do Outlook.
        
   - **Expirar acesso**: Selecione esta opção apenas para ficheiros sensíveis ao tempo para que as pessoas que especificou não poderão abrir o ficheiro ou ficheiros selecionados após uma data que definir, ainda poderá abrir o ficheiro original, mas após a meia-noite (seu fuso horário atual) , no dia em que definir, as pessoas que especificou não será possível abrir o ficheiro.
    
     Observe que se essa definição foi configurada anteriormente através de permissões personalizadas de uma aplicação do Office 2010, a data de expiração especificada não é apresentada nesta caixa de diálogo, mas continuará definida. Este é um problema de apresentação de quando a data de expiração foi configurada no Office 2010.

5. Clique em **Aplicar** e aguarde pela mensagem **Trabalho concluído** para ver os resultados. Em seguida, clique em **Fechar**.

O ficheiro ou ficheiros selecionados estão agora classificados e protegidos, de acordo com as suas seleções. Em alguns casos (quando a adição de proteção altera a extensão de nome de ficheiro), o ficheiro original no Explorador de Ficheiros é substituído por um novo ficheiro que tem o ícone de cadeado do Azure Information Protection. Por exemplo:

![Ficheiro protegido com o ícone de cadeado do Azure Information Protection](../media/Pfile.png)

Se mudar de ideias sobre a classificação e proteção, ou precisar de modificar as definições posteriormente, repita simplesmente este processo com as suas novas definições.

A classificação e proteção que especificou permanecem com o ficheiro, mesmo que o envie por e-mail ou o guarde noutra localização. Se tiver protegido o ficheiro, pode controlar a forma como as pessoas estão a utilizá-lo e, se necessário, revogar o acesso ao mesmo. Para obter mais informações, veja [Controlar e revogar os documentos protegidos quando utiliza o Azure Information Protection](client-track-revoke.md). 


## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

-   [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Informações adicionais para administradores    
Para obter instruções de configuração ativar a definição de política **disponibilizar a opção de permissões personalizadas para os usuários**, consulte [configurar as definições de política do Azure Information Protection](../configure-policy-settings.md).

Outras instruções de configuração: [Configurar a política do Azure Information Protection](../configure-policy.md).

