---
title: classe mip::ProtectionProfile::Observer
description: Documenta a classe mip::protectionprofile da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: ad8aebf1c5c05dfeed1e04a59dd7190406c5603c
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651416"
---
# <a name="class-mipprotectionprofileobserver"></a>classe mip::ProtectionProfile::Observer 
Interface que recebe notificações relacionadas com a [ProtectionProfile](class_mip_protectionprofile.md).
Esta interface tem de ser implementada por aplicativos que usam a proteção de SDK
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnLoadSuccess de void virtual público (const std::shared_ptr\<ProtectionProfile\>& perfil, const std::shared_ptr\<void\>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando o carregamento de um perfil provocou um erro.
OnListEnginesSuccess de void virtual público (Std:: vector const\<Std:: String\>& engineIds, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a lista de motores de foi gerada com êxito.
OnListEnginesFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a listagem mecanismos resultou num erro.
OnAddEngineSuccess de void virtual público (const std::shared_ptr\<ProtectionEngine\>& mecanismo, const std::shared_ptr\<void\>& contexto)  |  Chamado quando um novo mecanismo de foi adicionado com êxito.
OnAddEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando adicionar um novo mecanismo de resultou num erro.
OnDeleteEngineSuccess de void virtual público (const std::shared_ptr\<void\>& contexto)  |  Chamado quando um motor de foi eliminado com êxito.
OnDeleteEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a eliminação de um motor de resultou num erro.
  
## <a name="members"></a>Membros
  
### <a name="onloadsuccess-function"></a>Função de OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.

Parâmetros:  
* **profile**: Uma referência para o recém-criado [ProtectionProfile](class_mip_protectionprofile.md)


* **context**: O mesmo contexto transmitido a [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync-function)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync-function) e o mesmo contexto será encaminhado como-é [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess-function) ou [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure-function)
  
### <a name="onloadfailure-function"></a>Função de OnLoadFailure
Chamado quando o carregamento de um perfil provocou um erro.

Parâmetros:  
* **error**: [Erro](class_mip_error.md) que ocorreu ao carregar 


* **context**: O mesmo contexto transmitido a [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync-function)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function) para [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#addengineasync-function) e o mesmo contexto será encaminhado como-é [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess-function) ou [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure-function)
  
### <a name="onlistenginessuccess-function"></a>Função de OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.

Parâmetros:  
* **engineIds**: uma lista de IDs de motor estão disponíveis. 


* **context**: O mesmo contexto transmitido a [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync-function)


  
### <a name="onlistenginesfailure-function"></a>Função de OnListEnginesFailure
Chamado quando a listagem mecanismos resultou num erro.

Parâmetros:  
* **erro**: erro que provocou os mecanismos de lista falha da operação. 


* **context**: O mesmo contexto transmitido a [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync-function)


  
### <a name="onaddenginesuccess-function"></a>Função de OnAddEngineSuccess
Chamado quando um novo mecanismo de foi adicionado com êxito.

Parâmetros:  
* **motor**: Criado recentemente motor 


* **context**: O mesmo contexto transmitido a [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync-function)


  
### <a name="onaddenginefailure-function"></a>Função de OnAddEngineFailure
Chamado quando adicionar um novo mecanismo de resultou num erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação adicionar motor. 


* **context**: O mesmo contexto transmitido a [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync-function)


  
### <a name="ondeleteenginesuccess-function"></a>Função de OnDeleteEngineSuccess
Chamado quando um motor de foi eliminado com êxito.

Parâmetros:  
* **context**: O mesmo contexto transmitido a [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync-function)


  
### <a name="ondeleteenginefailure-function"></a>Função de OnDeleteEngineFailure
Chamado quando a eliminação de um motor de resultou num erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação delete motor. 


* **context**: O mesmo contexto transmitido a [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync-function)

