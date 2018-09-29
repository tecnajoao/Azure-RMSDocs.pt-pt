---
title: classe mip HttpResponse
description: Referência para a classe mip HttpResponse
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a19ea78b048cafe94501d452bb9c7409237f6ffd
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445364"
---
# <a name="class-miphttpresponse"></a>classe mip::HttpResponse 
Interface que descreve uma única resposta HTTP, implementada pela aplicação de cliente, ao substituir [HttpDelegate](class_mip_httpdelegate.md).
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público int32_t GetStatusCode() const  |  Obter o código de estado de resposta.
 público const Std:: String & GetBody() const  |  Obtenha o corpo do pedido.
público std::map const < Std:: String, Std:: String, CaseInsensitiveComparator > & GetHeaders() const  |  Obtenha os cabeçalhos de pedido.
  
## <a name="members"></a>Membros
  
### <a name="getstatuscode"></a>GetStatusCode
Obter o código de estado de resposta.

  
**Devolve**: código de estado
  
### <a name="getbody"></a>GetBody
Obtenha o corpo do pedido.

  
**Devolve**: corpo do pedido
  
### <a name="getheaders"></a>GetHeaders
Obtenha os cabeçalhos de pedido.

  
**Devolve**: cabeçalhos de pedido