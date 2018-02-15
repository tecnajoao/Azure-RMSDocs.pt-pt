---
title: "Configurar as definições de política do Azure Information Protection"
description: "Configurar as definições na política do Azure Information Protection aplicáveis a todos os utilizadores e a todos os dispositivos."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: be050f7307a83dcb229cf7a71fcf7bb5d2ec1380
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Como configurar as definições de política do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Para além de título da barra de Information Protection e a descrição, existem algumas definições da política do Azure Information Protection que pode configurar independentemente de etiquetas:

![Definições globais da política do Azure Information Protection](../media/info-protect-policy-default-settingsv3.png)

Tenha em atenção que as definições de política podem ter valores predefinido diferente, dependendo se comprou a sua subscrição do Azure Information Protection. Algumas definições também podem ser definidas uma [definição de cliente personalizada](../rms-client/client-admin-guide-customizations.md).

Configurar estas definições:

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no menu hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se as definições que pretende configurar serão aplicada a todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel.
    
    Se as definições que pretende configurar estão disponíveis num [âmbito política](configure-policy-scope.md) para que se apliquem a utilizadores selecionados apenas, do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

3. Do **Azure Information Protection - política Global** painel, ou o **política:\<nome >** painel, configure as definições:
    
    - **Selecione a etiqueta predefinida**: quando definir esta opção, selecione a etiqueta para atribuir a documentos e e-mails que não tenham uma etiqueta. Não é possível definir uma etiqueta como predefinição se tiver etiquetas secundárias. 
    
    - **Todos os documentos e e-mails devem ter uma etiqueta**: quando configurar esta opção como **Ativado**, todos os todos os documentos guardado e e-mails enviados devem ter uma etiqueta aplicada. As etiquetas podem ser atribuídas manualmente por um utilizador, automaticamente como resultado de uma [Condição](configure-policy-classification.md) ou pode ser atribuída por predefinição (definindo opção **Selecionar etiqueta predefinida**).
        
        Se uma etiqueta não estiver atribuída quando os utilizadores guardar um documento ou envia uma mensagem de e-mail, são-lhe pedidos para selecionar uma etiqueta. Por exemplo:
        
        ![Aviso do Azure Information Protection se a etiqueta for imposta](../media/info-protect-enforce-labelv2.png)
        
    - **Os utilizadores têm de fornecer uma justificação para reduzir a segurança da etiqueta de classificação, remover uma etiqueta ou remover a proteção**: quando define esta opção como **Ativado** e um utilizador realiza uma destas ações (como alterar a etiqueta **Público** para **Pessoal**), é-lhe pedido que forneça uma explicação para esta ação. Por exemplo, o utilizador pode explicar que o documento já não contém informações confidenciais. A ação e o motivo de justificação são registadas no respetivo registo de eventos do Windows local: **registos de serviços e aplicações** > **Azure Information Protection**.  
        
        ![Aviso do Azure Information Protection se a nova classificação for inferior](../media/info-protect-lower-justification.png)
        
        Esta opção não é aplicável a etiquetas secundárias.
        
    - **Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos**: quando define esta opção como **Recomendado**, é pedido aos utilizadores que apliquem uma etiqueta à respetiva mensagem de e-mail. A etiqueta é selecionada de forma dinâmica com base nas etiquetas de classificação aplicadas aos anexos e é selecionada a etiqueta de classificação mais elevada. O anexo tem de ser um ficheiro físico e não pode ser uma ligação a um ficheiro (por exemplo, uma ligação a um ficheiro no SharePoint ou no OneDrive para Empresas). Os utilizadores podem aceitar a recomendação ou ignorá-la. Quando define esta opção como **Ativado**, a etiqueta é automaticamente aplicada mas os utilizadores podem removê-la ou selecionar uma etiqueta diferente antes de enviarem o e-mail.  
    
    - **Apresentar a barra do Information Protection em aplicações do Office**: quando esta definição estiver desativada, os utilizadores não é possível selecionar etiquetas de uma barra no Word, Excel, PowerPoint e Outlook. Em vez disso, os utilizadores devem selecionar etiquetas do **proteger** botão no Friso. Quando esta definição está ativada, os utilizadores podem selecionar etiquetas da barra de ou no botão.
        
        > [!IMPORTANT]
        > Esta definição está em pré-visualização e requer a versão de pré-visualização atual do cliente Azure Information Protection.
        
        Quando esta definição está ativada, esta pode ser utilizada em conjunto com um cliente avançado definição para que os utilizadores podem [permanentemente ocultar a barra do Azure Information Protection](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar) se escolherem não mostrar a barra. Pode fazê-lo ao desmarcar a **Mostrar barra** opção do **proteger** botão.
    
    - **Adicionar o botão não reencaminhar para o Friso Outlook**: quando esta definição está ativada, os utilizadores podem selecionar este botão do **proteção** grupo no Friso Outlook, além de selecionar o **não reencaminhar** opção de menus do Outlook. Para ajudar a garantir que os utilizadores classificar os e-mails, bem como proteger, poderá preferir não, mas em vez disso, a adicionar este botão [configurar uma etiqueta para a proteção](configure-policy-protection.md) e um utilizador definido permissão para o Outlook. Esta definição de proteção é funcionalmente o mesmo como selecionar o **não reencaminhar** botão, mas quando esta funcionalidade está incluída com uma etiqueta, os e-mails são classificados, bem como protegidos.
    
        Esta definição de política também pode ser configurada com um cliente avançado definir como um [personalização de cliente](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook).
    
    - **Tornar disponível a opção de permissões personalizadas aos utilizadores**: quando esta definição está ativada, os utilizadores podem configurar as suas próprias definições de proteção e substituir as definições de proteção que tiver incluído com uma configuração de etiqueta. Quando esta definição estiver desativada, as opções de permissões personalizadas não estão disponíveis para os utilizadores selecionem o.
        
        > [!IMPORTANT]
        > A menos que utilize a versão de pré-visualização atual do cliente, não utilize o **desativar** definição se tiver etiquetas que estão configuradas para o utilizador definido permissões para Word, Excel, PowerPoint e Explorador de ficheiros. Se o fizer, quando a etiqueta é aplicada, os utilizadores não recebem um pedido para configurar as permissões personalizadas. O resultado é que o documento tem o nome, mas não está protegido como esperados.
        
        Tenha em atenção que esta definição de política não tem efeito em permissões personalizadas que os utilizadores podem configurar a partir das opções de menu do Office. No entanto, também pode ser configurado com um cliente avançado definir como um [personalização de cliente](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users).
        
        As opções de permissões personalizadas estão localizadas nos seguintes locais:
        
        - Nas aplicações do Office: a partir do Friso, **home page** separador > **proteção** grupo > **proteger** > **permissões personalizadas**
        
        - No Explorador de Ficheiros: clique com o botão direito do rato > **Classificar e proteger** > **Permissões personalizadas**
    
    - **Forneça um URL personalizado para o cliente Azure Information Protection "Informar-me mais" página da web**: os utilizadores veem esta ligação no **Microsoft Azure Information Protection** caixa de diálogo, **ajuda e comentários**secção, quando estes selecionam **proteger** > **ajuda e comentários** do **home page** separador nas aplicações do Office. Por predefinição, esta ligação direciona-o para o site do [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection). Pode introduzir um URL do tipo HTTP ou HTTPS (recomendado) se quiser que esta ligação redirecione o utilizador para uma página Web alternativa. Não é efetuada nenhuma verificação para confirmar que o URL personalizado que introduziu é acessível ou é apresentado corretamente em todos os dispositivos.
        
        Por exemplo, para suporte técnico, pode introduzir a página de documentação da Microsoft que inclui informações acerca da instalação e da utilização do cliente (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) ou informações relativas à versão de lançamento (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Em alternativa, poderá publicar a sua própria página Web com informações para que os utilizadores contactem o seu suporte técnico ou um vídeo com passos para que os utilizadores saibam como utilizar as etiquetas que configurou.

3. Para guardar as alterações, clique em **Guardar**.

4. Para disponibilizar as alterações aos utilizadores, no painel inicial **Azure Information Protection**, clique em **Publicar**.

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
