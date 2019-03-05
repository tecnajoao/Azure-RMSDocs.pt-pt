---
title: classe mip::MetadataAction
description: Documenta a classe mip::metadataaction da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: c180072eec94b2f71471c10b4344d65321ef49c6
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57332417"
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
