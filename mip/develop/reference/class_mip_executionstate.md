# <a name="class-mipexecutionstate"></a>classe mip::ExecutionState 
Interface para todos os Estados necessários para executar o motor.
Os clientes só devem chamar os métodos para obter o estado em que é necessária. Por conseguinte, para uma eficiência, clientes talvez queira implementar essa interface, de modo a que o estado correspondente é calculado dinamicamente em vez de computar com antecedência.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público Std:: String GetNewLabelId() const  |  Obtém o id de etiqueta de sensibilidade que deve ser aplicado no documento.
 público GetNewLabelActionSource() de ActionSource const  |  Obtém a origem para uma nova ação de etiqueta.
 público Std:: String GetContentIdentifier() const  |  Obtém o identificador de conteúdo que deve ser aplicado no documento com base no estado atual. exemplo de um ficheiro: "C:\mip-sdk-for-cpp\files\audit.docx" [caminho: nome do ficheiro] de exemplo para uma mensagem de e-mail: "RE: auditoria design:user1@contoso.com" [assunto: remetente].
 público GetContentState() de ContentState const  |  Obtém o ContentState dos dados conforme definido pela aplicação.
std::pair público < bool, Std:: String > IsDowngradeJustified() const  |  Implementação deve passar se ou não foi indicada justificação para alterar uma etiqueta existente.
 público GetNewLabelAssignmentMethod() de AssignmentMethod const  |  Obtenha o método de atribuição a nova etiqueta.
público Std:: vector < std::pair < Std:: String, Std:: String >> GetNewLabelExtendedProperties() const  |  Devolva propriedades expandidas da nova etiqueta.
público Std:: vector < std::pair < Std:: String, Std:: String >> GetContentMetadata (const Std:: vector < Std:: String > e nomes de contas, const Std:: vector < Std:: String > e namePrefixes) const  |  Obter os itens de metadados do conteúdo.
público std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor() const  |  Obter o descritor de proteção.
 público GetContentFormat() de ContentFormat const  |  Obtém o formato de conteúdo.
 público GetSupportedActions() de ActionType const  |  Obtém um enum mascarado, que representa todos os tipos de ação suportados.
público std::map virtual < Std:: String, std::shared_ptr<ClassificationResult>> GetClassificationResults (Std:: vector const < Std:: String > &) const  |  Devolva um mapa dos resultados de classificação.
  
## <a name="members"></a>Membros
  
### <a name="getnewlabelid"></a>GetNewLabelId
Obtém o id de etiqueta de sensibilidade que deve ser aplicado no documento.

  
**Devolve**: id de etiqueta de sensibilidade a ser aplicado para o conteúdo se existe outro vazia de forma remover etiqueta.
  
### <a name="getnewlabelactionsource"></a>GetNewLabelActionSource
Obtém a origem para uma nova ação de etiqueta.

  
**Devolve**: origem de ação.
  
### <a name="getcontentidentifier"></a>GetContentIdentifier
Obtém o identificador de conteúdo que deve ser aplicado no documento com base no estado atual. exemplo de um ficheiro: "C:\mip-sdk-for-cpp\files\audit.docx" [caminho: nome do ficheiro] de exemplo para uma mensagem de e-mail: "RE: auditoria design:user1@contoso.com" [assunto: remetente].

  
**Devolve**: identificador de conteúdo a ser aplicado ao conteúdo.
  
### <a name="getcontentstate"></a>GetContentState
Obtém o ContentState dos dados conforme definido pela aplicação.

  
**Devolve**: estado dos dados que está a ser alterados
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
Implementação deve passar se ou não foi indicada justificação para alterar uma etiqueta existente.

  
**Devolve**: VERDADEIRO se a mudança para versão anterior já está a ser justificadas, false Se ainda não tenha sido justificado. 

  
**Devolve**: mensagem de justificação associada a mudança para versão anterior 
  
**Consulte também**: [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
Obtenha o método de atribuição a nova etiqueta.

  
**Devolve**: O método de atribuição STANDARD, PRIVILEGIADO, AUTOMATICAMENTE. 
  
**Consulte também**: mip::AssignmentMethod
  
### <a name="getnewlabelextendedproperties"></a>GetNewLabelExtendedProperties
Devolva propriedades expandidas da nova etiqueta.

  
**Devolve**: um vetor de pares chave-valor que representa as propriedades expandidas aplicadas ao conteúdo.
  
### <a name="getcontentmetadata"></a>GetContentMetadata
Obter os itens de metadados do conteúdo.

  
**Devolve**: um vetor de pares chave-valor que representa os dados de meta aplicados ao conteúdo. Cada item de metadados é um par de nome e valor.
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Obter o descritor de proteção.

  
**Devolve**: O descritor de proteção
  
### <a name="getcontentformat"></a>GetContentFormat
Obtém o formato de conteúdo.

  
**Devolve**: predefinido, o E-Mail 
  
**Consulte também**: mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
Obtém um enum mascarado, que representa todos os tipos de ação suportados.

  
**Devolve**: um enum mascarado, que representa todos os tipos de ação suportados.
ActionType::Justify sempre têm de ser suportadas. Quando uma alteração de política e a etiqueta requer uma justificação, uma ação de justificação sempre será retornada.
  
### <a name="classificationresult"></a>ClassificationResult
Devolva um mapa dos resultados de classificação.

Parâmetros:  
* **classificationId**: uma lista de IDs de classificação 



  
**Devolve**: uma lista de resultados de classificação.