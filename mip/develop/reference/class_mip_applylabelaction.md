---
title: classe mip::ApplyLabelAction
description: Documenta a classe mip::applylabelaction da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: ce813a544504ce18b382cdb86bd31d89b6626fad
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650498"
---
# <a name="class-mipapplylabelaction"></a>classe mip::ApplyLabelAction 
Aplicar ações de etiqueta requer que o aplicativo de chamada para aplicar uma etiqueta específica.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetLabelId() const  |  Obtenha o ID de etiqueta necessário.
public const std::vector\<std::string\>& GetClassificationIds() const  |  Obter os IDs de classificação que correspondentes e causou esta etiqueta apareça.
público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getlabelid-function"></a>Função de GetLabelId
Obtenha o ID de etiqueta necessário.

  
**Devolve**: O ID da etiqueta.
  
### <a name="getclassificationids-function"></a>Função de GetClassificationIds
Obter os IDs de classificação que correspondentes e causou esta etiqueta apareça.

  
**Devolve**: & Obter uma lista de IDs que causou esta etiqueta apareça de classificação de Const Std:: vector < Std:: String >.
  
### <a name="gettype-function"></a>Função de GetType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.