---
title: classe mip::FileExecutionState
description: Documenta a classe mip::fileexecutionstate da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: bdf0814e56d64bd16918a6f4d269a057620f92f5
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573127"
---
# <a name="class-mipfileexecutionstate"></a>classe mip::FileExecutionState 
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público GetDataState() virtual DataState const  |  Obtém o estado do conteúdo enquanto a aplicação está a interagir com ele.
std::shared_ptr virtual pública\<ClassificationResults\> GetClassificationResults (const std::shared_ptr\<FileHandler\> &, const Std:: vector\<std::shared_ptr\<ClassificationRequest\> \> &) const  |  Devolva um mapa dos resultados de classificação.
público virtual Std:: vector\<uint8_t\> GetSerializedProtectionInfo() const  |  Devolver uma memória intermédia com o PL. serializado
public virtual std::map\<std::string, std::string\> GetAuditMetadata() const  |  Devolva um mapa de pares de chave-valor de auditoria específicos de aplicativo.
  
## <a name="members"></a>Membros
  
### <a name="getdatastate-function"></a>Função de GetDataState
Obtém o estado do conteúdo enquanto a aplicação está a interagir com ele.

  
**Devolve**: Estado dos dados do conteúdo
  
### <a name="getclassificationresults-function"></a>Função de GetClassificationResults
Devolva um mapa dos resultados de classificação.

Parâmetros:  
* **fileHandler**:-o manipulador de arquivo do ficheiro utilizado 


* **classificationIds**: uma lista de IDs de classificação. 



  
**Devolve**: Uma lista de resultados de classificação.
  
### <a name="getserializedprotectioninfo-function"></a>Função de GetSerializedProtectionInfo
Devolver uma memória intermédia com o PL. serializado

  
**Devolve**: Uma memória intermédia com o PL. serializado
  
### <a name="getauditmetadata-function"></a>Função de GetAuditMetadata
Devolva um mapa de pares de chave-valor de auditoria específicos de aplicativo.

  
**Devolve**: Uma lista de pares de chave: valor registado de metadados do aplicativo específico de auditoria remetente: Id de e-mail para o remetente de destinatários: Representa uma matriz JSON de destinatários para um e-mail LastModifiedBy: Id de e-mail para o utilizador que o conteúdo LastModifiedDate da última modificação: Data que o conteúdo foi modificado pela última vez.