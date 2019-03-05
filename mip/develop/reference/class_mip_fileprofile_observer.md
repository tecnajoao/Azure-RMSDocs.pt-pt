---
title: classe mip::FileProfile::Observer
description: Documenta a classe mip::fileprofile da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 7b9c3440d577e9ba2e08bdba6ed890d3a480c783
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57331023"
---
# <a name="class-mipfileprofileobserver"></a>classe mip::FileProfile::Observer 
[Observador](class_mip_fileprofile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
Todos os erros herdam [mip::Error](class_mip_error.md). Cliente não deve chamar o mecanismo de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public virtual ~Observer()  | _Ainda não documentado._
OnLoadSuccess de void virtual público (const std::shared_ptr\<mip::FileProfile\>& perfil, const std::shared_ptr\<void\>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando o carregamento de um perfil provocou um erro.
OnListEnginesSuccess de void virtual público (Std:: vector const\<Std:: String\>& engineIds, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a lista de motores de foi gerada com êxito.
OnListEnginesFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a listagem mecanismos provocou um erro.
OnUnloadEngineSuccess de void virtual público (const std::shared_ptr\<void\>& contexto)  |  Chamado quando um motor de foi descarregado com êxito.
OnUnloadEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando o descarregamento de um motor de provocou um erro.
OnAddEngineSuccess de void virtual público (const std::shared_ptr\<mip::FileEngine\>& mecanismo, const std::shared_ptr\<void\>& contexto)  |  Chamado quando um novo mecanismo de foi adicionado com êxito.
OnAddEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando adicionar um novo mecanismo de provocou um erro.
OnDeleteEngineSuccess de void virtual público (const std::shared_ptr\<void\>& contexto)  |  Chamado quando um motor de foi eliminado com êxito.
OnDeleteEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a eliminação de um motor de provocou um erro.
OnPolicyChanged de void virtual público (const Std:: String & engineId)  |  Chamado quando a política foi alterado para o motor com o ID especificado.
OnAddPolicyEngineStarting void virtual público (bool requiresPolicyFetch)  |  Chamado antes da criação do motor para descrever ou não os dados de política do motor de política devem ser obtidos do servidor ou se ele pode ser criado a partir de dados armazenados em cache localmente.
Observer() protegido  | _Ainda não documentado._
  
## <a name="members"></a>Membros
  
### <a name="observer-function"></a>~ Função de observador
_Não documentados ainda._

  
### <a name="onloadsuccess-function"></a>Função de OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.
  
### <a name="onloadfailure-function"></a>Função de OnLoadFailure
Chamado quando o carregamento de um perfil provocou um erro.
  
### <a name="onlistenginessuccess-function"></a>Função de OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.
  
### <a name="onlistenginesfailure-function"></a>Função de OnListEnginesFailure
Chamado quando a listagem mecanismos provocou um erro.
  
### <a name="onunloadenginesuccess-function"></a>Função de OnUnloadEngineSuccess
Chamado quando um motor de foi descarregado com êxito.
  
### <a name="onunloadenginefailure-function"></a>Função de OnUnloadEngineFailure
Chamado quando o descarregamento de um motor de provocou um erro.
  
### <a name="onaddenginesuccess-function"></a>Função de OnAddEngineSuccess
Chamado quando um novo mecanismo de foi adicionado com êxito.
  
### <a name="onaddenginefailure-function"></a>Função de OnAddEngineFailure
Chamado quando adicionar um novo mecanismo de provocou um erro.
  
### <a name="ondeleteenginesuccess-function"></a>Função de OnDeleteEngineSuccess
Chamado quando um motor de foi eliminado com êxito.
  
### <a name="ondeleteenginefailure-function"></a>Função de OnDeleteEngineFailure
Chamado quando a eliminação de um motor de provocou um erro.
  
### <a name="onpolicychanged-function"></a>Função de OnPolicyChanged
Chamado quando a política foi alterado para o motor com o ID especificado.
  
### <a name="onaddpolicyenginestarting-function"></a>Função de OnAddPolicyEngineStarting
Chamado antes da criação do motor para descrever ou não os dados de política do motor de política devem ser obtidos do servidor ou se ele pode ser criado a partir de dados armazenados em cache localmente.

Parâmetros:  
* **requiresPolicyFetch**: Descreve se os dados do motor devem ser obtidos por meio de HTTP ou se ele será carregado a partir da cache


Esse retorno de chamada opcional pode ser utilizado por uma aplicação para ser informado se é ou não uma operação de AddEngineAsync exigirá uma operação HTTP (com seu atraso associado) para concluir.
  
### <a name="observer-function"></a>Função de observador
_Não documentados ainda._
