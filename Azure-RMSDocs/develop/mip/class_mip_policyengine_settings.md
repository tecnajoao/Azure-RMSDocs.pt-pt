# <a name="class-mippolicyenginesettings"></a>classe mip::PolicyEngine::Settings 
Forneça uma instância desta classe com approprieted parâmetros devem ser para iniciar um motor.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública definições inline pública definições inline pública const std::string & GetId | Obter o id de motor. inline pública void SetId | Defina o id de motor. inline pública identidade const & GetIdentity | Obter o objeto de identidade.
inline pública void SetIdentity | Defina o objeto de identidade.
std::string const inline pública & GetClientData | Obter os dados de cliente definido nas definições.
inline pública void SetClientData | Defina a cadeia de dados de cliente.
std::string const inline pública & GetLocale | Obter a região definida nas definições.
inline pública void SetCustomSettings | Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
inline pública const std::vector < std::pair < std::string, std::string >> & GetCustomSettings | Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
inline pública void SetSessionId | Defina o id de sessão utilizado para telementry cliente definido.
std::string const inline pública & GetSessionId | Obter o id de sessão, um identificador exclusivo.
## <a name="members"></a>Membros
### <a name="settings"></a>Definições
Construir uma instância com parâmetros especificados. Utilize esta opção para criar [definições](#classmip_1_1_policy_engine_1_1_settings) chamar LoadEngineAsync ao carregar o motor de uma existente.
#### <a name="parameters"></a>Parâmetros
* ID de defini-lo para o id de motor exclusivo gerado pelo AddEngineAsync ou um automática gerado. Quando carregar um motor existente a utilizar novamente o id ou um novo motor será criado. 
* dados de cliente personalizável do clientData que podem ser armazenados com o motor quando descarregado, pode ser obtido a partir de um motor de carregar. 
* saída de localizável de motor de região irá ser fornecida nesta região, predefinição "en-US".
### <a name="settings"></a>Definições
Utilize esta opção para criar [definições](#classmip_1_1_policy_engine_1_1_settings) chamar AddEngineAsync para adicionar um novo motor.
#### <a name="parameters"></a>Parâmetros
* Identificador exclusivo de identidade do utilizador para o qual o motor tem de ser adicionada. 
* dados de cliente personalizável do clientData que podem ser armazenados com o motor quando descarregado, pode ser obtido a partir de um motor de carregar. 
* saída de localizável de motor de região irá ser fornecida nesta região, predefinição "en-US".
### <a name="getid"></a>GetId
Obter o id de motor.
#### <a name="returns"></a>Devolve
uma cadeia exclusiva que identifica o motor.
### <a name="setid"></a>SetId
Defina o id de motor.
#### <a name="parameters"></a>Parâmetros
* id do motor de ID.
### <a name="getidentity"></a>GetIdentity
Obter o objeto de identidade.
#### <a name="returns"></a>Devolve
um refrence para a identidade do objeto de definições. 
**Consulte também**: mip::Identity
### <a name="setidentity"></a>SetIdentity
Defina o objeto de identidade.
#### <a name="parameters"></a>Parâmetros
* identidade a identidade de um utilizador exclusiva. 
**Consulte também**: mip::Identity
### <a name="getclientdata"></a>GetClientData
Obter os dados de cliente definido nas definições.
#### <a name="returns"></a>Devolve
uma cadeia de dados especificados pelo cliente.
### <a name="setclientdata"></a>SetClientData
Defina a cadeia de dados de cliente.
#### <a name="parameters"></a>Parâmetros
* o utilizador de clientData especificado dados.
### <a name="getlocale"></a>GetLocale
Obter a região definida nas definições.
#### <a name="returns"></a>Devolve
a região.
### <a name="setcustomsettings"></a>SetCustomSettings
Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
#### <a name="parameters"></a>Parâmetros
* customSettings lista de pares nome/valor.
### <a name="getcustomsettings"></a>GetCustomSettings
Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
#### <a name="parameters"></a>Parâmetros
* Lista de pares nome/valor.
### <a name="setsessionid"></a>SetSessionId
Defina o id de sessão utilizado para telementry cliente definido.
#### <a name="parameters"></a>Parâmetros
* uma cadeia exclusiva que liga os eventos de telemetria de sessionId.
### <a name="getsessionid"></a>GetSessionId
Obter o id de sessão, um identificador exclusivo.
#### <a name="returns"></a>Devolve
o id de sessão.