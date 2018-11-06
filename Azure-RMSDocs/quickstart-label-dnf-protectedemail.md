---
title: Início rápido - configurar uma etiqueta para os utilizadores a proteger facilmente os e-mails que contêm informações confidenciais
description: Configure uma etiqueta que protege um e-mail para um utilizador ao aplicar automaticamente a proteção não reencaminhar.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 6beb55b6dbcd82582cc24c7beb787bf4b232f518
ms.sourcegitcommit: 80de8762953bdea2553c48b02259cd107d0c71dd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51027198"
---
# <a name="quickstart-configure-a-label-for-users-to-easily-protect-emails-that-contain-sensitive-information"></a>Início rápido: Configurar uma etiqueta para os utilizadores a proteger facilmente os e-mails que contêm informações confidenciais

Neste início rápido, irá configurar uma etiqueta existente para aplicar automaticamente a definição de proteção não reencaminhar.

A política do Azure Information Protection atual já contém duas etiquetas que têm esta configuração:

- **Confidencial \ apenas Recetores**

- **Altamente confidencial \ apenas Recetores**

No entanto, se a política é mais antiga ou se a proteção não estava ativada no momento foi criada a política da sua organização, não precisará estas etiquetas. 

Pode concluir esta configuração em 5 minutos.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este início rápido, precisa de:

1. Uma subscrição que inclui o Azure Information Protection plano 1 ou plano 2.
    
    Se não tiver uma destas subscrições, pode criar uma [gratuita](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) de conta para a sua organização.

2. Adicionei o painel do Azure Information Protection para o portal do Azure e confirmar que o serviço de proteção está ativado.

    Se precisar de ajuda com estas ações, veja [início rápido: começar a utilizar no portal do Azure](quickstart-viewpolicy.md).

3. Uma etiqueta do Azure Information Protection existente para configurar. 
    
    Pode utilizar as etiquetas predefinidas ou uma etiqueta que criou. Se precisar de obter ajuda na criação de uma nova etiqueta, veja [início rápido: criar uma nova etiqueta do Azure Information Protection para utilizadores específicos](quickstart-label-specificusers.md).

4. Para testar a nova etiqueta: cliente do Azure Information Protection tem de estar instalado nos computadores para os utilizadores. 
    
    Para experimentar a etiqueta para si próprio, pode instalar o cliente ao aceder a [Centro de transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) e transfira **AzInfoProtection.exe** da página do Azure Information Protection.

5. Para testar a nova etiqueta: um computador com Windows (no mínimo do Windows 7 com Service Pack 1), e neste computador, tem sessão iniciada para aplicações do Office de uma das seguintes categorias:
    
    - Office 365 com as aplicações do Office 2016 (versão mínima 1805, compilação 9330.2078). Para utilizar esta opção, a conta deve ser atribuída uma licença do Azure Rights Management. Esta licença é incluída na subscrição do Azure Information Protection.
    
    - O Office 365 ProPlus com aplicações de 2016 ou 2013 (instalação clique-e-Use ou baseada no Windows Installer).
    
    - Office Professional Plus 2016.
    
    - Office Professional Plus 2013 com Service Pack 1.
    
    - Office Professional Plus 2010 com Service Pack 2.

Para obter uma lista completa de pré-requisitos para utilizar o Azure Information Protection, consulte [requisitos do Azure Information Protection](requirements.md).

## <a name="configure-an-existing-label-to-apply-the-do-not-forward-protection"></a>Configurar uma etiqueta existente para aplicar a proteção não reencaminhar

1. Abra uma nova janela do browser e [inicie sessão no portal do Azure](https://portal.azure.com). Em seguida, navegue até **do Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção de menu: no **do Azure Information Protection – etiquetas** painel, selecione a etiqueta que pretende configurar para aplica a proteção. 

3. No painel **Etiqueta**, localize **Definir permissões para documentos e e-mails que contêm esta etiqueta**. Selecione **proteger**e, em seguida **proteção**:
    
    ![Configurar a proteção para uma etiqueta do Azure Information Protection](./media/info-protect-protection-bar-configured.png).

4. Sobre o **proteção** painel, certifique-se de que **Azure (chave da cloud)** está selecionada.
    
5. Selecione **definir permissões definidas pelo utilizador (pré-visualização)**.

6. Certifique-se de que a seguinte opção está selecionada: **no Outlook aplicam-se não reencaminhar**.

7. Se selecionada, desmarque a opção seguinte: **no Word, Excel, PowerPoint e o Explorador de ficheiros pedir ao utilizador para permissões personalizadas**.

8. Clique em **OK** sobre o **proteção** painel e clique em **guardar** no **etiqueta** painel.

A etiqueta está agora configurada para apresentar apenas no Outlook e aplicar a proteção não reencaminhar para e-mails.

## <a name="test-your-new-label"></a>Testar a sua nova etiqueta

A etiqueta configurada apresenta apenas no Outlook e é adequada para e-mails enviados para qualquer destinatário fora da sua organização, quando o Exchange Online está configurado para o [novas capacidades de encriptação de mensagens do Office 365](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e).

1. No seu computador, abra o Outlook e crie uma nova mensagem de e-mail. Se o Outlook já estiver aberto, reinicie-o para forçar uma atualização de política.

2. Especifique os destinatários, algum texto para mensagem de e-mail e, em seguida, aplicar a etiqueta que acabou de criar. 
    
    A mensagem de e-mail é classificada de acordo com o nome de etiqueta e protegida com a restrição não reencaminhar.

3. Envie o e-mail. 

O resultado é que os destinatários não é possível reencaminhar o e-mail, imprimi-lo, copiá-lo ou guardar anexos ou guardar o e-mail como um nome diferente. A mensagem de e-mail protegidas pode ser lidos por nenhum utilizador, em qualquer dispositivo.

## <a name="clean-up-resources"></a>Limpar recursos

Se não pretender manter esta configuração e retornar a etiqueta, de modo que ele não se aplica a proteção, efetue o seguinte procedimento:

1. Do **classificações** > **etiquetas** opção de menu: no **do Azure Information Protection – etiquetas** painel, selecione a etiqueta que configurou. 

3. Sobre o **etiqueta** painel, localize **definir permissões para documentos e e-mails que contenham esta etiqueta**, selecione **não configurado**e selecione **guardar**.

## <a name="next-steps"></a>Passos Seguintes

Este guia de introdução inclui as opções de mínimo, de modo a que pode configurar rapidamente uma etiqueta que torna mais fácil para os utilizadores a proteger suas mensagens de correio eletrónico. No entanto, se a configuração é demasiado restritivo, ou restritivas não suficiente, veja as outras configurações de exemplo:

- [Etiqueta de e-mail protegidas que suporte permissões menos restritivas do que não reencaminhar](configure-policy-protection.md#example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward)

- [Etiqueta, que criptografa o conteúdo, mas não restringe quem pode acessá-lo](configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it)

Para obter instruções completas, como configurar uma etiqueta que aplica a proteção, consulte [como configurar uma etiqueta para proteção do Rights Management](configure-policy-protection.md). 