# <a name="class-mipprotectionprofilesettings"></a>classe mip::ProtectionProfile::Settings 
[Definições](class_mip_protectionprofile_settings.md) utilizado pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a criação e ao longo da respetiva duração.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de público (const std::string & caminho, std::shared_ptr const < ProtectionProfile::Observer > & observador, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) construtor.
 pública std::string const & GetPath() const  |  Obtém o caminho no qual o registo, telemetria, e outro collateral de proteção está armazenado.
std::shared_ptr const pública < ProtectionProfile::Observer > & GetObserver() const  |  Obtém o observador de eventos relacionados com as notificações que receieves [ProtectionProfile](class_mip_protectionprofile.md).
 pública ApplicationInfo const & GetApplicationInfo() const  |  Obtém informações sobre a aplicação que está a consumir a proteção SDK.
 bool pública GetSkipTelemetryInit() const  |  Obtém ou não deve ser ignorada a inicialização de telemetria.
 SetSkipTelemetryInit() void público  |  Desativa a inicialização de telemetria.
 SetSessionId void público (const std::string & sessionId)  |  Define o id de sessão.
 pública std::string const & GetSessionId() const  |  Obtém o id de sessão.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) construtor.

Parâmetros:  
* **caminho**: caminho de ficheiro em que o registo, telemetria e de outras collateral de proteção é armazenado 


* **observador**: [observador](class_mip_protectionprofile_observer.md) instância que irá receber notificações de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md)


* **applicationInfo**: informações sobre a aplicação que está a consumir a proteção SDK


  
### <a name="getpath"></a>GetPath
Obtém o caminho no qual o registo, telemetria, e outro collateral de proteção está armazenado.

  
**Devolve**: caminho em que o registo, telemetria e de outras collateral de proteção é armazenado
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Obtém o observador de eventos relacionados com as notificações que receieves [ProtectionProfile](class_mip_protectionprofile.md).

  
**Devolve**: [observador](class_mip_protectionprofile_observer.md) as notificações que receieves de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
Obtém informações sobre a aplicação que está a consumir a proteção SDK.

  
**Devolve**: informações sobre a aplicação que está a consumir a proteção SDK
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Obtém ou não deve ser ignorada a inicialização de telemetria.

  
**Devolve**: se a inicialização de telemetria deve ser ignorada
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Desativa a inicialização de telemetria.
Isto não deve normalmente ser chamado por aplicações cliente, em vez disso é utilizado pelo SDK do ficheiro (o que já inicializa telemetria) para impedir a inicialização duplicada
  
### <a name="setsessionid"></a>SetSessionId
Define o id de sessão.

Parâmetros:  
* **sessionId**: id de sessão que será utilizado para correlacionar os registos/telemetria


  
### <a name="getsessionid"></a>GetSessionId
Obtém o id de sessão.

  
**Devolve**: id de sessão que será utilizado para correlacionar os registos/telemetria