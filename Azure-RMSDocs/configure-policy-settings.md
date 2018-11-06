---
title: Configurar as definições de política do Azure Information Protection
description: Configurar as definições na política do Azure Information Protection aplicáveis a todos os utilizadores e a todos os dispositivos.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: f8967b16f864939bfcb06f786e8ee1eff0603ac2
ms.sourcegitcommit: 80de8762953bdea2553c48b02259cd107d0c71dd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51026609"
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Como configurar as definições de política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Além do título da barra de Information Protection e a descrição, existem algumas definições na política do Azure Information Protection que pode configurar independentemente das etiquetas:

![Definições globais da política do Azure Information Protection](./media/info-protect-policy-default-settingsv3.png)

Tenha em atenção que as definições de política podem ter valores padrão diferente, dependendo de quando tiver adquirido sua assinatura do Azure Information Protection. Algumas definições que também podem ser definidas um [definição de cliente personalizada](./rms-client/client-admin-guide-customizations.md).

Configurar estas definições:

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **políticas** opção de menu: no **do Azure Information Protection - políticas** painel, selecione **Global** se as definições que pretende configurar se aplicar a todos os utilizadores.
    
    Se as definições que pretende configurar estão num [política de âmbito](configure-policy-scope.md) para que eles se aplicam apenas a utilizadores selecionados, selecione a política de âmbito.

