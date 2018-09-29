---
title: classe mip CustomAction
description: Referência para a classe mip CustomAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a94a41c0e7f7848201e2af44187cce2540579b27
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47444730"
---
# <a name="class-mipcustomaction"></a>classe mip::CustomAction 
[CustomAction](class_mip_customaction.md) é uma classe de ação genérica que captura todas as propriedades secundárias da ação como uma matriz de propriedades. O chamador é da responsabilidade compreender o significado da ação.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetName() const  |  Obtenha o nome da ação.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetProperties() const  |  Obter a lista de par de valor da chave de propriedades.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getname"></a>GetName
Obtenha o nome da ação.

  
**Devolve**: um nome de ação, se houver outro uma cadeia vazia.
  
### <a name="getproperties"></a>GetProperties
Obter a lista de par de valor da chave de propriedades.

  
**Devolve**: uma lista de par chave-valor.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.