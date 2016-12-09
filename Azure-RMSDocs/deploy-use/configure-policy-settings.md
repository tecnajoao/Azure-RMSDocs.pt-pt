---
title: "Como configurar as definições de política global | Azure Information Protection"
description: "Existem três definições na política do Azure Information Protection aplicáveis a todos os utilizadores e a todos os dispositivos."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: 8fa2ed9ff9ebe5c850ab5681e4dcc1f3d3c676b3
ms.openlocfilehash: de5f5fbddb84e4444751e9fefbfe6ec3fe3e45e4


---

# <a name="how-to-configure-the-global-policy-settings-for-azure-information-protection"></a>Como configurar as definições de política global para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Existem quatro definições da política do Azure Information Protection que se aplicam a todos os utilizadores e a todos os dispositivos:

![Definições globais da política do Azure Information Protection](../media/info-protect-policy-settings.png)


Configurar estas definições:

1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global e navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. No painel **Azure Information Protection**, configure estas definições globais:

    - **Todos os documentos e e-mails devem ter uma etiqueta**: quando configurar esta opção como **Ativado**, todos os todos os documentos guardado e e-mails enviados devem ter uma etiqueta aplicada. As etiquetas podem ser atribuídas manualmente por um utilizador, automaticamente como resultado de uma [Condição](configure-policy-classification.md) ou pode ser atribuída por predefinição (definindo opção **Selecionar etiqueta predefinida**). 

    Se uma etiqueta não estiver atribuída quando um utilizador guardar um documento ou enviar um e-mail, é-lhe pedido para selecionar uma etiqueta:

    ![Aviso do Azure Information Protection se a nova classificação for inferior](../media/info-protect-enforce-label.png)

    - **Selecione a etiqueta predefinida**: quando definir esta opção, selecione a etiqueta para atribuir a documentos e e-mails que não tenham uma etiqueta. Não é possível definir uma etiqueta como predefinição se tiver etiquetas secundárias. 

    - **Os utilizadores têm de fornecer uma justificação para reduzir a etiqueta de classificação, remover uma etiqueta ou remover a proteção**: quando define esta opção como **Ativado** e um utilizador realiza uma destas ações (como alterar a etiqueta **Secreto** para **Pessoal**), é-lhe pedido que forneça uma explicação para esta ação. Por exemplo, o utilizador pode explicar que o documento já não contém informações confidenciais. A ação e a justificação são registadas no registo de eventos do Windows local: **Aplicação** > **Proteção do Microsoft Azure Information Protection**.  

    ![Aviso do Azure Information Protection se a nova classificação for inferior](../media/info-protect-lower-justification.png)

    Esta opção não é aplicável a etiquetas secundárias.

    - **Forneça um URL personalizado para a página Web "Mais informações" do cliente do Azure Information Protection**: os utilizadores veem esta ligação na caixa de diálogo do **Microsoft Azure Information Protection**, na secção **Ajuda e Feedback**, quando selecionam **Proteger** > **Ajuda e feedback** no separador **Base** nas respetivas aplicações do Office. Por predefinição, esta ligação direciona-o para o site do [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection). Pode introduzir um URL do tipo HTTP ou HTTPS (recomendado) se quiser que esta ligação redirecione o utilizador para uma página Web alternativa. Não é efetuada nenhuma verificação para confirmar que o URL personalizado que introduziu é acessível ou é apresentado corretamente em todos os dispositivos.
    
    Por exemplo, para suporte técnico, pode introduzir a página de documentação da Microsoft que inclui informações acerca da instalação e da utilização do cliente (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) ou informações relativas à versão de lançamento (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Em alternativa, poderá publicar a sua própria página Web com informações para que os utilizadores contactem o seu suporte técnico ou um vídeo com passos para que os utilizadores saibam como utilizar as etiquetas que configurou.

3. Para guardar as alterações, clique em **Guardar**.

4. Para disponibilizar as alterações aos utilizadores, clique em **Publicar**.

## <a name="next-steps"></a>Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  












<!--HONumber=Nov16_HO3-->

