# <a name="class-mipfileprofilesettings"></a>classe mip::FileProfile::Settings 
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública SettingsObserver > observador, const ApplicationInfo & applicationInfo) | Interface para configurar o perfil.
inline pública ~ definições | 
std::string const inline pública & GetPath | 
inline pública bool GetUseInMemoryStorage | 
inline pública std::shared_ptr < AuthDelegate > GetAuthDelegate | 
inline pública std::shared_ptr < observador > GetObserver | 
inline pública const ApplicationInfo GetApplicationInfo | 
inline pública bool GetSkipTelemetryInit | 
inline pública void SetSkipTelemetryInit | 
inline pública void SetSessionId | Define o id de sessão de perfil.
std::string const inline pública & GetSessionId | Devolva o id de sessão de perfil.
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