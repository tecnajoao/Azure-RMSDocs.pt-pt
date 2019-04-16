---
title: classe mip::UserRoles
description: Documenta a classe mip::userroles da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 7e9e750f5b327dbad5e9b46fa1eca2a3291abdd3
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573110"
---
# <a name="class-mipuserroles"></a>classe mip::UserRoles 
Um grupo de utilizadores e as funções associadas a eles.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public UserRoles(const std::vector\<std::string\>& users, const std::vector\<std::string\>& roles)  |  [Funções de utilizador](class_mip_userroles.md) construtor.
public const std::vector\<std::string\>& Users() const  |  Obtém os utilizadores associados a um conjunto de funções.
público const Std:: vector\<Std:: String\>& Roles() const  |  Obtém as funções associadas um grupo de utilizadores.
  
## <a name="members"></a>Membros
  
### <a name="userroles-function"></a>Função de funções de utilizador
[Funções de utilizador](class_mip_userroles.md) construtor.

Parâmetros:  
* **Os utilizadores**: Grupo de usuários que compartilham as mesmas funções 


* **funções**: Funções compartilhadas por grupo de utilizadores


  
### <a name="users-function"></a>Função de utilizadores
Obtém os utilizadores associados a um conjunto de funções.

  
**Devolve**: Utilizadores associados a um conjunto de funções
  
### <a name="roles-function"></a>Função de funções
Obtém as funções associadas um grupo de utilizadores.

  
**Devolve**: Funções associadas um grupo de utilizadores