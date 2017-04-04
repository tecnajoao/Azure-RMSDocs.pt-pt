---
title: "Passo 2 do tutorial de início rápido – AIP"
description: "Passo 2 de um tutorial de introdução para experimentar o Azure Information Protection rapidamente – Configurar a política."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
ms.openlocfilehash: 98e65768651c77b4cc0616142e6b7515d275b7a9
ms.sourcegitcommit: 8ae83a9fc03bf2ee39ea758835ef52156f19784d
translationtype: HT
---
# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>Passo 2: configurar e publicar a política do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Apesar de o Azure Information Protection ser fornecido com uma política predefinida que pode utilizar sem configuração, iremos ver essa política e fazer algumas alterações.

1. Numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global do seu inquilino.

2. No menu do hub, clique em **Novo** e, em seguida, na lista **MARKETPLACE**, selecione **Security + Identity**. No painel **Segurança + Identidade**, na lista **APLICAÇÕES INCLUÍDAS**, selecione **Azure Information Protection**. No painel **Azure Information Protection**, clique em **Criar**.

    Esta ação ativa o serviço para o seu inquilino e cria o painel **Azure Information Protection** para que, da próxima vez que iniciar sessão no portal, possa selecionar o serviço a partir da lista **Mais serviços** do hub. 

    > [!TIP] 
    > Selecione **Afixar ao dashboard** para criar um mosaico do **Azure Information Protection** no seu dashboard. Assim, não terá de procurar o serviço da próxima vez que iniciar sessão no portal.

3.  Explore o painel **Política: Global**, apresentado automaticamente, que mostra a política do Information Protection predefinida criada automaticamente para o seu inquilino:
    
    - Etiquetas para classificação: **Pessoal**, **Público**, **Geral**, **Confidencial** e **Altamente Confidencial**. As últimas duas etiquetas expandem-se para mostrar subetiquetas: **Todos os Funcionários** e **Todos (não protegidos)**, para disponibilizar exemplos de como uma classificação pode ter subcategorias.
    
       > [!NOTE]
       > A sua política predefinida pode ter um aspeto diferente da que é apresentada neste tutorial. Por exemplo, tem uma etiqueta com o nome **Interno** em vez de **Geral** e **Secreto** em vez de **Altamente Confidencial**. Se for este o caso, está provavelmente a utilizar uma versão mais antiga da política predefinida. Também é possível que tenha editado a política antes de iniciar o tutorial.
       > 
       > Se a sua política predefinida tiver um aspeto diferente, ainda pode utilizar este tutorial, mas tenha em consideração estas alterações quando utilizar as instruções e as imagens que se seguem. Se quiser modificar a sua política predefinida para que corresponda à atual, veja [Política do Azure Information Protection predefinida](../deploy-use/configure-policy-default.md).

    - Com a configuração predefinida, algumas etiquetas não têm marcas visuais configuradas (como o rodapé, cabeçalho, marca d'água) e nenhuma delas tem uma proteção definida: 
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – política predefinida](../media/info-protect-policy-default-labelsv2.png)
    
    Além disso, existem algumas definições de política que não estão definidas para que, por exemplo, todos os documentos e e-mails não precisem de uma etiqueta, não existam etiquetas predefinidas e os utilizadores não tenham de fornecer uma justificação ao alterar as etiquetas:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – política predefinida](../media/info-protect-policy-default-settings.png)

## <a name="changing-the-settings-for-a-default-label-and-prompt-for-justification"></a>Alterar as definições para uma etiqueta predefinida e pedir uma justificação

Para o nosso tutorial, vamos alterar algumas dessas definições de política para que possa ver como funcionam:

1. Em **Selecione a etiqueta predefinida**, defina esta opção como **Geral**. 

    Se não tiver esta etiqueta porque tem uma versão mais antiga da política, selecione **Interno** como etiqueta equivalente.

2. Para **Os utilizadores têm de fornecer uma justificação para reduzir a etiqueta de classificação, remover uma etiqueta ou remover a proteção** defina esta opção como **Ativado**.

## <a name="configuring-a-label-for-protection-a-watermark-and-a-condition-to-prompt-for-classification"></a>Configurar uma etiqueta para proteção, uma marca d'água e uma condição para pedidos de classificação

Iremos alterar as definições de uma das subetiquetas, **Todos os Funcionários**, da etiqueta principal **Confidencial**. 

Se a sua etiqueta **Confidencial** não tiver subetiquetas porque tem uma versão mais antiga da política, pode utilizar a etiqueta **Confidencial** em alternativa. Os passos de configuração serão os mesmos, mas o nome do painel da etiqueta será **Confidencial** em vez de **Todos os Funcionários**.

1. Certifique-se de que a etiqueta **Confidencial** está expandida e, em seguida, selecione **Todos os Funcionários** a partir da mesma.
    
    No novo painel **Etiqueta: Todos os Funcionários**, pode ver agora as definições disponíveis para cada etiqueta. 

