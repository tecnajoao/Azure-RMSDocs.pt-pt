---
title: Alterar uma etiqueta do Azure Information Protection
description: "Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-os na política do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: 343b38caa14d3f67a932eedae37ed10c55f371ff
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2017
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Como alterar ou personalizar uma etiqueta existente para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-os na política do Azure Information Protection.

Por exemplo, pode alterar um nome de etiqueta ou de uma etiqueta secundária, a descrição, a cor, a ordem, se aplica marcas visuais como um rodapé ou uma marca d'água, se aplica proteção do Azure Rights Management e classificação recomendada ou automática.

Para alterar uma etiqueta, utilize as instruções seguintes.

1. Se ainda não o tiver feito, abra uma nova janela do browser e inicie sessão para o [portal do Azure](https://portal.azure.com) como um administrador de segurança ou um administrador global. Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Para alterar uma etiqueta da política global para que o se aplica a todos os utilizadores, selecione a etiqueta a alterar o **Azure Information Protection - política Global** painel e em quaisquer painéis subsequentes, conforme necessário. Para alterar uma etiqueta de um [âmbito política](configure-policy-scope.md) para que o se aplica apenas a utilizadores selecionados, primeiro selecione **âmbito políticas** do **políticas** selecção de menu. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

    A exceção é se pretender reordenar uma etiqueta, procedimento que é feito no painel da política a partir da política global ou da sua política de âmbito selecionada: clique com o botão direito do rato na etiqueta ou selecione o menu de contexto da etiqueta e, em seguida, selecione as opções **Mover para cima** ou **Mover para baixo**.

3. Sempre que efetuar alterações num painel, caso pretenda manter as alterações, clique em **Guardar** nesse mesmo painel.

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

5. Se alterou o nome da etiqueta ou a descrição e tiver configurado estes para idiomas adicionais, deve exportar novamente a política do Azure Information Protection, apresentar novas traduções e importar as alterações. Para obter mais informações, veja [Como configurar etiquetas para diferentes idiomas](configure-policy-languages.md).

> [!TIP]
>Se pretender regressar a um dos rótulos predefinidos para os valores predefinidos, utilize as informações em [Política do Information Protection predefinida](configure-policy-default.md).

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar as opções que pode efetuar em relação a uma etiqueta e outras definições para a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


