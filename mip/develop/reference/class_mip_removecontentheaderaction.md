---
title: class mip::RemoveContentHeaderAction
description: Documenta a classe mip::removecontentheaderaction da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: cf50f3ea6eeced3c8ab3699dd946174e508adeb1
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651382"
---
# <a name="class-mipremovecontentheaderaction"></a>class mip::RemoveContentHeaderAction 
Uma classe de ação que especifica a remover o cabeçalho de conteúdo do documento.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::vector\<std::string\>& GetUIElementNames()  |  Obtém uma lista de nomes que deve ser utilizado para localizar os elementos de interface do Usuário que devem ser removidos.
público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementnames-function"></a>Função de GetUIElementNames
Obtém uma lista de nomes que deve ser utilizado para localizar os elementos de interface do Usuário que devem ser removidos.

  
**Devolve**: Uma lista de nomes de elemento de interface do usuário.
  
### <a name="gettype-function"></a>Função de GetType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.