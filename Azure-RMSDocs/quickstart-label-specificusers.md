---
title: Início rápido - criar uma nova etiqueta do Azure Information Protection para utilizadores específicos – AIP
description: Criar e configurar uma nova etiqueta que classifica os documentos e e-mails para utilizadores específicos através da utilização de uma política de âmbito.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 1a8af09681411e49936c067c6161376c9d4f9f16
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023580"
---
# <a name="quickstart-create-a-new-azure-information-protection-label-for-specific-users"></a>Início rápido: Criar uma nova etiqueta do Azure Information Protection para utilizadores específicos

Neste início rápido, irá criar uma nova etiqueta que apenas utilizadores específicos, podem ver e aplicam-se para classificar e proteger os documentos e e-mails.

Esta configuração utiliza uma política de âmbito.

Pode concluir esta configuração em menos de 10 minutos.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este início rápido, precisa de:

1. Uma subscrição que inclui o Azure Information Protection plano 1 ou plano 2.
    
    Se não tiver uma destas subscrições, pode criar uma [gratuita](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) de conta para a sua organização.

2. Adicionei o painel do Azure Information Protection para o portal do Azure e confirmar que o serviço de proteção está ativado.

    Se precisar de ajuda com estas ações, veja [início rápido: começar a utilizar no portal do Azure](quickstart-viewpolicy.md).

3. Um grupo com capacidade de receber notificações por e-mail no Azure AD que contém os utilizadores que irão ver e aplicar a nova etiqueta.
    
    Se não tiver um grupo adequado, crie uma com o nome **equipa de vendas** e adicione pelo menos um utilizador.

4. Para testar a nova etiqueta: cliente do Azure Information Protection tem de estar instalado nos computadores para os utilizadores. 
    
    Para experimentar a etiqueta para si próprio, pode instalar o cliente ao aceder a [Centro de transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) e transfira **AzInfoProtection.exe** da página do Azure Information Protection.

Para obter uma lista completa de pré-requisitos para utilizar o Azure Information Protection, consulte [requisitos do Azure Information Protection](requirements.md).
    
## <a name="create-a-new-label"></a>Criar uma nova etiqueta

Primeiro, crie a sua nova etiqueta.

1. Se ainda não o tiver feito, abra uma nova janela do browser e iniciar sessão para o [portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.
    
    Se não for o administrador global, utilize a seguinte hiperligação para funções de alternativas: [o início de sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal)

2. Do **classificações** > **etiquetas** opção de menu: no **do Azure Information Protection – etiquetas** painel, clique em **adicionar uma nova etiqueta** .

3. Sobre o **etiqueta** painel, especifique, pelo menos, o seguinte:
    
    - **Nome a apresentar etiqueta**: um nome para a nova etiqueta que será apresentada aos utilizadores e que identifica a classificação para o conteúdo. Por exemplo: `Sales - Restricted`.
    
    - **Descrição**: uma dica de ferramenta para ajudar os utilizadores a identificar quando selecionar esta nova etiqueta. Por exemplo: `Business data that is restricted to the Sales Team.`

4. Certifique-se de que **Enabled** está definida como **no** (predefinição) e selecione **guardar**.

## <a name="add-the-label-to-a-new-scoped-policy"></a>Adicione a etiqueta para uma nova política de âmbito

Agora, adicione a etiqueta criada recentemente para uma nova política de âmbito.

1. Do **classificações** > **políticas** opção de menu: no **do Azure Information Protection - políticas** painel, selecione **adicionar um novo política**. 

2. Sobre o **política** painel, para o **nome da política** , introduza um nome que identifica o grupo de utilizadores que irão ver a nova etiqueta criada. Por exemplo, `Sales`.

3. Selecione a opção **selecionar quais os utilizadores ou grupos recebem esta política**.

4. Sobre o **AAD utilizadores e grupos** painel, selecione **utilizadores/grupos**. Em seguida, no novo **utilizadores/grupos** painel, procure e selecione o grupo que identificou nos pré-requisitos. Por exemplo, **equipa de vendas**. Clique em **selecionar** nesse mesmo painel e, em seguida **OK**.

5. Novamente o **diretiva** painel, selecione **etiquetas de adicionar ou remover**.

6. Sobre o **política: Adicionar ou remover as etiquetas** painel, selecione a etiqueta que criou, por exemplo, **vendas - restringidas**e, em seguida, selecione **OK**.

7. Novamente o **diretiva** painel, selecione **guardar**. 

A nova etiqueta agora é publicada apenas para os membros do grupo que especificou. 

## <a name="test-your-new-label"></a>Testar a sua nova etiqueta

Para testar esta etiqueta, é necessário um mínimo de dois computadores porque o cliente do Azure Information Protection não suporta vários usuários no mesmo computador:

 - No seu computador primeiro, inicie sessão como um membro do grupo da equipa de vendas. Abra o Word e confirme que consegue ver a nova etiqueta. Se o Word já estiver aberto, reinicie-o para forçar uma atualização de política.

- No segundo computador, inicie sessão como um utilizador que não é um membro do grupo da equipa de vendas. Abra o Word e confirme que não é possível ver a nova etiqueta. Como antes, se o Word já estiver aberto, reiniciá-lo.

## <a name="clean-up-resources"></a>Limpar recursos

Se não pretender manter esta etiqueta e a política de âmbito, efetue o seguinte procedimento:

1. Do **classificações** > **políticas** opção de menu: no **do Azure Information Protection - políticas** painel, selecione o menu de contexto (**...** ) para a política de âmbito que acabou de criar. Por exemplo, **vendas**.

2. Selecione **Eliminar política** e, se lhe for pedido para confirmar, selecione **OK**.

3. Do **classificações** > **etiqueta** opção de menu: no **do Azure Information Protection – etiqueta** painel, selecione o menu de contexto (**...**) para a etiqueta que acabou de criar.  Por exemplo, **vendas - restringidas**.

4.  Selecione **eliminar esta etiqueta** e, se lhe for pedido para confirmar, selecione **OK**.


## <a name="next-steps"></a>Passos Seguintes

Este guia de introdução inclui as opções de mínimo, de modo que pode criar rapidamente uma nova etiqueta para utilizadores específicos. Para obter instruções completas, consulte os artigos seguintes:

- [Como criar uma nova etiqueta](configure-policy-new-label.md)

- [Como configurar a política para utilizadores específicos com políticas de âmbito](configure-policy-scope.md)

Além disso, se pretender que a etiqueta para proteger o conteúdo de forma a que apenas os membros da equipe de vendas poderiam abri-lo, terá de configurar a etiqueta para aplicar a proteção. Para obter instruções, consulte [como configurar uma etiqueta para proteção do Rights Management](configure-policy-protection.md).

