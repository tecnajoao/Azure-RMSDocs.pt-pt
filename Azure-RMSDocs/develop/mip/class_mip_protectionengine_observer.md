# <a name="class-mipprotectionengineobserver"></a>classe mip::ProtectionEngine::Observer 
Interface que recebe notificações relacionadas com a [ProtectionEngine](class_mip_protectionengine.md).
Essa interface por tem implementada por aplicativos que usam a proteção de SDK
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnGetTemplatesSuccess de void virtual público (std::shared_ptr const < < Std:: String >> Std:: vector & templateIds, const std::shared_ptr<void>& contexto)  |  Chamado quando modelos foram obtidos com êxito.
OnGetTemplatesFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a obter modelos gerado um erro.
  
## <a name="members"></a>Membros
  
### <a name="ongettemplatessuccess"></a>OnGetTemplatesSuccess
Chamado quando modelos foram obtidos com êxito.

Parâmetros:  
* **templateIds**: obter uma referência à lista de modelos 


* **contexto**: O mesmo contexto transmitido a [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) e o mesmo contexto será encaminhado como-é [ProtectionEngine::Observer::O nGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) ou [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)
  
### <a name="ongettemplatesfailure"></a>OnGetTemplatesFailure
Chamado quando a obter modelos gerado um erro.

Parâmetros:  
* **erro**: [erro](class_mip_error.md) que ocorreu ao obter modelos 


* **contexto**: O mesmo contexto transmitido a [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionEngine::GetTemplatesAsync](class_mip_protectionengine.md#gettemplatesasync) e o mesmo contexto será encaminhado como-é [ProtectionEngine::Observer::O nGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongettemplatessuccess) ou [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongettemplatesfailure)