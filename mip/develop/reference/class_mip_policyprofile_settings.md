---
title: classe mip PolicyProfile definições
description: Referência para a classe mip PolicyProfile definições
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 07cbcbc022c02a43f751e1cf55b5b0efdfb816d1
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446978"
---
# <a name="class-mippolicyprofilesettings"></a>classe mip::PolicyProfile::Settings 
[As definições](class_mip_policyprofile_settings.md) utilizada pelo [PolicyProfile](class_mip_policyprofile.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (const std::shared_ptr Std:: String & caminho, bool useInMemoryStorage, const<AuthDelegate>& authDelegate, std::shared_ptr const < PolicyProfile::Observer > & observador, const ApplicationInfo & applicationInfo)  |  Interface para definir o perfil.
 público const Std:: String & GetPath() const  |  Obter o caminho para o estado armazenado.
 bool pública GetUseInMemoryStorage() const  |  Obtenha o sinalizador de armazenamento em utilização na memória.
público std::shared_ptr const<AuthDelegate>& GetAuthDelegate() const  |  Obtenha o delegado de autenticação.
std::shared_ptr const público < PolicyProfile::Observer > & GetObserver() const  |  Obtenha o observador de eventos.
 público GetApplicationInfo() const ApplicationInfo const  |  Obter as informações de aplicação.
público std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.
SetLoggerDelegate void pública (const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Substitua o agente de log padrão.
público std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Obtenha o delegado HTTP (se houver) fornecido pela aplicação.
SetHttpDelegate void pública (const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Substitua a pilha HTTP padrão do cliente.
 público OptOutTelemetry() void  |  Opta ativamente por toda a telemetria de recolha.
 bool pública IsTelemetryOptedOut() const  |  Obtém se telemetria recolha deve ser desabilitada ou não.
 SetMinimumLogLevel void pública (LogLevel logLevel)  |  Defina o nível de registo mínimo que irão acionar um evento de log.
 público GetMinimumLogLevel() de LogLevel const  |  Obtenha o objeto de nível de registo mínimo.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Interface para definir o perfil.

Parâmetros:  
* **caminho**: O caminho para um diretório em que o SDK irá armazenar o estado do perfil. 


* **useInMemoryStorage**: Store qualquer Estado em cache na memória, em vez de no disco. 


* **authDelegate**: O delegado de autenticação utilizado pelo SDK para adquirir os tokens de autenticação. 


* **observador**: implementar uma classe a [PolicyProfile::Observer](class_mip_policyprofile_observer.md) interface. Pode ser nullptr. 


* **applicationInfo**: os identificadores de aplicativo utilizados para acesso de serviço.


  
### <a name="getpath"></a>GetPath
Obter o caminho para o estado armazenado.

  
**Devolve**: caminho para o estado armazenado.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Obtenha o sinalizador de armazenamento em utilização na memória.

  
**Devolve**: True se o uso na memória está definido como outra FALSO.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Obtenha o delegado de autenticação.

  
**Devolve**: O delegado de autenticação.
  
### <a name="policyprofileobserver"></a>PolicyProfile::Observer
Obtenha o observador de eventos.

  
**Devolve**: O observador de eventos.
  
### <a name="applicationinfo"></a>ApplicationInfo
Obter as informações de aplicação.

  
**Devolve**: as informações da aplicação.
  
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

  
**Devolve**: delegado de Http a ser utilizado para operações de HTTP
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
Substitua a pilha HTTP padrão do cliente.

Parâmetros:  
* **httpDelegate**: interface de retorno de chamada de Http implementada pela aplicação cliente


  
### <a name="optouttelemetry"></a>OptOutTelemetry
Opta ativamente por toda a telemetria de recolha.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Obtém se telemetria recolha deve ser desabilitada ou não.

  
**Devolve**: recolha Iftelemetry deve ser desabilitada ou não
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Defina o nível de registo mínimo que irão acionar um evento de log.

Parâmetros:  
* **logLevel**: nível de registo mínimo que irão acionar um evento de log. 



  
**Devolve**: VERDADEIRO
  
### <a name="loglevel"></a>LogLevel
Obtenha o objeto de nível de registo mínimo.

  
**Devolve**: nível de registo mínimo que irão acionar um evento de log.