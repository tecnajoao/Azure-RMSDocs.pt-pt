# <a name="class-mipprofile"></a>classe mip::Profile 
[Perfil](class_mip_profile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar. Um aplicativo típico irá apenas precisa de um [perfil](class_mip_profile.md) , mas ele pode criar vários perfis, se for necessário.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Obtenha as configurações definidas no perfil.
ListEnginesAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a lista a operação de mecanismos.
UnloadEngineAsync void pública (Std:: String const & id, const std::shared_ptr<void>& contexto)  |  Começa a descarregar o motor de política com o id especificado.
AddEngineAsync void pública (const PolicyEngine::Settings e definições, const std::shared_ptr<void>& contexto)  |  Inicia a adicionar um novo mecanismo de política para o perfil.
DeleteEngineAsync void pública (Std:: String const & id, const std::shared_ptr<void>& contexto)  |  Começa a eliminar o motor de política com o id especificado. Todos os dados para o perfil de determinado serão eliminados completamente.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obtenha as configurações definidas no perfil.

  
**Devolve**: configurar as definições no perfil.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Começa a lista a operação de mecanismos.

Parâmetros:  
* **contexto**: um parâmetro que será passado para as funções de observador. 


[Profile::Observer](class_mip_profile_observer.md) será chamado após o êxito ou falha.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Começa a descarregar o motor de política com o id especificado.

Parâmetros:  
* **ID**: o id exclusivo do motor. 


* **contexto**: um parâmetro que será passado para as funções de observador. 


[Profile::Observer](class_mip_profile_observer.md) será chamado após o êxito ou falha.
  
### <a name="addengineasync"></a>AddEngineAsync
Inicia a adicionar um novo mecanismo de política para o perfil.

Parâmetros:  
* **as definições**: a [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) objeto que especifica os parâmetros de mecanismos. 


* **contexto**: um parâmetro que será passado para as funções de observador. 


[Profile::Observer](class_mip_profile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Começa a eliminar o motor de política com o id especificado. Todos os dados para o perfil de determinado serão eliminados completamente.

Parâmetros:  
* **ID**: o id exclusivo do motor. 


* **contexto**: um parâmetro que será passado para as funções de observador. 


[Profile::Observer](class_mip_profile_observer.md) será chamado após o êxito ou falha.