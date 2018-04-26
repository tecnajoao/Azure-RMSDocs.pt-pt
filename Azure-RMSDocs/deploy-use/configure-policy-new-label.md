---
title: Nova etiqueta do Azure Information Protection
description: Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: e36daed0dafe970a273d153512387dda9c1dca40
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2018
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Como criar uma nova etiqueta para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

>[!NOTE]
> Este artigo reflete as atualizações mais recentes para o portal do Azure, que permitem-lhe criar uma etiqueta de forma independente da política de global ou de uma política de âmbito. A opção de publicar as políticas também é removida. Se o inquilino é ainda não atualizado para que estas alterações — por exemplo, pode ainda ver um **publicar** opção para o Azure Information Protection e não vir o **classificações** opção do menu — Aguarde alguns dias e em seguida, regresse a estas instruções.

Apesar do Azure Information Protection vem com etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas.

Pode adicionar uma nova etiqueta ou adicionar um novo sublabel para uma etiqueta existente quando precisar de um nível adicional de classificação. Por exemplo, a etiqueta na última o [política predefinida](configure-policy-default.md), contém sublabels.

Ao criar a primeira sublabel para uma etiqueta, os utilizadores já não podem selecionar a original, a etiqueta principal. Se necessário, crie um novo sublabel para recriar as definições de etiqueta principal, para que os utilizadores podem aplicar as mesmas definições.

Utilize as seguintes instruções para adicionar uma nova etiqueta, que, em seguida, pode ser adicionada a uma política do Azure Information Protection.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção do menu: no **Azure Information Protection - etiquetas** painel, efetue uma das seguintes ações:
    
    - Para criar uma nova etiqueta: clique em **Adicionar uma nova etiqueta**.
    
    - Para criar um novo sublabel: faça duplo clique ou selecione o menu de contexto (**...** ) para a etiqueta que pretende criar um sublabel para e, em seguida, clique em **adicionar uma etiqueta secundária**.

4. No painel **Etiqueta** ou **Etiqueta secundária**, selecione as opções que pretende para esta nova etiqueta e, em seguida, clique em **Guardar**.
    
    Quando especificar um nome a apresentar, será impedido de especificação alguns carateres (por exemplo, uma barra invertida e "e" comercial) porque nem todos os serviços e aplicações que utilizam o Azure Information Protection podem suportar estes carateres. Para além dos carateres que estejam bloqueados, não especifique o **#** caráter.    
    
    Tenha em atenção que a cor preta é automaticamente atribuída às novas etiquetas. Selecione uma cor distinta na lista de cores ou introduza um código terno hexadecimal dos componentes RGB (vermelho, verde e azul) da cor. Por exemplo, **#DAA520**. Se precisar de uma referência para estes códigos, o artigo [Cores por Nome](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx) da documentação da MSDN é um ponto de partida útil. Poderá também encontrar estes códigos em muitos programas de edição de imagens, como o Microsoft Paint, onde pode selecionar uma cor personalizada a partir de uma paleta e os valores RGB são automaticamente apresentados.

5. Para disponibilizar a nova etiqueta aos utilizadores: do **classificações** > **políticas** opção de menu, selecione a política para conter a nova etiqueta, selecione **etiquetas de adicionar ou remover** , selecione a etiqueta do **política: Adicionar ou remover o painel de etiquetas**, selecione **OK**e, em seguida, selecione **guardar**.
    
    >[!TIP]
    >Para novas etiquetas, considere a adicioná-las pela primeira vez a uma política de âmbito que utiliza para fins de teste. Quando estiver satisfeito com os resultados, remover a etiqueta a este âmbito de teste e, em seguida, adicione a etiqueta para uma política que utilizar na produção.     
    
    Para obter mais informações sobre como adicionar etiquetas, consulte [como adicionar ou remover uma etiqueta](configure-policy-add-remove-label.md).
    
    As alterações são automaticamente disponibilizadas a utilizadores e serviços. Já não é uma opção de publicar separado.

6. Se pretender que esta nova etiqueta nome e descrição para apresentar em idiomas diferentes para os utilizadores: Siga os procedimentos [como configurar as etiquetas para idiomas diferentes](configure-policy-languages.md). 

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

