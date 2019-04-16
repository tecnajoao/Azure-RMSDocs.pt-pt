---
title: classe mip::PolicyEngine
description: Documenta a classe mip::policyengine da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: ce8ef7df12cdc9823a62234b5dadaaacdb7fed37
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573790"
---
# <a name="class-mippolicyengine"></a>classe mip::PolicyEngine 
Essa classe fornece uma interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de const públicas & GetSettings() const  |  Obter o mecanismo da diretiva [definições](class_mip_policyengine_settings.md).
público const Std:: vector\<std::shared_ptr\<etiqueta\>\>& ListSensitivityLabels()  |  Liste as etiquetas de sensibilidade associadas com o mecanismo da diretiva.
público const Std:: vector\<std::shared_ptr\<SensitivityTypesRulePackage\>\>& ListSensitivityTypes() const  |  lista os tipos de sensibilidade associados com o mecanismo da diretiva.
public const std::string& GetMoreInfoUrl() const  |  Forneça um url para buscar mais informações sobre as política/etiquetas.
bool pública IsLabelingRequired() const  |  Verifica se a política determina que um documento deve ser etiquetado ou não.
public std::shared_ptr\<Label\> GetDefaultSensitivityLabel()  |  Obtenha a etiqueta de sensibilidade predefinido.
público std::shared_ptr\<PolicyHandler\> CreatePolicyHandler (bool isAuditDiscoveryEnabled)  |  Crie um manipulador de política para executar funções relacionadas com a política no estado de execução de um ficheiro.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Regista um evento específico do aplicativo para o pipeline de auditoria.
public const std::string& GetPolicyDataXml() const  |  Obtém dados de política XML que descreve as definições, etiquetas e regras associadas esta política.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetCustomSettings() const  |  Obtém uma lista de definições personalizadas.
public const std::string& GetPolicyId() const  |  Obtém o ID de política.
bool pública HasClassificationRules() const  |  Obtém se a política tem regras de recomendação ou automático.
público std::chrono::time_point\<std::chrono::system_clock\> GetLastPolicyFetchTime() const  |  Obtém a hora quando a política pela última vez foi obtida.
  
## <a name="members"></a>Membros
  
### <a name="getsettings-function"></a>Função de GetSettings
Obter o mecanismo da diretiva [definições](class_mip_policyengine_settings.md).

  
**Devolve**: Definições de motor de política. 
  
**Consulte também**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="listsensitivitylabels-function"></a>Função de ListSensitivityLabels
Liste as etiquetas de sensibilidade associadas com o mecanismo da diretiva.

  
**Devolve**: Uma lista de etiquetas de sensibilidade.
  
### <a name="listsensitivitytypes-function"></a>Função de ListSensitivityTypes
lista os tipos de sensibilidade associados com o mecanismo da diretiva.

  
**Devolve**: Uma lista de etiquetas de sensibilidade. vazio se LoadSensitivityTypesEnabled foi false (
  
**Consulte também**: [PolicyEngine::Settings](class_mip_policyengine_settings.md)).
  
### <a name="getmoreinfourl-function"></a>Função de GetMoreInfoUrl
Forneça um url para buscar mais informações sobre as política/etiquetas.

  
**Devolve**: Um url no formato de cadeia de caracteres.
  
### <a name="islabelingrequired-function"></a>Função de IsLabelingRequired
Verifica se a política determina que um documento deve ser etiquetado ou não.

  
**Devolve**: VERDADEIRO se a etiquetagem é obrigatório, caso contrário FALSO.
  
### <a name="getdefaultsensitivitylabel-function"></a>Função de GetDefaultSensitivityLabel
Obtenha a etiqueta de sensibilidade predefinido.

  
**Devolve**: Etiqueta de sensibilidade a predefinição se existir, nullptr se não houver nenhum conjunto de etiqueta predefinida.
  
### <a name="createpolicyhandler-function"></a>Função de CreatePolicyHandler
Crie um manipulador de política para executar funções relacionadas com a política no estado de execução de um ficheiro.

Parâmetros:  
* **A**: booleano representando se a deteção de auditoria está ativada ou não.



  
**Devolve**: Processador de política.
Aplicação tem de manter o objeto de política de manipulador para o tempo de vida do documento.
  
### <a name="sendapplicationauditevent-function"></a>Função de SendApplicationAuditEvent
Regista um evento específico do aplicativo para o pipeline de auditoria.

Parâmetros:  
* **nível**: do nível de registo: Informações/erro/aviso. 


* **eventType**: uma descrição do tipo de evento. 


* **eventData**: os dados associados ao evento.


  
### <a name="getpolicydataxml-function"></a>Função de GetPolicyDataXml
Obtém dados de política XML que descreve as definições, etiquetas e regras associadas esta política.

  
**Devolve**: Dados de política XML.
  
### <a name="getcustomsettings-function"></a>Função de GetCustomSettings
Obtém uma lista de definições personalizadas.

  
**Devolve**: Um vetor de configurações personalizadas.
  
### <a name="getpolicyid-function"></a>Função de GetPolicyId
Obtém o ID de política.

  
**Devolve**: Uma cadeia de caracteres que representam o ID de política
  
### <a name="hasclassificationrules-function"></a>Função de HasClassificationRules
Obtém se a política tem regras de recomendação ou automático.

  
**Devolve**: Um booleano que informará se há qualquer automático ou recommandation regras na política
  
### <a name="getlastpolicyfetchtime-function"></a>Função de GetLastPolicyFetchTime
Obtém a hora quando a política pela última vez foi obtida.

  
**Devolve**: A hora quando a política pela última vez foi obtida