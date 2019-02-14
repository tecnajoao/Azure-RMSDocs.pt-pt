---
title: classe mip::ServiceDisabledError
description: Documenta a classe mip::servicedisablederror da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: adcdb252fc6988f7047c2d940ddaa19fe8381405
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256452"
---
# <a name="class-mipservicedisablederror"></a>classe mip::ServiceDisabledError 
O utilizador não foi possível obter acesso ao conteúdo devido a um serviço que está a ser desabilitado.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública de extensão de GetExtent() const  |  Obtém a extensão para o qual o serviço está desativado.
public char const* what() const  |  Obter a mensagem de erro.
público std::shared_ptr\<erro\> const clone)  |  Clone o erro.
público GetErrorType() virtual ErrorType const  |  Obter o tipo de erro.
público virtual const Std:: String & GetErrorName() const  |  Obtenha o nome do erro.
public virtual const std::string& GetMessage() const  |  Obter a mensagem de erro.
public virtual void SetMessage(const std::string& msg)  |  Defina a mensagem de erro.
Enum extensão  |  Descreve a extensão para o qual o serviço está desativado.
  
## <a name="members"></a>Membros
  
### <a name="getextent-function"></a>Função de GetExtent
Obtém a extensão para o qual o serviço está desativado.

  
**Devolve**: Extensão para o qual o serviço está desativado
  
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


  
### <a name="extent-enum"></a>Enumeração de extensão
 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
Utilizador            | O serviço é desativado para o utilizador.
Dispositivo            | O serviço é desativado para o dispositivo.
Plataforma            | O serviço é desativado para a plataforma.
Inquilino            | O serviço é desativado para o inquilino.
Descreve a extensão para o qual o serviço está desativado.
