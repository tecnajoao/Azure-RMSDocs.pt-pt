# <a name="class-mipuserpolicy"></a>classe mip::UserPolicy 
Representa a política associada a conteúdo protegido.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 bool pública AccessCheck (const Std:: String & direita) const  |  Verifica se a política concede acesso de utilizador especificado diretamente.
 público UserPolicyType GetType()  |  Obtém o tipo de política.
 público Std:: String GetName()  |  Obtém o nome de política.
 público Std:: String GetDescription()  |  Obtém a descrição da política.
público std::shared_ptr<TemplateDescriptor> GetTemplateDescriptor()  |  Obtém [TemplateDescriptor](class_mip_templatedescriptor.md) para um modelo baseado no [UserPolicy](class_mip_userpolicy.md).
público std::shared_ptr<PolicyDescriptor> GetPolicyDescriptor()  |  Obtém [PolicyDescriptor](class_mip_policydescriptor.md) para um ad hoc [UserPolicy](class_mip_userpolicy.md).
 público Std:: String GetOwner()  |  Obtém endereço de e-mail do proprietário do conteúdo.
 público Std:: String GetIssuedTo()  |  Obtém o utilizador associado a política de proteção.
 bool pública IsIssuedToOwner()  |  Obtém o se o utilizador atual é o proprietário do conteúdo ou não.
 público Std:: String GetContentId()  |  Obtém o identificador exclusivo para o/conteúdo do documento.
 público mip::AppDataHashMap const GetEncryptedAppData()  |  Obtém dados específicos da aplicação que foi encriptados.
 público mip::AppDataHashMap const GetSignedAppData()  |  Obtém os dados específicos da aplicação que foi assinados.
std::chrono::time_point público < std::chrono::system_clock > GetContentValidUntil()  |  Obtém a hora de expiração de política.
 bool pública DoesUseDeprecatedAlgorithms()  |  Obtém se ou não utiliza de política preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores.
 bool pública IsAuditedExtractAllowed()  |  Obtém independentemente da política concede o direito de usuário 'auditado extrair'.
público const Std:: vector<unsigned char> GetSerializedPolicy()  |  Serializar [UserPolicy](class_mip_userpolicy.md) numa licença de publicação (PL)
std::shared_ptr público < rmscore::core::ProtectionPolicy > GetImpl()  |  Obtém interno derivado de implementação da classe [UserPolicy](class_mip_userpolicy.md).
  
## <a name="members"></a>Membros
  
### <a name="accesscheck"></a>AccessCheck
Verifica se a política concede acesso de utilizador especificado diretamente.

Parâmetros:  
* **certo**: direito para verificar



  
**Devolve**: se deve ou não política concede acesso de utilizador para especificado à direita
  
### <a name="userpolicytype"></a>UserPolicyType
Obtém o tipo de política.

  
**Devolve**: tipo de política
  
### <a name="getname"></a>GetName
Obtém o nome de política.

  
**Devolve**: nome da política
  
### <a name="getdescription"></a>GetDescription
Obtém a descrição da política.

  
**Devolve**: descrição de política
  
### <a name="templatedescriptor"></a>TemplateDescriptor
Obtém [TemplateDescriptor](class_mip_templatedescriptor.md) para um modelo baseado no [UserPolicy](class_mip_userpolicy.md).

  
**Devolve**: [TemplateDescriptor](class_mip_templatedescriptor.md) se [UserPolicy](class_mip_userpolicy.md) é baseado em modelo, nullptr outra
  
### <a name="policydescriptor"></a>PolicyDescriptor
Obtém [PolicyDescriptor](class_mip_policydescriptor.md) para um ad hoc [UserPolicy](class_mip_userpolicy.md).

  
**Devolve**: [PolicyDescriptor](class_mip_policydescriptor.md) se [UserPolicy](class_mip_userpolicy.md) é ad hoc, nullptr outra
  
### <a name="getowner"></a>GetOwner
Obtém endereço de e-mail do proprietário do conteúdo.

  
**Devolve**: endereço de E-Mail do proprietário do conteúdo
  
### <a name="getissuedto"></a>GetIssuedTo
Obtém o utilizador associado a política de proteção.

  
**Devolve**: utilizador associado à política de proteção
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Obtém o se o utilizador atual é o proprietário do conteúdo ou não.

  
**Devolve**: se o utilizador atual é o proprietário do conteúdo
  
### <a name="getcontentid"></a>GetContentId
Obtém o identificador exclusivo para o/conteúdo do documento.

  
**Devolve**: Identificador exclusivo de conteúdo
  
### <a name="mipappdatahashmap"></a>Mip::AppDataHashMap
Obtém dados específicos da aplicação que foi encriptados.
R [UserPolicy](class_mip_userpolicy.md) pode conter um dicionário de dados específicos da aplicação que foi encriptados pelo serviço de RMS. Estes dados encriptados são independentes dos dados assinados podem ser acedidos através de [UserPolicy::GetSignedAppData](class_mip_userpolicy.md#getsignedappdata)
  
### <a name="mipappdatahashmap"></a>Mip::AppDataHashMap
Obtém os dados específicos da aplicação que foi assinados.
R [UserPolicy](class_mip_userpolicy.md) pode conter um dicionário de dados específicos da aplicação que foi assinados pelo serviço de RMS. Estes dados assinados são independentes dos dados encriptados podem ser acedidos através de [UserPolicy::GetEncryptedAppData](class_mip_userpolicy.md#getencryptedappdata)
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Obtém a hora de expiração de política.

  
**Devolve**: hora de expiração de política
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Obtém se ou não utiliza de política preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores.

  
**Devolve**: se é ou não política utiliza o preterido algoritmos criptográficos
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Obtém independentemente da política concede o direito de usuário 'auditado extrair'.

  
**Devolve**: se é ou não política concede o direito de usuário "auditado extract"
  
### <a name="getserializedpolicy"></a>GetSerializedPolicy
Serializar [UserPolicy](class_mip_userpolicy.md) numa licença de publicação (PL)

  
**Devolve**: serializado [UserPolicy](class_mip_userpolicy.md)
  
### <a name="getimpl"></a>GetImpl
Obtém interno derivado de implementação da classe [UserPolicy](class_mip_userpolicy.md).

  
**Devolve**: derivado de implementação da classe [UserPolicy](class_mip_userpolicy.md) interno apenas