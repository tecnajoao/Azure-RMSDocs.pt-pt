---
title: classe mip::ClassificationRequest
description: Documenta a classe mip::classificationrequest da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: a7350961af4c2e5d63211840382ee7a0b701f1c4
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652035"
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