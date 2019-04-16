---
title: classe mip::FileProfile::Settings
description: Documenta a classe mip::fileprofile da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: d85fe9f4b3de485ab966a38b2c41358a6ba091e0
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574290"
---
# <a name="class-mipfileprofilesettings"></a>classe mip::FileProfile::Settings 
[As definições](class_mip_fileprofile_settings.md) utilizada pelo [FileProfile](class_mip_fileprofile.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (std::shared_ptr de Std:: String & caminho, bool useInMemoryStorage, const\<AuthDelegate\> authDelegate, std::shared_ptr\<ConsentDelegate\> consentDelegate, std::shared_ptr\< Observador\> observador, const ApplicationInfo & applicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md) construtor.
public const std::string& GetPath() const  |  Obtém o caminho em que o registo, telemetria, e outro estado persistente é armazenado.
bool pública GetUseInMemoryStorage() const  |  Obtém se todos os Estados devem ser armazenados na memória (em vez de no disco)
público std::shared_ptr\<AuthDelegate\> GetAuthDelegate() const  |  Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.
public std::shared_ptr\<ConsentDelegate\> GetConsentDelegate() const  |  Obtém o delegado de autorização utilizado para pedir consentimento do utilizador se ligam a serviços.
público std::shared_ptr\<observador\> GetObserver() const  |  Obtém o observador que recebe notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md).
público GetApplicationInfo() const ApplicationInfo const  |  Obtém as informações sobre a aplicação que está a consumir o SDK.
público SetNewFeaturesDisabled() void  |  Desativa a novos recursos.
bool pública AreNewFeaturesDisabled() const  |  Obtém se novos recursos estão desativados ou não.
public std::shared_ptr\<LoggerDelegate\> GetLoggerDelegate() const  |  Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.
public void SetLoggerDelegate(const std::shared_ptr\<LoggerDelegate\>& loggerDelegate)  |  Substitua o agente de log padrão.
público std::shared_ptr\<HttpDelegate\> GetHttpDelegate() const  |  Obtenha o delegado HTTP (se houver) fornecido pela aplicação.
SetHttpDelegate void pública (const std::shared_ptr\<HttpDelegate\>& httpDelegate)  |  Substitua a pilha HTTP padrão do cliente.
público std::shared_ptr\<TaskDispatcherDelegate\> GetTaskDispatcherDelegate() const  |  Obtenha o delegado de TaskDispatcher (se houver) fornecido pela aplicação.
SetTaskDispatcherDelegate void pública (const std::shared_ptr\<TaskDispatcherDelegate\>& taskDispatcherDelegate)  |  Substitua a tarefa predefinida de assíncronos expedição de manipulação de do cliente.
public void OptOutTelemetry()  |  Opta ativamente por toda a telemetria de recolha.
public bool IsTelemetryOptedOut() const  |  Obtém se telemetria recolha deve ser desabilitada ou não.
public void SetSessionId(const std::string& sessionId)  |  Define o ID de sessão.
public const std::string& GetSessionId() const  |  Obtém o ID de sessão.
SetMinimumLogLevel void pública (LogLevel logLevel)  |  Defina o nível de registo mais baixo que irão acionar um evento de log.
público GetMinimumLogLevel() de LogLevel const  |  Obtenha o nível de registo mais baixo que irão acionar um evento de log.
  
## <a name="members"></a>Membros
  
### <a name="settings-function"></a>Função de definições
[FileProfile::Settings](class_mip_fileprofile_settings.md) construtor.

Parâmetros:  
* **path**: Caminho de ficheiro em que o registo, telemetria e outras estado persistente é armazenado 


* **useInMemoryStorage**: true se todos os Estados devem ser armazenados na memória, false se o estado pode ser colocado em cache em disco 


* **authDelegate**: Delegado de autenticação utilizado para aquisição de tokens de autenticação 


* **observer**: [Observador](class_mip_fileprofile_observer.md) instância que irá receber notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md)


* **applicationInfo**: Informações sobre a aplicação que está a consumir o SDK


  
### <a name="getpath-function"></a>Função de GetPath
Obtém o caminho em que o registo, telemetria, e outro estado persistente é armazenado.

  
**Devolve**: Caminho em que o registo, telemetria e outras estado persistente é armazenado
  
### <a name="getuseinmemorystorage-function"></a>Função de GetUseInMemoryStorage
Obtém se todos os Estados devem ser armazenados na memória (em vez de no disco)

  
**Devolve**: Se todos os Estados devem ser armazenados na memória (em vez de no disco)
  
