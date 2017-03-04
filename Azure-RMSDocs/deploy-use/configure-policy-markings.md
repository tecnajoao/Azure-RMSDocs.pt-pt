---
title: Configurar marcas visuais para uma etiqueta do Azure Information Protection
description: "Quando atribui uma etiqueta a um documento ou a um e-mail pode selecionar várias opções para tornar a classificação escolhida facilmente visível. Estas marcas visuais são um cabeçalho, um rodapé e uma marca d&quot;água."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 4ddacf2be34cb7921dfbe282a0476a8cd47de2cf
ms.lasthandoff: 02/24/2017


---

# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Como configurar uma etiqueta para marcas visuais para o Azure Information Protection

>*Aplica-se a: Azure Information Protection*

Quando atribui uma etiqueta a um documento ou a um e-mail pode selecionar várias opções para tornar a classificação escolhida facilmente visível. Estas marcas visuais são um cabeçalho, rodapé e uma marca d'água:

As marcas visuais são aplicadas a documentos do Word, do Excel e do PowerPoint quando a etiqueta é aplicada e quando o documento é guardado. Para e-mails, as marcas visuais são aplicadas quando o e-mail é enviado.

Informações adicionais sobre este marcadores visuais:

- Os cabeçalhos e rodapés aplicam-se ao Word, ao Excel, ao PowerPoint e ao Outlook.

- As marcas d'água aplicam-se ao Word, ao Excel e ao PowerPoint:

    - Excel: as marcas d'água só estarão visíveis nos modos de Pré-visualização de impressão e Esquema de página e quando foram impressas.

    - PowerPoint: as arcas d'água são aplicadas ao diapositivo principal, como uma imagem de fundo.

- Pode especificar apenas uma cadeia de texto ou utilizar [variáveis](#using-variables-in-the-text-string) para criar dinamicamente a cadeia de texto quando o cabeçalho, rodapé ou marca d'água for aplicada. 

Utilize as seguintes instruções para configurar marcas visuais para uma etiqueta.

1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global e navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a etiqueta que pretende configurar para marcas visuais se aplicar a todos os utilizadores, selecione a etiqueta a alterar no painel **Política:Global**. 

     Se a etiqueta que pretende configurar estiver numa [política de âmbito](configure-policy-scope.md) para ser aplicada apenas a utilizadores selecionados, selecione primeiro essa política de âmbito no painel inicial do **Azure Information Protection**.

3. No painel **Etiqueta**, na secção **Definir marcas visuais (como o cabeçalho ou o rodapé)** configure as definições para as marcas visuais que pretende e, em seguida, clique em **Guardar**:

    - Para configurar um cabeçalho: para **Documentos com esta etiqueta têm um cabeçalho**, selecione **Ativado** se pretender um cabeçalho e, caso contrário, clique em **Desativado**. Se selecionar **Ativado**, em seguida, especifique o texto do cabeçalho, o tamanho, a cor e o alinhamento para o cabeçalho.
    
    - Para configurar um rodapé: para **Documentos com esta etiqueta têm um rodapé**, selecione **Ativado** se pretender um rodapé e, caso contrário, clique em **Desativar**. Se selecionar **Ativado**, em seguida, especifique o texto do rodapé, o tamanho, a cor e o alinhamento para o cabeçalho.
    
    - Para configurar uma marca d’água: para **Documentos com esta etiqueta têm uma marca d’água**, selecione **Ativado** se pretender uma marca d’água e, caso contrário, clique em **Desativado**. Se selecionar **Ativado**, em seguida, especifique o texto da marca d’água, o tamanho, a cor e o modelo para o cabeçalho. 

4. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## <a name="using-variables-in-the-text-string"></a>Utilizar variáveis na cadeia de texto

Pode utilizar as seguintes variáveis na cadeia de texto para o seu cabeçalho, rodapé ou marca d'água:

- `${Item.Label}` para a etiqueta selecionada. Por exemplo: Interno

- `${Item.Name}` para o nome de ficheiro ou assunto de e-mail. Por exemplo: VendasJulho.docx

- `${Item.Location}` para o nome de ficheiro e caminho para os documentos e o assunto de e-mail para os e-mails. Por exemplo: \\\Vendas\2016\T3\RelatórioJulho.docx

- `${User.Name}` para o proprietário do documento ou e-mail, por nome de utilizador com sessão iniciada no Windows. Por exemplo: rsimone

- `${User.PrincipalName}` para o proprietário do documento ou e-mail, por endereço de e-mail com sessão iniciada no cliente do Azure Information Protection (UPN). Por exemplo: rsimone@vanarsdelltd.com

- `${Event.DateTime}` para a data e hora quando a etiqueta selecionada foi definida. Por exemplo: 16/8/2016 13:30
    
Exemplo: se especificar a cadeia `Document: ${item.name}  Classification: ${item.label}` para o rodapé de etiqueta Secreto, o texto do rodapé aplicado a um project.docx documentado será **Documento: project.docx Classificação: Secreto**.

## <a name="next-steps"></a>Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


