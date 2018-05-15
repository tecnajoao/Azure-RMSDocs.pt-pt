# <a name="class-mipprotectionprofileobserver"></a>classe mip::ProtectionProfile::Observer 
Interface que recebe notificações relacionadas com [ProtectionProfile](class_mip_protectionprofile.md).
Esta interface por tem implementada por aplicações utilizando a SDK de proteção
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnLoadSuccess void de virtual público (const std::shared_ptr<ProtectionProfile>& perfil, const std::shared_ptr<void>& contexto)  |  Chamado quando o perfil foi carregado com êxito.
OnLoadFailure void de virtual público (const std::exception_ptr & erro, const std::shared_ptr<void>& contexto)  |  Chamado quando carregar um perfil causou um erro.
  
## <a name="members"></a>Membros
  
### <a name="onloadsuccess"></a>OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.

Parâmetros:  
* **perfil**: uma referência para o recentemente criado [ProtectionProfile](class_mip_protectionprofile.md)


* **contexto**: O mesmo contexto que foi transmitido aos [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync)


Uma aplicação pode passar qualquer tipo de contexto (por exemplo, std::promise std::function, etc.) para [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync) e esse mesmo contexto será reencaminhado como-é [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) ou [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)
  
### <a name="onloadfailure"></a>OnLoadFailure
Chamado quando carregar um perfil causou um erro.

Parâmetros:  
* **erro**: [erro](class_mip_error.md) que ocorreu durante o carregamento 


* **contexto**: O mesmo contexto que foi transmitido aos [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync)


Uma aplicação pode passar qualquer tipo de contexto (por exemplo, std::promise std::function, etc.) para [ProtectionProfile::LoadAsync](class_mip_protectionprofile.md#loadasync) e esse mesmo contexto será reencaminhado como-é [ProtectionProfile::Observer::O nLoadSuccess](class_mip_protectionprofile_observer.md#onloadsuccess) ou [ProtectionProfile::Observer::OnLoadFailure](class_mip_protectionprofile_observer.md#onloadfailure)