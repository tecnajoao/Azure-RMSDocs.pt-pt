# <a name="class-mipfileenginesettings"></a>classe mip::FileEngine::Settings 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública definições (const std::string & id, const std::string & clientData, const std::string & região)  |  Cria uma instância com parâmetros especificados.
inline pública definições (const identidade & identidade, const std::string & clientData, const std::string e região)  |  Cria uma instância com parâmetros especificados.
std::string const inline pública & GetId() const  |  Devolve o motor de ID.
inline pública identidade const & GetIdentity() const  |  Devolve o motor de identidade.
inline pública void SetIdentity (const identidade e de identidade)  |  Define a identidade do motor.
std::string const inline pública & GetClientData() const  |  Devolve os dados de cliente do motor.
std::string const inline pública & GetLocale() const  |  Devolva a região de motor.
inline pública void SetCustomSettings (std::vector const < std::pair < std::string, std::string >> & valor)  |  Define uma lista de pares nome/valor utilizado para testar e experimentação.
inline pública const std::vector < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Obtém uma lista de pares nome/valor utilizado para testar e experimentação.
inline pública void SetSessionId (const std::string & sessionId)  |  Define o id de sessão do motor.
std::string const inline pública & GetSessionId() const  |  Devolva o id de sessão do motor.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Cria uma instância com parâmetros especificados.
Utilize esta opção para criar [definições](#classmip_1_1_file_engine_1_1_settings) chamar LoadEngineAsync para carregar um motor existente (anteriormente adicionado através de AddEngineAsync).
  
#### <a name="parameters"></a>Parâmetros
* ID de defini-lo para o id de motor exclusivo gerado pelo AddEngineAsync.
  
### <a name="settings"></a>Definições
Cria uma instância com parâmetros especificados.
Utilize esta opção para criar [definições](#classmip_1_1_file_engine_1_1_settings) chamar AddEngineAsync para adicionar um novo motor.
  
#### <a name="parameters"></a>Parâmetros
* informações de identidade de identidade do utilizador para o qual o motor tem de ser adicionada.
  
### <a name="getid"></a>GetId
Devolve o motor de ID.
  
### <a name="getidentity"></a>GetIdentity
Devolve o motor de identidade.
  
### <a name="setidentity"></a>SetIdentity
Define a identidade do motor.
  
### <a name="getclientdata"></a>GetClientData
Devolve os dados de cliente do motor.
  
### <a name="getlocale"></a>GetLocale
Devolva a região de motor.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Define uma lista de pares nome/valor utilizado para testar e experimentação.
  
### <a name="getcustomsettings"></a>GetCustomSettings
Obtém uma lista de pares nome/valor utilizado para testar e experimentação.
  
### <a name="setsessionid"></a>SetSessionId
Define o id de sessão do motor.
  
### <a name="getsessionid"></a>GetSessionId
Devolva o id de sessão do motor.