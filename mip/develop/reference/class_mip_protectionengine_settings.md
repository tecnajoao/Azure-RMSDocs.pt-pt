---
title: classe mip ProtectionEngine definições
description: Referência para a classe mip ProtectionEngine definições
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f61e86a87ecfea21bc9d02f4e55f3fbe663e9b80
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446707"
---
# <a name="class-mipprotectionenginesettings"></a>classe mip::ProtectionEngine::Settings 
[As definições](class_mip_protectionengine_settings.md) utilizada pelo [ProtectionEngine](class_mip_protectionengine.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de públicas (const identidade e identidade, const Std:: String & clientData, const Std:: String e Localidade)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para a criação de um novo mecanismo.
 Definições de públicas (const Std:: String & engineId, const Std:: String & clientData, const Std:: String e Localidade)  |  [ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para carregar um motor de existente.
 público const Std:: String & GetEngineId() const  |  Obtém o ID do motor.
 SetEngineId void pública (const Std:: String & engineId)  |  Define o ID do motor.
 Identidade de const pública e GetIdentity() const  |  Obtém o usuário que identidade associada com o motor.
 SetIdentity void pública (const identidade e de identidade)  |  Define o usuário que identidade associada com o motor.
 público const Std:: String & GetClientData() const  |  Obtém dados personalizados especificados pelo cliente.
 SetClientData void pública (const Std:: String & clientData)  |  Conjuntos de dados personalizados especificados pelo cliente.
 público const Std:: String & GetLocale() const  |  Obtém a localidade no mecanismo de qual dados serão escritos.
SetCustomSettings void pública (Std:: vector const < std::pair < Std:: String, Std:: String >> & valor)  |  Conjuntos de pares nome/valor utilizados para testar e experimentação.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetCustomSettings() const  |  Obtém pares nome/valor utilizados para testar e experimentação.
 SetSessionId void pública (const Std:: String & sessionId)  |  Define o ID de sessão do mecanismo, utilizado para a correlação de registo ou de telemetria.
 público const Std:: String & GetSessionId() const  |  Obtém o ID de sessão de motor.
 SetCloudEndpointBaseUrl void pública (const Std:: String & cloudEndpointBaseUrl)  |  Opcionalmente, define o URL base do ponto final de cloud.
 público const Std:: String & GetCloudEndpointBaseUrl() const  |  Obtém o URL de base da cloud utilizado por todos os pedidos de serviço, se for especificado.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para a criação de um novo mecanismo.

Parâmetros:  
* **identidade**: identidade, que será associada [ProtectionEngine](class_mip_protectionengine.md)


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas e podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída motor será fornecida nesta região.


  
### <a name="settings"></a>Definições
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md) construtor para carregar um motor de existente.

Parâmetros:  
* **engineId**: um identificador exclusivo do motor que será carregado 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas e podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída motor será fornecida nesta região.


  
### <a name="getengineid"></a>GetEngineId
Obtém o ID do motor.

  
**Devolve**: ID do motor
  
### <a name="setengineid"></a>SetEngineId
Define o ID do motor.

Parâmetros:  
* **engineId**: o motor de ID.


  
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
  
### <a name="setclientdata"></a>SetClientData
Conjuntos de dados personalizados especificados pelo cliente.

Parâmetros:  
* **Custom**: dados especificados pelo cliente


  
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
Define o ID de sessão do mecanismo, utilizado para a correlação de registo ou de telemetria.

Parâmetros:  
* **sessionId**: ID de sessão, para a correlação de registo ou de telemetria do motor


  
### <a name="getsessionid"></a>GetSessionId
Obtém o ID de sessão de motor.

  
**Devolve**: o motor de identificação da sessão
  
### <a name="setcloudendpointbaseurl"></a>SetCloudEndpointBaseUrl
Opcionalmente, define o URL base do ponto final de cloud.

Parâmetros:  
* **cloudEndpointBaseUrl**: o URL de base utilizado por todos os pedidos de serviço (por exemplo, "https://api.aadrm.com")


Se o base URL não for especificado, será determinada por meio de pesquisa de DNS de domínio a identidade de motor.
  
### <a name="getcloudendpointbaseurl"></a>GetCloudEndpointBaseUrl
Obtém o URL de base da cloud utilizado por todos os pedidos de serviço, se for especificado.

  
**Devolve**: URL de Base