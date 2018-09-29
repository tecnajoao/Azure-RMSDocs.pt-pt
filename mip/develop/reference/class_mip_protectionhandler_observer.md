---
title: classe mip ProtectionHandler observador
description: Referência para a classe mip ProtectionHandler observador
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 7fed286dec42f16d7dfa8e375ec739264bd365ba
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446189"
---
# <a name="class-mipprotectionhandlerobserver"></a>classe mip::ProtectionHandler::Observer 
Interface que recebe notificações relacionadas com a [ProtectionHandler](class_mip_protectionhandler.md).
Esta interface tem de ser implementada por aplicativos que usam a proteção de SDK
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnCreateProtectionHandlerSuccess de void virtual público (const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& contexto)  |  Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) foi criado com êxito.
OnCreateProtectionHandlerFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) falha na criação.
  
## <a name="members"></a>Membros
  
### <a name="oncreateprotectionhandlersuccess"></a>OnCreateProtectionHandlerSuccess
Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) foi criado com êxito.

Parâmetros:  
* **protectionHandler**: O recém-criado [ProtectionHandler](class_mip_protectionhandler.md)


* **contexto**: O mesmo contexto de que foi passado para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) ou [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) ou [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync), e o mesmo contexto será encaminhado como-é ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess ou ProtectionEngine::Observer::O nCreateProtectionHandlerFailure
  
### <a name="oncreateprotectionhandlerfailure"></a>OnCreateProtectionHandlerFailure
Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) falha na criação.

Parâmetros:  
* **erro**: Falha ao criar 


* **contexto**: O mesmo contexto de que foi passado para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) ou [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) ou [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync), e o mesmo contexto será encaminhado como-é ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess ou ProtectionEngine::Observer::O nCreateProtectionHandlerFailure