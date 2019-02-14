---
title: classe mip::AddContentFooterAction
description: Documenta a classe mip::addcontentfooteraction da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 28f9deb9460c88174f10c9a26c60f51407457b90
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254038"
---
# <a name="class-mipaddcontentfooteraction"></a>classe mip::AddContentFooterAction 
Uma classe de ação que especifica a adicionar um rodapé de conteúdo ao documento.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public const std::string& GetUIElementName()  |  Uma API utilizada para marcar o elemento de rodapé de conteúdo.
public const std::string& GetText() const  |  Obtenha o texto que serve para ir para o rodapé de conteúdo.
public const std::string& GetFontName() const  |  Obtenha o nome de tipo de letra utilizado para apresentar o rodapé de conteúdo.
public int GetFontSize() const  |  Obter o tamanho de tipo de letra utilizado para apresentar o rodapé de conteúdo.
public const std::string& GetFontColor() const  |  Obtenha a cor do tipo de letra utilizada para apresentar o rodapé de conteúdo.
public ContentMarkAlignment GetAlignment() const  |  Obtenha o alinhamento de rodapé.
public int GetMargin() const  |  Obtenha a margem de rodapé na parte inferior.
público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementname-function"></a>Função de GetUIElementName
Uma API utilizada para marcar o elemento de rodapé de conteúdo.

  
**Devolve**: O nome que deve ser utilizado para o elemento de interface do Usuário que contém o rodapé de conteúdo. O mesmo nome vai ser devolvido num [RemoveContentFooterAction](class_mip_removecontentfooteraction.md) no caso do rodapé de conteúdo tem de ser removido.
  
### <a name="gettext-function"></a>Função de GetText
Obtenha o texto que serve para ir para o rodapé de conteúdo.

  
**Devolve**: Texto do rodapé de conteúdo.
  
### <a name="getfontname-function"></a>Função de GetFontName
Obtenha o nome de tipo de letra utilizado para apresentar o rodapé de conteúdo.

  
**Devolve**: Nome do tipo de letra. Valor predefinido é Calibri se nada estiver definido pela política.
  
### <a name="getfontsize-function"></a>Função de GetFontSize
Obter o tamanho de tipo de letra utilizado para apresentar o rodapé de conteúdo.

  
**Devolve**: Tamanho da fonte como um número inteiro.
  
### <a name="getfontcolor-function"></a>Função de GetFontColor
Obtenha a cor do tipo de letra utilizada para apresentar o rodapé de conteúdo.

  
**Devolve**: Cor da fonte como uma cadeia de caracteres (por exemplo, "#000000").
  
### <a name="getalignment-function"></a>Função de GetAlignment
Obtenha o alinhamento de rodapé.

  
**Devolve**: O enumerador ContentMarkAlignment: ESQUERDA | DIREITA | CENTRO. 
  
**Consulte também**: [ContentMarkAlignment](mip-enums-and-structs.md#contentmarkalignment-enum)
  
### <a name="getmargin-function"></a>Função de GetMargin
Obtenha a margem de rodapé na parte inferior.

  
**Devolve**: As margens na parte inferior do documento (por exemplo, 10 mm).
  
### <a name="gettype-function"></a>Função de GetType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.
