---
title: classe mip::UserRights
description: Documenta a classe mip::userrights da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 148b1b1a9f70cc87c3297c69e1e9ffa67af34cf4
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573586"
---
# <a name="class-mipuserrights"></a>classe mip::UserRights 
Um grupo de utilizadores e os direitos associados aos mesmos.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public UserRights(const std::vector\<std::string\>& users, const std::vector\<std::string\>& rights)  |  [UserRights](class_mip_userrights.md) construtor.
public const std::vector\<std::string\>& Users() const  |  Obtém os utilizadores associados a um conjunto de direitos.
público const Std:: vector\<Std:: String\>& Rights() const  |  Obtém os direitos associados um grupo de utilizadores.
  
## <a name="members"></a>Membros
  
### <a name="userrights-function"></a>Função de UserRights
[UserRights](class_mip_userrights.md) construtor.

Parâmetros:  
* **Os utilizadores**: Grupo de usuários que compartilham os mesmos direitos 


* **direitos**: Direitos partilhados por grupo de utilizadores


  
### <a name="users-function"></a>Função de utilizadores
Obtém os utilizadores associados a um conjunto de direitos.

  
**Devolve**: Utilizadores associados a um conjunto de direitos
  
### <a name="rights-function"></a>Função de direitos
Obtém os direitos associados um grupo de utilizadores.

  
**Devolve**: Direitos associados um grupo de utilizadores