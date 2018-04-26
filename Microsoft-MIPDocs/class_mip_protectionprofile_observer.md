# <a name="class-mipprotectionprofileobserver"></a>classe mip::ProtectionProfile::Observer 
Interface que recebe notificações relacionadas com [ProtectionProfile](#classmip_1_1_protection_profile).
Esta interface por tem implementada por aplicações utilizando a SDK de proteção
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública inline virtual void OnLoadSuccessProtectionProfile > & perfil, const std::shared_ptr < void > & contexto) | Chamado quando o perfil foi carregado com êxito.
pública inline virtual void OnLoadFailure | Chamado quando carregar um perfil causou um erro.
## <a name="members"></a>Membros
### <a name="onloadsuccess"></a>OnLoadSuccess
Chamado quando o perfil foi carregado com êxito.
#### <a name="parameters"></a>Parâmetros
* perfil uma referência para o recentemente criado [ProtectionProfile](#classmip_1_1_protection_profile)
* contexto o mesmo contexto que foi transmitido aos [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) uma aplicação pode passar qualquer tipo de contexto (por exemplo, std::promise std::function, etc.) para [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) e esse mesmo contexto será reencaminhado como-é [ProtectionProfile::Observer::OnLoadSuccess](#classmip_1_1_protection_profile_1_1_observer_1a31e73965ffb0bd152b3954b013faa773) ou [ProtectionProfile::Observer::OnLoadFailure](#classmip_1_1_protection_profile_1_1_observer_1acdad73bb6a2dcc93295e0e16e422f291)
### <a name="onloadfailure"></a>OnLoadFailure
Chamado quando carregar um perfil causou um erro.
#### <a name="parameters"></a>Parâmetros
* erro [erro](#classmip_1_1_error) que ocorreu durante o carregamento 
* contexto o mesmo contexto que foi transmitido aos [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) uma aplicação pode passar qualquer tipo de contexto (por exemplo, std::promise std::function, etc.) para [ProtectionProfile::LoadAsync](#classmip_1_1_protection_profile_1aeb141706dc10935931841fdb82d11031) e esse mesmo contexto será reencaminhado como-é [ProtectionProfile::Observer::OnLoadSuccess](#classmip_1_1_protection_profile_1_1_observer_1a31e73965ffb0bd152b3954b013faa773) ou [ProtectionProfile::Observer::OnLoadFailure](#classmip_1_1_protection_profile_1_1_observer_1acdad73bb6a2dcc93295e0e16e422f291)