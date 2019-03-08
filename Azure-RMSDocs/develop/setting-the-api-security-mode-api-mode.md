---
title: Procedimentos para definir o modo de segurança da API | Azure RMS
description: Escolha o modo de segurança em que é executada a sua aplicação de API de Ficheiros.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: de05a0331e347dbfa4c10237433fcf370f088388
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330411"
---
# <a name="how-to-set-the-api-security-mode"></a>Procedimentos: definir o modo de segurança da API

Pode escolher em que modo de segurança a sua aplicação de API de Ficheiros é executada ao utilizar a função [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx).

Para inicializar a aplicação de modo a ser executada no *modo de servidor*, chame a função [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) e defina o modo de segurança para [IPC\_API\_MODE\_SERVER](https://msdn.microsoft.com/library/hh535236.aspx). Por predefinição, a aplicação é executada no *modo de cliente*, **IPC\_API\_MODE\_CLIENT**.

Para obter mais informações sobre o *modo de servidor*, consulte [Tipos de aplicações](application-types.md).

**Importante**  o modo de segurança deve ser definido antes de qualquer outra função do Rights Management Services SDK 2.1 é chamada. Depois de definir o modo de segurança, não o pode alterar para o processo atual.

## <a name="related-topics"></a>Tópicos relacionados

* [Tipos de aplicações](application-types.md)
* [Valores do modo de API](https://msdn.microsoft.com/library/hh535236.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)
