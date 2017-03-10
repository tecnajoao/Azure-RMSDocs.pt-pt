---
title: Alterar uma etiqueta do Azure Information Protection
description: "Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-os na política do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: e800818f87ab5b0b39ffdc244f871c04305039ae
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Como alterar ou personalizar uma etiqueta existente para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Pode alterar ou refinar qualquer uma das etiquetas que os utilizadores veem na barra Information Protection, configurando-os na política do Azure Information Protection.

Por exemplo, pode alterar um nome de etiqueta ou de uma etiqueta secundária, a descrição, a cor, a ordem, se aplica marcas visuais como um rodapé ou uma marca d'água, se aplica proteção do Azure Rights Management e classificação recomendada ou automática.

Para alterar uma etiqueta, utilize as instruções seguintes.


1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global e navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Para alterar uma etiqueta da política global, de modo a que se aplique a todos os utilizadores, selecione a etiqueta a alterar no painel **Política:Global** e, em seguida, faça as alterações no painel **Etiqueta** e em todos os painéis subsequentes, conforme necessário. Para alterar uma etiqueta a partir de uma [política de âmbito](configure-policy-scope.md) para que se aplique a utilizadores selecionados, selecione primeiro essa política no painel inicial do **Azure Information Protection**.

    A exceção é se pretender reordenar uma etiqueta, procedimento que é feito no painel da política a partir da política global ou da sua política de âmbito selecionada: clique com o botão direito do rato na etiqueta ou selecione o menu de contexto da etiqueta e, em seguida, selecione as opções **Mover para cima** ou **Mover para baixo**.

3. Sempre que efetuar alterações num painel, caso pretenda manter as alterações, clique em **Guardar** nesse mesmo painel.

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

> [!TIP]
>Se pretender regressar a um dos rótulos predefinidos para os valores predefinidos, utilize as informações em [Política do Information Protection predefinida](configure-policy-default.md).

## <a name="next-steps"></a>Passos seguintes

Para mais informações sobre como configurar as opções que pode efetuar em relação a uma etiqueta e outras definições para a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


