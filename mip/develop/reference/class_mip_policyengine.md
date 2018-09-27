# <a name="class-mippolicyengine"></a>classe mip::PolicyEngine 
Essa classe fornece uma interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Obter o mecanismo da diretiva [definições](class_mip_policyengine_settings.md).
Std:: vector const público < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Liste as etiquetas de sensibilidade associadas com o mecanismo da diretiva.
 público const Std:: String & GetMoreInfoUrl() const  |  Forneça um url para buscar mais informações sobre as política/etiquetas.
 bool pública IsLabelingRequired() const  |  Verifica se é ou não a política determina que um documento deve ser o nome.
público std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  Obtenha a etiqueta de sensibilidade predefinido.
público std::shared_ptr<PolicyHandler> CreatePolicyHandler (const Std:: String & contentIdentifier)  |  Criar um manipulador de política para executar a política relacionados com as funções no estado de execução de um ficheiro.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obter o mecanismo da diretiva [definições](class_mip_policyengine_settings.md).

  
**Devolve**: definições de motor de política. 
  
**Consulte também**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Etiqueta
Liste as etiquetas de sensibilidade associadas com o mecanismo da diretiva.

  
**Devolve**: uma lista de etiquetas de sensibilidade.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Forneça um url para buscar mais informações sobre as política/etiquetas.

  
**Devolve**: um url no formato de cadeia de caracteres.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Verifica se é ou não a política determina que um documento deve ser o nome.

  
**Devolve**: VERDADEIRO se a etiquetagem é obrigatório, caso contrário FALSO.
  
### <a name="label"></a>Etiqueta
Obtenha a etiqueta de sensibilidade predefinido.

  
**Devolve**: a predefinição de etiqueta sensitivy se existir, nullptr se não houver nenhum conjunto de etiqueta predefinida.
  
### <a name="policyhandler"></a>PolicyHandler
Criar um manipulador de política para executar a política relacionados com as funções no estado de execução de um ficheiro.

Parâmetros:  
* **contentIdentifier**: uma cadeia de caracteres exclusiva que identifica um ficheiro {conteúdo}. exemplo de um ficheiro: "C:\mip-sdk-for-cpp\files\audit.docx" [caminho: nome do ficheiro] de exemplo para uma mensagem de e-mail: "RE: auditoria design:user1@contoso.com" [assunto: remetente]



  
**Devolve**: o processador de política.