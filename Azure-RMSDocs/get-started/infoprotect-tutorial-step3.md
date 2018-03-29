---
title: Passo 3 do tutorial de início rápido – AIP
description: Passo 3 de um tutorial de introdução para experimentar o Azure Information Protection rapidamente – Instalar o cliente.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/18/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
ms.openlocfilehash: 363902fac8036b118ce28c3ea87c812e262c3d47
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="step-3-install-the-client"></a>Passo 3: instalar o cliente

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Neste passo, irá instalar o cliente Azure Information Protection, para que a política que acabou de configurar seja transferida para um PC com Windows e apresentar as etiquetas em aplicações do Office.


## <a name="install-the-azure-information-protection-client"></a>Instalar o cliente do Azure Information Protection

1. Num PC com o Office instalado (mas não está actualmente aberto Word), visite o [Centro de transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) e transferir **AzInfoProtection.exe**.
    
2. Executar o executável que acabou de transferir e siga as instruções para instalar o cliente.
    
    Para este tutorial, não interessa se selecionou a opção para instalar uma política de demonstração, porque a nossa política que transferimos vai ser transferida do Azure e substituir a política de demonstração, caso esteja instalada. No entanto, pode utilizar a opção de política de demonstração caso pretenda experimentar as etiquetas predefinidas sem ligar ao Azure Information Protection. 

## <a name="verify-the-installation"></a>Verificar a instalação

Verifique se a instalação foi bem-sucedida ao abrir o Word e um novo documento em branco (não o guarde por agora). Se lhe for pedido para introduzir o seu nome de utilizador e palavra-passe, introduza os detalhes da sua conta de administrador global. 

Se esta é a primeira vez que instala o cliente, verá a página **Parabéns** com instruções básicas. Depois de a ler, clique em **Fechar**.

Quando o documento é carregado, deve ver duas novas opções:

![Passo 3 do tutorial de início rápido do Azure Information Protection – cliente instalado](../media/word2016-calloutsv2.png)

- No separador **Base**, um novo grupo **Proteção**, com um botão com o nome **Proteger**.
    
    Clique em **Proteger** > **Ajuda e Feedback** e, na caixa de diálogo **Microsoft Azure Information Protection**, confirme o estado do cliente. Deverá apresentar **Ligado como** e o seu nome de utilizador. Além disso, também deverá ver uma hora e data recentes para a última ligação e quando a política do Information Protection foi instalada. Verifique se o seu nome de utilizador apresentado está correto para o seu inquilino.

- Uma nova barra abaixo do friso; a barra do Information Protection. Apresenta o título da **sensibilidade**e as etiquetas que vimos no portal do Azure. 

Agora está pronto para ver o Azure Information Protection em ação.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Sobre instalar o cliente do Azure Information Protection|[Transferir e instalar o cliente do Azure Information Protection](../rms-client/install-client-app.md)|
|Instruções de administrador para o cliente do Azure Information Protection|[Guia do administrador de clientes do Azure Information Protection](../rms-client/client-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; Passo 2](infoprotect-tutorial-step2.md)
[Passo 4 &#187;](infoprotect-tutorial-step4.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]