# <a name="class-mippolicyhandler"></a>classe mip::PolicyHandler 
Essa classe fornece uma interface para todas as funções do manipulador de política num arquivo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::shared_ptr<ContentLabel> GetSensitivityLabel (const ExecutionState & Estado)  |  Obter etiqueta de confidencialidade do conteúdo existente.
Std:: vector público < std::shared_ptr<Action>> ComputeActions (const ExecutionState & Estado)  |  Executa as regras no manipulador com base no estado fornecido e retorna a lista de ações a ser executado.
 NotifyCommitedActions void pública (const ExecutionState & Estado)  |  Chamado assim que as ações calculadas terem sido aplicadas e o consolidado de dados no disco.
  
## <a name="members"></a>Membros
  
### <a name="contentlabel"></a>ContentLabel
Obter etiqueta de confidencialidade do conteúdo existente.
As informações necessárias para obter a etiqueta serão obtidas utilizando o estado de execução fornecida. 

Parâmetros:  
* **estado**: 



  
**Devolve**: um objeto de etiqueta de conteúdo que contém a sensibilidade de informações adicionais, bem como da etiqueta. Devolve vazio se não existir. 
  
**Consulte também**: [mip::ContentLabel](class_mip_contentlabel.md).
  
### <a name="action"></a>Ação
Executa as regras no manipulador com base no estado fornecido e retorna a lista de ações a ser executado.

Parâmetros:  
* **estado**: o estado de execução atual do conteúdo as regras estão em execução. 



  
**Devolve**: lista de ações que devem ser aplicadas no conteúdo.
  
### <a name="notifycommitedactions"></a>NotifyCommitedActions
Chamado assim que as ações calculadas terem sido aplicadas e o consolidado de dados no disco.

Parâmetros:  
* **estado**: o estado de execução atual do conteúdo depois das ações foram consolidado 


: Esta chamada envia um evento de auditoria