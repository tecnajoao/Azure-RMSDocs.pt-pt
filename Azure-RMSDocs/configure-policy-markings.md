---
title: Configurar marcas visuais para uma etiqueta do Azure Information Protection
description: Quando atribui uma etiqueta a um documento ou a um e-mail pode selecionar várias opções para tornar a classificação escolhida facilmente visível. Estas marcas visuais são um cabeçalho, um rodapé e uma marca d'água.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/28/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: 23185d2d6b5b1bb14633647c345d0e58eeda3bdc
ms.sourcegitcommit: e72c89e35cae6a19dca060f688838d78dc8f0448
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/29/2018
ms.locfileid: "52585997"
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Como configurar uma etiqueta para marcas visuais para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Quando atribui uma etiqueta a um documento ou a um e-mail pode selecionar várias opções para tornar a classificação escolhida facilmente visível. Estas marcas visuais são um cabeçalho, um rodapé e uma marca d'água. 

Obter informações adicionais sobre estas marcas visuais:

- Os cabeçalhos e rodapés aplicam-se ao Word, ao Excel, ao PowerPoint e ao Outlook.

- As marcas d'água aplicam-se ao Word, ao Excel e ao PowerPoint:

    - Excel: as marcas d'água só estarão visíveis nos modos de Pré-visualização de impressão e Esquema de página e quando foram impressas.
    
    - PowerPoint: as arcas d'água são aplicadas ao diapositivo principal, como uma imagem de fundo. Na **exibição** separador, **Slide mestre**, certifique-se de que o **ocultar gráficos de plano de fundo** não está selecionada a caixa de verificação.

- Várias linhas são suportadas para as marcas d'água e para cabeçalhos e rodapés do Word, Excel e PowerPoint. Se especificar várias linhas para o cabeçalho ou rodapé é aplicada uma etiqueta no Outlook, as linhas são concatenadas. Neste cenário, considere utilizar a configuração para [definir diferentes marcas visuais para Word, Excel, PowerPoint e Outlook](##setting-different-visual-markings-for-word-excel-powerpoint-and-outlook).

- Comprimentos de cadeia de caracteres máximo:
    
    - O comprimento máximo da cadeia que pode introduzir para cabeçalhos e rodapés é de 1024 caracteres. No entanto, o Excel tem um limite total de 255 carateres para cabeçalhos e rodapés. Ao introduzir uma cadeia longa para cabeçalhos e rodapés, no Excel, este texto pode ser truncada de 255 carateres ou menos.
    
    - O comprimento máximo da cadeia para marcas de água que pode introduzir é 255 carateres.

