---
title: classe mip ApplyLabelAction
description: Referência para a classe mip ApplyLabelAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 06a17ef1e60503cfb7d690bea9bb72316544f16d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445772"
---
# <a name="class-mipapplylabelaction"></a>classe mip::ApplyLabelAction 
Aplicar ações de etiqueta requer que o aplicativo de chamada para aplicar uma etiqueta específica.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetLabelId() const  |  Obtenha o ID de etiqueta necessário.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getlabelid"></a>GetLabelId
Obtenha o ID de etiqueta necessário.

  
**Devolve**: O ID da etiqueta.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.