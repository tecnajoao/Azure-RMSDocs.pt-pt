---
title: Configurar definições de política do Azure Information Protection – AIP
description: Configurar as definições na política do Azure Information Protection aplicáveis a todos os utilizadores e a todos os dispositivos.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/16/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: c3d95b0dc8328665c921ab4ff6b37e53ec726f03
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393487"
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Como configurar as definições de política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Além do título da barra de Information Protection e a descrição, existem algumas definições na política do Azure Information Protection que pode configurar independentemente das etiquetas:

![Definições globais da política do Azure Information Protection](./media/info-protect-policy-default-settingsv3.png)

Tenha em atenção que as definições de política podem ter valores padrão diferente, dependendo de quando tiver adquirido sua assinatura do Azure Information Protection. Algumas definições que também podem ser definidas um [definição de cliente personalizada](./rms-client/client-admin-guide-customizations.md).

Configurar estas definições:

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **políticas** opção de menu: Sobre o **do Azure Information Protection - políticas** painel, selecione **Global** se as definições que pretende configurar se aplicar a todos os utilizadores.
    
    Se as definições que pretende configurar estão num [política de âmbito](configure-policy-scope.md) para que eles se aplicam apenas a utilizadores selecionados, selecione a política de âmbito.

3. Sobre o **política** painel, configure as definições:
    
   - **Selecione a etiqueta predefinida**: Quando definir esta opção, selecione a etiqueta a atribuir a documentos e e-mails que não tenham uma etiqueta. Não é possível definir uma etiqueta como predefinição se tiver subetiquetas. 
    
   - **Todos os documentos e e-mails devem ter uma etiqueta**: Quando define esta opção como **no**, todos os documentos guardado e e-mails enviados devem ter uma etiqueta aplicada. As etiquetas podem ser atribuídas manualmente por um utilizador, automaticamente como resultado de uma [Condição](configure-policy-classification.md) ou pode ser atribuída por predefinição (definindo opção **Selecionar etiqueta predefinida**).
        
       Se uma etiqueta não estiver atribuída quando os utilizadores guardar um documento ou enviar um e-mail, é-lhes pedido para selecionar uma etiqueta. Por exemplo:
        
       ![Aviso do Azure Information Protection se a etiqueta for imposta](./media/info-protect-enforce-labelv2.png)
        
       Esta opção não se aplica quando remover uma etiqueta com o [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) cmdlet do PowerShell com o *RemoveLabel* parâmetro.
        
   - **Os utilizadores têm de fornecer justificação para definir uma etiqueta de classificação inferior, remover uma etiqueta ou remover a proteção**: Quando define esta opção como **no** e um utilizador realiza uma destas ações (por exemplo, altere a **público** a etiqueta a **pessoais**), é pedido ao utilizador que forneça uma explicação para esta ação. Por exemplo, o utilizador pode explicar que o documento já não contém informações confidenciais. A ação e a justificação são registadas no registo de eventos Windows local: **Registos de serviços e aplicativos** > **Azure Information Protection**.  
        
       ![Aviso do Azure Information Protection se a nova classificação for inferior](./media/info-protect-lower-justification.png)
        
       Esta opção não é aplicável para reduzir a classificação de subetiquetas sob o mesmo rótulo de principal ou para a versão de pré-visualização do scanner.
        
   - **Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos**: Quando define esta opção como **recomendado**, é pedido aos utilizadores para aplicar uma etiqueta à respetiva mensagem de e-mail. A etiqueta é selecionada de forma dinâmica com base nas etiquetas de classificação aplicadas aos anexos e é selecionada a etiqueta de classificação mais elevada. O anexo tem de ser um ficheiro físico e não pode ser uma ligação a um ficheiro (por exemplo, uma ligação a um ficheiro no SharePoint ou no OneDrive para Empresas). Os utilizadores podem aceitar a recomendação ou ignorá-la. Quando define esta opção como **automática**, a etiqueta é aplicada automaticamente, mas os utilizadores podem remover a etiqueta ou selecione uma etiqueta diferente antes de enviar o e-mail.
    
     Quando o anexo com a etiqueta de classificação mais alta é configurado para proteção com a definição de pré-visualização de permissões definidas pelo utilizador, a mensagem de e-mail tem o nome com a mesma classificação, mas não a proteção é aplicada.
    
   - **Apresentar a barra de Information Protection nas aplicações do Office**: Quando esta definição estiver desativada, os utilizadores não é possível selecionar etiquetas a partir de uma barra no Word, Excel, PowerPoint e Outlook. Em vez disso, os utilizadores devem selecionar etiquetas a partir da **Protect** botão na faixa de opções. Quando esta definição está ativado, os utilizadores podem selecionar etiquetas a partir da barra ou no botão.
        
       Quando esta definição está ativado, ele pode ser utilizado em conjunto com um definição para que os utilizadores podem de cliente avançado [ocultar permanentemente a barra do Azure Information Protection](./rms-client/client-admin-guide-customizations.md#permanently-hide-the-azure-information-protection-bar) se optarem por não mostrar a barra. Pode fazê-lo ao desmarcar a **Mostrar barra** opção da **proteger** botão.
    
   - **Adicionar o botão não reencaminhar ao Friso do Outlook**: Quando esta definição está ativado, os utilizadores podem selecionar esse botão a partir da **proteção** grupo no Friso do Outlook, além de selecionar o **não reencaminhar** opção a partir dos menus do Outlook. Para ajudar a garantir que os utilizadores classificar seus emails, bem como protegê-los, não adicione este botão, mas em vez disso, pode preferir [configurar uma etiqueta para proteção](configure-policy-protection.md) e um utilizador definida permissão para o Outlook. Esta definição de proteção é funcionalmente o mesmo como selecionar o **não reencaminhar** botão, mas quando esta funcionalidade está incluída com uma etiqueta, mensagens de correio eletrónico são classificadas como protegidas.
    
       Esta definição de política também pode ser configurada com um cliente avançado definir como um [personalização de cliente](./rms-client/client-admin-guide-customizations.md#hide-or-show-the-do-not-forward-button-in-outlook).
    
   - **Disponibilizar a opção de permissões personalizadas aos utilizadores**: Quando esta definição está ativado, os utilizadores veem as opções para definir suas próprias definições de proteção que podem substituir as definições de proteção que possa ter incluído com uma configuração de etiqueta. Os utilizadores também podem ver uma opção para remover a proteção. Quando esta definição estiver desativada, os utilizadores não vir estas opções.
        
       Tenha em atenção que esta definição de política não tem qualquer efeito nas permissões personalizadas que os utilizadores podem configurar a partir das opções de menu do Office. No entanto, também pode ser configurado com um cliente avançado definir como um [personalização de cliente](./rms-client/client-admin-guide-customizations.md#make-the-custom-permissions-options-available-or-unavailable-to-users).
        
       As opções de permissões personalizadas estão localizadas nos seguintes locais:
        
       - Em aplicativos do Office: A partir do friso **home page** separador > **proteção** grupo > **proteger** > **permissões personalizadas**
        
       - No Explorador de ficheiros: Com o botão direito > **classificar e proteger** > **permissões personalizadas**
    
   - **Fornecer um URL personalizado para o cliente do Azure Information Protection, página da web "Mais informações"**: Os utilizadores veem esta ligação no **Microsoft Azure Information Protection** caixa de diálogo **ajuda e Feedback** secção, quando estes selecionarem **proteger**  >  **Ajuda e feedback** partir da **home page** separador nas aplicações do Office. Por predefinição, esta ligação direciona-o para o site do [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection). Pode introduzir um URL do tipo HTTP ou HTTPS (recomendado) se quiser que esta ligação redirecione o utilizador para uma página Web alternativa. Não é efetuada nenhuma verificação para confirmar que o URL personalizado que introduziu é acessível ou é apresentado corretamente em todos os dispositivos.
        
       Por exemplo, para o suporte técnico, poderá introduzir a página de documentação da Microsoft que inclui informações sobre como instalar e utilizar o cliente (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) ou informações sobre a versão de lançamento (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Em alternativa, poderá publicar a sua própria página Web com informações para que os utilizadores contactem o seu suporte técnico ou um vídeo com passos para que os utilizadores saibam como utilizar as etiquetas que configurou.

4. Para guardar as alterações e disponibilizá-los aos utilizadores, clique em **guardar**.

Quando clica em **guardar**, as suas alterações estão automaticamente disponíveis para utilizadores e serviços. Já não existe uma opção de publicar separado.

## <a name="next-steps"></a>Passos Seguintes

Para ver como algumas destas definições de política podem trabalhar em conjunto, experimente o [definições de política de configurar o Azure Information Protection que funcionam em conjunto](infoprotect-settings-tutorial.md) tutorial.

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).

