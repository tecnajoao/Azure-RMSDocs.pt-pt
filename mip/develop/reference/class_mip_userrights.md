---
title: classe mip::UserRights
description: Documenta a classe mip::userrights da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: aadf12606f74d508ba3ebdc1ce0770febd49e142
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56251309"
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
