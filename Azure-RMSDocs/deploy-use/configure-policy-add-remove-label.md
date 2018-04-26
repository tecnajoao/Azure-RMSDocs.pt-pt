---
title: Adicionar ou remover uma etiqueta de ou para uma política do Azure Information Protection
description: Adicionar ou remover uma etiqueta de Azure Information Protection para ou da política global para todos os utilizadores, ou para ou a partir de uma política de âmbito para um subconjunto de utilizadores.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0546cc11-67a5-4194-8c54-f3ac8ce9ebe1
ms.openlocfilehash: 73152d2202096775d315f874b30269c89213f8e1
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2018
---
# <a name="add-or-remove-a-label-to-or-from-an-azure-information-protection-policy"></a>Adicionar ou remover uma etiqueta de ou para uma política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

>[!NOTE]
> Este artigo reflete as atualizações mais recentes para o portal do Azure, que permitem-lhe criar uma etiqueta de forma independente da política de global ou de uma política de âmbito. A opção de publicar as políticas também é removida. Se o inquilino é ainda não atualizado para que estas alterações — por exemplo, pode ainda ver um **publicar** opção para o Azure Information Protection e não vir o **classificações** opção do menu — Aguarde alguns dias e em seguida, regresse a estas instruções.  

Depois de criar uma etiqueta de Azure Information Protection, pode, em seguida, adicioná-la a uma política para que fique disponível para os utilizadores. Se a etiqueta para todos os utilizadores, adicione a etiqueta para a política global. Se a etiqueta é para um subconjunto de utilizadores, adicione a etiqueta a uma política de âmbito. Atualmente, uma etiqueta pode ser adicionada a apenas uma política. Para adicionar um sublabel, a etiqueta principal tem de ser na mesma política ou na política de global.

Para etiquetas que já estão a ser uma política, pode removê-los da política. Esta ação não elimina a etiqueta. Permanece disponível para ser utilizado em outra política.

Se ainda não criou a etiqueta, consulte o artigo [como criar uma nova etiqueta para o Azure Information Protection](configure-policy-new-label.md).

Se precisar de criar uma política de âmbito para que a etiqueta aplica-se a um subconjunto de utilizadores, consulte [como configurar a política do Azure Information Protection para utilizadores específicos através da utilização de políticas de âmbito](configure-policy-scope.md).

## <a name="to-add-or-remove-a-label-to-or-from-a-policy"></a>Para adicionar ou remover uma etiqueta de ou para uma política

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **políticas** opção do menu: no **Azure Information Protection** - **políticas** painel, selecione **Global** se a etiqueta para adicionar ou remover aplica-se a todos os utilizadores.

    Se a etiqueta para adicionar ou remover aplica-se a um subconjunto de utilizadores, selecione a política de âmbito em vez disso.

3. No **política** painel, selecione **etiquetas de adicionar ou remover**.

4. No **política: Adicionar ou remover etiquetas** painel, pode ver todas as etiquetas com uma caixa de verificação selecionada se que já estão a ser uma política e o nome da política correspondente no **política** coluna.
     
    Apresentar sublabels como avanços. No âmbito, uma política de etiquetas que são herdadas da política global apresentam como indisponíveis.
    
    Efetue um ou mais das seguintes ações e, em seguida, clique em **OK**:
    
    - Para adicionar uma etiqueta, selecione-, que adiciona uma caixa de verificação selecionada.
    
    - Para remover uma etiqueta, desmarque a caixa de verificação.
  
5. Para guardar as alterações, clique em **Guardar**.
   
    As alterações são automaticamente disponibilizadas a utilizadores e serviços. Já não é uma opção de publicar separado.


## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
