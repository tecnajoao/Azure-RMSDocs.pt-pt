# <a name="class-mipprofileobserver"></a>classe mip::Profile::Observer 
[Observador](class_mip_profile_observer.md) interface para os clientes receber notificações para o perfil de eventos relacionados.
Se um * evento de erro ocorre, o objeto erro contém dentro [mip::Error](class_mip_error.md) classe. Cliente deve não chamar o motor de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnLoadSuccess void de virtual público (const std::shared_ptr<Profile>& perfil, const std::shared_ptr<void>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure void de virtual público (const std::exception_ptr & erro, const std::shared_ptr<void>& contexto)  |  Chamado quando carregar um perfil causou um erro.
OnListEnginesSuccess void de virtual público (std::vector const < std::string > & engineIds, const std::shared_ptr<void>& contexto)  |  Chamado quando a lista de motores de foi gerada com êxito.
OnListEnginesError void de virtual público (const std::exception_ptr & erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a listagem motores causou um erro.
OnUnloadEngineSuccess void de virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor foi descarregado com êxito.
OnUnloadEngineError void de virtual público (const std::exception_ptr & erro, const std::shared_ptr<void>& contexto)  |  Chamado quando o descarregamento de um motor causou um erro.
OnAddEngineSuccess void de virtual público (const std::shared_ptr<PolicyEngine>& motor, const std::shared_ptr<void>& contexto)  |  Chamado quando um novo motor foi adicionado com êxito.
OnAddEngineError void de virtual público (const std::exception_ptr & erro, const std::shared_ptr<void>& contexto)  |  Chamado quando adicionar um novo motor causou um erro.
OnDeleteEngineSuccess void de virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor foi eliminado com êxito.
OnDeleteEngineError void de virtual público (const std::exception_ptr & erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a eliminação de um motor causou um erro.
 OnPolicyChanged void de virtual público (const std::string & engineId)  |  Chamado quando a política foi alterada para o motor com o id especificado.
  
## <a name="members"></a>Membros
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.

Parâmetros:  
* **perfil**: o perfil atual utilizado para iniciar a operação. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onloadfailure"></a>OnLoadFailure
Chamado quando carregar um perfil causou um erro.

Parâmetros:  
* **erro**: erro provocar a falha da operação de carga. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.

Parâmetros:  
* **engineIds**: uma lista de ids de motor estão disponíveis. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onlistengineserror"></a>OnListEnginesError
Chamado quando a listagem motores causou um erro.

Parâmetros:  
* **erro**: erro provocar a falha da operação de motor da lista. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Chamado quando um motor foi descarregado com êxito.

Parâmetros:  
* **contexto**: o contexto transmitido para a operação.


  
### <a name="onunloadengineerror"></a>OnUnloadEngineError
Chamado quando o descarregamento de um motor causou um erro.

Parâmetros:  
* **erro**: o erro que fazer com que a operação de motor de descarregamento falhar. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Chamado quando um novo motor foi adicionado com êxito.
  
### <a name="onaddengineerror"></a>OnAddEngineError
Chamado quando adicionar um novo motor causou um erro.

Parâmetros:  
* **erro**: o erro que fazer com que a operação de motor de adicionar a falhar. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Chamado quando um motor foi eliminado com êxito.

Parâmetros:  
* **contexto**: o contexto transmitido para a operação.


  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Chamado quando a eliminação de um motor causou um erro.

Parâmetros:  
* **erro**: o erro que fazer com que a operação de motor de eliminação falhou. 


* **contexto**: o contexto transmitido para a operação.


  
### <a name="onpolicychanged"></a>OnPolicyChanged
Chamado quando a política foi alterada para o motor com o id especificado.

Parâmetros:  
* **engineId**: o motor 


Para carregar a nova política é necessário chamar AddEngineAsync novamente com o Id indicado do motor.