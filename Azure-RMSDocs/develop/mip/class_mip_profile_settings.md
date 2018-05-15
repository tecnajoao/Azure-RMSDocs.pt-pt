# <a name="class-mipprofilesettings"></a>classe mip::Profile::Settings 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de público (const std::shared_ptr std::string & caminho, bool useInMemoryStorage, const<AuthDelegate>& authDelegate, std::shared_ptr const < Profile::Observer > & observador, const ApplicationInfo & applicationInfo)  |  Interface para configurar o perfil.
 pública std::string const & GetPath() const  |  Obter o caminho para o estado armazenado.
 bool pública GetUseInMemoryStorage() const  |  Obter o sinalizador de utilização no armazenamento de memória.
pública std::shared_ptr const<AuthDelegate>& GetAuthDelegate() const  |  Obter o delegado de autenticação.
std::shared_ptr const pública < Profile::Observer > & GetObserver() const  |  Obter o observador de eventos.
 pública GetApplicationInfo() const ApplicationInfo const  |  Obter as informações de aplicação.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Interface para configurar o perfil.

Parâmetros:  
* **caminho**: O caminho para um diretório em que o sdk irá armazenar o estado do perfil. 


* **useInMemoryStorage**: um sinalizador que indica se é ou não Estado deve ser armazenado no disco. 


* **authDelegate**: O delegado de autenticação utilizado pelo SDK para adquirir authenitication tokens. 


* **observador**: implementar uma classe a [Profile::Observer](class_mip_profile_observer.md) interface. Pode ser nullptr. 


* **applicationInfo**: os identificadores de aplicação utilizados para o acesso ao serviço.


  
### <a name="getpath"></a>GetPath
Obter o caminho para o estado armazenado.

  
**Devolve**: caminho para o estado armazenado.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Obter o sinalizador de utilização no armazenamento de memória.

  
**Devolve**: True se a utilização na memória está definida ou falsa.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Obter o delegado de autenticação.

  
**Devolve**: O delegado de autenticação.
  
### <a name="profileobserver"></a>Profile::Observer
Obter o observador de eventos.

  
**Devolve**: O observador de eventos.
  
### <a name="applicationinfo"></a>ApplicationInfo
Obter as informações de aplicação.

  
**Devolve**: as informações de aplicação.