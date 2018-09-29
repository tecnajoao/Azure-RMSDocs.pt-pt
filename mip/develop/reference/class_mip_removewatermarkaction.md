---
title: classe mip RemoveWatermarkAction
description: Referência para a classe mip RemoveWatermarkAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 8f0b0a06088ed8a48e358c4ff9f005abf50db38f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445330"
---
# <a name="class-mipremovewatermarkaction"></a>classe mip::RemoveWatermarkAction 
Uma classe de ação que especifica a remover as marcas de água do documento.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público const Std:: vector < Std:: String > & GetUIElementNames()  |  Obtém uma lista de nomes que deve ser utilizado para localizar os elementos de interface do Usuário que devem ser removidos.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementnames"></a>GetUIElementNames
Obtém uma lista de nomes que deve ser utilizado para localizar os elementos de interface do Usuário que devem ser removidos.

  
**Devolve**: uma lista de nomes do elemento de interface do usuário.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.