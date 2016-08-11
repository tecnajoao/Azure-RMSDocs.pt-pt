---
title: Como configurar uma etiqueta para marcas visuais para o Azure Information Protection | Azure Rights Management
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 9f2d28e4f162891497a7b0518322338628118b9d


---

# Como configurar uma etiqueta para marcas visuais para o Azure Information Protection

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Quando atribui uma etiqueta a um documento ou a um e-mail pode selecionar várias opções para tornar a classificação escolhida facilmente visível. Estas marcas visuais são um cabeçalho, rodapé e uma marca d'água:

As marcas visuais são aplicadas a documentos do Word, do Excel e do PowerPoint quando a etiqueta é aplicada e quando o documento é guardado. Para e-mails, as marcas visuais são aplicadas quando o e-mail é enviado.

Informações adicionais sobre este marcadores visuais:

- Os cabeçalhos e rodapés aplicam-se ao Word, ao Excel, ao PowerPoint e ao Outlook.

- As marcas d'água aplicam-se ao Word, ao Excel e ao PowerPoint:

    - Excel: as marcas d'água só estarão visíveis nos modos de Pré-visualização de impressão e Esquema de página e quando foram impressas.

    - PowerPoint: as arcas d'água são aplicadas ao diapositivo principal, como uma imagem de fundo.

Utilize as seguintes instruções para configurar marcas visuais para uma etiqueta.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
 
2. No menu Hub, clique em **Procurar** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

3. No painel do **Azure Information Protection**, selecione a etiqueta que pretende configurar com marcas visuais.

4. No painel **Etiqueta**, na secção **Definir marcas visuais (como o cabeçalho ou o rodapé)** configure as definições para as marcas visuais que pretende e, em seguida, clique em **Guardar**:

    - Para configurar um cabeçalho: para **Documentos com esta etiqueta têm um cabeçalho**, selecione **Ativado** se pretender um cabeçalho e, caso contrário, clique em **Desativado**. Se selecionar **Ativado**, em seguida, especifique o texto do cabeçalho, o tamanho, a cor e o alinhamento para o cabeçalho.

    - Para configurar um rodapé: para **Documentos com esta etiqueta têm um rodapé**, selecione **Ativado** se pretender um rodapé e, caso contrário, clique em **Desativar**. Se selecionar **Ativado**, em seguida, especifique o texto do rodapé, o tamanho, a cor e o alinhamento para o cabeçalho.

    - Para configurar uma marca d’água: para **Documentos com esta etiqueta têm uma marca d’água**, selecione **Ativado** se pretender uma marca d’água e, caso contrário, clique em **Desativado**. Se selecionar **Ativado**, em seguida, especifique o texto da marca d’água, o tamanho, a cor e o modelo para o cabeçalho.

5. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Jul16_HO5-->


