---
title: Configurar marcas visuais para uma etiqueta do Azure Information Protection
description: "Quando atribui uma etiqueta a um documento ou a um e-mail pode selecionar várias opções para tornar a classificação escolhida facilmente visível. Estas marcas visuais são um cabeçalho, um rodapé e uma marca d'água."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: 03e7e2a4e2fc6dc75bd6c56c117c627e0c854f98
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Como configurar uma etiqueta para marcas visuais para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Quando atribui uma etiqueta a um documento ou a um e-mail pode selecionar várias opções para tornar a classificação escolhida facilmente visível. Estas marcas visuais são um cabeçalho, um rodapé e uma marca d'água.

Informações adicionais sobre este marcadores visuais:

- Os cabeçalhos e rodapés aplicam-se ao Word, ao Excel, ao PowerPoint e ao Outlook.

- As marcas d'água aplicam-se ao Word, ao Excel e ao PowerPoint:

    - Excel: as marcas d'água só estarão visíveis nos modos de Pré-visualização de impressão e Esquema de página e quando foram impressas.
    
    - PowerPoint: as arcas d'água são aplicadas ao diapositivo principal, como uma imagem de fundo.
    
    - São suportadas várias linhas de texto.

- Pode especificar apenas uma cadeia de texto ou utilizar [variáveis](#using-variables-in-the-text-string) para criar dinamicamente a cadeia de texto quando o cabeçalho, rodapé ou marca d'água for aplicada.

- Marcas visuais suportam apenas um idioma.

## <a name="when-visual-markings-are-applied"></a>Quando as marcas visuais são aplicadas

Para as mensagens de e-mail, as marcas visuais são aplicadas quando o e-mail é enviado do Outlook.

Para documentos, as marcas visuais são aplicadas da seguinte forma:

- Numa aplicação Office, de uma etiqueta, as marcas visuais são aplicadas quando a etiqueta é aplicada. Marcas visuais também são aplicadas quando um documento com nome é aberto e o documento é guardado primeiro.  

- Quando um documento assinalada como utilizando o Explorador de ficheiros ou o PowerShell, marcas visuais não são aplicadas de imediato, mas são aplicadas quando esse documento é aberto numa aplicação Office e o documento é guardado primeiro.

## <a name="to-configure-visual-markings-for-a-label"></a>Para configurar marcas visuais para uma etiqueta

Utilize as seguintes instruções para configurar marcas visuais para uma etiqueta.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Se a etiqueta que pretende configurar será aplicada a todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel.
    
    Se a etiqueta que pretende configurar está a ser um [âmbito política](configure-policy-scope.md) para que o se aplica apenas a utilizadores selecionados do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

3. No painel **Etiqueta**, na secção **Definir marcas visuais (como o cabeçalho ou o rodapé)** configure as definições para as marcas visuais que pretende e, em seguida, clique em **Guardar**:
    
    - Para configurar um cabeçalho: para **Documentos com esta etiqueta têm um cabeçalho**, selecione **Ativado** se pretender um cabeçalho e, caso contrário, clique em **Desativado**. Se selecionar **no**, em seguida, especifique o cabeçalho de texto, tamanho, [tipo de letra](#setting-the-font-name), [cor](#setting-the-font-color)e o alinhamento para o cabeçalho.
    
    - Para configurar um rodapé: para **Documentos com esta etiqueta têm um rodapé**, selecione **Ativado** se pretender um rodapé e, caso contrário, clique em **Desativar**. Se selecionar **no**, em seguida, especifique o rodapé texto, tamanho, [tipo de letra](#setting-the-font-name), [cor](#setting-the-font-color)e o alinhamento para o rodapé.
    
    - Para configurar uma marca d’água: para **Documentos com esta etiqueta têm uma marca d’água**, selecione **Ativado** se pretender uma marca d’água e, caso contrário, clique em **Desativado**. Se selecionar **no**, em seguida, especifique a marca d'água texto, tamanho, [tipo de letra](#setting-the-font-name), [cor](#setting-the-font-color)e o alinhamento para o limite de tamanho.

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## <a name="using-variables-in-the-text-string"></a>Utilizar variáveis na cadeia de texto

Pode utilizar as seguintes variáveis na cadeia de texto para o seu cabeçalho, rodapé ou marca d'água:

- `${Item.Label}` para a etiqueta selecionada. Por exemplo: Interno

- `${Item.Name}` para o nome de ficheiro ou assunto de e-mail. Por exemplo: VendasJulho.docx

- `${Item.Location}` para o nome de ficheiro e caminho para os documentos e o assunto de e-mail para os e-mails. Por exemplo: \\\Vendas\2016\T3\RelatórioJulho.docx

- `${User.Name}` para o proprietário do documento ou e-mail, por nome de utilizador com sessão iniciada no Windows. Por exemplo: rsimone

- `${User.PrincipalName}` para o proprietário do documento ou e-mail, por endereço de e-mail com sessão iniciada no cliente do Azure Information Protection (UPN). Por exemplo: rsimone@vanarsdelltd.com

- `${Event.DateTime}` para a data e hora quando a etiqueta selecionada foi definida. Por exemplo: 16/8/2016 13:30

Exemplo: se especificar a cadeia `Document: ${item.name}  Classification: ${item.label}` para o rodapé de etiqueta **Geral**, o texto do rodapé aplicado a um documento chamado projeto.docx será **Documento: projeto.docx Classificação: Geral**.

## <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Definição diferentes visuais para Word, Excel, PowerPoint e Outlook

Esta definição está atualmente em pré-visualização e requer a versão de pré-visualização do cliente Azure Information Protection.

Por predefinição, as marcas visuais que especificar são aplicadas entre Word, Excel, PowerPoint e Outlook. No entanto, pode especificar marcas visuais por tipo de aplicação do Office quando utilizar uma instrução de variável "If.App" na cadeia de texto e identifique o tipo de aplicação utilizando os valores **Word**, **Excel**, **PowerPoint**, ou **Outlook**. Também pode abbreviate estes valores e abbreiwhich é necessário se pretender especificar mais do que um na mesma instrução If.App.

Utilize a seguinte sintaxe:

    ${If.App.<application type>}<your visual markings text> ${If.End}

Esta sintaxe nesta instrução diferencia maiúsculas de minúsculas.

Exemplos:

- **Definir o texto do cabeçalho para documentos do Word apenas:**
    
    `${If.App.Word}This Word document is sensitive ${If.End}`
    
    No Word documento cabeçalhos só, a etiqueta se aplica o texto do cabeçalho "neste documento do Word é sensível a maiúsculas e minúsculas". O texto do cabeçalho não é aplicado a outras aplicações do Office.

- **Definir o texto do rodapé para Word, Excel e o Outlook e o texto do rodapé diferente para o PowerPoint:**
    
    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`
    
    No Word, Excel e o Outlook, a etiqueta aplica-se o texto do rodapé "este conteúdo é confidencial." Nos PowerPoint, a etiqueta aplica-se o texto do rodapé "desta apresentação é confidencial."

- **Definir o texto da marca de água específico para Word e ao PowerPoint e, em seguida, marca d'água texto para Word, Excel e PowerPoint:**
    
    `${If.App.WP}This content is ${If.End}Confidential`
    
    No Word e PointPoint, a etiqueta se aplica o texto da marca de água "este conteúdo é confidencial". No Excel, a etiqueta aplica-se o texto da marca de água "Confidencial". No Outlook, a etiqueta não qualquer texto da marca de água porque as marcas d'água como marcas visuais não são suportadas para o Outlook.

### <a name="setting-the-font-name"></a>O nome de tipo de letra da definição

Esta definição está atualmente em pré-visualização.

Calibri é o tipo de letra predefinido para cabeçalhos, rodapés de página e texto da marca de água. Se especificar um nome de tipo de letra alternativo, certifique-se de que está disponível nos dispositivos cliente que serão aplicadas as marcas visuais. Caso contrário, o tipo de letra que será utilizado não é determinística. 

Se tiver a versão de pré-visualização do cliente Azure Information Protection e o tipo de letra especificado não está disponível, o cliente utilizará o tipo de letra Calibri.

### <a name="setting-the-font-color"></a>Definir a cor do tipo de letra

Pode selecionar na lista de cores disponíveis ou especificar uma cor personalizada introduzindo um código hexadecimal triplet para os componentes de (RGB) vermelho, verdes e azuis da cor. Por exemplo, **#DAA520**. 

Se precisar de uma referência para estes códigos [cores pelo nome](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx) partir o MSDN, documentação é de um ponto de partida útil. Encontrará também estes códigos em muitas aplicações permitem-lhe editar imagens. Por exemplo, a Microsoft Paint permite-lhe escolher uma cor personalizada a partir de uma paleta e os valores RGB são apresentados automaticamente, que, em seguida, pode copiar.

## <a name="next-steps"></a>Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
