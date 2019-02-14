---
title: classe mip::HttpDelegate
description: Documenta a classe mip::httpdelegate da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 8dd81508766c65d6232c278d56f3720a98aaa9eb
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256299"
---
# <a name="class-miphttpdelegate"></a>classe mip::HttpDelegate 
Interface para substituir o tratamento de HTTP.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::shared_ptr\<HttpResponse\> enviar (const std::shared_ptr\<HttpRequest\>& pedido, const std::shared_ptr\<void\>& contexto)  |  Envie pedido de HTTP.
SendAsync void pública (const std::shared_ptr\<HttpRequest\>& pedido, const std::shared_ptr\<void\>& context, const std::function\<void(std::shared_ptr\<HttpResponse\>)\>& fnCallback)  | _Ainda não documentado._
  
## <a name="members"></a>Membros
  
### <a name="send-function"></a>Enviar a função
Envie pedido de HTTP.

Parâmetros:  
* **request**: Pedido HTTP 


* **context**: O mesmo contexto de cliente opaco, que foi passado para a API que resultaram neste pedido HTTP



  
**Devolve**: Resposta HTTP
  
### <a name="sendasync-function"></a>Função de SendAsync
_Não documentados ainda._
