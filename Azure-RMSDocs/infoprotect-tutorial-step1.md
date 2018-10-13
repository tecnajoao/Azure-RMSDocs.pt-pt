---
title: Passo 1 do tutorial de início rápido – AIP
description: Passo 1 de um tutorial de introdução para experimentar o Azure Information Protection rapidamente – a criação de ativar o serviço de proteção.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/28/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: af3958d7c3bafc37772944e2cb39a9b3244eccc2
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169979"
---
# <a name="step-1-activate-protection"></a>Passo 1: Ativar proteção
 
>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
>Mesmo que a proteção é ativada para o seu inquilino, conclua este passo para confirmar o estado de ativação. As instruções incluem o início de sessão no portal do Azure e criar o painel do Azure Information Protection, para que está pronto para o passo 2.

Quando a proteção é ativada para o Azure Information Protection, pode proteger e-mails e documentos mais confidenciais da sua organização. Também pode controlar a forma como estes documentos protegidos são utilizados quando os partilhar com outras pessoas. 

Existem várias formas que pode ativar a proteção. Pode utilizar o PowerShell e portais de administração. Mas, neste tutorial, vamos utilizar o portal do Azure, o que é onde também configurar etiquetas para os utilizadores. 

## <a name="to-activate-protection"></a>Para ativar a proteção

1. Inicie sessão para o [portal do Azure](https://portal.azure.com) utilizando a conta de administrador global do seu inquilino. 
    
    Se não for o administrador global, pode utilizar um dos seguintes [funções administrativas](/azure/active-directory/active-directory-assign-admin-roles-azure-portal): **administrador do Information Protection** ou **administrador de segurança**.

2. No hub menu, selecione **criar um recurso**e, em seguida, a partir da caixa de pesquisa para o Marketplace, escreva **do Azure Information Protection**. 
    
3. Na lista de resultados, selecione **do Azure Information Protection**. Sobre o **do Azure Information Protection** painel, clique em **criar**.
    
    > [!TIP] 
    > Opcionalmente, selecione **afixar ao dashboard** para criar um **do Azure Information Protection** mosaico no dashboard, para que não terá de procurar para o serviço da próxima vez que iniciar sessão no portal.
    
    Clique em **criar** novamente.

4. Preste atenção às informações na página **Início rápido** que se abre automaticamente ao ligar ao serviço pela primeira vez. Pode regressar aqui mais tarde. Neste tutorial, selecione **Manage** > **ativação de proteção**. 

5. Agora, ver se a proteção está ativada para o seu inquilino. 
    
    - Se estiver ativada a proteção, verá a confirmação seguinte:
        
        ![Estado de proteção de informações do Azure para o Azure RMS](./media/info-protect-azurerms-activated.png)
        
    - Se não estiver ativada a proteção, verá que isto refletido nas informações de estado e a opção para ativar:
        
        ![Estado de proteção de informações do Azure para o Azure RMS](./media/info-protect-azurerms-deactivated.png)

6. Se a proteção não está ativada, selecione **Activate**. 

    Quando a ativação estar concluída, a barra de informações apresenta **ativação foi concluído com êxito**.

É tudo o que precisa de fazer neste primeiro passo para concluir este tutorial. Está pronto para ir para o passo 2.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Informações sobre a ativação de proteção|[Ativar o Azure Rights Management](activate-service.md)|


>[!div class="step-by-step"]
[&#171; Introdução](infoprotect-quick-start-tutorial.md)
[Passo 2 &#187;](infoprotect-tutorial-step2.md)

