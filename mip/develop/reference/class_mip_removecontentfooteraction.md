---
title: classe mip RemoveContentFooterAction
description: Referência para a classe mip RemoveContentFooterAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: d275e2256c8a65bf63fd16d5761f42563d7a7f07
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445636"
---
# <a name="class-mipremovecontentfooteraction"></a>classe mip::RemoveContentFooterAction 
Uma classe de ação que especifica a remover o rodapé de conteúdo do documento.
  
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