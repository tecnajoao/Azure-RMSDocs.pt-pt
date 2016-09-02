---
title: "Como configurar as definições globais da política do Azure Information Protection | Azure Rights Management"
description: "Existem três definições na política do Azure Information Protection aplicáveis a todos os utilizadores e a todos os dispositivos."
manager: mbaldwin
ms.date: 08/08/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: c48f5488e49a54b970f76012e0f2f17fe4158691


---

# Como configurar as definições de política global para o Azure Information Protection

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Existem 3 definições da política de proteção de informações do Azure que se aplicam a todos os utilizadores e a todos os dispositivos:

![Definições globais da política do Azure Information Protection](../media/info-protect-policy-settings.png)


Configurar estas definições:

1. Se ainda não o fez, inicie sessão no [portal do Azure](https://portal.azure.com) e, em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Procurar** e comece a escrever **Information** na caixa Filtro. Selecione **Azure Information Protection**.

2. No painel **Azure Information Protection**, configure estas definições globais:

    - **Todos os documentos e e-mails devem ter uma etiqueta**: quando configurar esta opção como **Ativado**, todos os todos os documentos guardado e e-mails enviados devem ter uma etiqueta aplicada. As etiquetas podem ser atribuídas manualmente por um utilizador, automaticamente como resultado de uma [Condição](configure-policy-classification.md) ou pode ser atribuída por predefinição (definindo opção **Selecionar etiqueta predefinida**). 

    Se uma etiqueta não estiver atribuída quando um utilizador guardar um documento ou enviar um e-mail, é-lhe pedido para selecionar uma etiqueta:

    ![Aviso do Azure Information Protection se a nova classificação for inferior](../media/info-protect-enforce-label.png)

    - **Selecione a etiqueta predefinida**: quando definir esta opção, selecione a etiqueta para atribuir a documentos e e-mails que não tenham uma etiqueta. Não é possível definir uma etiqueta como predefinição se tiver etiquetas secundárias. 

    - **Os utilizadores tem de fornecer justificação ao reduzir o nível de confidencialidade**: ao configurar esta opção como **Ativado** e um utilizador altera a etiqueta de um documento ou e-mail existente a uma etiqueta que tem um nível inferior de confidencialidade (por exemplo, a partir de **Secreto** para **Público**), é pedido ao utilizador que forneça uma explicação para esta ação. Por exemplo, o utilizador pode explicar que o documento já não contém informações confidenciais. A ação e a justificação são registadas no registo de eventos do Windows local: **Aplicação** > **Proteção do Microsoft Azure Information Protection**.  

    ![Aviso do Azure Information Protection se a nova classificação for inferior](../media/info-protect-lower-justification.png)

    Esta opção não é aplicável a etiquetas secundárias.

3. Para guardar as alterações, clique em **Guardar**.

4. Para disponibilizar as alterações aos utilizadores, clique em **ublicar**.

## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy).  












<!--HONumber=Aug16_HO4-->


