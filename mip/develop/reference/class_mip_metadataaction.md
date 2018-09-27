# <a name="class-mipmetadataaction"></a>classe mip::MetadataAction 
Uma [ação](class_mip_action.md) que adiciona informações de metadados para o conteúdo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público const Std:: vector < Std:: String > & GetMetadataToRemove() const  |  Obter a lista de nomes dos metadados que têm de ser removido do conteúdo.
público const Std:: vector < std::pair < Std:: String, Std:: String >> & GetMetadataToAdd() const  |  Obter a lista de metadados como pares chave-valor. Os metadados precisam ser adicionado aos metadados de conteúdo.
 público GetType() de ActionType const  |  Obter o tipo de [ação](class_mip_action.md).
  
## <a name="members"></a>Membros
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Obter a lista de nomes dos metadados que têm de ser removido do conteúdo.

  
**Devolve**: um vetor de cadeias de caracteres para remover. remover metadados deve ser feito antes de adicionar metadados.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Obter a lista de metadados como pares chave-valor. Os metadados precisam ser adicionado aos metadados de conteúdo.

  
**Devolve**: Const Std:: vector < std::pair < Std:: String, Std:: String >> & remover metadados devem ser feitas antes de adicionar metadados.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](class_mip_action.md).

  
**Devolve**: ActionType o tipo de ação derivada dessa classe base pode ser convertida no.