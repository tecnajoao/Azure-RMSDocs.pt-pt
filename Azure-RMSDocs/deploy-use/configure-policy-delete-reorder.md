---
title: Como eliminar ou reordenar uma etiqueta | Azure Information Protection
description: "Pode eliminar ou reordenar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-o na política do Azure Information Protection."
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
translationtype: Human Translation
ms.sourcegitcommit: ebb11148718f22c79bb49c82b9855f5e6f2a5b18
ms.openlocfilehash: 3e73e928c8a0189c275e02c189db5c872993d9dd


---

# Como eliminar ou reordenar uma etiqueta para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Pode eliminar ou reordenar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-o na política do Azure Information Protection.

![Eliminar ou reordenar etiquetas na política do Azure Information Protection](../media/info-protect-contextmenu.png)

Em vez de eliminar uma etiqueta, poderá simplesmente querer desativá-la, no caso de pretender manter a configuração de etiqueta mas impedi-la de ser apresentada na barra Information Protection.

Ordene as etiquetas para que os utilizadores visualizem uma progressão lógica na barra Information Protection. Por exemplo, ordenar as etiquetas de acordo com o aumento de confidencialidade para que os utilizadores vejam a etiqueta menos confidencial em primeiro e a etiqueta mais confidencial em último. A [política predefinida](configure-policy-default.md) utiliza esta configuração.

> [!IMPORTANT]
>Se configurar [condições](configure-policy-classification.md) para as etiquetas que podem ser aplicadas a mais do que uma etiqueta, deve ordenar as etiquetas desde a menos confidencial à mais confidencial. Esta ordem garante que a etiqueta mais confidencial é aplicada quando são condições são avaliadas.


Utilize as seguintes instruções para efetuar as alterações.

1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global e navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. No painel do **Azure Information Protection**, efetue uma das seguintes ações, dependendo se pretende eliminar, desativar ou reordenar uma etiqueta:

    - Para eliminar uma etiqueta: faça duplo clique ou selecione o menu de contexto (**…**) para a etiqueta que pretende eliminar, clique em **Eliminar esta etiqueta** e clique em **Sim** para confirmar. Em seguida, clique em **Guardar**. 

    - Para desativar uma etiqueta: selecione a etiqueta que pretende desativar. No painel **Etiqueta**, para **Ativado**, clique em **Desativar**e, em seguida, clique em **Guardar**.

    - Para reordenar uma etiqueta: faça duplo clique ou selecione o menu de contexto (**…**) para a etiqueta que pretende reordenar, clique em **Mover para cima** ou **Mover para baixo** até que a etiqueta esteja na ordem em que pretende. Em seguida, clique em **Guardar**. 

3. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Sep16_HO4-->