- Pode especificar apenas uma cadeia de texto ou utilizar [variáveis](#using-variables-in-the-text-string) para criar dinamicamente a cadeia de texto quando o cabeçalho, rodapé ou marca d'água for aplicada.

- Word, PowerPoint, Outlook e agora Excel suportam marcas visuais com cores diferentes.

- Marcas visuais suportam apenas um idioma.

## <a name="when-visual-markings-are-applied"></a>Quando as marcas visuais são aplicadas

Para as mensagens de e-mail, as marcas visuais são aplicadas quando o e-mail é enviado do Outlook.

Para documentos, as marcas visuais são aplicadas da seguinte forma:

- Num aplicativo do Office, as marcas visuais de uma etiqueta são aplicadas quando a etiqueta é aplicada. Marcas visuais também são aplicadas quando um documento etiquetado é aberto e o documento é salvo em primeiro lugar.  

- Quando um documento tem o nome, utilizando o Explorador de ficheiros, o PowerShell ou o scanner do Azure Information Protection: marcas visuais não são aplicadas imediatamente, mas são aplicadas pelo cliente do Azure Information Protection quando esse documento é aberto num aplicativo do Office e o documento é salvo em primeiro lugar.
    
    A exceção é quando usar [gravação automática](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) com o Office 2016 para os ficheiros que são guardados no SharePoint Online, OneDrive ou OneDrive para empresas: gravação automática quando estiver ativado, marcas visuais não são aplicadas a menos que configure o [ definição de cliente avançado](./rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background) para ativar a classificação para executar continuamente em segundo plano. 

## <a name="to-configure-visual-markings-for-a-label"></a>Para configurar marcas visuais para uma etiqueta

Utilize as seguintes instruções para configurar marcas visuais para uma etiqueta.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção de menu: no **do Azure Information Protection – etiquetas** painel, selecione a etiqueta que contém o elemento visual marcas que pretende adicionar ou alterar.

3. Sobre o **etiqueta** painel, na **definir marcas visuais (como o cabeçalho ou rodapé)** secção, configure as definições para as marcas visuais que pretende e, em seguida, clique em **guardar**:
    
    - Para configurar um cabeçalho: para **Documentos com esta etiqueta têm um cabeçalho**, selecione **Ativado** se pretender um cabeçalho e, caso contrário, clique em **Desativado**. Se selecionar **no**, em seguida, especifique o cabeçalho de texto, tamanho, [tipo de letra](#setting-the-font-name), [cor](#setting-the-font-color)e o alinhamento para o cabeçalho.
    
    - Para configurar um rodapé: para **Documentos com esta etiqueta têm um rodapé**, selecione **Ativado** se pretender um rodapé e, caso contrário, clique em **Desativar**. Se selecionar **no**, em seguida, especifique o rodapé de texto, tamanho, [tipo de letra](#setting-the-font-name), [cor](#setting-the-font-color)e o alinhamento para o rodapé.
    
    - Para configurar uma marca d’água: para **Documentos com esta etiqueta têm uma marca d’água**, selecione **Ativado** se pretender uma marca d’água e, caso contrário, clique em **Desativado**. Se selecionou **no**, em seguida, especifique a marca d'água texto, tamanho, [tipo de letra](#setting-the-font-name), [cor](#setting-the-font-color)e o alinhamento para o limite de tamanho.
    
Quando clica em **guardar**, as suas alterações estão automaticamente disponíveis para utilizadores e serviços. Já não existe uma opção de publicar separado.


## <a name="using-variables-in-the-text-string"></a>Utilizar variáveis na cadeia de texto

Pode utilizar as seguintes variáveis na cadeia de texto para o seu cabeçalho, rodapé ou marca d'água:

- `${Item.Label}` para a etiqueta selecionada. Por exemplo: geral

- `${Item.Name}` para o nome de ficheiro ou assunto de e-mail. Por exemplo: VendasJulho.docx

- `${Item.Location}` para o nome de ficheiro e caminho para os documentos e o assunto de e-mail para os e-mails. Por exemplo: \\\Vendas\2016\T3\RelatórioJulho.docx

- `${User.Name}` para o proprietário do documento ou e-mail, por nome de utilizador com sessão iniciada no Windows. Por exemplo: rsimone

- `${User.PrincipalName}` para o proprietário do documento ou e-mail, por endereço de e-mail com sessão iniciada no cliente do Azure Information Protection (UPN). Por exemplo: rsimone@vanarsdelltd.com

- `${Event.DateTime}` para a data e hora quando a etiqueta selecionada foi definida. Por exemplo: 16/8/2016 13:30

Exemplo: se especificar a cadeia `Document: ${item.name}  Classification: ${item.label}` para o rodapé de etiqueta **Geral**, o texto do rodapé aplicado a um documento chamado projeto.docx será **Documento: projeto.docx Classificação: Geral**.

>[!TIP]
> Também é usar um [campo de código para inserir o nome de rótulo](faqs-infoprotect.md#can-i-create-a-document-template-that-automatically-includes-the-classification) num documento ou modelo.

## <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Definir diferentes marcas visuais para Word, Excel, PowerPoint e Outlook

Por predefinição, as marcas visuais que especificar são aplicadas em Word, Excel, PowerPoint e Outlook. No entanto, pode especificar as marcas visuais por tipo de aplicação do Office quando utilizar uma instrução de variável "If.App" na cadeia de texto e identifique o tipo de aplicação com os valores **Word**, **Excel**, **PowerPoint**, ou **Outlook**. Também pode abreviar estes valores e abbreiwhich é necessário se pretender especificar mais do que uma na mesma instrução If.App.

Utilize a seguinte sintaxe:

    ${If.App.<application type>}<your visual markings text> ${If.End}

Essa sintaxe nesta declaração diferencia maiúsculas de minúsculas.

Exemplos:

- **Definir o texto do cabeçalho para documentos do Word só:**
    
    `${If.App.Word}This Word document is sensitive ${If.End}`
    
    No Word documento apenas cabeçalhos, a etiqueta aplicar o texto do cabeçalho "este documento do Word é sensível a maiúsculas e minúsculas". Sem texto do cabeçalho é aplicado a outros aplicativos do Office.

- **Definir o texto do rodapé para Word, Excel e Outlook e o texto do rodapé diferentes para o PowerPoint:**
    
    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`
    
    No Word, Excel e Outlook, a etiqueta aplica-se o texto do rodapé "este conteúdo é confidencial". No PowerPoint, a etiqueta aplica-se o texto do rodapé "Esta apresentação é confidencial".

- **Definir o texto da marca d'água específico para o Word e PowerPoint e, em seguida, marca d'água texto para Word, Excel e PowerPoint:**
    
    `${If.App.WP}This content is ${If.End}Confidential`
    
    No Word e PointPoint, a etiqueta aplicar o texto da marca d'água "este conteúdo é confidencial". No Excel, a etiqueta, aplica-se o texto da marca d'água "Confidencial". No Outlook, a etiqueta não qualquer texto da marca d'água, uma vez que as marcas d'água, como marcas visuais não são suportadas para o Outlook.

### <a name="setting-the-font-name"></a>Definição do nome de tipo de letra

Calibri é o tipo de letra predefinido para cabeçalhos, rodapés e texto da marca d'água. Se especificar um nome de tipo de letra alternativo, certifique-se de que está disponível nos dispositivos cliente que serão aplicadas as marcas visuais. 

Se o tipo de letra especificado não estiver disponível, o cliente utilizará o tipo de letra Calibri.

### <a name="setting-the-font-color"></a>Definir a cor do tipo de letra

Pode escolher a partir da lista de cores disponíveis ou especificar uma cor personalizada ao introduzir um código terno hexadecimal dos componentes de (RGB) de vermelho, verde e azul da cor. Por exemplo, **#DAA520**. 

Se precisar de uma referência para estes códigos [cores por nome](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx) da MSDN documentação é um ponto de partida útil. Também encontrar estes códigos em muitos aplicativos que permitem editar imagens. Por exemplo, o Microsoft Paint permite que escolha uma cor personalizada a partir de uma paleta e os valores RGB são apresentados automaticamente, que, em seguida, pode ser copiado.

## <a name="next-steps"></a>Passos Seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

