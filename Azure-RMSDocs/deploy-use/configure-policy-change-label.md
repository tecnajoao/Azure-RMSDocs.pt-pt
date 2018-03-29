---
title: Alterar uma etiqueta do Azure Information Protection
description: Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-os na política do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: aac1d87fb76848e31a21a046f14442293d29aa9f
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Como alterar ou personalizar uma etiqueta existente para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-os na política do Azure Information Protection.

Por exemplo, pode alterar um nome de etiqueta ou sublabel, a descrição, a cor e a ordem. Pode alterar se a etiqueta aplica marcas visuais como um rodapé ou marca de água. Pode alterar também se aplica-se a etiqueta da proteção e classificação recomendada ou automática.

Para alterar uma etiqueta, utilize as instruções seguintes:

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Para alterar uma etiqueta da política global para que o se aplica a todos os utilizadores, selecione a etiqueta a alterar o **Azure Information Protection - política Global** painel e em quaisquer painéis subsequentes, conforme necessário. Para alterar uma etiqueta de um [âmbito política](configure-policy-scope.md) para que o se aplica apenas a utilizadores selecionados, primeiro selecione **âmbito políticas** do **políticas** selecção de menu. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

    A exceção é se pretende reordenar uma etiqueta. No painel de política de política global ou a política de âmbito selecionada: O botão direito do rato a etiqueta ou selecione o menu de contexto para a etiqueta. Em seguida, selecione o **mover para cima** ou **mover para baixo** opções.

3. Sempre que efetuar alterações num painel, caso pretenda manter as alterações, clique em **Guardar** nesse mesmo painel.

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

5. Se tiver alterado o nome a apresentar etiqueta ou a descrição e o tiver configurado estes para idiomas adicionais: Exportar a política do Azure Information Protection novamente, forneça traduções novas e importar as alterações. Para obter mais informações, veja [Como configurar etiquetas para diferentes idiomas](configure-policy-languages.md).

> [!TIP]
>Se pretender regressar a um dos rótulos predefinidos para os valores predefinidos, utilize as informações em [Política do Information Protection predefinida](configure-policy-default.md).

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar as opções que pode efetuar em relação a uma etiqueta e outras definições para a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


