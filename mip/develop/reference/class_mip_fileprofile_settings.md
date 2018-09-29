---
title: classe mip FileProfile definições
description: Referência para a classe mip FileProfile definições
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 4b79d8eb75a54a56f1b3e48645bdd5eec0afaa19
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446384"
---
# <a name="class-mipfileprofilesettings"></a>classe mip::FileProfile::Settings 
[As definições](class_mip_fileprofile_settings.md) utilizada pelo [FileProfile](class_mip_fileprofile.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (const std::shared_ptr Std:: String & caminho, bool useInMemoryStorage,<AuthDelegate> authDelegate, std::shared_ptr<ConsentDelegate> consentDelegate, std::shared_ptr<Observer> observador, const ApplicationInfo & applicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md) construtor.
 público const Std:: String & GetPath() const  |  Obtém o caminho em que o registo, telemetria, e outro estado persistente é armazenado.
 bool pública GetUseInMemoryStorage() const  |  Obtém se todos os Estados devem ser armazenados na memória (em vez de no disco)
público std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.
público std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Obtém o delegado de autorização utilizado para pedir consentimento do utilizador se ligam a serviços.
público std::shared_ptr<Observer> GetObserver() const  |  Obtém o observador que recebe notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md).
 público GetApplicationInfo() const ApplicationInfo const  |  Obtém as informações sobre a aplicação que está a consumir o SDK.
 bool pública GetSkipTelemetryInit() const  |  Obtém se deve ser ignorada a inicialização de telemetria ou não.
 público SetSkipTelemetryInit() void  |  Desativa a inicialização de telemetria.
 público SetNewFeaturesDisabled() void  |  Desativa a novos recursos.
 bool pública AreNewFeaturesDisabled() const  |  Obtém se novos recursos estão desativados ou não.
público std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.
SetLoggerDelegate void pública (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Substitua o agente de log padrão.
público std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Obtenha o delegado HTTP (se houver) fornecido pela aplicação.
SetHttpDelegate void pública (const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Substitua a pilha HTTP padrão do cliente.
 público OptOutTelemetry() void  |  Opta ativamente por toda a telemetria de recolha.
 bool pública IsTelemetryOptedOut() const  |  Obtém se telemetria recolha deve ser desabilitada ou não.
 SetSessionId void pública (const Std:: String & sessionId)  |  Define o ID de sessão.
 público const Std:: String & GetSessionId() const  |  Obtém o ID de sessão.
 SetMinimumLogLevel void pública (LogLevel logLevel)  |  Defina o nível de registo mais baixo que irão acionar um evento de log.
 público GetMinimumLogLevel() de LogLevel const  |  Obtenha o nível de registo mais baixo que irão acionar um evento de log.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
[FileProfile::Settings](class_mip_fileprofile_settings.md) construtor.

Parâmetros:  
* **caminho**: caminho de ficheiro em que o registo, telemetria e outras estado persistente é armazenado 


* **useInMemoryStorage**: true se todos os Estados devem ser armazenados na memória, false se o estado pode ser colocado em cache em disco 


* **authDelegate**: delegado de autenticação utilizado para aquisição de tokens de autenticação 


* **observador**: [observador](class_mip_fileprofile_observer.md) instância que irá receber notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md)


* **applicationInfo**: informações sobre a aplicação que está a consumir o SDK


  
### <a name="getpath"></a>GetPath
Obtém o caminho em que o registo, telemetria, e outro estado persistente é armazenado.

  
**Devolve**: caminho em que o registo, telemetria e outras estado persistente é armazenado
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Obtém se todos os Estados devem ser armazenados na memória (em vez de no disco)

  
**Devolve**: se todos os Estados devem ser armazenados na memória (em vez de no disco)
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.

  
**Devolve**: delegado de autenticação utilizado para aquisição de tokens de autenticação
  
### <a name="consentdelegate"></a>ConsentDelegate
Obtém o delegado de autorização utilizado para pedir consentimento do utilizador se ligam a serviços.

  
**Devolve**: delegado de autorização utilizado para pedir o consentimento do utilizador
  
### <a name="observer"></a>Observador
Obtém o observador que recebe notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md).

  
**Devolve**: [observador](class_mip_fileprofile_observer.md) que recebe notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md)
  
### <a name="applicationinfo"></a>ApplicationInfo
Obtém as informações sobre a aplicação que está a consumir o SDK.

  
**Devolve**: informações sobre a aplicação que está a consumir o SDK
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Obtém se deve ser ignorada a inicialização de telemetria ou não.

  
**Devolve**: se a inicialização de telemetria deve ser ignorada ou não
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Desativa a inicialização de telemetria.
Esse método não é normalmente chamado por aplicações cliente, em vez disso, ela é usada pelo SDK de ficheiro para impedir a inicialização duplicada
  
### <a name="setnewfeaturesdisabled"></a>SetNewFeaturesDisabled
Desativa a novos recursos.
Para aplicações que não querem experimentar novas funcionalidades
  
### <a name="arenewfeaturesdisabled"></a>AreNewFeaturesDisabled
Obtém se novos recursos estão desativados ou não.

  
**Devolve**: se os novos recursos estão desativados ou não
  
### <a name="loggerdelegate"></a>LoggerDelegate
Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.

  
**Devolve**: Logger
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Substitua o agente de log padrão.

Parâmetros:  
* **loggerDelegate**: interface de retorno de chamada de registo implementada por aplicações cliente


Este método deve ser chamado por aplicações cliente que utilizam a sua própria implementação de agente de log
  
### <a name="httpdelegate"></a>HttpDelegate
Obtenha o delegado HTTP (se houver) fornecido pela aplicação.

  
**Devolve**: HTTP delegar a ser utilizado para operações de HTTP
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
Substitua a pilha HTTP padrão do cliente.

Parâmetros:  
* **httpDelegate**: interface de retorno de chamada HTTP implementada pela aplicação cliente


  
### <a name="optouttelemetry"></a>OptOutTelemetry
Opta ativamente por toda a telemetria de recolha.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Obtém se telemetria recolha deve ser desabilitada ou não.

  
**Devolve**: se a telemetria de recolha deve ser desativada ou não
  
### <a name="setsessionid"></a>SetSessionId
Define o ID de sessão.

Parâmetros:  
* **sessionId**: ID de sessão que será utilizado para correlacionar os registos/telemetria


  
### <a name="getsessionid"></a>GetSessionId
Obtém o ID de sessão.

  
**Devolve**: ID de sessão que será utilizado para correlacionar os registos/telemetria
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Defina o nível de registo mais baixo que irão acionar um evento de log.

Parâmetros:  
* **logLevel**: mais baixo nível que irão acionar um evento de log de registo. 



  
**Devolve**: VERDADEIRO
  
### <a name="loglevel"></a>LogLevel
Obtenha o nível de registo mais baixo que irão acionar um evento de log.

  
**Devolve**: menor nível de registo que irá acionar um evento de log.