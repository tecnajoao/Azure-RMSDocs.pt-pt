---
title: "Remover etiquetas de classificação e proteção de ficheiros e e-mails | Azure Information Protection"
description: "Instruções para remover etiquetas de classificação e proteção de ficheiros que foram etiquetados pelo Azure Information Protection ou protegidos pelo Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0a720ab08596964ed04fdc800ce55f3932a7cc0f
ms.openlocfilehash: fc401131a11426a17be4417d049199fb1c1a8f68


---

# <a name="remove-labels-and-protection-from-files-and-emails-that-have-been-labeled-by-azure-information-protection-or-protected-by-rights-management"></a>Remover etiquetas e proteção de ficheiros e e-mails que foram etiquetados pelo Azure Information Protection ou protegidos pelo Rights Management

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8 e Windows 7 com SP1*

Quando o [cliente do Azure Information Protection está instalado no computador](install-client-app.md), pode remover as etiquetas de classificação e a proteção de ficheiros e e-mails.

Se a etiqueta que remover estiver configurada para aplicar proteção, esta ação removerá também a proteção do ficheiro. Poderá ter que indicar o motivo pelo qual está a remover a etiqueta.

> [!IMPORTANT]
> Tem de ser o proprietário do ficheiro para remover a proteção ou de ter recebido permissões para remover a proteção (a permissão Controlo Total ou Extração do Rights Management).

Se pretender escolher uma etiqueta diferente ou um conjunto de definições de proteção diferente, não precisa de remover a etiqueta ou a proteção. Em vez disso, escolha uma nova etiqueta e, se for preciso, pode definir permissões personalizadas. 

Pode remover as etiquetas e a proteção dos documentos do Office e e-mails durante a criação ou edição dos mesmos nas aplicações de ambiente de trabalho do Office: **Word**, **Excel**, **PowerPoint** e **Outlook**. 

Também pode remover as etiquetas e a proteção através do **Explorador de Ficheiros**, que suporta outros tipos de ficheiro e é um meio cómodo para remover a proteção e as etiquetas de vários ficheiros ao mesmo tempo.

## <a name="using-office-apps-to-remove-labels-and-protection-from-documents-and-emails"></a>Utilizar as aplicações do Office para remover as etiquetas e a proteção de documentos e e-mails

Na barra do Information Protection, clique no ícone **Eliminar etiqueta**:

![Barra do Azure Information Protection – Eliminar Etiqueta](../media/delete-label.png)

Se o ícone **Eliminar Etiqueta** não estiver imediatamente disponível, clique primeiro no ícone **Editar Etiqueta**:

![Barra do Azure Information Protection – Editar Etiqueta](../media/edit-label.png)

> [!NOTE]
> Se não vir esta barra do Information Protection nas suas aplicações do Office:
> 
> - Poderá não ter o cliente do Azure Information Protection [instalado](install-client-app.md) ou o cliente está em execução no [modo apenas de proteção](client-protection-only-mode.md).

## <a name="using-file-explorer-to-remove-labels-and-protection-from-files"></a>Utilizar o Explorador de Ficheiros para remover as etiquetas e a proteção de ficheiros

Quando utiliza o Explorador de Ficheiros, pode rapidamente remover as etiquetas e a proteção de um ficheiro único, vários ficheiros ou uma pasta. Quando seleciona uma pasta, todos os ficheiros nessa pasta e eventuais subpastas são automaticamente selecionados. 

1.  No Explorador de Ficheiros, selecione o ficheiro, vários ficheiros ou uma pasta. Clique com o botão direito do rato e selecione **Classificar e proteger**.

2. Para remover uma etiqueta: na caixa de diálogo **Classificar e proteger – Azure Information Protection**, clique em **Eliminar Etiqueta**. Se a etiqueta tiver sido configurada para aplicar a proteção, essa proteção será removida automaticamente.

3. Para remover a proteção personalizada de um único ficheiro: na caixa de diálogo **Classificar e proteger – Azure Information Protection**, desmarque a opção **Proteger com permissões personalizadas**.
    
4. Para remover a proteção personalizada de vários ficheiros: na caixa de diálogo **Classificar e proteger – Azure Information Protection**, clique em **Remover permissões personalizadas**.

5. Clique em **Aplicar** e aguarde pela mensagem **Trabalho concluído** para ver os resultados. Em seguida, clique em **Fechar**.


## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

- [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

-   [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Feb17_HO2-->


