# <a name="class-mipaddcontentheaderaction"></a>classe mip::AddContentHeaderAction 
Uma classe de ação que especifica o cabeçalho de conteúdo de adição.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública std::string const & GetUIElementName | Uma API utilizada para marcar o elemento de cabeçalho de conteúdo.
pública std::string const & GetText | Obter o texto que tem o objetivo para ir para o cabeçalho de conteúdo.
pública std::string const & GetFontName | Obter o nome de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
int pública GetFontSize | Obter o tamanho de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
pública std::string const & GetFontColor | Obter a cor de tipo de letra utilizada para apresentar o cabeçalho de conteúdo.
pública ContentMarkAlignment GetAlignment | Obter o alinhamento do cabeçalho.
int pública GetMargin | Obter a margem de cabeçalho na parte inferior.
pública ActionType GetType
## <a name="members"></a>Membros
### <a name="getuielementname"></a>GetUIElementName
Uma API utilizada para marcar o elemento de cabeçalho de conteúdo.
#### <a name="returns"></a>Devolve
o nome que deve ser utilizado para o elemento de IU que contém o cabeçalho de conteúdo. O mesmo nome será devolvido na [RemoveContentHeaderAction](#classmip_1_1_remove_content_header_action) no caso do cabeçalho de conteúdo tem de ser removido.
### <a name="gettext"></a>GetText
Obter o texto que tem o objetivo para ir para o cabeçalho de conteúdo.
#### <a name="returns"></a>Devolve
texto do cabeçalho de conteúdo.
### <a name="getfontname"></a>GetFontName
Obter o nome de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
#### <a name="returns"></a>Devolve
Nome de tipo de letra, valor predefinido se não for definido pela política Calibri.
### <a name="getfontsize"></a>GetFontSize
Obter o tamanho de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
#### <a name="returns"></a>Devolve
tamanho do tipo de letra como um número inteiro.
### <a name="getfontcolor"></a>GetFontColor
Obter a cor de tipo de letra utilizada para apresentar o cabeçalho de conteúdo.
#### <a name="returns"></a>Devolve
cor do tipo de letra como uma cadeia (e.g."#000000").
### <a name="getalignment"></a>GetAlignment
Obter o alinhamento do cabeçalho.
#### <a name="returns"></a>Devolve
O enumerador ContentMarkAlignment, à esquerda | DIREITO | SYSTEM CENTER. 
**Consulte também**: ContentMarkAlignment
### <a name="getmargin"></a>GetMargin
Obter a margem de cabeçalho na parte inferior.
#### <a name="returns"></a>Devolve
um número inteiro represeting as margens do fim do documento (por exemplo, 10 mm).
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](#classmip_1_1_action).
#### <a name="returns"></a>Devolve
ActionType o tipo de ação derivada esta classe base pode ser convertido.