# <a name="class-mipuserpolicy"></a>classe mip::UserPolicy 
Representa a política associada ao conteúdo protegido.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
bool pública AccessCheck (const std::string & direita) const  |  Verifica se a política concede acesso de utilizador para a direita especificado.
pública UserPolicyType GetType()  |  Obtém o tipo de política.
std::string pública GetName()  |  Obtém o nome da política.
std::string pública GetDescription()  |  Obtém a descrição da política.
std::shared_ptr pública<TemplateDescriptor> GetTemplateDescriptor()  |  Obtém [TemplateDescriptor](#classmip_1_1_template_descriptor) para um modelo baseado em [UserPolicy](#classmip_1_1_user_policy).
std::shared_ptr pública<PolicyDescriptor> GetPolicyDescriptor()  |  Obtém [PolicyDescriptor](#classmip_1_1_policy_descriptor) para um ad hoc [UserPolicy](#classmip_1_1_user_policy).
std::string pública GetOwner()  |  Obtém endereço de e-mail do proprietário do conteúdo.
std::string pública GetIssuedTo()  |  Obtém o utilizador associado a política de proteção.
bool pública IsIssuedToOwner()  |  Obtém ou não o utilizador atual é o proprietário do conteúdo.
std::string pública GetContentId()  |  Obtém o identificador exclusivo para o/conteúdo do documento.
mip::AppDataHashMap const pública GetEncryptedAppData()  |  Obtém dados específicos da aplicação que foi encriptados.
mip::AppDataHashMap const pública GetSignedAppData()  |  Obtém os dados específicos da aplicação foi assinados.
std::chrono::time_point pública < std::chrono::system_clock > GetContentValidUntil()  |  Obtém a hora de expiração de política.
bool pública DoesUseDeprecatedAlgorithms()  |  Obtém ou não utiliza de política preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores.
bool pública IsAuditedExtractAllowed()  |  Obtém ou não política concede o direito de 'auditada extrair' de utilizador.
pública std::vector const<unsigned char> GetSerializedPolicy()  |  Serializar [UserPolicy](#classmip_1_1_user_policy) para uma licença de publicação (LP)
std::shared_ptr pública < rmscore::core::ProtectionPolicy > GetImpl()  |  Obtém interno derivado de implementação de classe de [UserPolicy](#classmip_1_1_user_policy).
  
## <a name="members"></a>Membros
  
### <a name="accesscheck"></a>AccessCheck
Verifica se a política concede acesso de utilizador para a direita especificado.
  
#### <a name="parameters"></a>Parâmetros
* Direito direito para verificar
  
#### <a name="returns"></a>Devolve
Se deve ou não política concede acesso de utilizador para especificar o direito
  
### <a name="userpolicytype"></a>UserPolicyType
Obtém o tipo de política.
  
#### <a name="returns"></a>Devolve
Tipo de política
  
### <a name="getname"></a>GetName
Obtém o nome da política.
  
#### <a name="returns"></a>Devolve
Nome da política
  
### <a name="getdescription"></a>GetDescription
Obtém a descrição da política.
  
#### <a name="returns"></a>Devolve
Descrição da política
  
### <a name="templatedescriptor"></a>TemplateDescriptor
Obtém [TemplateDescriptor](#classmip_1_1_template_descriptor) para um modelo baseado em [UserPolicy](#classmip_1_1_user_policy).
  
#### <a name="returns"></a>Devolve
[TemplateDescriptor](#classmip_1_1_template_descriptor) se [UserPolicy](#classmip_1_1_user_policy) baseado no modelo, nullptr pessoa
  
### <a name="policydescriptor"></a>Policydescriptor …
Obtém [PolicyDescriptor](#classmip_1_1_policy_descriptor) para um ad hoc [UserPolicy](#classmip_1_1_user_policy).
  
#### <a name="returns"></a>Devolve
[PolicyDescriptor](#classmip_1_1_policy_descriptor) se [UserPolicy](#classmip_1_1_user_policy) é ad hoc, nullptr pessoa
  
### <a name="getowner"></a>GetOwner
Obtém endereço de e-mail do proprietário do conteúdo.
  
#### <a name="returns"></a>Devolve
Endereço de e-mail do proprietário do conteúdo
  
### <a name="getissuedto"></a>GetIssuedTo
Obtém o utilizador associado a política de proteção.
  
#### <a name="returns"></a>Devolve
Utilizador associado à política de proteção
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Obtém ou não o utilizador atual é o proprietário do conteúdo.
  
#### <a name="returns"></a>Devolve
Se o utilizador atual é o proprietário do conteúdo
  
### <a name="getcontentid"></a>GetContentId
Obtém o identificador exclusivo para o/conteúdo do documento.
  
#### <a name="returns"></a>Devolve
Identificador exclusivo de conteúdo
  
### <a name="mipappdatahashmap"></a>Mip::AppDataHashMap
Obtém dados específicos da aplicação que foi encriptados.
A [UserPolicy](#classmip_1_1_user_policy) pode conter um dicionário de dados específicos da aplicação que foi encriptados pelo serviço RMS. Estes dados encriptados são independentes dos dados assinados acessíveis através de [UserPolicy::GetSignedAppData](#classmip_1_1_user_policy_1a1c8a284d50adcac1a0a09316afa1d43e)
  
### <a name="mipappdatahashmap"></a>Mip::AppDataHashMap
Obtém os dados específicos da aplicação foi assinados.
A [UserPolicy](#classmip_1_1_user_policy) pode conter um dicionário de dados específico da aplicação foi assinados pelo serviço de RMS. Estes dados assinados são independentes dos dados encriptados acessíveis através de [UserPolicy::GetEncryptedAppData](#classmip_1_1_user_policy_1a610fbc799284ab0ce4354c0611ece0e8)
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Obtém a hora de expiração de política.
  
#### <a name="returns"></a>Devolve
Hora de expiração de política
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Obtém ou não utiliza de política preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores.
  
#### <a name="returns"></a>Devolve
Se pretende ou não utiliza a política preterido algoritmos criptográficos
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Obtém ou não política concede o direito de 'auditada extrair' de utilizador.
  
#### <a name="returns"></a>Devolve
Se pretende ou não política concede o direito de 'auditada extrair' de utilizador
  
### <a name="getserializedpolicy"></a>GetSerializedPolicy
Serializar [UserPolicy](#classmip_1_1_user_policy) para uma licença de publicação (LP)
  
#### <a name="returns"></a>Devolve
Serializado [UserPolicy](#classmip_1_1_user_policy)
  
### <a name="getimpl"></a>GetImpl
Obtém interno derivado de implementação de classe de [UserPolicy](#classmip_1_1_user_policy).
  
#### <a name="returns"></a>Devolve
Derivado de implementação de classe de [UserPolicy](#classmip_1_1_user_policy) interna apenas