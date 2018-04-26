# <a name="class-mipprofileobserver"></a>classe mip::Profile::Observer 
[Observador](#classmip_1_1_profile_1_1_observer) interface para os clientes receber notificações para o perfil de eventos relacionados.
Se um * evento de erro ocorre, o objeto erro contém dentro [mip::Error](#classmip_1_1_error) classe. Cliente deve não chamar o motor de volta no thread que chama o observador.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública inline virtual void OnLoadSuccessProfile > & perfil, const std::shared_ptr < void > & contexto) | Chamado quando o perfil foi carregado com êxito.
pública inline virtual void OnLoadFailure | Chamado quando carregar um perfil causou um erro.
pública inline virtual void OnListEnginesSuccess | Chamado quando a lista de motores de foi gerada com êxito.
pública inline virtual void OnListEnginesError | Chamado quando a listagem motores causou um erro.
pública inline virtual void OnUnloadEngineSuccess | Chamado quando um motor foi descarregado com êxito.
pública inline virtual void OnUnloadEngineError | Chamado quando o descarregamento de um motor causou um erro.
pública inline virtual void OnAddEngineSuccessPolicyEngine > & motor, const std::shared_ptr < void > & contexto) | Chamado quando um novo motor foi adicionado com êxito.
pública inline virtual void OnAddEngineError | Chamado quando adicionar um novo motor causou um erro.
pública inline virtual void OnDeleteEngineSuccess | Chamado quando um motor foi eliminado com êxito.
pública inline virtual void OnDeleteEngineError | Chamado quando a eliminação de um motor causou um erro.
pública inline virtual void OnPolicyChanged | Chamado quando a política foi alterada para o motor com o id especificado.
## <a name="members"></a>Membros
### <a name="onloadsuccess"></a>OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.
#### <a name="parameters"></a>Parâmetros
* o perfil atual utilizado para iniciar a operação do perfil. 
* o contexto de contexto transmitido para a operação.
### <a name="onloadfailure"></a>OnLoadFailure
Chamado quando carregar um perfil causou um erro.
#### <a name="parameters"></a>Parâmetros
* Erro de erro provocar a falha da operação de carga. 
* o contexto de contexto transmitido para a operação.
### <a name="onlistenginessuccess"></a>OnListEnginesSuccess
Chamado quando a lista de motores de foi gerada com êxito.
#### <a name="parameters"></a>Parâmetros
* motor de engineIds uma lista de ids estão disponíveis. 
* o contexto de contexto transmitido para a operação.
### <a name="onlistengineserror"></a>OnListEnginesError
Chamado quando a listagem motores causou um erro.
#### <a name="parameters"></a>Parâmetros
* Erro de erro que fazer com que a lista de motor de operação não foi bem-sucedida. 
* o contexto de contexto transmitido para a operação.
### <a name="onunloadenginesuccess"></a>OnUnloadEngineSuccess
Chamado quando um motor foi descarregado com êxito.
#### <a name="parameters"></a>Parâmetros
* o contexto de contexto transmitido para a operação.
### <a name="onunloadengineerror"></a>OnUnloadEngineError
Chamado quando o descarregamento de um motor causou um erro.
#### <a name="parameters"></a>Parâmetros
* Erro de erro que fazer com que o descarregamento de motor de operação não foi bem-sucedida. 
* o contexto de contexto transmitido para a operação.
### <a name="onaddenginesuccess"></a>OnAddEngineSuccess
Chamado quando um novo motor foi adicionado com êxito.
### <a name="onaddengineerror"></a>OnAddEngineError
Chamado quando adicionar um novo motor causou um erro.
#### <a name="parameters"></a>Parâmetros
* Erro de erro provocar a adicionar motor de operação não foi bem-sucedida. 
* o contexto de contexto transmitido para a operação.
### <a name="ondeleteenginesuccess"></a>OnDeleteEngineSuccess
Chamado quando um motor foi eliminado com êxito.
#### <a name="parameters"></a>Parâmetros
* o contexto de contexto transmitido para a operação.
### <a name="ondeleteengineerror"></a>OnDeleteEngineError
Chamado quando a eliminação de um motor causou um erro.
#### <a name="parameters"></a>Parâmetros
* Erro de erro provocar a eliminação motor de operação não foi bem-sucedida. 
* o contexto de contexto transmitido para a operação.
### <a name="onpolicychanged"></a>OnPolicyChanged
Chamado quando a política foi alterada para o motor com o id especificado.
#### <a name="parameters"></a>Parâmetros
* engineId motor ao carregar a nova política é necessário chamar AddEngineAsync novamente com o Id indicado do motor.