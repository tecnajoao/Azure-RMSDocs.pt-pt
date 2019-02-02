---
title: classe mip::FileExecutionState
description: Documenta a classe mip::fileexecutionstate da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 08a9064645f0ffb3ffbaa72f00db26c5b29d3643
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652341"
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