---
title: classe mip::FileHandler::Observer
description: Documenta a classe mip::filehandler da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: f6362eab61228cdb161f514c643563f9c45a0857
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254752"
---
# <a name="class-mipfilehandlerobserver"></a>classe mip::FileHandler::Observer 
[Observador](class_mip_filehandler_observer.md) interface para que os clientes obter notificações de eventos relacionados com o manipulador de arquivo.
Todos os erros herdam [mip::Error](class_mip_error.md). Cliente não deve chamar o mecanismo de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public virtual void OnCreateFileHandlerSuccess(const std::shared_ptr\<FileHandler\>& fileHandler, const std::shared_ptr\<void\>& context)  |  Chamado quando o manipulador é criado com êxito.
OnCreateFileHandlerFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a falha ao criar o manipulador.
OnClassifySuccess de void virtual público (Std:: vector const\<std::shared_ptr\<ação\>\>& ações, const std::shared_ptr\<void\>& contexto)  |  Chamado quando classificar êxito.
OnClassifyFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando classificar falhou.
public virtual void OnGetDecryptedTemporaryFileSuccess(const std::string& decryptedFilePath, const std::shared_ptr\<void\>& context)  |  Chamado quando a obter o êxito do ficheiro temporário desencriptada.
public virtual void OnGetDecryptedTemporaryFileFailure(const std::exception_ptr& error, const std::shared_ptr\<void\>& context)  |  Chamado quando o ficheiro temporário desencriptado falhou a obter.
OnCommitSuccess de void virtual público (bool confirmada, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a consolidar as alterações no ficheiro foram bem-sucedidas.
OnCommitFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr\<void\>& contexto)  |  Chamado quando a falha ao consolidar as alterações ao ficheiro.
  
## <a name="members"></a>Membros
  
### <a name="oncreatefilehandlersuccess-function"></a>Função de OnCreateFileHandlerSuccess
Chamado quando o manipulador é criado com êxito.
  
### <a name="oncreatefilehandlerfailure-function"></a>Função de OnCreateFileHandlerFailure
Chamado quando a falha ao criar o manipulador.
  
### <a name="onclassifysuccess-function"></a>Função de OnClassifySuccess
Chamado quando classificar êxito.
  
### <a name="onclassifyfailure-function"></a>Função de OnClassifyFailure
Chamado quando classificar falhou.
  
### <a name="ongetdecryptedtemporaryfilesuccess-function"></a>OnGetDecryptedTemporaryFileSuccess function
Chamado quando a obter o êxito do ficheiro temporário desencriptada.
  
### <a name="ongetdecryptedtemporaryfilefailure-function"></a>Função de OnGetDecryptedTemporaryFileFailure
Chamado quando o ficheiro temporário desencriptado falhou a obter.
  
### <a name="oncommitsuccess-function"></a>Função de OnCommitSuccess
Chamado quando a consolidar as alterações no ficheiro foram bem-sucedidas.
  
### <a name="oncommitfailure-function"></a>Função de OnCommitFailure
Chamado quando a falha ao consolidar as alterações ao ficheiro.
