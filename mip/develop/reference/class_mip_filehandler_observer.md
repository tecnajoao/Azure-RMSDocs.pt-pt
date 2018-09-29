---
title: classe mip FileHandler observador
description: Referência para a classe mip FileHandler observador
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a587107afc2b8963d64c31ad47af81761bf2b9f8
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446190"
---
# <a name="class-mipfilehandlerobserver"></a>classe mip::FileHandler::Observer 
[Observador](class_mip_filehandler_observer.md) interface para que os clientes obter notificações de eventos relacionados com o manipulador de arquivo.
Todos os erros herdam [mip::Error](class_mip_error.md). Cliente não deve chamar o mecanismo de volta no thread que chama o observador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
OnCreateFileHandlerSuccess de void virtual público (const std::shared_ptr<FileHandler>& fileHandler, const std::shared_ptr<void>& contexto)  |  Chamado quando o manipulador é criado com êxito.
OnCreateFileHandlerFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a falha ao criar o manipulador.
OnGetLabelSuccess de void virtual público (const std::shared_ptr<ContentLabel>& etiqueta, const std::shared_ptr<void>& contexto)  |  Chamado quando a etiqueta é recuperada com êxito.
OnGetLabelFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a falha ao obter a etiqueta.
OnGetProtectionSuccess de void virtual público (const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& contexto)  |  Chamado quando a política de proteção é obtida com êxito.
OnGetProtectionFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a falha ao obter a política de proteção.
OnCommitSuccess de void virtual público (bool confirmada, const std::shared_ptr<void>& contexto)  |  Chamado quando a consolidar as alterações no ficheiro foram bem-sucedidas.
OnCommitFailure de void virtual público (const std::exception_ptr e erro, const std::shared_ptr<void>& contexto)  |  Chamado quando a falha ao consolidar as alterações ao ficheiro.
  
## <a name="members"></a>Membros
  
### <a name="oncreatefilehandlersuccess"></a>OnCreateFileHandlerSuccess
Chamado quando o manipulador é criado com êxito.
  
### <a name="oncreatefilehandlerfailure"></a>OnCreateFileHandlerFailure
Chamado quando a falha ao criar o manipulador.
  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
Chamado quando a etiqueta é recuperada com êxito.
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
Chamado quando a falha ao obter a etiqueta.
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
Chamado quando a política de proteção é obtida com êxito.
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
Chamado quando a falha ao obter a política de proteção.
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
Chamado quando a consolidar as alterações no ficheiro foram bem-sucedidas.
  
### <a name="oncommitfailure"></a>OnCommitFailure
Chamado quando a falha ao consolidar as alterações ao ficheiro.