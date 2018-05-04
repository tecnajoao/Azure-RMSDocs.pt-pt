# <a name="class-mipremovecontentheaderaction"></a>classe mip::RemoveContentHeaderAction 
Uma classe de ação que especifica a remover o cabeçalho de conteúdo do documento.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
std::vector const pública < std::string > & GetUIElementNames()  |  Obtém uma lista de nomes que devem ser utilizadas para localizar os elementos de IU que devem ser removidos.
pública ActionType GetType() const  |  Obter o tipo de [ação](#classmip_1_1_action).
  
## <a name="members"></a>Membros
  
### <a name="getuielementnames"></a>GetUIElementNames
Obtém uma lista de nomes que devem ser utilizadas para localizar os elementos de IU que devem ser removidos.
  
#### <a name="returns"></a>Devolve
uma lista de nomes do elemento de IU.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](#classmip_1_1_action).
  
#### <a name="returns"></a>Devolve
ActionType o tipo de ação derivada esta classe base pode ser convertido.