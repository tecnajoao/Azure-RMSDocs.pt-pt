---
title: classe mip::ProtectionProfile::Settings
description: Documenta a classe mip::protectionprofile da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 3d3685656f8814fe495e6e29d7fe12cf54d7d7d4
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574079"
---
# <a name="class-mipprotectionprofilesettings"></a>classe mip::ProtectionProfile::Settings 
[As definições](class_mip_protectionprofile_settings.md) utilizada pelo [ProtectionProfile](class_mip_protectionprofile.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (const std::shared_ptr Std:: String & caminho, bool useInMemoryStorage, const\<AuthDelegate\>& authDelegate, const std::shared_ptr\<ConsentDelegate\>& consentDelegate const std::shared_ptr\<ProtectionProfile::Observer\>& observador, const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) construtor que especifica um observador a ser utilizado para operações assíncronas.
Definições de públicas (const std::shared_ptr Std:: String & caminho, bool useInMemoryStorage, const\<AuthDelegate\>& authDelegate, const std::shared_ptr\<ConsentDelegate\>& consentDelegate const ApplicationInfo & applicationInfo)  |  [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) construtor, utilizado para operações síncronas.
public const std::string& GetPath() const  |  Obtém o caminho em que o registo, telemetria, e outros materiais de proteção são armazenados.
bool pública GetUseInMemoryStorage() const  |  Obter se ou caches são armazenadas na memória apenas (em vez de no disco)
público std::shared_ptr\<AuthDelegate\> GetAuthDelegate() const  |  Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.
public std::shared_ptr\<ConsentDelegate\> GetConsentDelegate() const  |  Obtém o delegado de autorização utilizado para ligar aos serviços.
public std::shared_ptr\<ProtectionProfile::Observer\> GetObserver() const  |  Obtém o observador que recebe notificações de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md).
público ApplicationInfo const & GetApplicationInfo() const  |  Obtém as informações sobre a aplicação que está a consumir a proteção do SDK.
public void OptOutTelemetry()  |  Opta ativamente por toda a telemetria de recolha.
public bool IsTelemetryOptedOut() const  |  Obtém se telemetria recolha deve ser desabilitada ou não.
public std::shared_ptr\<LoggerDelegate\> GetLoggerDelegate() const  |  Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.
public void SetLoggerDelegate(const std::shared_ptr\<LoggerDelegate\>& loggerDelegate)  |  Substitua o agente de log padrão.
público std::shared_ptr\<HttpDelegate\> GetHttpDelegate() const  |  Obtenha o delegado HTTP (se houver) fornecido pela aplicação.
SetHttpDelegate void pública (const std::shared_ptr\<HttpDelegate\>& httpDelegate)  |  Substitua a pilha HTTP padrão do cliente.
público std::shared_ptr\<TaskDispatcherDelegate\> GetTaskDispatcherDelegate() const  |  Obtenha o delegado de TaskDispatcher (se houver) fornecido pela aplicação.
SetTaskDispatcherDelegate void pública (const std::shared_ptr\<TaskDispatcherDelegate\>& taskDispatcherDelegate)  |  Substitua a tarefa predefinida de assíncronos expedição de manipulação de do cliente.
público SetNewFeaturesDisabled() void  |  Desativa a novos recursos.
bool pública AreNewFeaturesDisabled() const  |  Obtém se novos recursos estão desativados ou não.
public void SetSessionId(const std::string& sessionId)  |  Define o ID de sessão.
public const std::string& GetSessionId() const  |  Obtém o ID de sessão.
SetMinimumLogLevel void pública (LogLevel logLevel)  |  Defina o nível de registo mínimo que irão acionar um evento de log.
público GetMinimumLogLevel() de LogLevel const  |  Obtenha o objeto de nível de registo mínimo.
  
## <a name="members"></a>Membros
  
### <a name="settings-function"></a>Função de definições
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) construtor que especifica um observador a ser utilizado para operações assíncronas.

Parâmetros:  
* **path**: Caminho de ficheiro em que o registo, telemetria e outros materiais de proteção são armazenados 


* **useInMemoryStorage**: Store qualquer Estado em cache na memória, em vez de no disco 


