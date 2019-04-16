---
title: classe mip::HttpOperation
description: Documenta a classe mip::httpoperation da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: e3eaedbf508f116b19521286b686bc955d108efe
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574487"
---
# <a name="class-miphttpoperation"></a>classe mip::HttpOperation 
Interface que descreve uma única operação de HTTP, implementada pela aplicação de cliente, ao substituir [HttpDelegate](class_mip_httpdelegate.md).
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Obtém o ID de operação.
public std::shared_ptr\<HttpResponse\> GetResponse()  |  Obter resposta, se aplicável.
bool pública IsCancelled()  |  Obter o estado de cancelamento da operação.
  
## <a name="members"></a>Membros
  
### <a name="getid-function"></a>Função de GetId
Obtém o ID de operação.

  
**Devolve**: ID de operação correspondente [HttpRequest](class_mip_httprequest.md) e [HttpResponse](class_mip_httpresponse.md) terão o mesmo ID
  
### <a name="getresponse-function"></a>Função de GetResponse
Obter resposta, se aplicável.

  
**Devolve**: Resposta
  
### <a name="iscancelled-function"></a>Função de IsCancelled
Obter o estado de cancelamento da operação.

  
**Devolve**: Estado de cancelamento