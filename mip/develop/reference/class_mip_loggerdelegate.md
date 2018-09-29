---
title: classe mip LoggerDelegate
description: Referência para a classe mip LoggerDelegate
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b25cdb177735feccfa5c4d344613e4747d18b77f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445857"
---
# <a name="class-miploggerdelegate"></a>classe mip::LoggerDelegate 
Uma classe que define a interface para o agente de log MIP SDK.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Init void pública (Std:: String const & storagePath, LogLevel logLevel)  |  Inicialize o agente de log.
 público GetLogLevel() de LogLevel const  |  Obtenha a mais baixa evel logl que irá acionar um evento de log.
 Flush () de void pública  |  Esvaziar o agente de log.
 WriteToLog void pública (nível de LogLevel const, Std:: String const & mensagem, Std:: String const & função, Std:: String const & ficheiro, const int32_t linha)  |  Escreva uma instrução de registo para o ficheiro de registo.
  
## <a name="members"></a>Membros
  
### <a name="init"></a>Init
Inicialize o agente de log.

Parâmetros:  
* **storagePath**: o caminho para a localização onde o estado persistente, incluindo registos, pode ser armazenado. 


* **logLevel**: o nível de registo mais baixo que deve acionar um evento de log.


  
### <a name="loglevel"></a>LogLevel
Obtenha a mais baixa evel logl que irá acionar um evento de log.

  
**Devolve**: O nível de registo mais baixo que irá acionar um evento de log.
  
### <a name="flush"></a>Remoção da cache
Esvaziar o agente de log.
  
### <a name="writetolog"></a>WriteToLog
Escreva uma instrução de registo para o ficheiro de registo.

Parâmetros:  
* **nível**: o nível de registo para a instrução de log. 


* **mensagem**: a mensagem para a instrução de log. 


* **função**: o nome da função para a instrução de log. 


* **ficheiro**: o nome do ficheiro onde foi gerada a instrução de log. 


* **linha**: o número de linha em que a instrução de log foi gerada.

