# <a name="class-mippolicydescriptor"></a>classe mip::PolicyDescriptor 
Representa uma política ad-hoc associada com conteúdo protegido.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetName()  |  Obtém o nome de política.
 SetName void pública (const Std:: String & valor)  |  Nome da política de conjuntos.
 público const Std:: String & GetDescription()  |  Obtém a descrição da política.
 SetDescription void pública (const Std:: String & valor)  |  Define a descrição da política.
público const Std:: vector<UserRights>& GetUserRightsList() const  |  Obtém a coleção de mapeamentos de direitos de usuários.
público const Std:: vector < mip::UserRoles > & GetUserRolesList()  |  Obtém a coleção de mapeamentos de funções de utilizadores.
std::chrono::time_point const público < std::chrono::system_clock > & GetContentValidUntil()  |  Obtém a hora de expiração de política.
SetContentValidUntil void pública (const std::chrono::time_point < std::chrono::system_clock > & valor)  |  Define a hora de expiração de política.
 bool pública DoesAllowOfflineAccess()  |  Obtém se ou não permite a política de acesso ao conteúdo offline.
 SetAllowOfflineAccess void pública (valor bool)  |  Conjuntos de diretiva permite a offline ou não acesso ao conteúdo.
 público const Std:: String & GetReferrer() const  |  Obtém o endereço de referência de política.
 SetReferrer void pública (const Std:: String & uri)  |  Define o endereço de referência de política.
 público AppDataHashMap const & GetEncryptedAppData()  |  Obtém dados específicos da aplicação que foi encriptados.
 SetEncryptedAppData void pública (const AppDataHashMap & valor)  |  Conjuntos de dados de aplicação específicos que devem ser encriptados.
 público AppDataHashMap const & GetSignedAppData()  |  Obtém os dados específicos da aplicação que foi assinados.
 SetSignedAppData void pública (const AppDataHashMap & valor)  |  Conjuntos de dados específicos da aplicação que devem ser assinados.
  
## <a name="members"></a>Membros
  
### <a name="getname"></a>GetName
Obtém o nome de política.

  
**Devolve**: nome da política
  
### <a name="setname"></a>SetName
Nome da política de conjuntos.

Parâmetros:  
* **valor**: nome da política


  
### <a name="getdescription"></a>GetDescription
Obtém a descrição da política.

  
**Devolve**: descrição de política
  
### <a name="setdescription"></a>SetDescription
Define a descrição da política.

Parâmetros:  
* **valor**: descrição de política


  
### <a name="userrights"></a>UserRights
Obtém a coleção de mapeamentos de direitos de usuários.

  
**Devolve**: coleção de mapeamentos de direitos de usuários o valor da propriedade UserRightsList estará vazio se o utilizador atual não tem acesso às informações de direitos de utilizador (ou seja, não é o proprietário e não tem direito a VIEWRIGHTSDATA).
  
### <a name="mipuserroles"></a>Mip::UserRoles
Obtém a coleção de mapeamentos de funções de utilizadores.

  
**Devolve**: coleção de mapeamentos de funções de utilizadores
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Obtém a hora de expiração de política.

  
**Devolve**: hora de expiração de política
  
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
Define a hora de expiração de política.

Parâmetros:  
* **valor**: hora de expiração de política


  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Obtém se ou não permite a política de acesso ao conteúdo offline.

  
**Devolve**: se é ou não política permite o acesso offline de conteúdo (predefinição = true)
  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Conjuntos de diretiva permite a offline ou não acesso ao conteúdo.

Parâmetros:  
* **valor**: ou não a diretiva permite acesso ao conteúdo offline


  
### <a name="getreferrer"></a>GetReferrer
Obtém o endereço de referência de política.

  
**Devolve**: endereço de referência de política o Referenciador for um URI que pode ser apresentado ao utilizador após a falha na aquisição de política que contém informações sobre como esse utilizador pode obter a permissão para aceder ao conteúdo.
  
### <a name="setreferrer"></a>SetReferrer
Define o endereço de referência de política.

Parâmetros:  
* **URI**: endereço do referenciador de política


O Referenciador for um URI que pode ser apresentado ao utilizador após a aquisição de política com falha que contém informações sobre como esse utilizador pode obter a permissão para aceder ao conteúdo.
  
### <a name="appdatahashmap"></a>AppDataHashMap
Obtém dados específicos da aplicação que foi encriptados.

  
**Devolve**: A de dados de aplicação específicos [UserPolicy](class_mip_userpolicy.md) pode conter um dicionário de dados específicos da aplicação que foi encriptados pelo serviço de RMS. Estes dados encriptados são independentes dos dados assinados podem ser acedidos através de [PolicyDescriptor::GetSignedAppData](class_mip_policydescriptor.md#getsignedappdata)
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Conjuntos de dados de aplicação específicos que devem ser encriptados.

Parâmetros:  
* **valor**: dados específicos da aplicação


Um aplicativo pode especificar um dicionário de dados específicos da aplicação serão encriptados pelo serviço de RMS. Estes dados encriptados são independentes do conjunto de dados assinado pelo [PolicyDescriptor::SetSignedAppData](class_mip_policydescriptor.md#setsignedappdata).
  
### <a name="appdatahashmap"></a>AppDataHashMap
Obtém os dados específicos da aplicação que foi assinados.

  
**Devolve**: A de dados de aplicação específicos [UserPolicy](class_mip_userpolicy.md) pode conter um dicionário de dados específicos da aplicação que foi assinados pelo serviço de RMS. Estes dados assinados são independentes dos dados encriptados podem ser acedidos através de [PolicyDescriptor::GetEncryptedAppData](class_mip_policydescriptor.md#getencryptedappdata)
  
### <a name="setsignedappdata"></a>SetSignedAppData
Conjuntos de dados específicos da aplicação que devem ser assinados.

Parâmetros:  
* **valor**: dados específicos da aplicação


Um aplicativo pode especificar um dicionário de dados específicos da aplicação que irão ser assinados pelo serviço de RMS. Estes dados assinados são independentes do conjunto de dados encriptado pela [PolicyDescriptor::SetEncryptedAppData](class_mip_policydescriptor.md#setencryptedappdata).