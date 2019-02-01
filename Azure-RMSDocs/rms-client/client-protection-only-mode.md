---
title: Modo de apenas de proteção para o Azure Information Protection
description: Informações para utilizadores que executam o cliente do Azure Information Protection no modo de apenas de proteção.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/24/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: dedacab4509b88f300739bd92012debedfaacf7d
ms.sourcegitcommit: 1c1d7067ae7aa8b822bb4ecd23cd7a644989e38c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55067973"
---
# <a name="user-guide-protection-only-mode-for-the-azure-information-protection-client"></a>Guia de utilizador: Modo de apenas de proteção para o cliente do Azure Information Protection

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*


Quando o cliente do Azure Information Protection não tem etiquetas para classificar os documentos e e-mails, ele é executado **apenas de proteção** modo. Por exemplo, neste modo, poderá ver o seguinte ao utilizar o Explorador de ficheiros do Windows, rato, **classificar e proteger**:

![Modo de apenas de proteção](../media/protection-only-mode.png)

Modo apenas de proteção é executado nos seguintes cenários:

- Sua organização não tem uma subscrição do Azure Information Protection, que inclui a classificação e etiquetas de recursos, mas tem uma subscrição do Office 365 que inclui proteção de dados com o serviço Azure Rights Management. 
    
    - Pode utilizar o cliente do Azure Information Protection para proteger ficheiros e ver ficheiros protegidos. Não é possível classificar ou Etiquetar documentos e e-mails.

- Sua organização tem uma subscrição do Azure Information Protection para apenas um subconjunto de utilizadores:
    
    - Para esta combinação de subscrições, é responsabilidade do administrador para se certificar de que apenas o subconjunto de utilizadores pode utilizar a classificação e etiquetagem funcionalidades. O restante dos usuários deve executar o cliente do Azure Information Protection no modo apenas de proteção. 

- A sua organização tem uma subscrição do Azure Information Protection, mas não tem quaisquer etiquetas configuradas por si.
    
    - Isto pode acontecer quando estão desativadas todas as etiquetas na política global e a sua conta não é adicionada a uma política de âmbito. Isso poderá ser porque o departamento de TI tem apenas começar a implementar o Azure Information Protection, mas ainda não foi fornecido a as etiquetas para classificar os documentos e e-mails. Entretanto, pode utilizar o cliente do Azure Information Protection para proteger ficheiros e ver ficheiros protegidos.

- A sua organização tem uma subscrição para o Azure Information Protection, mas não pode transferir a política do Azure Information Protection. 
    
    - Isto pode acontecer devido a uma configuração incorreta ou porque o seu início de sessão não é efetuada com êxito. Contacte o suporte técnico ou o administrador, mas, entretanto, pode conseguir utilizar o cliente do Azure Information Protection para proteger ficheiros e visualizar ficheiros protegidos.

- Sua organização utiliza o Active Directory Rights Management Services (AD RMS) apenas. 


## <a name="limitations-for-protection-only-mode"></a>Limitações para o modo de apenas de proteção

- Em aplicações do Office, não é apresentada a barra do Azure Information Protection. Quando clica em **Proteger** > **Mostrar Barra**, esta opção de menu não está disponível.

- Quando utilizar a caixa de diálogo **Classificar e proteger – Azure Information Protection** com o Explorador de Ficheiros, não verá etiquetas para classificação. Em vez disso, tal como na imagem anterior, pode ver uma opção para selecionar modelos Rights Management (RMS). 

## <a name="supported-tasks-for-protection-only-mode"></a>Tarefas suportadas para o modo de apenas de proteção

- Proteger (e desproteger) documentos e e-mails de aplicações do Office, ao utilizar a funcionalidade de gestão de direitos de informação (IRM) do Office: Por exemplo: Clique em **arquivo** > **informações** > **Proteger documento** > **restringir o acesso**. Para obter mais informações, consulte [utilizar a proteção de informações com o Office 365, Office 2019, Office 2016 ou Office 2013](../help-users.md#using-information-protection-with-Office-365-Office 2019-Office-2016-or-Office-2013).

- Proteger (e desproteger) ficheiros através do Explorador de ficheiros do Windows: Com o botão direito do ficheiros, ficheiros ou pasta > **classificar e proteger**. Para aplicar proteção que tenha sido configurada pelo seu administrador, na caixa de diálogo **Classificar e proteger – Azure Information Protection**, clique em **Selecionar modelo** e escolha um dos modelos disponíveis.

- Veja ficheiros protegidos através do Visualizador do Azure Information Protection.

- Aceda ao site de controlo de documentos a partir das aplicações do Office. No entanto, tem de ter uma subscrição válida para controlar e revogar documentos a partir deste site.
  
