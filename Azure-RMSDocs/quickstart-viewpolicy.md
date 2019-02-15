---
title: Início rápido - introdução ao Azure Information Protection no portal do Azure – AIP
description: Se a sua organização é totalmente nova para o Azure Information Protection, comece por aqui para adicionar o serviço para o portal do Azure, confirme o serviço de proteção é ativado e ver a política.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/15/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.openlocfilehash: 3e4e81f7300f319f9fd5887cd859f43e58d60c10
ms.sourcegitcommit: 89d2c2595bc7abda9a8b5e505b7dcf963e18c822
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56266051"
---
# <a name="quickstart-get-started-with-azure-information-protection-in-the-azure-portal"></a>Início rápido: Introdução ao Azure Information Protection no portal do Azure

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Neste início rápido, vai adicionar o Azure Information Protection para o portal do Azure, confirme o serviço de proteção é ativado e ver a política de predefinida da sua organização. 

Pode concluir este início rápido em 5 minutos.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este início rápido, precisa de:

- Uma subscrição que inclui o Azure Information Protection plano 1 ou plano 2.
    
    Se não tiver uma destas subscrições, pode criar uma [gratuita](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) de conta para a sua organização.

Para obter uma lista completa de pré-requisitos para utilizar o Azure Information Protection, consulte [requisitos do Azure Information Protection](requirements.md).

## <a name="add-azure-information-protection-to-the-azure-portal"></a>Adicionar o Azure Information Protection para o portal do Azure

O Azure Information Protection não está automaticamente disponível no portal do Azure. Deve adicioná-lo.

1. Inicie sessão para o [portal do Azure](https://portal.azure.com) utilizando a conta de administrador global do seu inquilino. 
    
    Se não for o administrador global, utilize a seguinte hiperligação para funções de alternativas: [O início de sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal)

2. No hub menu, selecione **criar um recurso**e, em seguida, a partir da caixa de pesquisa para o Marketplace, escreva **do Azure Information Protection**. 
    
3. Na lista de resultados, selecione **do Azure Information Protection**. Em seguida, sobre o **do Azure Information Protection** painel, clique em **criar**.
    
    > [!TIP] 
    > Opcionalmente, selecione **afixar ao dashboard** para criar um **do Azure Information Protection** mosaico no dashboard, para que não terá de procurar para o serviço da próxima vez que iniciar sessão no portal.
    
    Clique em **criar** novamente.

## <a name="confirm-the-protection-service-is-activated"></a>Confirme que o serviço de proteção está ativado

O serviço de proteção agora é automaticamente ativado para novos inquilinos, mas é uma boa idéia para confirmar se que ele não precisa de ativar manualmente. 

1. Sobre o **do Azure Information Protection** painel, selecione **gerir** > **ativação de proteção**.

2. Confirme se a proteção está ativada para o seu inquilino: 
    
    - Se estiver ativada a proteção, verá a confirmação seguinte:
        
        ![Estado de proteção de informações do Azure para o Azure RMS](./media/info-protect-azurerms-activated.png)
        
    - Se não estiver ativada a proteção, verá que isto refletido nas informações de estado e a opção para ativar:
        
        ![Estado de proteção de informações do Azure para o Azure RMS](./media/info-protect-azurerms-deactivated.png)

3. Se a proteção não está ativada, selecione **Activate**. 

    Quando a ativação estar concluída, a barra de informações apresenta **ativação foi concluído com êxito**.

## <a name="view-your-organizations-default-policy---labels-and-policy-settings"></a>Ver a política predefinida da sua organização - etiquetas e as definições de política

Na primeira vez que ligar para o serviço Azure Information Protection com o portal do Azure, é criada uma política de padrão para o seu inquilino. A política predefinida contém etiquetas e as definições que pode utilizar como-é, ou personalizar.

1. Selecione **classificações** > **políticas** > **Global** para apresentar a política do Azure Information Protection predefinida criada para o o inquilino.
    
2. Passe alguns minutos, ao se familiarizar com as etiquetas que são apresentadas:
    
   - Etiquetas para classificação: **Pessoais**, **pública**, **geral**, **confidenciais**, e **altamente confidencial**. As últimas duas etiquetas se expandem para mostrar subetiquetas, que fornecem exemplos de como uma classificação pode ter subcategorias:
    
   - Com a configuração predefinida, algumas etiquetas não têm marcas visuais configuradas. As marcas visuais são um rodapé, cabeçalho e marca d'água. Dependendo da sua diretiva padrão, alguns rótulos, talvez também tenha proteção definida. Por exemplo: 
    
     ![Passo 3 do tutorial de início rápido do Azure Information Protection – política predefinida](./media/info-protect-policy-default-labelsv2.png)
    
3. Depois das etiquetas, no **configurar definições para apresentar e aplicar-se sobre os usuários finais do Information Protection** seção, também deve ver-se algumas definições de política. Por exemplo, não existe nenhum conjunto de etiqueta predefinida, documentos e e-mails não têm de ter uma etiqueta e os utilizadores não têm de fornecer uma justificação ao alterar as etiquetas:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – política predefinida](./media/info-protect-policy-default-settings-quickstart.png) 

4. Uma vez que só está a ver as definições e etiquetas, pode fechar todos os painéis que abriu.

## <a name="next-steps"></a>Passos Seguintes

Agora que já viu as etiquetas e as definições de política no portal do Azure, poderá considerar o tutorial seguinte úteis como o próximo passo: [Editar a política e criar uma nova etiqueta do Azure Information Protection](infoprotect-quick-start-tutorial.md).

Em alternativa, para obter instruções detalhadas para configurar todos os aspetos da política do Azure Information Protection, consulte [configurar a política do Azure Information Protection](configure-policy.md).
