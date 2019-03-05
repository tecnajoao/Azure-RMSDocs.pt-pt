---
title: classe mip::LoggerDelegate
description: Documenta a classe mip::loggerdelegate da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 511c8dabc8ff31c70c8343a80d423b76c43fa946
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330326"
---
# <a name="class-miploggerdelegate"></a>classe mip::LoggerDelegate 
Uma classe que define a interface para o agente de log MIP SDK.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public void Init(const std::string& storagePath, LogLevel logLevel)  |  Inicialize o agente de log.
público GetLogLevel() de LogLevel const  |  Obtenha a mais baixa evel logl que irá acionar um evento de log.
public void Flush()  |  Esvaziar o agente de log.
public void WriteToLog(const LogLevel level, const std::string& message, const std::string& function, const std::string& file, const int32_t line)  |  Escreva uma instrução de registo para o ficheiro de registo.
  
## <a name="members"></a>Membros
  
### <a name="init-function"></a>Função init
Inicialize o agente de log.

Parâmetros:  
* **storagePath**: o caminho para a localização onde o estado persistente, incluindo registos, pode ser armazenado. 


* **logLevel**: o nível de registo mais baixo que deve acionar um evento de log.


  
### <a name="getloglevel-function"></a>Função de GetLogLevel
Obtenha a mais baixa evel logl que irá acionar um evento de log.

  
**Devolve**: O nível de registo mais baixo que irá acionar um evento de log.
  
### <a name="flush-function"></a>Remover função
Esvaziar o agente de log.
  
### <a name="writetolog-function"></a>Função de WriteToLog
Escreva uma instrução de registo para o ficheiro de registo.

Parâmetros:  
* **nível**: o nível de registo para a instrução de log. 


* **mensagem**: a mensagem para a instrução de log. 


* **função**: o nome da função para a instrução de log. 


* **ficheiro**: o nome do ficheiro onde foi gerada a instrução de log. 


* **linha**: o número de linha em que a instrução de log foi gerada.

