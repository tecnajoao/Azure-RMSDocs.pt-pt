# <a name="class-mipcustomaction"></a>classe mip::CustomAction 
[CustomAction](class_mip_customaction.md) é uma classe de ação genérica que captura todas as propriedades secundárias da ação como uma matriz de propriedades. O chamador é da responsabilidade compreender o significado da ação.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetProperties() const  |  Obter a lista de par de valor da chave de propriedades.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getproperties"></a>GetProperties
Obter a lista de par de valor da chave de propriedades.

  
**Devolve**: uma lista de par chave-valor.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.