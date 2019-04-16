---
title: classe mip::ClassificationResult
description: Documenta a classe mip::classificationresult da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 6a048dd7902e8148e4f32f8cc9e62d63110b2b4a
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573569"
---
# <a name="class-mipclassificationresult"></a>classe mip::ClassificationResult 
Classe que contém o resultado de uma chamada de classificação no estado de execução.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public std::string GetId() const  |  Obtenha o ID da política de classificação.
público int GetCount() const  |  Obter a contagem de instâncias.
público int GetConfidenceLevel() const  |  Obtenha a confiança no resultado.
public std::string GetSensitiveInformationDetections() const  |  Obtenha as deteções de informações confidenciais.
  
## <a name="members"></a>Membros
  
### <a name="getid-function"></a>Função de GetId
Obtenha o ID da política de classificação.

  
**Devolve**: ID da política de classificação.
  
### <a name="getcount-function"></a>Função de GetCount
Obter a contagem de instâncias.

  
**Devolve**: A contagem de instâncias.
  
### <a name="getconfidencelevel-function"></a>Função de GetConfidenceLevel
Obtenha a confiança no resultado.
  
### <a name="getsensitiveinformationdetections-function"></a>Função de GetSensitiveInformationDetections
Obtenha as deteções de informações confidenciais.

  
**Devolve**: Cadeia de caracteres do JSON de todas as detecções de informações confidenciais.