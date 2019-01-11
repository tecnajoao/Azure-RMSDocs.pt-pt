---
title: Como&#58; utilizar direitos incorporados | Azure RMS
description: Descreve os direitos incorporados que o SDK RMS 4.2 concede e as restrições de utilização que uma aplicação deve impor para respeitar essas restrições.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 3fd505e8e692cfacafbfec7b65d6e6ac37d539f5
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071272"
---
# <a name="how-to-use-built-in-rights"></a>Como: Utilizar direitos incorporados

Este tópico descreve os direitos incorporados que o Microsoft Rights Management SDK 4.2 concede e as restrições de utilização que uma aplicação deve impor para respeitar essas restrições. Em seguida, são apresentados os direitos incorporados, direitos comuns, direitos de documento editável e direitos de e-mail, seguidos de uma descrição e os respetivos valores por sistema operativo.

**Nota:** para o SDK Linux, consulte o ficheiro de origem *rights.h* para ver os detalhes.

## <a name="common-rights"></a>Direitos Comuns

**Todos** – Uma coleção de todos os direitos comuns.
- Android: [Commonrights. all](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS e OS x: [MSCommonRights](https://msdn.microsoft.com/library/dn758314.aspx) -vista e proprietário de utilizador para implementar **todos os**
- Windows Store e Windows Phone: [Commonrights. all</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.all.aspx)
- Linux: [CommonRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**Proprietário** – o direito Proprietário concede o controlo total sobre os conteúdos protegidos.
- Android: [<strong>Commonrights. Owner](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS e OS x: [MSCommonRights proprietário](https://msdn.microsoft.com/library/dn758314.aspx)
- Windows Store e Windows Phone: [Commonrights. Owner](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.owner.aspx)
- Linux: [CommonRights::Owner](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**Ver** – o direito de ver conteúdo protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador abra e visualize conteúdo protegido. No entanto, são necessários direitos adicionais para modificar, extrair, reencaminhar ou guardar o conteúdo.

- Android: [Commonrights. View](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS e OS x: [MSCommonRights view](https://msdn.microsoft.com/library/dn758314.aspx)
- Windows Store e Windows Phone: [Commonrights. View](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.view.aspx)
- Linux: [CommonRights::View](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## <a name="editable-document-rights"></a>Direitos de Documento Editável
**Todos** – Uma coleção que contém todos os direitos de documento editável.
- Android: [Editabledocumentrights. all](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights todos os](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [Editabledocumentrights. all](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.all.aspx)
- Linux: [EditableDocumentRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Comentário** – o direito de adicionar comentários no documento.
- Android: [Editabledocumentrights. Comment](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [Comentário de MSEditableDocumentRights](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [Editabledocumentrights. Comment](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.comment.aspx)
- Linux: [EditableDocumentRights::Comment](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Editar** – o direito de editar conteúdo protegido e guardá-lo no mesmo formato protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador altere conteúdo protegido e, em seguida, o guarde no mesmo ficheiro.
- Android: [Editabledocumentrights. Edit](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights edit](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [Editabledocumentrights. Edit](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.edit.aspx)
- Linux: [EditableDocumentRights::Edit](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Exportar** – o direito de extrair conteúdo de um formato protegido e colocá-lo num formato diferente protegido pelo AD RMS. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador guarde conteúdo protegido para outros formatos que não o protegido por AD RMS. Por exemplo, se a aplicação implementar uma funcionalidade *Guardar Como*.

- Android: [Editabledocumentrights. Export](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights exportável](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [Editabledocumentrights. Export](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.export.aspx)
- Linux: [EditableDocumentRights::Export](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Extrair** – o direito de extrair conteúdo de um formato protegido e colocá-lo num formato não protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador copie e cole informações a partir de conteúdo protegido. Se a aplicação implementar uma funcionalidade <em>Guardar Como</em>, a aplicação também poderá permitir que o utilizador guarde conteúdo protegido para formatos não protegidos e outros formatos protegidos. Este direito tem o mesmo valor que o direito Extrair para e-mail.

- Android: [Editabledocumentrights. Extract](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights extract](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [Editabledocumentrights. Extract](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.extract.aspx)
- Linux: [EditableDocumentRights::Extract](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Imprimir** – o direito de imprimir conteúdo protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador imprima conteúdo protegido. Este direito tem o mesmo valor que o direito Imprimir para e-mail.

- Android: [Editabledocumentrights. Print](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS e OS x: [MSEditableDocumentRights impressão](https://msdn.microsoft.com/library/dn758318.aspx)
- Windows Store e Windows Phone: [Editabledocumentrights. Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.print.aspx)
- Linux: [EditableDocumentRights::Print](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## <a name="email-rights"></a>Direitos de E-mail

**Todos** – uma coleção que contém todos os direitos de e-mail.
- Android: [Emailrights. all](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights todos os](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [Emailrights. all](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.all.aspx)
- Linux: [EmailRights::All](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Extrair** – o direito de extrair conteúdo de um formato protegido e colocá-lo num formato não protegido. Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail copie e cole informações a partir de uma mensagem protegida. Se a aplicação implementar uma funcionalidade <em>Guardar Como</em>, a aplicação também poderá permitir que o destinatário guarde conteúdo protegido para formatos não protegidos e outros formatos protegidos. Este direito tem o mesmo valor que o direito Extrair para documentos editáveis.

- Android: [Emailrights. Extract](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights extract](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [Emailrights. Extract</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.extract.aspx)
- Linux: [EmailRights::Extract](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Reencaminhar** – o direito de reencaminhar uma mensagem protegida. Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail reencaminhe uma mensagem protegida.
- Android: [<strong>Emailrights. forward</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights forward](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [Emailrights. forward](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.forward.aspx)
- Linux: [EmailRights::Forward](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Imprimir** – o direito de imprimir conteúdo protegido. Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail imprima uma mensagem protegida. Este direito tem o mesmo valor que o direito Imprimir para documentos editáveis.

- Android: [Emailrights. Print](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights impressão](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [Emailrights. Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.print.aspx)
- Linux: [EmailRights::Print](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Responder** – normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail responda a uma mensagem protegida e inclua uma cópia da mensagem original.

- Android: [Emailrights. Reply](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [Resposta de MSEmailRights](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [Emailrights. Reply](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.reply.aspx)
- Linux: [EmailRights::Reply](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Responder a Todos** – normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail responda a todos os destinatários de uma mensagem protegida e inclua uma cópia da mensagem original.

- Android: [Emailrights. replyall</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS e OS x: [MSEmailRights replyAll](https://msdn.microsoft.com/library/dn758319.aspx)
- Windows Store e Windows Phone: [Emailrights. replyall](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.replyall.aspx)
- Linux: [EmailRights::ReplyAll](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)
