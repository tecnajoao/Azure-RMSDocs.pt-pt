# <a name="class-mipfileprofilesettings"></a>classe mip::FileProfile::Settings 
[As definições](class_mip_fileprofile_settings.md) utilizada pelo [FileProfile](class_mip_fileprofile.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (const std::shared_ptr Std:: String & caminho, bool useInMemoryStorage,<AuthDelegate> authDelegate, std::shared_ptr<ConsentDelegate> consentDelegate, std::shared_ptr<Observer> observador, const ApplicationInfo & applicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md) construtor.
 público const Std:: String & GetPath() const  |  Obtém o caminho em que o registo, telemetria, e outro estado persistente é armazenado.
 bool pública GetUseInMemoryStorage() const  |  Obtém se ou não a todos os Estados devem ser armazenados na memória (em vez de no disco)
público std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.
público std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Obtém o delegado de autorização utilizado para pedir consentimento do utilizador se ligam a serviços.
público std::shared_ptr<Observer> GetObserver() const  |  Obtém o observador que recebe notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md).
 público GetApplicationInfo() const ApplicationInfo const  |  Obtém informações sobre a aplicação que está a consumir o SDK.
 bool pública GetSkipTelemetryInit() const  |  Obtém se ou não a inicialização de telemetria deve ser ignorada.
 público SetSkipTelemetryInit() void  |  Desativa a inicialização de telemetria.
 público SetNewFeaturesDisabled() void  |  Desativa a novos recursos.
 bool pública AreNewFeaturesDisabled() const  |  Obtém independentemente de novos recursos estão desativados.
público std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.
SetLoggerDelegate void pública (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Substitua o agente de log padrão.
público std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Obtenha o delegado de http (se houver) fornecido pela aplicação.
SetHttpDelegate void pública (const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Substitua a pilha de http padrão do cliente.
 público OptOutTelemetry() void  |  Opta ativamente por toda a telemetria de recolha.
 bool pública IsTelemetryOptedOut() const  |  Obtém se ou não de recolha de telemetria que deve ser desabilitada.
 SetSessionId void pública (const Std:: String & sessionId)  |  Define o id de sessão.
 público const Std:: String & GetSessionId() const  |  Obtém o id de sessão.
 SetMinimumLogLevel void pública (LogLevel logLevel)  |  Defina o nível de registo mínimo que irão acionar um evento de log.
 público GetMinimumLogLevel() de LogLevel const  |  Obtenha o objeto de nível de registo mínimo.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
[FileProfile::Settings](class_mip_fileprofile_settings.md) construtor.

Parâmetros:  
* **caminho**: caminho de ficheiro em que o registo, telemetria e outras estado persistente é armazenado 


* **useInMemoryStorage**: se todos os Estados devem ser armazenados na memória (em vez de no disco) 


* **authDelegate**: delegado de autenticação utilizado para aquisição de tokens de autenticação 


* **observador**: [observador](class_mip_fileprofile_observer.md) instância que irão receber notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md)


* **applicationInfo**: informações sobre a aplicação que está a consumir o SDK


  
### <a name="getpath"></a>GetPath
Obtém o caminho em que o registo, telemetria, e outro estado persistente é armazenado.

  
**Devolve**: caminho em que o registo, telemetria e outras estado persistente é armazenado
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Obtém se ou não a todos os Estados devem ser armazenados na memória (em vez de no disco)

  
**Devolve**: se todos os Estados devem ser armazenados na memória (em vez de no disco)
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.

  
**Devolve**: delegado de autenticação utilizado para aquisição de tokens de autenticação
  
### <a name="consentdelegate"></a>ConsentDelegate
Obtém o delegado de autorização utilizado para pedir consentimento do utilizador se ligam a serviços.

  
**Devolve**: delegado de autorização utilizado para pedir o consentimento do utilizador
  
### <a name="observer"></a>Observador
Obtém o observador que recebe notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md).

  
**Devolve**: [observador](class_mip_fileprofile_observer.md) que recebe notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
Obtém informações sobre a aplicação que está a consumir o SDK.

  
**Devolve**: informações sobre a aplicação que está a consumir o SDK
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Obtém se ou não a inicialização de telemetria deve ser ignorada.

  
**Devolve**: se é ou não deve ser ignorada a inicialização de telemetria
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Desativa a inicialização de telemetria.
Isso não deve normalmente ser chamado por aplicações cliente, em vez disso, ela é usada pelo SDK de ficheiros (que já inicializa telemetria) para impedir a inicialização duplicada
  
### <a name="setnewfeaturesdisabled"></a>SetNewFeaturesDisabled
Desativa a novos recursos.
Para aplicações que não querem experimentar novas funcionalidades
  
### <a name="arenewfeaturesdisabled"></a>AreNewFeaturesDisabled
Obtém independentemente de novos recursos estão desativados.

  
**Devolve**: se é ou não os novos recursos estão desativados
  
### <a name="loggerdelegate"></a>LoggerDelegate
Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.

  
**Devolve**: delegado de agente de log a ser utilizado para registo
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Substitua o agente de log padrão.

Parâmetros:  
* **loggerDelegate**: interface de retorno de chamada de registo implementada por aplicações cliente


Isso deve ser chamado por aplicações cliente que utilizam a sua própria implementação de agente de log
  
### <a name="httpdelegate"></a>HttpDelegate
Obtenha o delegado de http (se houver) fornecido pela aplicação.

  
**Devolve**: delegado de Http a ser utilizado para operações de http
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
Substitua a pilha de http padrão do cliente.

Parâmetros:  
* **httpDelegate**: interface de retorno de chamada de Http implementada pela aplicação cliente


  
### <a name="optouttelemetry"></a>OptOutTelemetry
Opta ativamente por toda a telemetria de recolha.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Obtém se ou não de recolha de telemetria que deve ser desabilitada.

  
**Devolve**: se é ou não deve ser desabilitada de recolha de telemetria
  
### <a name="setsessionid"></a>SetSessionId
Define o id de sessão.

Parâmetros:  
* **sessionId**: id de sessão que será utilizado para correlacionar os registos/telemetria


  
### <a name="getsessionid"></a>GetSessionId
Obtém o id de sessão.

  
**Devolve**: id de sessão que será utilizado para correlacionar os registos/telemetria
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Defina o nível de registo mínimo que irão acionar um evento de log.

Parâmetros:  
* **logLevel**: nível de registo mínimo que irão acionar um evento de log. 



  
**Devolve**: VERDADEIRO
  
### <a name="loglevel"></a>LogLevel
Obtenha o objeto de nível de registo mínimo.

  
**Devolve**: nível de registo mínimo que irão acionar um evento de log.