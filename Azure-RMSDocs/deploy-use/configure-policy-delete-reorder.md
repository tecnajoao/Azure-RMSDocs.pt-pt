---
title: Eliminar ou reordenar uma etiqueta do Azure Information Protection
description: "Pode eliminar ou reordenar etiquetas que os utilizadores veem na barra do Information Protection, configurando-o na política do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: 85d8e612d95358ce7f5d883450dc207e54549828
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Como eliminar ou reordenar uma etiqueta para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Pode eliminar ou reordenar etiquetas que os utilizadores veem na barra do Information Protection selecionando estas ações na política do Azure Information Protection.

![Eliminar ou reordenar etiquetas na política do Azure Information Protection](../media/info-protect-contextmenu.png)

Quando eliminar uma etiqueta que tenha sido aplicada a documentos e e-mails e, em seguida, publicar a política do Azure Information Protection, essa etiqueta é removida automaticamente estes documentos ou e-mails quando estão seguintes aberto pelo cliente Azure Information Protection.

No entanto, se a etiqueta aplicada proteção, o que a proteção não é removida. As definições de proteção da etiqueta permanecem e apresenta na **modelos proteção**. Este modelo pode agora ser convertido para uma nova etiqueta ou ligado a uma etiqueta. Enquanto este modelo permanece, não é possível criar uma nova etiqueta com o mesmo nome que a etiqueta que tenha eliminado. Se pretender fazê-lo, tem as seguintes opções:

- Converta o modelo para uma etiqueta. 
    
    Esta ação é recomendada porque se necessário, em seguida, pode alterar o nome do modelo e modificar as definições de proteção.

- Utilize o PowerShell para o modelo de mudar o nome ou eliminá-lo.
    
    Antes de efetuar estas ações, considere se outros administradores ou serviços estão a utilizar o modelo e identificação-lo pelo respetivo nome atual. Elimine um modelo apenas se não precisa de abrir documentos ou e-mails que foram protegidos pelo modelo.

Para obter mais informações sobre a gestão de modelos de proteção, consulte [configurar e gerir modelos do Azure Information Protection](configure-policy-templates.md).

Antes de eliminar uma etiqueta, pondere desativá-la. Ao desativar uma etiqueta que tenha sido aplicada a documentos e e-mails, a etiqueta aplicada não é removida destes documentos e e-mails, mas já não é apresentada como uma etiqueta que os utilizadores podem selecionar na barra de Information Protection. Desativar uma etiqueta também lhe permite manter a configuração original. Se quiser que os utilizadores selecionem a etiqueta posteriormente, basta reativá-la.

Ordene as etiquetas para que os utilizadores visualizem uma progressão lógica na barra Information Protection. Por exemplo, ordenar as etiquetas de acordo com o aumento de confidencialidade para que os utilizadores vejam a etiqueta menos confidencial em primeiro e a etiqueta mais confidencial em último. A [política predefinida](configure-policy-default.md) utiliza esta configuração e reflete o aumento de confidencialidade nos nomes das etiquetas.

> [!IMPORTANT]
>Se configurar [condições](configure-policy-classification.md) para as etiquetas que podem ser aplicadas a mais do que uma etiqueta, deve ordenar as etiquetas desde a menos confidencial à mais confidencial. Esta ordem garante que a etiqueta mais confidencial é aplicada quando são condições são avaliadas.


Utilize as seguintes instruções para efetuar as alterações.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Se a etiqueta que pretende configurar será aplicada a todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel.
    
    Se a etiqueta que pretende configurar está a ser um [âmbito política](configure-policy-scope.md) para que o se aplica apenas a utilizadores selecionados do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

3. Do **Azure Information Protection - política Global** painel, ou o **política:\<nome >** painel, efetue um ou mais das seguintes ações: 

    - Para eliminar uma etiqueta: faça duplo clique ou selecione o menu de contexto (**…**) para a etiqueta que pretende eliminar, clique em **Eliminar esta etiqueta** e clique em **Sim** para confirmar. Em seguida, clique em **Guardar**. 

    - Para desativar uma etiqueta: selecione a etiqueta que pretende desativar. No painel **Etiqueta**, para **Ativado**, clique em **Desativar**e, em seguida, clique em **Guardar**.

    - Para reordenar uma etiqueta: faça duplo clique ou selecione o menu de contexto (**...** ) para a etiqueta que pretende reordenar, clique em **mover para cima** ou **mover para baixo** até que a etiqueta esteja na ordem em que pretende. Em seguida, clique em **Guardar**. 

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

