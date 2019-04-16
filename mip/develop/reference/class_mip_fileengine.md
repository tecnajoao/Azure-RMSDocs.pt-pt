---
title: classe mip::FileEngine
description: Documenta a classe mip::fileengine da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 15ce90a80430f50854580f6c7a2993d92db0a744
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573994"
---
# <a name="class-mipfileengine"></a>classe mip::FileEngine 
Essa classe fornece uma interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de const públicas & GetSettings() const  |  Devolve as definições de motor.
público const Std:: vector\<std::shared_ptr\<SensitivityTypesRulePackage\>\>& ListSensitivityTypes() const  |  lista os tipos de sensibilidade associados com o mecanismo da diretiva.
public const std::shared_ptr\<Label\> GetDefaultSensitivityLabel() const  |  Obtenha a etiqueta de sensibilidade predefinido.
público const Std:: vector\<std::shared_ptr\<etiqueta\>\>& ListSensitivityLabels()  |  Devolve uma lista de etiquetas de sensibilidade.
public const std::string& GetMoreInfoUrl() const  |  Forneça um url para buscar mais informações sobre as política/etiquetas.
public const std::string& GetPolicyId() const  |  Obtém o ID de política.
bool pública IsLabelingRequired() const  |  Verifica se a política determina que um documento deve ser o nome.
público std::chrono::time_point\<std::chrono::system_clock\> GetLastPolicyFetchTime() const  |  Obtém a hora quando a política pela última vez foi obtida.
CreateFileHandlerAsync void pública (Std:: String const & inputFilePath, const std::shared_ptr Std:: String & actualFilePath, bool isAuditDiscoveryEnabled, const\<FileHandler::Observer\>& fileHandlerObserver const std::shared_ptr\<void\>& context, const std::shared_ptr\<FileExecutionState\>& fileExecutionState)  |  Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.
CreateFileHandlerAsync void pública (const std::shared_ptr\<Stream\>& inputStream, const std::shared_ptr Std:: String & actualFilePath, bool isAuditDiscoveryEnabled, const\<FileHandler::Observer \>& fileHandlerObserver, const std::shared_ptr\<void\>& context, const std::shared_ptr\<FileExecutionState\>& fileExecutionState)  |  É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Regista um evento específico do aplicativo para o pipeline de auditoria.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetCustomSettings() const  |  Obtém uma lista de definições personalizadas.
bool pública HasClassificationRules() const  |  Obtém se a política tem regras de recomendação ou automático.
  
## <a name="members"></a>Membros
  
### <a name="getsettings-function"></a>Função de GetSettings
Devolve as definições de motor.
  
### <a name="listsensitivitytypes-function"></a>Função de ListSensitivityTypes
lista os tipos de sensibilidade associados com o mecanismo da diretiva.

  
**Devolve**: Uma lista de etiquetas de sensibilidade. vazio se LoadSensitivityTypesEnabled foi false (
  
**Consulte também**: [FileEngine::Settings](class_mip_fileengine_settings.md)).
  
### <a name="getdefaultsensitivitylabel-function"></a>Função de GetDefaultSensitivityLabel
Obtenha a etiqueta de sensibilidade predefinido.

  
**Devolve**: Etiqueta de sensibilidade a predefinição se existir, nullptr se não houver nenhum conjunto de etiqueta predefinida.
  
### <a name="listsensitivitylabels-function"></a>Função de ListSensitivityLabels
Devolve uma lista de etiquetas de sensibilidade.
  
### <a name="getmoreinfourl-function"></a>Função de GetMoreInfoUrl
Forneça um url para buscar mais informações sobre as política/etiquetas.

  
**Devolve**: Um url no formato de cadeia de caracteres.
  
### <a name="getpolicyid-function"></a>Função de GetPolicyId
Obtém o ID de política.

  
**Devolve**: Uma cadeia de caracteres que representam o ID de política
  
### <a name="islabelingrequired-function"></a>Função de IsLabelingRequired
Verifica se a política determina que um documento deve ser o nome.

  
**Devolve**: VERDADEIRO se a etiquetagem é obrigatório, caso contrário FALSO.
  
### <a name="getlastpolicyfetchtime-function"></a>Função de GetLastPolicyFetchTime
Obtém a hora quando a política pela última vez foi obtida.

  
**Devolve**: A hora quando a política pela última vez foi obtida
  
### <a name="createfilehandlerasync-function"></a>Função de CreateFileHandlerAsync
Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.

Parâmetros:  
* **inputFilePath**: O ficheiro para o abrir. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. 


* **actualFilePath**: O caminho de ficheiro (não temporária) real, será utilizado para auditoria. 


* **isAuditDiscoveryEnabled**: que representa se a deteção de auditoria está ativada ou não. 


* **fileHandlerObserver**: Implementar uma classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. 


* **context**: Contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="createfilehandlerasync-function"></a>Função de CreateFileHandlerAsync
É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.

Parâmetros:  
* **inputStream**: Um fluxo que contém os dados de ficheiro. 


* **actualFilePath**: O caminho para o ficheiro. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. Também irá utilizar para identificar o arquivo de auditoria. 


* **isAuditDiscoveryEnabled**: que representa se a deteção de auditoria está ativada ou não. 


* **fileHandlerObserver**: Implementar uma classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. 


* **context**: Contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="sendapplicationauditevent-function"></a>Função de SendApplicationAuditEvent
Regista um evento específico do aplicativo para o pipeline de auditoria.

Parâmetros:  
* **nível**: uma descrição de nível de registo: Informações/erro/aviso 


* **eventType**: uma descrição do tipo de evento 


* **eventData**: os dados associados ao evento


  
### <a name="getcustomsettings-function"></a>Função de GetCustomSettings
Obtém uma lista de definições personalizadas.

  
**Devolve**: Um vetor de configurações personalizadas
  
### <a name="hasclassificationrules-function"></a>Função de HasClassificationRules
Obtém se a política tem regras de recomendação ou automático.

  
**Devolve**: Um booleano que informará se há qualquer automático ou recommandation regras na política