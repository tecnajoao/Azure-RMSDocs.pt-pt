---
title: classe mip ProtectionProfile observador
description: Referência para a classe mip ProtectionProfile observador
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3678e6c1e1659f28b2f1dcc36f61295a8d29393e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446435"
---
# <a name="class-mipprotectionprofileobserver"></a>classe mip::ProtectionProfile::Observer 
Interface que recebe notificações relacionadas com a [ProtectionProfile](class_mip_protectionprofile.md).
Esta interface tem de ser implementada por aplicativos que usam a proteção de SDK
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnLoadSuccess de void virtual público (const std::shared_ptr<ProtectionProfile>& perfil, const std::shared_ptr<void>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando o carregamento de um perfil provocou um erro.
OnListEnginesSuccess de void virtual público (Std:: vector const < Std:: String > & engineIds, const std::shared_ptr<void>& contexto)  |  Chamado quando a lista de motores de foi gerada com êxito.
OnListEnginesFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a listagem mecanismos resultou num erro.
OnAddEngineSuccess de void virtual público (const std::shared_ptr<ProtectionEngine>& mecanismo, const std::shared_ptr<void>& contexto)  |  Chamado quando um novo mecanismo de foi adicionado com êxito.
OnAddEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando adicionar um novo mecanismo de resultou num erro.
OnDeleteEngineSuccess de void virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor de foi eliminado com êxito.
OnDeleteEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a eliminação de um motor de resultou num erro.
  
## <a name="members"></a>Membros
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.

Parâmetros:  
* **perfil**: uma referência para o recém-criado [ProtectionProfile](class_mip_protectionprofile.md)


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync) e o mesmo contexto será encaminhado como-é [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) ou [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onloadfailure"></a>OnLoadFailure
Chamado quando o carregamento de um perfil provocou um erro.

Parâmetros:  
* **erro**: [erro](class_mip_error.md) que ocorreu ao carregar 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync) e o mesmo contexto será encaminhado como-é [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) ou [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.

Parâmetros:  
* **engineIds**: uma lista de IDs de motor estão disponíveis. 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)


  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
Chamado quando a listagem mecanismos resultou num erro.

Parâmetros:  
* **erro**: erro que provocou os mecanismos de lista falha da operação. 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Chamado quando um novo mecanismo de foi adicionado com êxito.

Parâmetros:  
* **motor**: recém-criado motor 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
Chamado quando adicionar um novo mecanismo de resultou num erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação adicionar motor. 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Chamado quando um motor de foi eliminado com êxito.

Parâmetros:  
* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)


  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
Chamado quando a eliminação de um motor de resultou num erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação delete motor. 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)

