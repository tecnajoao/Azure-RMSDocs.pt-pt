# <a name="class-mipmetadataaction"></a>classe mip::MetadataAction 
Um [ação](#classmip_1_1_action) esperava que especifica as informações de dados de metadados devem ser adicionadas ao conteúdo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
std::vector const pública < std::string > & GetMetadataToRemove() const  |  Obter a lista de nomes de meta-data tem de ser removido do conteúdo.
std::vector const pública < std::pair < std::string, std::string >> & GetMetadataToAdd() const  |  Obter a lista de meta-data como pares de valor de chave. Os dados de metadados tem de ser adicionado aos dados de metadados de conteúdo.
pública ActionType GetType() const  |  Obter o tipo de [ação](#classmip_1_1_action).
  
## <a name="members"></a>Membros
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Obter a lista de nomes de meta-data tem de ser removido do conteúdo.
  
#### <a name="returns"></a>Devolve
um vetor de cadeias para remover. Se remover dados de metadados deve ser feito antes de adicionar dados de metadados.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Obter a lista de meta-data como pares de valor de chave. Os dados de metadados tem de ser adicionado aos dados de metadados de conteúdo.
  
#### <a name="returns"></a>Devolve
Const std::vector < std::pair < std::string, std::string >> & Remover dados de metadados devem ser feitas antes de adicionar dados de metadados.
  
### <a name="actiontype"></a>ActionType
Obter o tipo de [ação](#classmip_1_1_action).
  
#### <a name="returns"></a>Devolve
ActionType o tipo de ação derivada esta classe base pode ser convertido.