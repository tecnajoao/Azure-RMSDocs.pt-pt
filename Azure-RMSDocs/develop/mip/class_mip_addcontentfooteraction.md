# <a name="class-mipaddcontentfooteraction"></a>classe mip::AddContentFooterAction 
Uma classe de ação que especifica a adição de um rodapé de conteúdo para o documento.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 pública std::string const & GetUIElementName()  |  Uma API utilizada para marcar o elemento de rodapé conteúdo.
 pública std::string const & GetText() const  |  Obter o texto que tem o objetivo para ir para o rodapé de conteúdo.
 pública std::string const & GetFontName() const  |  Obter o nome de tipo de letra utilizado para apresentar o conteúdo rodapé.
 int pública GetFontSize() const  |  Obter o tamanho de tipo de letra utilizado para apresentar o conteúdo rodapé.
 pública std::string const & GetFontColor() const  |  Obter a cor de tipo de letra utilizada para apresentar o conteúdo rodapé.
 pública ContentMarkAlignment GetAlignment() const  |  Obter o alinhamento do rodapé.
 int pública GetMargin() const  |  Obter a margem de rodapé na parte inferior.
 pública ActionType GetType() const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementname"></a>GetUIElementName
Uma API utilizada para marcar o elemento de rodapé conteúdo.

  
**Devolve**: O nome que deve ser utilizado para o elemento de IU que detém o conteúdo rodapé. O mesmo nome será devolvido na [RemoveContentFooterAction](class_mip_removecontentfooteraction.md) no caso do rodapé de conteúdo tem de ser removido.
  
### <a name="gettext"></a>GetText
Obter o texto que tem o objetivo para ir para o rodapé de conteúdo.

  
**Devolve**: texto do rodapé de conteúdo.
  
### <a name="getfontname"></a>GetFontName
Obter o nome de tipo de letra utilizado para apresentar o conteúdo rodapé.

  
**Devolve**: nome de tipo de letra, valor predefinido se não for definido pela política Calibri.
  
### <a name="getfontsize"></a>GetFontSize
Obter o tamanho de tipo de letra utilizado para apresentar o conteúdo rodapé.

  
**Devolve**: tamanho de tipo de letra, como um número inteiro.
  
### <a name="getfontcolor"></a>GetFontColor
Obter a cor de tipo de letra utilizada para apresentar o conteúdo rodapé.

  
**Devolve**: cores de tipo de letra, como uma cadeia (e.g."#000000").
  
### <a name="getalignment"></a>GetAlignment
Obter o alinhamento do rodapé.

  
**Devolve**: ContentMarkAlignment o enumerador, à esquerda | DIREITO | SYSTEM CENTER. 
**Consulte também**: ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
Obter a margem de rodapé na parte inferior.

  
**Devolve**: um número inteiro represeting as margens do fim do documento (por exemplo, 10 mm).
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada esta classe base pode ser convertido.