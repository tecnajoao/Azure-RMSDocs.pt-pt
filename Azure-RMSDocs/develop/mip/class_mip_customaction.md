# <a name="class-mipcustomaction"></a>classe mip::CustomAction 
[CustomAction](class_mip_customaction.md) é uma classe de ação genérica captura todas as propriedades secundárias da ação como uma matriz de propriedades. O chamador é da responsabilidade compreender o significado da ação.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
std::vector const pública < std::pair < std::string, std::string >> & GetProperties() const  |  Obter a lista de par de valor de chave de propriedades.
 pública ActionType GetType() const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getproperties"></a>GetProperties
Obter a lista de par de valor de chave de propriedades.

  
**Devolve**: uma lista de par de valor de chave.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada esta classe base pode ser convertido.