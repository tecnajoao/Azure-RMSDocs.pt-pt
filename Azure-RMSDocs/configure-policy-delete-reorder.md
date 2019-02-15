---
title: Eliminar ou reordenar uma etiqueta do Azure Information Protection – AIP
description: Pode eliminar ou reordenar etiquetas do Azure Information Protection que os utilizadores veem.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/28/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: 8a672c1d5f4b6c18a25687ebb183285cd3d6881f
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260090"
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Como eliminar ou reordenar uma etiqueta para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Pode eliminar ou reordenar etiquetas do Azure Information Protection que os utilizadores veem nas aplicações do Office, ao selecionar estas ações para as etiquetas.

![Eliminar ou reordenar etiquetas na política do Azure Information Protection](./media/info-protect-contextmenu.png)

Quando elimina uma etiqueta que foi aplicada a documentos e e-mails, os utilizadores veem **nenastaveno** para a etiqueta de estado quando estes documentos e e-mails são os próximos aberto pelo cliente do Azure Information Protection. No entanto, os permanecem de informações da etiqueta nos metadados e ele ainda podem ser lidos por serviços que procure estas informações de etiqueta.

Além disso, se a etiqueta eliminada aplicada proteção, essa proteção não é removida. As definições de proteção de etiqueta permanecem e apresentar os **modelos de proteção** secção. Este modelo pode agora ser convertido para uma nova etiqueta. Enquanto este modelo permanece, não é possível criar uma nova etiqueta com o mesmo nome que a etiqueta que eliminou. Se quiser fazer isso, tem as seguintes opções:

- Converta o modelo numa etiqueta. 
    
    Esta ação é recomendada porque se for necessário, em seguida, pode alterar o nome do modelo e modificar as definições de proteção.

- Utilize o PowerShell para mudar o nome do modelo ou eliminá-lo.
    
    Antes de efetuar estas ações, considere se outros administradores ou serviços estão a utilizar o modelo ou usaram no passado. É possível identificar o modelo pelo respetivo ID de modelo que não é alterada, ou seu nome (que pode ser alterado). Como melhor prática, elimine um modelo apenas se tiver a certeza de que os utilizadores não terão que abrir documentos ou e-mails que foram protegidos pelo modelo.

Para obter mais informações sobre a gestão de modelos de proteção, consulte [configurando e gerenciando modelos do Azure Information Protection](configure-policy-templates.md).

Antes de eliminar uma etiqueta, em vez disso, considere desativá-lo ou removê-lo da política:
    
- Ao desativar uma etiqueta que foi aplicada a documentos e e-mails, a etiqueta aplicada não é removida destes documentos e e-mails. A etiqueta permanece na política, mas já não é apresentado como uma etiqueta que os utilizadores podem selecionar na barra do Information Protection. Desativar uma etiqueta permite-lhe manter a configuração original para quando quiser que os utilizadores na mesma política que selecionem a etiqueta mais tarde, quando simplesmente voltar a ativar a etiqueta.

- Quando remover uma etiqueta de uma política, a etiqueta aplicada também não é removida destes documentos e e-mails. Mas, ao remover a etiqueta da política, torna-se disponíveis para adicionar esta etiqueta à política de outro. Para obter mais informações, consulte [adicionar ou remover uma etiqueta de ou para uma política do Azure Information Protection](configure-policy-add-remove-label.md).

Ordene as etiquetas para que os utilizadores visualizem uma progressão lógica na barra Information Protection. Por exemplo, ordenar as etiquetas de acordo com o aumento de confidencialidade para que os utilizadores vejam a etiqueta menos confidencial em primeiro e a etiqueta mais confidencial em último. A [política predefinida](configure-policy-default.md) utiliza esta configuração e reflete o aumento de confidencialidade nos nomes das etiquetas.

> [!IMPORTANT]
>Se configurar [condições](configure-policy-classification.md) para as etiquetas que podem ser aplicadas a mais do que uma etiqueta, deve ordenar as etiquetas desde a menos confidencial à mais confidencial. Esta ordem garante que a etiqueta mais confidencial é aplicada quando são condições são avaliadas.


Utilize as seguintes instruções para efetuar as alterações.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção de menu: Sobre o **do Azure Information Protection – etiquetas** painel, efetue um ou mais das seguintes ações: 

    - Para eliminar uma etiqueta: Faça duplo clique ou selecione o menu de contexto (**...** ) para a etiqueta que pretende eliminar, clique em **eliminar esta etiqueta**e clique em **OK** para confirmar. 

    - Para desativar uma etiqueta: Selecione a etiqueta que pretende desativar. Sobre o **etiqueta** painel, para **ativado**, selecione **desativar**e, em seguida, clique em **guardar**.

    - Para reordenar uma etiqueta: Faça duplo clique ou selecione o menu de contexto (**...** ) para a etiqueta que pretende reordenar, clique em **mover para cima** ou **mover para baixo** até que a etiqueta esteja na ordem em que desejar.  

## <a name="next-steps"></a>Passos Seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  


