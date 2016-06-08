---
# required metadata

title: Definir o modo de segurança de API | Azure RMS
description: Escolha o modo de segurança em que é executada a sua aplicação de API de Ficheiros.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Este conteúdo do SDK não está atualizado. Durante um curto período de tempo, pode encontrar a [versão atual](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) da documentação no MSDN. **
# Definir o modo de segurança de API

Pode escolher em que modo de segurança a sua aplicação de API de Ficheiros é executada ao utilizar a função [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty).

Para inicializar a aplicação de modo a ser executada no *modo de servidor*, chame a função [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) e defina o modo de segurança para [**IPC\_API\_MODE\_SERVER**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER). Por predefinição, a aplicação é executada no *modo de cliente*, **IPC\_API\_MODE\_CLIENT**.

Para obter mais informações sobre o *modo de servidor*, consulte [Tipos de aplicações](application-types.md).

**Importante** O modo de segurança deve ser definido antes de ser chamada qualquer outra função do SDK Rights Management Services 2.1. Depois de definir o modo de segurança, não o pode alterar para o processo atual.

 

## Tópicos relacionados

* [Tipos de aplicações](application-types.md)
* [Conceitos do programador](ad-rms-concepts-nav.md)
* [**Valores do modo de API**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
 

 





<!--HONumber=Jun16_HO1-->


