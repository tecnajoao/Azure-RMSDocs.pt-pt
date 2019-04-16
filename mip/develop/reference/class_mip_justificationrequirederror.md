---
title: classe mip::JustificationRequiredError
description: Documenta a classe mip::justificationrequirederror da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: f24b380b892739faec0602f3dd6b60467e4f4993
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573637"
---
# <a name="class-mipjustificationrequirederror"></a>classe mip::JustificationRequiredError 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
std::shared_ptr virtual pública\<erro\> const clone)  |  Clone o erro.
public char const* what() const  |  Obter a mensagem de erro.
público std::shared_ptr\<erro\> const clone)  |  Clone o erro.
público GetErrorType() virtual ErrorType const  |  Obter o tipo de erro.
público virtual const Std:: String & GetErrorName() const  |  Obtenha o nome do erro.
public virtual const std::string& GetMessage() const  |  Obter a mensagem de erro.
public virtual void SetMessage(const std::string& msg)  |  Defina a mensagem de erro.
  
## <a name="members"></a>Membros
  
### <a name="clone-function"></a>Função de clone
Clone o erro.

  
**Devolve**: Um clone do erro.

### <a name="what-function"></a>o que funcionar
Obter a mensagem de erro.

  
**Devolve**: A mensagem de erro
  
### <a name="geterrortype-function"></a>Função de GetErrorType
Obter o tipo de erro.

  
**Devolve**: O tipo de erro.
  
### <a name="geterrorname-function"></a>Função de GetErrorName
Obtenha o nome do erro.

  
**Devolve**: O nome do erro.
  
### <a name="getmessage-function"></a>Função GetMessage
Obter a mensagem de erro.

  
**Devolve**: A mensagem de erro.
  
### <a name="setmessage-function"></a>Função de SetMessage
Defina a mensagem de erro.

Parâmetros:  
* **msg**: a mensagem de erro.