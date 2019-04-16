---
title: classe mip::ProtectionEngine::Settings
description: Documenta a classe mip::protectionengine da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 841eddc32e5e6928469dc11aba581defae09bc09
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574011"
---
# <a name="class-mipprotectionenginesettings"></a>classe mip::ProtectionEngine::Settings 
[As definições](class_mip_protectionengine_settings.md) utilizada pelo [ProtectionEngine](class_mip_protectionengine.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (const identidade e identidade, const Std:: String & clientData, const Std:: String e Localidade)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para a criação de um novo mecanismo.
Definições de públicas (const Std:: String & engineId, const Std:: String & clientData, const Std:: String e Localidade)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para carregar um motor de existente.
public const std::string& GetEngineId() const  |  Obtém o ID do motor.
SetEngineId void pública (const Std:: String & engineId)  |  Define o ID do motor.
Identidade de const pública e GetIdentity() const  |  Obtém o usuário [identidade](class_mip_identity.md) associados com o motor.
SetIdentity void pública (const identidade e de identidade)  |  Define o usuário [identidade](class_mip_identity.md) associados com o motor.
public const std::string& GetClientData() const  |  Obtém dados personalizados especificados pelo cliente.
SetClientData void pública (const Std:: String & clientData)  |  Conjuntos de dados personalizados especificados pelo cliente.
public const std::string& GetLocale() const  |  Obtém a localidade no mecanismo de qual dados serão escritos.
public void SetCustomSettings(const std::vector\<std::pair\<std::string, std::string\>\>& value)  |  Conjuntos de pares nome/valor utilizados para testar e experimentação.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetCustomSettings() const  |  Obtém pares nome/valor utilizados para testar e experimentação.
public void SetSessionId(const std::string& sessionId)  |  Define o ID de sessão do mecanismo, utilizado para a correlação de registo ou de telemetria.
public const std::string& GetSessionId() const  |  Obtém o ID de sessão de motor.
public void SetCloudEndpointBaseUrl(const std::string& cloudEndpointBaseUrl)  |  Opcionalmente, define o URL base do ponto final de cloud.
public const std::string& GetCloudEndpointBaseUrl() const  |  Obtém o URL de base da cloud utilizado por todos os pedidos de serviço, se for especificado.
  
## <a name="members"></a>Membros
  
### <a name="settings-function"></a>Função de definições
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para a criação de um novo mecanismo.

Parâmetros:  
* **identity**: [Identidade](class_mip_identity.md) que será associado [ProtectionEngine](class_mip_protectionengine.md)


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas e podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **locale**: Saída de motor será fornecida nesta região.


  
### <a name="settings-function"></a>Função de definições
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para carregar um motor de existente.

Parâmetros:  
* **engineId**: Identificador exclusivo do motor que será carregado 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas e podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **locale**: Saída de motor será fornecida nesta região.


  
### <a name="getengineid-function"></a>Função de GetEngineId
Obtém o ID do motor.

  
**Devolve**: ID do motor
  
### <a name="setengineid-function"></a>Função de SetEngineId
Define o ID do motor.

Parâmetros:  
* **engineId**: o motor de ID.


  
### <a name="getidentity-function"></a>Função de GetIdentity
Obtém o usuário [identidade](class_mip_identity.md) associados com o motor.

  
**Devolve**: Usuário [identidade](class_mip_identity.md) associados com o mecanismo de
  
### <a name="setidentity-function"></a>Função de SetIdentity
Define o usuário [identidade](class_mip_identity.md) associados com o motor.

Parâmetros:  
* **identity**: Usuário [identidade](class_mip_identity.md) associados com o mecanismo de


  
### <a name="getclientdata-function"></a>Função de GetClientData
Obtém dados personalizados especificados pelo cliente.

  
**Devolve**: Dados personalizados especificados pelo cliente
  
### <a name="setclientdata-function"></a>Função de SetClientData
Conjuntos de dados personalizados especificados pelo cliente.

Parâmetros:  
* **Custom**: dados especificados pelo cliente


  
### <a name="getlocale-function"></a>Função de GetLocale
Obtém a localidade no mecanismo de qual dados serão escritos.

  
**Devolve**: Localidade no mecanismo de qual dados serão escritos
  
### <a name="setcustomsettings-function"></a>Função de SetCustomSettings
Conjuntos de pares nome/valor utilizados para testar e experimentação.

Parâmetros:  
* **customSettings**: Utilizado para testar e experimentação de pares nome/valor


  
### <a name="getcustomsettings-function"></a>Função de GetCustomSettings
Obtém pares nome/valor utilizados para testar e experimentação.

  
**Devolve**: Utilizado para testar e experimentação de pares nome/valor
  
### <a name="setsessionid-function"></a>Função de SetSessionId
Define o ID de sessão do mecanismo, utilizado para a correlação de registo ou de telemetria.

Parâmetros:  
* **sessionId**: ID de sessão do mecanismo, utilizado para a correlação de registo/telemetria


  
### <a name="getsessionid-function"></a>Função de GetSessionId
Obtém o ID de sessão de motor.

  
**Devolve**: ID de sessão do motor
  
### <a name="setcloudendpointbaseurl-function"></a>SetCloudEndpointBaseUrl function
Opcionalmente, define o URL base do ponto final de cloud.

Parâmetros:  
* **cloudEndpointBaseUrl**: o URL de base utilizado por todos os pedidos de serviço (por exemplo, "https://api.aadrm.com")


Se o base URL não for especificado, será determinada por meio de pesquisa de DNS de domínio a identidade de motor.
  
### <a name="getcloudendpointbaseurl-function"></a>GetCloudEndpointBaseUrl function
Obtém o URL de base da cloud utilizado por todos os pedidos de serviço, se for especificado.

  
**Devolve**: URL de base