---
title: classe mip::HttpResponse
description: Documenta a classe mip::httpresponse da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 9cbd899548be15833456a7c1e1fe34c3b5629717
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650297"
---
# <a name="class-miphttpresponse"></a>classe mip::HttpResponse 
Interface que descreve uma única resposta HTTP, implementada pela aplicação de cliente, ao substituir [HttpDelegate](class_mip_httpdelegate.md).
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public int32_t GetStatusCode() const  |  Obter o código de estado de resposta.
public const std::string& GetBody() const  |  Obtenha o corpo do pedido.
public const std::map\<std::string, std::string, CaseInsensitiveComparator\>& GetHeaders() const  |  Obtenha os cabeçalhos de pedido.
  
## <a name="members"></a>Membros
  
### <a name="getstatuscode-function"></a>Função de GetStatusCode
Obter o código de estado de resposta.

  
**Devolve**: Código de estado
  
### <a name="getbody-function"></a>Função de GetBody
Obtenha o corpo do pedido.

  
**Devolve**: Corpo do pedido
  
### <a name="getheaders-function"></a>Função de GetHeaders
Obtenha os cabeçalhos de pedido.

  
**Devolve**: Cabeçalhos do pedido