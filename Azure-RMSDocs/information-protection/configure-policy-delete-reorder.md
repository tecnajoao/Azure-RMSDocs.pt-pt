---
title: Como eliminar ou reordenar uma etiqueta para o Azure Information Protection | Azure Rights Management
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 50a60f8a0f8cb92aba7453e6c1dedacbe004a5ed


---

# Como eliminar ou reordenar uma etiqueta para o Azure Information Protection

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Pode eliminar ou reordenar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-o na política do Azure Information Protection.

![Eliminar ou reordenar etiquetas na política do Azure Information Protection](../media/info-protect-contextmenu.png)

Em vez de eliminar uma etiqueta, poderá simplesmente querer desativá-la, no caso de pretender manter a configuração de etiqueta mas impedi-la de ser apresentada na barra Information Protection.

Ordene as etiquetas para que os utilizadores visualizem uma progressão lógica na barra Information Protection. Por exemplo, ordenar as etiquetas de acordo com o aumento de confidencialidade para que os utilizadores vejam a etiqueta menos confidencial em primeiro e a etiqueta mais confidencial em último. A [política predefinida](configure-policy-default.md) utiliza esta configuração.

> [!IMPORTANT]
>Se configurar [condições](configure-policy-classification.md) para as etiquetas que podem ser aplicadas a mais do que uma etiqueta, deve ordenar as etiquetas desde a menos confidencial à mais confidencial. Esta ordem garante que a etiqueta mais confidencial é aplicada quando são condições são avaliadas.


Utilize as seguintes instruções para efetuar as alterações.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).

2. No menu Hub, clique em **Procurar** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

3. No painel do **Azure Information Protection**, efetue uma das seguintes ações, dependendo se pretende eliminar, desativar ou reordenar uma etiqueta:

    - Para eliminar uma etiqueta: faça duplo clique ou selecione o menu de contexto (**…**) para a etiqueta que pretende eliminar, clique em **Eliminar esta etiqueta** e clique em **Sim** para confirmar. Em seguida, clique em **Guardar**. 

    - Para desativar uma etiqueta: selecione a etiqueta que pretende desativar. No painel **Etiqueta** , para **Ativado**, clique em **Desativar**e, em seguida, clique em **Guardar**.

    - Para reordenar uma etiqueta: faça duplo clique ou selecione o menu de contexto (**…**) para a etiqueta que pretende reordenar, clique em **Mover para cima** ou **Mover para baixo** até que a etiqueta esteja na ordem em que pretende. Em seguida, clique em **Guardar**. 

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Jul16_HO5-->

