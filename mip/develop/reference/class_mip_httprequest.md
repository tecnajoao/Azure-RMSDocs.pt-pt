---
title: classe mip HttpRequest
description: Referência para a classe mip HttpRequest
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e838eb247bc00d43da72db1de03304e89a1b1da5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445245"
---
# <a name="class-miphttprequest"></a>classe mip::HttpRequest 
Interface que descreve um único pedido HTTP.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público GetRequestType() de HttpRequestType const  |  Obter o tipo de pedido.
 público const Std:: String & GetUrl() const  |  Url do pedido GET.
 público const Std:: String & GetBody() const  |  Obtenha o corpo do pedido.
público std::map const < Std:: String, Std:: String, CaseInsensitiveComparator > & GetHeaders() const  |  Obtenha os cabeçalhos de pedido.
  
## <a name="members"></a>Membros
  
### <a name="httprequesttype"></a>HttpRequestType
Obter o tipo de pedido.

  
**Devolve**: tipo de pedido
  
### <a name="geturl"></a>GetUrl
Url do pedido GET.

  
**Devolve**: url do pedido
  
### <a name="getbody"></a>GetBody
Obtenha o corpo do pedido.

  
**Devolve**: corpo do pedido
  
### <a name="getheaders"></a>GetHeaders
Obtenha os cabeçalhos de pedido.

  
**Devolve**: cabeçalhos de pedido