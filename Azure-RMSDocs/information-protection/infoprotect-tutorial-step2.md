---
title: "Tutorial de início rápido do Azure Information Protection, passo 2 | Azure Rights Management"
description: "Passo 2 de um tutorial de apresentação para experimentar rapidamente o Microsoft Azure Information Protection na sua organização com apenas 4 passos que devem demorar menos de 15 minutos."
author: cabailey
manager: mbaldwin
ms.date: 07/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: 463c0bc1fa86f73e2623faf5a624afeabcadeedb
ms.openlocfilehash: c6ecf22b72d862c605f8be2ab1f75fd2126f8575


---

# Passo 2: configurar e publicar a política do Azure Information Protection

*Aplica-se a: pré-visualização do Azure Information Protection*

Apesar do Azure Information Protection ser fornecido com uma política predefinida que pode utilizar sem configuração, vamos ver essa política e efetuar algumas alterações.

1. Inicie sessão no portal do Azure utilizando esta ligação para o Azure Information Protection: https://portal.azure.com/?microsoft_azure_informationprotection=true
 
2. No menu Hub, clique em **Procurar** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

- Agora verá a lâmina principal **Azure Information Protection**, que mostra a política de Information Protection predefinida que é criada automaticamente. Esta política predefinida contém as seguintes etiquetas para classificação: **Pessoal**, **Público**, **Internas**, **Confidencial**, e **Segredo**. Leia a descrição de cada etiqueta para compreender como devem ser utilizadas. Tenha em atenção que **Segredo** tem duas etiquetas secundárias: **Todos os Funcionários** e **O Meu Grupo**, que fornece um exemplo de como uma classificação pode ter subcategorias.

- Com as respetivas predefinições, **Interna**, **Confidencial**, e **Segredo** têm marcas visuais configuradas (por exemplo, rodapé, cabeçalho, marca d'água) e nenhuma das etiquetas têm a proteção definida. Além disso, as três definições globais não estão definidas para que todos os documentos e e-mails não necessitem de uma etiqueta, não há qualquer etiqueta predefinida e os utilizadores não têm de indicar uma justificação quando reduzirem o nível de sensibilidade.

    ![Tutorial de início rápido do Azure Information Protection, passo 3 - política predefinida](../media/info-protect-policy.png)

Para o nosso tutorial, vamos alterar algumas dessas definições globais para que possa ver como funcionam:

-  **Selecione a etiqueta predefinida**: defina esta opção como **Interna**.

- **Os utilizadores têm de fornecer justificação quando reduzirem o nível de sensibilidade**: defina esta opção como **Ligado**.

Agora vamos alterar as definições de uma das etiquetas, **Confidencial**:

1. Clique na entrada de etiqueta **Confidencial**.

2. Na lâmina **Etiqueta: confidencial**, pode ver as definições disponíveis para cada etiqueta. Efetue as seguintes alterações:

    a. Se tiver ativado a Azure Rights Managment, para **Selecionar modelo RMS**: clique na caixa pendente e selecione o modelo predefinido **\<o nome da organização > - Confidencial**. Por exemplo, se o nome de organização for VanArsdel, Lda., verá e selecione **VanArsdel, Lda. - Confidencial**. Se tiver desativado este modelo da Azure Rights Management predefinido, selecione um modelo alternativo. No entanto, se selecionar um modelo departamental, certifique-se de que a sua conta está incluída no âmbito.

    Se não tiver ativado a Azure Rights Management, não é possível utilizar esta opção.

    b. **Documentos com esta etiqueta têm uma marca d'água**: clique em **Ligado** e na caixa **Texto**, escreva o nome da organização. Por exemplo, **VanArsdel, Lda.**. 

    c. Clique em **Adicionar uma nova condição** e, em seguida, na lâmina **Condição**, selecione o seguinte:

    - **Escolha o tipo de condição**: **Incorporada**

    - **Selecione Incorporada**: **Número do cartão de crédito**

    - **Número mínimo de ocorrências:**: **1**

    - Clique em **Guardar** para voltar para a lâmina **Etiqueta: confidencial**.

3. Na lâmina **Etiqueta: Confidencial** irá verificar que **Número do Cartão de Crédito** é apresentado como **NOME DA CONDIÇÃO**, com **1** **OCORRÊNCIAS**.

4. Deixe **Selecione a forma como esta etiqueta é aplicada**: **Recomendado**

5. Na caixa **introduzir notas para manutenção interna**, escreva **Apenas para fins de testes**.

6. Clique em **Guardar** nesta lâmina **Etiqueta: Confidencial** e na lâmina principal **Azure Information Protection**, clique em **Guardar** novamente.

7. Agora que fizemos as nossas alterações e guardámo-las, queremos disponibilizá-las aos utilizadores, por isso, clique em **Publicar** e clique em **Sim** para confirmar.

![Tutorial de início rápido do Azure Information Protection, passo 3 - política predefinida configurada](../media/info-protect-policy-configured.png)

Pode fechar o portal do Azure ou deixá-lo aberto para experimentar opções de configuração adicionais depois de concluir este tutorial.

Agora que conhece o que é a política predefinida e efetuou algumas alterações, o próximo passo é instalar o cliente do Azure Information Protection.


>[!div class="step-by-step"]
[&#171; Passo 1](infoprotect-tutorial-step1.md)
[Passo 3 &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Jul16_HO3-->


