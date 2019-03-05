---
title: classe mip::ProtectionHandler::Observer
description: Documenta a classe mip::protectionhandler da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 00d74069374850a562547cd161ad4c5f15927b0a
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333726"
---
# <a name="class-mipprotectionhandlerobserver"></a>classe mip::ProtectionHandler::Observer 
Interface que recebe notificações relacionadas com a [ProtectionHandler](class_mip_protectionhandler.md).
Esta interface tem de ser implementada por aplicativos que usam a proteção de SDK
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public virtual void OnCreateProtectionHandlerSuccess(const std::shared_ptr\<ProtectionHandler\>& protectionHandler, const std::shared_ptr\<void\>& context)  |  Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) foi criado com êxito.
OnCreateProtectionHandlerFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) falha na criação.
  
## <a name="members"></a>Membros
  
### <a name="oncreateprotectionhandlersuccess-function"></a>Função de OnCreateProtectionHandlerSuccess
Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) foi criado com êxito.

Parâmetros:  
* **protectionHandler**: O recém-criado [ProtectionHandler](class_mip_protectionhandler.md)


* **context**: O mesmo contexto transmitido a [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) ou [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) ou [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function), e o mesmo contexto será encaminhado como-é ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess ou ProtectionEngine::Observer::O nCreateProtectionHandlerFailure
  
### <a name="oncreateprotectionhandlerfailure-function"></a>Função de OnCreateProtectionHandlerFailure
Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) falha na criação.

Parâmetros:  
* **error**: Falha ao criar 


* **context**: O mesmo contexto transmitido a [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) ou [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync-function) ou [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync-function), e o mesmo contexto será encaminhado como-é ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess ou ProtectionEngine::Observer::O nCreateProtectionHandlerFailure
