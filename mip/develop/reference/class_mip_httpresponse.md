---
title: classe mip::HttpResponse
description: Documenta a classe mip::httpresponse da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 06bc3f52bdecd85412dc0c35df46c7847167aa1b
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573765"
---
# <a name="class-miphttpresponse"></a>classe mip::HttpResponse 
Interface que descreve uma única resposta HTTP, implementada pela aplicação de cliente, ao substituir [HttpDelegate](class_mip_httpdelegate.md).
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Obtém o ID de resposta.
public int32_t GetStatusCode() const  |  Obter o código de estado de resposta.
public const std::vector\<uint8_t\>& GetBody() const  |  Obtenha o corpo do pedido.
public const std::map\<std::string, std::string, CaseInsensitiveComparator\>& GetHeaders() const  |  Obtenha os cabeçalhos de pedido.
  
## <a name="members"></a>Membros
  
### <a name="getid-function"></a>Função de GetId
Obtém o ID de resposta.

  
**Devolve**: Resposta de ID correspondente [HttpRequest](class_mip_httprequest.md) será tiveram o mesmo ID
  
### <a name="getstatuscode-function"></a>Função de GetStatusCode
Obter o código de estado de resposta.

  
**Devolve**: Código de estado
  
### <a name="getbody-function"></a>Função de GetBody
Obtenha o corpo do pedido.

  
**Devolve**: Corpo do pedido
  
### <a name="getheaders-function"></a>Função de GetHeaders
Obtenha os cabeçalhos de pedido.

  
**Devolve**: Cabeçalhos do pedido