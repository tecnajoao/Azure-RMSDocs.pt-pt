---
title: classe mip FileEngine definições
description: Referência para a classe mip FileEngine definições
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 656ad1cf21a2d761dfb4c857b278b7421ee2b790
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446486"
---
# <a name="class-mipfileenginesettings"></a>classe mip::FileEngine::Settings 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de públicas (const Std:: String & engineId, const Std:: String & clientData, const Std:: String e Localidade)  |  [FileEngine::Settings](class_mip_fileengine_settings.md) construtor para carregar um motor de existente.
 Definições de públicas (const identidade e identidade, const Std:: String & clientData, const Std:: String e Localidade)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md) construtor para a criação de um novo mecanismo.
 público const Std:: String & GetEngineId() const  |  Devolve o ID do motor.
 Identidade de const pública e GetIdentity() const  |  Devolve o mecanismo de identidade.
 SetIdentity void pública (const identidade e de identidade)  |  Define a identidade do motor.
 público const Std:: String & GetClientData() const  |  Devolve os dados de cliente do motor.
 público const Std:: String & GetLocale() const  |  Devolva a Localidade do motor.
SetCustomSettings void pública (Std:: vector const < std::pair < Std:: String, Std:: String >> & valor)  |  Define uma lista de pares nome/valor utilizado para testar e experimentação.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetCustomSettings() const  |  Obtém uma lista de pares nome/valor utilizado para testar e experimentação.
 SetSessionId void pública (const Std:: String & sessionId)  |  Define o ID de sessão de motor.
 público const Std:: String & GetSessionId() const  |  Devolver o ID de sessão de motor.
 SetProtectionCloudEndpointBaseUrl void pública (const Std:: String & protectionCloudEndpointBaseUrl)  |  Define a proteção na nuvem base url de ponto final, utilizado para especificar o limite da cloud.
 público const Std:: String & GetProtectionCloudEndpointBaseUrl() const  |  Obtém o cloudEndpointBaseUrl.
 SetProtectionOnlyEngine void pública (const bool protectionOnly)  |  Não define o indicador de motor apenas proteção - nenhuma política/rótulo.
 bool const pública IsProtectionOnlyEngine() const  |  Não devolva o indicador de motor apenas proteção - nenhuma política/rótulo.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
[FileEngine::Settings](class_mip_fileengine_settings.md) construtor para carregar um motor de existente.

Parâmetros:  
* **engineId**: defina-o para o ID de mecanismo exclusivo gerado pelo AddEngineAsync. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade.


  
### <a name="settings"></a>Definições
[FileProfile::Settings](class_mip_fileprofile_settings.md) construtor para a criação de um novo mecanismo.

Parâmetros:  
* **identidade**: informações de identidade do utilizador associada com o novo mecanismo. 


* **clientData**: dados de cliente personalizável que podem ser armazenados com o mecanismo quando descarregadas, podem ser obtidos a partir de um mecanismo de carregá-lo. 


* **Localidade**: saída localizáveis do motor, será disponibilizada nessa localidade.


  
### <a name="getengineid"></a>GetEngineId
Devolve o ID do motor.
  
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
Define o ID de sessão de motor.
  
### <a name="getsessionid"></a>GetSessionId
Devolver o ID de sessão de motor.
  
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