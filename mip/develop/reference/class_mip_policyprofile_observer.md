---
title: classe mip PolicyProfile observador
description: Referência para a classe mip PolicyProfile observador
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 5de2156f4906c14e4ebc1418df8acb092c089d7d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446972"
---
# <a name="class-mippolicyprofileobserver"></a>classe mip::PolicyProfile::Observer 
[Observador](class_mip_policyprofile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
Todos os erros herdam [mip::Error](class_mip_error.md). Cliente não deve chamar o mecanismo de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnLoadSuccess de void virtual público (const std::shared_ptr<PolicyProfile>& perfil, const std::shared_ptr<void>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando o carregamento de um perfil provocou um erro.
OnListEnginesSuccess de void virtual público (Std:: vector const < Std:: String > & engineIds, const std::shared_ptr<void>& contexto)  |  Chamado quando a lista de motores de foi gerada com êxito.
OnListEnginesFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a listagem mecanismos provocou um erro.
OnUnloadEngineSuccess de void virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor de foi descarregado com êxito.
OnUnloadEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando o descarregamento de um motor de provocou um erro.
OnAddEngineSuccess de void virtual público (const std::shared_ptr<PolicyEngine>& mecanismo, const std::shared_ptr<void>& contexto)  |  Chamado quando um novo mecanismo de foi adicionado com êxito.
OnAddEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando adicionar um novo mecanismo de provocou um erro.
OnDeleteEngineSuccess de void virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor de foi eliminado com êxito.
OnDeleteEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a eliminação de um motor de provocou um erro.
 OnPolicyChanged de void virtual público (const Std:: String & engineId)  |  Chamado quando a política foi alterado para o motor com o ID especificado.
  
## <a name="members"></a>Membros
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.

Parâmetros:  
* **perfil**: o perfil atual utilizado para iniciar a operação. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onloadfailure"></a>OnLoadFailure
Chamado quando o carregamento de um perfil provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação de carga. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.

Parâmetros:  
* **engineIds**: uma lista de IDs de motor estão disponíveis. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
Chamado quando a listagem mecanismos provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação de motor da lista. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Chamado quando um motor de foi descarregado com êxito.

Parâmetros:  
* **contexto**: o contexto transmitido para a operação.


  
### <a name="onunloadenginefailure"></a>OnUnloadEngineFailure
Chamado quando o descarregamento de um motor de provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação de motor do descarregamento. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Chamado quando um novo mecanismo de foi adicionado com êxito.
  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
Chamado quando adicionar um novo mecanismo de provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação adicionar motor. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Chamado quando um motor de foi eliminado com êxito.

Parâmetros:  
* **contexto**: o contexto transmitido para a operação.


  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
Chamado quando a eliminação de um motor de provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação delete motor. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onpolicychanged"></a>OnPolicyChanged
Chamado quando a política foi alterado para o motor com o ID especificado.

Parâmetros:  
* **engineId**: o motor 


Para carregar a nova política é necessário chamar AddEngineAsync novamente com o ID de motor tendo em conta.