* **authDelegate**: Objeto de retorno de chamada a ser utilizado para autenticação, implementada pela aplicação cliente 


* **observer**: [Observador](class_mip_protectionprofile_observer.md) instância que irá receber notificações de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md)


* **applicationInfo**: Informações sobre a aplicação que está a consumir a proteção de SDK


  
### <a name="settings-function"></a>Função de definições
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) construtor, utilizado para operações síncronas.

Parâmetros:  
* **path**: Caminho de ficheiro em que o registo, telemetria e outros materiais de proteção são armazenados 


* **useInMemoryStorage**: Store qualquer Estado em cache na memória, em vez de no disco 


* **authDelegate**: Objeto de retorno de chamada a ser utilizado para autenticação, implementada pela aplicação cliente 


* **applicationInfo**: Informações sobre a aplicação que esteja a consumir a proteção de SDK


  
### <a name="getpath-function"></a>Função de GetPath
Obtém o caminho em que o registo, telemetria, e outros materiais de proteção são armazenados.

  
**Devolve**: Caminho em que o registo, telemetria e outros materiais de proteção são armazenados
  
### <a name="getuseinmemorystorage-function"></a>Função de GetUseInMemoryStorage
Obter se ou caches são armazenadas na memória apenas (em vez de no disco)

  
**Devolve**: TRUE se as caches são armazenadas na memória apenas
  
### <a name="getauthdelegate-function"></a>Função de GetAuthDelegate
Obtém o delegado de autenticação utilizado para aquisição de tokens de autenticação.

  
**Devolve**: Delegado de autenticação utilizado para aquisição de tokens de autenticação
  
### <a name="getconsentdelegate-function"></a>Função de GetConsentDelegate
Obtém o delegado de autorização utilizado para ligar aos serviços.

  
**Devolve**: Delegado de autorização utilizado para ligar aos serviços
  
### <a name="getobserver-function"></a>Função de GetObserver
Obtém o observador que recebe notificações de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md).

  
**Devolve**: [Observador](class_mip_protectionprofile_observer.md) que recebe notificações de eventos relacionados com [ProtectionProfile](class_mip_protectionprofile.md)
  
### <a name="getapplicationinfo-function"></a>Função de GetApplicationInfo
Obtém as informações sobre a aplicação que está a consumir a proteção do SDK.

  
**Devolve**: Informações sobre a aplicação que está a consumir a proteção de SDK
  
### <a name="optouttelemetry-function"></a>Função de OptOutTelemetry
Opta ativamente por toda a telemetria de recolha.
  
### <a name="istelemetryoptedout-function"></a>Função de IsTelemetryOptedOut
Obtém se telemetria recolha deve ser desabilitada ou não.

  
**Devolve**: Se a telemetria de recolha deve ser desativada ou não
  
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


  
### <a name="setnewfeaturesdisabled-function"></a>Função de SetNewFeaturesDisabled
Desativa a novos recursos.
Para aplicações que não querem experimentar novas funcionalidades
  
### <a name="arenewfeaturesdisabled-function"></a>Função de AreNewFeaturesDisabled
Obtém se novos recursos estão desativados ou não.

  
**Devolve**: Se os novos recursos estão desativados ou não
  
### <a name="setsessionid-function"></a>Função de SetSessionId
Define o ID de sessão.

Parâmetros:  
* **sessionId**: ID de sessão que será utilizado para correlacionar os registos/telemetria


  
### <a name="getsessionid-function"></a>Função de GetSessionId
Obtém o ID de sessão.

  
**Devolve**: ID de sessão que será utilizado para correlacionar os registos/telemetria
  
### <a name="setminimumloglevel-function"></a>Função de SetMinimumLogLevel
Defina o nível de registo mínimo que irão acionar um evento de log.

Parâmetros:  
* **logLevel**: nível de registo mínimo que irão acionar um evento de log. 



  
**Devolve**: Verdadeiro
  
### <a name="getminimumloglevel-function"></a>Função de GetMinimumLogLevel
Obtenha o objeto de nível de registo mínimo.

  
**Devolve**: Nível de registo mínimo que irão acionar um evento de log.