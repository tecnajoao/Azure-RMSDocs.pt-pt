---
title: classe mip::FileExecutionState
description: Documenta a classe mip::fileexecutionstate da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 380e5f6732a2662d83b9bb37af5763ef30ffa3bf
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259223"
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
