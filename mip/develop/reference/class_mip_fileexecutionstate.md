---
title: classe mip::FileExecutionState
description: Documenta a classe mip::fileexecutionstate da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 9433ca2f47496e0d28d46c68b3100b53cd25c3f3
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333692"
---
# <a name="class-mipfileexecutionstate"></a>classe mip::FileExecutionState 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
std::map virtual pública\<Std:: String, std::shared_ptr\<ClassificationResult\> \> GetClassificationResults (const std::shared_ptr\<FileHandler\> &, const e padrão :: vector\<std::shared_ptr\<ClassificationRequest\> \> &) const  |  Devolva um mapa dos resultados de classificação.
público virtual Std:: vector\<uint8_t\> GetSerializedProtectionInfo() const  |  Devolver uma memória intermédia com o PL. serializado
  
## <a name="members"></a>Membros
  
### <a name="getclassificationresults-function"></a>Função de GetClassificationResults
Devolva um mapa dos resultados de classificação.

Parâmetros:  
* **fileHandler**:-o manipulador de arquivo do ficheiro utilizado 


* **classificationIds**: uma lista de IDs de classificação. 



  
**Devolve**: Uma lista de resultados de classificação.
  
### <a name="getserializedprotectioninfo-function"></a>Função de GetSerializedProtectionInfo
Devolver uma memória intermédia com o PL. serializado

  
**Devolve**: Uma memória intermédia com o PL. serializado
