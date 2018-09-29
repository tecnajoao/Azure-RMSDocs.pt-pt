---
title: classe mip FileEngine
description: Referência para a classe mip FileEngine
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a7342edf27b19f43881b2e8d378fa243d26f7056
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446078"
---
# <a name="class-mipfileengine"></a>classe mip::FileEngine 
Essa classe fornece uma interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Devolve as definições de motor.
Std:: vector const público < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Devolve uma lista de etiquetas de sensibilidade.
 público const Std:: String & GetMoreInfoUrl() const  |  Forneça um url para buscar mais informações sobre as política/etiquetas.
 bool pública IsLabelingRequired() const  |  Verifica se a política determina que um documento deve ser o nome.
CreateFileHandlerAsync void pública (const Std:: String & inputFilePath, const ContentState contentState, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& contexto)  |  Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.
CreateFileHandlerAsync void pública (const std::shared_ptr<Stream>& inputStream, const Std:: String & inputFilePath, const mip::ContentState contentState, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& contexto)  |  É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.
 SendApplicationAuditEvent void pública (Std:: String const e nível, Std:: String const & eventType, Std:: String const e eventData)  |  Regista um evento específico do aplicativo para o pipeline de auditoria.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Devolve as definições de motor.
  
### <a name="label"></a>Etiqueta
Devolve uma lista de etiquetas de sensibilidade.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Forneça um url para buscar mais informações sobre as política/etiquetas.

  
**Devolve**: um url no formato de cadeia de caracteres.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Verifica se a política determina que um documento deve ser o nome.

  
**Devolve**: VERDADEIRO se a etiquetagem é obrigatório, caso contrário FALSO.
  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.

Parâmetros:  
* **O**: ficheiro para o abrir. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. 


* **contentState**: O estado do conteúdo enquanto a aplicação está a interagir com ele. 


* **R**: a implementação da classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.

Parâmetros:  
* **inputStream**: um fluxo que contém os dados de ficheiro. 


* **inputFilePath**: O caminho para o ficheiro. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. 


* **contentState**: O estado do conteúdo enquanto a aplicação está a interagir com ele. 


* **fileHandlerObserver**: implementar uma classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="sendapplicationauditevent"></a>SendApplicationAuditEvent
Regista um evento específico do aplicativo para o pipeline de auditoria.

Parâmetros:  
* **nível**: uma descrição de nível de registo: informações/erro/aviso 


* **eventType**: uma descrição do tipo de evento 


* **eventData**: os dados associados ao evento

