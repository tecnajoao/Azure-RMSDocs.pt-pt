---
title: classe mip::UserRights
description: Documenta a classe mip::userrights da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 3e3abd2045b0e66ee8c2b307d555bf860e489625
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650617"
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