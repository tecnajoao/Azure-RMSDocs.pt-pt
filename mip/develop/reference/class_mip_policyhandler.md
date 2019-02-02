---
title: classe mip::PolicyHandler
description: Documenta a classe mip::policyhandler da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: ca644716d730a43d4455919b7555852e770e0cda
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651501"
---
# <a name="class-mippolicyhandler"></a>classe mip::PolicyHandler 
Essa classe fornece uma interface para todas as funções do manipulador de política num arquivo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::shared_ptr\<ContentLabel\> GetSensitivityLabel (const ExecutionState & Estado)  |  Obter etiqueta de confidencialidade do conteúdo existente.
público Std:: vector\<std::shared_ptr\<ação\> \> ComputeActions (const ExecutionState & Estado)  |  Executa as regras no manipulador com base no estado fornecido e retorna a lista de ações a ser executado.
NotifyCommittedActions void pública (const ExecutionState & Estado)  |  Chamado assim que as ações calculadas foram aplicadas e os dados dedicada para o disco.
  
## <a name="members"></a>Membros
  
### <a name="getsensitivitylabel-function"></a>Função de GetSensitivityLabel
Obter etiqueta de confidencialidade do conteúdo existente.

Parâmetros:  
* **state**: Estado atual do conteúdo 



  
**Devolve**: A etiqueta aplicada atualmente ao conteúdo. Se não o nome, devolve vazio.
  
### <a name="computeactions-function"></a>Função de ComputeActions
Executa as regras no manipulador com base no estado fornecido e retorna a lista de ações a ser executado.

Parâmetros:  
* **estado**: o estado de execução atual do conteúdo as regras estão em execução. 



  
**Devolve**: Lista de ações que devem ser aplicadas no conteúdo.
  
### <a name="notifycommittedactions-function"></a>Função de NotifyCommittedActions
Chamado assim que as ações calculadas foram aplicadas e os dados dedicada para o disco.

Parâmetros:  
* **estado**: o estado de execução atual do conteúdo depois das ações foram confirmadas 


: Esta chamada envia um evento de auditoria