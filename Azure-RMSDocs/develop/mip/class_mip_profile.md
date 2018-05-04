# <a name="class-mipprofile"></a>classe mip::Profile 
[Perfil](#classmip_1_1_profile) classe é a classe de raiz para utilizar as operações de proteção de informações da Microsoft. Uma aplicação típica só precisará de um [perfil](#classmip_1_1_profile) , mas pode criar vários perfis se for necessário.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de const público & GetSettings() const  |  Obter as definições definidas no perfil.
ListEnginesAsync void público (const std::shared_ptr<void>& contexto)  |  Inicia uma lista operação motores.
UnloadEngineAsync void público (const std::string & id, const std::shared_ptr<void>& contexto)  |  Inicia o descarregamento o motor de política com o id especificado.
AddEngineAsync void público (const PolicyEngine::Settings & definições, const std::shared_ptr<void>& contexto)  |  Inicia a adicionar um novo motor de política para o perfil.
DeleteEngineAsync void público (const std::string & id, const std::shared_ptr<void>& contexto)  |  Inicia a eliminar o motor de política com o id especificado. Todos os dados para o perfil especificado serão eliminados por completo.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obter as definições definidas no perfil.
  
#### <a name="returns"></a>Devolve
configurar as definições no perfil.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Inicia uma lista operação motores.
  
#### <a name="parameters"></a>Parâmetros
* contexto de um parâmetro que será transmitido para as funções de observador. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) será chamado após o êxito ou falha.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Inicia o descarregamento o motor de política com o id especificado.
  
#### <a name="parameters"></a>Parâmetros
* o id exclusivo do motor de ID. 
* contexto de um parâmetro que será transmitido para as funções de observador. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) será chamado após o êxito ou falha.
  
### <a name="addengineasync"></a>AddEngineAsync
Inicia a adicionar um novo motor de política para o perfil.
  
#### <a name="parameters"></a>Parâmetros
* definições de [mip::PolicyEngine::Settings](#classmip_1_1_policy_engine_1_1_settings) objet que especifica os parâmetros de motores. 
* contexto de um parâmetro que será transmitido para as funções de observador. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) será chamado após o êxito ou falha.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Inicia a eliminar o motor de política com o id especificado. Todos os dados para o perfil especificado serão eliminados por completo.
  
#### <a name="parameters"></a>Parâmetros
* o id exclusivo do motor de ID. 
* contexto de um parâmetro que será transmitido para as funções de observador. 
[Profile::Observer](#classmip_1_1_profile_1_1_observer) será chamado após o êxito ou falha.