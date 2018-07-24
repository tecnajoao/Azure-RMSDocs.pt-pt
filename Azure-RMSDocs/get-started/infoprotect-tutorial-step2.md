---
title: Passo 2 do tutorial de início rápido – AIP
description: Passo 2 de um tutorial de introdução para experimentar o Azure Information Protection rapidamente – Configurar a política.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
ms.openlocfilehash: 994b9fb3db3c4a1616896ffac7fcd68b0aff7887
ms.sourcegitcommit: c7e943700189eeaad3f4c919cc0fa3410fd4df5b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204463"
---
# <a name="step-2-configure-the-azure-information-protection-policy"></a>Passo 2: Configurar a política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Apesar de o Azure Information Protection ser fornecido com uma política predefinida que pode utilizar sem configuração, iremos ver essa política e fazer algumas alterações.

1. Continuar a partir [passo 1](infoprotect-tutorial-step1.md) e, ainda no portal do Azure, selecione **classificações** > **políticas** > **Global** para abrir o **política: Global** painel. Este painel mostra a política do Azure Information Protection predefinida criada para o seu inquilino.

2. Passe alguns minutos, ao se familiarizar com as etiquetas que são apresentadas:
    
    - Etiquetas para classificação: **Pessoal**, **Público**, **Geral**, **Confidencial** e **Altamente Confidencial**. As últimas duas etiquetas se expandem para mostrar subetiquetas, que fornecem exemplos de como uma classificação pode ter subcategorias:
    
       > [!NOTE]
       > A sua política predefinida pode ter um aspeto diferente da que é apresentada neste tutorial. Por exemplo, tem uma etiqueta com o nome **Interno** em vez de **Geral** e **Secreto** em vez de **Altamente Confidencial**. Talvez não tiver subetiquetas com o nome **apenas os destinatários**, ou não tem quaisquer etiquetas em todos os. Estas alterações são porque existem versões diferentes da política predefinida, dependendo de quando foi criado para o seu inquilino. Também é possível que tenha editado a política antes de iniciar o tutorial.
       > 
       > Se a sua política predefinida tiver um aspeto diferente, ainda pode utilizar este tutorial, mas tenha em consideração estas alterações quando utilizar as instruções e as imagens que se seguem. Se quiser modificar a sua política predefinida para que corresponda à atual, veja [Política do Azure Information Protection predefinida](../deploy-use/configure-policy-default.md).
    
    - Com a configuração predefinida, algumas etiquetas não têm marcas visuais configuradas. As marcas visuais são um rodapé, cabeçalho e marca d'água. Dependendo da sua diretiva padrão, alguns rótulos, talvez também tenha proteção definida. Por exemplo: 
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – política predefinida](../media/info-protect-policy-default-labelsv2.png)
    
3. Depois das etiquetas, no **configurar definições para apresentar e aplicar-se sobre os usuários finais do Information Protection** seção, também deve ver-se algumas definições de política. Por exemplo, não existe nenhum conjunto de etiqueta predefinida, documentos e e-mails não têm de ter uma etiqueta e os utilizadores não têm de fornecer uma justificação ao alterar as etiquetas:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – política predefinida](../media/info-protect-policy-default-settings.png)

## <a name="changing-the-settings-for-a-default-label-and-prompt-for-justification"></a>Alterar as definições para uma etiqueta predefinida e pedir uma justificação

Para este tutorial, vamos alterar algumas dessas definições de política para que pode ver como funcionam:

1. Para **selecione a etiqueta predefinida**, selecione **geral**. 

    Se não tiver esta etiqueta porque tem uma versão mais antiga da política, selecione **Interno** como etiqueta equivalente.

2. Para **os utilizadores têm de fornecer justificação para definir uma etiqueta de classificação inferior, remover uma etiqueta ou remover a proteção**, defina esta opção como **no**.

3. Além disso, localize a definição **disponibilizar a opção de permissões personalizadas aos utilizadores**. Se esta definição estiver **Off**, altere-o para **no**.
    
    Não poderá ter de alterar esta definição, porque o padrão depende de quando tiver adquirido sua assinatura. Utilizamos permissões personalizadas mais tarde no tutorial para partilhar um documento protegido com um utilizador que especificou ao clicar o ficheiro no Explorador de ficheiros.

