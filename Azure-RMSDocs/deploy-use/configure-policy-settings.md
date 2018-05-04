---
title: Configurar as definições de política do Azure Information Protection
description: Configurar as definições na política do Azure Information Protection aplicáveis a todos os utilizadores e a todos os dispositivos.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: cfdb1537ad5444ef478c18380b535f38b5f7c667
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Como configurar as definições de política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Para além de título da barra de Information Protection e a descrição, existem algumas definições da política do Azure Information Protection que pode configurar independentemente de etiquetas:

![Definições globais da política do Azure Information Protection](../media/info-protect-policy-default-settingsv3.png)

Tenha em atenção que as definições de política podem ter valores predefinido diferente, dependendo se comprou a sua subscrição do Azure Information Protection. Algumas definições também podem ser definidas uma [definição de cliente personalizada](../rms-client/client-admin-guide-customizations.md).

Configurar estas definições:

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **políticas** opção do menu: no **Azure Information Protection - políticas** painel, selecione **Global** se as definições que pretende configurar serão aplicada a todos os utilizadores.
    
    Se as definições que pretende configurar estão disponíveis num [âmbito política](configure-policy-scope.md) para que estas são aplicadas apenas a utilizadores selecionados, selecione a política de âmbito em vez disso.

3. No **política** painel, configure as definições:
    
    - **Selecione a etiqueta predefinida**: quando definir esta opção, selecione a etiqueta para atribuir a documentos e e-mails que não tenham uma etiqueta. Não é possível definir uma etiqueta como predefinição se tiver etiquetas secundárias. 
    
    - **Todos os documentos e e-mails devem ter uma etiqueta**: quando configurar esta opção como **Ativado**, todos os todos os documentos guardado e e-mails enviados devem ter uma etiqueta aplicada. As etiquetas podem ser atribuídas manualmente por um utilizador, automaticamente como resultado de uma [Condição](configure-policy-classification.md) ou pode ser atribuída por predefinição (definindo opção **Selecionar etiqueta predefinida**).
        
        Se uma etiqueta não estiver atribuída quando os utilizadores guardar um documento ou envia uma mensagem de e-mail, são-lhe pedidos para selecionar uma etiqueta. Por exemplo:
        
        ![Aviso do Azure Information Protection se a etiqueta for imposta](../media/info-protect-enforce-labelv2.png)
        
    - **Os utilizadores têm de fornecer uma justificação para reduzir a segurança da etiqueta de classificação, remover uma etiqueta ou remover a proteção**: quando define esta opção como **Ativado** e um utilizador realiza uma destas ações (como alterar a etiqueta **Público** para **Pessoal**), é-lhe pedido que forneça uma explicação para esta ação. Por exemplo, o utilizador pode explicar que o documento já não contém informações confidenciais. A ação e o motivo de justificação são registadas no respetivo registo de eventos do Windows local: **registos de serviços e aplicações** > **Azure Information Protection**.  
        
        ![Aviso do Azure Information Protection se a nova classificação for inferior](../media/info-protect-lower-justification.png)
        
        Esta opção não é aplicável para sublabels.
        
    - **Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos**: quando define esta opção como **Recomendado**, é pedido aos utilizadores que apliquem uma etiqueta à respetiva mensagem de e-mail. A etiqueta é selecionada de forma dinâmica com base nas etiquetas de classificação aplicadas aos anexos e é selecionada a etiqueta de classificação mais elevada. O anexo tem de ser um ficheiro físico e não pode ser uma ligação a um ficheiro (por exemplo, uma ligação a um ficheiro no SharePoint ou no OneDrive para Empresas). Os utilizadores podem aceitar a recomendação ou ignorá-la. Quando define esta opção como **Ativado**, a etiqueta é automaticamente aplicada mas os utilizadores podem removê-la ou selecionar uma etiqueta diferente antes de enviarem o e-mail.  
    
    - **Apresentar a barra do Information Protection em aplicações do Office**: quando esta definição estiver desativada, os utilizadores não é possível selecionar etiquetas de uma barra no Word, Excel, PowerPoint e Outlook. Em vez disso, os utilizadores devem selecionar etiquetas do **proteger** botão no Friso. Quando esta definição está ativada, os utilizadores podem selecionar etiquetas da barra de ou no botão.
        
        Quando esta definição está ativada, esta pode ser utilizada em conjunto com um cliente avançado definição para que os utilizadores podem [permanentemente ocultar a barra do Azure Information Protection](../rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar) se escolherem não mostrar a barra. Pode fazê-lo ao desmarcar a **Mostrar barra** opção do **proteger** botão.
    
    - **Adicionar o botão não reencaminhar para o Friso Outlook**: quando esta definição está ativada, os utilizadores podem selecionar este botão do **proteção** grupo no Friso Outlook, além de selecionar o **não reencaminhar** opção de menus do Outlook. Para ajudar a garantir que os utilizadores classificar os e-mails, bem como proteger, poderá preferir não, mas em vez disso, a adicionar este botão [configurar uma etiqueta para a proteção](configure-policy-protection.md) e um utilizador definido permissão para o Outlook. Esta definição de proteção é funcionalmente o mesmo como selecionar o **não reencaminhar** botão, mas quando esta funcionalidade está incluída com uma etiqueta, os e-mails são classificados, bem como protegidos.
    
        Esta definição de política também pode ser configurada com um cliente avançado definir como um [personalização de cliente](../rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook).
    
    - **Tornar disponível a opção de permissões personalizadas aos utilizadores**: quando esta definição está ativada, os utilizadores podem configurar as suas próprias definições de proteção e substituir as definições de proteção que tiver incluído com uma configuração de etiqueta. Quando esta definição estiver desativada, as opções de permissões personalizadas não estão disponíveis para os utilizadores selecionem o.
        
        Tenha em atenção que esta definição de política não tem efeito em permissões personalizadas que os utilizadores podem configurar a partir das opções de menu do Office. No entanto, também pode ser configurado com um cliente avançado definir como um [personalização de cliente](../rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users).
        
        As opções de permissões personalizadas estão localizadas nos seguintes locais:
        
        - Nas aplicações do Office: a partir do Friso, **home page** separador > **proteção** grupo > **proteger** > **permissões personalizadas**
        
        - No Explorador de Ficheiros: clique com o botão direito do rato > **Classificar e proteger** > **Permissões personalizadas**
    
    - **Forneça um URL personalizado para o cliente Azure Information Protection "Informar-me mais" página da web**: os utilizadores veem esta ligação no **Microsoft Azure Information Protection** caixa de diálogo, **ajuda e comentários**secção, quando estes selecionam **proteger** > **ajuda e comentários** do **home page** separador nas aplicações do Office. Por predefinição, esta ligação direciona-o para o site do [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection). Pode introduzir um URL do tipo HTTP ou HTTPS (recomendado) se quiser que esta ligação redirecione o utilizador para uma página Web alternativa. Não é efetuada nenhuma verificação para confirmar que o URL personalizado que introduziu é acessível ou é apresentado corretamente em todos os dispositivos.
        
        Por exemplo, para o suporte técnico, poderá introduzir a página de documentação do Microsoft que inclui informações sobre como instalar e utilizar o cliente (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) ou informações sobre a versão de lançamento (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Em alternativa, poderá publicar a sua própria página Web com informações para que os utilizadores contactem o seu suporte técnico ou um vídeo com passos para que os utilizadores saibam como utilizar as etiquetas que configurou.

3. Para guardar as alterações e disponibilizá-las aos utilizadores, clique em **guardar**.

Ao clicar em **guardar**, as alterações são automaticamente disponibilizadas a utilizadores e serviços. Já não é uma opção de publicar separado.

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
