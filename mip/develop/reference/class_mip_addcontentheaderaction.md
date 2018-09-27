# <a name="class-mipaddcontentheaderaction"></a>classe mip::AddContentHeaderAction 
Uma classe de ação que especifica o cabeçalho de conteúdo a adicionar.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público const Std:: String & GetUIElementName()  |  Uma API utilizada para marcar o elemento de cabeçalho de conteúdo.
 público const Std:: String & GetText() const  |  Obtenha o texto que serve para ir para o cabeçalho de conteúdo.
 público const Std:: String & GetFontName() const  |  Obtenha o nome de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
 público int GetFontSize() const  |  Obter o tamanho de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.
 público const Std:: String & GetFontColor() const  |  Obtenha a cor do tipo de letra utilizada para apresentar o cabeçalho de conteúdo.
 público GetAlignment() de ContentMarkAlignment const  |  Obtenha o alinhamento do cabeçalho.
 público int GetMargin() const  |  Obter a margem do cabeçalho da parte inferior.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getuielementname"></a>GetUIElementName
Uma API utilizada para marcar o elemento de cabeçalho de conteúdo.

  
**Devolve**: O nome que deve ser utilizado para o elemento de interface do Usuário que contém o cabeçalho de conteúdo. O mesmo nome vai ser devolvido num [RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) caso o cabeçalho conteúdo tem de ser removido.
  
### <a name="gettext"></a>GetText
Obtenha o texto que serve para ir para o cabeçalho de conteúdo.

  
**Devolve**: texto do cabeçalho de conteúdo.
  
### <a name="getfontname"></a>GetFontName
Obtenha o nome de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.

  
**Devolve**: nome da fonte. Valor predefinido é Calibri se nada estiver definido pela política.
  
### <a name="getfontsize"></a>GetFontSize
Obter o tamanho de tipo de letra utilizado para apresentar o cabeçalho de conteúdo.

  
**Devolve**: tamanho da fonte como um número inteiro.
  
### <a name="getfontcolor"></a>GetFontColor
Obtenha a cor do tipo de letra utilizada para apresentar o cabeçalho de conteúdo.

  
**Devolve**: cor da fonte como uma cadeia de caracteres (e.g."#000000").
  
### <a name="getalignment"></a>GetAlignment
Obtenha o alinhamento do cabeçalho.

  
**Devolve**: ContentMarkAlignment o enumerador: esquerda | DIREITA | CENTRO. 
  
**Consulte também**: ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
Obter a margem do cabeçalho da parte inferior.

  
**Devolve**: um número inteiro que representa as margens na parte inferior do documento (por exemplo, 10 mm).
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.