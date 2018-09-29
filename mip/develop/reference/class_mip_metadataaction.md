---
title: classe mip MetadataAction
description: Referência para a classe mip MetadataAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 8f7480775a0226c7161c9ad770184e54427a5084
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47444624"
---
# <a name="class-mipmetadataaction"></a>classe mip::MetadataAction 
Uma [ação](class_mip_action.md) que adiciona informações de metadados para o conteúdo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público const Std:: vector < Std:: String > & GetMetadataToRemove() const  |  Obter a lista de nomes dos metadados que devem ser removidos do conteúdo.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetMetadataToAdd() const  |  Obter os metadados de pares nome/valor que devem ser adicionados ao conteúdo.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Obter a lista de nomes dos metadados que devem ser removidos do conteúdo.

  
**Devolve**: um vetor de cadeias de caracteres para remover. remover metadados deve ser feito antes de adicionar metadados.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Obter os metadados de pares nome/valor que devem ser adicionados ao conteúdo.

  
**Devolve**: Const Std:: vector < std::pair < Std:: String, Std:: String >> & remover metadados devem ser feitas antes de adicionar metadados.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.