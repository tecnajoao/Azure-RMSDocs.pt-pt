---
title: classe mip FileHandler
description: Referência para a classe mip FileHandler
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: efae18bdc10f8878f255f35c608a50482a29887b
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446129"
---
# <a name="class-mipfilehandler"></a>classe mip::FileHandler 
Interface para o ficheiro de todas as funções de manipulação.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
GetLabelAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a obter a etiqueta de sensibilidade do ficheiro.
GetProtectionAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a obter a política de proteção do ficheiro.
 SetLabel void pública (const Std:: String & labelId, const LabelingOptions & labelingOptions)  |  Define a etiqueta de sensibilidade para o ficheiro.
 DeleteLabel void pública (const LabelingOptions & labelingOptions)  |  Elimina a etiqueta de sensibilidade a partir do ficheiro.
SetProtection void pública (const std::shared_ptr<ProtectionDescriptor>& protectionDescriptor)  |  Define as permissões personalizadas ou baseadas em modelos (de acordo com protectionDescriptor -> GetProtectionType) para o ficheiro.
 público RemoveProtection() void  |  Remove a proteção do ficheiro. Se o ficheiro tem o nome, a etiqueta serão perdida.
CommitAsync void pública (Std:: String const & outputFilePath, const std::shared_ptr<void>& contexto) | Grava as alterações para o ficheiro especificado pelo \|outputFilePath\ |  parâmetro.
CommitAsync void pública (const std::shared_ptr<Stream>& outputStream, const std::shared_ptr<void>& contexto) | Grava as alterações no fluxo especificado pelo \|outputStream\ |  parâmetro.
 NotifyCommitSuccessful void pública (const Std:: String & contentIdentifier)  |  Para ser chamado quando as alterações foram confirmadas no disco.
 público Std:: String GetOutputFileName()  |  Calcula o nome de ficheiro de saída e a extensão com base no nome do ficheiro original e as alterações acumuladas.
  
## <a name="members"></a>Membros
  
### <a name="getlabelasync"></a>GetLabelAsync
Começa a obter a etiqueta de sensibilidade do ficheiro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.

Parâmetros:  
* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="getprotectionasync"></a>GetProtectionAsync
Começa a obter a política de proteção do ficheiro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.

Parâmetros:  
* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="setlabel"></a>SetLabel
Define a etiqueta de sensibilidade para o ficheiro.
As alterações não ser gravadas no arquivo até que seja chamado CommitAsync. Com privilégios e o método de automática permite que a API para substituir qualquer lança etiqueta existente [JustificationRequiredError](class_mip_justificationrequirederror.md) quando definir a etiqueta precisa da operação para ser justificada (por meio do parâmetro de labelingOptions).
  
### <a name="deletelabel"></a>DeleteLabel
Elimina a etiqueta de sensibilidade a partir do ficheiro.
As alterações não ser gravadas no arquivo até que seja chamado CommitAsync. Com privilégios e o método de automática permite que a API para substituir qualquer lança etiqueta existente [JustificationRequiredError](class_mip_justificationrequirederror.md) quando definir a etiqueta precisa da operação para ser justificada (por meio do parâmetro de labelingOptions).
  
### <a name="setprotection"></a>SetProtection
Define as permissões personalizadas ou baseadas em modelos (de acordo com protectionDescriptor -> GetProtectionType) para o ficheiro.
As alterações não ser gravadas no arquivo até que seja chamado CommitAsync.
  
### <a name="removeprotection"></a>RemoveProtection
Remove a proteção do ficheiro. Se o ficheiro tem o nome, a etiqueta serão perdida.
As alterações não ser gravadas no arquivo até que seja chamado CommitAsync.
  
### <a name="commitasync"></a>CommitAsync
Grava as alterações para o ficheiro especificado pelo | outputFilePath | parâmetro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.
  
### <a name="commitasync"></a>CommitAsync
Grava as alterações no fluxo especificado pelo | outputStream | parâmetro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.
  
### <a name="notifycommitsuccessful"></a>NotifyCommitSuccessful
Para ser chamado quando as alterações foram confirmadas no disco.

Parâmetros:  
* **contentIdentifier**: exemplo de um ficheiro: "C:\mip-sdk-for-cpp\files\audit.docx" [caminho] de exemplo para uma mensagem de e-mail: "RE: auditoria design:user1@contoso.com" [assunto: remetente] 


É acionado um evento de auditoria
  
### <a name="getoutputfilename"></a>GetOutputFileName
Calcula o nome de ficheiro de saída e a extensão com base no nome do ficheiro original e as alterações acumuladas.