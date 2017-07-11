---
title: Configure etiquetas para diferentes idiomas no Azure Information Protection
description: "Pode adicionar suporte a idiomas diferentes nas etiquetas que os utilizadores veem na barra Information Protection, ao especificar os idiomas na política do Azure Information Protection e importar as suas traduções."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ms.openlocfilehash: ec99bf36e8904a7304a9d33c32d17ba92e2e22d2
ms.sourcegitcommit: 8b768e7e249e124f24acdf630d165eaf743f9c21
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/05/2017
---
<a id="how-to-configure-labels-for-different-languages-in-azure-information-protection" class="xliff"></a>

# Como configurar etiquetas para diferentes idiomas no Azure Information Protection

>*Aplica-se a: Azure Information Protection*

>[!NOTE]
>Esta funcionalidade está atualmente em pré-visualização, para ser utilizada em conjunto com a versão de **pré-visualização** do cliente do Azure Information Protection que pode transferir a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Por predefinição, os nomes e as descrições das etiquetas suportam um único idioma que é apresentado para todos os utilizadores na sua organização. Pode adicionar suporte para idiomas diferentes ao selecionar os que precisa, exportar os seus nomes de etiqueta atuais e descrições para um ficheiro, editar o ficheiro para apresentar as suas traduções e, em seguida, importar o ficheiro novamente para a política do Azure Information Protection.

Selecione os idiomas que correspondem à definição de idioma do Office e do Windows. Estes nomes de etiqueta e descrições apresentam então a barra do Azure Information Protection em aplicações do Office, e na caixa de diálogo **Classificar e proteção - Azure Information Protection**, respetivamente. Para obter mais informações sobre os idiomas que são escolhidos, veja a secção [Como o cliente do Azure Information Protection determina o idioma a apresentar](#how-the-azure-information-protection-client-determines-the-language-to- display) nesta página. 

<a id="to-configure-labels-to-display-in-different-languages" class="xliff"></a>

## Configurar etiquetas para apresentar diferentes idiomas

1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global e navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. No painel inicial **Azure Information Protection**, encontre **GERIR**e, em seguida, selecione **Idiomas (Pré-visualização)**.

3. No painel **Azure Information Protection - Idiomas (Pré-visualização)**, encontre o primeiro idioma que deseja adicionar, ao escrever o nome na caixa de pesquisa ou ao deslocar pela lista de idiomas disponíveis. 

4. Selecione o seu idioma e selecione **OK**.

5. No próximo painel, verá o idioma selecionado adicionado a uma lista:
    
    - Para adicionar outro idioma, selecione **Adicionar um novo idioma para tradução** e repita os passos 3 e 4. 
        
        > [!NOTE]
        > Certifique-se de que seleciona os idiomas que os seus utilizadores têm para o Office e para o Windows. Em alguns casos, isto pode exigir duas seleções diferentes por computador.
        
    - Se mudar de ideias sobre qualquer idioma que adicionou, selecione a entrada na lista e, em seguida, clique em **Remover**.

6. Quando todos os idiomas que deseja suportar estão listados, selecione a caixa de verificação junto a **NOME DO IDIOMA** para selecionar todas as entradas (ou, em alternativa, selecione as entradas individuais) e, em seguida, clique em **Exportar** para guardar uma cópia local dos nomes das etiquetas e das descrições existentes num ficheiro. 
    
    O ficheiro transferido é denominado **localização exportada.zip** e é guardado na pasta de Transferências local. Este também pode ser acedido ao selecionar este nome de ficheiro na barra de estado no portal do Azure.

7. Extraia os ficheiros da **localização exportada.zip**, para que tenha os ficheiros .xml para cada idioma que selecionou para transferência. 

8. Edite cada ficheiro .xml: para cada cadeia dentro de etiquetas `<LocalizedText>`, apresente as traduções que deseja para cada idioma escolhido. 

9. Quando tiver editado cada ficheiro .xml, crie uma nova pasta comprimida (zipada) que contém estes ficheiros. A pasta comprimida pode ter qualquer nome, mas deve ter uma extensão .zip.

10. Regresse ao painel do portal do Azure e selecione **Importação**. Note que, se essa opção não estiver disponível, primeiro desmarque a caixa de verificação **NOME DO IDIOMA** ou as caixas de verificação para os idiomas selecionados individualmente.
    
    Quando a importação é concluída, os nomes das etiquetas e das descrições são transferidos para os utilizadores depois de publicar a política do Azure Information Protection. Pode clicar em **Publicar** a partir do painel **Política global** ou **Políticas de âmbito**.

<a id="how-the-azure-information-protection-client-determines-the-language-to-display" class="xliff"></a>

## Como o cliente do Azure Information Protection determina o idioma a apresentar

Quando os utilizadores transferem uma política do Azure Information Protection que suporta idiomas diferentes, o idioma que os utilizadores veem para os seus nomes de etiqueta e descrições é determinado pela seguinte lógica:

**Para as etiquetas e descrições que os utilizadores veem na barra do Azure Information Protection em aplicações do Office:**

- Quando há uma correspondência direta do idioma da sua aplicação do Office, os nomes de etiqueta e as descrições são apresentados nesse idioma.

- Quando não há nenhuma correspondência do idioma da sua aplicação do Office, os nomes de etiqueta e as descrições são apresentados no idioma especificado por predefinição de todos os utilizadores. Este idioma é normalmente o inglês, que é o idioma utilizado na política predefinida.

**Para as etiquetas e descrições que os utilizadores veem quando utilizam a tecla direita do rato para classificar e proteger ficheiros ou pastas:**

- Quando há uma correspondência direta do idioma do seu sistema operativo, os nomes de etiqueta e as descrições são apresentados nesse idioma.

- Quando não há nenhuma correspondência do idioma do seu sistema operativo, os nomes de etiqueta e as descrições são apresentados no idioma especificado por predefinição de todos os utilizadores. Este idioma é normalmente o inglês, que é o idioma utilizado na política predefinida.

<a id="when-localized-label-names-are-not-used" class="xliff"></a>

## Quando os nomes de etiqueta localizados não são utilizados

Nos cenários a seguir, os nomes de etiqueta (e subetiqueta) localizados não são utilizados. Para obter consistência com o seu inquilino, o idioma predefinido sempre utilizado é o seguinte:

- Registos de utilização do cliente

- PowerShell (saída de Get-AIPFileStatus)

- Metadados de documento e cabeçalhos de e-mail


<a id="next-steps" class="xliff"></a>

## Passos seguintes

Para mais informações sobre como configurar as opções que pode efetuar em relação a uma etiqueta e outras definições para a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


