---
title: Como&#58; utilizar direitos incorporados | Azure RMS
description: "Descreve os direitos incorporados que o SDK RMS 4.2 concede e as restrições de utilização que uma aplicação devem impor para respeitar essas restrições."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
experiment_id: priyamo-TableVsFlatList-20160805
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: a8a513260dde6047c95c52c48217b7b4d8466cbc


---

# Como: utilizar direitos incorporados

Este tópico descreve os direitos incorporados que o SDK Microsoft Rights Management 4.2 concede e as restrições de utilização que uma aplicação deve impor para respeitar essas restrições. A tabela seguinte mostra os direitos incorporados, direitos comuns, direitos de documento editável e direitos de e-mail, seguidos de uma descrição e os respetivos valores por sistema operativo.

**Nota** – Para o SDK Linux, consulte o ficheiro de origem *rights.h* para ver os detalhes.

## Direitos Comuns ##

| Direita | Descrição | Android | iOS e OSX | Loja Windows e Windows Phone | Linux |
|-------|-------------|---------|-------------|---------------------------------|-------|
| **Todas** | Uma coleção de todos os direitos comuns. | [CommonRights.All](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_ALL) | [MSCommonRights owner](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)| [CommonRights.All</strong>](/information-protection/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights)| [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)|
| **Proprietário**| Concede o controlo total sobre o conteúdo protegido |  [CommonRights.Owner](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_Owner) |[MSCommonRights owner](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_) |[CommonRights.Owner](/information-protection/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights_owner) |  [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)|
| **Veja os** | O direito de ver conteúdo protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador abra e visualize conteúdo protegido. No entanto, são necessários direitos adicionais para modificar, extrair, reencaminhar ou guardar o conteúdo. |  [CommonRights.View](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View) | [MSCommonRights view](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)|[CommonRights.View](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View) | [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html) |


## Direitos de Documento Editável ##

| Direita | Descrição | Android | iOS e OSX | Loja Windows e Windows Phone | Linux |
|-------|-------------|---------|-------------|---------------------------------|-------|
| **Todas** | Uma coleção que contém todos os direitos de documento editável.| [EditableDocumentRights.All](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_ALL) | [MSEditableDocumentRights all](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) | [EditableDocumentRights.All](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_all) |[EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Comentário** | O direito de adicionar comentários no documento. | [EditableDocumentRights.Comment](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Comment)|[MSEditableDocumentRights comment](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) |[EditableDocumentRights.Comment](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights__comment)| [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Editar** | O direito de editar conteúdo protegido e guardá-lo no mesmo formato protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador altere conteúdo protegido e, em seguida, o guarde no mesmo ficheiro. | [EditableDocumentRights.Edit](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Edit) | [MSEditableDocumentRights edit](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) | [EditableDocumentRights.Edit](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_edit) | [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html) |
| **Exportar** | O direito de extrair conteúdo de um formato protegido e colocá-lo num formato diferente protegido pelo AD RMS. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador guarde conteúdo protegido para outros formatos que não o protegido por AD RMS. Por exemplo, se a aplicação implementar uma funcionalidade *Guardar Como*. | [EditableDocumentRights.Export](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Export) | [MSEditableDocumentRights exportable](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) |[EditableDocumentRights.Export](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_export) | [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Extração** | O direito de extrair conteúdo de um formato protegido e colocá-lo num formato não protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador copie e cole informações a partir de conteúdo protegido. Se a aplicação implementar uma funcionalidade <em>Guardar Como</em>, a aplicação também poderá permitir que o utilizador guarde conteúdo protegido para formatos não protegidos e outros formatos protegidos. Este direito tem o mesmo valor que o direito Extrair para e-mail. |  [EditableDocumentRights.Extract](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Extract) |[MSEditableDocumentRights extract](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) | [EditableDocumentRights.Extract](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_extract) |  [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Imprimir** | O direito de imprimir conteúdo protegido. Normalmente, quando este direito é concedido, a aplicação permite que o utilizador imprima conteúdo protegido. Este direito tem o mesmo valor que o direito Imprimir para e-mail. | [EditableDocumentRights.Print](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Print) |  [MSEditableDocumentRights print](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)| [EditableDocumentRights.Print](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_print) | [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
 

## Direitos de E-mail ##

| Direita | Descrição | Android | iOS e OSX | Loja Windows e Windows Phone | Linux |
|-------|-------------|---------|-------------|---------------------------------|-------|
| **Todas** |Uma coleção que contém todos os direitos de e-mail. |  [EmailRights.All](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ALL) | [MSEmailRights all](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.All](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_all)|[EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|
| **Extração** | O direito de extrair conteúdo de um formato protegido e colocá-lo num formato não protegido. Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail copie e cole informações a partir de uma mensagem protegida. Se a aplicação implementar uma funcionalidade <em>Guardar Como</em>, a aplicação também poderá permitir que o destinatário guarde conteúdo protegido para formatos não protegidos e outros formatos protegidos. Este direito tem o mesmo valor que o direito Extrair para documentos editáveis. | [EmailRights.Extract](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Extract) | [MSEmailRights extract](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Extract</strong>](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_extract) | [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html) |
|**Reencaminhar**| O direito de reencaminhar uma mensagem protegida. Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail reencaminhe uma mensagem protegida.| [<strong>EmailRights.Forward</strong>](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Forward) | [MSEmailRights forward](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Forward](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_forward) | [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html) |
|**Imprimir** | O direito de imprimir conteúdo protegido. Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail imprima uma mensagem protegida. Este direito tem o mesmo valor que o direito Imprimir para documentos editáveis. | [EmailRights.Print](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Print) |[MSEmailRights print](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Print](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_print) | [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|
| **Responder** | Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail responda a uma mensagem protegida e inclua uma cópia da mensagem original. | [EmailRights.Reply](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Reply) | [MSEmailRights reply](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Reply](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_reply) | [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|
| **ReplyAll** | Normalmente, quando este direito é concedido, a aplicação permite que o destinatário de um e-mail responda a todos os destinatários de uma mensagem protegida e inclua uma cópia da mensagem original. | [EmailRights.ReplyAll</strong>](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ReplyAll) | [MSEmailRights replyAll](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.ReplyAll](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_replyall) | [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|



<!--HONumber=Oct16_HO1-->


