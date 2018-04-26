# <a name="class-mipfileprofile"></a>classe mip::FileProfile 
[FileProfile](#classmip_1_1_file_profile) classe é a classe de raiz para utilizar as operações de proteção de informações da Microsoft.
Uma aplicação típica só precisará de um [perfil](#classmip_1_1_profile) , mas pode criar vários perfis se for necessário.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública inline virtual ~ FileProfile | 
Definições de const público & GetSettings | Devolve as definições de perfil.
ListEnginesAsync void público | Inicia uma lista operação motores.
UnloadEngineAsync void público | Inicia o descarregamento o motor de ficheiro com o id especificado.
pública AddEngineAsyncFileEngine::Settings void & definições, const std::shared_ptr < void > & contexto) | Inicia a adicionar um novo motor de ficheiro para o perfil.
DeleteEngineAsync void público | Inicia a eliminar o motor de ficheiro com o id especificado. Todos os dados para o perfil especificado serão eliminados por completo.
inline protegido FileProfile | 
## <a name="members"></a>Membros
### <a name="fileprofile"></a>~ FileProfile
### <a name="settings"></a>Definições
Devolve as definições de perfil.
### <a name="listenginesasync"></a>ListEnginesAsync
Inicia uma lista operação motores.
[FileProfile::Observer](#classmip_1_1_file_profile_1_1_observer) será chamado após o êxito ou falha.
### <a name="unloadengineasync"></a>UnloadEngineAsync
Inicia o descarregamento o motor de ficheiro com o id especificado. [FileProfile::Observer](#classmip_1_1_file_profile_1_1_observer) será chamado após o êxito ou falha.
### <a name="addengineasync"></a>AddEngineAsync
Inicia a adicionar um novo motor de ficheiro para o perfil.
[FileProfile::Observer](#classmip_1_1_file_profile_1_1_observer) será chamado após o êxito ou falha.
### <a name="deleteengineasync"></a>DeleteEngineAsync
Inicia a eliminar o motor de ficheiro com o id especificado. Todos os dados para o perfil especificado serão eliminados por completo.
[FileProfile::Observer](#classmip_1_1_file_profile_1_1_observer) será chamado após o êxito ou falha.
### <a name="fileprofile"></a>FileProfile