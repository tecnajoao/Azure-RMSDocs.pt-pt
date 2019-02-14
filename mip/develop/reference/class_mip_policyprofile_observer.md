---
title: classe mip::PolicyProfile::Observer
description: Documenta a classe mip::policyprofile da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 1a07f71f54889d203ad47f38ad1b101240938b9b
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254158"
---
# <a name="class-mippolicyprofileobserver"></a>classe mip::PolicyProfile::Observer 
[Observador](class_mip_policyprofile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
Todos os erros herdam [mip::Error](class_mip_error.md). Cliente não deve chamar o mecanismo de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnLoadSuccess de void virtual público (const std::shared_ptr\<PolicyProfile\>& perfil, const std::shared_ptr\<void\>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando o carregamento de um perfil provocou um erro.
OnListEnginesSuccess de void virtual público (Std:: vector const\<Std:: String\>& engineIds, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a lista de motores de foi gerada com êxito.
OnListEnginesFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a listagem mecanismos provocou um erro.
OnUnloadEngineSuccess de void virtual público (const std::shared_ptr\<void\>& contexto)  |  Chamado quando um motor de foi descarregado com êxito.
OnUnloadEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando o descarregamento de um motor de provocou um erro.
OnAddEngineSuccess de void virtual público (const std::shared_ptr\<PolicyEngine\>& mecanismo, const std::shared_ptr\<void\>& contexto)  |  Chamado quando um novo mecanismo de foi adicionado com êxito.
OnAddEngineStarting void virtual público (bool requiresPolicyFetch)  |  Chamado antes da criação do motor para descrever ou não os dados de política do mecanismo devem ser obtidos do servidor ou se ele pode ser criado a partir de dados armazenados em cache localmente.
OnAddEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando adicionar um novo mecanismo de provocou um erro.
OnDeleteEngineSuccess de void virtual público (const std::shared_ptr\<void\>& contexto)  |  Chamado quando um motor de foi eliminado com êxito.
OnDeleteEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a eliminação de um motor de provocou um erro.
OnPolicyChanged de void virtual público (const Std:: String & engineId)  |  Chamado quando a política foi alterado para o motor com o ID fornecido ou quando os tipos de sensibilidade personalizada carregada foram alterados.
  
## <a name="members"></a>Membros
  
### <a name="onloadsuccess-function"></a>Função de OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.

Parâmetros:  
* **perfil**: o perfil atual utilizado para iniciar a operação. 


* **contexto**: o contexto transmitido para a operação de LoadAsync.


  
### <a name="onloadfailure-function"></a>Função de OnLoadFailure
Chamado quando o carregamento de um perfil provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação de carga. 


* **contexto**: o contexto transmitido para a operação de LoadAsync.


  
### <a name="onlistenginessuccess-function"></a>Função de OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.

Parâmetros:  
* **engineIds**: uma lista de IDs de motor estão disponíveis. 


* **contexto**: o contexto transmitido para a operação de ListEnginesAsync.


  
### <a name="onlistenginesfailure-function"></a>Função de OnListEnginesFailure
Chamado quando a listagem mecanismos provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação de motor da lista. 


* **contexto**: o contexto transmitido para a operação de ListEnginesAsync.


  
### <a name="onunloadenginesuccess-function"></a>Função de OnUnloadEngineSuccess
Chamado quando um motor de foi descarregado com êxito.

Parâmetros:  
* **contexto**: o contexto transmitido para a operação de UnloadEngineAsync.


  
### <a name="onunloadenginefailure-function"></a>Função de OnUnloadEngineFailure
Chamado quando o descarregamento de um motor de provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação de motor do descarregamento. 


* **contexto**: o contexto transmitido para a operação de UnloadEngineAsync.


  
### <a name="onaddenginesuccess-function"></a>Função de OnAddEngineSuccess
Chamado quando um novo mecanismo de foi adicionado com êxito.

Parâmetros:  
* **motor**: o motor recentemente adicionado 


* **contexto**: o contexto transmitido para a operação de AddEngineAsync


  
### <a name="onaddenginestarting-function"></a>Função de OnAddEngineStarting
Chamado antes da criação do motor para descrever ou não os dados de política do mecanismo devem ser obtidos do servidor ou se ele pode ser criado a partir de dados armazenados em cache localmente.

Parâmetros:  
* **requiresPolicyFetch**: Descreve se os dados do motor devem ser obtidos por meio de HTTP ou se ele será carregado a partir da cache


Esse retorno de chamada opcional pode ser utilizado por uma aplicação para ser informado se é ou não uma operação de AddEngineAsync exigirá uma operação HTTP (com seu atraso associado) para concluir.
  
### <a name="onaddenginefailure-function"></a>Função de OnAddEngineFailure
Chamado quando adicionar um novo mecanismo de provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação adicionar motor. 


* **contexto**: o contexto transmitido para a operação de AddEngineAsync.


  
### <a name="ondeleteenginesuccess-function"></a>Função de OnDeleteEngineSuccess
Chamado quando um motor de foi eliminado com êxito.

Parâmetros:  
* **contexto**: o contexto transmitido para a operação de DeleteEngineAsync.


  
### <a name="ondeleteenginefailure-function"></a>Função de OnDeleteEngineFailure
Chamado quando a eliminação de um motor de provocou um erro.

Parâmetros:  
* **erro**: erro que provocou a falha da operação delete motor. 


* **contexto**: o contexto transmitido para a operação de DeleteEngineAsync.


  
### <a name="onpolicychanged-function"></a>Função de OnPolicyChanged
Chamado quando a política foi alterado para o motor com o ID fornecido ou quando os tipos de sensibilidade personalizada carregada foram alterados.

Parâmetros:  
* **engineId**: o motor 


Para carregar a nova política é necessário chamar AddEngineAsync novamente com o ID de motor tendo em conta.
