---
title: classe mip::HttpRequest
description: Documenta a classe mip::httprequest da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 8b0349db2e985d6fb015e1a2698187089483fbe3
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573076"
---
# <a name="class-miphttprequest"></a>classe mip::HttpRequest 
Interface que descreve um único pedido HTTP.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Obtém pedido ID.
public HttpRequestType GetRequestType() const  |  Obter o tipo de pedido.
public const std::string& GetUrl() const  |  Url do pedido GET.
public const std::vector\<uint8_t\>& GetBody() const  |  Obtenha o corpo do pedido.
public const std::map\<std::string, std::string, CaseInsensitiveComparator\>& GetHeaders() const  |  Obtenha os cabeçalhos de pedido.
  
## <a name="members"></a>Membros
  
### <a name="getid-function"></a>Função de GetId
Obtém pedido ID.

  
**Devolve**: ID correspondente do pedido [HttpResponse](class_mip_httpresponse.md) terão o mesmo ID
  
### <a name="getrequesttype-function"></a>Função de GetRequestType
Obter o tipo de pedido.

  
**Devolve**: Tipo de pedido
  
### <a name="geturl-function"></a>Função de GetUrl
Url do pedido GET.

  
**Devolve**: Url do pedido
  
### <a name="getbody-function"></a>Função de GetBody
Obtenha o corpo do pedido.

  
**Devolve**: Corpo do pedido
  
### <a name="getheaders-function"></a>Função de GetHeaders
Obtenha os cabeçalhos de pedido.

  
**Devolve**: Cabeçalhos do pedido