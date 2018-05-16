# <a name="class-mipfileprofilesettings"></a>classe mip::FileProfile::Settings 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de público (const std::shared_ptr std::string & caminho, bool useInMemoryStorage,<AuthDelegate> authDelegate, std::shared_ptr<Observer> observador, const ApplicationInfo & applicationInfo)  |  Interface para configurar o perfil.
 ~Settings() público  | _Ainda não documentado._
 pública std::string const & GetPath() const  | _Ainda não documentado._
 bool pública GetUseInMemoryStorage() const  | _Ainda não documentado._
std::shared_ptr pública<AuthDelegate> GetAuthDelegate() const  | _Ainda não documentado._
std::shared_ptr pública<Observer> GetObserver() const  | _Ainda não documentado._
 pública GetApplicationInfo() const ApplicationInfo const  | _Ainda não documentado._
 bool pública GetSkipTelemetryInit() const  | _Ainda não documentado._
 SetSkipTelemetryInit() void público  | _Ainda não documentado._
 SetSessionId void público (const std::string & sessionId)  |  Define o id de sessão de perfil.
 pública std::string const & GetSessionId() const  |  Devolva o id de sessão de perfil.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Interface para configurar o perfil.

Parâmetros:  
* **observador**: implementar uma classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. Pode ser nullptr.


  
### <a name="settings"></a>~ Definições de
_Não documentados ainda._

  
### <a name="getpath"></a>GetPath
_Não documentados ainda._

  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
_Não documentados ainda._

  
### <a name="getauthdelegate"></a>GetAuthDelegate
_Não documentados ainda._

  
### <a name="observer"></a>Observador
_Não documentados ainda._

  
### <a name="applicationinfo"></a>ApplicationInfo
_Não documentados ainda._

  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
_Não documentados ainda._

  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
_Não documentados ainda._

  
### <a name="setsessionid"></a>SetSessionId
Define o id de sessão de perfil.
  
### <a name="getsessionid"></a>GetSessionId
Devolva o id de sessão de perfil.