---
title: classe mip::PolicyEngine::Settings
description: Documenta a classe mip::policyengine da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 6ad384768ef876109a6a43237765474345a666bc
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56257540"
---
# <a name="class-mippolicyenginesettings"></a>classe mip::PolicyEngine::Settings 
Especifica as definições associadas com uma [PolicyEngine](class_mip_policyengine.md).
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (Std:: String const & engineId, Std:: String const & clientData, Std:: String const & localidade, bool loadSensitivityTypes)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md) construtor para carregar um motor de existente.
Definições de públicas (const identidade & identidade, Std:: String const & clientData, Std:: String const & localidade, bool loadSensitivityTypes)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md) construtor para a criação de um novo mecanismo.
public const std::string& GetEngineId() const  |  Obter o ID do motor.
public void SetEngineId(const std::string& id)  |  Definir o ID do motor.
Identidade de const pública e GetIdentity() const  |  Obter o [identidade](class_mip_identity.md) objeto.
SetIdentity void pública (const identidade e de identidade)  |  Definir o [identidade](class_mip_identity.md) objeto.
public const std::string& GetClientData() const  |  Obter os dados de cliente definido nas definições.
SetClientData void pública (const Std:: String & clientData)  |  Defina a cadeia de dados do cliente.
public const std::string& GetLocale() const  |  Obtenha a região definida nas definições.
public void SetCustomSettings(const std::vector\<std::pair\<std::string, std::string\>\>& customSettings)  |  Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetCustomSettings() const  |  Obter as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.
public void SetSessionId(const std::string& sessionId)  |  Defina o ID de sessão utilizado para a telemetria de cliente definida.
public const std::string& GetSessionId() const  |  Obtenha o ID de sessão, um identificador exclusivo.
bool pública IsLoadSensitivityTypesEnabled() const  |  Obter o sinalizador que indica se as etiquetas de sensibilidade de carga está habilitado.
  
## <a name="members"></a>Membros
  
### <a name="settings-function"></a>Função de definições
[PolicyEngine::Settings](class_mip_policyengine_settings.md) construtor para carregar um motor de existente.

Parâmetros:  
* **engineId**: Defini-lo para o ID exclusivo do motor gerado por AddEngineAsync ou Self-gerado. Ao carregar um motor de existente, reutilize o ID de outro será criado um novo mecanismo. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade. 


* **Opcional**: sinalizador que indica quando o motor é carregado deve ser carregado também tipos de sensibilidade personalizada, se true OnPolicyChange observador no perfil será invocado as atualizações para os tipos de sensibilidade personalizada, bem como as alterações à política. se chamar ListSensitivityTypes falso devolverá sempre uma lista vazia.


  
### <a name="settings-function"></a>Função de definições
[PolicyEngine::Settings](class_mip_policyengine_settings.md) construtor para a criação de um novo mecanismo.

Parâmetros:  
* **identity**: [Identidade](class_mip_identity.md) informações do utilizador associada com o novo mecanismo. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade. 


* **Opcional**: sinalizador que indica quando o motor é carregado deve ser carregado também tipos de sensibilidade personalizada, se true OnPolicyChange observador no perfil será invocado as atualizações para os tipos de sensibilidade personalizada, bem como as alterações à política. se chamar ListSensitivityTypes falso devolverá sempre uma lista vazia.


  
### <a name="getengineid-function"></a>Função de GetEngineId
Obter o ID do motor.

  
**Devolve**: Uma cadeia exclusiva de identificar o motor.
  
### <a name="setengineid-function"></a>Função de SetEngineId
Definir o ID do motor.

Parâmetros:  
* **ID**: o motor de ID.


  
### <a name="getidentity-function"></a>Função de GetIdentity
Obter o [identidade](class_mip_identity.md) objeto.

  
**Devolve**: Uma referência para a identidade no objeto de definições. 
  
**Consulte também**: [mip::Identity](class_mip_identity.md)
  
### <a name="setidentity-function"></a>Função de SetIdentity
Definir o [identidade](class_mip_identity.md) objeto.

Parâmetros:  
* **identidade**: a identidade exclusiva de um utilizador. 


  
**Consulte também**: [mip::Identity](class_mip_identity.md)
  
### <a name="getclientdata-function"></a>Função de GetClientData
Obter os dados de cliente definido nas definições.

  
**Devolve**: Uma cadeia de caracteres de dados especificada pelo cliente.
  
### <a name="setclientdata-function"></a>Função de SetClientData
Defina a cadeia de dados do cliente.

Parâmetros:  
* **clientData**: especificadas pelo utilizador e dados.


  
### <a name="getlocale-function"></a>Função de GetLocale
Obtenha a região definida nas definições.

  
**Devolve**: A localidade.
  
### <a name="setcustomsettings-function"></a>Função de SetCustomSettings
Defina as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.

Parâmetros:  
* **customSettings**: Lista de pares nome/valor.


  
### <a name="getcustomsettings-function"></a>Função de GetCustomSettings
Obter as definições personalizadas, utilizadas para a funcionalidade de controlo e o teste.

  
**Devolve**: Lista de pares nome/valor.
  
### <a name="setsessionid-function"></a>Função de SetSessionId
Defina o ID de sessão utilizado para a telemetria de cliente definida.

Parâmetros:  
* **sessionId**: uma cadeia exclusiva que conecta eventos de telemetria.


  
### <a name="getsessionid-function"></a>Função de GetSessionId
Obtenha o ID de sessão, um identificador exclusivo.

  
**Devolve**: O ID de sessão.
  
### <a name="isloadsensitivitytypesenabled-function"></a>Função de IsLoadSensitivityTypesEnabled
Obter o sinalizador que indica se as etiquetas de sensibilidade de carga está habilitado.

  
**Devolve**: VERDADEIRO se estiver ativada outra false.
