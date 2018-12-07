---
title: Adicionar ou remover uma etiqueta de ou para uma política do Azure Information Protection – AIP
description: Adicionar ou remover uma etiqueta do Azure Information Protection para ou da política global para todos os utilizadores, ou para ou a partir de uma política de âmbito para um subconjunto de utilizadores.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 0546cc11-67a5-4194-8c54-f3ac8ce9ebe1
ms.openlocfilehash: f097ec2f0e3db75d679e6c0a6251fb128f583d4b
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023313"
---
# <a name="add-or-remove-a-label-to-or-from-an-azure-information-protection-policy"></a>Adicionar ou remover uma etiqueta de ou para uma política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Depois de criar uma etiqueta do Azure Information Protection, pode, em seguida, adicioná-lo a uma política para que fique disponível para os utilizadores. Se a etiqueta é para todos os utilizadores, adicione a etiqueta para a política global. Se a etiqueta for para um subconjunto de utilizadores, adicione a etiqueta para uma política de âmbito. Atualmente, uma etiqueta pode ser adicionada a apenas uma política. Para adicionar uma subetiqueta, a etiqueta principal tem de ser na mesma política ou na política global.

Para etiquetas que já estão numa política, pode removê-lo da política. Esta ação não elimina a etiqueta. Continua a ser disponível para serem utilizados na outra política.

Se ainda não criou o rótulo, veja [como criar uma nova etiqueta do Azure Information Protection](configure-policy-new-label.md).

Se precisar de criar uma política de âmbito para que a etiqueta aplica-se a um subconjunto de utilizadores, consulte [como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito](configure-policy-scope.md).

## <a name="to-add-or-remove-a-label-to-or-from-a-policy"></a>Para adicionar ou remover uma etiqueta de ou para uma política

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **políticas** opção de menu: no **do Azure Information Protection** - **políticas** painel, selecione **Global** se a etiqueta para adicionar ou remover aplica-se a todos os utilizadores.

    Se a etiqueta para adicionar ou remover aplica-se a um subconjunto de utilizadores, selecione a política de âmbito.

3. Sobre o **diretiva** painel, selecione **adicionar ou remover etiquetas**.

4. Sobre o **política: Adicionar ou remover as etiquetas** painel, verá todas as suas etiquetas com uma caixa de verificação selecionada se eles já estão numa política e o nome da política correspondente no **política** coluna.
     
    Subetiquetas apresentam como recuada. Numa política de âmbito, as herdadas da política global são apresentadas como indisponível.
    
    Efetue um ou mais das seguintes ações e, em seguida, clique em **OK**:
    
    - Para adicionar uma etiqueta, selecioná-la, que adiciona uma caixa de verificação selecionada.
    
    - Para remover uma etiqueta, desmarque a caixa de verificação.
  
5. Para guardar as alterações, clique em **Guardar**.
   
    As alterações estão automaticamente disponíveis para utilizadores e serviços. Já não existe uma opção de publicar separado.


## <a name="next-steps"></a>Passos Seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

