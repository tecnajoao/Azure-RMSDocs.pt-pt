---
title: classe mip::NoPermissionsError
description: Documenta a classe mip::nopermissionserror da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: ea7edbc6e30d3ac529d55ddeaeecc63f140c512f
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57329425"
---
# <a name="class-mipnopermissionserror"></a>classe mip::NoPermissionsError 
O utilizador não foi possível obter acesso ao conteúdo. Por exemplo, não existem permissões, conteúdos revogaram.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public std::string GetReferrer() const  |  Obtém o contacto em caso de direitos em falta para o documento.
public std::string GetOwner() const  | _Ainda não documentado._
public char const* what() const  |  Obter a mensagem de erro.
público std::shared_ptr\<erro\> const clone)  |  Clone o erro.
público GetErrorType() virtual ErrorType const  |  Obter o tipo de erro.
público virtual const Std:: String & GetErrorName() const  |  Obtenha o nome do erro.
public virtual const std::string& GetMessage() const  |  Obter a mensagem de erro.
public virtual void SetMessage(const std::string& msg)  |  Defina a mensagem de erro.
  
## <a name="members"></a>Membros
  
### <a name="getreferrer-function"></a>Função de GetReferrer
Obtém o contacto em caso de direitos em falta para o documento.

  
**Devolve**: O contacto em caso de direitos em falta para o documento.
  
### <a name="getowner-function"></a>Função de GetOwner
_Não documentados ainda._

  
### <a name="what-function"></a>o que funcionar
Obter a mensagem de erro.

  
**Devolve**: A mensagem de erro
  
### <a name="clone-function"></a>Função de clone
Clone o erro.

  
**Devolve**: Um clone do erro.
  
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

