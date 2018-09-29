---
title: classe mip HttpDelegate
description: Referência para a classe mip HttpDelegate
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3e55f9aff5a9ebd97731ec21e408a33f22905648
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445377"
---
# <a name="class-miphttpdelegate"></a>classe mip::HttpDelegate 
Interface para substituir o tratamento de HTTP.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::shared_ptr<HttpResponse> enviar (const std::shared_ptr<HttpRequest>& pedido, const std::shared_ptr<void>& contexto)  |  Envie pedido de HTTP.
  
## <a name="members"></a>Membros
  
### <a name="httpresponse"></a>HttpResponse
Envie pedido de HTTP.

Parâmetros:  
* **pedido**: pedido HTTP 


* **contexto**: O mesmo contexto de cliente opaco, que foi passado para a API que resultaram neste pedido HTTP



  
**Devolve**: resposta HTTP