---
title: classe mip PolicyHandler
description: Referência para a classe mip PolicyHandler
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 23de5616558a298189cb885727d69a20373a3609
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445942"
---
# <a name="class-mippolicyhandler"></a>classe mip::PolicyHandler 
Essa classe fornece uma interface para todas as funções do manipulador de política num arquivo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::shared_ptr<ContentLabel> GetSensitivityLabel (const ExecutionState & Estado)  |  Obter etiqueta de confidencialidade do conteúdo existente.
Std:: vector público < std::shared_ptr<Action>> ComputeActions (const ExecutionState & Estado)  |  Executa as regras no manipulador com base no estado fornecido e retorna a lista de ações a ser executado.
 NotifyCommittedActions void pública (const ExecutionState & Estado)  |  Chamado assim que as ações calculadas foram aplicadas e os dados dedicada para o disco.
  
## <a name="members"></a>Membros
  
### <a name="contentlabel"></a>ContentLabel
Obter etiqueta de confidencialidade do conteúdo existente.

Parâmetros:  
* **estado**: estado atual do conteúdo 



  
**Devolve**: A etiqueta aplicada atualmente ao conteúdo. Se não o nome, devolve vazio.
  
### <a name="action"></a>Ação
Executa as regras no manipulador com base no estado fornecido e retorna a lista de ações a ser executado.

Parâmetros:  
* **estado**: o estado de execução atual do conteúdo as regras estão em execução. 



  
**Devolve**: lista de ações que devem ser aplicadas no conteúdo.
  
### <a name="notifycommittedactions"></a>NotifyCommittedActions
Chamado assim que as ações calculadas foram aplicadas e os dados dedicada para o disco.

Parâmetros:  
* **estado**: o estado de execução atual do conteúdo depois das ações foram confirmadas 


: Esta chamada envia um evento de auditoria