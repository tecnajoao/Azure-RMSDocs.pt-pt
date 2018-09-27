# <a name="class-mipprotectionengineobserver"></a>classe mip::ProtectionEngine::Observer 
Interface que recebe notificações relacionadas com a [ProtectionEngine](class_mip_protectionengine.md).
Essa interface por tem implementada por aplicativos que usam a proteção de SDK
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnGetTemplatesSuccess de void virtual público (std::shared_ptr const < < Std:: String >> Std:: vector & templateIds, const std::shared_ptr<void>& contexto)  |  Chamado quando modelos foram obtidos com êxito.
OnGetTemplatesFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a obter modelos gerado um erro.
OnGetRightsForLabelIdSuccess de void virtual público (std::shared_ptr const < < Std:: String >> Std:: vector & direitos, const std::shared_ptr<void>& contexto)  |  Chamado quando direitos foram obtidos com êxito.
OnGetRightsForLabelIdFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a obter direitos para um labelId para o utilizador.
OnGetGrantingLabelIdsSuccess de void virtual público (std::shared_ptr const < < Std:: String >> Std:: vector & lableIds, const std::shared_ptr<void>& contexto)  |  Chamado quando labelIds foram obtidos com êxito.
OnGetGrantingLabelIdsFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando labelIds para o utilizador a obter.
  
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
  
### <a name="ongetrightsforlabelidsuccess"></a>OnGetRightsForLabelIdSuccess
Chamado quando direitos foram obtidos com êxito.

Parâmetros:  
* **direitos**: obter uma referência para a lista de direitos 


* **contexto**: O mesmo contexto transmitido a [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) e o mesmo contexto será encaminhado como-é [ProtectionEngine::Observer :: OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) ou [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)
  
### <a name="ongetrightsforlabelidfailure"></a>OnGetRightsForLabelIdFailure
Chamado quando a obter direitos para um labelId para o utilizador.

Parâmetros:  
* **erro**: [erro](class_mip_error.md) que ocorreu ao obter direitos 


* **contexto**: O mesmo contexto transmitido a [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionEngine::GetRightsForLabelIdAsync](class_mip_protectionengine.md#getrightsforlabelidasync) e o mesmo contexto será encaminhado como-é [ProtectionEngine::Observer :: OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) ou [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)
  
### <a name="ongetgrantinglabelidssuccess"></a>OnGetGrantingLabelIdsSuccess
Chamado quando labelIds foram obtidos com êxito.

Parâmetros:  
* **lableIds**: obter uma referência à lista de lableIds 


* **contexto**: O mesmo contexto transmitido a [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) e o mesmo contexto será encaminhado como-é [ProtectionEngine::Observer :: OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) ou [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure)
  
### <a name="ongetgrantinglabelidsfailure"></a>OnGetGrantingLabelIdsFailure
Chamado quando labelIds para o utilizador a obter.

Parâmetros:  
* **erro**: [erro](class_mip_error.md) que ocorreu ao obter labelIds 


* **contexto**: O mesmo contexto transmitido a [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync)


Um aplicativo pode passar qualquer tipo de contexto (por exemplo, std::promise, std::function, etc.) para [ProtectionEngine::GetGrantingLabelIdsAsync](class_mip_protectionengine.md#getgrantinglabelidsasync) e o mesmo contexto será encaminhado como-é [ProtectionEngine::Observer :: OnGetGrantingLabelIdsSuccess](class_mip_protectionengine_observer.md#ongetgrantinglabelidssuccess) ou [ProtectionEngine::Observer::OnGetGrantingLabelIdsFailure](class_mip_protectionengine_observer.md#ongetgrantinglabelidsfailure)