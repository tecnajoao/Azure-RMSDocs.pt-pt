---
title: "Passo 1 do tutorial de início rápido | Azure Information Protection"
description: "Passo 2 de um tutorial de introdução com uma duração de aproximadamente 30 minutos, para experimentar rapidamente o Microsoft Azure Information Protection na sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: bce1682624b040545d30ca1cc426e4e2f8c38018
ms.openlocfilehash: 7ba1566a81ca9a3ac45f340f69d3c9e933f015ff


---

# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>Passo 2: configurar e publicar a política do Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Apesar de o Azure Information Protection ser fornecido com uma política predefinida que pode utilizar sem configuração, iremos ver essa política e fazer algumas alterações.

1. Numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global do seu inquilino.

2. No menu hub, clique em **Novo** e, em seguida, na lista **MARKETPLACE**, selecione **Security + Identity**. No painel **Segurança + Identidade**, na lista **APLICAÇÕES INCLUÍDAS**, selecione **Azure Information Protection**. No painel **Azure Information Protection**, clique em **Criar**.

    Esta ação cria o painel **Azure Information Protection** para que, da próxima vez que iniciar sessão no portal, possa selecionar o serviço a partir da lista **Mais serviços** do hub. 

    > [!TIP] 
    > Selecione **Afixar ao dashboard** para criar um mosaico do **Azure Information Protection** no seu dashboard. Assim, não terá de procurar o serviço da próxima vez que iniciar sessão no portal.

3.  Explore o painel principal **Azure Information Protection**, que mostra a política do Information Protection predefinida criada automaticamente:
    
    - Etiquetas para classificação: **Pessoal**, **Público**, **Interno**, **Confidencial** e **Secreto**. Leia a descrição de cada etiqueta para compreender como devem ser utilizadas. Tenha em atenção que **Segredo** tem duas etiquetas secundárias: **Todos os Funcionários** e **O Meu Grupo**, que fornece um exemplo de como uma classificação pode ter subcategorias.

    - Com as predefinições, as etiquetas **Interno**, **Confidencial** e **Secreto** têm marcas visuais configuradas (por exemplo, rodapé, cabeçalho, marca d'água) e nenhuma das etiquetas tem a proteção definida. Além disso, as quatro definições globais não estão definidas para que todos os documentos e e-mails não precisem de uma etiqueta, não existem etiquetas predefinidas e os utilizadores não têm de fornecer uma justificação ao alterar as etiquetas, além de que o cliente não está configurado para obter uma ligação de ajuda personalizada.

    ![Tutorial de início rápido do Azure Information Protection, passo 3 - política predefinida](../media/info-protect-policy.png)

## <a name="changing-the-global-settings-for-a-default-template-and-prompt-for-justification"></a>Alterar as definições globais de um modelo predefinido e pedido de justificação

Para o nosso tutorial, vamos alterar algumas dessas definições globais para que possa ver como funcionam:

1. Para **Selecione a etiqueta predefinida**, defina esta opção como **Interno**.

2. Para **Os utilizadores têm de fornecer uma justificação para reduzir a etiqueta de classificação, remover uma etiqueta ou remover a proteção** defina esta opção como **Ativado**.

## <a name="configuring-a-label-for-protection-a-watermark-and-a-condition-to-prompt-for-classification"></a>Configurar uma etiqueta para proteção, uma marca d'água e uma condição para pedidos de classificação

Agora vamos alterar as definições de uma das etiquetas, **Confidencial**:

1. Clique na etiqueta **Confidencial**. 
    
    No novo painel **Etiqueta: Confidencial**, pode ver agora as definições disponíveis para cada etiqueta. 

2. No painel **Etiqueta: Confidencial**, localize a secção **Definir modelo RMS para proteger documentos e e-mails que contêm esta etiqueta**:
    
    Para a opção **Selecionar modelo RMS a partir de**, mantenha a predefinição **Azure RMS**. Em seguida, para **Selecionar modelo RMS**clique na caixa pendente e selecione o modelo predefinido **\<o nome da organização > - Confidencial**. 
    
    Por exemplo, se o nome de organização for VanArsdel, Lda., irá ver e selecionar **VanArsdel, Lda. – Confidencial**: 
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – definir a proteção Azure RMS](../media/step2-select-rms-template.png)
    
    Se tiver desativado este modelo da Azure Rights Management predefinido, selecione um modelo alternativo. No entanto, se selecionar um modelo departamental, certifique-se de que a sua conta está incluída no âmbito.
    
3. Procure a secção **Definir marcas visuais**:
    
    Para a definição **Documentos com esta etiqueta têm uma marca d'água**, clique em **Ativado** e, na caixa **Texto**, escreva o nome da organização. Por exemplo, **VanArsdel, Lda.**: 
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – definir a proteção Azure RMS](../media/step2-configure-watermark.png)
    
    Embora possa alterar o tamanho, a cor e o esquema das marcas d'água, iremos deixá-las nas predefinições por agora.
    
4. Localize a secção **Configurar condições para aplicar esta etiqueta automaticamente**:
    
    Clique em **Adicionar uma nova condição** e, em seguida, na lâmina **Condição**, selecione o seguinte:
    
    a. **Escolha o tipo de condição**: mantenha a predefinição **Incorporada**.
    
    b. **Selecione incorporada**: no menu pendente, selecione **Número do Cartão de Crédito**.
    
    c. **Número mínimo de ocorrências**: mantenha a predefinição de **1**.
    
    d. **Contagem de ocorrências com apenas valores exclusivos**: mantenha a predefinição **Desativado**.
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – configurar condição de cartão de crédito](../media/step2-configure-condition.png)
    
    Clique em **Guardar** para voltar para a lâmina **Etiqueta: confidencial**.

5. No painel **Etiqueta: Confidencial** irá verificar que **Número do Cartão de Crédito** é apresentado como **NOME DA CONDIÇÃO**, com **1** **OCORRÊNCIAS**:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – configurar condição de cartão de crédito](../media/step2-see-condition.png)

6. Em **Selecione a forma como esta etiqueta é aplicada**: mantenha a predefinição **Recomendado** e não altere a sugestão de política predefinida:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – Classificação recomendada](../media/step2-keep-recommended.png)

7. Na caixa **Introduzir notas para manutenção interna**, escreva **Apenas para fins de testes**:
    
    ![Passo 3 do tutorial de início rápido do Azure Information Protection – escrever notas](../media/step2-type-notes.png)

8. Clique em **Guardar** neste painel **Etiqueta: Confidencial**. Em seguida, no painel principal **Azure Information Protection**, clique novamente em **Guardar**.

9. Agora que fizemos as nossas alterações e guardámo-las, queremos disponibilizá-las aos utilizadores, por isso, clique em **Publicar** e clique em **Sim** para confirmar.

![Tutorial de início rápido do Azure Information Protection, passo 3 - política predefinida configurada](../media/info-protect-policy-configured.png)

Pode fechar o portal do Azure ou deixá-lo aberto para experimentar opções de configuração adicionais depois de concluir este tutorial.

Agora que conhece a política predefinida e fez algumas alterações, o próximo passo é instalar o cliente do Azure Information Protection e a aplicação de partilha Rights Management.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Sobre as opções de configuração para a política|[Configurar a política do Azure Information Protection](../deploy-use/configure-policy.md)|


>[!div class="step-by-step"]
[&#171; Passo 1](infoprotect-tutorial-step1.md)
[Passo 3 &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Nov16_HO3-->


