---
title: Remover etiquetas do Azure Information Protection
description: Instruções para remover etiquetas de classificação e proteção de ficheiros que foram etiquetados pelo Azure Information Protection ou protegidos pelo Rights Management.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ''
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: ab98e211bf0f346359c6f6627a68db3071f7482e
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305085"
---
# <a name="user-guide-remove-labels-and-protection-from-files-and-emails-that-have-been-labeled-by-azure-information-protection-or-protected-by-rights-management"></a>Guia de utilizador: Remover etiquetas e proteção de ficheiros e e-mails que foram etiquetados pelo Azure Information Protection ou protegidos pelo Rights Management

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

Quando o [cliente do Azure Information Protection está instalado no computador](install-client-app.md), pode remover as etiquetas de classificação e a proteção de ficheiros e e-mails.

Se a etiqueta que remover estiver configurada para aplicar proteção, esta ação removerá também a proteção do ficheiro. Poderá ter que indicar o motivo pelo qual está a remover a etiqueta.

> [!IMPORTANT]
> Tem de ser o proprietário do ficheiro para remover a proteção, ou foram concedidas permissões para remover a proteção (a permissão de gestão de direitos de **exportar** ou **controlo total**).

Se pretender escolher uma etiqueta diferente ou um conjunto de definições de proteção diferente, não precisa de remover a etiqueta ou a proteção. Em vez disso, escolha uma nova etiqueta e, se necessário, pode definir permissões personalizadas se o administrador permite esta configuração. 

Pode remover etiquetas e proteção de documentos do Office e e-mails durante a criação ou edição dos mesmos nas suas aplicações de ambiente de trabalho do Office: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Também pode remover as etiquetas e a proteção através do **Explorador de Ficheiros**, que suporta outros tipos de ficheiro e é um meio cómodo para remover a proteção e as etiquetas de vários ficheiros ao mesmo tempo.

## <a name="using-office-apps-to-remove-labels-and-protection-from-documents-and-emails"></a>Utilizar as aplicações do Office para remover as etiquetas e a proteção de documentos e e-mails

Na barra do Information Protection, clique no ícone **Eliminar etiqueta**:

![Barra do Azure Information Protection – Eliminar Etiqueta](../media/delete-label.png)

Se o ícone **Eliminar Etiqueta** não estiver imediatamente disponível, clique primeiro no ícone **Editar Etiqueta**:

![Barra do Azure Information Protection – Editar Etiqueta](../media/edit-label.png)

Se ainda não vir a **eliminar etiqueta** ícone, o administrador não lhe permite utilizar esta opção.

> [!NOTE]
> Se não vir esta barra do Information Protection nas suas aplicações do Office:
>
> - Se vir um **Protect** botão na faixa de opções: Selecione **Protect**e, em seguida, selecione **Mostrar barra**.
> 
> - Poderá não ter o cliente do Azure Information Protection [instalado](install-client-app.md) ou o cliente está em execução no [modo apenas de proteção](client-protection-only-mode.md).

## <a name="using-file-explorer-to-remove-labels-and-protection-from-files"></a>Utilizar o Explorador de Ficheiros para remover as etiquetas e a proteção de ficheiros

Quando utiliza o Explorador de Ficheiros, pode rapidamente remover as etiquetas e a proteção de um ficheiro único, vários ficheiros ou uma pasta. Quando seleciona uma pasta, todos os ficheiros nessa pasta e eventuais subpastas são automaticamente selecionados. 

1. No Explorador de Ficheiros, selecione o ficheiro, vários ficheiros ou uma pasta. Clique com o botão direito do rato e selecione **Classificar e proteger**.

2. Para remover uma etiqueta: Na **classificar e proteger – Azure Information Protection** caixa de diálogo, clique em **eliminar etiqueta**. Se a etiqueta tiver sido configurada para aplicar a proteção, essa proteção será removida automaticamente.

3. Para remover a proteção personalizada de um único arquivo: Na **classificar e proteger – Azure Information Protection** caixa de diálogo, desmarque a **proteger com permissões personalizadas** opção. 
    
    Se não vir a **proteger com permissões personalizadas** opção, o administrador não permite-lhe utilizar esta opção.
    
4. Para remover a proteção personalizada de vários ficheiros: Na **classificar e proteger – Azure Information Protection** caixa de diálogo, clique em **remover permissões personalizadas**.
    
    Se não vir a **remover permissões personalizadas** opção, o administrador não permite-lhe utilizar esta opção.

5. Clique em **Aplicar** e aguarde pela mensagem **Trabalho concluído** para ver os resultados. Em seguida, clique em **Fechar**.


## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

- [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Informações adicionais para administradores    
Para obter instruções de configuração ativar a definição de política **disponibilizar a opção de permissões personalizadas para os usuários**, consulte [configurar as definições de política do Azure Information Protection](../configure-policy-settings.md).

Outras instruções de configuração: [Configurar a política do Azure Information Protection](../configure-policy.md).

