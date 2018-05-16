# <a name="class-mippolicyenginesettings"></a>classe mip::PolicyEngine::Settings 
Forneça uma instância desta classe com approprieted parâmetros devem ser para iniciar um motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de público (const std::string & id, const std::string & clientData, const std::string & região)  |  Construir uma instância com parâmetros especificados. Utilize esta opção para criar [definições](class_mip_policyengine_settings.md) chamar LoadEngineAsync ao carregar o motor de uma existente.
 Definições de público (const identidade & identidade, const std::string & clientData, const std::string e região)  |  Utilize esta opção para criar [definições](class_mip_policyengine_settings.md) chamar AddEngineAsync para adicionar um novo motor.
 pública std::string const & GetId() const  |  Obter o id de motor.
 SetId void público (const std::string & id)  |  Defina o id de motor.
 Identidade const pública & GetIdentity() const  |  Obter o objeto de identidade.
 SetIdentity void público (const identidade e de identidade)  |  Defina o objeto de identidade.
 pública std::string const & GetClientData() const  |  Obter os dados de cliente definido nas definições.
 SetClientData void público (const std::string & clientData)  |  Defina a cadeia de dados de cliente.
 pública std::string const & GetLocale() const  |  Obter a região definida nas definições.
SetCustomSettings void público (std::vector const < std::pair < std::string, std::string >> & customSettings)  |  Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
std::vector const pública < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
 SetSessionId void público (const std::string & sessionId)  |  Defina o id de sessão utilizado para telementry cliente definido.
 pública std::string const & GetSessionId() const  |  Obter o id de sessão, um identificador exclusivo.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Construir uma instância com parâmetros especificados. Utilize esta opção para criar [definições](class_mip_policyengine_settings.md) chamar LoadEngineAsync ao carregar o motor de uma existente.

Parâmetros:  
* **ID**: defini-lo para o id de motor exclusivo gerado pelo AddEngineAsync ou uma automática gerado. Quando carregar um motor existente a utilizar novamente o id ou um novo motor será criado. 


* **clientData**: dados de cliente personalizáveis que podem ser armazenados com o motor quando descarregado, pode ser obtido a partir de um motor de carregar. 


* **região**: saída localizável motor irá ser fornecida nesta região, predefinição "en-US".


  
### <a name="settings"></a>Definições
Utilize esta opção para criar [definições](class_mip_policyengine_settings.md) chamar AddEngineAsync para adicionar um novo motor.

Parâmetros:  
* **identidade**: Identificador exclusivo do utilizador para o qual o motor tem de ser adicionada. 


* **clientData**: dados de cliente personalizáveis que podem ser armazenados com o motor quando descarregado, pode ser obtido a partir de um motor de carregar. 


* **região**: saída localizável motor irá ser fornecida nesta região, predefinição "en-US".


  
### <a name="getid"></a>GetId
Obter o id de motor.

  
**Devolve**: uma cadeia exclusiva que identifica o motor.
  
### <a name="setid"></a>SetId
Defina o id de motor.

Parâmetros:  
* **ID**: id do motor.


  
### <a name="getidentity"></a>GetIdentity
Obter o objeto de identidade.

  
**Devolve**: um refrence para a identidade do objeto de definições. 
**Consulte também**: mip::Identity
  
### <a name="setidentity"></a>SetIdentity
Defina o objeto de identidade.

Parâmetros:  
* **identidade**: a identidade de um utilizador exclusiva. 


**Consulte também**: mip::Identity
  
### <a name="getclientdata"></a>GetClientData
Obter os dados de cliente definido nas definições.

  
**Devolve**: uma cadeia de dados especificados pelo cliente.
  
### <a name="setclientdata"></a>SetClientData
Defina a cadeia de dados de cliente.

Parâmetros:  
* **clientData**: o utilizador especificado dados.


  
### <a name="getlocale"></a>GetLocale
Obter a região definida nas definições.

  
**Devolve**: A região.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.

Parâmetros:  
* **customSettings**: lista de pares nome/valor.


  
### <a name="getcustomsettings"></a>GetCustomSettings
Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.

Parâmetros:  
* **Lista**: de pares nome/valor.


  
### <a name="setsessionid"></a>SetSessionId
Defina o id de sessão utilizado para telementry cliente definido.

Parâmetros:  
* **sessionId**: uma cadeia exclusiva que liga os eventos de telemetria.


  
### <a name="getsessionid"></a>GetSessionId
Obter o id de sessão, um identificador exclusivo.

  
**Devolve**: O id de sessão.