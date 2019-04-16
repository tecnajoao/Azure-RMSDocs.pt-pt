---
title: classe mip::ProtectionEngine::Observer
description: Documenta a classe mip::protectionengine da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 2473e4bc1e64e3e8de498d2976d07b5324346a53
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573501"
---
# <a name="class-mipprotectionengineobserver"></a>classe mip::ProtectionEngine::Observer 
Interface que recebe notificações relacionadas com a [ProtectionEngine](class_mip_protectionengine.md).
Esta interface tem de ser implementada por aplicativos que usam a proteção de SDK
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnGetTemplatesSuccess de void virtual público (const std::shared_ptr\<Std:: vector\<Std:: String\>\>& templateIds, const std::shared_ptr\<void\>& contexto)  |  Chamado quando modelos foram obtidos com êxito.
OnGetTemplatesFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a obter modelos gerado um erro.
OnGetRightsForLabelIdSuccess de void virtual público (const std::shared_ptr\<Std:: vector\<Std:: String\>\>& direitos, const std::shared_ptr\<void\>& contexto)  |  Chamado quando direitos foram obtidos com êxito.
OnGetRightsForLabelIdFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a obter direitos para obter um ID de etiqueta para o utilizador.
  
## <a name="members"></a>Membros
  
### <a name="ongettemplatessuccess-function"></a>Função de OnGetTemplatesSuccess
Chamado quando modelos foram obtidos com êxito.

Parâmetros:  
* **templateIds**: Obter uma referência à lista de modelos 


* **context**: O mesmo contexto transmitido a [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function) e o mesmo contexto será encaminhado como-é [ProtectionEngine::Observer::O nGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess-function) ou [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure-function)
  
### <a name="ongettemplatesfailure-function"></a>Função de OnGetTemplatesFailure
Chamado quando a obter modelos gerado um erro.

Parâmetros:  
* **error**: [Erro](class_mip_error.md) que ocorreu ao obter modelos 


* **context**: O mesmo contexto transmitido a [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync-function) e o mesmo contexto será encaminhado como-é [ProtectionEngine::Observer::O nGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess-function) ou [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure-function)
  
### <a name="ongetrightsforlabelidsuccess-function"></a>Função de OnGetRightsForLabelIdSuccess
Chamado quando direitos foram obtidos com êxito.

Parâmetros:  
* **direitos**: Obter uma referência para a lista de direitos 


* **context**: O mesmo contexto transmitido a [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync-function)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync-function) e o mesmo contexto será encaminhado como-é [ProtectionEngine::O bserver::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess-function) ou [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure-function)
  
### <a name="ongetrightsforlabelidfailure-function"></a>Função de OnGetRightsForLabelIdFailure
Chamado quando a obter direitos para obter um ID de etiqueta para o utilizador.

Parâmetros:  
* **error**: [Erro](class_mip_error.md) que ocorreu ao obter direitos 


* **context**: O mesmo contexto transmitido a [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync-function)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync-function) e o mesmo contexto será encaminhado como-é [ProtectionEngine::O bserver::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess-function) ou [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure-function)