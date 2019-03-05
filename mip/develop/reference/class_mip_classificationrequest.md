---
title: classe mip::ClassificationRequest
description: Documenta a classe mip::classificationrequest da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 61846ef3b8273169e9cf38eaa173eac3ba18dae6
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330528"
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
