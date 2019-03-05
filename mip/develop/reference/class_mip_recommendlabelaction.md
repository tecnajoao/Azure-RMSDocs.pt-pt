---
title: class mip::RecommendLabelAction
description: Documenta a classe mip::recommendlabelaction da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 085bcd9438c1a4753cde6a9c99036cc7cb53e440
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57332621"
---
# <a name="class-miprecommendlabelaction"></a>class mip::RecommendLabelAction 
Recomendamos a ações de etiqueta destina-se a sugerir uma etiqueta para os utilizadores. Suprimir esta chamada depois que um utilizador ignora a etiqueta recomendada deve ser feito por meio de ações suportadas sobre o estado de execução.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetLabelId() const  |  Obtenha o ID de etiqueta sugerido.
public const std::vector\<std::string\>& GetClassificationIds() const  |  Obter os IDs de classificação que correspondentes e causou esta etiqueta apareça.
público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getlabelid-function"></a>Função de GetLabelId
Obtenha o ID de etiqueta sugerido.

  
**Devolve**: O ID da etiqueta.
  
### <a name="getclassificationids-function"></a>Função de GetClassificationIds
Obter os IDs de classificação que correspondentes e causou esta etiqueta apareça.

  
**Devolve**: & Obter uma lista de IDs que causou esta etiqueta apareça de classificação de Const Std:: vector < Std:: String >.
  
### <a name="gettype-function"></a>Função de GetType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.