### <a name="getauthdelegate-function"></a>Função de GetAuthDelegate
Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.

  
**Devolve**: Delegado de autenticação utilizado para aquisição de tokens de autenticação
  
### <a name="getconsentdelegate-function"></a>Função de GetConsentDelegate
Obtém o delegado de autorização utilizado para pedir consentimento do utilizador se ligam a serviços.

  
**Devolve**: Utilizado para pedir o consentimento do utilizador de delegado de consentimento
  
### <a name="getobserver-function"></a>Função de GetObserver
Obtém o observador que recebe notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md).

  
**Devolve**: [Observador](class_mip_fileprofile_observer.md) que recebe notificações de eventos relacionados com [FileProfile](class_mip_fileprofile.md)
  
### <a name="getapplicationinfo-function"></a>Função de GetApplicationInfo
Obtém as informações sobre a aplicação que está a consumir o SDK.

  
**Devolve**: Informações sobre a aplicação que está a consumir o SDK
  
### <a name="setnewfeaturesdisabled-function"></a>Função de SetNewFeaturesDisabled
Desativa a novos recursos.
Para aplicações que não querem experimentar novas funcionalidades
  
### <a name="arenewfeaturesdisabled-function"></a>Função de AreNewFeaturesDisabled
Obtém se novos recursos estão desativados ou não.

  
**Devolve**: Se os novos recursos estão desativados ou não
  
### <a name="getloggerdelegate-function"></a>Função de GetLoggerDelegate
Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.

  
**Devolve**: agente de log
  
### <a name="setloggerdelegate-function"></a>Função de SetLoggerDelegate
Substitua o agente de log padrão.

Parâmetros:  
* **loggerDelegate**: Interface de retorno de chamada de registo implementada por aplicações cliente


Este método deve ser chamado por aplicações cliente que utilizam a sua própria implementação de agente de log
  
### <a name="gethttpdelegate-function"></a>Função de GetHttpDelegate
Obtenha o delegado HTTP (se houver) fornecido pela aplicação.

  
**Devolve**: Delegado HTTP a ser utilizado para operações de HTTP
  
### <a name="sethttpdelegate-function"></a>Função de SetHttpDelegate
Substitua a pilha HTTP padrão do cliente.

Parâmetros:  
* **httpDelegate**: Interface de retorno de chamada HTTP implementada pela aplicação cliente


  
### <a name="gettaskdispatcherdelegate-function"></a>Função de GetTaskDispatcherDelegate
Obtenha o delegado de TaskDispatcher (se houver) fornecido pela aplicação.

  
**Devolve**: TaskDispatcher delegado a ser utilizado para executar tarefas assíncronas
  
### <a name="settaskdispatcherdelegate-function"></a>Função de SetTaskDispatcherDelegate
Substitua a tarefa predefinida de assíncronos expedição de manipulação de do cliente.

Parâmetros:  
* **taskDispatcherDelegate**: Tarefa de expedição de interface de retorno de chamada implementada pela aplicação cliente


  
### <a name="optouttelemetry-function"></a>Função de OptOutTelemetry
Opta ativamente por toda a telemetria de recolha.
  
### <a name="istelemetryoptedout-function"></a>Função de IsTelemetryOptedOut
Obtém se telemetria recolha deve ser desabilitada ou não.

  
**Devolve**: Se a telemetria de recolha deve ser desativada ou não
  
### <a name="setsessionid-function"></a>Função de SetSessionId
Define o ID de sessão.

Parâmetros:  
* **sessionId**: ID de sessão que será utilizado para correlacionar os registos/telemetria


  
### <a name="getsessionid-function"></a>Função de GetSessionId
Obtém o ID de sessão.

  
**Devolve**: ID de sessão que será utilizado para correlacionar os registos/telemetria
  
### <a name="setminimumloglevel-function"></a>Função de SetMinimumLogLevel
Defina o nível de registo mais baixo que irão acionar um evento de log.

Parâmetros:  
* **logLevel**: mais baixo nível que irão acionar um evento de log de registo. 



  
**Devolve**: Verdadeiro
  
### <a name="getminimumloglevel-function"></a>Função de GetMinimumLogLevel
Obtenha o nível de registo mais baixo que irão acionar um evento de log.

  
**Devolve**: Nível de registo mais baixo que irá acionar um evento de log.