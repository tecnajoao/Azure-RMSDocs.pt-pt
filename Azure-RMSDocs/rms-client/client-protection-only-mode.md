---
title: "Modo de apenas de proteção para o Azure Information Protection"
description: "Informações para utilizadores que executam o cliente do Azure Information Protection no modo de apenas de proteção."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 55254496b23e49fe7e2dbd19721a824739004b21
ms.lasthandoff: 02/24/2017


---

# <a name="protection-only-mode-for-the-azure-information-protection-client"></a>Modo de apenas de proteção para o cliente do Azure Information Protection

Quando executa o cliente do Azure Information Protection sem uma política do Azure Information Protection, apresenta o modo de **apenas de proteção**. Por exemplo, quando utiliza o Explorador de Ficheiros do Windows, clique com o botão direito do rato em **Classificar e proteger**:

![Modo de apenas de proteção](../media/protection-only-mode.png)

 Este modo é executado nos seguintes cenários:

- A sua organização não tem uma subscrição para o Azure Information Protection (para a classificação e proteção de dados), mas tem uma subscrição para o serviço Azure Rights Management (para a proteção de dados com o Office 365). 
    - Este cenário é suportado e pode utilizar o cliente do Azure Information Protection para proteger ficheiros e ver ficheiros protegidos.

- A sua organização tem uma subscrição para o Azure Information Protection, mas não pode transferir a política do Azure Information Protection. 
    - Tal pode acontecer devido a uma configuração incorreta ou porque o seu início de sessão não teve êxito. Contacte o suporte técnico ou o administrador, mas, entretanto, pode conseguir utilizar o cliente do Azure Information Protection para proteger ficheiros e visualizar ficheiros protegidos.

## <a name="limitations-for-protection-only-mode"></a>Limitações para o modo de apenas de proteção

- Em aplicações do Office, não é apresentada a barra do Azure Information Protection. Quando clica em **Proteger** > **Mostrar Barra**, esta opção de menu não está disponível.

- Quando utilizar a caixa de diálogo **Classificar e proteger – Azure Information Protection** com o Explorador de Ficheiros, não verá etiquetas para classificação. Em vez disso, tal como na imagem anterior, pode ver uma opção para selecionar modelos Rights Management (RMS). 

## <a name="supported-tasks-for-protection-only-mode"></a>Tarefas suportadas para o modo de apenas de proteção

- Proteja (e desproteja) documentos e e-mails a partir das aplicações do Office através da funcionalidade Gestão de Direitos de Informação (IRM) do Office: por exemplo: clique em **Ficheiro** > **Informações** > **Proteger Documento** > **Restringir Acesso**. Para obter mais informações, veja [Utilizar a proteção de informações com o Office 365, Office 2016 ou Office 2013](../deploy-use/help-users.md).

- Proteja (e desproteja) ficheiros através do Explorador de Ficheiros do Windows: clique com o botão direito do rato no ficheiro, ficheiros ou pasta > **Classificar e proteger**. Para aplicar proteção que tenha sido configurada pelo seu administrador, na caixa de diálogo **Classificar e proteger – Azure Information Protection**, clique em **Selecionar modelo** e escolha um dos modelos disponíveis.

- Veja ficheiros protegidos através do Visualizador do Azure Information Protection.

- Aceda ao site de controlo de documentos a partir das aplicações do Office. No entanto, tem de ter uma subscrição válida para controlar e revogar documentos a partir deste site.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]  

