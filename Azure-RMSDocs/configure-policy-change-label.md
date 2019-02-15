---
title: Alterar uma etiqueta do Azure Information Protection – AIP
description: Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-os na política do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/12/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: 1f40efbe102eb15cd62c616455414a26b1cd6c9f
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259087"
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Como alterar ou personalizar uma etiqueta existente para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem sobre a proteção de informações de barra ou a partir da **Protect** botão da faixa de opções do Office, ao configurar as etiquetas no portal do Azure.

Por exemplo, pode alterar um nome de etiqueta ou a subetiqueta, a descrição, a cor e a ordem. Pode alterar se a etiqueta se aplica marcas visuais como um rodapé ou marca d'água. Também pode alterar, se a etiqueta se aplica a proteção e classificação recomendada ou automática.

Para alterar uma etiqueta, utilize as instruções seguintes:

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção de menu: Sobre o **do Azure Information Protection – etiquetas** painel, selecione a etiqueta que pretende alterar.

    A exceção é se pretende reordenar uma etiqueta: Em vez de selecionar a etiqueta, com o botão direito a etiqueta ou selecione o menu de contexto para a etiqueta. Em seguida, selecione o **mover para cima** ou **mover para baixo** opções.

3. Sempre que efetuar alterações num novo painel, clique em **guardar** nesse mesmo painel se pretender manter as suas alterações.
    
    Quando clica em **guardar**, as suas alterações estão automaticamente disponíveis para utilizadores e serviços. Já não existe uma opção de publicar separado.

4. Se tiver alterado o nome a apresentar etiqueta ou a descrição e tiver configurado estes para idiomas adicionais: Exportar novamente a política do Azure Information Protection, apresentar novas traduções e importar as alterações. Para obter mais informações, veja [Como configurar etiquetas para diferentes idiomas](configure-policy-languages.md).

> [!TIP]
>Se pretender regressar a um dos rótulos predefinidos para os valores predefinidos, utilize as informações em [Política do Information Protection predefinida](configure-policy-default.md).

## <a name="next-steps"></a>Passos Seguintes

Para mais informações sobre como configurar as opções que pode efetuar em relação a uma etiqueta e outras definições para a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).



