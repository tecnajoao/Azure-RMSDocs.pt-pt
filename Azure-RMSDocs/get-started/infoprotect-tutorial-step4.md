---
title: "Passo 4 do tutorial de início rápido – AIP"
description: "Passo 3 de um tutorial de introdução com uma duração de aproximadamente 20 minutos para experimentar rapidamente o Microsoft Azure Information Protection na sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 57a46c7afe34717dd4335b0f9a19bd539821fc72
ms.lasthandoff: 02/24/2017


---

# <a name="step-4-see-classification-labeling-and-protection-in-action"></a>Passo 4: ver classificação, etiquetas e proteção em ação 

>*Aplica-se a: Azure Information Protection*

Agora que já tem um documento do Word aberto com o cliente do Azure Information Protection instalado, está pronto para ver como é fácil iniciar a etiquetagem e proteger o seu documento, utilizando a política que configurámos.

A classificação e a proteção ocorrem quando guarda o documento, mas antes de o fazermos, vamos utilizar o nosso documento não guardado para ver como é fácil aplicar e alterar etiquetas.

## <a name="to-manually-change-our-default-label"></a>Para alterar manualmente a nossa etiqueta predefinida

Na barra do Information Protection, selecione a etiqueta **Pessoal** e ser-lhe-á pedido para indicar a razão pela qual está a reduzir o nível de classificação:

![Tutorial de início rápido do Azure Information Protection, passo 4 - pedido para indicar o motivo da redução](../media/info-protect-lower-justification.png)

Selecione **A etiqueta anterior já não se aplica** e clique em **Confirmar**. O valor **Sensibilidade** é alterado para **Pessoal**.

## <a name="to-remove-the-classification-completely"></a>Para remover a classificação por completo

Na barra do Information Protection, clique no ícone **Editar Etiqueta** junto a **Pessoal**. Esta ação apresenta as etiquetas disponíveis. No entanto, em vez de selecionar uma das etiquetas, desta vez, clique no ícone **Eliminar etiqueta**. Desta vez, escreva “Este documento não precisa de classificação” e clique em **Confirmar**.  

Verá que o valor **Sensibilidade** apresenta **Não definido**, a opção vista pelos utilizadores inicialmente se não definir uma etiqueta predefinida:

![Tutorial de início rápido do Azure Information Protection, passo 4 - remover classificação](../media/sensitivity-not-set.png)


## <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>Para ver um pedido de recomendação para etiquetagem e proteção automática

1. No documento do Word, escreva um número de cartão de crédito válido, por exemplo: **4242-4242-4242-4242**. 

2. Guarde o documento (utilize qualquer nome de ficheiro, qualquer localização). 

3. Verá então o pedido: **É recomendável etiquetar este ficheiro como Confidencial**. Clique em **Alterar agora**.

    ![Tutorial de início rápido do Azure Information Protection, passo 4 - recomendar pedido](../media/change-now.png)

    Além de o documento ter a etiqueta definida como Confidencial, verá imediatamente a marca d'água do nome da organização na página e também será aplicado o rodapé de **Sensibilidade: Confidencial**. 

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
