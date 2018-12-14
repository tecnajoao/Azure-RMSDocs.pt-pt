---
title: Nova etiqueta do Azure Information Protection – AIP
description: Apesar do Azure Information Protection ter etiquetas predefinidas que pode personalizar, também pode criar as suas próprias etiquetas que os utilizadores veem na barra Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ms.openlocfilehash: 7302e0e0e76f6ca94eba678390e7d938172e40c4
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305000"
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Como criar uma nova etiqueta para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Embora o Azure Information Protection inclui etiquetas predefinidas que pode personalizar, também pode criar suas próprias etiquetas.

Pode adicionar uma nova etiqueta ou adicionar uma nova subetiqueta a uma etiqueta existente quando precisar de um nível adicional de classificação. Por exemplo, a última etiqueta na [política predefinida](configure-policy-default.md), contém subetiquetas.

Ao criar a primeira subetiqueta para uma etiqueta, os utilizadores já não podem selecionar o original, a etiqueta principal. Se necessário, crie uma nova subetiqueta para recriar as definições de etiquetas de principal para que os utilizadores podem aplicar as mesmas definições.

Utilize as seguintes instruções para adicionar uma nova etiqueta que, em seguida, pode ser adicionada a uma política do Azure Information Protection.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção de menu: Sobre o **do Azure Information Protection – etiquetas** painel, escolha uma das seguintes ações:
    
    - Para criar uma nova etiqueta: Clique em **adicionar uma nova etiqueta**.
    
    - Para criar uma nova subetiqueta: Faça duplo clique ou selecione o menu de contexto (**...** ) para a etiqueta que pretende criar uma subetiqueta para e, em seguida, clique em **adicionar uma etiqueta secundária**.

4. No painel **Etiqueta** ou **Etiqueta secundária**, selecione as opções que pretende para esta nova etiqueta e, em seguida, clique em **Guardar**.
    
    Quando especificar um nome a apresentar, será impedido de especificação de alguns caracteres (por exemplo, uma barra invertida e "e" comercial) porque nem todos os serviços e aplicações que utilizam o Azure Information Protection podem suportar estes carateres. Além dos caracteres que são bloqueados, não especifique o **#** caráter.    
    
    Tenha em atenção que a cor preta é automaticamente atribuída às novas etiquetas. Selecione uma cor distinta na lista de cores ou introduza um código terno hexadecimal dos componentes RGB (vermelho, verde e azul) da cor. Por exemplo, **#DAA520**. Se precisar de uma referência para estes códigos, o artigo [Cores por Nome](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx) da documentação da MSDN é um ponto de partida útil. Poderá também encontrar estes códigos em muitos programas de edição de imagens, como o Microsoft Paint, onde pode selecionar uma cor personalizada a partir de uma paleta e os valores RGB são automaticamente apresentados.

5. Para tornar sua nova etiqueta disponível aos utilizadores: Partir do **classificações** > **políticas** menu opção, selecione a política para conter a nova etiqueta. Selecione **adicionar ou remover etiquetas**. Selecione a etiqueta do **política: Adicionar ou remover as etiquetas** painel, selecione **OK**e, em seguida, selecione **guardar**.
    
    >[!TIP]
    >Para novas etiquetas, considere a adicioná-los primeiro para uma política de âmbito que utilize para testes. Quando estiver satisfeito com os resultados, remover a etiqueta deste âmbito de teste e, em seguida, adicione a etiqueta a uma política que utilizar na produção.     
    
    Para obter mais informações sobre como adicionar etiquetas, consulte [como adicionar ou remover uma etiqueta](configure-policy-add-remove-label.md).
    
    As alterações estão automaticamente disponíveis para utilizadores e serviços. Já não existe uma opção de publicar separado.

6. Se pretender que este novo nome de etiqueta e descrição sejam apresentados em idiomas diferentes para os utilizadores: Siga os procedimentos [como configurar etiquetas para diferentes idiomas](configure-policy-languages.md). 

## <a name="next-steps"></a>Passos Seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  


