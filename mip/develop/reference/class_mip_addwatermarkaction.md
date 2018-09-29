---
title: classe mip AddWatermarkAction
description: Referência para a classe mip AddWatermarkAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f49bd7aa16ae12aef240d05fff6acf507ddc341d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446095"
---
# <a name="class-mipaddwatermarkaction"></a>classe mip::AddWatermarkAction 
Uma classe de ação que especifica o limite de tamanho de adição.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetUIElementName()  |  Uma API utilizada para marcar o elemento de marca d'água.
 público GetLayout() de WatermarkLayout const  |  Uma API utilizada para obter o esquema de marca de água.
 público const Std:: String & GetText() const  |  Obtenha o texto que serve para ir para a marca d'água.
 público const Std:: String & GetFontName() const  |  Obtenha o nome de tipo de letra utilizado para apresentar a marca d'água.
 público int GetFontSize() const  |  Obter o tamanho da fonte usado para exibir a marca d'água.
 público const Std:: String & GetFontColor() const  |  Obtenha a cor da fonte usada para exibir a marca d'água.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementname"></a>GetUIElementName
Uma API utilizada para marcar o elemento de marca d'água.

  
**Devolve**: O nome que deve ser utilizado para o elemento de interface do Usuário que contém a marca d'água. No caso do limite de tamanho tem de ser removido em RemoveWatermarkingAction retornará o mesmo nome.
  
### <a name="getlayout"></a>GetLayout
Uma API utilizada para obter o esquema de marca de água.

  
**Devolve**: WatermarkLayout o layout de marca d'água na forma de th de uma enum HORIZONTAL | DIAGONAL. ,
  
### <a name="gettext"></a>GetText
Obtenha o texto que serve para ir para a marca d'água.

  
**Devolve**: texto do cabeçalho de conteúdo.
  
### <a name="getfontname"></a>GetFontName
Obtenha o nome de tipo de letra utilizado para apresentar a marca d'água.

  
**Devolve**: nome da fonte. Valor predefinido é Calibri se nada estiver definido pela política.
  
### <a name="getfontsize"></a>GetFontSize
Obter o tamanho da fonte usado para exibir a marca d'água.

  
**Devolve**: tamanho da fonte como um número inteiro.
  
### <a name="getfontcolor"></a>GetFontColor
Obtenha a cor da fonte usada para exibir a marca d'água.

  
**Devolve**: cor da fonte como uma cadeia de caracteres (por exemplo, "#000000").
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.