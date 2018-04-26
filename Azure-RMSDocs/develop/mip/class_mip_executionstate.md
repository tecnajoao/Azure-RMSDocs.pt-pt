# <a name="class-mipexecutionstate"></a>classe mip::ExecutionState 
Interface para todos os Estado necessário para o motor de execução.
Os clientes só devem chamar os métodos para obter o estado de que é necessária. Por conseguinte, para uma eficiência, os clientes podem querer implementar esta interface de forma a que o estado correspondente é calculado dinamicamente em vez de informática antecipadamente.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
std::string pública GetNewLabelId | Obtém o id da etiqueta de sensibilidade que deve ser aplicado no documento.
bool pública IsDowngradeJustified | Implementação deverá passar se ou não foi indicada justificação mudar uma etiqueta existente.
pública AssignmentMethod GetNewLabelAssignmentMethod | Obter o método de atribuição a nova etiqueta.
std::vector pública < std::pair < std::string, std::string >> GetContentMetadata | Obter os itens de dados de metadados do conteúdo.
std::string pública GetTemplateId | Obtém o id de modelo de proteção de serviço de gestão de direitos.
pública ContentFormat GetContentFormat | Obtém o formato de conteúdo.
pública ActionType GetSupportedActions const
## <a name="members"></a>Membros
### <a name="getnewlabelid"></a>GetNewLabelId
Obtém o id da etiqueta de sensibilidade que deve ser aplicado no documento.
#### <a name="returns"></a>Devolve
id da etiqueta de sensibilidade a aplicar aos conteúdos se senão existe vazio para remover etiqueta.
### <a name="isdowngradejustified"></a>IsDowngradeJustified
Implementação deverá passar se ou não foi indicada justificação mudar uma etiqueta existente.
#### <a name="returns"></a>Devolve
VERDADEIRO se a mudança para versão anterior já for false Se ainda não foram seria-justificado, seria justificado. 
**Consulte também**: [mip::JustifyAction](#classmip_1_1_justify_action)
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
Obter o método de atribuição a nova etiqueta.
#### <a name="returns"></a>Devolve
o método de atribuição STANDARD, PRIVILEGIADO, AUTO. 
**Consulte também**: mip::AssignmentMethod
### <a name="getcontentmetadata"></a>GetContentMetadata
Obter os itens de dados de metadados do conteúdo.
#### <a name="returns"></a>Devolve
um vetor de pares de valor de chave que representa os dados de metadados aplicados ao conteúdo. Cada item meta-data é um par de nome e valor.
### <a name="gettemplateid"></a>GetTemplateId
Obtém o id de modelo de proteção de serviço de gestão de direitos.
#### <a name="returns"></a>Devolve
o rights management service id de modelo de proteção se existe senão num formato de guid sem chavetas, retorno uma cadeia vazia.
### <a name="getcontentformat"></a>GetContentFormat
Obtém o formato de conteúdo.
#### <a name="returns"></a>Devolve
PREDEFINIÇÃO, o E-Mail **Consulte também**: mip::ContentFormat
### <a name="actiontype"></a>ActionType
Devolva uma lista de ações que a aplicação o suportar. Todos os tipos de ações estão listados na [mip/upe/action.h](#action_8h).