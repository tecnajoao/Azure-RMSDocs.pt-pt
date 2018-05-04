# <a name="class-mipprofilesettings"></a>classe mip::Profile::Settings 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública definições (const std::shared_ptr std::string & caminho, bool useInMemoryStorage, const<AuthDelegate>& authDelegate, std::shared_ptr const < Profile::Observer > & observador, const ApplicationInfo & applicationInfo)  |  Interface para configurar o perfil.
std::string const inline pública & GetPath() const  |  Obter o caminho para o estado armazenado.
inline pública bool GetUseInMemoryStorage() const  |  Obter o sinalizador de utilização no armazenamento de memória.
std::shared_ptr const inline pública<AuthDelegate>& GetAuthDelegate() const  |  Obter o delegado de autenticação.
inline pública const std::shared_ptr < Profile::Observer > & GetObserver() const  |  Obter o observador de eventos.
inline pública const ApplicationInfo GetApplicationInfo() const  |  Obter as informações de aplicação.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Interface para configurar o perfil.
  
#### <a name="parameters"></a>Parâmetros
* o caminho para um diretório em que o sdk irá armazenar o estado do perfil do caminho. 
* useInMemoryStorage um sinalizador que indica se é ou não Estado deve ser armazenado no disco. 
* authDelegate o delegado de autenticação utilizado pelo SDK para adquirir authenitication tokens. 
* implementar uma classe de observador a [Profile::Observer](#classmip_1_1_profile_1_1_observer) interface. Pode ser nullptr. 
* applicationInfo os identificadores de aplicação utilizado para acesso de serviço.
  
### <a name="getpath"></a>GetPath
Obter o caminho para o estado armazenado.
  
#### <a name="returns"></a>Devolve
caminho para o estado armazenado.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Obter o sinalizador de utilização no armazenamento de memória.
  
#### <a name="returns"></a>Devolve
VERDADEIRO se a utilização na memória está definida ou falsa.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Obter o delegado de autenticação.
  
#### <a name="returns"></a>Devolve
o delegado de autenticação.
  
### <a name="profileobserver"></a>Profile::Observer
Obter o observador de eventos.
  
#### <a name="returns"></a>Devolve
o observador de eventos.
  
### <a name="applicationinfo"></a>ApplicationInfo
Obter as informações de aplicação.
  
#### <a name="returns"></a>Devolve
as informações de aplicação.