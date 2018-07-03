# <a name="class-mipprotectionenginesettings"></a>classe mip::ProtectionEngine::Settings 
[As definições](class_mip_protectionengine_settings.md) utilizada pelo [ProtectionEngine](class_mip_protectionengine.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de públicas (const identidade e identidade, const Std:: String & clientData, const Std:: String e Localidade)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para a criação de um novo mecanismo.
 Definições de públicas (const Std:: String & engineId, const Std:: String & clientData, const Std:: String e Localidade)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para carregar um motor de existente.
 público const Std:: String & GetEngineId() const  |  Obtém o mecanismo de ID.
 SetEngineId void pública (const Std:: String & engineId)  |  Define o id de motor.
 Identidade de const pública e GetIdentity() const  |  Obtém o usuário que identidade associada com o motor.
 SetIdentity void pública (const identidade e de identidade)  |  Define o usuário que identidade associada com o motor.
 público const Std:: String & GetClientData() const  |  Obtém dados personalizados especificados pelo cliente.
 público const Std:: String & GetLocale() const  |  Obtém a localidade no mecanismo de qual dados serão escritos.
SetCustomSettings void pública (Std:: vector const < std::pair < Std:: String, Std:: String >> & valor)  |  Conjuntos de pares nome/valor utilizados para testar e experimentação.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetCustomSettings() const  |  Obtém pares nome/valor utilizados para testar e experimentação.
 SetSessionId void pública (const Std:: String & sessionId)  |  Define o id de sessão do mecanismo, utilizado para a correlação de registo ou de telemetria.
 público const Std:: String & GetSessionId() const  |  Obtém o id de sessão do motor.
 SetCloudEndpointBaseUrl void pública (const Std:: String & cloudEndpointBaseUrl)  |  Define o cloud base url de ponto final, utilizado para especificar o limite da cloud.
 público const Std:: String & GetCloudEndpointBaseUrl() const  |  Obtém o cloudEndpointBaseUrl.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para a criação de um novo mecanismo.

Parâmetros:  
* **identidade**: identidade que será associada [ProtectionEngine](class_mip_protectionengine.md)


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas e podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída motor será fornecida nesta região, predefinida "en-US".


  
### <a name="settings"></a>Definições
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para carregar um motor de existente.

Parâmetros:  
* **engineId**: um identificador exclusivo do motor que será carregado 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas e podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída motor será fornecida nesta região, predefinida "en-US".


  
### <a name="getengineid"></a>GetEngineId
Obtém o mecanismo de ID.

  
**Devolve**: id de motor
  
### <a name="setengineid"></a>SetEngineId
Define o id de motor.

Parâmetros:  
* **engineId**: id de motor.


  
### <a name="getidentity"></a>GetIdentity
Obtém o usuário que identidade associada com o motor.

  
**Devolve**: identidade de utilizador associadas com o mecanismo de
  
### <a name="setidentity"></a>SetIdentity
Define o usuário que identidade associada com o motor.

Parâmetros:  
* **identidade**: identidade de utilizador associadas com o mecanismo de


  
### <a name="getclientdata"></a>GetClientData
Obtém dados personalizados especificados pelo cliente.

  
**Devolve**: dados personalizados especificados pelo cliente
  
### <a name="getlocale"></a>GetLocale
Obtém a localidade no mecanismo de qual dados serão escritos.

  
**Devolve**: região no qual mecanismo os dados serão escritos
  
### <a name="setcustomsettings"></a>SetCustomSettings
Conjuntos de pares nome/valor utilizados para testar e experimentação.

Parâmetros:  
* **customSettings**: pares nome/valor utilizados para testar e experimentação


  
### <a name="getcustomsettings"></a>GetCustomSettings
Obtém pares nome/valor utilizados para testar e experimentação.

  
**Devolve**: pares nome/valor utilizados para testar e experimentação
  
### <a name="setsessionid"></a>SetSessionId
Define o id de sessão do mecanismo, utilizado para a correlação de registo ou de telemetria.

Parâmetros:  
* **sessionId**: id de sessão do mecanismo, utilizado para a correlação de registo/telemetria


  
### <a name="getsessionid"></a>GetSessionId
Obtém o id de sessão do motor.

  
**Devolve**: id de sessão do motor
  
### <a name="setcloudendpointbaseurl"></a>SetCloudEndpointBaseUrl
Define o cloud base url de ponto final, utilizado para especificar o limite da cloud.

Parâmetros:  
* **cloudEndpointBaseUrl**: url associado a pontos finais de proteção de Base


  
### <a name="getcloudendpointbaseurl"></a>GetCloudEndpointBaseUrl
Obtém o cloudEndpointBaseUrl.

  
**Devolve**: url associado a pontos finais de proteção de Base