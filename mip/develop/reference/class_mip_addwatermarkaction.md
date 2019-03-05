---
title: classe mip::AddWatermarkAction
description: Documenta a classe mip::addwatermarkaction da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 8121763106c9f46022264a7eea3bc16e363e523c
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330479"
---
# <a name="class-mipaddwatermarkaction"></a>classe mip::AddWatermarkAction 
Uma classe de ação que especifica o limite de tamanho de adição.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetUIElementName()  |  Uma API utilizada para marcar o elemento de marca d'água.
public WatermarkLayout GetLayout() const  |  Uma API utilizada para obter o esquema de marca de água.
public const std::string& GetText() const  |  Obtenha o texto que serve para ir para a marca d'água.
public const std::string& GetFontName() const  |  Obtenha o nome de tipo de letra utilizado para apresentar a marca d'água.
public int GetFontSize() const  |  Obter o tamanho da fonte usado para exibir a marca d'água.
public const std::string& GetFontColor() const  |  Obtenha a cor da fonte usada para exibir a marca d'água.
público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementname-function"></a>Função de GetUIElementName
Uma API utilizada para marcar o elemento de marca d'água.

  
**Devolve**: O nome que deve ser utilizado para o elemento de interface do Usuário que contém a marca d'água. No caso do limite de tamanho tem de ser removido em RemoveWatermarkingAction retornará o mesmo nome.
  
### <a name="getlayout-function"></a>Função de GetLayout
Uma API utilizada para obter o esquema de marca de água.

  
**Devolve**: WatermarkLayout o layout de marca d'água na forma de th de uma enum HORIZONTAL | DIAGONAL. , 
  
### <a name="gettext-function"></a>Função de GetText
Obtenha o texto que serve para ir para a marca d'água.

  
**Devolve**: Texto do cabeçalho de conteúdo.
  
### <a name="getfontname-function"></a>Função de GetFontName
Obtenha o nome de tipo de letra utilizado para apresentar a marca d'água.

  
**Devolve**: Nome do tipo de letra. Valor predefinido é Calibri se nada estiver definido pela política.
  
### <a name="getfontsize-function"></a>Função de GetFontSize
Obter o tamanho da fonte usado para exibir a marca d'água.

  
**Devolve**: Tamanho da fonte como um número inteiro.
  
### <a name="getfontcolor-function"></a>Função de GetFontColor
Obtenha a cor da fonte usada para exibir a marca d'água.

  
**Devolve**: Cor da fonte como uma cadeia de caracteres (por exemplo, "#000000").
  
### <a name="gettype-function"></a>Função de GetType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.
