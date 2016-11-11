---
title: "Como configurar as definições de política global | Azure Information Protection"
description: "Existem três definições na política do Azure Information Protection aplicáveis a todos os utilizadores e a todos os dispositivos."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/04/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: addc24fed28cee52b57c7e3bde926d6324478e7b
ms.openlocfilehash: 970a42e89d09af34e9ff16714682d1de250175f6


---

# <a name="how-to-configure-the-global-policy-settings-for-azure-information-protection"></a>Como configurar as definições de política global para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Existem 3 definições da política de proteção de informações do Azure que se aplicam a todos os utilizadores e a todos os dispositivos:

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

3. Para guardar as alterações, clique em **Guardar**.

4. Para disponibilizar as alterações aos utilizadores, clique em **ublicar**.

## <a name="next-steps"></a>Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  












<!--HONumber=Nov16_HO1-->


