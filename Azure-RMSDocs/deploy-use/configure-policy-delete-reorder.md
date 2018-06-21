---
title: Eliminar ou reordenar uma etiqueta do Azure Information Protection
description: Pode eliminar ou reordenar etiquetas do Azure Information Protection que os utilizadores veem.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: 887fbf7c349a7400e46393dc07c824238fba9e09
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32326604"
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Como eliminar ou reordenar uma etiqueta para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Pode eliminar ou reordenar etiquetas do Azure Information Protection que os utilizadores veem nas aplicações do Office, ao selecionar estas ações para as etiquetas.

![Eliminar ou reordenar etiquetas na política do Azure Information Protection](../media/info-protect-contextmenu.png)

Quando elimina uma etiqueta que tenha sido aplicada a documentos e e-mails, os utilizadores veem **não definido** da etiqueta de estado quando estes documentos e e-mails são seguintes aberto pelo cliente Azure Information Protection. No entanto, permanece de informações a etiqueta nos metadados e ainda pode ser lidos pelos serviços procurarem estas informações de etiqueta.

Além disso, se a etiqueta eliminada aplicada proteção, o que a proteção não é removida. As definições de proteção da etiqueta permanecem e apresenta na **modelos proteção** secção. Este modelo pode agora ser convertido para uma nova etiqueta ou ligado a uma etiqueta. Enquanto este modelo permanece, não é possível criar uma nova etiqueta com o mesmo nome que a etiqueta que tenha eliminado. Se pretender fazê-lo, tem as seguintes opções:

- Converta o modelo para uma etiqueta. 
    
    Esta ação é recomendada porque se necessário, em seguida, pode alterar o nome do modelo e modificar as definições de proteção.

- Utilize o PowerShell para o modelo de mudar o nome ou eliminá-lo.
    
    Antes de efetuar estas ações, considere se outros administradores ou serviços estão a utilizar o modelo e identificação-lo pelo respetivo nome atual. Elimine um modelo apenas se não precisa de abrir documentos ou e-mails que foram protegidos pelo modelo.

Para obter mais informações sobre a gestão de modelos de proteção, consulte [configurar e gerir modelos do Azure Information Protection](configure-policy-templates.md).

Antes de eliminar uma etiqueta, em vez disso, considere desativá-lo ou removê-lo da política:
    
- Ao desativar uma etiqueta que tenha sido aplicada a documentos e e-mails, a etiqueta aplicada não é removida destes documentos e e-mails. A etiqueta permanece na política, mas já não é apresentado como uma etiqueta que os utilizadores podem selecionar na barra de Information Protection. Desativar uma etiqueta permite-lhe manter a configuração original de quando poderá pretender que os utilizadores na mesma política selecione a etiqueta num momento posterior, quando simplesmente voltar a ativar a etiqueta.

- Quando remover uma etiqueta de uma política, a etiqueta aplicada também não é removida destes documentos e e-mails. Mas, ao remover a etiqueta da política, esta fica disponível para adicionar esta etiqueta à política de outra. Para obter mais informações, consulte [adicionar ou remover uma etiqueta de ou para uma política do Azure Information Protection](configure-policy-add-remove-label.md).

Ordene as etiquetas para que os utilizadores visualizem uma progressão lógica na barra Information Protection. Por exemplo, ordenar as etiquetas de acordo com o aumento de confidencialidade para que os utilizadores vejam a etiqueta menos confidencial em primeiro e a etiqueta mais confidencial em último. A [política predefinida](configure-policy-default.md) utiliza esta configuração e reflete o aumento de confidencialidade nos nomes das etiquetas.

> [!IMPORTANT]
>Se configurar [condições](configure-policy-classification.md) para as etiquetas que podem ser aplicadas a mais do que uma etiqueta, deve ordenar as etiquetas desde a menos confidencial à mais confidencial. Esta ordem garante que a etiqueta mais confidencial é aplicada quando são condições são avaliadas.


Utilize as seguintes instruções para efetuar as alterações.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção do menu: no **Azure Information Protection - etiquetas** painel, efetue um ou mais das seguintes ações: 

    - Para eliminar uma etiqueta: faça duplo clique ou selecione o menu de contexto (**...** ) para a etiqueta que pretende eliminar, clique em **eliminar esta etiqueta**e clique em **OK** para confirmar. 

    - Para desativar uma etiqueta: selecione a etiqueta que pretende desativar. No **etiqueta** painel, para **ativado**, selecione **desativar**e, em seguida, clique em **guardar**.

    - Para reordenar uma etiqueta: faça duplo clique ou selecione o menu de contexto (**...** ) para a etiqueta que pretende reordenar, clique em **mover para cima** ou **mover para baixo** até que a etiqueta esteja na ordem em que pretende.  

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

