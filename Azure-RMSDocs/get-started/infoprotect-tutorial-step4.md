---
title: "Passo 4 do tutorial de início rápido – AIP"
description: "Passo 4 de um tutorial de introdução para experimentar o Azure Information Protection rapidamente – Ver etiquetas e proteção em ação."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
ms.openlocfilehash: 56ecd7b99f81a3b2399e166c1ca6a50797e65fa3
ms.sourcegitcommit: f0402cf14506b4c61a156a2baf7e69b7b16883a1
translationtype: HT
---
# <a name="step-4-see-classification-labeling-and-protection-in-action"></a>Passo 4: ver classificação, etiquetas e proteção em ação 

>*Aplica-se a: Azure Information Protection*

Agora que já tem um documento do Word aberto com o cliente do Azure Information Protection instalado, está pronto para ver como é fácil iniciar a etiquetagem e proteger o seu documento, utilizando a política que configurámos.

A classificação e a proteção ocorrem quando guarda o documento, mas antes de o fazermos, vamos utilizar o nosso documento não guardado para ver como é fácil aplicar e alterar etiquetas.

## <a name="to-manually-change-our-default-label"></a>Para alterar manualmente a nossa etiqueta predefinida

Na barra do Information Protection, selecione a última etiqueta e verá a forma como as subetiquetas são apresentadas:

![Passo 4 do tutorial de início rápido do Azure Information Protection – selecionar uma subetiqueta](../media/info-protect-sub-labelsv2.png)

Selecione uma destas subetiquetas e verá que as outras etiquetas deixarão de ser apresentadas na barra após ter selecionado uma etiqueta para este documento. O valor **Sensibilidade** é alterado para mostrar o nome da etiqueta e da subetiqueta com uma alteração correspondente da cor da etiqueta. Por exemplo:

![Passo 4 do tutorial de início rápido do Azure Information Protection – subetiqueta selecionada](../media/info-protect-sub-label-selectedv2.png)

Na barra do Information Protection, clique no ícone **Editar Etiqueta** junto ao valor da etiqueta selecionada:

![Passo 4 do tutorial de início rápido do Azure Information Protection – ícone Editar Etiqueta](../media/info-protect-edit-label-selectedv2.png)

Esta ação volta a apresentar as etiquetas disponíveis.

Selecione a primeira etiqueta, **Pessoal**. Devido a ter selecionado uma etiqueta com uma classificação de nível inferior à da etiqueta anteriormente selecionada para este documento, ser-lhe-á pedido que justifique o motivo pelo qual está a reduzir o nível de classificação:

![Passo 4 do tutorial de início rápido do Azure Information Protection – pedido para indicar o motivo da redução](../media/info-protect-lower-justification.png)

Selecione **A etiqueta anterior já não se aplica** e clique em **Confirmar**. O valor **Sensibilidade** é alterado para **Pessoal** e as outras etiquetas voltam a ficar ocultas.

## <a name="to-remove-the-classification-completely"></a>Para remover a classificação por completo

Na barra Information Protection, clique novamente no ícone **Editar Etiqueta**. Em vez de selecionar uma das etiquetas, clique no ícone **Eliminar Etiqueta**:

![Passo 4 do tutorial de início rápido do Azure Information Protection – Eliminar Ícone](../media/delete-icon-from-personalv2.png)

Desta vez, quando lhe for apresentada uma mensagem, escreva "Este documento não precisa de ser classificado" e clique em **Confirmar**.  

Verá que o valor **Sensibilidade** apresenta **Não definido**, a opção vista pelos utilizadores inicialmente se não definir uma etiqueta predefinida:

![Passo 4 do tutorial de início rápido do Azure Information Protection – remover classificação](../media/sensitivity-not-setv2.png)


## <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>Para ver um pedido de recomendação para etiquetagem e proteção automática

1. No documento do Word, escreva um número de cartão de crédito válido, por exemplo: **4242-4242-4242-4242**. 

2. Guarde o documento (utilize qualquer nome de ficheiro, qualquer localização). 

3. Verá um pedido para aplicar a etiqueta que configurou para proteção quando forem detetados números de cartão de crédito. Se não concordar com a recomendação, a definição da política permite rejeitá-la ao selecionar **Dispensar**. Fornecer uma recomendação mas deixar que o utilizador a ignore ajuda a reduzir os falsos positivos quando utiliza a classificação automática. Para este tutorial, clique em **Alterar agora**.

    ![Passo 4 do tutorial de início rápido do Azure Information Protection – recomendar pedido](../media/change-nowv2.png)

    Para além do documento a mostrar que a etiqueta configurada foi aplicada (por exemplo, **Confidencial\Todos os Funcionários**), verá automaticamente a marca d'água do nome da sua organização na página. O rodapé **Classificado como Confidencial** também é aplicado. 

    O documento é também protegido com o modelo do Azure Rights Management especificado, que pode confirmar quando clica no separador **Ficheiro** e ver as informações de **Proteger Documento**. Se utilizou o modelo de confidencialidade predefinido, é apresentada uma informação a indicar que o documento está restrito a utilizadores internos (os utilizadores fora da sua organização não conseguem abrir o documento) e os respetivos conteúdos não podem ser copiados ou impressos. Como proprietário do documento, pode copiar a partir do mesmo e imprimi-lo, mas se o enviar por e-mail a outro utilizador na sua organização, o mesmo não poderá efetuar estas ações.

4. Agora, pode fechar este documento.

Agora que viu a classificação, a etiquetagem e a proteção em ação, vamos ver como pode proteger os documentos, mesmo quando são partilhados com outras pessoas noutra organização. Pode até controlar como estão a ser utilizados e revogar o acesso aos mesmos.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Instruções completas para etiquetar e proteger ficheiros |[Classificar e proteger um ficheiro ou e-mail](../rms-client/client-classify-protect.md)|





>[!div class="step-by-step"]
[&#171; Passo 3](infoprotect-tutorial-step3.md)
[Passo 5 &#187;](infoprotect-tutorial-step5.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]