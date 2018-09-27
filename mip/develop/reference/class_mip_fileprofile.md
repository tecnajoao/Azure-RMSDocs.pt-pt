# <a name="class-mipfileprofile"></a>classe mip::FileProfile 
[FileProfile](class_mip_fileprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar.
Um aplicativo típico irá apenas precisa de um [perfil](class_mip_profile.md) , mas ele pode criar vários perfis, se for necessário.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Devolve as definições de perfil.
ListEnginesAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a lista a operação de mecanismos.
UnloadEngineAsync void pública (Std:: String const & id, const std::shared_ptr<void>& contexto)  |  Começa a descarregar o mecanismo de ficheiro com o id especificado.
AddEngineAsync void pública (const FileEngine::Settings e definições, const std::shared_ptr<void>& contexto)  |  Inicia a adicionar um novo mecanismo de ficheiro para o perfil.
DeleteEngineAsync void pública (Std:: String const & id, const std::shared_ptr<void>& contexto)  |  Começa a eliminar o mecanismo de ficheiro com o id especificado. Todos os dados para o perfil de determinado serão eliminados completamente.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Devolve as definições de perfil.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Começa a lista a operação de mecanismos.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Começa a descarregar o mecanismo de ficheiro com o id especificado. [FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="addengineasync"></a>AddEngineAsync
Inicia a adicionar um novo mecanismo de ficheiro para o perfil.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Começa a eliminar o mecanismo de ficheiro com o id especificado. Todos os dados para o perfil de determinado serão eliminados completamente.
[FileProfile::Observer](class_mip_fileprofile_observer.md) será chamado após o êxito ou falha.