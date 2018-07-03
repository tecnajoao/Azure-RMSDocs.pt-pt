# <a name="class-mippolicyengine"></a>classe mip::PolicyEngine 
Essa classe fornece uma interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Obter o mecanismo da diretiva [definições](class_mip_policyengine_settings.md).
Std:: vector const público < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Liste as etiquetas de sensibilidade associadas com o mecanismo da diretiva.
público std::shared_ptr<ContentLabel> GetSensitivityLabel (const ExecutionState & Estado) const  |  Obter etiqueta de confidencialidade do conteúdo existente.
público std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  Obtenha a etiqueta de sensibilidade predefinido.
Std:: vector público < std::shared_ptr<Action>> ComputeActions (const ExecutionState & Estado)  |  Executa as regras no mecanismo de com base no estado fornecido e retorna a lista de ações a ser executado.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obter o mecanismo da diretiva [definições](class_mip_policyengine_settings.md).

  
**Devolve**: definições de motor de política. 
  
**Consulte também**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Etiqueta
Liste as etiquetas de sensibilidade associadas com o mecanismo da diretiva.

  
**Devolve**: uma lista de etiquetas de sensibilidade.
  
### <a name="contentlabel"></a>ContentLabel
Obter etiqueta de confidencialidade do conteúdo existente.
As informações necessárias para obter a etiqueta serão obtidas utilizando o estado de execução fornecida. 

Parâmetros:  
* **estado**: 



  
**Devolve**: um objeto de etiqueta de conteúdo que contém a sensibilidade de informações adicionais, bem como da etiqueta. Devolve vazio se não existir. 
  
**Consulte também**: [mip::ContentLabel](class_mip_contentlabel.md).
  
### <a name="label"></a>Etiqueta
Obtenha a etiqueta de sensibilidade predefinido.

  
**Devolve**: a predefinição de etiqueta sensitivy se existir, nullptr se não houver nenhum conjunto de etiqueta predefinida.
  
### <a name="action"></a>Ação
Executa as regras no mecanismo de com base no estado fornecido e retorna a lista de ações a ser executado.

Parâmetros:  
* **estado**: o estado de execução atual do conteúdo as regras estão em execução. 



  
**Devolve**: lista de ações que devem ser aplicadas no conteúdo.