---
title: classe mip RecommendLabelAction
description: Referência para a classe mip RecommendLabelAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b8e56daed967523b7580087d7bb934c1b2164320
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446010"
---
# <a name="class-miprecommendlabelaction"></a>classe mip::RecommendLabelAction 
Recomendamos a ações de etiqueta destina-se a sugerir uma etiqueta para os utilizadores. Suprimir esta chamada depois que um utilizador ignora a etiqueta recomendada deve ser feito por meio de ações suportadas sobre o estado de execução.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetLabelId() const  |  Obtenha o ID de etiqueta sugerido.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getlabelid"></a>GetLabelId
Obtenha o ID de etiqueta sugerido.

  
**Devolve**: O ID da etiqueta.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.