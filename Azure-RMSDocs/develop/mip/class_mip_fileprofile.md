# <a name="class-mipfileprofile"></a>classe mip::FileProfile 
[FileProfile](class_mip_fileprofile.md) classe é a classe de raiz para utilizar as operações de proteção de informações da Microsoft.
Uma aplicação típica só precisará de um [perfil](class_mip_profile.md) , mas pode criar vários perfis se for necessário.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 pública ~FileProfile() virtual  | _Ainda não documentado._
 Definições de const público & GetSettings() const  |  Devolve as definições de perfil.
ListEnginesAsync void público (const std::shared_ptr<void>& contexto)  |  Inicia uma lista operação motores.
UnloadEngineAsync void público (const std::string & id, const std::shared_ptr<void>& contexto)  |  Inicia o descarregamento o motor de ficheiro com o id especificado.
AddEngineAsync void público (const FileEngine::Settings & definições, const std::shared_ptr<void>& contexto)  |  Inicia a adicionar um novo motor de ficheiro para o perfil.
DeleteEngineAsync void público (const std::string & id, const std::shared_ptr<void>& contexto)  |  Inicia a eliminar o motor de ficheiro com o id especificado. Todos os dados para o perfil especificado serão eliminados por completo.
 FileProfile() protegido  | _Ainda não documentado._
  
## <a name="members"></a>Membros
  
### <a name="fileprofile"></a>~ FileProfile
_Não documentados ainda._

  
### <a name="settings"></a>Definições
Devolve as definições de perfil.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Inicia uma lista operação motores.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Inicia o descarregamento o motor de ficheiro com o id especificado. [FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="addengineasync"></a>AddEngineAsync
Inicia a adicionar um novo motor de ficheiro para o perfil.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Inicia a eliminar o motor de ficheiro com o id especificado. Todos os dados para o perfil especificado serão eliminados por completo.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="fileprofile"></a>FileProfile
_Não documentados ainda._
