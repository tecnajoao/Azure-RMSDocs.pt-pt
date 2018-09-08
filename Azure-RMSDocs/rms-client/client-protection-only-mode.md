---
title: Modo de apenas de proteção para o Azure Information Protection
description: Informações para utilizadores que executam o cliente do Azure Information Protection no modo de apenas de proteção.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 5a2b01af0e246e732d087a344ecf037c13a47546
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151584"
---
# <a name="user-guide-protection-only-mode-for-the-azure-information-protection-client"></a>Guia de utilizador: Modo apenas de proteção para o cliente do Azure Information Protection

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*


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

- Proteja (e desproteja) documentos e e-mails a partir das aplicações do Office através da funcionalidade Gestão de Direitos de Informação (IRM) do Office: por exemplo: clique em **Ficheiro** > **Informações** > **Proteger Documento** > **Restringir Acesso**. Para obter mais informações, veja [Utilizar a proteção de informações com o Office 365, Office 2016 ou Office 2013](../help-users.md).

- Proteja (e desproteja) ficheiros através do Explorador de Ficheiros do Windows: clique com o botão direito do rato no ficheiro, ficheiros ou pasta > **Classificar e proteger**. Para aplicar proteção que tenha sido configurada pelo seu administrador, na caixa de diálogo **Classificar e proteger – Azure Information Protection**, clique em **Selecionar modelo** e escolha um dos modelos disponíveis.

- Veja ficheiros protegidos através do Visualizador do Azure Information Protection.

- Aceda ao site de controlo de documentos a partir das aplicações do Office. No entanto, tem de ter uma subscrição válida para controlar e revogar documentos a partir deste site.
  