3. Sobre o **política** painel, configure as definições:
    
    - **Selecione a etiqueta predefinida**: quando definir esta opção, selecione a etiqueta para atribuir a documentos e e-mails que não tenham uma etiqueta. Não é possível definir uma etiqueta como predefinição se tiver subetiquetas. 
    
    - **Todos os documentos e e-mails devem ter uma etiqueta**: quando configurar esta opção como **Ativado**, todos os todos os documentos guardado e e-mails enviados devem ter uma etiqueta aplicada. As etiquetas podem ser atribuídas manualmente por um utilizador, automaticamente como resultado de uma [Condição](configure-policy-classification.md) ou pode ser atribuída por predefinição (definindo opção **Selecionar etiqueta predefinida**).
        
        Se uma etiqueta não estiver atribuída quando os utilizadores guardar um documento ou enviar um e-mail, é-lhes pedido para selecionar uma etiqueta. Por exemplo:
        
        ![Aviso do Azure Information Protection se a etiqueta for imposta](./media/info-protect-enforce-labelv2.png)
        
        Esta opção não se aplica quando remover uma etiqueta com o [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) cmdlet do PowerShell com o *RemoveLabel* parâmetro.
        
    - **Os utilizadores têm de fornecer uma justificação para reduzir a segurança da etiqueta de classificação, remover uma etiqueta ou remover a proteção**: quando define esta opção como **Ativado** e um utilizador realiza uma destas ações (como alterar a etiqueta **Público** para **Pessoal**), é-lhe pedido que forneça uma explicação para esta ação. Por exemplo, o utilizador pode explicar que o documento já não contém informações confidenciais. A ação e a justificação são registadas no registo de eventos Windows local: **Applications and Services Logs** > **do Azure Information Protection**.  
        
        ![Aviso do Azure Information Protection se a nova classificação for inferior](./media/info-protect-lower-justification.png)
        
        Esta opção não é aplicável para reduzir a classificação de subetiquetas sob o mesmo rótulo de principal.
        
    - **Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos**: quando define esta opção como **Recomendado**, é pedido aos utilizadores que apliquem uma etiqueta à respetiva mensagem de e-mail. A etiqueta é selecionada de forma dinâmica com base nas etiquetas de classificação aplicadas aos anexos e é selecionada a etiqueta de classificação mais elevada. O anexo tem de ser um ficheiro físico e não pode ser uma ligação a um ficheiro (por exemplo, uma ligação a um ficheiro no SharePoint ou no OneDrive para Empresas). Os utilizadores podem aceitar a recomendação ou ignorá-la. Quando define esta opção como **automática**, a etiqueta é aplicada automaticamente, mas os utilizadores podem remover a etiqueta ou selecione uma etiqueta diferente antes de enviar o e-mail.  
    
    - **Apresentar a barra de Information Protection nas aplicações do Office**: quando esta definição estiver desativada, os utilizadores não é possível selecionar etiquetas de uma barra no Word, Excel, PowerPoint e Outlook. Em vez disso, os utilizadores devem selecionar etiquetas a partir da **Protect** botão na faixa de opções. Quando esta definição está ativado, os utilizadores podem selecionar etiquetas a partir da barra ou no botão.
        
        Quando esta definição está ativado, ele pode ser utilizado em conjunto com um definição para que os utilizadores podem de cliente avançado [ocultar permanentemente a barra do Azure Information Protection](./rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar) se optarem por não mostrar a barra. Pode fazê-lo ao desmarcar a **Mostrar barra** opção da **proteger** botão.
    
    - **Adicionar o botão não reencaminhar ao Friso do Outlook**: quando esta definição está ativado, os utilizadores podem selecionar esse botão a partir de **proteção** grupo no Friso do Outlook, além de selecionar o **não reencaminhar** opção a partir dos menus do Outlook. Para ajudar a garantir que os utilizadores classificar seus emails, bem como protegê-los, não adicione este botão, mas em vez disso, pode preferir [configurar uma etiqueta para proteção](configure-policy-protection.md) e um utilizador definida permissão para o Outlook. Esta definição de proteção é funcionalmente o mesmo como selecionar o **não reencaminhar** botão, mas quando esta funcionalidade está incluída com uma etiqueta, mensagens de correio eletrónico são classificadas como protegidas.
    
        Esta definição de política também pode ser configurada com um cliente avançado definir como um [personalização de cliente](./rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook).
    
    - **Disponibilizar a opção de permissões personalizadas aos utilizadores**: quando esta definição está ativado, os utilizadores veem as opções para definir suas próprias definições de proteção que podem substituir as definições de proteção que possa ter incluído com uma configuração de etiqueta. Os utilizadores também podem ver uma opção para remover a proteção. Quando esta definição estiver desativada, os utilizadores não vir estas opções.
        
        Tenha em atenção que esta definição de política não tem qualquer efeito nas permissões personalizadas que os utilizadores podem configurar a partir das opções de menu do Office. No entanto, também pode ser configurado com um cliente avançado definir como um [personalização de cliente](./rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users).
        
        As opções de permissões personalizadas estão localizadas nos seguintes locais:
        
        - Em aplicativos do Office: a partir do friso **home page** separador > **proteção** grupo > **proteger** > **permissões personalizadas**
        
        - No Explorador de Ficheiros: clique com o botão direito do rato > **Classificar e proteger** > **Permissões personalizadas**
    
    - **Fornecer um URL personalizado para o cliente do Azure Information Protection "Mais informações" a página da web**: os utilizadores veem esta ligação no **Microsoft Azure Information Protection** caixa de diálogo, **ajuda e Feedback**seção, quando estes selecionarem **proteger** > **ajuda e feedback** do **base** separador nas aplicações do Office. Por predefinição, esta ligação direciona-o para o site do [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection). Pode introduzir um URL do tipo HTTP ou HTTPS (recomendado) se quiser que esta ligação redirecione o utilizador para uma página Web alternativa. Não é efetuada nenhuma verificação para confirmar que o URL personalizado que introduziu é acessível ou é apresentado corretamente em todos os dispositivos.
        
        Por exemplo, para o suporte técnico, poderá introduzir a página de documentação da Microsoft que inclui informações sobre como instalar e utilizar o cliente (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) ou informações sobre a versão de lançamento (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Em alternativa, poderá publicar a sua própria página Web com informações para que os utilizadores contactem o seu suporte técnico ou um vídeo com passos para que os utilizadores saibam como utilizar as etiquetas que configurou.

3. Para guardar as alterações e disponibilizá-los aos utilizadores, clique em **guardar**.

Quando clica em **guardar**, as suas alterações estão automaticamente disponíveis para utilizadores e serviços. Já não existe uma opção de publicar separado.

## <a name="next-steps"></a>Passos Seguintes

Para ver como algumas destas definições de política podem trabalhar em conjunto, experimente o [definições de política de configurar o Azure Information Protection que funcionam em conjunto](infoprotect-settings-tutorial.md) tutorial.

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).

