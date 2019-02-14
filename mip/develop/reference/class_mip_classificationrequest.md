---
title: classe mip::ClassificationRequest
description: Documenta a classe mip::classificationrequest da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 81e9a7276b78817f3d2f409cc403992284d23ceb
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259155"
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
