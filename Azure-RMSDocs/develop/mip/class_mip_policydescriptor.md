# <a name="class-mippolicydescriptor"></a>classe mip::PolicyDescriptor 
Representa uma política ad-hoc associada ao conteúdo protegido.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 pública std::string const & GetName()  |  Obtém o nome da política.
 SetName void público (const std::string & valor)  |  Nome da política de conjuntos.
 pública std::string const & GetDescription()  |  Obtém a descrição da política.
 SetDescription void público (const std::string & valor)  |  Define a descrição da política.
pública std::vector const<UserRights>& GetUserRightsList() const  |  Obtém a coleção de mapeamentos de direitos de utilizadores.
std::vector const pública < mip::UserRoles > & GetUserRolesList()  |  Obtém a coleção de mapeamentos de funções de utilizadores.
std::chrono::time_point const pública < std::chrono::system_clock > & GetContentValidUntil()  |  Obtém a hora de expiração de política.
SetContentValidUntil void público (const std::chrono::time_point < std::chrono::system_clock > & valor)  |  Define a hora de expiração de política.
 bool pública DoesAllowOfflineAccess()  |  Obtém ou não permite a política de acesso a conteúdos offline.
 SetAllowOfflineAccess void público (bool valor)  |  Define se pretende ou não permite offline a política de acesso a conteúdos.
 pública std::string const & GetReferrer() const  |  Obtém o endereço de referência de política.
 SetReferrer void público (const std::string & uri)  |  Define o endereço de referência de política.
 pública AppDataHashMap const & GetEncryptedAppData()  |  Obtém dados específicos da aplicação que foi encriptados.
 SetEncryptedAppData void público (const AppDataHashMap & valor)  |  Define dados específicos da aplicação que devem ser encriptados.
 pública AppDataHashMap const & GetSignedAppData()  |  Obtém os dados específicos da aplicação foi assinados.
 SetSignedAppData void público (const AppDataHashMap & valor)  |  Define dados específicos da aplicação que devem estar assinados.
  
## <a name="members"></a>Membros
  
### <a name="getname"></a>GetName
Obtém o nome da política.

  
**Devolve**: nome da política
  
### <a name="setname"></a>SetName
Nome da política de conjuntos.

Parâmetros:  
* **valor**: nome da política


  
### <a name="getdescription"></a>GetDescription
Obtém a descrição da política.

  
**Devolve**: Descrição da política
  
### <a name="setdescription"></a>SetDescription
Define a descrição da política.

Parâmetros:  
* **valor**: Descrição da política


  
### <a name="userrights"></a>UserRights
Obtém a coleção de mapeamentos de direitos de utilizadores.

  
**Devolve**: recolha de mapeamentos de direitos de utilizadores o valor da propriedade UserRightsList estará vazio se o utilizador atual não tem acesso às informações de direitos de utilizador (ou seja, não é o proprietário e não tem o direito VIEWRIGHTSDATA).
  
### <a name="mipuserroles"></a>Mip::UserRoles
Obtém a coleção de mapeamentos de funções de utilizadores.

  
**Devolve**: recolha de mapeamentos de funções de utilizadores
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Obtém a hora de expiração de política.

  
**Devolve**: hora de expiração de política
  
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
Define a hora de expiração de política.

Parâmetros:  
* **valor**: hora de expiração de política


  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Obtém ou não permite a política de acesso a conteúdos offline.

  
**Devolve**: ou não política permite o acesso ao conteúdo offline (predefinição = true)
  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Define se pretende ou não permite offline a política de acesso a conteúdos.

Parâmetros:  
* **valor**: ou não política permite o acesso ao conteúdo offline


  
### <a name="getreferrer"></a>GetReferrer
Obtém o endereço de referência de política.

  
**Devolve**: endereço de referência de política de referência é um URI que pode ser apresentado ao utilizador após a falha na aquisição de política que contém informações sobre a forma como esse utilizador pode ter permissão para aceder ao conteúdo.
  
### <a name="setreferrer"></a>SetReferrer
Define o endereço de referência de política.

Parâmetros:  
* **URI**: endereço de referência de política


A referência é um URI que pode ser apresentado ao utilizador após a aquisição de política de falha que contém informações sobre a forma como esse utilizador pode ter permissão para aceder ao conteúdo.
  
### <a name="appdatahashmap"></a>AppDataHashMap
Obtém dados específicos da aplicação que foi encriptados.

  
**Devolve**: dados específicos da aplicação A [UserPolicy](class_mip_userpolicy.md) pode conter um dicionário de dados específicos da aplicação que foi encriptados pelo serviço RMS. Estes dados encriptados são independentes dos dados assinados acessíveis através de [PolicyDescriptor::GetSignedAppData](class_mip_policydescriptor.md#getsignedappdata)
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Define dados específicos da aplicação que devem ser encriptados.

Parâmetros:  
* **valor**: dados específicos da aplicação


Uma aplicação pode especificar um dicionário de dados específico da aplicação serão encriptados pelo serviço de RMS. Estes dados encriptados são independentes do conjunto de dados assinado pelo [PolicyDescriptor::SetSignedAppData](class_mip_policydescriptor.md#setsignedappdata).
  
### <a name="appdatahashmap"></a>AppDataHashMap
Obtém os dados específicos da aplicação foi assinados.

  
**Devolve**: dados específicos da aplicação A [UserPolicy](class_mip_userpolicy.md) pode conter um dicionário de dados específico da aplicação foi assinados pelo serviço de RMS. Estes dados assinados são independentes dos dados encriptados acessíveis através de [PolicyDescriptor::GetEncryptedAppData](class_mip_policydescriptor.md#getencryptedappdata)
  
### <a name="setsignedappdata"></a>SetSignedAppData
Define dados específicos da aplicação que devem estar assinados.

Parâmetros:  
* **valor**: dados específicos da aplicação


Uma aplicação pode especificar um dicionário de dados específicos da aplicação que serão assinados pelo serviço de RMS. Estes dados assinados são independentes do conjunto de dados encriptado pela [PolicyDescriptor::SetEncryptedAppData](class_mip_policydescriptor.md#setencryptedappdata).