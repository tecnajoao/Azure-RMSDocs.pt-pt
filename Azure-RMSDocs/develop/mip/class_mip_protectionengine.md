# <a name="class-mipprotectionengine"></a>classe mip::ProtectionEngine 
Executa ações relacionadas com a proteção relacionados com uma identidade específica.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Obtém as definições de motor.
GetTemplatesAsync void pública (std::shared_ptr const < ProtectionEngine::Observer > & observador, const std::shared_ptr<void>& contexto)  |  Obter coleção de modelos disponíveis para um utilizador.
CreateProtectionHandlerFromDescriptorAsync void pública (const std::shared_ptr<ProtectionDescriptor>& descritor, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr < ProtectionHandler::Observer > e observador, Const std::shared_ptr<void>& contexto)  |  Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.
CreateProtectionHandlerFromPublishingLicenseAsync void pública (const Std:: vector < uint8_t > & serializedPublishingLicense, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr < ProtectionHandler::Observer > & observador, const std::shared_ptr<void>& contexto)  |  Cria um manipulador de proteção a partir do respetivo formato serializado.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obtém as definições de motor.

  
**Devolve**: o motor de definições
  
### <a name="gettemplatesasync"></a>GetTemplatesAsync
Obter coleção de modelos disponíveis para um utilizador.

Parâmetros:  
* **observador**: implementar uma classe a [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interface 


* **contexto**: este mesmo contexto será encaminhado ao [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) ou [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)


  
### <a name="createprotectionhandlerfromdescriptorasync"></a>CreateProtectionHandlerFromDescriptorAsync
Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.

Parâmetros:  
* **descritor**: A [ProtectionDescriptor](class_mip_protectiondescriptor.md) que descreve a configuração da proteção 


* **Opções de**: opções de criação 


* **observador**: implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **contexto**: este mesmo contexto será encaminhado ao [ProtectionHandler::Observer::OnCreateProtectionHandlerSuccess](class_mip_protectionhandler_observer.md#oncreateprotectionhandlersuccess) ou ProtectionHandler::Observer::OnCreateProtectionHandlerFailure


  
### <a name="createprotectionhandlerfrompublishinglicenseasync"></a>CreateProtectionHandlerFromPublishingLicenseAsync
Cria um manipulador de proteção a partir do respetivo formato serializado.

Parâmetros:  
* **serializedPublishingLicense**: serializada de uma licença de publicação 


* **Opções de**: opções de criação 


* **observador**: implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **contexto**: este mesmo contexto será encaminhado ao [ProtectionHandler::Observer::OnCreateProtectionHandlerSuccess](class_mip_protectionhandler_observer.md#oncreateprotectionhandlersuccess) ou ProtectionHandler::Observer::OnCreateProtectionHandlerFailure

