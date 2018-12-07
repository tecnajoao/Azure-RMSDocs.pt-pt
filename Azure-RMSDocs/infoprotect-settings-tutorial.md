---
title: Tutorial - configurar definições de política do Azure Information Protection para ajudar a classificar documentos e e-mails – AIP
description: Um tutorial de introdução orienta-o através da configuração das definições de política do Azure Information Protection para ajudar a classificar documentos e e-mails da sua organização.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: tutorial
ms.service: information-protection
ms.openlocfilehash: 0341ba1b232551f89e1ee43f77a3425b8c6e8ffb
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024370"
---
# <a name="tutorial-configure-azure-information-protection-policy-settings-that-work-together"></a>Tutorial: Configurar definições de política do Azure Information Protection que funcionam em conjunto

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Neste tutorial, ficará a saber como:
> [!div class="checklist"]
> * Configurar definições de política que funcionam em conjunto
> * Consulte as definições em ação

Em vez de contar que os utilizadores manualmente etiquetar os documentos e e-mails, pode utilizar as definições de política para:

- Certifique-se de um nível básico de classificação de conteúdo novo e editado

- Informe os utilizadores sobre etiquetas e facilitam a aplicação a etiqueta correta

Pode concluir este tutorial em cerca de 15 minutos.

## <a name="prerequisites"></a>Pré-requisitos 

Para concluir este tutorial, precisa de:

1. Uma subscrição que inclui o Azure Information Protection plano 1 ou plano 2.
    
    Se não tiver uma subscrição que inclui este plano, pode criar uma [gratuita](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) de conta para a sua organização.

2. Adicionei o painel do Azure Information Protection para o portal do Azure e confirmar que o serviço de proteção está ativado.

    Se precisar de ajuda com estas ações, consulte o artigo [início rápido: adicionar o Azure Information Protection para o portal do Azure e ver a política](quickstart-viewpolicy.md)

3. O cliente do Azure Information Protection está instalado no seu computador. 
    
    Para instalar o cliente, vá para o [Centro de transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) e transfira **AzInfoProtection.exe** da página do Azure Information Protection.

4. Um computador com Windows (no mínimo do Windows 7 com Service Pack 1), e neste computador, tem sessão iniciada para aplicações do Office de uma das seguintes categorias:
    
    - Office 365 com as aplicações do Office 2016 (versão mínima 1805, compilação 9330.2078). Para utilizar esta opção, a conta deve ser atribuída uma licença do Azure Rights Management. Esta licença é incluída na subscrição do Azure Information Protection.
    
    - O Office 365 ProPlus com aplicações de 2016 ou 2013 (instalação clique-e-Use ou baseada no Windows Installer).
    
    - Office Professional Plus 2016.
    
    - Office Professional Plus 2013 com Service Pack 1.
    
    - Office Professional Plus 2010 com Service Pack 2.

Para obter uma lista completa de pré-requisitos para utilizar o Azure Information Protection, consulte [requisitos do Azure Information Protection](requirements.md).

Vamos começar.

## <a name="edit-the-azure-information-protection-policy"></a>Editar a política do Azure Information Protection

Em vez de contar que os utilizadores manualmente etiquetar os documentos e e-mails, pode utilizar algumas das definições de política para garantir um nível básico de classificação. 

Utilizar o portal do Azure, podemos irá editar a política global para alterar as definições de política para todos os utilizadores.

