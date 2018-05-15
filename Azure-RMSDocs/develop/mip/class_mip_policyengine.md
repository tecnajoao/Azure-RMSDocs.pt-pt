# <a name="class-mippolicyengine"></a>classe mip::PolicyEngine 
Esta classe fornece uma interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const público & GetSettings() const  |  Obter o motor de política [definições](class_mip_policyengine_settings.md).
pública std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Liste as etiquetas de sensibilidade associadas com o motor de política.
std::shared_ptr pública<ContentLabel> GetSensitivityLabel (Estado & const ExecutionState)  |  Obter a etiqueta de sensibilidade de conteúdo existente.
std::shared_ptr pública<Label> GetDefaultSensitivityLabel()  |  Obter a etiqueta de sensibilidade predefinida.
std::vector pública < std::shared_ptr<Action>> ComputeActions (Estado & const ExecutionState)  |  Executa as regras no motor de com base no estado do fornecida e devolve a lista de ações para ser executada.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obter o motor de política [definições](class_mip_policyengine_settings.md).

  
**Devolve**: definições de motor de política. 
**Consulte também**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Etiqueta
Liste as etiquetas de sensibilidade associadas com o motor de política.

  
**Devolve**: uma lista de etiquetas de sensibilidade.
  
### <a name="contentlabel"></a>ContentLabel
Obter a etiqueta de sensibilidade de conteúdo existente.
As informações necessárias para obter a etiqueta irão ser obtidas usando o estado de execução fornecida. 

Parâmetros:  
* **Estado**: 



  
**Devolve**: informações adicionais, bem como de etiqueta de um objeto de etiqueta de conteúdo que contém a sensibilidade. Devolve em branco se não existir. 
**Consulte também**: [mip::ContentLabel](class_mip_contentlabel.md).
  
### <a name="label"></a>Etiqueta
Obter a etiqueta de sensibilidade predefinida.

  
**Devolve**: predefinido etiqueta sensitivy se existir, nullptr se não houver nenhum conjunto de etiqueta predefinida.
  
### <a name="action"></a>Ação
Executa as regras no motor de com base no estado do fornecida e devolve a lista de ações para ser executada.

Parâmetros:  
* **estado**: o estado de execução atual do conteúdo as regras estão em execução. 



  
**Devolve**: lista de ações que deve ser aplicada no conteúdo.