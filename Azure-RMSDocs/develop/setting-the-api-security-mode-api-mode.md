---
title: Procedimentos para definir o modo de segurança da API | Azure RMS
description: Escolha o modo de segurança em que é executada a sua aplicação de API de Ficheiros.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 2b21601a767f18106044548ada8d10b212b8cb5a
ms.sourcegitcommit: 93124ef58e471277c7793130f1a82af33dabcea9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/11/2018
ms.locfileid: "27765403"
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