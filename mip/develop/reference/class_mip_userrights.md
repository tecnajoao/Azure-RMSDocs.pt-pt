---
title: classe mip UserRights
description: Referência para a classe mip UserRights
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: c1ef7aaba00bf595d80f07f318aa5808f3a56409
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445126"
---
# <a name="class-mipuserrights"></a>classe mip::UserRights 
Um grupo de utilizadores e os direitos associados aos mesmos.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
UserRights pública (const Std:: vector < Std:: String > e os utilizadores, const Std:: vector < Std:: String > e direitos)  |  [UserRights](class_mip_userrights.md) construtor.
público const Std:: vector < Std:: String > & Users() const  |  Obtém os utilizadores associados a um conjunto de direitos.
público const Std:: vector < Std:: String > & Rights() const  |  Obtém os direitos associados um grupo de utilizadores.
  
## <a name="members"></a>Membros
  
### <a name="userrights"></a>UserRights
[UserRights](class_mip_userrights.md) construtor.

Parâmetros:  
* **os utilizadores**: grupo de usuários que compartilham os mesmos direitos 


* **direitos**: direitos partilharam por grupo de utilizadores


  
### <a name="users"></a>Users
Obtém os utilizadores associados a um conjunto de direitos.

  
**Devolve**: os utilizadores associados a um conjunto de direitos
  
### <a name="rights"></a>Direitos
Obtém os direitos associados um grupo de utilizadores.

  
**Devolve**: direitos associados a um grupo de utilizadores