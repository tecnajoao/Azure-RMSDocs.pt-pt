---
title: Como&#58; utilizar direitos incorporados | Azure RMS
description: Descreve os direitos incorporados que o SDK RMS 4.2 concede e as restrições de utilização que uma aplicação deve impor para respeitar essas restrições.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: cd9c1ae8873b8f5a8d0440bd017d92d16801219b
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259614"
---
# <a name="how-to-use-built-in-rights"></a>Como: Utilizar direitos incorporados

Este tópico descreve os direitos incorporados que o Microsoft Rights Management SDK 4.2 concede e as restrições de utilização que uma aplicação deve impor para respeitar essas restrições. Em seguida, são apresentados os direitos incorporados, direitos comuns, direitos de documento editável e direitos de e-mail, seguidos de uma descrição e os respetivos valores por sistema operativo.

**Nota:** para o SDK Linux, consulte o ficheiro de origem *rights.h* para ver os detalhes.

## <a name="common-rights"></a>Direitos Comuns

**Todos** – Uma coleção de todos os direitos comuns.
- Android: [CommonRights.All](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS e OS x: [MSCommonRights](https://msdn.microsoft.com/library/dn758314.aspx) -vista e proprietário de utilizador para implementar **todos os**
- Windows Store e Windows Phone: [CommonRights.All</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.all.aspx)
- Linux: [CommonRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**Proprietário** – o direito Proprietário concede o controlo total sobre os conteúdos protegidos.
- Android: [<strong>CommonRights.Owner](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS e OS x: [MSCommonRights proprietário](https://msdn.microsoft.com/library/dn758314.aspx)
- Windows Store e Windows Phone: [CommonRights.Owner](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.owner.aspx)
- Linux: [CommonRights::Owner](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**Ver** – o direito de ver conteúdo protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador abra e visualize conteúdo protegido. No entanto, são necessários direitos adicionais para modificar, extrair, reencaminhar ou guardar o conteúdo.

- Android: [CommonRights.View](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS e OS x: [MSCommonRights view](https://msdn.microsoft.com/library/dn758314.aspx)
- Windows Store e Windows Phone: [CommonRights.View](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.view.aspx)
- Linux: [CommonRights::View](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## <a name="editable-document-rights"></a>Direitos de Documento Editável
**Todos** – Uma coleção que contém todos os direitos de documento editável.
- Android: [EditableDocumentRights.All](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights todos os](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [EditableDocumentRights.All](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.all.aspx)
- Linux: [EditableDocumentRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Comentário** – o direito de adicionar comentários no documento.
- Android: [EditableDocumentRights.Comment](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [Comentário de MSEditableDocumentRights](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [EditableDocumentRights.Comment](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.comment.aspx)
- Linux: [EditableDocumentRights::Comment](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Editar** – o direito de editar conteúdo protegido e guardá-lo no mesmo formato protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador altere conteúdo protegido e, em seguida, o guarde no mesmo ficheiro.
- Android: [EditableDocumentRights.Edit](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights edit](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [EditableDocumentRights.Edit](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.edit.aspx)
- Linux: [EditableDocumentRights::Edit](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Exportar** – o direito de extrair conteúdo de um formato protegido e colocá-lo num formato diferente protegido pelo AD RMS. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador guarde conteúdo protegido para outros formatos que não o protegido por AD RMS. Por exemplo, se a aplicação implementar uma funcionalidade *Guardar Como*.

- Android: [EditableDocumentRights.Export](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights exportável](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [EditableDocumentRights.Export](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.export.aspx)
- Linux: [EditableDocumentRights::Export](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Extrair** – o direito de extrair conteúdo de um formato protegido e colocá-lo num formato não protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador copie e cole informações a partir de conteúdo protegido. Se a aplicação implementar uma funcionalidade <em>Guardar Como</em>, a aplicação também poderá permitir que o utilizador guarde conteúdo protegido para formatos não protegidos e outros formatos protegidos. Este direito tem o mesmo valor que o direito Extrair para e-mail.

- Android: [EditableDocumentRights.Extract](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights extract](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [EditableDocumentRights.Extract](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.extract.aspx)
- Linux: [EditableDocumentRights::Extract](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Imprimir** – o direito de imprimir conteúdo protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador imprima conteúdo protegido. Este direito tem o mesmo valor que o direito Imprimir para e-mail.

- Android: [EditableDocumentRights.Print](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights impressão](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [EditableDocumentRights.Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.print.aspx)
- Linux: [EditableDocumentRights::Print](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## <a name="email-rights"></a>Direitos de E-mail

**Todos** – uma coleção que contém todos os direitos de e-mail.
- Android: [EmailRights.All](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights todos os](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [EmailRights.All](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.all.aspx)
- Linux: [EmailRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Extrair** – o direito de extrair conteúdo de um formato protegido e colocá-lo num formato não protegido. Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail copie e cole informações a partir de uma mensagem protegida. Se a aplicação implementar uma funcionalidade <em>Guardar Como</em>, a aplicação também poderá permitir que o destinatário guarde conteúdo protegido para formatos não protegidos e outros formatos protegidos. Este direito tem o mesmo valor que o direito Extrair para documentos editáveis.

- Android: [EmailRights.Extract](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights extract](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [EmailRights.Extract</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.extract.aspx)
- Linux: [EmailRights::Extract](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Reencaminhar** – o direito de reencaminhar uma mensagem protegida. Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail reencaminhe uma mensagem protegida.
- Android: [<strong>EmailRights.Forward</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights forward](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [EmailRights.Forward](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.forward.aspx)
- Linux: [EmailRights::Forward](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Imprimir** – o direito de imprimir conteúdo protegido. Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail imprima uma mensagem protegida. Este direito tem o mesmo valor que o direito Imprimir para documentos editáveis.

- Android: [EmailRights.Print](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights impressão](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [EmailRights.Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.print.aspx)
- Linux: [EmailRights::Print](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Responder** – normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail responda a uma mensagem protegida e inclua uma cópia da mensagem original.

- Android: [EmailRights.Reply](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [Resposta de MSEmailRights](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [EmailRights.Reply](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.reply.aspx)
- Linux: [EmailRights::Reply](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Responder a Todos** – normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail responda a todos os destinatários de uma mensagem protegida e inclua uma cópia da mensagem original.

- Android: [EmailRights.ReplyAll</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights replyAll](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [EmailRights.ReplyAll](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.replyall.aspx)
- Linux: [EmailRights::ReplyAll](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)