4. Selecione **salvar** nisso **política: Global** painel e, se lhe for pedido para confirmar a ação, selecione **OK**. Feche este painel.

## <a name="creating-a-new-label-for-protection-visual-markers-and-a-condition-to-prompt-for-classification"></a>Criar uma nova etiqueta para proteção, marcadores visuais e uma condição para pedidos de classificação

Vamos agora criar uma nova subetiqueta para **confidencial**.

1. Do **classificações** > **etiquetas** opção de menu: com o botão direito do **confidencial** Etiquetar e selecione **adicionar uma etiqueta secundária**.
    
    Se não tiver uma etiqueta denominada **confidencial**, pode selecionar outra etiqueta ou pode criar uma nova etiqueta em vez disso e ainda, siga o tutorial com pequenas diferenças.

2. Sobre o **subetiqueta** painel, especifique o nome de etiqueta do **Finanças** e adicione a seguinte descrição: **dados confidenciais que contém informações financeiras, que é restritas aos funcionários apenas**.
    
    Este texto descreve como a etiqueta selecionada se destina a ser utilizado e é visível para os utilizadores como uma descrição para os ajudar a decidir qual a etiqueta a selecionar.

3. Para **Defina permissões para documentos e e-mails que contenham esta etiqueta**, selecione **Proteger** e, em seguida, selecione **Proteção**:
    
    ![Proteção configurada para uma etiqueta do Azure Information Protection](../media/info-protect-protection-bar-configured.png) 
    
4. Sobre o **proteção** painel, certifique-se de que **Azure (chave da cloud)** está selecionada. Esta opção utiliza o serviço Azure Rights Management para proteger documentos e e-mails. Também certificar-se de que o **definir permissões** opção está selecionada. Em seguida, selecione **adicionar permissões**.

5. Sobre o **adicionar permissões** painel, selecione **Add \<nome da organização >-todos os membros**. Por exemplo, se o nome da sua organização for VanArsdel Ltd, verá a seguinte opção para selecionar:
    
    ![Todos os membros a conceder permissões de proteção para uma etiqueta do Azure Information Protection](../media/info-protect-protection-all-members.png) 
    
    Esta opção seleciona automaticamente todos os utilizadores na sua organização que pode ser concedida permissões. No entanto, pode ver as outras opções que pudesse e procurar grupos ou utilizadores do seu inquilino. Ou, quando seleciona a **introduza os detalhes** opção, pode especificar endereços de e-mail individuais ou até todos os utilizadores de outra organização.

6. Para obter as permissões, selecione **revisor** entre as opções predefinidas. Verá como esse nível de permissão concede automaticamente algumas permissões listados, mas não todas as permissões:
    
    ![Conceder permissões de proteção de Coautor para uma etiqueta do Azure Information Protection](../media/info-protect-protection-reviewer.png)
    
    Pode selecionar níveis de permissão diferentes ou especificar direitos de utilização individuais utilizando o **personalizado** opção. Mas este tutorial, mantenha a **revisor** opção. Pode experimentar com permissões diferentes, mais tarde e ler como restringir o que os utilizadores especificados podem fazer com o documento protegido ou o e-mail.

7. Clique em **OK** fechar isto **adicionar permissões** painel e veja como o **proteção** painel é atualizado para refletir a configuração. Por exemplo:
    
     ![Painel de proteção que mostra a configuração de permissões para uma etiqueta do Azure Information Protection](../media/info-protect-protection-configured.png)
    
    Se selecionou **adicionar permissões**, esta ação abre o **adicionar permissões** painel novamente, para que pode adicionar mais utilizadores e conceder-lhes permissões diferentes. Por exemplo, apenas modo de exibição de conceder acesso a um grupo específico. Mas para este tutorial, vamos manter com um conjunto de permissões para todos os utilizadores.

8. Reveja e mantenha as predefinições para a expiração de conteúdo e acesso offline e, em seguida, clique em **OK** para guardar e fechar isso **proteção** painel.

