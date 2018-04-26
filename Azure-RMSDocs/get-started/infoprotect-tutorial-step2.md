---
title: Passo 2 do tutorial de início rápido – AIP
description: Passo 2 de um tutorial de introdução para experimentar o Azure Information Protection rapidamente – Configurar a política.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
ms.openlocfilehash: e2850a0f67f18febdbd98e59d01b2f28b00bff2a
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2018
---
# <a name="step-2-configure-the-azure-information-protection-policy"></a>Passo 2: Configurar a política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

>[!NOTE]
> Neste passo do tutorial reflete as atualizações mais recentes para o portal do Azure. Se não vir um **classificações** opção do menu e ainda ver um **publicar** opção, as instruções de navegação corresponderá não exatamente o que vê. Se for esse o caso, considere devolver para este passo do tutorial em alguns dias quando o seu inquilino está atualizado para que as alterações mais recentes.

Apesar de o Azure Information Protection ser fornecido com uma política predefinida que pode utilizar sem configuração, iremos ver essa política e fazer algumas alterações.

1. Continuar de [passo 1](infoprotect-tutorial-step1.md) e ainda no portal do Azure, selecione **classificações** > **políticas** > **Global** para abrir o **política: Global** painel. Este painel mostra a política do Azure Information Protection predefinida que é criada para o seu inquilino.

2. Demora alguns minutos familiarizing por si com as etiquetas que são apresentadas:
    
    - Etiquetas para classificação: **Pessoal**, **Público**, **Geral**, **Confidencial** e **Altamente Confidencial**. Expanda as últimas duas etiquetas para mostrar sublabels, que fornecem exemplos de como uma classificação pode ter subcategorias:
    
       > [!NOTE]
       > A sua política predefinida pode ter um aspeto diferente da que é apresentada neste tutorial. Por exemplo, tem uma etiqueta com o nome **Interno** em vez de **Geral** e **Secreto** em vez de **Altamente Confidencial**. Talvez não dispõe de sublabels denominados **destinatários apenas**, ou não tem qualquer das etiquetas de todo. Estas alterações são porque existem versões diferentes da política predefinida, dependendo de que foi criada para o seu inquilino. Também é possível que tenha editado a política antes de iniciar o tutorial.
       > 
       > Se a sua política predefinida tiver um aspeto diferente, ainda pode utilizar este tutorial, mas tenha em consideração estas alterações quando utilizar as instruções e as imagens que se seguem. Se quiser modificar a sua política predefinida para que corresponda à atual, veja [Política do Azure Information Protection predefinida](../deploy-use/configure-policy-default.md).
    
    - A configuração predefinida, algumas etiquetas não têm marcas visuais configuradas. As marcas visuais são um rodapé, cabeçalho e marca de água. Consoante a política predefinida, algumas etiquetas também podem ter proteção definida. Por exemplo: 
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – política predefinida](../media/info-protect-policy-default-labelsv2.png)
    
3. Também verá que existem algumas definições de política. Por exemplo, não há nenhum conjunto de etiqueta predefinida, documentos e e-mails não têm de ter uma etiqueta e os utilizadores têm de fornecer justificação quando são alterados etiquetas:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – política predefinida](../media/info-protect-policy-default-settings.png)

## <a name="changing-the-settings-for-a-default-label-and-prompt-for-justification"></a>Alterar as definições para uma etiqueta predefinida e pedir uma justificação

Para o nosso tutorial, vamos alterar algumas dessas definições de política para que possa ver como funcionam:

1. Para **selecione a etiqueta predefinida**, selecione **geral**. 

    Se não tiver esta etiqueta porque tem uma versão mais antiga da política, selecione **Interno** como etiqueta equivalente.

2. Para **os utilizadores têm de fornecer justificação para definir uma etiqueta de classificação inferior, remova uma etiqueta ou remova a proteção**, defina esta opção **no**.

3. Além disso, localize a definição **disponibilizar a opção de permissões personalizadas aos utilizadores**. Se estiver definido como **desativar**, esta opção para alterar **no**.
    
    Não poderá ter de alterar esta definição, porque a predefinição depende da altura em que obteve a sua subscrição. Utilizamos permissões personalizadas mais tarde no tutorial para partilhar um documento protegido com um utilizador que especificou quando clique com botão direito do ficheiro a partir do Explorador de ficheiros.

## <a name="creating-a-new-label-for-protection-visual-markers-and-a-condition-to-prompt-for-classification"></a>Criar uma nova etiqueta para proteção, marcas visuais e uma condição para a linha de comandos para classificação

Vamos agora criar um novo sublabel para **confidencial**.

1. Clique com botão direito do **confidencial** etiqueta e selecione **adicionar uma etiqueta secundária**.
    
    Se não tiver uma etiqueta com o nome **confidencial**, pode selecionar outra etiqueta ou pode criar uma nova etiqueta em vez disso e ainda siga o tutorial com pequenas diferenças.

2. No **subetiqueta** painel, especifique o nome de etiqueta do **financeiro** e adicione a seguinte descrição: **dados confidenciais que contém informações financeiras é restringidas aos funcionários apenas**.
    
    Este texto descreve como a etiqueta selecionada se destina a ser utilizado e é visível para os utilizadores como uma descrição para ajudar a decidir qual a etiqueta para selecionar.

3. Para **Defina permissões para documentos e e-mails que contenham esta etiqueta**, selecione **Proteger** e, em seguida, selecione **Proteção**:
    
    ![Proteção configurada para uma etiqueta de Azure Information Protection](../media/info-protect-protection-bar-configured.png) 
    
4. No **proteção** painel, certifique-se de que **Azure (chave de nuvem)** está selecionada. Esta opção utiliza o serviço Azure Rights Management para proteger documentos e e-mails. Certifique-se de que **definir permissões** também é selecionada. Em seguida, selecione **adicionar permissões**.

