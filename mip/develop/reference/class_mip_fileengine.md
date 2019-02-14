---
title: classe mip::FileEngine
description: Documenta a classe mip::fileengine da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: e397ad68fa39b318d6e4c08e36c450a474c3e5a9
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56255177"
---
# <a name="class-mipfileengine"></a>classe mip::FileEngine 
Essa classe fornece uma interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de const públicas & GetSettings() const  |  Devolve as definições de motor.
público const Std:: vector\<std::shared_ptr\<SensitivityTypesRulePackage\>\>& ListSensitivityTypes() const  |  lista os tipos de sensibilidade associados com o mecanismo da diretiva.
público const Std:: vector\<std::shared_ptr\<etiqueta\>\>& ListSensitivityLabels()  |  Devolve uma lista de etiquetas de sensibilidade.
public const std::string& GetMoreInfoUrl() const  |  Forneça um url para buscar mais informações sobre as política/etiquetas.
bool pública IsLabelingRequired() const  |  Verifica se a política determina que um documento deve ser o nome.
CreateFileHandlerAsync void pública (Std:: String const & inputFilePath, isAuditDiscoveryEnabled de bool Std:: String & contentIdentifier, const ContentState contentState, const, const std::shared_ptr\<FileHandler::Observer\>& fileHandlerObserver, const std::shared_ptr\<void\>& context, const std::shared_ptr\<FileExecutionState\>& fileExecutionState)  |  Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.
CreateFileHandlerAsync void pública (const std::shared_ptr\<Stream\>& inputStream, Std:: String const & inputFilePath, Std:: String const & contentIdentifier, const mip::ContentState contentState, bool isAuditDiscoveryEnabled, const std::shared_ptr\<FileHandler::Observer\>& fileHandlerObserver, const std::shared_ptr\<void\>& context, const std::shared_ptr\< FileExecutionState\>& fileExecutionState)  |  É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Regista um evento específico do aplicativo para o pipeline de auditoria.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetCustomSettings() const  |  Obtém uma lista de definições personalizadas.
  
## <a name="members"></a>Membros
  
### <a name="getsettings-function"></a>Função de GetSettings
Devolve as definições de motor.
  
### <a name="listsensitivitytypes-function"></a>Função de ListSensitivityTypes
lista os tipos de sensibilidade associados com o mecanismo da diretiva.

  
**Devolve**: Uma lista de etiquetas de sensibilidade. vazio se LoadSensitivityTypesEnabled foi false (
  
**Consulte também**: [FileEngine::Settings](class_mip_fileengine_settings.md)).
  
### <a name="listsensitivitylabels-function"></a>Função de ListSensitivityLabels
Devolve uma lista de etiquetas de sensibilidade.
  
### <a name="getmoreinfourl-function"></a>Função de GetMoreInfoUrl
Forneça um url para buscar mais informações sobre as política/etiquetas.

  
**Devolve**: Um url no formato de cadeia de caracteres.
  
### <a name="islabelingrequired-function"></a>Função de IsLabelingRequired
Verifica se a política determina que um documento deve ser o nome.

  
**Devolve**: VERDADEIRO se a etiquetagem é obrigatório, caso contrário FALSO.
  
### <a name="createfilehandlerasync-function"></a>Função de CreateFileHandlerAsync
Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.

Parâmetros:  
* **inputFilePath**: O ficheiro para o abrir. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. 


* **contentIdentifier**: um identificador legível por humanos para o conteúdo. exemplo de um arquivo: Exemplo de "C:\mip-sdk-for-cpp\files\audit.docx" [path\filename] para uma mensagem de e-mail: "RE: Auditoria design:user1@contoso.com"[assunto: remetente] 


* **contentState**: O estado do conteúdo enquanto a aplicação está a interagir com ele. 


* **isAuditDiscoveryEnabled**: que representa se a deteção de auditoria está ativada ou não. 


* **fileHandlerObserver**: Implementar uma classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. 


* **context**: Contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="createfilehandlerasync-function"></a>Função de CreateFileHandlerAsync
É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.

Parâmetros:  
* **inputStream**: Um fluxo que contém os dados de ficheiro. 


* **inputFilePath**: O caminho para o ficheiro. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. 


* **contentIdentifier**: um identificador legível por humanos para o conteúdo. exemplo de um arquivo: Exemplo de "C:\mip-sdk-for-cpp\files\audit.docx" [path\filename] para uma mensagem de e-mail: "RE: Auditoria design:user1@contoso.com"[assunto: remetente] 


* **contentState**: O estado do conteúdo enquanto a aplicação está a interagir com ele. 


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