8. Novamente o **subetiqueta** painel, localize a **definir marcas visuais** secção:
    
    Para o **documentos com esta etiqueta têm um rodapé** definir, clique em **no**e, em seguida, para o **texto** , escreva **classificado como confidencial** . 
    
    Para a definição **Documentos com esta etiqueta têm uma marca d'água**, clique em **Ativado** e, na caixa **Texto**, escreva o nome da organização. Por exemplo, **VanArsdel, Lda.** 
    
    Embora possa alterar a aparência para este marcadores visuais, vamos deixar estas definições nas predefinições por agora.
    
9. Localize a secção **Configurar condições para aplicar esta etiqueta automaticamente**:
    
    Clique em **adicionar uma nova condição** e, em seguida, no **condição** painel, selecione o seguinte:
    
    a. **Escolha o tipo de condição**: mantenha a predefinição **tipos de informações**.
    
    b. Na **seleciona os tipos de informações** caixa de pesquisa: tipo **número de cartão de crédito**. Em seguida, resultados da pesquisa, selecione **número de cartão de crédito**.
    
    c. **Número mínimo de ocorrências**: mantenha a predefinição de **1**.
    
    d. **Contagem de ocorrências com apenas valores exclusivos**: mantenha a predefinição **Desativado**.
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – configurar condição de cartão de crédito](../media/step2-configure-condition.png)
    
    Clique em **salvar** para voltar para o **subetiqueta** painel.

10. Sobre o **subetiqueta** painel, verá que **número de cartão de crédito** é apresentado como o **nome da condição**, com **1**  **OCORRÊNCIAS**:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – configurar condição de cartão de crédito](../media/step2-see-condition.png)

11. Para **selecione a forma como esta etiqueta é aplicada**: mantenha a predefinição **recomendado**e não altere a sugestão de política predefinida. 

12. Na caixa **introduzir notas para manutenção interna**, escreva **Apenas para fins de testes**.

13. Clique em **salvar** nisso **subetiqueta** painel. Se lhe for pedido para confirmar, clique em **OK**. A nova etiqueta é criada e guardada, mas ainda não foram adicionada a uma política.

14. Do **classificações** > **políticas** opção de menu: selecione **Global** novamente e, em seguida, selecione o **adicionar ou remover as etiquetas**link depois das etiquetas.

15. Do **política: Adicionar ou remover as etiquetas** painel, selecione a etiqueta que acabou de criar, subetiqueta com o nome **Finanças**e clique em **OK**.

16. Sobre o **política: Global** painel, verá agora sua nova subetiqueta na sua política global, que está configurada para marcas visuais e proteção. Por exemplo:

    ![Tutorial de início rápido do Azure Information Protection, passo 3 - política predefinida configurada](../media/info-protect-policy-configuredv2.png)
    
    Também pode ver que as definições são configuradas com as suas alterações para a etiqueta predefinida e a justificação:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – definições configuradas](../media/info-protect-settings-configuredv2.png)
    

17. Clique em **salvar** nisso **política: Global** painel. Se lhe for pedido para confirmar esta ação, clique em **OK**.

Pode fechar o portal do Azure ou deixá-lo aberto para experimentar opções de configuração adicionais depois de concluir este tutorial.

Agora que conhece o que é a política predefinida e efetuou algumas alterações, o próximo passo é instalar o cliente do Azure Information Protection.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Sobre a política predefinida e as versões diferentes|[A política do Azure Information Protection predefinida](../deploy-use/configure-policy-default.md)|
|Sobre como configurar a política|[Configurar a política do Azure Information Protection](../deploy-use/configure-policy.md)|
|Instruções detalhadas para configurar uma etiqueta para a proteção|[Como configurar uma etiqueta para proteção do Rights Management](../deploy-use/configure-policy-protection.md)|
|Informações detalhadas sobre as permissões|[Configurar direitos de utilização do Azure Rights Management](../deploy-use/configure-usage-rights.md)|



>[!div class="step-by-step"]
[&#171; Passo 1](infoprotect-tutorial-step1.md)
[Passo 3 &#187;](infoprotect-tutorial-step3.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]