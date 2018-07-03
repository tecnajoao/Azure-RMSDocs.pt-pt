# <a name="class-mipfileenginesettings"></a>classe mip::FileEngine::Settings 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de públicas (const Std:: String & engineId, const Std:: String & clientData, const Std:: String e Localidade)  |  Cria uma instância com os parâmetros especificados.
 Definições de públicas (const identidade e identidade, const Std:: String & clientData, const Std:: String e Localidade)  |  Cria uma instância com os parâmetros especificados.
 público const Std:: String & GetEngineId() const  |  Devolve o mecanismo de ID.
 Identidade de const pública e GetIdentity() const  |  Devolve o mecanismo de identidade.
 SetIdentity void pública (const identidade e de identidade)  |  Define a identidade do motor.
 público const Std:: String & GetClientData() const  |  Devolve os dados de cliente do motor.
 público const Std:: String & GetLocale() const  |  Devolva a Localidade do motor.
SetCustomSettings void pública (Std:: vector const < std::pair < Std:: String, Std:: String >> & valor)  |  Define uma lista de pares nome/valor utilizado para testar e experimentação.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetCustomSettings() const  |  Obtém uma lista de pares nome/valor utilizado para testar e experimentação.
 SetSessionId void pública (const Std:: String & sessionId)  |  Define o id de sessão do motor.
 público const Std:: String & GetSessionId() const  |  Devolva o id de sessão do motor.
 SetProtectionCloudEndpointBaseUrl void pública (const Std:: String & protectionCloudEndpointBaseUrl)  |  Define a proteção na nuvem base url de ponto final, utilizado para especificar o limite da cloud.
 público const Std:: String & GetProtectionCloudEndpointBaseUrl() const  |  Obtém o cloudEndpointBaseUrl.
 SetProtectionOnlyEngine void pública (const bool protectionOnly)  |  Não define o indicador de motor apenas proteção - nenhuma política/rótulo.
 bool const pública IsProtectionOnlyEngine() const  |  Não devolva o indicador de motor apenas proteção - nenhuma política/rótulo.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Cria uma instância com os parâmetros especificados.
Utilize esta opção para criar [definições](class_mip_fileengine_settings.md) chamar LoadEngineAsync para carregar um motor existente (anteriormente adicionado por meio de AddEngineAsync).

Parâmetros:  
* **engineId**: defina-o para o id de mecanismo exclusivo gerado pelo AddEngineAsync.


  
### <a name="settings"></a>Definições
Cria uma instância com os parâmetros especificados.
Utilize esta opção para criar [definições](class_mip_fileengine_settings.md) AddEngineAsync para adicionar um novo mecanismo de chamar.

Parâmetros:  
* **identidade**: informações de identidade do utilizador para quem o mecanismo de tem de ser adicionada.


  
### <a name="getengineid"></a>GetEngineId
Devolve o mecanismo de ID.
  
### <a name="getidentity"></a>GetIdentity
Devolve o mecanismo de identidade.
  
### <a name="setidentity"></a>SetIdentity
Define a identidade do motor.
  
### <a name="getclientdata"></a>GetClientData
Devolve os dados de cliente do motor.
  
### <a name="getlocale"></a>GetLocale
Devolva a Localidade do motor.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Define uma lista de pares nome/valor utilizado para testar e experimentação.
  
### <a name="getcustomsettings"></a>GetCustomSettings
Obtém uma lista de pares nome/valor utilizado para testar e experimentação.
  
### <a name="setsessionid"></a>SetSessionId
Define o id de sessão do motor.
  
### <a name="getsessionid"></a>GetSessionId
Devolva o id de sessão do motor.
  
### <a name="setprotectioncloudendpointbaseurl"></a>SetProtectionCloudEndpointBaseUrl
Define a proteção na nuvem base url de ponto final, utilizado para especificar o limite da cloud.

Parâmetros:  
* **protectionCloudEndpointBaseUrl**: url associado a pontos finais de proteção de Base


  
### <a name="getprotectioncloudendpointbaseurl"></a>GetProtectionCloudEndpointBaseUrl
Obtém o cloudEndpointBaseUrl.

  
**Devolve**: url associado a pontos finais de proteção de Base
  
### <a name="setprotectiononlyengine"></a>SetProtectionOnlyEngine
Não define o indicador de motor apenas proteção - nenhuma política/rótulo.
  
### <a name="isprotectiononlyengine"></a>IsProtectionOnlyEngine
Não devolva o indicador de motor apenas proteção - nenhuma política/rótulo.