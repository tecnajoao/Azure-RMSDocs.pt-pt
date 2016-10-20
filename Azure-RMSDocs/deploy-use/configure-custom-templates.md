---
title: "Configurar modelos personalizados para o serviço Azure Rights Management | Azure Information Protection"
description: "Informações e instruções para os administradores configurarem e gerirem modelos de direitos de utilização. Os modelos permitem aos utilizadores e outros administradores aplicar facilmente políticas a ficheiros confidenciais que restringem o acesso a utilizadores autorizados."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d5b6a1fc3fa0a19f3a6b65aa7b8815eda7432cd7
ms.openlocfilehash: d8db7f0346fad1b9c46423875d1e559d41987686


---

# Configurar modelos personalizados para o serviço Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

Quando o serviço Azure Rights Management tiver sido [ativado](activate-service.md), os utilizadores podem utilizar automaticamente dois modelos predefinidos que facilitam a aplicação de políticas de gestão de direitos a ficheiros confidenciais que restringem o acesso aos utilizadores autorizados na sua organização. Estes dois modelos têm as seguintes restrições de política de direitos:

-   Visualização só de leitura dos conteúdos protegidos

    -   Nome a apresentar: **&lt;nome da organização&gt; – Apenas Visualização Confidencial**

    -   Permissão específica: Ver Conteúdo

-   Permissões Ler ou Modificar para o conteúdo protegido

    -   Nome a apresentar: **&lt;nome da organização&gt; – Confidencial**

    -   Permissões específicas: Ver Conteúdo, Guardar Ficheiro, Editar Conteúdo, Ver Direitos Atribuídos, Permitir Macros, Reencaminhar, Responder, Responder A Todos

Além disso, a [aplicação de partilha RMS](../rms-client/sharing-app-windows.md) permite que os utilizadores definam o seu próprio conjunto de permissões. E, para o cliente do Outlook e o Outlook Web Access, os utilizadores podem selecionar a [opção Não Reencaminhar](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails).

Para muitas organizações, os modelos predefinidos poderão ser suficientes. No entanto, se quiser criar os seus próprios modelos de políticas de direitos personalizados, pode fazê-lo. Seguem-se algumas das razões para criar um modelo personalizado:

-   Quer um modelo que conceda direitos a um subconjunto de utilizadores na organização em vez de os conceder a todos os utilizadores.

-   Quer que apenas um subconjunto de utilizadores possa ver e selecionar um modelo (modelo departamental) a partir de aplicações, em vez de todos os utilizadores na organização poderem ver e selecionar o modelo.

-   Quer definir um direito personalizado para um modelo, como Ver e Editar, mas não Copiar e Imprimir.

-   Quer configurar opções adicionais num modelo que inclua uma data de expiração e definir se os conteúdos pode ser acedidos sem uma ligação à Internet.

Para os utilizadores poderem selecionar um modelo personalizado com definições como estas, primeiro tem de criar um modelo personalizado, configurá-lo e, em seguida, publicá-lo. Embora provavelmente venha a necessitar de apenas alguns modelos, pode ter um máximo de 500 modelos personalizados guardados no Azure. 

Utilize as informações seguintes para configurar e utilizar modelos personalizados:

-   [Como criar, configurar e publicar um modelo personalizado](create-template.md)

-   [Como copiar um modelo](copy-template.md)

-   [Como remover (arquivar) modelos](remove-template.md)

-   [Como atualizar modelos para utilizadores](refresh-templates.md)

-   [Utilizar o PowerShell para gerir modelos](configure-templates-with-powershell.md)





<!--HONumber=Sep16_HO4-->


