---
title: class mip::AddContentHeaderAction
description: Documenta a classe mip::addcontentheaderaction da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 8cd04bc610944bbbdf00873267161b06a9c09038
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650940"
---
# <a name="class-mipaddcontentheaderaction"></a>class mip::AddContentHeaderAction 
Uma classe de ação que especifica o cabeçalho de conteúdo a adicionar.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetUIElementName()  |  Uma API utilizada para marcar o elemento de cabeçalho de conteúdo.
public const std::string& GetText() const  |  Obtenha o texto que serve para ir para o cabeçalho de conteúdo.
public const std::string& GetFontName() const  |  Obtenha o nome de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
public int GetFontSize() const  |  Obter o tamanho de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
public const std::string& GetFontColor() const  |  Obtenha a cor do tipo de letra utilizada para apresentar o cabeçalho de conteúdo.
public ContentMarkAlignment GetAlignment() const  |  Obtenha o alinhamento do cabeçalho.
public int GetMargin() const  |  Obter a margem do cabeçalho da parte inferior.
público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementname-function"></a>Função de GetUIElementName
Uma API utilizada para marcar o elemento de cabeçalho de conteúdo.

  
**Devolve**: O nome que deve ser utilizado para o elemento de interface do Usuário que contém o cabeçalho de conteúdo. O mesmo nome vai ser devolvido num [RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) caso o cabeçalho conteúdo tem de ser removido.
  
### <a name="gettext-function"></a>Função de GetText
Obtenha o texto que serve para ir para o cabeçalho de conteúdo.

  
**Devolve**: Texto do cabeçalho de conteúdo.
  
### <a name="getfontname-function"></a>Função de GetFontName
Obtenha o nome de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.

  
**Devolve**: Nome do tipo de letra. Valor predefinido é Calibri se nada estiver definido pela política.
  
### <a name="getfontsize-function"></a>Função de GetFontSize
Obter o tamanho de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.

  
**Devolve**: Tamanho da fonte como um número inteiro.
  
### <a name="getfontcolor-function"></a>Função de GetFontColor
Obtenha a cor do tipo de letra utilizada para apresentar o cabeçalho de conteúdo.

  
**Devolve**: Cor da fonte como uma cadeia de caracteres (por exemplo, #000000 ").
  
### <a name="getalignment-function"></a>Função de GetAlignment
Obtenha o alinhamento do cabeçalho.

  
**Devolve**: O enumerador ContentMarkAlignment: ESQUERDA | DIREITA | CENTRO. 
  
**Consulte também**: [ContentMarkAlignment](mip-enums-and-structs.md#contentmarkalignment-enum)
  
### <a name="getmargin-function"></a>Função de GetMargin
Obter a margem do cabeçalho da parte inferior.

  
**Devolve**: As margens na parte inferior do documento (por exemplo, 10 mm).
  
### <a name="gettype-function"></a>Função de GetType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.