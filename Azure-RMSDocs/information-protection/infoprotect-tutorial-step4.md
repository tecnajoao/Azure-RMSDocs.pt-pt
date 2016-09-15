---
title: "Passo 4 do tutorial de introdução do Azure Information Protection | Azure Information Protection"
description: "Passo 4 de um tutorial de apresentação para experimentar rapidamente o Microsoft Azure Information Protection na sua organização com apenas 4 passos que devem demorar menos de 15 minutos."
author: cabailey
manager: mbaldwin
ms.date: 09/07/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
translationtype: Human Translation
ms.sourcegitcommit: 6bbac611f9c8bba96fbbba69e8044e494134d792
ms.openlocfilehash: 2c04c749ff73050dc8a15dd984c33f700e3e6ed5


---

# Passo 4: ver classificação, etiquetas e proteção em ação 

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Agora que já tem um documento do Word aberto com o cliente Azure Information Protection instalado, está pronto para ver como é fácil iniciar a etiquetagem e proteger o seu documento, utilizando a política que configurámos.

A classificação e a proteção ocorrem quando guarda o documento, mas antes de o fazermos, vamos utilizar o nosso documento não guardado para ver como é fácil aplicar e alterar etiquetas.

### Para alterar manualmente a nossa etiqueta predefinida:

- Na barra do Information Protection, selecione a etiqueta **Pessoal**ser-lhe-á pedido para indicar a razão pela qual está a reduzir o nível de classificação. Selecione **Este ficheiro já não necessita dessa classificação**, e clique em **Confirmar**.  

    O valor **Sensibilidade** é alterado para **Pessoal**.

    ![Tutorial de início rápido do Azure Information Protection, passo 4 - pedido para indicar o motivo da redução](../media/info-protect-lower-justification.png)

### Para remover a classificação por completo:

- Na barra do Information Protection, clique no ícone **Editar etiqueta** junto a **Pessoal**. Esta ação apresenta as etiquetas disponíveis. No entanto, em vez de selecionar uma das etiquetas, desta vez, clique no ícone **Remover etiqueta**. Clique em **OK** para confirmar e fornecer a justificação para esta ação.  

    Verá que o valor **Sensibilidade** apresenta **Não definido**, a opção visualizada pelos utilizadores inicialmente se não definir uma etiqueta predefinida.

    ![Tutorial de início rápido do Azure Information Protection, passo 4 - remover classificação](../media/sensitivity-not-set.png)


### Para ver um pedido de recomendação para etiquetagem e proteção automática:

1. No documento do Word, escreva um número de cartão de crédito válido, por exemplo: **4242-4242-4242-4242**. 

2. Guarde o documento (utilize qualquer nome de ficheiro, qualquer localização). 

3. Verá então o pedido: **É recomendável etiquetar este ficheiro como Confidencial**. Clique em **Alterar agora**.

    ![Tutorial de início rápido do Azure Information Protection, passo 4 - recomendar pedido](../media/change-now.png)

    De imediato, verá a marca d'água do nome da sua organização na página, para além do rodapé de **Sensibilidade: confidencial**. 

    Se tiver escolhido a opção para aplicar um modelo de RMS, o documento é também protegido com o modelo do Azure Rights Management especificado, que pode confirmar quando clica no separador **Ficheiro** e ver as informações de **Proteger documento**. Se utilizou o modelo de confidencialidade predefinido, é apresentada uma informação a indicar que o documento está restrito a utilizadores internos (os utilizadores fora da sua organização não conseguem abrir o documento) e os respetivos conteúdos não podem ser copiados ou impressos. Como proprietário do documento, pode copiar a partir do mesmo e imprimi-lo, mas se o enviar por e-mail a outro utilizador na sua organização, o mesmo não poderá efetuar estas ações.

> [!NOTE]
>Se tiver dificuldade em concluir estes passos, no separador **Início**, no grupo **Proteção**, clique em **Proteger**, e, em seguida, clique em **Ajuda e comentários**. 
>
>Na caixa de diálogo **Microsoft Azure Information Protection**, clique em **Enviar comentários**. Esta ação envia um e-mail à equipa do Information Protection e anexa automaticamente os ficheiros de registo do seu PC para ajudar a diagnosticar problemas.

##  Passos seguintes

Agora que viu a política predefinida do Azure Information Protection, como personalizá-la e como funciona a etiquetagem para um documento do Word, experimente algumas das outras definições e saiba como funcionam nas outras aplicações do Office que suportam o Azure Information Protection: Excel, PowerPoint, Outlook. Se estas aplicações tiverem sido abertas quando instalou o cliente Azure Information Protection, feche-as e volte a abri-las antes de tentar utilizá-las com o Azure Information Protection.

Por exemplo, pode alterar o título predefinido de **Sensibilidade** na barra do Information Protection para um título à sua escolha. Pode alterar as descrições, as cores de etiqueta, a ordem das etiquetas e os respetivos nomes. Pode criar novas etiquetas e definir as suas próprias regras automáticas. Pode otimizar as marcas d'água, configurando o tamanho, a cor e mudar de diagonal para horizontal.

Tenha em atenção que se utilizar marcas d'água com o Excel, estas só estarão visíveis nos modos de Pré-visualização de impressão e Esquema de página e quando foram impressas.

Sempre que alterar quaisquer definições no portal do Azure para a política do Information Protection, lembre-se de **guardar** a política e, em seguida, **publicá-la**. Uma vez que pode fazer alterações em vários painéis, é boa ideia confirmar que nenhum painel tem o botão **Guardar** ativado relativo a alterações não guardadas. Se a sua aplicação do Office tiver sido aberta quando publicou novas alterações, feche a aplicação e volte a abri-la para transferir a política mais recente.

Quando tiver terminado o seu teste, poderá ser útil ver as [perguntas mais frequentes sobre o Azure Information Protection](faq.md).




<!--HONumber=Sep16_HO1-->


