---
title: Configurar etiquetas e modelos para diferentes idiomas no Azure Information Protection – AIP
description: Pode adicionar suporte para idiomas diferentes para as etiquetas que os utilizadores veem na barra do Information Protection e para todos os modelos que os utilizadores veem, especificando os idiomas na política do Azure Information Protection e importar as suas traduções.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/03/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ms.openlocfilehash: 82dc592263117d075cb3793b9034a8adc0f1ca15
ms.sourcegitcommit: 7283b7c7619d65b5e8272d51bbf85a1bc846befd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58867522"
---
# <a name="how-to-configure-labels-and-templates-for-different-languages-in-azure-information-protection"></a>Como configurar etiquetas e modelos para diferentes idiomas no Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Embora as etiquetas predefinidas do Azure Information Protection suportam vários idiomas, tem de configurar o suporte para nomes de etiqueta e descrições que especificar. Esta configuração requer que faça o seguinte:

1. Selecione os idiomas que os utilizadores utilizam. 

2. Exporte seus nomes de etiqueta atuais e descrições para um ficheiro.

3. Edite o ficheiro para suas traduções.

4. Importe o ficheiro novamente para a política do Azure Information Protection.

Também pode configurar modelos para idiomas diferentes quando uma das seguintes condições aplicam-se. Esta configuração é adequada se os utilizadores ou administradores precisam de ver o nome do modelo atual e a descrição em seus idiomas localizados.

- O modelo foi criado no portal clássico do Azure ou através do PowerShell e o modelo não está ligado a uma etiqueta ao utilizar o **selecionar um modelo predefinido** definição de proteção.

- Não tem uma subscrição que suporta etiquetas, pelo que só pode criar e gerir modelos no portal do Azure.

Selecione os idiomas que correspondem à definição de idioma do Office e do Windows. Estes nomes de etiqueta e descrições apresentam então a barra do Azure Information Protection nas aplicações do Office e no **classificar e proteger – Azure Information Protection** caixa de diálogo, respectivamente. Para obter mais informações sobre os idiomas que são escolhidos, veja a secção [Como o cliente do Azure Information Protection determina o idioma a apresentar](#how-the-azure-information-protection-client-determines-the-language-to- display) nesta página. 

## <a name="to-configure-labels-and-templates-for-different-languages"></a>Configurar etiquetas e modelos para diferentes idiomas

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **Manage** > **idiomas** opção de menu: Sobre o **do Azure Information Protection - idiomas** painel, selecione **adicionar um novo idioma para tradução**. Selecione os idiomas que pretende adicionar e, em seguida, selecione **OK**. Pode digitar o nome do idioma na caixa de pesquisa ou percorra a lista de idiomas de disponíveis

3. Os idiomas selecionados agora apresentam no **do Azure Information Protection - idiomas** painel:
    
    - Para adicionar outro idioma, selecione **adicionar um novo idioma para tradução** e repita o passo anterior. 
        
        > [!NOTE]
        > Certifique-se de que seleciona os idiomas que os seus utilizadores têm para o Office e para o Windows. Em alguns casos, isto pode exigir duas seleções diferentes por computador.
        
    - Se mudar de ideias sobre qualquer idioma que adicionou, selecione a entrada na lista e, em seguida, clique em **Remover**.

4. Quando todos os idiomas que deseja suportar estão listados, selecione a caixa de verificação junto a **NOME DO IDIOMA** para selecionar todas as entradas (ou, em alternativa, selecione as entradas individuais) e, em seguida, clique em **Exportar** para guardar uma cópia local dos nomes das etiquetas e das descrições existentes num ficheiro. 
    
    O ficheiro transferido é denominado **localização exportada.zip** e é guardado na pasta de Transferências local. Este também pode ser acedido ao selecionar este nome de ficheiro na barra de estado no portal do Azure.

5. Extraia os ficheiros da **localização exportada. zip** para que tenha arquivos. XML para cada idioma que selecionou para transferência. 

6. Edite cada ficheiro. XML: Para cada cadeia dentro de `<LocalizedText>` etiquetas, apresente as traduções que deseja para cada idioma escolhido. 

7. Quando tiver editado cada ficheiro .xml, crie uma nova pasta comprimida (zipada) que contém estes ficheiros. A pasta comprimida pode ter qualquer nome, mas deve ter uma extensão .zip.
    
    Sugestão: Não tenha de esperar até que tive editado cada ficheiro de idioma que baixou. Em vez disso, pode implementar linguagens diferentes num mannor em fases, incluindo no ficheiro. zip um subconjunto do total de ficheiros que transferiu. Em seguida, repita os passos 7 e 8 quando tiver concluído as traduções de mais idiomas.

8. Retorno para o **do Azure Information Protection - idiomas** painel e selecione **importação**. Note que, se essa opção não estiver disponível, primeiro desmarque a caixa de verificação **NOME DO IDIOMA** ou as caixas de verificação para os idiomas selecionados individualmente.
    
    Quando a importação estiver concluída, os nomes localizados e as descrições são transferidos para os utilizadores.

Tem de repetir este procedimento se precisar de suporte uma nova linguagem, criar novas etiquetas ou alterar o nome ou descrição das etiquetas no portal do Azure.

## <a name="how-the-azure-information-protection-client-determines-the-language-to-display"></a>Como o cliente do Azure Information Protection determina o idioma a apresentar

Quando os utilizadores transferem uma política do Azure Information Protection que suporta idiomas diferentes, o idioma que os utilizadores veem para os seus nomes de etiqueta e descrições é determinado pela seguinte lógica:

**Para as etiquetas e descrições que os utilizadores veem na barra do Azure Information Protection em aplicações do Office:**

- Quando há uma correspondência direta do idioma da sua aplicação do Office, os nomes de etiqueta e as descrições são apresentados nesse idioma.

- Quando não há nenhuma correspondência do idioma da sua aplicação do Office, os nomes de etiqueta e as descrições são apresentados no idioma especificado por predefinição de todos os utilizadores. Este idioma é normalmente o inglês, que é o idioma utilizado na política predefinida.

**Para as etiquetas e descrições que os utilizadores veem quando utilizam a tecla direita do rato para classificar e proteger ficheiros ou pastas:**

- Quando há uma correspondência direta do idioma do seu sistema operativo, os nomes de etiqueta e as descrições são apresentados nesse idioma.

- Quando não há nenhuma correspondência do idioma do seu sistema operativo, os nomes de etiqueta e as descrições são apresentados no idioma especificado por predefinição de todos os utilizadores. Este idioma é normalmente o inglês, que é o idioma utilizado na política predefinida.

## <a name="when-localized-label-names-are-not-used"></a>Quando os nomes de etiqueta localizados não são utilizados

Nos seguintes cenários, os nomes de etiqueta (e subetiqueta) localizados não são utilizados. Para obter consistência com o seu inquilino, o idioma predefinido sempre utilizado é o seguinte:

- Registos de utilização do cliente

- PowerShell (saída de Get-AIPFileStatus)

- Metadados de documento e cabeçalhos de e-mail


## <a name="next-steps"></a>Passos Seguintes

Para obter mais informações sobre como configurar as opções que pode fazer para uma etiqueta e outras definições para as políticas do Azure Information Protection, utilize as ligações na [configurar a política da sua organização](configure-policy.md#configuring-your-organizations-policy) secção.



