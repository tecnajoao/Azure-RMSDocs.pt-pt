---
title: "Passo 1 do tutorial de início rápido – AIP"
description: "Passo 1 de um tutorial de introdução para experimentar o Azure Information Protection rapidamente – Ativar o serviço Azure Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
translationtype: Human Translation
ms.sourcegitcommit: 611b65589bdd8aa495fbfbd4a67c30a5fb9c387a
ms.openlocfilehash: aa1808503e92d0afeb7c0f3f7f9da446d2f13b51
ms.lasthandoff: 03/01/2017


---

# <a name="step-1-activate-the-rights-management-service"></a>Passo 1: ativar o serviço Rights Management
 
>*Aplica-se a: Azure Information Protection*

> [!NOTE]
>Se já ativou o serviço Azure Rights Management para o seu inquilino, avance diretamente para o [passo seguinte](infoprotect-tutorial-step2.md). 

Quando o serviço Azure Rights Management for ativado, poderá proteger os e-mails e os documentos mais confidenciais da sua organização e controlar a forma como os documentos protegidos são utilizados quando os partilhar com outras pessoas. Existem diferentes formas de ativar este serviço, que incluem a utilização do Windows PowerShell e a navegação nos portais de administração.

Para este tutorial, iremos diretamente para a página de ativação para administradores do Office 365, que é a mesma página do portal clássico do Office 365 e da pré-visualização do centro de administração do Office 365. 

Se preferir navegar para esta página a partir do seu portal de administração do Office 365, em vez de ir diretamente para a página, veja as instruções completas em [Ativar o Azure Rights Management](../deploy-use/activate-service.md). Além disso, utilize estas instruções completas se tiver acesso ao portal do Azure, mas não ao portal de administração do Office 365.

## <a name="to-activate-the-rights-management-service"></a>Para ativar o serviço Rights Management

1. Abra uma nova janela do browser e aceda diretamente à [página de ativação do Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) para administradores do Office 365.
    
    Se lhe for pedido para iniciar sessão, utilize uma conta que seja um administrador global do Office 365.

2. Na página **rights management**, clique em **ativar**.

3. Quando lhe for perguntado **Pretende ativar o Rights Management?**, clique em **ativar**.

    Já deverá estar visível **O Rights Management encontra-se ativado** e a opção para desativar (poderá ter de atualizar manualmente a página)

    Neste momento, não clique em **funcionalidades avançadas**. Isto leva-o para o portal clássico do Azure onde poderá configurar modelos personalizados, que não são necessários para este tutorial. Em vez disso, pode fechar esta página.

É tudo o que precisa de fazer neste primeiro passo para concluir este tutorial. Para uma implementação de produção, provavelmente, será útil configurar modelos personalizados como suplemento ou em vez de modelos predefinidos do Azure Rights Management. No entanto, os modelos personalizados não são necessários para este tutorial, pelo que pode ir para o passo 2.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Como ativar o Azure Rights Management|[Ativar o Azure Rights Management](../deploy-use/activate-service.md)|
|Acerca dos modelos predefinidos e de como criar modelos novos e personalizados|[Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md)|

>[!div class="step-by-step"]
[&#171; Introdução](infoprotect-quick-start-tutorial.md)
[Passo 2 &#187;](infoprotect-tutorial-step2.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

