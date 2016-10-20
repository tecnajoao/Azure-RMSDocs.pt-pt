---
title: Como criar uma nova etiqueta | Azure Information Protection
description: "Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection."
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
translationtype: Human Translation
ms.sourcegitcommit: ebb11148718f22c79bb49c82b9855f5e6f2a5b18
ms.openlocfilehash: 5cf6237f33d0818c8411cbb5126fc825c3c411d7


---

# Como criar uma nova etiqueta para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection.

Pode adicionar uma nova etiqueta ou adicionar uma nova etiqueta secundária a uma etiqueta existente quando precisar de um nível adicional de classificação. Por exemplo, a etiqueta **Secreto** etiqueta, que se encontra na [política predefinia](configure-policy-default.md), contém etiquetas secundárias.

Utilize as seguintes instruções para adicionar uma nova etiqueta à política do Azure Information Protection.

1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global e navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. No painel **Azure Information Protection**, efetue um dos seguintes procedimentos:

    - Para criar uma nova etiqueta: clique em **Adicionar uma nova etiqueta**.

    - Para criar uma nova etiqueta secundária: faça duplo clique ou selecione o menu de contexto (**…**) da etiqueta para a qual pretende criar uma etiqueta secundária e, em seguida, clique em **Adicionar uma etiqueta secundária**.

3. No painel **Etiqueta** ou **Etiqueta secundária**, selecione as opções que pretende para esta nova etiqueta e, em seguida, clique em **Guardar**.

    > [!NOTE]
    >Para informações sobre proteção de definições, consulte [Como configurar uma etiqueta para aplicar proteção](configure-policy-protection.md).

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Sep16_HO4-->


