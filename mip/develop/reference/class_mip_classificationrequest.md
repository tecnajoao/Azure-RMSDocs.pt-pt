---
title: classe mip::ClassificationRequest
description: Documenta a classe mip::classificationrequest da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 3fddd870b6aebb9f5209fc43160c32d87b1d7129
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573745"
---
# <a name="class-mipclassificationrequest"></a>classe mip::ClassificationRequest 
Classe que contém o pedido de uma chamada de classificação no estado de execução.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public std::string GetClassificationId() const  |  Obtenha o ID da política de classificação.
public std::string GetRulePackageId() const  |  Obtenha o ID do pacote de regra.
  
## <a name="members"></a>Membros
  
### <a name="getclassificationid-function"></a>Função de GetClassificationId
Obtenha o ID da política de classificação.

  
**Devolve**: ID da política de classificação.
  
### <a name="getrulepackageid-function"></a>GetRulePackageId function
Obtenha o ID do pacote de regra.

  
**Devolve**: ID do pacote de regra. classificações pré-criados serão definidas como um guid vazio.