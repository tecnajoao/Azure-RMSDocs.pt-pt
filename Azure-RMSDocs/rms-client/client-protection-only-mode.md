---
title: "Modo de apenas de proteção para o Azure Information Protection"
description: "Informações para utilizadores que executam o cliente do Azure Information Protection no modo de apenas de proteção."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/02/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: ea865f91751ed171779c587d1af4cb0f4226a59e
ms.sourcegitcommit: bc47834ae7180491ed1d9bc9f69eab398bcdc0a8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2018
---
# <a name="user-guide-protection-only-mode-for-the-azure-information-protection-client"></a>Guia do utilizador: O modo só de proteção para o cliente Azure Information Protection

Quando o cliente Azure Information Protection não tem etiquetas para classificar os documentos e e-mails, é executada no **só de proteção** modo. Por exemplo, neste modo, poderá ver o seguinte quando utilizar o Explorador de ficheiros do Windows, rato, **classificar e proteger**:

![Modo de apenas de proteção](../media/protection-only-mode.png)

Modo só de proteção é executado nos seguintes cenários:

- A organização não tiver uma subscrição do Azure Information Protection, que inclui a classificação e etiquetas funcionalidades, mas tem uma subscrição do Office 365 que inclui proteção de dados utilizando o serviço Azure Rights Management. 
    
    - Pode utilizar o cliente Azure Information Protection para proteger ficheiros e ver ficheiros protegidos. Não é possível classificar ou Etiquetar documentos e e-mails.

- A sua organização tem uma subscrição do Azure Information Protection para apenas um subconjunto de utilizadores:
    
    - Para esta combinação de subscrições, é responsabilidade do administrador para se certificar de que apenas o subconjunto de utilizadores pode utilizar a classificação e etiquetagem funcionalidades. O resto dos utilizadores deve estar a executar o cliente Azure Information Protection no modo só de proteção. 

- A sua organização tem uma subscrição para o Azure Information Protection, mas não pode transferir a política do Azure Information Protection. 
    
    - Isto pode acontecer devido a uma configuração incorreta ou porque o seu início de sessão não é efetuada com êxito. Contacte o suporte técnico ou o administrador, mas, entretanto, pode conseguir utilizar o cliente do Azure Information Protection para proteger ficheiros e visualizar ficheiros protegidos.

- A organização utiliza o Active Directory Rights Management Services (AD RMS) apenas. 


## <a name="limitations-for-protection-only-mode"></a>Limitações para o modo de apenas de proteção

- Em aplicações do Office, não é apresentada a barra do Azure Information Protection. Quando clica em **Proteger** > **Mostrar Barra**, esta opção de menu não está disponível.

- Quando utilizar a caixa de diálogo **Classificar e proteger – Azure Information Protection** com o Explorador de Ficheiros, não verá etiquetas para classificação. Em vez disso, tal como na imagem anterior, pode ver uma opção para selecionar modelos Rights Management (RMS). 

## <a name="supported-tasks-for-protection-only-mode"></a>Tarefas suportadas para o modo de apenas de proteção

- Proteja (e desproteja) documentos e e-mails a partir das aplicações do Office através da funcionalidade Gestão de Direitos de Informação (IRM) do Office: por exemplo: clique em **Ficheiro** > **Informações** > **Proteger Documento** > **Restringir Acesso**. Para obter mais informações, veja [Utilizar a proteção de informações com o Office 365, Office 2016 ou Office 2013](../deploy-use/help-users.md).

- Proteja (e desproteja) ficheiros através do Explorador de Ficheiros do Windows: clique com o botão direito do rato no ficheiro, ficheiros ou pasta > **Classificar e proteger**. Para aplicar proteção que tenha sido configurada pelo seu administrador, na caixa de diálogo **Classificar e proteger – Azure Information Protection**, clique em **Selecionar modelo** e escolha um dos modelos disponíveis.

- Veja ficheiros protegidos através do Visualizador do Azure Information Protection.

- Aceda ao site de controlo de documentos a partir das aplicações do Office. No entanto, tem de ter uma subscrição válida para controlar e revogar documentos a partir deste site.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]  
