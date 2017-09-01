---
title: "Configurar as definições de política do Azure Information Protection"
description: "Configurar as definições na política do Azure Information Protection aplicáveis a todos os utilizadores e a todos os dispositivos."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: 2bc5493c906b0d21be2679f0d777cb4fd5fbe30c
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2017
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Como configurar as definições de política do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Além do título da barra e a descrição do Information Protection, existem algumas definições na política do Azure Information Protection que se aplicam a todos os utilizadores e a todos os dispositivos:

![Definições globais da política do Azure Information Protection](../media/info-protect-policy-default-settingsv2.png)


Configurar estas definições:

1. Se que ainda não o fez, numa nova janela do browser, inicie sessão no [portal do Azure](https://portal.azure.com) como um administrador de segurança ou um administrador global. Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se as definições que pretende configurar serão aplicada a todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel.
    
    Se as definições que pretende configurar estão disponíveis num [âmbito política](configure-policy-scope.md) para que se apliquem a utilizadores selecionados apenas, do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

3. Do **Azure Information Protection - política Global** painel, ou o **política:\<nome >** painel, configure as definições:
    
    - **Todos os documentos e e-mails devem ter uma etiqueta**: quando configurar esta opção como **Ativado**, todos os todos os documentos guardado e e-mails enviados devem ter uma etiqueta aplicada. As etiquetas podem ser atribuídas manualmente por um utilizador, automaticamente como resultado de uma [Condição](configure-policy-classification.md) ou pode ser atribuída por predefinição (definindo opção **Selecionar etiqueta predefinida**). 
        
        Se uma etiqueta não estiver atribuída quando um utilizador guardar um documento ou enviar um e-mail, é-lhe pedido para selecionar uma etiqueta. Por exemplo:
        
        ![Aviso do Azure Information Protection se a etiqueta for imposta](../media/info-protect-enforce-labelv2.png)
        
    - **Selecione a etiqueta predefinida**: quando definir esta opção, selecione a etiqueta para atribuir a documentos e e-mails que não tenham uma etiqueta. Não é possível definir uma etiqueta como predefinição se tiver etiquetas secundárias. 
        
    - **Os utilizadores têm de fornecer uma justificação para reduzir a segurança da etiqueta de classificação, remover uma etiqueta ou remover a proteção**: quando define esta opção como **Ativado** e um utilizador realiza uma destas ações (como alterar a etiqueta **Público** para **Pessoal**), é-lhe pedido que forneça uma explicação para esta ação. Por exemplo, o utilizador pode explicar que o documento já não contém informações confidenciais. A ação e a justificação são registadas no registo de eventos do Windows local: **Aplicação** > **Proteção do Microsoft Azure Information Protection**.  
        
        ![Aviso do Azure Information Protection se a nova classificação for inferior](../media/info-protect-lower-justification.png)
        
        Esta opção não é aplicável a etiquetas secundárias.
        
    - **Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos**: quando define esta opção como **Recomendado**, é pedido aos utilizadores que apliquem uma etiqueta à respetiva mensagem de e-mail. A etiqueta é selecionada de forma dinâmica com base nas etiquetas de classificação aplicadas aos anexos e é selecionada a etiqueta de classificação mais elevada. O anexo tem de ser um ficheiro físico e não pode ser uma ligação a um ficheiro (por exemplo, uma ligação a um ficheiro no SharePoint ou no OneDrive para Empresas). Os utilizadores podem aceitar a recomendação ou ignorá-la. Quando define esta opção como **Ativado**, a etiqueta é automaticamente aplicada mas os utilizadores podem removê-la ou selecionar uma etiqueta diferente antes de enviarem o e-mail.  

    - **Forneça um URL personalizado para a página Web "Mais informações" do cliente do Azure Information Protection**: os utilizadores veem esta ligação na caixa de diálogo do **Microsoft Azure Information Protection**, na secção **Ajuda e Feedback**, quando selecionam **Proteger** > **Ajuda e feedback** no separador **Base** nas respetivas aplicações do Office. Por predefinição, esta ligação direciona-o para o site do [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection). Pode introduzir um URL do tipo HTTP ou HTTPS (recomendado) se quiser que esta ligação redirecione o utilizador para uma página Web alternativa. Não é efetuada nenhuma verificação para confirmar que o URL personalizado que introduziu é acessível ou é apresentado corretamente em todos os dispositivos.
        
        Por exemplo, para suporte técnico, pode introduzir a página de documentação da Microsoft que inclui informações acerca da instalação e da utilização do cliente (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) ou informações relativas à versão de lançamento (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Em alternativa, poderá publicar a sua própria página Web com informações para que os utilizadores contactem o seu suporte técnico ou um vídeo com passos para que os utilizadores saibam como utilizar as etiquetas que configurou.

3. Para guardar as alterações, clique em **Guardar**.

4. Para disponibilizar as alterações aos utilizadores, no painel inicial **Azure Information Protection**, clique em **Publicar**.

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
