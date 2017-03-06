---
title: Nova etiqueta do Azure Information Protection
description: "Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 602fef628f882eb79fe78b5acf89bde1721aa0ec
ms.lasthandoff: 02/24/2017


---

# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Como criar uma nova etiqueta para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection.

Pode adicionar uma nova etiqueta ou adicionar uma nova etiqueta secundária a uma etiqueta existente quando precisar de um nível adicional de classificação. Por exemplo, a etiqueta **Secreto** etiqueta, que se encontra na [política predefinia](configure-policy-default.md), contém etiquetas secundárias.

Utilize as seguintes instruções para adicionar uma nova etiqueta à política do Azure Information Protection.

1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global e navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a nova etiqueta que pretende adicionar se aplicar a todos os utilizadores, realize uma das seguintes ações no painel **Política:Global**. 

    - Para criar uma nova etiqueta: clique em **Adicionar uma nova etiqueta**.

    - Para criar uma nova etiqueta secundária: faça duplo clique ou selecione o menu de contexto (**…**) da etiqueta para a qual pretende criar uma etiqueta secundária e, em seguida, clique em **Adicionar uma etiqueta secundária**.
    
     Se a nova etiqueta que pretende adicionar for incluída numa [política de âmbito](configure-policy-scope.md) para ser aplicada apenas a utilizadores selecionados, selecione primeiro essa política de âmbito no painel inicial do **Azure Information Protection**.

3. No painel **Etiqueta** ou **Etiqueta secundária**, selecione as opções que pretende para esta nova etiqueta e, em seguida, clique em **Guardar**.

    > [!NOTE]
    >Para informações sobre proteção de definições, consulte [Como configurar uma etiqueta para aplicar proteção](configure-policy-protection.md).

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## <a name="next-steps"></a>Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


