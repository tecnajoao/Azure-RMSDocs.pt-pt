---
title: classe mip::FileEngine::Settings
description: Documenta a classe mip::fileengine da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 2481ee7d42f00ce5b33529b15e17b22ba6556b0e
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574045"
---
# <a name="class-mipfileenginesettings"></a>classe mip::FileEngine::Settings 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (Std:: String const & engineId, Std:: String const & clientData, Std:: String const & localidade, bool loadSensitivityTypes)  |  [FileEngine::Settings](class_mip_fileengine_settings.md) construtor para carregar um motor de existente.
Definições de públicas (const identidade & identidade, Std:: String const & clientData, Std:: String const & localidade, bool loadSensitivityTypes)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md) construtor para a criação de um novo mecanismo.
public const std::string& GetEngineId() const  |  Devolve o ID do motor.
public void SetEngineId(const std::string& id)  |  Definir o ID do motor.
Identidade de const pública e GetIdentity() const  |  Devolve o mecanismo [identidade](class_mip_identity.md).
SetIdentity void pública (const identidade e de identidade)  |  Define a identidade do motor.
public const std::string& GetClientData() const  |  Devolve os dados de cliente do motor.
public const std::string& GetLocale() const  |  Devolva a Localidade do motor.
public void SetCustomSettings(const std::vector\<std::pair\<std::string, std::string\>\>& value)  |  Define uma lista de pares nome/valor utilizado para testar e experimentação.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetCustomSettings() const  |  Obtém uma lista de pares nome/valor utilizado para testar e experimentação.
public void SetSessionId(const std::string& sessionId)  |  Define o ID de sessão de motor.
public const std::string& GetSessionId() const  |  Devolver o ID de sessão de motor.
SetProtectionCloudEndpointBaseUrl void pública (const Std:: String & protectionCloudEndpointBaseUrl)  |  Define a proteção na nuvem base url de ponto final, utilizado para especificar o limite da cloud.
public const std::string& GetProtectionCloudEndpointBaseUrl() const  |  Obtém o url de base do ponto final de cloud de proteção.
SetPolicyCloudEndpointBaseUrl void pública (const Std:: String & policyCloudEndpointBaseUrl)  |  Define a política cloud base url de ponto final, utilizado para especificar o limite da cloud.
public const std::string& GetPolicyCloudEndpointBaseUrl() const  |  Obtém o url de base do ponto final de cloud de política.
SetProtectionOnlyEngine void pública (const bool protectionOnly)  |  Não define o indicador de motor apenas proteção - nenhuma política/rótulo.
bool const pública IsProtectionOnlyEngine() const  |  Não devolva o indicador de motor apenas proteção - nenhuma política/rótulo.
bool pública IsLoadSensitivityTypesEnabled() const  |  Obter o sinalizador que indica se as etiquetas de sensibilidade de carga está habilitado.
  
## <a name="members"></a>Membros
  
### <a name="settings-function"></a>Função de definições
[FileEngine::Settings](class_mip_fileengine_settings.md) construtor para carregar um motor de existente.

Parâmetros:  
* **engineId**: Defini-lo para o ID de mecanismo exclusivo gerado pelo AddEngineAsync. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade. 


* **loadSensitivityTypes**: Sinalizador opcional que indica quando o motor é carregado deve carregar tipos de sensibilidade personalizada, também, se true OnPolicyChange observador no perfil será invocado as atualizações para os tipos de sensibilidade personalizada, bem como as alterações à política. se chamar ListSensitivityTypes falso devolverá sempre uma lista vazia.


  
### <a name="settings-function"></a>Função de definições
[FileProfile::Settings](class_mip_fileprofile_settings.md) construtor para a criação de um novo mecanismo.

Parâmetros:  
* **identity**: [Identidade](class_mip_identity.md) informações do utilizador associada com o novo mecanismo. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade. 


* **loadSensitivityTypes**: Sinalizador opcional que indica quando o motor é carregado deve carregar tipos de sensibilidade personalizada, também, se true OnPolicyChange observador no perfil será invocado as atualizações para os tipos de sensibilidade personalizada, bem como as alterações à política. se chamar ListSensitivityTypes falso devolverá sempre uma lista vazia.


  
### <a name="getengineid-function"></a>Função de GetEngineId
Devolve o ID do motor.
  
### <a name="setengineid-function"></a>Função de SetEngineId
Definir o ID do motor.

Parâmetros:  
* **ID**: o motor de ID.


  
### <a name="getidentity-function"></a>Função de GetIdentity
Devolve o mecanismo [identidade](class_mip_identity.md).
  
### <a name="setidentity-function"></a>Função de SetIdentity
Define a identidade do motor.
  
### <a name="getclientdata-function"></a>Função de GetClientData
Devolve os dados de cliente do motor.
  
### <a name="getlocale-function"></a>Função de GetLocale
Devolva a Localidade do motor.
  
### <a name="setcustomsettings-function"></a>Função de SetCustomSettings
Define uma lista de pares nome/valor utilizado para testar e experimentação.
  
### <a name="getcustomsettings-function"></a>Função de GetCustomSettings
Obtém uma lista de pares nome/valor utilizado para testar e experimentação.
  
### <a name="setsessionid-function"></a>Função de SetSessionId
Define o ID de sessão de motor.
  
### <a name="getsessionid-function"></a>Função de GetSessionId
Devolver o ID de sessão de motor.
  
### <a name="setprotectioncloudendpointbaseurl-function"></a>SetProtectionCloudEndpointBaseUrl function
Define a proteção na nuvem base url de ponto final, utilizado para especificar o limite da cloud.

Parâmetros:  
* **protectionCloudEndpointBaseUrl**: Url de base associados com pontos finais de proteção


  
### <a name="getprotectioncloudendpointbaseurl-function"></a>GetProtectionCloudEndpointBaseUrl function
Obtém o url de base do ponto final de cloud de proteção.

  
**Devolve**: Url de base associados com pontos finais de proteção
  
### <a name="setpolicycloudendpointbaseurl-function"></a>Função de SetPolicyCloudEndpointBaseUrl
Define a política cloud base url de ponto final, utilizado para especificar o limite da cloud.

Parâmetros:  
* **policyCloudEndpointBaseUrl**: Url de base associados com pontos finais de política


  
### <a name="getpolicycloudendpointbaseurl-function"></a>GetPolicyCloudEndpointBaseUrl function
Obtém o url de base do ponto final de cloud de política.

  
**Devolve**: Url de base associados com pontos finais de política
  
### <a name="setprotectiononlyengine-function"></a>Função de SetProtectionOnlyEngine
Não define o indicador de motor apenas proteção - nenhuma política/rótulo.
  
### <a name="isprotectiononlyengine-function"></a>Função de IsProtectionOnlyEngine
Não devolva o indicador de motor apenas proteção - nenhuma política/rótulo.
  
### <a name="isloadsensitivitytypesenabled-function"></a>Função de IsLoadSensitivityTypesEnabled
Obter o sinalizador que indica se as etiquetas de sensibilidade de carga está habilitado.

  
**Devolve**: VERDADEIRO se estiver ativada outra false.