---
title: classe mip FileProfile observador
description: Referência para a classe mip FileProfile observador
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 105380ef63f6533839190e4c9e3f3ee5379781f1
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446401"
---
# <a name="class-mipfileprofileobserver"></a>classe mip::FileProfile::Observer 
[Observador](class_mip_fileprofile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
Todos os erros herdam [mip::Error](class_mip_error.md). Cliente não deve chamar o mecanismo de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público ~Observer() virtual  | _Ainda não documentado._
OnLoadSuccess de void virtual público (std::shared_ptr const < mip::FileProfile > & perfil, const std::shared_ptr<void>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando o carregamento de um perfil provocou um erro.
OnListEnginesSuccess de void virtual público (Std:: vector const < Std:: String > & engineIds, const std::shared_ptr<void>& contexto)  |  Chamado quando a lista de motores de foi gerada com êxito.
OnListEnginesFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a listagem mecanismos provocou um erro.
OnUnloadEngineSuccess de void virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor de foi descarregado com êxito.
OnUnloadEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando o descarregamento de um motor de provocou um erro.
OnAddEngineSuccess de void virtual público (std::shared_ptr const < mip::FileEngine > & mecanismo, const std::shared_ptr<void>& contexto)  |  Chamado quando um novo mecanismo de foi adicionado com êxito.
OnAddEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando adicionar um novo mecanismo de provocou um erro.
OnDeleteEngineSuccess de void virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor de foi eliminado com êxito.
OnDeleteEngineFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a eliminação de um motor de provocou um erro.
 OnPolicyChanged de void virtual público (const Std:: String & engineId)  |  Chamado quando a política foi alterado para o motor com o ID especificado.
 Observer() protegido  | _Ainda não documentado._
  
## <a name="members"></a>Membros
  
### <a name="observer"></a>~ Observador
_Não documentados ainda._

  
### <a name="onloadsuccess"></a>OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.
  
### <a name="onloadfailure"></a>OnLoadFailure
Chamado quando o carregamento de um perfil provocou um erro.
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.
  
### <a name="onlistenginesfailure"></a>OnListEnginesFailure
Chamado quando a listagem mecanismos provocou um erro.
  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Chamado quando um motor de foi descarregado com êxito.
  
### <a name="onunloadenginefailure"></a>OnUnloadEngineFailure
Chamado quando o descarregamento de um motor de provocou um erro.
  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Chamado quando um novo mecanismo de foi adicionado com êxito.
  
### <a name="onaddenginefailure"></a>OnAddEngineFailure
Chamado quando adicionar um novo mecanismo de provocou um erro.
  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Chamado quando um motor de foi eliminado com êxito.
  
### <a name="ondeleteenginefailure"></a>OnDeleteEngineFailure
Chamado quando a eliminação de um motor de provocou um erro.
  
### <a name="onpolicychanged"></a>OnPolicyChanged
Chamado quando a política foi alterado para o motor com o ID especificado.
  
### <a name="observer"></a>Observador
_Não documentados ainda._