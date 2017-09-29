---
title: "Passo 1 do tutorial de início rápido – AIP"
description: "Passo 1 de um tutorial de introdução rapidamente experimentar o Azure Information Protection-ativar o serviço de proteção."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: 91eb9ec61f4fa1ebd7aac3cf0c244878ef450bb9
ms.sourcegitcommit: faaab68064f365c977dfd1890f7c8b05a144a95c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2017
---
# <a name="step-1-activate-protection"></a>Passo 1: Ativar proteção
 
>*Aplica-se a: Azure Information Protection*

> [!NOTE]
>Mesmo se já tiver ativado o serviço Azure Rights Management para o seu inquilino, conclua este passo para confirmar o estado de ativação. As instruções incluem o início de sessão portal do Azure e criar painel do Azure Information Protection, para que esteja preparado para o passo 2. 

Quando o serviço Azure Rights Management for ativado, poderá proteger os e-mails e os documentos mais confidenciais da sua organização e controlar a forma como os documentos protegidos são utilizados quando os partilhar com outras pessoas. Existem várias formas que pode ativar a proteção, o que inclui utilizando o Windows PowerShell e utilizar os portais de admin.

Para este tutorial, iremos utilizar o portal do Azure, o que é onde também configurar as etiquetas para utilizadores. 

## <a name="to-activate-the-azure-rights-management-service"></a>Para ativar o serviço Azure Rights Management

1. Iniciar sessão para o [portal do Azure](https://portal.azure.com) como um administrador global ou o administrador de segurança para o seu inquilino.

2. No menu do hub, clique em **Novo** e, em seguida, na lista **MARKETPLACE**, selecione **Security + Identity**. 
    
3.  No **segurança + identidade** painel, do **aplicações em destaque** lista, selecione **Azure Information Protection**. Em seguida, no **Azure Information Protection** painel, clique em **criar**.
    
    Esta ação cria o **Azure Information Protection** painel para que a próxima vez que iniciar sessão no portal, pode selecionar o serviço do hub **mais serviços** lista. 
    
    > [!TIP] 
    > Selecione **Afixar ao dashboard** para criar um mosaico do **Azure Information Protection** no seu dashboard. Assim, não terá de procurar o serviço da próxima vez que iniciar sessão no portal.

4. Preste atenção às informações na página **Início rápido** que se abre automaticamente ao ligar ao serviço pela primeira vez. Pode regressar aqui mais tarde. Para este tutorial, selecione **ativação da proteção**. 

5. Pode agora ver se o serviço do Azure Rights Management está ativado para o seu inquilino. 
    
    - Se o serviço está ativado, consulte a confirmação do seguinte:
        
        ![Estado de proteção de informações do Azure para o Azure RMS](../media/info-protect-azurerms-activated.png)
        
    - Se o serviço não está ativado, consulte que este serão refletidas nas informações de estado e a opção para ativar:
        
        ![Estado de proteção de informações do Azure para o Azure RMS](../media/info-protect-azurerms-deactivated.png)

6. Se o serviço não está ativado, selecione **ativar**. 

    Quando a ativação estiver concluída, a barra de informações apresenta **ativação foi concluído com sucesso**.

É tudo o que precisa de fazer neste primeiro passo para concluir este tutorial. Está pronto para ir para o passo 2.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Como ativar o Azure Rights Management|[Ativar o Azure Rights Management](../deploy-use/activate-service.md)|


>[!div class="step-by-step"]
[&#171; Introdução](infoprotect-quick-start-tutorial.md)
[Passo 2 &#187;](infoprotect-tutorial-step2.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
