# <a name="class-mipprotectionprofilesettings"></a>classe mip::ProtectionProfile::Settings 
[As definições](class_mip_protectionprofile_settings.md) utilizada pelo [ProtectionProfile](class_mip_protectionprofile.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (isLicenseCachingEnabled de bool Std:: String & caminho, bool useInMemoryStorage, const, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const std::shared_ptr < ProtectionProfile::Observer > & observador, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) construtor.
 público const Std:: String & GetPath() const  |  Obtém o caminho em que o registo, telemetria, e outros materiais de proteção são armazenados.
 bool pública GetUseInMemoryStorage() const  |  Obter se ou caches são armazenadas na memória apenas (em vez de no disco)
 bool pública IsLicenseCachingEnabled() const  |  Obter se ou a colocação em cache de licenças é ativada.
público std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.
público std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Obtém o delegado de autorização utilizado para ligar aos serviços.
std::shared_ptr const público < ProtectionProfile::Observer > & GetObserver() const  |  Obtém o observador que recebe notificações de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md).
 público ApplicationInfo const & GetApplicationInfo() const  |  Obtém informações sobre a aplicação que esteja a consumir a proteção do SDK.
 público OptOutTelemetry() void  |  Opta ativamente por toda a telemetria de recolha.
 bool pública IsTelemetryOptedOut() const  |  Obtém se ou não de recolha de telemetria que deve ser desabilitada.
público std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.
SetLoggerDelegate void pública (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Utilize a implementação de agente de log externo.
 bool pública GetSkipTelemetryInit() const  |  Obtém se ou não a inicialização de telemetria deve ser ignorada.
 público SetSkipTelemetryInit() void  |  Desativa a inicialização de telemetria.
 SetSessionId void pública (const Std:: String & sessionId)  |  Define o id de sessão.
 público const Std:: String & GetSessionId() const  |  Obtém o id de sessão.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) construtor.

Parâmetros:  
* **caminho**: caminho de ficheiro em que o registo, telemetria e outros materiais de proteção são armazenados 


* **useInMemoryStorage**: Store qualquer Estado em cache na memória, em vez de no disco 


* **isLicenseCachingEnabled**: Ativar ou desativar a colocação em cache de licenças do sdk de proteção 


* **authDelegate**: objeto de retorno de chamada a ser utilizado para autenticação, implementada pela aplicação cliente 


* **observador**: [observador](class_mip_protectionprofile_observer.md) instância que irão receber notificações de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md)


* **applicationInfo**: informações sobre a aplicação que esteja a consumir a proteção de SDK


  
### <a name="getpath"></a>GetPath
Obtém o caminho em que o registo, telemetria, e outros materiais de proteção são armazenados.

  
**Devolve**: caminho em que o registo, telemetria e outros materiais de proteção são armazenados
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Obter se ou caches são armazenadas na memória apenas (em vez de no disco)

  
**Devolve**: True se as caches são armazenadas na memória apenas
  
### <a name="islicensecachingenabled"></a>IsLicenseCachingEnabled
Obter se ou a colocação em cache de licenças é ativada.

  
**Devolve**: True se o cache da licença SDK de proteção está ativada
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.

  
**Devolve**: delegado de autenticação utilizado para aquisição de tokens de autenticação
  
### <a name="consentdelegate"></a>ConsentDelegate
Obtém o delegado de autorização utilizado para ligar aos serviços.

  
**Devolve**: delegado de autorização utilizado para ligar aos serviços
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Obtém o observador que recebe notificações de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md).

  
**Devolve**: [observador](class_mip_protectionprofile_observer.md) que recebe notificações de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
Obtém informações sobre a aplicação que esteja a consumir a proteção do SDK.

  
**Devolve**: informações sobre a aplicação que esteja a consumir a proteção de SDK
  
### <a name="optouttelemetry"></a>OptOutTelemetry
Opta ativamente por toda a telemetria de recolha.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Obtém se ou não de recolha de telemetria que deve ser desabilitada.

  
**Devolve**: se é ou não deve ser desabilitada de recolha de telemetria
  
### <a name="loggerdelegate"></a>LoggerDelegate
Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.

  
**Devolve**: delegado de agente de log a ser utilizado para registo
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Utilize a implementação de agente de log externo.
Isso deve ser chamado por aplicações cliente se desejarem usar sua própria implementação de agente de log
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Obtém se ou não a inicialização de telemetria deve ser ignorada.

  
**Devolve**: se é ou não deve ser ignorada a inicialização de telemetria
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Desativa a inicialização de telemetria.
Isso não deve normalmente ser chamado por aplicações cliente, em vez disso, ela é usada pelo SDK de ficheiros (que já inicializa telemetria) para impedir a inicialização duplicada
  
### <a name="setsessionid"></a>SetSessionId
Define o id de sessão.

Parâmetros:  
* **sessionId**: id de sessão que será utilizado para correlacionar os registos/telemetria


  
### <a name="getsessionid"></a>GetSessionId
Obtém o id de sessão.

  
**Devolve**: id de sessão que será utilizado para correlacionar os registos/telemetria