---
title: classe mip::CustomAction
description: Documenta a classe mip::customaction da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 12ecba0f442ee3e51a5cb58e77bee546ac262deb
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333573"
---
# <a name="class-mipcustomaction"></a>classe mip::CustomAction 
[CustomAction](class_mip_customaction.md) é uma classe de ação genérica que captura todas as propriedades secundárias da ação como uma matriz de propriedades. O chamador é da responsabilidade compreender o significado da ação.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetName() const  |  Obtenha o nome da ação.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetProperties() const  |  Obter a lista de par de valor da chave de propriedades.
público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getname-function"></a>Função de GetName
Obtenha o nome da ação.

  
**Devolve**: Um nome de ação, se um existe, caso contrário, uma cadeia vazia.
  
### <a name="getproperties-function"></a>Função de GetProperties
Obter a lista de par de valor da chave de propriedades.

  
**Devolve**: Uma lista de par chave-valor.
  
### <a name="gettype-function"></a>Função de GetType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.
