---
title: classe mip PolicyEngine definições
description: Referência para a classe mip PolicyEngine definições
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6ac94d1e34615a0248dac85f28c55154b127574f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446350"
---
# <a name="class-mippolicyenginesettings"></a>classe mip::PolicyEngine::Settings 
Especifica as definições associadas com uma [PolicyEngine](class_mip_policyengine.md).
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de públicas (const Std:: String & engineId, const Std:: String & clientData, const Std:: String e Localidade)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md) construtor para carregar um motor de existente.
 Definições de públicas (const identidade e identidade, const Std:: String & clientData, const Std:: String e Localidade)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md) construtor para a criação de um novo mecanismo.
 público const Std:: String & GetEngineId() const  |  Obter o ID do motor.
 SetEngineId void pública (const Std:: String & id)  |  Definir o ID do motor.
 Identidade de const pública e GetIdentity() const  |  Obtenha o objeto de identidade.
 SetIdentity void pública (const identidade e de identidade)  |  Defina o objeto de identidade.
 público const Std:: String & GetClientData() const  |  Obter os dados de cliente definido nas definições.
 SetClientData void pública (const Std:: String & clientData)  |  Defina a cadeia de dados do cliente.
 público const Std:: String & GetLocale() const  |  Obtenha a região definida nas definições.
SetCustomSettings void pública (Std:: vector const < std::pair < Std:: String, Std:: String >> & customSettings)  |  Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetCustomSettings() const  |  Obter as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
 SetSessionId void pública (const Std:: String & sessionId)  |  Defina o ID de sessão utilizado para a telemetria de cliente definida.
 público const Std:: String & GetSessionId() const  |  Obtenha o ID de sessão, um identificador exclusivo.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
[PolicyEngine::Settings](class_mip_policyengine_settings.md) construtor para carregar um motor de existente.

Parâmetros:  
* **engineId**: configurá-lo para o ID de mecanismo exclusivo gerado pelo AddEngineAsync ou Self-gerado. Ao carregar um motor de existente, reutilize o ID de outro será criado um novo mecanismo. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade.


  
### <a name="settings"></a>Definições
[PolicyEngine::Settings](class_mip_policyengine_settings.md) construtor para a criação de um novo mecanismo.

Parâmetros:  
* **identidade**: informações de identidade do utilizador associada com o novo mecanismo. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade.


  
### <a name="getengineid"></a>GetEngineId
Obter o ID do motor.

  
**Devolve**: uma cadeia exclusiva de identificar o motor.
  
### <a name="setengineid"></a>SetEngineId
Definir o ID do motor.

Parâmetros:  
* **ID**: o motor de ID.


  
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
Defina o ID de sessão utilizado para a telemetria de cliente definida.

Parâmetros:  
* **sessionId**: uma cadeia exclusiva que conecta eventos de telemetria.


  
### <a name="getsessionid"></a>GetSessionId
Obtenha o ID de sessão, um identificador exclusivo.

  
**Devolve**: O ID de sessão.