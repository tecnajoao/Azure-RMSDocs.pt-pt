# <a name="class-mipprotectionprofileobserver"></a>classe mip::ProtectionProfile::Observer 
Interface que recebe notificações relacionadas com a [ProtectionProfile](class_mip_protectionprofile.md).
Essa interface por tem implementada por aplicativos que usam a proteção de SDK
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnLoadSuccess de void virtual público (const std::shared_ptr<ProtectionProfile>& perfil, const std::shared_ptr<void>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando o carregamento de um perfil provocou um erro.
OnListEnginesSuccess de void virtual público (Std:: vector const < Std:: String > & engineIds, const std::shared_ptr<void>& contexto)  |  Chamado quando a lista de motores de foi gerada com êxito.
OnListEnginesError de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a listagem mecanismos resultou num erro.
OnAddEngineSuccess de void virtual público (const std::shared_ptr<ProtectionEngine>& mecanismo, const std::shared_ptr<void>& contexto)  |  Chamado quando um novo mecanismo de foi adicionado com êxito.
OnAddEngineError de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando adicionar um novo mecanismo de resultou num erro.
OnDeleteEngineSuccess de void virtual público (const std::shared_ptr<void>& contexto)  |  Chamado quando um motor de foi eliminado com êxito.
OnDeleteEngineError de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a eliminação de um motor de resultou num erro.
  
## <a name="members"></a>Membros
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.

Parâmetros:  
* **perfil**: uma referência para o recém-criado [ProtectionProfile](class_mip_protectionprofile.md)


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync) e o mesmo contexto será encaminhado como-é [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) ou [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onloadfailure"></a>OnLoadFailure
Chamado quando o carregamento de um perfil provocou um erro.

Parâmetros:  
* **erro**: [erro](class_mip_error.md) que ocorreu ao carregar 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync) e o mesmo contexto será encaminhado como-é [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) ou [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.

Parâmetros:  
* **engineIds**: uma lista de ids de motor estão disponíveis. 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)


  
### <a name="onlistengineserror"></a>OnListEnginesError
Chamado quando a listagem mecanismos resultou num erro.

Parâmetros:  
* **erro**: o erro que fazem com que os mecanismos de lista falha da operação. 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::ListEnginesAsync](class_mip_protectionprofile.md#listenginesasync)


  
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Chamado quando um novo mecanismo de foi adicionado com êxito.

Parâmetros:  
* **motor**: motor recentemente criado 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


  
### <a name="onaddengineerror"></a>OnAddEngineError
Chamado quando adicionar um novo mecanismo de resultou num erro.

Parâmetros:  
* **erro**: o erro que fazem com que a operação de motor de adicionar a falhar. 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::AddEngineAsync](class_mip_protectionprofile.md#addengineasync)


  
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Chamado quando um motor de foi eliminado com êxito.

Parâmetros:  
* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)


  
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Chamado quando a eliminação de um motor de resultou num erro.

Parâmetros:  
* **erro**: o erro que fazem com que a operação de motor de eliminação efetuar a ativação. 


* **contexto**: O mesmo contexto transmitido a [ProtectionProfile::DeleteEngineAsync](class_mip_protectionprofile.md#deleteengineasync)

