---
title: Como criar uma nova etiqueta para o Azure Information Protection | Azure Rights Management
description: "Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection."
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: 96cbe6cbe823d2c90ec91cbf77ef7d96cc6a568c


---

# Como criar uma nova etiqueta para o Azure Information Protection

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection.

Pode adicionar uma nova etiqueta ou adicionar uma nova etiqueta secundária a uma etiqueta existente quando precisar de um nível adicional de classificação. Por exemplo, a etiqueta **Secreto** etiqueta, que se encontra na [política predefinia](configure-policy-default.md), contém etiquetas secundárias.

Utilize as seguintes instruções para adicionar uma nova etiqueta à política do Azure Information Protection.

1. Se ainda não o fez, inicie sessão no [portal do Azure](https://portal.azure.com) e, em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Procurar** e comece a escrever **Information** na caixa Filtro. Selecione **Azure Information Protection**.

2. No painel **Azure Information Protection**, efetue um dos seguintes procedimentos:

    - Para criar uma nova etiqueta: clique em **Adicionar uma nova etiqueta**.

    - Para criar uma nova etiqueta secundária: faça duplo clique ou selecione o menu de contexto (**…**) da etiqueta para a qual pretende criar uma etiqueta secundária e, em seguida, clique em **Adicionar uma etiqueta secundária**.

3. No painel **Etiqueta** ou **Etiqueta secundária**, selecione as opções que pretende para esta nova etiqueta e, em seguida, clique em **Guardar**.

    > [!NOTE]
    >Para informações sobre proteção de definições, consulte [Como configurar uma etiqueta para aplicar proteção](configure-policy-protection.md).

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Aug16_HO4-->


