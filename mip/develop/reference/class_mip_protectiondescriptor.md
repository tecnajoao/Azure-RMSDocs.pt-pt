# <a name="class-mipprotectiondescriptor"></a>classe mip::ProtectionDescriptor 
Representa uma política ad-hoc associada com conteúdo protegido.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público GetProtectionType() de ProtectionType const  |  Obtém o tipo de proteção, se foi gerado a partir de modelo do sdk de proteção ou não.
 público Std:: String GetOwner() const  |  Obtém o proprietário para a proteção.
 público Std:: String GetName() const  |  Obtém o nome de política.
 público Std:: String GetDescription() const  |  Obtém a descrição da política.
 público Std:: String GetTemplateId() const  |  Obtém o id do modelo de proteção.
 público Std:: String GetLabelId() const  |  Obtém o id de etiqueta.
público Std:: vector<UserRights> GetUserRights() const  |  Obtém a coleção de mapeamentos de direitos de usuários.
público Std:: vector<UserRoles> GetUserRoles() const  |  Obtém a coleção de mapeamentos de funções de utilizadores.
std::chrono::time_point público < std::chrono::system_clock > GetContentValidUntil() const  |  Obtém a hora de expiração de política.
 bool pública DoesAllowOfflineAccess() const  |  Obtém se ou não permite a política de acesso ao conteúdo offline.
 público Std:: String GetReferrer() const  |  Obtém o endereço de referência de política.
std::map público < Std:: String, Std:: String > GetEncryptedAppData() const  |  Obtém dados específicos da aplicação que foi encriptados.
std::map público < Std:: String, Std:: String > GetSignedAppData() const  |  Obtém os dados específicos da aplicação que foi assinados.
  
## <a name="members"></a>Membros
  
### <a name="protectiontype"></a>ProtectionType
Obtém o tipo de proteção, se foi gerado a partir de modelo do sdk de proteção ou não.

  
**Devolve**: tipo de proteção
  
### <a name="getowner"></a>GetOwner
Obtém o proprietário para a proteção.

  
**Devolve**: proprietário de proteção
  
### <a name="getname"></a>GetName
Obtém o nome de política.

  
**Devolve**: nome da política
  
### <a name="getdescription"></a>GetDescription
Obtém a descrição da política.

  
**Devolve**: descrição de política
  
### <a name="gettemplateid"></a>GetTemplateId
Obtém o id do modelo de proteção.

  
**Devolve**: id do modelo
  
### <a name="getlabelid"></a>GetLabelId
Obtém o id de etiqueta.

  
**Devolve**: [etiqueta](class_mip_label.md) esta propriedade só irá ser preenchida no ProtectionDescriptors para preexistente de id de conteúdo protegido. ou seja, é um campo preenchido pelo servidor neste momento é consumido conteúdo protegido.
  
### <a name="userrights"></a>UserRights
Obtém a coleção de mapeamentos de direitos de usuários.

  
**Devolve**: a coleção de mapeamentos de direitos de usuários o valor da [UserRights](class_mip_userrights.md) propriedade estará vazia se o utilizador atual não tem acesso às informações de direitos de utilizador (ou seja, não é o proprietário e não tem o Direito VIEWRIGHTSDATA).
  
### <a name="userroles"></a>Funções de utilizador
Obtém a coleção de mapeamentos de funções de utilizadores.

  
**Devolve**: coleção de mapeamentos de funções de utilizadores
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Obtém a hora de expiração de política.

  
**Devolve**: hora de expiração de política
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Obtém se ou não permite a política de acesso ao conteúdo offline.

  
**Devolve**: se é ou não política permite o acesso offline de conteúdo (predefinição = true)
  
### <a name="getreferrer"></a>GetReferrer
Obtém o endereço de referência de política.

  
**Devolve**: endereço de referência de política o Referenciador for um URI que pode ser apresentado ao utilizador após a falha na aquisição de política que contém informações sobre como esse utilizador pode obter a permissão para aceder ao conteúdo.
  
### <a name="getencryptedappdata"></a>GetEncryptedAppData
Obtém dados específicos da aplicação que foi encriptados.

  
**Devolve**: A de dados de aplicação específicos [ProtectionHandler](class_mip_protectionhandler.md) pode conter um dicionário de dados específicos da aplicação que foi encriptados pelo serviço de proteção. Estes dados encriptados são independentes dos dados assinados podem ser acedidos através de [ProtectionDescriptor::GetSignedAppData](class_mip_protectiondescriptor.md#getappsigneddata)
  
### <a name="getsignedappdata"></a>GetSignedAppData
Obtém os dados específicos da aplicação que foi assinados.

  
**Devolve**: A de dados de aplicação específicos [ProtectionHandler](class_mip_protectionhandler.md) pode conter um dicionário de dados específicos da aplicação que foi assinados pelo serviço de proteção. Estes dados assinados são independentes dos dados encriptados podem ser acedidos através de [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata)