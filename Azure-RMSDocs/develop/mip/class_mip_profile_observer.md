# <a name="class-mipprofileobserver"></a>classe mip::Profile::Observer 
[Observador](class_mip_profile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
Se um * eventos de erro ocorrer, o objeto de erro contém dentro [mip::Error](class_mip_error.md) classe. Cliente não deve chamar o mecanismo de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnLoadSuccess de void virtual público (const std::shared_ptr<Profile>& perfil, const std::shared_ptr<void>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando o carregamento de um perfil provocou um erro.
OnListEnginesSuccess de void virtual público (Std:: vector const < Std:: String > & engineIds, const std::shared_ptr<void>& contexto)  |  Chamado quando a lista de motores de foi gerada com êxito.
OnListEnginesError de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a listagem mecanismos provocou um erro.
OnUnloadEngineSuccess de void virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor de foi descarregado com êxito.
OnUnloadEngineError de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando o descarregamento de um motor de provocou um erro.
OnAddEngineSuccess de void virtual público (const std::shared_ptr<PolicyEngine>& mecanismo, const std::shared_ptr<void>& contexto)  |  Chamado quando um novo mecanismo de foi adicionado com êxito.
OnAddEngineError de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando adicionar um novo mecanismo de provocou um erro.
OnDeleteEngineSuccess de void virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor de foi eliminado com êxito.
OnDeleteEngineError de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a eliminação de um motor de provocou um erro.
 OnPolicyChanged de void virtual público (const Std:: String & engineId)  |  Chamado quando a política foi alterado para o motor com o id especificado.
  
## <a name="members"></a>Membros
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.

Parâmetros:  
* **perfil**: o perfil atual utilizado para iniciar a operação. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onloadfailure"></a>OnLoadFailure
Chamado quando o carregamento de um perfil provocou um erro.

Parâmetros:  
* **erro**: o erro que fazem com que a operação de carregamento falhe. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.

Parâmetros:  
* **engineIds**: uma lista de ids de motor estão disponíveis. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onlistengineserror"></a>OnListEnginesError
Chamado quando a listagem mecanismos provocou um erro.

Parâmetros:  
* **erro**: o erro que fazem com que a falha da operação de motor da lista. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Chamado quando um motor de foi descarregado com êxito.

Parâmetros:  
* **contexto**: o contexto transmitido para a operação.


  
### <a name="onunloadengineerror"></a>OnUnloadEngineError
Chamado quando o descarregamento de um motor de provocou um erro.

Parâmetros:  
* **erro**: o erro que fazem com que a operação de descarregamento de motor efetuar a ativação. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Chamado quando um novo mecanismo de foi adicionado com êxito.
  
### <a name="onaddengineerror"></a>OnAddEngineError
Chamado quando adicionar um novo mecanismo de provocou um erro.

Parâmetros:  
* **erro**: o erro que fazem com que a operação de motor de adicionar a falhar. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Chamado quando um motor de foi eliminado com êxito.

Parâmetros:  
* **contexto**: o contexto transmitido para a operação.


  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Chamado quando a eliminação de um motor de provocou um erro.

Parâmetros:  
* **erro**: o erro que fazem com que a operação de motor de eliminação efetuar a ativação. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onpolicychanged"></a>OnPolicyChanged
Chamado quando a política foi alterado para o motor com o id especificado.

Parâmetros:  
* **engineId**: o motor 


Para carregar a nova política é necessário chamar AddEngineAsync novamente com o mecanismo de Id fornecido.