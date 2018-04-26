# <a name="class-mipcustomaction"></a>classe mip::CustomAction 
[CustomAction](#classmip_1_1_custom_action) é uma classe de ação genérica captura todas as propriedades secundárias da ação como uma matriz de propriedades. O chamador é da responsabilidade compreender o significado da ação.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
std::vector const pública < std::pair < std::string, std::string >> & GetProperties | Obter a lista de par de valor de chave de propriedades.
pública ActionType GetType
## <a name="members"></a>Membros
### <a name="getproperties"></a>GetProperties
Obter a lista de par de valor de chave de propriedades.
#### <a name="returns"></a>Devolve
uma lista de par de valor de chave.
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](#classmip_1_1_action).
#### <a name="returns"></a>Devolve
ActionType o tipo de ação derivada esta classe base pode ser convertido.