1. Abra uma nova janela do browser e inicie sessão para o [portal do Azure](https://portal.azure.com) como um administrador global. Em seguida, navegue até **do Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.
    
    Se não for o administrador global, utilize a seguinte hiperligação para funções de alternativas: [o início de sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal)

2. Selecione **classificações** > **políticas** > **Global** para abrir o **política: Global** painel. 

3. Localizar as definições de política depois das etiquetas, no **configurar definições para apresentar e aplicar-se sobre os usuários finais do Information Protection** secção. As definições podem ter valores diferentes para as que mostrado:
    
    ![Tutorial do Azure Information Protection - predefinições](./media/defaultsettings-aip.png)

4. Altere as definições de acordo com o valor na tabela seguinte. Tome nota das definições que alterar caso queira alterar volta novamente, quando tiver concluído este tutorial. 

    |Definição|Valor|Informações|
    |-------|-----|-----|
    |**Selecione a etiqueta predefinida**|**Geral**|Se não tiver uma etiqueta denominada **gerais**, selecione outra etiqueta na lista pendente. Sem etiqueta de documentos e e-mails terão esta etiqueta aplicada automaticamente como uma classificação de base. No entanto, os utilizadores podem alterar a etiqueta escolhida para outra.|
    |**Todos os documentos e e-mails devem ter uma etiqueta**|**no**|Esta definição é frequentemente referida como a etiquetagem obrigatório porque ele evita que os utilizadores de gravação de documentos ou e-mails que são sem etiqueta de envio. Em conjunto com a etiqueta predefinida, documentos e e-mails terá o rótulo padrão que definir, ou uma etiqueta que escolherem.
    |**Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos**|**Recomendado**|Esta definição solicita aos usuários para selecionarem uma etiqueta de classificação superior para seus e-mails mesmo quando eles anexar documentos que tenham uma classificação superior à sua etiqueta predefinidas selecionadas.
    |**Apresentar a barra de Information Protection nas aplicações do Office**|**no**|Apresentar a barra do Information Protection torna mais fácil para os utilizadores vejam e alterar a etiqueta predefinida.
    
    As definições devem agora ter um aspeto semelhante a esta:
    
    ![Tutorial do Azure Information Protection - predefinições alterados](./media/defaultsettings-aip-changed.png)

5. Selecione **salvar** nisso **política: Global** painel e se lhe for pedido para confirmar a ação, selecione **OK**. 

## <a name="see-your-policy-settings-in-action"></a>Consulte as definições de política em ação 

Para este tutorial, vamos utilizar Word e Outlook para ver as alterações de política em ação. Se estas aplicações já foram carregadas antes que alterou as definições de política, reiniciá-las para transferir as alterações.

### <a name="default-label-and-the-information-protection-bar"></a>Etiqueta predefinida e a barra do Information Protection

Abra um novo documento do Word. Verá o documento é identificado automaticamente como **gerais** em vez de contar os utilizadores selecionarem uma etiqueta. 

Com a barra do Information Protection apresentado e mostrar as etiquetas disponíveis, é fácil para os utilizadores vejam a etiqueta selecionada atualmente e alterá-lo se a etiqueta predefinida não é apropriada:

![Tutorial do Azure Information Protection - novo documento com a etiqueta predefinida](./media/defaultlabel-word.png)

Em vez de alterar a etiqueta, feche a barra do Information Protection para comparar a experiência se a barra não é apresentada:

![Tutorial do Azure Information Protection - novo documento com a etiqueta predefinida](./media/infoprotect-bar-close.png)

O **gerais** etiqueta ainda selecionada, mas é muito menos óbvia. Também é menos óbvio como selecionar uma etiqueta diferente. Para tal, os utilizadores devem selecionar o **Protect** botão:

![Tutorial do Azure Information Protection – proteger botão selecionado](./media/infoprotect-protectbutton-pulldown.png)

Agora, no menu pendente, verá que o **gerais** etiqueta é selecionada porque tem uma marca de verificação junto ao mesmo. Para alterar a etiqueta selecionada atualmente, os utilizadores podem selecionar uma etiqueta diferente na lista. Quando os utilizadores estiverem novo etiquetagem, eles provavelmente não não se esqueça de selecionar o **Protect** botão cada vez. Eles também podem não perceber que podem selecionar outra etiqueta.

Para apresentar a barra do Information Protection novamente, selecione **Mostrar barra** no menu pendente.

> [!TIP]
> Pode selecionar uma etiqueta predefinida diferente para o Outlook, ao configurar uma [definição de cliente avançado](./rms-client/client-admin-guide-customizations.md#set-a-different-default-label-for-outlook).

### <a name="mandatory-labeling"></a>Etiquetagem obrigatório

Pode alterar o selecionado atualmente **gerais** etiqueta para uma etiqueta diferente, mas não é possível removê-lo. Como nós alteramos a **todos os documentos e e-mails devem ter uma etiqueta** definição **no**, o **eliminar etiqueta** ícone não está disponível na barra do Information Protection. 

Se ainda não alteramos essa definição, a barra do Information Protection mostra este ícone:

![Tutorial do Azure Information Protection – proteger botão selecionado](./media/infoprotect-deletelabel-icon.png)

Em conjunto com uma etiqueta predefinida, a etiquetagem obrigatório garante que os documentos novos e editados (e e-mails) têm uma classificação de base à sua escolha. 

Se não tivesse definimos uma etiqueta predefinida com a definição de etiquetagem obrigatória, sempre é pedido aos utilizadores para selecionar uma etiqueta quando guardar um documento sem etiqueta ou enviar um e-mail sem etiqueta. Para muitos usuários, esses prompts contínuas podem ser frustrante e também resultar em menos precisas de etiquetagem. Para lhes seja pedido para selecionar uma etiqueta quando eles terminar a trabalhar num documento ou e-mail interrompe seus fluxos de trabalho e não existe, em seguida, Sentimos para selecionar qualquer etiqueta aleatoriamente, de modo que podem passar para a próxima coisa precisam de fazer.

### <a name="recommendations-for-emails-with-attachments"></a>Recomendações para e-mails com anexos

Para o documento do Word aberto, escolha uma etiqueta que tem uma classificação superior à **gerais**. Por exemplo, uma das subetiquetas sob **confidencial**, tal como **confidencial - (não protegidos)**. Guarde o documento localmente e forneça um nome. 

Iniciar o Outlook e crie uma nova mensagem de e-mail. Como vimos com o Word, a nova mensagem de e-mail é identificada automaticamente como **gerais** e é apresentada a barra do Information Protection.

Adicione o documento do Word que identificou apenas como um anexo à mensagem de e-mail. Verá uma linha de comandos para alterar a etiqueta de e-mail para o **confidencial** etiqueta que corresponda o anexo do Word. Pode aceitar a recomendação ou descartá-lo:

![Tutorial de proteção de informações do Azure – linha de comandos para relabel e-mail para corresponder ao anexo etiquetado](./media/infoprotect-matchemail-label.png)

Se clicar **dispensar**, não se aplica a nova etiqueta mas ver como o e-mail ainda tem uma etiqueta com a etiqueta predefinida que configurámos, **geral**. As etiquetas disponíveis são ainda fica visíveis para selecionar como alternativa.

Se selecionou **alterar agora**, o e-mail é relabeled para o **confidencial** subetiqueta. No entanto, os utilizadores ainda podem alterar a etiqueta antes de enviar o e-mail, selecionando Editar etiqueta:

![Tutorial de proteção de informações do Azure – linha de comandos para relabel e-mail para corresponder ao anexo etiquetado](./media/infoprotect-editlabel-icon.png)

A barra do Information Protection, em seguida, apresenta mais uma vez, para os utilizadores selecionarem uma etiqueta alternativa.

Uma vez que a etiqueta é selecionada antes de enviar o e-mail, não é necessário para efetivamente enviar o e-mail para ver como funciona esta definição de política. Pode fechar a mensagem de e-mail sem enviar ou salvá-lo.

No entanto, talvez queira tentar repetir neste exercício, mas também anexar outro documento que tem uma classificação mais elevada (uma subetiqueta do **altamente confidencial** etiqueta). Em seguida, irá ver como a linha de comandos muda para aplicar a etiqueta de classificação mais elevada.

## <a name="clean-up-resources"></a>Limpar recursos

Se não desejar manter as alterações efetuadas neste tutorial, faça o seguinte:

1. Selecione **classificações** > **políticas** > **Global** para abrir o **política: Global** painel.

2. Devolver as definições de política para os valores originais que apontou e, em seguida, selecione **guardar**.

Reinicie as suas aplicações Word e Outlook para transferir essas alterações.

## <a name="next-steps"></a>Passos Seguintes

Para obter mais informações sobre como editar o veja de definições de política do Azure Information Protection [como configurar as definições de política do Azure Information Protection](configure-policy-settings.md).

As definições de política que alteramos ajudaram a garantir um nível de base de classificação, bem como encorajar os utilizadores selecionarem uma etiqueta adequada. A próxima etapa é melhorar esta estratégia ao inspecionar o conteúdo de documentos e e-mails e, em seguida, recomendando ou aplicar uma etiqueta apropriada automaticamente. Pode fazê-lo ao configurar etiquetas para condições. Para obter mais informações, consulte [como configurar condições para classificação automática e recomendada para o Azure Information Protection](configure-policy-classification.md).
