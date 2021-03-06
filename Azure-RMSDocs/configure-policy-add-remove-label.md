---
title: Adicionar ou remover uma etiqueta de ou para uma política do Azure Information Protection – AIP
description: Adicionar ou remover uma etiqueta do Azure Information Protection para ou da política global para todos os utilizadores, ou para ou a partir de uma política de âmbito para um subconjunto de utilizadores.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/27/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 0546cc11-67a5-4194-8c54-f3ac8ce9ebe1
ms.openlocfilehash: 825161b85dd1999374eab61fa640ddb5a2a05953
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259206"
---
# <a name="add-or-remove-a-label-to-or-from-an-azure-information-protection-policy"></a>Adicionar ou remover uma etiqueta de ou para uma política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Depois de criar uma etiqueta do Azure Information Protection, pode, em seguida, adicioná-lo a uma política para que fique disponível para os utilizadores. Se a etiqueta é para todos os utilizadores, adicione a etiqueta para a política global. Se a etiqueta for para um subconjunto de utilizadores, adicione a etiqueta para uma política de âmbito. Pode ser adicionada uma etiqueta para apenas uma política. 

Para adicionar uma subetiqueta, a etiqueta principal tem de ser na mesma política ou na política global. Quando adicionar uma subetiqueta, as definições da etiqueta principal não são herdadas. Para os utilizadores que estão atribuídos a subetiqueta na sua política, a etiqueta principal é suportada apenas como um contêiner de apresentação para o nome e a cor. Neste cenário, as outras definições de configuração na etiqueta principal não são suportadas para marcas visuais, proteção e condições. Embora ainda pode configurá-las, essas definições na etiqueta principal são suportadas apenas para utilizadores que têm a etiqueta principal na sua política sem a subetiqueta.

Para etiquetas que já estão numa política, pode removê-lo da política. Esta ação não elimina a etiqueta. Continua a ser disponível para serem utilizados na outra política.

Se ainda não criou o rótulo, veja [como criar uma nova etiqueta do Azure Information Protection](configure-policy-new-label.md).

Se precisar de criar uma política de âmbito para que a etiqueta aplica-se a um subconjunto de utilizadores, consulte [como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito](configure-policy-scope.md).

## <a name="to-add-or-remove-a-label-to-or-from-a-policy"></a>Para adicionar ou remover uma etiqueta de ou para uma política

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **políticas** opção de menu: Sobre o **do Azure Information Protection** - **políticas** painel, selecione **Global** se a etiqueta para adicionar ou remover aplica-se a todos os utilizadores.

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
