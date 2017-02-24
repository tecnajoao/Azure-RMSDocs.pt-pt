---
title: "Procedimentos para definir o modo de segurança da API | Azure RMS"
description: "Escolha o modo de segurança em que é executada a sua aplicação de API de Ficheiros."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 49e87a8bf7ec5e628cf76c6ec82df2bb1b0835a3


---

# <a name="how-to-set-the-api-security-mode"></a>Procedimentos: definir o modo de segurança da API

Pode escolher em que modo de segurança a sua aplicação de API de Ficheiros é executada ao utilizar a função [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx).

Para inicializar a aplicação de modo a ser executada no *modo de servidor*, chame a função [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) e defina o modo de segurança para [IPC\_API\_MODE\_SERVER](https://msdn.microsoft.com/library/hh535236.aspx). Por predefinição, a aplicação é executada no *modo de cliente*, **IPC\_API\_MODE\_CLIENT**.

Para obter mais informações sobre o *modo de servidor*, consulte [Tipos de aplicações](application-types.md).

**Importante** O modo de segurança deve ser definido antes de ser chamada qualquer outra função do SDK Rights Management Services 2.1. Depois de definir o modo de segurança, não o pode alterar para o processo atual.

## <a name="related-topics"></a>Tópicos relacionados

* [Tipos de aplicações](application-types.md)
* [Valores do modo de API](https://msdn.microsoft.com/library/hh535236.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


