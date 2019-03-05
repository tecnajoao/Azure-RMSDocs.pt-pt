---
title: classe mip::FileHandler
description: Documenta a classe mip::filehandler da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 997b3fbfb7dc302f7a47b5cfb281bdaf37c11295
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57332689"
---
# <a name="class-mipfilehandler"></a>classe mip::FileHandler 
Interface para o ficheiro de todas as funções de manipulação.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public std::shared_ptr\<ContentLabel\> GetLabel()  |  Começa a obter a etiqueta de sensibilidade do ficheiro.
public std::shared_ptr\<ProtectionHandler\> GetProtection()  |  Começa a obter a política de proteção do ficheiro.
ClassifyAsync void pública (const std::shared_ptr\<void\>& contexto)  |  Executa as regras no manipulador e retorna a lista de ações a ser executado.
SetLabel void pública (const Std:: String & labelId, const LabelingOptions & labelingOptions)  |  Define a etiqueta de sensibilidade para o ficheiro.
DeleteLabel void pública (const LabelingOptions & labelingOptions)  |  Elimina a etiqueta de sensibilidade a partir do ficheiro.
SetProtection void pública (const std::shared_ptr\<ProtectionDescriptor\>& protectionDescriptor)  |  Define as permissões personalizadas ou baseadas em modelos (de acordo com protectionDescriptor -> GetProtectionType) para o ficheiro.
SetProtection void pública (Std:: vector const\<uint8_t\>& serializedPublishingLicense, Std:: vector const\<uint8_t\>& serializedProtectionInfo)  |  Define as permissões de personalizados ou baseada em modelo (de acordo com serializedPublishingLicense e serializedProtectionInfo) para o ficheiro.
public void RemoveProtection()  |  Remove a proteção do ficheiro. Se o ficheiro tem o nome, a etiqueta serão perdida.
public void CommitAsync(const std::string& outputFilePath, const std::shared_ptr\<void\>& context) | Grava as alterações para o ficheiro especificado pelo \|outputFilePath\ |  parâmetro.
CommitAsync void pública (const std::shared_ptr\<Stream\>& outputStream, const std::shared_ptr\<void\>& contexto) | Grava as alterações no fluxo especificado pelo \|outputStream\ |  parâmetro.
public void GetDecryptedTemporaryFileAsync(const std::shared_ptr\<void\>& context)  |  Retorna um caminho para um arquivo temporário (que vai ser eliminado se possível) – que representam o conteúdo desencriptado.
public void NotifyCommitSuccessful(const std::string& contentIdentifier)  |  Para ser chamado quando as alterações foram confirmadas no disco.
public std::string GetOutputFileName()  |  Calcula o nome de ficheiro de saída e a extensão com base no nome do ficheiro original e as alterações acumuladas.
  
## <a name="members"></a>Membros
  
### <a name="getlabel-function"></a>Função de GetLabel
Começa a obter a etiqueta de sensibilidade do ficheiro.
  
### <a name="getprotection-function"></a>Função de GetProtection
Começa a obter a política de proteção do ficheiro.
  
### <a name="classifyasync-function"></a>Função de ClassifyAsync
Executa as regras no manipulador e retorna a lista de ações a ser executado.

  
**Devolve**: Lista de ações que devem ser aplicadas no conteúdo.
  
### <a name="setlabel-function"></a>Função de SetLabel
Define a etiqueta de sensibilidade para o ficheiro.
As alterações não ser gravadas no arquivo até que seja chamado CommitAsync. Com privilégios e o método de automática permite que a API para substituir qualquer lança etiqueta existente [JustificationRequiredError](class_mip_justificationrequirederror.md) quando definir a etiqueta precisa da operação para ser justificada (por meio do parâmetro de labelingOptions).
  
### <a name="deletelabel-function"></a>Função de DeleteLabel
Elimina a etiqueta de sensibilidade a partir do ficheiro.
As alterações não ser gravadas no arquivo até que seja chamado CommitAsync. Com privilégios e o método de automática permite que a API para substituir qualquer lança etiqueta existente [JustificationRequiredError](class_mip_justificationrequirederror.md) quando definir a etiqueta precisa da operação para ser justificada (por meio do parâmetro de labelingOptions).
  
### <a name="setprotection-function"></a>Função de SetProtection
Define as permissões personalizadas ou baseadas em modelos (de acordo com protectionDescriptor -> GetProtectionType) para o ficheiro.
As alterações não ser gravadas no arquivo até que seja chamado CommitAsync.
  
### <a name="setprotection-function"></a>Função de SetProtection
Define as permissões de personalizados ou baseada em modelo (de acordo com serializedPublishingLicense e serializedProtectionInfo) para o ficheiro.
As alterações não ser gravadas no arquivo até que seja chamado CommitAsync.
  
### <a name="removeprotection-function"></a>Função de RemoveProtection
Remove a proteção do ficheiro. Se o ficheiro tem o nome, a etiqueta serão perdida.
As alterações não ser gravadas no arquivo até que seja chamado CommitAsync.
  
### <a name="commitasync-function"></a>Função de CommitAsync
Grava as alterações para o ficheiro especificado pelo | outputFilePath | parâmetro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.
  
### <a name="commitasync-function"></a>Função de CommitAsync
Grava as alterações no fluxo especificado pelo | outputStream | parâmetro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.
  
### <a name="getdecryptedtemporaryfileasync-function"></a>Função de GetDecryptedTemporaryFileAsync
Retorna um caminho para um arquivo temporário (que vai ser eliminado se possível) – que representam o conteúdo desencriptado.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.
  
### <a name="notifycommitsuccessful-function"></a>Função de NotifyCommitSuccessful
Para ser chamado quando as alterações foram confirmadas no disco.

Parâmetros:  
* **contentIdentifier**: exemplo de um arquivo: Exemplo de "C:\mip-sdk-for-cpp\files\audit.docx" [path\filename] para uma mensagem de e-mail: "RE: Auditoria design:user1@contoso.com"[assunto: remetente] 


É acionado um evento de auditoria
  
### <a name="getoutputfilename-function"></a>GetOutputFileName function
Calcula o nome de ficheiro de saída e a extensão com base no nome do ficheiro original e as alterações acumuladas.