2. Leia o texto de **Descrição** desta etiqueta. Este texto descreve como a etiqueta selecionada se destina a ser utilizada e a ser visível para os utilizadores como uma descrição para ajudá-los a decidir qual a etiqueta a selecionar.

3. Localize a secção **Defina permissões para documentos e e-mails que contenham esta etiqueta** e selecione **Proteger**:
    
    ![Configurar a proteção para uma etiqueta do Azure Information Protection](../media/info-protect-protection-barv2.png) 
    
    Esta ação abre o painel **Proteção**.
    
3. No painel **Proteção**, certifique-se de que as opções **Azure RMS** e **Selecionar modelo** estão selecionadas e, em seguida, clique na caixa pendente e selecione o modelo predefinido **\<o nome da sua organização> - Confidencial**.     
    
    Por exemplo, se o nome de organização for VanArsdel, Lda., irá ver e selecionar **VanArsdel, Lda. – Confidencial**: 
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – definir a proteção do Azure RMS](../media/step2-select-rms-template.png)
    
    Se tiver desativado este modelo da Azure Rights Management predefinido, selecione um modelo alternativo. No entanto, se selecionar um modelo departamental, certifique-se de que a sua conta está incluída no âmbito.
    
4. Clique em **OK** para guardar as suas alterações, o que fecha o painel **Proteção**. Verá a sua configuração refletida no painel **Etiqueta: Todos os Funcionários**:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – proteção do Azure RMS configurada](../media/protection-bar-configured.png)
    
5. No painel **Etiqueta: Todos os Funcionários**, localize a secção **Definir marcas visuais**:
    
    Para a definição **Documentos com esta etiqueta têm uma marca d'água**, clique em **Ativado** e, na caixa **Texto**, escreva o nome da organização. Por exemplo, **VanArsdel, Lda.**: 
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – definir a proteção do Azure RMS](../media/step2-configure-watermark.png)
    
    Embora possa alterar o tamanho, a cor e o esquema das marcas d'água, iremos deixá-las nas predefinições por agora.
    
6. Localize a secção **Configurar condições para aplicar esta etiqueta automaticamente**:
    
    Clique em **Adicionar uma nova condição** e, em seguida, na lâmina **Condição**, selecione o seguinte:
    
    a. **Escolha o tipo de condição**: mantenha a predefinição **Incorporada**.
    
    b. **Selecione incorporada**: no menu pendente, selecione **Número do Cartão de Crédito**.
    
    c. **Número mínimo de ocorrências**: mantenha a predefinição de **1**.
    
    d. **Contagem de ocorrências com apenas valores exclusivos**: mantenha a predefinição **Desativado**.
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – configurar condição de cartão de crédito](../media/step2-configure-condition.png)
    
    Clique em **Guardar** para voltar ao painel **Etiqueta: Todos os Funcionários**.

7. No painel **Etiqueta: Todos os Funcionários** irá verificar que **Número do Cartão de Crédito** é apresentado como **NOME DA CONDIÇÃO**, com **1** **OCORRÊNCIAS**:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – configurar condição de cartão de crédito](../media/step2-see-condition.png)

8. Em **Selecione a forma como esta etiqueta é aplicada**: mantenha a predefinição **Recomendado** e não altere a sugestão de política predefinida:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – Classificação recomendada](../media/step2-keep-recommendedv2.png)

9. Na caixa **Introduzir notas para manutenção interna**, escreva **Apenas para fins de testes**:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – escrever notas](../media/step2-type-notes.png)

10. Clique em **Guardar** neste painel **Etiqueta: Todos os Funcionários**. Em seguida, no painel **Política:Global**, clique em **Guardar** novamente.
    
    Neste momento, as suas etiquetas mostram a proteção do Azure RMS para a etiqueta que configurou:

    ![Tutorial de início rápido do Azure Information Protection, passo 3 - política predefinida configurada](../media/info-protect-policy-configuredv2.png)
    
    As definições são configuradas com as suas alterações para a etiqueta e a justificação predefinidas:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – definições configuradas](../media/info-protect-settings-configuredv2.png)
    
11. Agora que fizemos as nossas alterações e as guardamos, queremos disponibilizá-las aos utilizadores, por isso, no painel inicial do **Azure Information Protection**, clique em **Publicar** e clique em **Sim** para confirmar.

    ![Passo 3 do tutorial de início rápido do Azure Information Protection – publicar a política configurada](../media/info-protect-publish.png)

Pode fechar o portal do Azure ou deixá-lo aberto para experimentar opções de configuração adicionais depois de concluir este tutorial.

Agora que conhece o que é a política predefinida e efetuou algumas alterações, o próximo passo é instalar o cliente do Azure Information Protection.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Sobre as opções de configuração para a política|[Configurar a política do Azure Information Protection](../deploy-use/configure-policy.md)|


>[!div class="step-by-step"]
[&#171; Passo 1](infoprotect-tutorial-step1.md)
[Passo 3 &#187;](infoprotect-tutorial-step3.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]