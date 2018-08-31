---
title: Passo 4 do tutorial de início rápido – AIP
description: Passo 4 de um tutorial de introdução para experimentar o Azure Information Protection rapidamente – Ver etiquetas e proteção em ação.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/29/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
ms.openlocfilehash: 2429a56163c79468bab681a9544c828c6d218392
ms.sourcegitcommit: b0c4fe8c522987a7863958ffdc6866a91ebabf86
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43242195"
---
# <a name="step-4-see-classification-labeling-and-protection-in-action"></a>Passo 4: ver classificação, etiquetas e proteção em ação 

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Agora que já tem um documento do Word aberto com o cliente do Azure Information Protection instalado, está pronto para ver como é fácil iniciar a etiquetagem e proteger o seu documento, utilizando a política que configurámos.

Classificação e a proteção ocorrem quando guarda o documento. Mas antes de o fazermos, vamos utilizar o nosso documento não guardado para ver como é fácil aplicar e alterar etiquetas.

## <a name="to-manually-change-our-default-label"></a>Para alterar manualmente a nossa etiqueta predefinida

Na barra do Information Protection, selecione a última etiqueta e verá a forma como as subetiquetas são apresentadas:

![O Azure Information Protection início rápido do passo 4 do tutorial - escolha uma subetiqueta](./media/info-protect-sub-labelsv2.png)

Selecione uma destas subetiquetas e verá que as outras etiquetas já não apresentadas na barra de ter selecionado uma etiqueta para este documento. O **sensibilidade** nome muda de valor para mostrar a etiqueta e subetiqueta, com uma alteração correspondente da cor da etiqueta. Por exemplo:

![O Azure Information Protection início rápido do passo 4 do tutorial – subetiqueta selecionada](./media/info-protect-sub-label-selectedv2.png)

Na barra do Information Protection, clique no ícone **Editar Etiqueta** junto ao valor da etiqueta selecionada:

![Passo 4 do tutorial de início rápido do Azure Information Protection – ícone Editar Etiqueta](./media/info-protect-edit-label-selectedv2.png)

Esta ação volta a apresentar as etiquetas disponíveis.

Selecione a primeira etiqueta, **Pessoal**. Uma vez que selecionar uma etiqueta com uma classificação de nível inferior da etiqueta anteriormente selecionada para este documento, lhe for pedido para indicar a razão pela qual está a reduzir o nível de classificação:

![Passo 4 do tutorial de início rápido do Azure Information Protection – pedido para indicar o motivo da redução](./media/info-protect-lower-justification.png)

Selecione **A etiqueta anterior já não se aplica** e clique em **Confirmar**. O valor **Sensibilidade** é alterado para **Pessoal** e as outras etiquetas voltam a ficar ocultas.

## <a name="to-remove-the-classification-completely"></a>Para remover a classificação por completo

Na barra Information Protection, clique novamente no ícone **Editar Etiqueta**. Em vez de selecionar uma das etiquetas, clique no ícone **Eliminar Etiqueta**:

![Passo 4 do tutorial de início rápido do Azure Information Protection – Eliminar Ícone](./media/delete-icon-from-personalv2.png)

Desta vez, quando lhe for pedido, escreva "este documento não precisa classificar" e clique em **confirmar**.  

Verá o **sensibilidade** valor a apresentar **nenastaveno**, que é que os utilizadores veem inicialmente se não definir uma etiqueta predefinida.

## <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>Para ver um pedido de recomendação para etiquetagem e proteção automática

1. No documento do Word, escreva um número de cartão de crédito válido, por exemplo: **4242-4242-4242-4242**. 

2. Guarde localmente, o documento com um nome de ficheiro. 

3. Verá um pedido para aplicar a etiqueta que configurou para proteção quando forem detetados números de cartão de crédito. Se não concordar com a recomendação, a definição da política permite rejeitá-la ao selecionar **Dispensar**. Fornecer uma recomendação mas deixar que o utilizador a ignore ajuda a reduzir os falsos positivos quando utiliza a classificação automática. Para este tutorial, clique em **Alterar agora**.

    ![Passo 4 do tutorial de início rápido do Azure Information Protection – recomendar pedido](./media/change-nowv2.png)

    Para além do documento a mostrar que a etiqueta configurada foi aplicada (por exemplo, **confidencial \ Finanças**), verá imediatamente a marca d'água do nome da organização em toda a página e rodapé de  **Classificado como confidencial** também é aplicado. 

    O documento é também protegido com as permissões que especificou para esta etiqueta. Pode confirmar que o documento é protegido ao clicar o **arquivo** separador e ver as informações de **Proteger documento**. Verá que o documento é protegido pelo **confidencial \ Finanças** e a descrição da etiqueta. 
    
    Devido a configuração da proteção da etiqueta, apenas os funcionários podem abrir o documento e algumas ações são restritas para eles. Por exemplo, porque eles não têm a impressão e a cópia e extrair conteúdas permissões, eles não é possível imprimir o documento ou uma cópia do mesmo. Essas restrições quanto ajuda a evitar a perda de dados. Como o proprietário do documento, pode imprimi-lo e copiá-los. No entanto, se enviar por e-mail o documento para outro utilizador na sua organização, eles não podem fazer com que estas ações.

4. Agora, pode fechar este documento.

Agora que viu a classificação, a etiquetagem e a proteção em ação, vamos ver como pode proteger os documentos, mesmo quando são partilhados com outras pessoas noutra organização. Pode até controlar como estão a ser utilizados e revogar o acesso aos mesmos.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Instruções completas para etiquetar e proteger ficheiros |[Classificar e proteger um ficheiro ou e-mail](./rms-client/client-classify-protect.md)|
|Onde a atividade de etiquetagem está a registar |[Registo de utilização do cliente do Azure Information Protection](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client)|


>[!div class="step-by-step"]
[&#171; Passo 3](infoprotect-tutorial-step3.md)
[Passo 5 &#187;](infoprotect-tutorial-step5.md)
