---
title: classe mip::ContentLabel
description: Documenta a classe mip::contentlabel da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 96f8cca48f385a21685e93eb5bc57abac571975c
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573024"
---
# <a name="class-mipcontentlabel"></a>classe mip::ContentLabel 
Abstração para uma etiqueta do Microsoft Information Protection que é aplicada a uma parte do conteúdo, normalmente, um documento.
Ele também contém propriedades para a instância de uma etiqueta aplicada específico.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::chrono::time_point\<std::chrono::system_clock\> GetCreationTime() const  |  Obter a hora de criação da etiqueta.
público GetAssignmentMethod() de AssignmentMethod const  |  Obtenha o método de atribuição da etiqueta.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetExtendedProperties() const  |  Obtém as Propriedades estendidas.
bool pública IsProtectionAppliedFromLabel() const  |  Obtém se a proteção foi aplicada pela etiqueta ou não.
público std::shared_ptr\<etiqueta\> const getlabel)  |  Obtenha o objeto de rótulo real aplicadas no conteúdo.
  
## <a name="members"></a>Membros
  
### <a name="getcreationtime-function"></a>GetCreationTime função
Obter a hora de criação da etiqueta.

  
**Devolve**: Hora de criação.
  
### <a name="getassignmentmethod-function"></a>Função de GetAssignmentMethod
Obtenha o método de atribuição da etiqueta.

  
**Devolve**: AssignmentMethod STANDARD | PRIVILEGED | AUTOMÁTICA. 
  
**Consulte também**: [mip::AssignmentMethod](mip-enums-and-structs.md#assignmentmethod)
  
### <a name="getextendedproperties-function"></a>Função de GetExtendedProperties
Obtém as Propriedades estendidas.

  
**Devolve**: Propriedades expandidas.
  
### <a name="isprotectionappliedfromlabel-function"></a>Função de IsProtectionAppliedFromLabel
Obtém se a proteção foi aplicada pela etiqueta ou não.

  
**Devolve**: TRUE se existir proteção de modelo e era por esta etiqueta, caso contrário falsa.
  
### <a name="getlabel-function"></a>Função de GetLabel
Obtenha o objeto de rótulo real aplicadas no conteúdo.

  
**Devolve**: O objeto de etiqueta aplicado no conteúdo. 
  
**Consulte também**: [mip::Label](class_mip_label.md)