---
title: Nova etiqueta do Azure Information Protection
description: "Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: ac12ab9023499d5aac632159ef689a8f10a91418
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Como criar uma nova etiqueta para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection.

Pode adicionar uma nova etiqueta ou adicionar uma nova etiqueta secundária a uma etiqueta existente quando precisar de um nível adicional de classificação. Por exemplo, a última etiqueta na [política predefinida](configure-policy-default.md) contém subetiquetas.

Utilize as seguintes instruções para adicionar uma nova etiqueta à política do Azure Information Protection.

1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global e navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a nova etiqueta que pretende adicionar se aplicar a todos os utilizadores, realize uma das seguintes ações no painel **Política:Global**. 

    - Para criar uma nova etiqueta: clique em **Adicionar uma nova etiqueta**.

    - Para criar uma nova etiqueta secundária: faça duplo clique ou selecione o menu de contexto (**…**) da etiqueta para a qual pretende criar uma etiqueta secundária e, em seguida, clique em **Adicionar uma etiqueta secundária**.
    
     Se a nova etiqueta que pretende adicionar for incluída numa [política de âmbito](configure-policy-scope.md) para ser aplicada apenas a utilizadores selecionados, selecione primeiro essa política de âmbito no painel inicial do **Azure Information Protection**.

3. No painel **Etiqueta** ou **Etiqueta secundária**, selecione as opções que pretende para esta nova etiqueta e, em seguida, clique em **Guardar**.
    
    Tenha em atenção que a cor preta é automaticamente atribuída às novas etiquetas. Selecione uma cor distinta na lista de cores ou introduza um código terno hexadecimal dos componentes RGB (vermelho, verde e azul) da cor. Por exemplo, **#DAA520**. Se precisar de uma referência para estes códigos, o artigo [Cores por Nome](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx) da documentação da MSDN é um ponto de partida útil. Poderá também encontrar estes códigos em muitos programas de edição de imagens, como o Microsoft Paint, onde pode selecionar uma cor personalizada a partir de uma paleta e os valores RGB são automaticamente apresentados.

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

5. Se pretender que este novo nome de etiqueta e descrição sejam apresentados em idiomas diferentes para os utilizadores, siga os procedimentos em [Como configurar etiquetas para diferentes idiomas](configure-policy-languages.md). 

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

