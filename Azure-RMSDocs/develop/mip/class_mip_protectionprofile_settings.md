# <a name="class-mipprotectionprofilesettings"></a>classe mip::ProtectionProfile::Settings 
[Definições](#classmip_1_1_protection_profile_1_1_settings) utilizado pelo [ProtectionProfile](#classmip_1_1_protection_profile) durante a criação e ao longo da respetiva duração.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública definições (const std::string & caminho, std::shared_ptr const < ProtectionProfile::Observer > & observador, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](#classmip_1_1_protection_profile_1_1_settings) construtor.
std::string const inline pública & GetPath() const  |  Obtém o caminho no qual o registo, telemetria, e outro collateral de proteção está armazenado.
inline pública const std::shared_ptr < ProtectionProfile::Observer > & GetObserver() const  |  Obtém o observador de eventos relacionados com as notificações que receieves [ProtectionProfile](#classmip_1_1_protection_profile).
inline pública const ApplicationInfo & GetApplicationInfo() const  |  Obtém informações sobre a aplicação que está a consumir a proteção SDK.
inline pública bool GetSkipTelemetryInit() const  |  Obtém ou não deve ser ignorada a inicialização de telemetria.
inline pública void SetSkipTelemetryInit()  |  Desativa a inicialização de telemetria.
inline pública void SetSessionId (const std::string & sessionId)  |  Define o id de sessão.
std::string const inline pública & GetSessionId() const  |  Obtém o id de sessão.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
[ProtectionProfile::Settings](#classmip_1_1_protection_profile_1_1_settings) construtor.
  
#### <a name="parameters"></a>Parâmetros
* caminho de ficheiro de caminho em que o registo, telemetria e de outras collateral de proteção é armazenado 
* observador [observador](#classmip_1_1_protection_profile_1_1_observer) instância que irá receber notificações de eventos relacionados com [ProtectionProfile](#classmip_1_1_protection_profile)
* applicationInfo informações relativamente à aplicação que está a consumir a proteção SDK
  
### <a name="getpath"></a>GetPath
Obtém o caminho no qual o registo, telemetria, e outro collateral de proteção está armazenado.
  
#### <a name="returns"></a>Devolve
Caminho em que o registo, telemetria e de outras collateral de proteção é armazenado
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Obtém o observador de eventos relacionados com as notificações que receieves [ProtectionProfile](#classmip_1_1_protection_profile).
  
#### <a name="returns"></a>Devolve
[Observador](#classmip_1_1_protection_profile_1_1_observer) as notificações que receieves de eventos relacionados com [ProtectionProfile](#classmip_1_1_protection_profile)
  
### <a name="applicationinfo"></a>ApplicationInfo
Obtém informações sobre a aplicação que está a consumir a proteção SDK.
  
#### <a name="returns"></a>Devolve
Informações sobre a aplicação que está a consumir a proteção SDK
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Obtém ou não deve ser ignorada a inicialização de telemetria.
  
#### <a name="returns"></a>Devolve
Se pretende ou não deve ser ignorada a inicialização de telemetria
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Desativa a inicialização de telemetria.
Isto não deve normalmente ser chamado por aplicações cliente, em vez disso é utilizado pelo SDK do ficheiro (o que já inicializa telemetria) para impedir a inicialização duplicada
  
### <a name="setsessionid"></a>SetSessionId
Define o id de sessão.
  
#### <a name="parameters"></a>Parâmetros
* id de sessão de sessionId que será utilizado para correlacionar os registos/telemetria
  
### <a name="getsessionid"></a>GetSessionId
Obtém o id de sessão.
  
#### <a name="returns"></a>Devolve
Id de sessão que será utilizado para correlacionar os registos/telemetria