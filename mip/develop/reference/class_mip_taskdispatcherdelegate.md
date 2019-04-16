---
title: classe mip::TaskDispatcherDelegate
description: Documenta a classe mip::taskdispatcherdelegate da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 568a6df614370769556cd3634070e199beb4da5b
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574436"
---
# <a name="class-miptaskdispatcherdelegate"></a>classe mip::TaskDispatcherDelegate 
Uma classe que define a interface ao dispatcher de tarefa MIP SDK.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public void DispatchTask(const std::string& taskId, std::function\<void()\> task)  |  Execute uma tarefa num thread de segundo plano.
public void DispatchTask(const std::string& taskId, std::function\<void()\> task, int64_t delay)  |  Execute uma tarefa num thread em segundo plano com o atraso especificado.
public void ExecuteTaskOnIndependentThread(const std::string& taskId, std::function\<void()\> task)  |  Execute imediatamente uma tarefa num thread independente.
bool pública CancelTask (const Std:: String & taskId)  |  Cancele uma tarefa em segundo plano.
público CancelAllTasks() void  |  Cancele todas as tarefas em segundo plano.
  
## <a name="members"></a>Membros
  
### <a name="dispatchtask-function"></a>Função de DispatchTask
Execute uma tarefa num thread de segundo plano.

Parâmetros:  
* **taskId**: ID para identificar exclusivamente uma tarefa 


* **task**: Função a ser executado


  
### <a name="dispatchtask-function"></a>Função de DispatchTask
Execute uma tarefa num thread em segundo plano com o atraso especificado.

Parâmetros:  
* **taskId**: ID para identificar exclusivamente uma tarefa 


* **task**: Função a ser executado 


* **delay**: Atraso (em segundos) antes de executar a tarefa


  
### <a name="executetaskonindependentthread-function"></a>Função de ExecuteTaskOnIndependentThread
Execute imediatamente uma tarefa num thread independente.

Parâmetros:  
* **taskId**: ID para identificar exclusivamente uma tarefa 


* **task**: Função a ser executado


  
### <a name="canceltask-function"></a>Função de CancelTask
Cancele uma tarefa em segundo plano.

Parâmetros:  
* **taskId**: ID da tarefa para cancelar



  
**Devolve**: VERDADEIRO se a tarefa foi cancelado com êxito, caso contrário FALSO
  
### <a name="cancelalltasks-function"></a>Função de CancelAllTasks
Cancele todas as tarefas em segundo plano.