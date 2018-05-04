# <a name="class-mipfileprofilesettings"></a>classe mip::FileProfile::Settings 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública definições (const std::shared_ptr std::string & caminho, bool useInMemoryStorage,<AuthDelegate> authDelegate, std::shared_ptr<Observer> observador, const ApplicationInfo & applicationInfo)  |  Interface para configurar o perfil.
~Settings() inline público  |  
std::string const inline pública & GetPath() const  |  
inline pública bool GetUseInMemoryStorage() const  |  
inline pública std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  
inline pública std::shared_ptr<Observer> GetObserver() const  |  
inline pública const ApplicationInfo GetApplicationInfo() const  |  
inline pública bool GetSkipTelemetryInit() const  |  
inline pública void SetSkipTelemetryInit()  |  
inline pública void SetSessionId (const std::string & sessionId)  |  Define o id de sessão de perfil.
std::string const inline pública & GetSessionId() const  |  Devolva o id de sessão de perfil.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Interface para configurar o perfil.
  
#### <a name="parameters"></a>Parâmetros
* implementar uma classe de observador a [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) interface. Pode ser nullptr.
  
### <a name="settings"></a>~ Definições de
  
### <a name="getpath"></a>GetPath
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
  
### <a name="getauthdelegate"></a>GetAuthDelegate
  
### <a name="observer"></a>Observador
  
### <a name="applicationinfo"></a>ApplicationInfo
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
  
### <a name="setsessionid"></a>SetSessionId
Define o id de sessão de perfil.
  
### <a name="getsessionid"></a>GetSessionId
Devolva o id de sessão de perfil.