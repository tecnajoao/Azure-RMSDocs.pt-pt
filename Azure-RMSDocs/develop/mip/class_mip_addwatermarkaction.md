# <a name="class-mipaddwatermarkaction"></a>classe mip::AddWatermarkAction 
Uma classe de ação que especifica a adição de marca de água.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 pública std::string const & GetUIElementName()  |  Uma API utilizada para marcar o elemento de marca de água.
 pública WatermarkLayout GetLayout() const  |  Uma API utilizada para obter o esquema de marca de níveis máximos.
 pública std::string const & GetText() const  |  Obter o texto que tem o objetivo para ir para o cabeçalho de conteúdo.
 pública std::string const & GetFontName() const  |  Obter o nome de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
 int pública GetFontSize() const  |  Obter o tamanho de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
 pública std::string const & GetFontColor() const  |  Obter a cor de tipo de letra utilizada para apresentar o cabeçalho de conteúdo.
 pública ActionType GetType() const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementname"></a>GetUIElementName
Uma API utilizada para marcar o elemento de marca de água.

  
**Devolve**: O nome que deve ser utilizado para o elemento de IU que contém a marca de água. O mesmo nome será devolvido na RemoveWatermarkingAction no caso de marca de água tem de ser removido.
  
### <a name="getlayout"></a>GetLayout
Uma API utilizada para obter o esquema de marca de níveis máximos.

  
**Devolve**: WatermarkLayout o esquema watermarking no formato ésimo uma enumeração HORIZONTAL | DIAGONAL. ,
  
### <a name="gettext"></a>GetText
Obter o texto que tem o objetivo para ir para o cabeçalho de conteúdo.

  
**Devolve**: o texto do cabeçalho de conteúdo.
  
### <a name="getfontname"></a>GetFontName
Obter o nome de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.

  
**Devolve**: nome de tipo de letra, valor predefinido se não for definido pela política Calibri.
  
### <a name="getfontsize"></a>GetFontSize
Obter o tamanho de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.

  
**Devolve**: tamanho de tipo de letra, como um número inteiro.
  
### <a name="getfontcolor"></a>GetFontColor
Obter a cor de tipo de letra utilizada para apresentar o cabeçalho de conteúdo.

  
**Devolve**: cores de tipo de letra, como uma cadeia (e.g."#000000").
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada esta classe base pode ser convertido.