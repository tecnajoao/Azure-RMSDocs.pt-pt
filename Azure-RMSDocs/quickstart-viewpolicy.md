---
title: Início rápido - introdução ao Azure Information Protection no portal do Azure – AIP
description: Se a sua organização é totalmente nova para o Azure Information Protection, comece por aqui para adicionar o serviço para o portal do Azure, confirme o serviço de proteção é ativado e ver etiquetas e as definições de política.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/09/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: information-protection
ms.openlocfilehash: 1d857fc3282b0851e80765fe3f53a2315ed59b5f
ms.sourcegitcommit: 729b12e1219c6dbf1bb2a6cfa7239f24d1d13cc5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59364645"
---
# <a name="quickstart-get-started-with-azure-information-protection-in-the-azure-portal"></a>Início rápido: Introdução ao Azure Information Protection no portal do Azure

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Neste início rápido, vai adicionar o Azure Information Protection para o portal do Azure, confirme que o serviço de proteção é ativado, criar etiquetas predefinidas, se já não ter etiquetas e ver as definições de política do Azure Information Protection.

Pode concluir este início rápido em menos de 10 minutos.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este início rápido, precisa de:

- Uma subscrição que inclui o Azure Information Protection plano 1 ou plano 2.
    
    Se não tiver uma destas subscrições, pode criar uma [gratuita](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) de conta para a sua organização.

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

O serviço de proteção está agora ativado automaticamente para os novos clientes, mas é uma boa idéia para confirmar se que ele não precisa de ativar manualmente. 

1. Sobre o **do Azure Information Protection** painel, selecione **gerir** > **ativação de proteção**.

2. Confirme se a proteção está ativada para o seu inquilino: 
    
    - Se estiver ativada a proteção, verá a confirmação seguinte:
        
        ![Estado de proteção de informações do Azure para o Azure RMS](./media/info-protect-azurerms-activated.png)
        
    - Se não estiver ativada a proteção, verá que isto refletido nas informações de estado e a opção para ativar:
        
        ![Estado de proteção de informações do Azure para o Azure RMS](./media/info-protect-azurerms-deactivated.png)

3. Se a proteção não está ativada, selecione **Activate**. 

    Quando a ativação estar concluída, a barra de informações apresenta **ativação foi concluído com êxito**.

## <a name="create-labels---if-necessary"></a>Criar etiquetas - se necessário

Sua organização pode já ter etiquetas, porque foram criadas automaticamente para o seu inquilino ou porque tem etiquetas de sensibilidade no Centro de conformidade e segurança do Office 365, o Centro de segurança da Microsoft ou o Centro de conformidade da Microsoft. Vamos dar uma olhada:

1. Selecione **classificações** > **etiquetas**:
    
    Se vir a opção **gerar etiquetas predefinidas**, ainda não tem quaisquer etiquetas:
    
     ![O Azure Information Protection não existem etiquetas predefinidas](./media/info-protect-nodefaultlabels.png)
    
    Se não vir esta opção para gerar etiquetas predefinidas, já tem etiquetas, provavelmente semelhantes às mostradas na imagem seguinte, que são as etiquetas predefinidas do Azure Information Protection:
    
    ![Etiquetas de padrão do Azure Information Protection](./media/info-protect-defaultlabels.png)

2. Se tiver etiquetas, vá para a secção seguinte para ver as etiquetas. Se ainda não tiver as etiquetas, selecione essa opção para **gerar etiquetas predefinidas**.

4. Em seguida, para publicar as etiquetas para todos os utilizadores, a partir do **classificações** > **políticas** > **Global**:
    
    a. Selecione **adicionar ou remover etiquetas**.
    
    b. Do **política: Adicionar ou remover as etiquetas** painel, selecione todas as etiquetas e, em seguida, selecione **OK**.
    
    c. Novamente o **política: Painel global**, selecione **guardar**.

## <a name="view-your-labels"></a>Ver as etiquetas

Selecione **classificações** > **etiquetas**e alguns minutos ao se familiarizar com as etiquetas que são apresentados no **Azure Information Protection – etiquetas**  painel.

Se eles não ter um aspeto semelhantes às etiquetas na imagem da secção anterior, não estiver a utilizar etiquetas predefinidas do Azure Information Protection, mas as etiquetas que foram criadas a partir de segurança do Office 365 e o Centro de conformidade, a segurança do Microsoft 365 Center ou o Centro de conformidade do Microsoft 365.

> [!TIP]
> Se não pretender utilizar as suas etiquetas personalizadas, mas em vez disso, utilize etiquetas predefinidas do Azure Information Protection: 
> - Eliminar as etiquetas personalizadas e, em seguida, ver a opção para gerar etiquetas predefinidas no **etiquetas** painel, conforme descrito no [seção anterior](#create-labels---if-necessary). 

Partir do **do Azure Information Protection – etiquetas** painel:

- As etiquetas predefinidas para classificação são **pessoais**, **público**, **geral**, **confidencial**, e **elevada Confidencial**. As últimas duas etiquetas se expandem para mostrar subetiquetas, que fornecem exemplos de como uma classificação pode ter subcategorias.

- Partir do **marcar** e **PROTEÇÃO** colunas, pode ver que algumas etiquetas têm marcas visuais configuradas. As marcas visuais são um rodapé, cabeçalho e marca d'água. Algumas etiquetas também podem ter a proteção definida. 

Por exemplo: 

![Descrição geral da Azure início rápido de proteção de informações de etiquetas predefinidas](./media/info-protect-policy-default-labelsv2.png)

Se selecionar uma etiqueta, pode ver detalhes para essa configuração de etiqueta num novo painel.

## <a name="view-your-policy-settings"></a>Ver as definições de política

Na primeira vez que ligar para o serviço Azure Information Protection com o portal do Azure, as definições predefinidas são sempre criadas para si que são utilizados pelo cliente do Azure Information Protection. Para este cliente, as definições de política e as etiquetas visualizamos são transferidas para o cliente na política do Azure Information Protection.

Se estiver a utilizar o cliente de etiquetagem unificado do Azure Information Protection, este cliente não utiliza estas definições de política. Em vez disso, este cliente transfere etiquetas e as definições de política da conformidade do Office 365 e o Centro de segurança, o Centro de conformidade do Microsoft 365 ou o Centro de segurança do Microsoft 365.

Para ver as definições de política do Azure Information Protection predefinida:

1. Selecione **classificações** > **políticas** > **Global** para apresentar as definições de política do Azure Information Protection predefinida que são criado para o seu inquilino.
    
2. Depois das etiquetas, no **configurar definições para apresentar e aplicar-se sobre os usuários finais do Information Protection** secção, pode ver as definições de política. Por exemplo, não existe nenhum conjunto de etiqueta predefinida, documentos e e-mails não têm de ter uma etiqueta e os utilizadores não têm de fornecer uma justificação ao alterar as etiquetas:
    
    ![Definições globais da política do Azure Information Protection](./media/info-protect-policy-default-settingsv3.png)

3. Uma vez que está a ver apenas as definições, pode fechar todos os painéis no portal do que abriu.

## <a name="next-steps"></a>Passos Seguintes

Agora que já viu as etiquetas predefinidas e definições de política no portal do Azure, poderá considerar o tutorial seguinte úteis como o próximo passo: [Editar a política e criar uma nova etiqueta do Azure Information Protection](infoprotect-quick-start-tutorial.md).

Em alternativa, para obter instruções detalhadas para configurar todos os aspetos da política do Azure Information Protection, consulte [configurar a política do Azure Information Protection](configure-policy.md).
