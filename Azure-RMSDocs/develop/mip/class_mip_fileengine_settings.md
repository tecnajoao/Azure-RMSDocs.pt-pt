# <a name="class-mipfileenginesettings"></a>classe mip::FileEngine::Settings 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de público (const std::string & id, const std::string & clientData, const std::string & região)  |  Cria uma instância com parâmetros especificados.
 Definições de público (const identidade & identidade, const std::string & clientData, const std::string e região)  |  Cria uma instância com parâmetros especificados.
 pública std::string const & GetId() const  |  Devolve o motor de ID.
 Identidade const pública & GetIdentity() const  |  Devolve o motor de identidade.
 SetIdentity void público (const identidade e de identidade)  |  Define a identidade do motor.
 pública std::string const & GetClientData() const  |  Devolve os dados de cliente do motor.
 pública std::string const & GetLocale() const  |  Devolva a região de motor.
SetCustomSettings void público (std::vector const < std::pair < std::string, std::string >> & valor)  |  Define uma lista de pares nome/valor utilizado para testar e experimentação.
std::vector const pública < std::pair < std::string, std::string >> & GetCustomSettings() const  |  Obtém uma lista de pares nome/valor utilizado para testar e experimentação.
 SetSessionId void público (const std::string & sessionId)  |  Define o id de sessão do motor.
 pública std::string const & GetSessionId() const  |  Devolva o id de sessão do motor.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Cria uma instância com parâmetros especificados.
Utilize esta opção para criar [definições](class_mip_fileengine_settings.md) chamar LoadEngineAsync para carregar um motor existente (anteriormente adicionado através de AddEngineAsync).

Parâmetros:  
* **ID**: defina-o para o id de motor exclusivo gerado pelo AddEngineAsync.


  
### <a name="settings"></a>Definições
Cria uma instância com parâmetros especificados.
Utilize esta opção para criar [definições](class_mip_fileengine_settings.md) chamar AddEngineAsync para adicionar um novo motor.

Parâmetros:  
* **identidade**: informações de identidade do utilizador para o qual o motor tem de ser adicionada.


  
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