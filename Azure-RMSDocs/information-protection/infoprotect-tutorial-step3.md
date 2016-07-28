---
title: "Tutorial de início rápido do Azure Information Protection, passo 3 | Azure Rights Management"
description: "Passo 3 de um tutorial de apresentação para experimentar rapidamente o Microsoft Azure Information Protection na sua organização com apenas 4 passos que devem demorar menos de 15 minutos."
author: cabailey
manager: mbaldwin
ms.date: 07/11/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: 7f85c673cd1e8055d6a27dcc49b5da18a7e12f98
ms.openlocfilehash: 41ebf56c55d94e9aecf9538d474c8fa2c77ae83e


---

# Passo 3: instalar o cliente do Azure Information Protection 

*Aplica-se a: pré-visualização do Azure Information Protection*

Neste passo, irá instalar o cliente Azure Information Protection, para que a política que acabou de configurar seja transferida para um PC com Windows e apresentar as etiquetas em aplicações do Office. 

1. Num PC com o Office instalado (mas sem o Word aberto), [transfira o cliente Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) a partir do Centro de transferências da Microsoft. 

2. Execute **AZInfoProtection.exe** e siga as instruções para instalar o cliente.

    Para este tutorial, não interessa se selecionou a opção para instalar uma política de demonstração, porque a nossa política que transferimos vai ser transferida do Azure e substituir a política de demonstração, caso esteja instalada. No entanto, pode utilizar a opção de política de demonstração caso pretenda experimentar as etiquetas predefinidas sem ligar ao Azure Information Protection. 

3. Verifique se o cliente foi instalado abrindo o Word e um novo documento em branco (não guarde-o neste momento). Se lhe for pedido para introduzir o seu nome de utilizador e palavra-passe, introduza os detalhes da sua conta de administrador global. Quando o documento é carregado, deve ver duas novas opções:

    - No separador **Home page**, um novo grupo **Proteção**, com um botão com a etiqueta **Proteger**.

        Clique em **Proteger** > **Ajuda e comentários** e, na caixa de diálogo **Microsoft Azure Information Protection**, confirme o estado do cliente. Deverá ser apresentado **A política de Information Protection está instalada** e um tempo de ligação recente. Verifique se o seu nome de utilizador apresentado está correto para o seu inquilino.

    - É apresentada uma nova barra abaixo do friso; a barra de Information Protection. Apresenta o título da **Sensibilidade** e a etiqueta predefinida que configurámos de **Interna**. 


![Tutorial de início rápido do Azure Information Protection, passo 3 - cliente instalado](../media/word2013-callouts.png)

Está pronto para o passo final, ver a classificação, etiquetagem e proteção em ação.

>[!div class="step-by-step"]
[&#171; Passo 2](infoprotect-tutorial-step2.md)
[Passo 4 &#187;](infoprotect-tutorial-step4.md)


<!--HONumber=Jul16_HO3-->


