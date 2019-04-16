---
title: classe mip::HttpDelegate
description: Documenta a classe mip::httpdelegate da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 6dedd5e52b0599a58acabd85f7bd076169b3758e
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574198"
---
# <a name="class-miphttpdelegate"></a>classe mip::HttpDelegate 
Interface para substituir o tratamento de HTTP.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::shared_ptr\<HttpOperation\> enviar (const std::shared_ptr\<HttpRequest\>& pedido, const std::shared_ptr\<void\>& contexto)  |  Envie pedido de HTTP.
pública std::shared_ptr\<HttpOperation\> SendAsync (const std::shared_ptr\<HttpRequest\>& pedido, const std::shared_ptr\<void\>& context, const std:: função\<void (std::shared_ptr\<HttpOperation\>)\>& callbackFn)  |  Envie pedido de HTTP de forma assíncrona.
CancelOperation void pública (const Std:: String & requestId)  |  Cancele uma operação HTTP específica.
público CancelAllOperations() void  |  Cancele pedidos HTTP em curso.
  
## <a name="members"></a>Membros
  
### <a name="send-function"></a>Enviar a função
Envie pedido de HTTP.

Parâmetros:  
* **request**: Pedido HTTP 


* **context**: O mesmo contexto de cliente opaco, que foi passado para a API que resultaram neste pedido HTTP



  
**Devolve**: Contentor de operação de HTTP
  
### <a name="sendasync-function"></a>Função de SendAsync
Envie pedido de HTTP de forma assíncrona.

Parâmetros:  
* **request**: Pedido HTTP 


* **context**: O mesmo contexto de cliente opaco, que foi passado para a API que resultaram neste pedido HTTP 


* **callbackFn**: Função que será executada após a conclusão



  
**Devolve**: Contentor de operação de HTTP
  
### <a name="canceloperation-function"></a>Função de CancelOperation
Cancele uma operação HTTP específica.

Parâmetros:  
* **requestId**: ID do pedido de cancelamento


  
### <a name="cancelalloperations-function"></a>Função de CancelAllOperations
Cancele pedidos HTTP em curso.