# <a name="class-mipprotectionhandlerobserver"></a>classe mip::ProtectionHandler::Observer 
Interface que recebe notificações relacionadas com a [ProtectionHandler](class_mip_protectionhandler.md).
Essa interface por tem implementada por aplicativos que usam a proteção de SDK
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnCreateProtectionHandlerSuccess de void virtual público (const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& contexto)  |  Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) foi criado com êxito.
OnCreateProtectionHandlerError de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) falha na criação.
  
## <a name="members"></a>Membros
  
### <a name="oncreateprotectionhandlersuccess"></a>OnCreateProtectionHandlerSuccess
Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) foi criado com êxito.

Parâmetros:  
* **protectionHandler**: O recentemente criado [ProtectionHandler](class_mip_protectionhandler.md)


* **contexto**: O mesmo contexto de que foi passado para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) ou [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) ou [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync), e o mesmo contexto será encaminhado como-é ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess ou ProtectionEngine::Observer::O nCreateProtectionHandlerFailure
  
### <a name="oncreateprotectionhandlererror"></a>OnCreateProtectionHandlerError
Chamado quando [ProtectionHandler](class_mip_protectionhandler.md) falha na criação.

Parâmetros:  
* **erro**: [erro](class_mip_error.md) que ocorreu durante a criação 


* **contexto**: O mesmo contexto de que foi passado para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) ou [ProtectionEngine::CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionEngine::CreateProtectionHandlerFromDescriptorAsync](class_mip_protectionengine.md#createprotectionhandlerfromdescriptorasync) ou [ProtectionEngine:: CreateProtectionHandlerFromPublishingLicenseAsync](class_mip_protectionengine.md#createprotectionhandlerfrompublishinglicenseasync), e o mesmo contexto será encaminhado como-é ProtectionEngine::Observer::OnCreateProtectionHandlerSuccess ou ProtectionEngine::Observer::O nCreateProtectionHandlerFailure