# <a name="class-mipuserpolicy"></a>classe mip::UserPolicy 
Representa a política associada ao conteúdo protegido.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 bool pública AccessCheck (const std::string & direita) const  |  Verifica se a política concede acesso de utilizador para a direita especificado.
 pública UserPolicyType GetType()  |  Obtém o tipo de política.
 std::string pública GetName()  |  Obtém o nome da política.
 std::string pública GetDescription()  |  Obtém a descrição da política.
std::shared_ptr pública<TemplateDescriptor> GetTemplateDescriptor()  |  Obtém [TemplateDescriptor](class_mip_templatedescriptor.md) para um modelo baseado em [UserPolicy](class_mip_userpolicy.md).
std::shared_ptr pública<PolicyDescriptor> GetPolicyDescriptor()  |  Obtém [PolicyDescriptor](class_mip_policydescriptor.md) para um ad hoc [UserPolicy](class_mip_userpolicy.md).
 std::string pública GetOwner()  |  Obtém endereço de e-mail do proprietário do conteúdo.
 std::string pública GetIssuedTo()  |  Obtém o utilizador associado a política de proteção.
 bool pública IsIssuedToOwner()  |  Obtém ou não o utilizador atual é o proprietário do conteúdo.
 std::string pública GetContentId()  |  Obtém o identificador exclusivo para o/conteúdo do documento.
 mip::AppDataHashMap const pública GetEncryptedAppData()  |  Obtém dados específicos da aplicação que foi encriptados.
 mip::AppDataHashMap const pública GetSignedAppData()  |  Obtém os dados específicos da aplicação foi assinados.
std::chrono::time_point pública < std::chrono::system_clock > GetContentValidUntil()  |  Obtém a hora de expiração de política.
 bool pública DoesUseDeprecatedAlgorithms()  |  Obtém ou não utiliza de política preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores.
 bool pública IsAuditedExtractAllowed()  |  Obtém ou não política concede o direito de 'auditada extrair' de utilizador.
pública std::vector const<unsigned char> GetSerializedPolicy()  |  Serializar [UserPolicy](class_mip_userpolicy.md) para uma licença de publicação (LP)
std::shared_ptr pública < rmscore::core::ProtectionPolicy > GetImpl()  |  Obtém interno derivado de implementação de classe de [UserPolicy](class_mip_userpolicy.md).
  
## <a name="members"></a>Membros
  
### <a name="accesscheck"></a>AccessCheck
Verifica se a política concede acesso de utilizador para a direita especificado.

Parâmetros:  
* **direito**: direito para verificar



  
**Devolve**: se deve ou não política concede acesso de utilizador à direita especificado
  
### <a name="userpolicytype"></a>UserPolicyType
Obtém o tipo de política.

  
**Devolve**: tipo de política
  
### <a name="getname"></a>GetName
Obtém o nome da política.

  
**Devolve**: nome da política
  
### <a name="getdescription"></a>GetDescription
Obtém a descrição da política.

  
**Devolve**: Descrição da política
  
### <a name="templatedescriptor"></a>TemplateDescriptor
Obtém [TemplateDescriptor](class_mip_templatedescriptor.md) para um modelo baseado em [UserPolicy](class_mip_userpolicy.md).

  
**Devolve**: [TemplateDescriptor](class_mip_templatedescriptor.md) se [UserPolicy](class_mip_userpolicy.md) baseado no modelo, nullptr pessoa
  
### <a name="policydescriptor"></a>Policydescriptor …
Obtém [PolicyDescriptor](class_mip_policydescriptor.md) para um ad hoc [UserPolicy](class_mip_userpolicy.md).

  
**Devolve**: [PolicyDescriptor](class_mip_policydescriptor.md) se [UserPolicy](class_mip_userpolicy.md) é ad hoc, nullptr pessoa
  
### <a name="getowner"></a>GetOwner
Obtém endereço de e-mail do proprietário do conteúdo.

  
**Devolve**: endereço de E-Mail do proprietário do conteúdo
  
### <a name="getissuedto"></a>GetIssuedTo
Obtém o utilizador associado a política de proteção.

  
**Devolve**: utilizador associado à política de proteção
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Obtém ou não o utilizador atual é o proprietário do conteúdo.

  
**Devolve**: se o utilizador atual é o proprietário do conteúdo
  
### <a name="getcontentid"></a>GetContentId
Obtém o identificador exclusivo para o/conteúdo do documento.

  
**Devolve**: Identificador exclusivo de conteúdo
  
### <a name="mipappdatahashmap"></a>Mip::AppDataHashMap
Obtém dados específicos da aplicação que foi encriptados.
A [UserPolicy](class_mip_userpolicy.md) pode conter um dicionário de dados específicos da aplicação que foi encriptados pelo serviço RMS. Estes dados encriptados são independentes dos dados assinados acessíveis através de [UserPolicy::GetSignedAppData](class_mip_userpolicy.md#getsignedappdata)
  
### <a name="mipappdatahashmap"></a>Mip::AppDataHashMap
Obtém os dados específicos da aplicação foi assinados.
A [UserPolicy](class_mip_userpolicy.md) pode conter um dicionário de dados específico da aplicação foi assinados pelo serviço de RMS. Estes dados assinados são independentes dos dados encriptados acessíveis através de [UserPolicy::GetEncryptedAppData](class_mip_userpolicy.md#getencryptedappdata)
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Obtém a hora de expiração de política.

  
**Devolve**: hora de expiração de política
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Obtém ou não utiliza de política preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores.

  
**Devolve**: ou não utiliza de política preterido algoritmos criptográficos
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Obtém ou não política concede o direito de 'auditada extrair' de utilizador.

  
**Devolve**: ou não política concede o direito de 'auditada extrair' de utilizador
  
### <a name="getserializedpolicy"></a>GetSerializedPolicy
Serializar [UserPolicy](class_mip_userpolicy.md) para uma licença de publicação (LP)

  
**Devolve**: serializado [UserPolicy](class_mip_userpolicy.md)
  
### <a name="getimpl"></a>GetImpl
Obtém interno derivado de implementação de classe de [UserPolicy](class_mip_userpolicy.md).

  
**Devolve**: derivado de implementação de classe de [UserPolicy](class_mip_userpolicy.md) interna apenas