---
title: classe mip etiqueta
description: Referência para a classe mip da etiqueta
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 2a80748430df83a16a4d5ee716344d17ce7deee4
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446282"
---
# <a name="class-miplabel"></a>classe mip::Label 
Abstração para um único rótulo do Microsoft Information Protection.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetId() const  |  Obter o ID da etiqueta.
 público const Std:: String & GetName() const  |  Obtenha o nome de etiqueta.
 público const Std:: String & GetDescription() const  |  Obter a descrição da etiqueta.
 público const Std:: String & const getcolor)  |  Obtenha a cor que da etiqueta deve ser exibida.
 público int GetSensitivity() const  |  Obtenha a sensibilidade da etiqueta.
 público const Std:: String & GetTooltip() const  |  Obter a descrição de descrição da etiqueta.
 bool pública IsActive() const  |  Obtém um valor de Booleano indicando se a etiqueta está ativa.
público std::weak_ptr<Label> GetParent() const  |  Obtenha a etiqueta principal.
Std:: vector const público < std::shared_ptr<Label>> & GetChildren() const  |  Obtenha os filhos etiquetas da etiqueta atual.
  
## <a name="members"></a>Membros
  
### <a name="getid"></a>GetId
Obter o ID da etiqueta.

  
**Devolve**: O ID da etiqueta.
  
### <a name="getname"></a>GetName
Obtenha o nome de etiqueta.

  
**Devolve**: O nome de rótulo.
  
### <a name="getdescription"></a>GetDescription
Obter a descrição da etiqueta.

  
**Devolve**: A descrição da etiqueta.
  
### <a name="getcolor"></a>GetColor
Obtenha a cor que da etiqueta deve ser exibida.

  
**Devolve**: valor de cor o formato de cadeia de caracteres. Em que cada um dos BB RR, GG, é um hexadecimal 0-f "#RRGGBB".
  
### <a name="getsensitivity"></a>GetSensitivity
Obtenha a sensibilidade da etiqueta.

  
**Devolve**: um valor numérico. Valor mais alto define mais alta sensibilidade.
  
### <a name="gettooltip"></a>GetTooltip
Obter a descrição de descrição da etiqueta.

  
**Devolve**: uma cadeia de descrição.
  
### <a name="isactive"></a>IsActive
Obtém um valor de Booleano indicando se a etiqueta está ativa.
Etiquetas de Active Directory só podem ser aplicadas. Etiquetas Inativas não não possível aplicar e são utilizadas para fins de exibição apenas. 

  
**Devolve**: VERDADEIRO se a etiqueta é o Active Directory, caso contrário FALSO.
  
### <a name="label"></a>Etiqueta
Obtenha a etiqueta principal.

  
**Devolve**: um ponteiro fraco para o elemento principal da etiqueta se existe, caso contrário, um ponteiro de vazio.
  
### <a name="label"></a>Etiqueta
Obtenha os filhos etiquetas da etiqueta atual.

  
**Devolve**: um vetor de ponteiros partilhados em etiquetas.