5. No **adicionar permissões** painel, selecione **adicionar \<nome da organização >-todos os membros**. Por exemplo, se o nome de organização for VanArsdel Lda., verá a seguinte opção para selecionar:
    
    ![Conceder a todos os membros permissões de proteção para uma etiqueta de Azure Information Protection](../media/info-protect-protection-all-members.png) 
    
    Esta opção seleciona automaticamente todos os utilizadores na sua organização que pode ser concedida permissões. No entanto, pode ver as opções que pode procurar e procurar grupos ou utilizadores do seu inquilino. Ou, quando seleciona o **Introduza detalhes** opção, pode especificar endereços de e-mail individuais ou mesmo a todos os utilizadores de outra organização.

6. Para conhecer as permissões, selecione **revisor** entre as opções predefinidas. Pode ver como este nível de permissões concede automaticamente algumas permissões listadas, mas não todas as permissões:
    
    ![Conceder permissões de proteção de Coautor para uma etiqueta de Azure Information Protection](../media/info-protect-protection-reviewer.png)
    
    Pode selecionar os níveis de permissão diferentes ou especifique os direitos de utilização individuais utilizando o **personalizada** opção. Mas para este tutorial, mantenha o **revisor** opção. Pode experimentar com permissões diferentes mais tarde e ler como restringir que os utilizadores especificados podem fazer com o documento protegido ou o e-mail.

7. Clique em **OK** para fechar este **adicionar permissões** painel e ver como o **proteção** painel é atualizado para refletir a configuração. Por exemplo:
    
     ![Painel de proteção que mostra a configuração de permissões para uma etiqueta de Azure Information Protection](../media/info-protect-protection-configured.png)
    
    Se selecionar **adicionar permissões**, esta ação abre o **adicionar permissões** painel novamente, para que possam adicionar mais utilizadores e conceder-lhes permissões diferentes. Por exemplo, apenas vista de conceder acesso a um grupo específico. Mas para este tutorial, vamos manter com um conjunto de permissões para todos os utilizadores.

8. Reveja e mantenha as predefinições de expiração de conteúdo e acesso offline e, em seguida, clique em **OK** para guardar e fechar este **proteção** painel.

8. Reverter o **subetiqueta** painel, localize o **definir marcação visual** secção:
    
    Para o **documentos com esta etiqueta têm um rodapé** definição, clique em **no**e, em seguida, para o **texto** caixa, escreva **classificados como confidenciais** . 
    
    Para a definição **Documentos com esta etiqueta têm uma marca d'água**, clique em **Ativado** e, na caixa **Texto**, escreva o nome da organização. Por exemplo, **VanArsdel, Lda.** 
    
    Embora o pode alterar o aspeto de marcadores visuais, iremos irá deixe estas definições as predefinições por agora.
    
9. Localize a secção **Configurar condições para aplicar esta etiqueta automaticamente**:
    
    Clique em **adicionar uma nova condição** e, em seguida, no **condição** painel, selecione o seguinte:
    
    a. **Escolha o tipo de condição**: mantenha a predefinição **tipos de informações**.
    
    b. No **seleciona os tipos de informações** caixa de pesquisa: tipo **número de cartão de crédito**. em seguida, os resultados da pesquisa, selecione **número de cartão de crédito**.
    
    c. **Número mínimo de ocorrências**: mantenha a predefinição de **1**.
    
    d. **Contagem de ocorrências com apenas valores exclusivos**: mantenha a predefinição **Desativado**.
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – configurar condição de cartão de crédito](../media/step2-configure-condition.png)
    
    Clique em **guardar** para voltar para o **subetiqueta** painel.

10. No **subetiqueta** painel, verá que **número de cartão de crédito** é apresentado como o **nome da condição**, com **1**  **As OCORRÊNCIAS**:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – configurar condição de cartão de crédito](../media/step2-see-condition.png)

11. Para **selecione a forma como esta etiqueta é aplicada**: mantenha a predefinição **recomendado**, alteram a sugestão de política predefinido. 

12. Na caixa **introduzir notas para manutenção interna**, escreva **Apenas para fins de testes**.

13. Clique em **guardar** neste **subetiqueta** painel. Em seguida, no painel **Política:Global**, clique em **Guardar** novamente.
    
    Agora, ver o seu novo sublabel, que é configurado para proteção e marcas visuais. Por exemplo:

    ![Tutorial de início rápido do Azure Information Protection, passo 3 - política predefinida configurada](../media/info-protect-policy-configuredv2.png)
    
    Consulte também se as definições são configuradas com as suas alterações para a etiqueta predefinida e a justificação:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – definições configuradas](../media/info-protect-settings-configuredv2.png)
    
Pode fechar o portal do Azure ou deixá-lo aberto para experimentar opções de configuração adicionais depois de concluir este tutorial.

Agora que conhece o que é a política predefinida e efetuou algumas alterações, o próximo passo é instalar o cliente do Azure Information Protection.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Sobre a política predefinida e as versões diferentes|[A política do Azure Information Protection predefinida](../deploy-use/configure-policy-default.md)|
|Sobre como configurar a política|[Configurar a política do Azure Information Protection](../deploy-use/configure-policy.md)|
|Instruções detalhadas para configurar uma etiqueta para a proteção|[Como configurar uma etiqueta para a proteção Rights Management](../deploy-use/configure-policy-protection.md)|
|Informações detalhadas sobre as permissões|[Configurar direitos de utilização do Azure Rights Management](../deploy-use/configure-usage-rights.md)|



>[!div class="step-by-step"]
[&#171; Passo 1](infoprotect-tutorial-step1.md)
[Passo 3 &#187;](infoprotect-tutorial-step3.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]