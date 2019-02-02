---
title: classe mip::Label
description: Documenta a classe mip::label da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: aa2d5106f8da03b4cf6a9dbd99c440989dc7ff6d
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650668"
---
# <a name="class-miplabel"></a>classe mip::Label 
Abstração para um único rótulo do Microsoft Information Protection.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Obter o ID da etiqueta.
public const std::string& GetName() const  |  Obtenha o nome de etiqueta.
public const std::string& GetDescription() const  |  Obter a descrição da etiqueta.
public const std::string& GetColor() const  |  Obtenha a cor que da etiqueta deve ser exibida.
público int GetSensitivity() const  |  Obtenha a sensibilidade da etiqueta.
public const std::string& GetTooltip() const  |  Obter a descrição de descrição da etiqueta.
bool pública IsActive() const  |  Obtém um valor de Booleano indicando se a etiqueta está ativa.
público std::weak_ptr\<etiqueta\> GetParent() const  |  Obtenha a etiqueta principal.
público const Std:: vector\<std::shared_ptr\<etiqueta\>\>& GetChildren() const  |  Obtenha os filhos etiquetas da etiqueta atual.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetCustomSettings() const  |  Obter as definições personalizadas de uma etiqueta.
  
## <a name="members"></a>Membros
  
### <a name="getid-function"></a>Função de GetId
Obter o ID da etiqueta.

  
**Devolve**: O ID da etiqueta.
  
### <a name="getname-function"></a>Função de GetName
Obtenha o nome de etiqueta.

  
**Devolve**: O nome de etiqueta.
  
### <a name="getdescription-function"></a>Função de GetDescription
Obter a descrição da etiqueta.

  
**Devolve**: A descrição da etiqueta.
  
### <a name="getcolor-function"></a>Função de GetColor
Obtenha a cor que da etiqueta deve ser exibida.

  
**Devolve**: O formato de cadeia de valor de cor. Em que cada um dos BB RR, GG, é um hexadecimal 0-f "#RRGGBB".
  
### <a name="getsensitivity-function"></a>Função de GetSensitivity
Obtenha a sensibilidade da etiqueta.

  
**Devolve**: Um valor numérico. Valor mais alto define mais alta sensibilidade.
  
### <a name="gettooltip-function"></a>Função de GetTooltip
Obter a descrição de descrição da etiqueta.

  
**Devolve**: Uma cadeia de descrição.
  
### <a name="isactive-function"></a>Função de IsActive
Obtém um valor de Booleano indicando se a etiqueta está ativa.
Etiquetas de Active Directory só podem ser aplicadas. Etiquetas Inativas não não possível aplicar e são utilizadas para fins de exibição apenas. 

  
**Devolve**: VERDADEIRO se a etiqueta é o Active Directory, caso contrário FALSO.
  
### <a name="getparent-function"></a>Função de GetParent
Obtenha a etiqueta principal.

  
**Devolve**: Um ponteiro fraco para o elemento principal da etiqueta se existe, caso contrário, um ponteiro de vazio.
  
### <a name="getchildren-function"></a>Função de GetChildren
Obtenha os filhos etiquetas da etiqueta atual.

  
**Devolve**: Um vetor de ponteiros partilhados em etiquetas.
  
### <a name="getcustomsettings-function"></a>Função de GetCustomSettings
Obter as definições personalizadas de uma etiqueta.

  
**Devolve**: Um vetor de pares chave-valor que representa as definições personalizadas.