# <a name="class-mipprotectionprofile"></a>classe mip::ProtectionProfile 
[ProtectionProfile](class_mip_protectionprofile.md) é a classe de raiz para a execução de operações de proteção.
Uma aplicação tem de criar uma [ProtectionProfile](class_mip_protectionprofile.md) antes de realizar quaisquer operações de proteção
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Obtém as definições utilizadas pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo de seu ciclo de vida.
ListEnginesAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a lista a operação de mecanismos.
público Std:: vector Std:: < String > ListEngines()  |  Mecanismos de lista.
AddEngineAsync void pública (const ProtectionEngine::Settings e definições, const std::shared_ptr<void>& contexto)  |  Inicia a adicionar um novo mecanismo de proteção para o perfil.
público std::shared_ptr<ProtectionEngine> AddEngine (const ProtectionEngine::Settings e definições)  |  Adicione um novo mecanismo de proteção para o perfil.
DeleteEngineAsync void pública (Std:: String const & engineId, const std::shared_ptr<void>& contexto)  |  Começa a eliminar o mecanismo de proteção com o id especificado. Todos os dados para o mecanismo de determinado serão eliminados completamente.
 DeleteEngine void pública (const Std:: String & engineId)  |  Elimine o mecanismo de proteção com o id especificado. Todos os dados para o mecanismo de determinado serão eliminados completamente.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obtém as definições utilizadas pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo de seu ciclo de vida.

  
**Devolve**: [configurações](class_mip_protectionprofile_settings.md) utilizado pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo de seu ciclo de vida
  
### <a name="listenginesasync"></a>ListEnginesAsync
Começa a lista a operação de mecanismos.

Parâmetros:  
* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para observadores


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="listengines"></a>ListEngines
Mecanismos de lista.

  
**Devolve**: em cache os ids de motor
  
### <a name="addengineasync"></a>AddEngineAsync
Inicia a adicionar um novo mecanismo de proteção para o perfil.

Parâmetros:  
* **as definições**: a [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) objeto que especifica os parâmetros do mecanismo. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para observadores


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="protectionengine"></a>ProtectionEngine
Adicione um novo mecanismo de proteção para o perfil.

Parâmetros:  
* **as definições**: a [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) objeto que especifica os parâmetros do mecanismo.



  
**Devolve**: recentemente criado [ProtectionEngine](class_mip_protectionengine.md)
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Começa a eliminar o mecanismo de proteção com o id especificado. Todos os dados para o mecanismo de determinado serão eliminados completamente.

Parâmetros:  
* **ID**: o id exclusivo do motor. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para observadores


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengine"></a>DeleteEngine
Elimine o mecanismo de proteção com o id especificado. Todos os dados para o mecanismo de determinado serão eliminados completamente.

Parâmetros:  
* **ID**: o id exclusivo do motor.

