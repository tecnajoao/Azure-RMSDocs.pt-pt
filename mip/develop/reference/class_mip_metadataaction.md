---
title: classe mip::MetadataAction
description: Documenta a classe mip::metadataaction da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 677de5965c0fe506af3731c2b54b4faaab225471
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573382"
---
# <a name="class-mipmetadataaction"></a>classe mip::MetadataAction 
Uma [ação](class_mip_action.md) que adiciona informações de metadados para o conteúdo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::vector\<std::string\>& GetMetadataToRemove() const  |  Obter a lista de nomes dos metadados que devem ser removidos do conteúdo.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetMetadataToAdd() const  |  Obter os metadados de pares nome/valor que devem ser adicionados ao conteúdo.
público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).

## <a name="members"></a>Membros
  
### <a name="getmetadatatoremove-function"></a>Função de GetMetadataToRemove
Obter a lista de nomes dos metadados que devem ser removidos do conteúdo.

  
**Devolve**: Um vetor de cadeias de caracteres para remover. remover metadados deve ser feito antes de adicionar metadados.
  
### <a name="getmetadatatoadd-function"></a>Função de GetMetadataToAdd
Obter os metadados de pares nome/valor que devem ser adicionados ao conteúdo.

  
**Devolve**: Const Std:: vector < std::pair < Std:: String, Std:: String >> & remover metadados devem ser feitas antes de adicionar metadados.


### <a name="gettype-function"></a>Função de GetType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.