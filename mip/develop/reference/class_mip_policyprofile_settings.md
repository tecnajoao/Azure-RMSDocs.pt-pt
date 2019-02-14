---
title: classe mip::PolicyProfile::Settings
description: Documenta a classe mip::policyprofile da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: a857f8f2dd9b5544fbdff4949c833f048bb78aca
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56253395"
---
# <a name="class-mippolicyprofilesettings"></a>classe mip::PolicyProfile::Settings 
[As definições](class_mip_policyprofile_settings.md) utilizada pelo [PolicyProfile](class_mip_policyprofile.md) durante sua criação e ao longo de seu ciclo de vida.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de públicas (const std::shared_ptr Std:: String & caminho, bool useInMemoryStorage, const\<AuthDelegate\>& authDelegate, const std::shared_ptr\<PolicyProfile::Observer\>& observador, const ApplicationInfo & applicationInfo)  |  Interface para definir o perfil.
public const std::string& GetPath() const  |  Obter o caminho para o estado armazenado.
bool pública GetUseInMemoryStorage() const  |  Obtenha o sinalizador de armazenamento em utilização na memória.
público std::shared_ptr const\<AuthDelegate\>& GetAuthDelegate() const  |  Obtenha o delegado de autenticação.
public const std::shared_ptr\<PolicyProfile::Observer\>& GetObserver() const  |  Obtenha o observador de eventos.
público GetApplicationInfo() const ApplicationInfo const  |  Obter as informações de aplicação.
public std::shared_ptr\<LoggerDelegate\> GetLoggerDelegate() const  |  Obtenha o delegado de agente de log (se houver) fornecido pela aplicação.
public void SetLoggerDelegate(const std::shared_ptr\<LoggerDelegate\>& loggerDelegate)  |  Substitua o agente de log padrão.
público std::shared_ptr\<HttpDelegate\> GetHttpDelegate() const  |  Obtenha o delegado HTTP (se houver) fornecido pela aplicação.
SetHttpDelegate void pública (const std::shared_ptr\<HttpDelegate\>& httpDelegate)  |  Substitua a pilha HTTP padrão do cliente.
public void OptOutTelemetry()  |  Opta ativamente por toda a telemetria de recolha.
public bool IsTelemetryOptedOut() const  |  Obtém se telemetria recolha deve ser desabilitada ou não.
SetMinimumLogLevel void pública (LogLevel logLevel)  |  Defina o nível de registo mínimo que irão acionar um evento de log.
público GetMinimumLogLevel() de LogLevel const  |  Obtenha o objeto de nível de registo mínimo.
  
## <a name="members"></a>Membros
  
### <a name="settings-function"></a>Função de definições
Interface para definir o perfil.

Parâmetros:  
* **path**: O caminho para um diretório em que o SDK irá armazenar o estado do perfil. 


* **useInMemoryStorage**: Store qualquer Estado em cache na memória, em vez de no disco. 


* **authDelegate**: O delegado de autenticação utilizado pelo SDK para adquirir os tokens de autenticação. 


* **observer**: Implementar uma classe a [PolicyProfile::Observer](class_mip_policyprofile_observer.md) interface. Pode ser nullptr. 


* **applicationInfo**: Os identificadores de aplicativo utilizados para acesso de serviço.


  
### <a name="getpath-function"></a>Função de GetPath
Obter o caminho para o estado armazenado.

  
**Devolve**: Caminho para o estado armazenado.
  
### <a name="getuseinmemorystorage-function"></a>Função de GetUseInMemoryStorage
Obtenha o sinalizador de armazenamento em utilização na memória.

  
**Devolve**: VERDADEIRO se a utilização na memória está definida como outra falsa.
  
### <a name="getauthdelegate-function"></a>Função de GetAuthDelegate
Obtenha o delegado de autenticação.

  
**Devolve**: O delegado de autenticação.
  
### <a name="getobserver-function"></a>Função de GetObserver
Obtenha o observador de eventos.

  
**Devolve**: O observador de eventos.
  
### <a name="getapplicationinfo-function"></a>Função de GetApplicationInfo
Obter as informações de aplicação.

  
**Devolve**: As informações da aplicação.
  
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

  
**Devolve**: Delegado de HTTP a ser utilizado para operações de HTTP
  
### <a name="sethttpdelegate-function"></a>Função de SetHttpDelegate
Substitua a pilha HTTP padrão do cliente.

Parâmetros:  
* **httpDelegate**: Interface de retorno de chamada de HTTP implementada pela aplicação cliente


  
### <a name="optouttelemetry-function"></a>Função de OptOutTelemetry
Opta ativamente por toda a telemetria de recolha.
  
### <a name="istelemetryoptedout-function"></a>Função de IsTelemetryOptedOut
Obtém se telemetria recolha deve ser desabilitada ou não.

  
**Devolve**: VERDADEIRO se a recolha de telemetria que deve ser desabilitada outra false
  
### <a name="setminimumloglevel-function"></a>Função de SetMinimumLogLevel
Defina o nível de registo mínimo que irão acionar um evento de log.

Parâmetros:  
* **logLevel**: nível de registo mínimo que irão acionar um evento de log. 



  
**Devolve**: Verdadeiro
  
### <a name="getminimumloglevel-function"></a>Função de GetMinimumLogLevel
Obtenha o objeto de nível de registo mínimo.

  
**Devolve**: Nível de registo mínimo que irão acionar um evento de log.
