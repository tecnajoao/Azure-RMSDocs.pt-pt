---
title: classe mip ContentLabel
description: Referência para a classe mip ContentLabel
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: c105f620ed2cd3d6f1427f2543784ea66ce2c4d7
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446027"
---
# <a name="class-mipcontentlabel"></a>classe mip::ContentLabel 
Abstração para uma etiqueta do Microsoft Information Protection que é aplicada a uma parte do conteúdo, normalmente, um documento.
Ele também contém propriedades para a instância de uma etiqueta aplicada específico.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetCreationTime() const  |  Obter a hora de criação da etiqueta.
 público GetAssignmentMethod() de AssignmentMethod const  |  Obtenha o método de atribuição da etiqueta.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetExtendedProperties() const  |  Obtém as Propriedades estendidas.
 bool pública IsProtectionAppliedFromLabel() const  |  Obtém se a proteção foi aplicada pela etiqueta ou não.
público std::shared_ptr<Label> const getlabel)  |  Obtenha o objeto de rótulo real aplicadas no conteúdo.
  
## <a name="members"></a>Membros
  
### <a name="getcreationtime"></a>GetCreationTime
Obter a hora de criação da etiqueta.

  
**Devolve**: hora de criação como uma cadeia de GMT.
  
### <a name="getassignmentmethod"></a>GetAssignmentMethod
Obtenha o método de atribuição da etiqueta.

  
**Devolve**: AssignmentMethod STANDARD | PRIVILEGED | AUTOMÁTICA. 
  
**Consulte também**: mip::AssignmentMethod
  
### <a name="getextendedproperties"></a>GetExtendedProperties
Obtém as Propriedades estendidas.

  
**Devolve**: Propriedades estendidas.
  
### <a name="isprotectionappliedfromlabel"></a>IsProtectionAppliedFromLabel
Obtém se a proteção foi aplicada pela etiqueta ou não.

  
**Devolve**: True se existir proteção de modelo e era por esta etiqueta, caso contrário falsa.
  
### <a name="label"></a>Etiqueta
Obtenha o objeto de rótulo real aplicadas no conteúdo.

  
**Devolve**: O objeto de etiqueta aplicado no conteúdo. 
  
**Consulte também**: [mip::Label](class_mip_label.md)