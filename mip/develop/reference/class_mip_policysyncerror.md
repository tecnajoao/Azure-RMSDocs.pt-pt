---
title: classe mip PolicySyncError
description: Referência para a classe mip PolicySyncError
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 29b107f94303d39a233b798996d1ee9fd28b3b40
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446966"
---
# <a name="class-mippolicysyncerror"></a>classe mip::PolicySyncError 
Falha ao tentar sincronizar dados de política.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 char pública const * what() const  |  Obter a mensagem de erro.
público std::shared_ptr<Error> const clone)  |  Clone o erro.
 público GetErrorType() virtual ErrorType const  |  Obter o tipo de erro.
 público virtual const Std:: String & GetErrorName() const  |  Obtenha o nome do erro.
 público virtual const Std:: String & const GetMessage)  |  Obter a mensagem de erro.
 SetMessage de void virtual público (const Std:: String & msg)  |  Defina a mensagem de erro.
  
## <a name="members"></a>Membros
  
### <a name="what"></a>o que
Obter a mensagem de erro.

  
**Devolve**: A mensagem de erro
  
### <a name="error"></a>Error
Clone o erro.

  
**Devolve**: um clone do erro.
  
### <a name="errortype"></a>ErrorType
Obter o tipo de erro.

  
**Devolve**: O tipo de erro.
  
### <a name="geterrorname"></a>GetErrorName
Obtenha o nome do erro.

  
**Devolve**: O nome do erro.
  
### <a name="getmessage"></a>GetMessage
Obter a mensagem de erro.

  
**Devolve**: A mensagem de erro.
  
### <a name="setmessage"></a>SetMessage
Defina a mensagem de erro.

Parâmetros:  
* **msg**: a mensagem de erro.

