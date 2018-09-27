# <a name="class-mippolicyenginesettings"></a>classe mip::PolicyEngine::Settings 
Deve ser fornecer uma instância dessa classe com os parâmetros adequados para iniciar um motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de públicas (const Std:: String & engineId, const Std:: String & clientData, const Std:: String e Localidade)  |  Construa uma instância com os parâmetros especificados. Utilize esta opção para criar [definições](class_mip_policyengine_settings.md) chamar LoadEngineAsync para carregar um motor de existente.
 Definições de públicas (const identidade e identidade, const Std:: String & clientData, const Std:: String e Localidade)  |  Utilize esta opção para criar [definições](class_mip_policyengine_settings.md) AddEngineAsync para adicionar um novo mecanismo de chamar.
 público const Std:: String & GetEngineId() const  |  Obtenha o id de motor.
 SetEngineId void pública (const Std:: String & id)  |  Defina o id de motor.
 Identidade de const pública e GetIdentity() const  |  Obtenha o objeto de identidade.
 SetIdentity void pública (const identidade e de identidade)  |  Defina o objeto de identidade.
 público const Std:: String & GetClientData() const  |  Obter os dados de cliente definido nas definições.
 SetClientData void pública (const Std:: String & clientData)  |  Defina a cadeia de dados do cliente.
 público const Std:: String & GetLocale() const  |  Obtenha a região definida nas definições.
SetCustomSettings void pública (Std:: vector const < std::pair < Std:: String, Std:: String >> & customSettings)  |  Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetCustomSettings() const  |  Obter as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
 SetSessionId void pública (const Std:: String & sessionId)  |  Defina o id de sessão utilizado para a telemetria de cliente definida.
 público const Std:: String & GetSessionId() const  |  Obtenha o id de sessão, um identificador exclusivo.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Construa uma instância com os parâmetros especificados. Utilize esta opção para criar [definições](class_mip_policyengine_settings.md) chamar LoadEngineAsync para carregar um motor de existente.

Parâmetros:  
* **engineId**: configurá-lo para o id de mecanismo exclusivo gerado pelo AddEngineAsync ou Self-gerado. Quando voltar a carregar um motor de existente a utilizar o id de outro um novo mecanismo será criado. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade.


  
### <a name="settings"></a>Definições
Utilize esta opção para criar [definições](class_mip_policyengine_settings.md) AddEngineAsync para adicionar um novo mecanismo de chamar.

Parâmetros:  
* **identidade**: um identificador exclusivo do utilizador para quem o mecanismo de tem de ser adicionada. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade.


  
### <a name="getengineid"></a>GetEngineId
Obtenha o id de motor.

  
**Devolve**: uma cadeia exclusiva de identificar o motor.
  
### <a name="setengineid"></a>SetEngineId
Defina o id de motor.

Parâmetros:  
* **ID**: id de motor.


  
### <a name="getidentity"></a>GetIdentity
Obtenha o objeto de identidade.

  
**Devolve**: uma referência para a identidade no objeto de definições. 
  
**Consulte também**: mip::Identity
  
### <a name="setidentity"></a>SetIdentity
Defina o objeto de identidade.

Parâmetros:  
* **identidade**: a identidade exclusiva de um utilizador. 


  
**Consulte também**: mip::Identity
  
### <a name="getclientdata"></a>GetClientData
Obter os dados de cliente definido nas definições.

  
**Devolve**: uma cadeia de caracteres de dados especificada pelo cliente.
  
### <a name="setclientdata"></a>SetClientData
Defina a cadeia de dados do cliente.

Parâmetros:  
* **clientData**: especificadas pelo utilizador e dados.


  
### <a name="getlocale"></a>GetLocale
Obtenha a região definida nas definições.

  
**Devolve**: A localidade.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.

Parâmetros:  
* **customSettings**: lista de pares nome/valor.


  
### <a name="getcustomsettings"></a>GetCustomSettings
Obter as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.

  
**Devolve**: lista de pares nome/valor.
  
### <a name="setsessionid"></a>SetSessionId
Defina o id de sessão utilizado para a telemetria de cliente definida.

Parâmetros:  
* **sessionId**: uma cadeia exclusiva que conecta eventos de telemetria.


  
### <a name="getsessionid"></a>GetSessionId
Obtenha o id de sessão, um identificador exclusivo.

  
**Devolve**: O id de sessão.