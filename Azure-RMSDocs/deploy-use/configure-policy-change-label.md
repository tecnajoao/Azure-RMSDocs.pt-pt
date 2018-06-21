---
title: Alterar uma etiqueta do Azure Information Protection
description: Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-os na política do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: a8c745ac51c34139792367d55c5a83592c191571
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32326264"
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Como alterar ou personalizar uma etiqueta existente para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem na proteção de informações de barra ou do **proteger** botão no friso Office, configurando as etiquetas no portal do Azure.

Por exemplo, pode alterar um nome de etiqueta ou sublabel, a descrição, a cor e a ordem. Pode alterar se a etiqueta aplica marcas visuais como um rodapé ou marca de água. Pode alterar também se aplica-se a etiqueta da proteção e classificação recomendada ou automática.

Para alterar uma etiqueta, utilize as instruções seguintes:

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção do menu: no **Azure Information Protection - etiquetas** painel, selecione a etiqueta que pretende alterar.

    A exceção é se pretende reordenar uma etiqueta: em vez de selecionar a etiqueta, clique com o botão direito a etiqueta ou selecione o menu de contexto para a etiqueta. Em seguida, selecione o **mover para cima** ou **mover para baixo** opções.

3. Sempre que efetuar alterações num novo painel, clique em **guardar** nesse mesmo se pretende manter as suas alterações.
    
    Ao clicar em **guardar**, as alterações são automaticamente disponibilizadas a utilizadores e serviços. Já não é uma opção de publicar separado.

4. Se tiver alterado o nome a apresentar etiqueta ou a descrição e o tiver configurado estes para idiomas adicionais: Exportar a política do Azure Information Protection novamente, forneça traduções novas e importar as alterações. Para obter mais informações, veja [Como configurar etiquetas para diferentes idiomas](configure-policy-languages.md).

> [!TIP]
>Se pretender regressar a um dos rótulos predefinidos para os valores predefinidos, utilize as informações em [Política do Information Protection predefinida](configure-policy-default.md).

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar as opções que pode efetuar em relação a uma etiqueta e outras definições para a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


