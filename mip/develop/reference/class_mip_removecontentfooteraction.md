---
title: class mip::RemoveContentFooterAction
description: Documenta a classe mip::removecontentfooteraction da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 14afd4688c13f419ab3019e9c268ba7d355121c8
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574266"
---
# <a name="class-mipremovecontentfooteraction"></a>class mip::RemoveContentFooterAction 
Uma classe de ação que especifica a remover o rodapé de conteúdo do documento.
  
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