---
title: classe mip AddContentFooterAction
description: Referência para a classe mip AddContentFooterAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 73f641d965c3cf0236919557128af2ed07705672
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445840"
---
# <a name="class-mipaddcontentfooteraction"></a>classe mip::AddContentFooterAction 
Uma classe de ação que especifica a adicionar um rodapé de conteúdo ao documento.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetUIElementName()  |  Uma API utilizada para marcar o elemento de rodapé de conteúdo.
 público const Std:: String & GetText() const  |  Obtenha o texto que serve para ir para o rodapé de conteúdo.
 público const Std:: String & GetFontName() const  |  Obtenha o nome de tipo de letra utilizado para apresentar o rodapé de conteúdo.
 público int GetFontSize() const  |  Obter o tamanho de tipo de letra utilizado para apresentar o rodapé de conteúdo.
 público const Std:: String & GetFontColor() const  |  Obtenha a cor do tipo de letra utilizada para apresentar o rodapé de conteúdo.
 público GetAlignment() de ContentMarkAlignment const  |  Obtenha o alinhamento de rodapé.
 público int GetMargin() const  |  Obtenha a margem de rodapé na parte inferior.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementname"></a>GetUIElementName
Uma API utilizada para marcar o elemento de rodapé de conteúdo.

  
**Devolve**: O nome que deve ser utilizado para o elemento de interface do Usuário que contém o rodapé de conteúdo. O mesmo nome vai ser devolvido num [RemoveContentFooterAction](class_mip_removecontentfooteraction.md) no caso do rodapé de conteúdo tem de ser removido.
  
### <a name="gettext"></a>GetText
Obtenha o texto que serve para ir para o rodapé de conteúdo.

  
**Devolve**: texto do rodapé de conteúdo.
  
### <a name="getfontname"></a>GetFontName
Obtenha o nome de tipo de letra utilizado para apresentar o rodapé de conteúdo.

  
**Devolve**: nome da fonte. Valor predefinido é Calibri se nada estiver definido pela política.
  
### <a name="getfontsize"></a>GetFontSize
Obter o tamanho de tipo de letra utilizado para apresentar o rodapé de conteúdo.

  
**Devolve**: tamanho da fonte como um número inteiro.
  
### <a name="getfontcolor"></a>GetFontColor
Obtenha a cor do tipo de letra utilizada para apresentar o rodapé de conteúdo.

  
**Devolve**: cor da fonte como uma cadeia de caracteres (por exemplo, "#000000").
  
### <a name="getalignment"></a>GetAlignment
Obtenha o alinhamento de rodapé.

  
**Devolve**: ContentMarkAlignment o enumerador: esquerda | DIREITA | CENTRO. 
  
**Consulte também**: ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
Obtenha a margem de rodapé na parte inferior.

  
**Devolve**: as margens na parte inferior do documento (por exemplo, 10 mm).
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.