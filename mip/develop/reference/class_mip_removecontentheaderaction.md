---
title: classe mip RemoveContentHeaderAction
description: Referência para a classe mip RemoveContentHeaderAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: dc79ebf5d5c7cd35a8fc5ed854315179ed9190f0
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446452"
---
# <a name="class-mipremovecontentheaderaction"></a>classe mip::RemoveContentHeaderAction 
Uma classe de ação que especifica a remover o cabeçalho de conteúdo do documento.
  
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