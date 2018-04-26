# <a name="class-mippolicydescriptor"></a>classe mip::PolicyDescriptor 
Representa uma política ad-hoc associada ao conteúdo protegido.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública std::string const & GetName | Obtém o nome da política.
SetName void público | Nome da política de conjuntos.
pública std::string const & GetDescription | Obtém a descrição da política.
SetDescription void público | Define a descrição da política.
std::vector const pública < UserRights > & GetUserRightsList | Obtém a coleção de mapeamentos de direitos de utilizadores.
std::vector const pública < mip::UserRoles > & GetUserRolesList | Obtém a coleção de mapeamentos de funções de utilizadores.
std::chrono::time_point const pública < std::chrono::system_clock > & GetContentValidUntil | Obtém a hora de expiração de política.
SetContentValidUntil void público | Define a hora de expiração de política.
bool pública DoesAllowOfflineAccess | Obtém ou não permite a política de acesso a conteúdos offline.
SetAllowOfflineAccess void público | Define se pretende ou não permite offline a política de acesso a conteúdos.
pública std::string const & GetReferrer | Obtém o endereço de referência de política.
SetReferrer void público | Define o endereço de referência de política.
pública AppDataHashMap const & GetEncryptedAppData | Obtém dados específicos da aplicação que foi encriptados.
pública SetEncryptedAppDataAppDataHashMap void & valor) | Define dados específicos da aplicação que devem ser encriptados.
pública AppDataHashMap const & GetSignedAppData | Obtém os dados específicos da aplicação foi assinados.
pública SetSignedAppDataAppDataHashMap void & valor) | Define dados específicos da aplicação que devem estar assinados.
## <a name="members"></a>Membros
### <a name="getname"></a>GetName
Obtém o nome da política.
#### <a name="returns"></a>Devolve
Nome da política
### <a name="setname"></a>SetName
Nome da política de conjuntos.
#### <a name="parameters"></a>Parâmetros
* nome do valor de política
### <a name="getdescription"></a>GetDescription
Obtém a descrição da política.
#### <a name="returns"></a>Devolve
Descrição da política
### <a name="setdescription"></a>SetDescription
Define a descrição da política.
#### <a name="parameters"></a>Parâmetros
* valor de descrição da política
### <a name="userrights"></a>UserRights
Obtém a coleção de mapeamentos de direitos de utilizadores.
#### <a name="returns"></a>Devolve
Coleção de mapeamentos de direitos de utilizadores o valor da propriedade UserRightsList estará vazio se o utilizador atual não tem acesso às informações de direitos de utilizador (ou seja, não é o proprietário e não tem o direito VIEWRIGHTSDATA).
### <a name="mipuserroles"></a>Mip::UserRoles
Obtém a coleção de mapeamentos de funções de utilizadores.
#### <a name="returns"></a>Devolve
Coleção de mapeamentos de funções de utilizadores
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Obtém a hora de expiração de política.
#### <a name="returns"></a>Devolve
Hora de expiração de política
### <a name="setcontentvaliduntil"></a>SetContentValidUntil
Define a hora de expiração de política.
#### <a name="parameters"></a>Parâmetros
* hora de expiração de política de valor
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Obtém ou não permite a política de acesso a conteúdos offline.
#### <a name="returns"></a>Devolve
Se pretende ou não política permite acesso a conteúdos offline (predefinição = true)
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Define se pretende ou não permite offline a política de acesso a conteúdos.
#### <a name="parameters"></a>Parâmetros
* valor ou não política permite o acesso ao conteúdo offline
### <a name="getreferrer"></a>GetReferrer
Obtém o endereço de referência de política.
#### <a name="returns"></a>Devolve
Endereço de referência de política de referência é um URI que pode ser apresentado ao utilizador após a aquisição de política de falha que contém informações sobre a forma como esse utilizador pode ter permissão para aceder ao conteúdo.
### <a name="setreferrer"></a>SetReferrer
Define o endereço de referência de política.
#### <a name="parameters"></a>Parâmetros
* endereço de referência de política de URI de referência é um URI que pode ser apresentado ao utilizador após a aquisição de política de falha que contém informações sobre a forma como esse utilizador pode ter permissão para aceder ao conteúdo.
### <a name="appdatahashmap"></a>AppDataHashMap
Obtém dados específicos da aplicação que foi encriptados.
#### <a name="returns"></a>Devolve
Dados de aplicação específicos A [UserPolicy](#classmip_1_1_user_policy) pode conter um dicionário de dados específicos da aplicação que foi encriptados pelo serviço RMS. Estes dados encriptados são independentes dos dados assinados acessíveis através de [PolicyDescriptor::GetSignedAppData](#classmip_1_1_policy_descriptor_1ad523870efc92f9f81c82121a054d74d4)
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Define dados específicos da aplicação que devem ser encriptados.
#### <a name="parameters"></a>Parâmetros
* dados do valor específico da aplicação uma aplicação pode especificar um dicionário de dados específico da aplicação serão encriptados pelo serviço de RMS. Estes dados encriptados são independentes do conjunto de dados assinado pelo [PolicyDescriptor::SetSignedAppData](#classmip_1_1_policy_descriptor_1a00f35c0b91e48ccdcc6387466a61f362).
### <a name="appdatahashmap"></a>AppDataHashMap
Obtém os dados específicos da aplicação foi assinados.
#### <a name="returns"></a>Devolve
Dados de aplicação específicos A [UserPolicy](#classmip_1_1_user_policy) pode conter um dicionário de dados específico da aplicação foi assinados pelo serviço de RMS. Estes dados assinados são independentes dos dados encriptados acessíveis através de [PolicyDescriptor::GetEncryptedAppData](#classmip_1_1_policy_descriptor_1a9a5bcf9d1bf7357de549429179197ab6)
### <a name="setsignedappdata"></a>SetSignedAppData
Define dados específicos da aplicação que devem estar assinados.
#### <a name="parameters"></a>Parâmetros
* dados do valor específico da aplicação uma aplicação pode especificar um dicionário de dados específicos da aplicação que serão assinados pelo serviço de RMS. Estes dados assinados são independentes do conjunto de dados encriptado pela [PolicyDescriptor::SetEncryptedAppData](#classmip_1_1_policy_descriptor_1a5275224932dc17319092304497e59eb2).