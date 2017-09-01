---
title: Configurar as etiquetas e modelos para idiomas diferentes no Azure Information Protection
description: "Pode adicionar suporte para idiomas diferentes para as etiquetas que os utilizadores veem na barra do Information Protection e para todos os modelos que os utilizadores veem, ao especificar os idiomas numa política do Azure Information Protection e importar as traduções."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ms.openlocfilehash: 33666be46b9b2fc022e541ec710a0be596f4ede0
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2017
---
# <a name="how-to-configure-labels-and-templates-for-different-languages-in-azure-information-protection"></a>Como configurar as etiquetas e modelos para idiomas diferentes no Azure Information Protection

>*Aplica-se a: Azure Information Protection*

>[!NOTE]
>Esta funcionalidade está atualmente em pré-visualização, a ser utilizado em conjunto com a atual **pré-visualização** versão do cliente Azure Information Protection que pode transferir a partir de [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Embora as etiquetas predefinidas para o Azure Information Protection suportam vários idiomas, tem de configurar o suporte para os nomes das etiquetas e descrições que especificar. Esta configuração requer que efetue o seguinte:

1. Selecione os idiomas que utilizam os seus utilizadores. 

2. Exporte os nomes de etiqueta atual e descrições para um ficheiro.

3. Edite o ficheiro para fornecer as traduções.

4. Importe o ficheiro de volta para a política do Azure Information Protection.

Também pode configurar modelos para idiomas diferentes quando uma das seguintes condições aplicam-se. Esta configuração é apropriada se os utilizadores ou administradores precisam de ver o nome do modelo atual e a descrição no respetivo idioma localizado.

- O modelo foi criado no portal clássico do Azure ou através do PowerShell e o modelo não está ligado a uma etiqueta, utilizando o **selecionar um modelo predefinido** definição de proteção.

- Não dispõe de uma subscrição que suporta etiquetas, pelo que só pode criar e gerir modelos no portal do Azure.

Selecione os idiomas que correspondem à definição de idioma do Office e do Windows. Estes nomes de etiqueta e descrições apresentam então a barra do Azure Information Protection em aplicações do Office, e na caixa de diálogo **Classificar e proteção - Azure Information Protection**, respetivamente. Para obter mais informações sobre os idiomas que são escolhidos, veja a secção [Como o cliente do Azure Information Protection determina o idioma a apresentar](#how-the-azure-information-protection-client-determines-the-language-to- display) nesta página. 

## <a name="to-configure-labels-and-templates-for-different-languages"></a>Para configurar as etiquetas e modelos para idiomas diferentes

1. Se ainda não o fez, inicie sessão no [portal do Azure](https://portal.azure.com) como um administrador de segurança ou um administrador global e, em seguida, navegue para o **Azure Information Protection** painel. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Do **GERIR** selecção de menu, selecione **idiomas (pré-visualização)**.

3. No **Azure Information Protection - idiomas (pré-visualização)** painel, selecione **adicionar um novo idioma para tradução**. Selecione os idiomas que pretende adicionar e, em seguida, selecione **OK**. Pode escrever o nome do idioma na caixa de pesquisa ou deslocar a lista dos idiomas disponíveis

4. Os idiomas selecionados agora a apresentar no **Azure Information Protection - idiomas (pré-visualização)** painel:
    
    - Para adicionar outro idioma, selecione **adicionar um novo idioma para tradução** e repita o passo anterior. 
        
        > [!NOTE]
        > Certifique-se de que seleciona os idiomas que os seus utilizadores têm para o Office e para o Windows. Em alguns casos, isto pode exigir duas seleções diferentes por computador.
        
    - Se mudar de ideias sobre qualquer idioma que adicionou, selecione a entrada na lista e, em seguida, clique em **Remover**.

5. Quando todos os idiomas que deseja suportar estão listados, selecione a caixa de verificação junto a **NOME DO IDIOMA** para selecionar todas as entradas (ou, em alternativa, selecione as entradas individuais) e, em seguida, clique em **Exportar** para guardar uma cópia local dos nomes das etiquetas e das descrições existentes num ficheiro. 
    
    O ficheiro transferido é denominado **localização exportada.zip** e é guardado na pasta de Transferências local. Este também pode ser acedido ao selecionar este nome de ficheiro na barra de estado no portal do Azure.

6. Extraia os ficheiros da **localização exportada.zip**, para que tenha os ficheiros .xml para cada idioma que selecionou para transferência. 

7. Edite cada ficheiro .xml: para cada cadeia dentro de etiquetas `<LocalizedText>`, apresente as traduções que deseja para cada idioma escolhido. 

8. Quando tiver editado cada ficheiro .xml, crie uma nova pasta comprimida (zipada) que contém estes ficheiros. A pasta comprimida pode ter qualquer nome, mas deve ter uma extensão .zip.

9. Volte à **Azure Information Protection - idiomas (pré-visualização)** painel e selecione **importação**. Note que, se essa opção não estiver disponível, primeiro desmarque a caixa de verificação **NOME DO IDIOMA** ou as caixas de verificação para os idiomas selecionados individualmente.
    
    Quando a importação estiver concluída, a transferência de nomes e descrições localizada para os utilizadores depois de publicar junto a política do Azure Information Protection. Pode clicar em **Publicar** a partir do painel **Política global** ou **Políticas de âmbito**.

## <a name="how-the-azure-information-protection-client-determines-the-language-to-display"></a>Como o cliente do Azure Information Protection determina o idioma a apresentar

Quando os utilizadores transferem uma política do Azure Information Protection que suporta idiomas diferentes, o idioma que os utilizadores veem para os seus nomes de etiqueta e descrições é determinado pela seguinte lógica:

**Para as etiquetas e descrições que os utilizadores veem na barra do Azure Information Protection em aplicações do Office:**

- Quando há uma correspondência direta do idioma da sua aplicação do Office, os nomes de etiqueta e as descrições são apresentados nesse idioma.

- Quando não há nenhuma correspondência do idioma da sua aplicação do Office, os nomes de etiqueta e as descrições são apresentados no idioma especificado por predefinição de todos os utilizadores. Este idioma é normalmente o inglês, que é o idioma utilizado na política predefinida.

**Para as etiquetas e descrições que os utilizadores veem quando utilizam a tecla direita do rato para classificar e proteger ficheiros ou pastas:**

- Quando há uma correspondência direta do idioma do seu sistema operativo, os nomes de etiqueta e as descrições são apresentados nesse idioma.

- Quando não há nenhuma correspondência do idioma do seu sistema operativo, os nomes de etiqueta e as descrições são apresentados no idioma especificado por predefinição de todos os utilizadores. Este idioma é normalmente o inglês, que é o idioma utilizado na política predefinida.

## <a name="when-localized-label-names-are-not-used"></a>Quando os nomes de etiqueta localizados não são utilizados

Nos cenários a seguir, os nomes de etiqueta (e subetiqueta) localizados não são utilizados. Para obter consistência com o seu inquilino, o idioma predefinido sempre utilizado é o seguinte:

- Registos de utilização do cliente

- PowerShell (saída de Get-AIPFileStatus)

- Metadados de documento e cabeçalhos de e-mail


## <a name="next-steps"></a>Passos seguintes

Para mais informações sobre como configurar as opções que pode efetuar em relação a uma etiqueta e outras definições para a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


