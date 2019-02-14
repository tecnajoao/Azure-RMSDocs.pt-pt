---
title: classe mip::HttpRequest
description: Documenta a classe mip::httprequest da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 56c736d985e7c8bd258fcb7c1f7e42b5db3801fd
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256945"
---
# <a name="class-miphttprequest"></a>classe mip::HttpRequest 
Interface que descreve um único pedido HTTP.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public HttpRequestType GetRequestType() const  |  Obter o tipo de pedido.
public const std::string& GetUrl() const  |  Url do pedido GET.
public const std::string& GetBody() const  |  Obtenha o corpo do pedido.
public const std::map\<std::string, std::string, CaseInsensitiveComparator\>& GetHeaders() const  |  Obtenha os cabeçalhos de pedido.
  
## <a name="members"></a>Membros
  
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
