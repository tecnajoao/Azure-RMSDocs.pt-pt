---
title: Nova etiqueta do Azure Information Protection
description: "Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: cb7af6831040bb42a3c7e3a7e8ea355f72fc433c
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Como criar uma nova etiqueta para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection.

Pode adicionar uma nova etiqueta ou adicionar um novo sublabel para uma etiqueta existente quando precisar de um nível adicional de classificação. Por exemplo, a etiqueta na última o [política predefinida](configure-policy-default.md), contém sublabels.

Utilize as seguintes instruções para adicionar uma nova etiqueta à política do Azure Information Protection.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no menu hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a nova etiqueta que pretende adicionar for para todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel.
    
    Se estiver a nova etiqueta que pretende adicionar utilizadores selecionados um [âmbito política](configure-policy-scope.md), do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

3. Do **Azure Information Protection - política Global** painel, ou o **política:\<nome >** painel, efetue uma das seguintes ações:
    
    - Para criar uma nova etiqueta: clique em **Adicionar uma nova etiqueta**.
    
    - Para criar um novo sublabel: faça duplo clique ou selecione o menu de contexto (**...** ) para a etiqueta que pretende criar um sublabel para e, em seguida, clique em **adicionar uma etiqueta secundária**.

4. No painel **Etiqueta** ou **Etiqueta secundária**, selecione as opções que pretende para esta nova etiqueta e, em seguida, clique em **Guardar**.
    
    Tenha em atenção que a cor preta é automaticamente atribuída às novas etiquetas. Selecione uma cor distinta na lista de cores ou introduza um código terno hexadecimal dos componentes RGB (vermelho, verde e azul) da cor. Por exemplo, **#DAA520**. Se precisar de uma referência para estes códigos [cores pelo nome](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx) partir o MSDN, documentação é de um ponto de partida útil e encontrará estes códigos de imagem muitos editar programas, tais como Microsoft Paint, onde escolher uma cor personalizada de um paleta e apresenta os valores RGB automaticamente.

5. Para disponibilizar as alterações aos utilizadores, no painel inicial **Azure Information Protection**, clique em **Publicar**.

6. Se pretender que este novo nome de etiqueta e descrição sejam apresentados em idiomas diferentes para os utilizadores, siga os procedimentos em [Como configurar etiquetas para diferentes idiomas](configure-policy-languages.md). 

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

