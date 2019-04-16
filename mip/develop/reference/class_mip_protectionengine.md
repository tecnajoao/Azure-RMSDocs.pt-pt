---
title: classe mip::ProtectionEngine
description: Documenta a classe mip::protectionengine da Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 60a61f5e06b5e76cbf0c557e7d489a8d618a8261
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574160"
---
# <a name="class-mipprotectionengine"></a>classe mip::ProtectionEngine 
Gere as ações relacionadas com a proteção relacionados com uma identidade específica.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Definições de const públicas & GetSettings() const  |  Obtém as definições de motor.
public void GetTemplatesAsync(const std::shared_ptr\<ProtectionEngine::Observer\>& observer, const std::shared_ptr\<void\>& context)  |  Obter coleção de modelos disponíveis para um utilizador.
public std::vector\<std::string\> GetTemplates(const std::shared_ptr\<void\>& context)  |  Obter coleção de modelos disponíveis para um utilizador.
GetRightsForLabelIdAsync void pública (Std:: String const & documentId, Std:: String const & labelId, Std:: String const & ownerEmail, const std::shared_ptr\<ProtectionEngine::Observer\>& observador, e const padrão: : shared_ptr\<void\>& contexto)  |  Obter coleção de direitos disponíveis a um utilizador para um ID de etiqueta.
public std::vector\<std::string\> GetRightsForLabelId(const std::string& documentId, const std::string& labelId, const std::string& ownerEmail, const std::shared_ptr\<void\>& context)  |  Obter coleção de direitos disponíveis a um utilizador para um labelId.
CreateProtectionHandlerFromDescriptorAsync void pública (const std::shared_ptr\<ProtectionDescriptor\>& descritor, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr\< ProtectionHandler::Observer\>& observador, const std::shared_ptr\<void\>& contexto)  |  Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.
público std::shared_ptr\<ProtectionHandler\> CreateProtectionHandlerFromDescriptor (const std::shared_ptr\<ProtectionDescriptor\>& descritor de const ProtectionHandlerCreationOptions & Opções, const std::shared_ptr\<void\>& contexto)  |  Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.
CreateProtectionHandlerFromPublishingLicenseAsync void pública (Std:: vector const\<uint8_t\>& serializedPublishingLicense, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr\<ProtectionHandler::Observer\>& observador, const std::shared_ptr\<void\>& contexto)  |  Cria um manipulador de proteção a partir de uma licença de publicação serializada.
público std::shared_ptr\<ProtectionHandler\> CreateProtectionHandlerFromPublishingLicense (Std:: vector const\<uint8_t\>& serializedPublishingLicense, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr\<void\>& contexto)  |  Cria um manipulador de proteção a partir de uma licença de publicação serializada.
CreateProtectionHandlerFromProtectionInfoAsync void pública (Std:: vector const\<uint8_t\>& serializedPublishingLicense, Std:: vector const\<uint8_t\>& serializedProtectionInfo, Const std::shared_ptr\<ProtectionHandler::Observer\>& observador, const std::shared_ptr\<void\>& contexto)  |  Cria um manipulador de proteção a partir de uma licença de publicação serializada e uma informação de proteção serializada.
público std::shared_ptr\<ProtectionHandler\> CreateProtectionHandlerFromProtectionInfo (Std:: vector const\<uint8_t\>& serializedPublishingLicense, Std:: vector const\< uint8_t\>& serializedProtectionInfo, const std::shared_ptr\<void\>& contexto)  |  Cria um manipulador de proteção a partir de uma licença de publicação serializada e uma informação de proteção serializada.
CreateProtectionHandlerFromPublishingLicenseContextAsync void pública (const std::shared_ptr PublishingLicenseContext & publishingLicenseContext, const ProtectionHandlerCreationOptions e opções, const\< ProtectionHandler::Observer\>& observador, const std::shared_ptr\<void\>& contexto)  |  Cria um manipulador de proteção de um contexto de licença de publicação.
público std::shared_ptr\<ProtectionHandler\> CreateProtectionHandlerFromPublishingLicenseContext (const PublishingLicenseContext & publishingLicenseContext, const ProtectionHandlerCreationOptions & opções, const std::shared_ptr\<void\>& contexto)  |  Cria um manipulador de proteção de um contexto de licença de publicação.
  
## <a name="members"></a>Membros
  
### <a name="getsettings-function"></a>Função de GetSettings
Obtém as definições de motor.

  
**Devolve**: Definições de motor
  
### <a name="gettemplatesasync-function"></a>Função de GetTemplatesAsync
Obter coleção de modelos disponíveis para um utilizador.

Parâmetros:  
* **observer**: Implementar uma classe a [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interface 


* **context**: Contexto de cliente que será forma opaca com êxito para observadores e opcional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="gettemplates-function"></a>Função de GetTemplates
Obter coleção de modelos disponíveis para um utilizador.

Parâmetros:  
* **context**: Contexto de cliente que será forma opaca passado para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: Lista de IDs de modelo
  
### <a name="getrightsforlabelidasync-function"></a>Função de GetRightsForLabelIdAsync
Obter coleção de direitos disponíveis a um utilizador para um ID de etiqueta.

Parâmetros:  
* **documentId**: ID do documento associado com os metadados de documento 


* **labelId**: [Etiqueta](class_mip_label.md) ID associado o metadados de documentos com a qual o documento criado 


* **ownerEmail**: proprietário do documento 


* **observer**: Implementar uma classe a [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interface 


* **context**: Neste contexto mesmo será encaminhado ao [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess-function) ou [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure-function)


  
### <a name="getrightsforlabelid-function"></a>GetRightsForLabelId function
Obter coleção de direitos disponíveis a um utilizador para um labelId.

Parâmetros:  
* **documentId**: ID do documento associado com os metadados de documento 


* **labelId**: [Etiqueta](class_mip_label.md) ID associado o metadados de documentos com a qual o documento criado 


* **ownerEmail**: Proprietário do documento 


* **context**: Neste contexto mesmo será reencaminhado para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: Lista de direitos
  
### <a name="createprotectionhandlerfromdescriptorasync-function"></a>Função de CreateProtectionHandlerFromDescriptorAsync
Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.

Parâmetros:  
* **descriptor**: R [ProtectionDescriptor](class_mip_protectiondescriptor.md) que descreve a configuração da proteção 


* **Opções de**: Opções de criação 


* **observer**: Implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **context**: Contexto de cliente que será forma opaca com êxito para observadores e opcional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="createprotectionhandlerfromdescriptor-function"></a>Função de CreateProtectionHandlerFromDescriptor
Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.

Parâmetros:  
* **descriptor**: R [ProtectionDescriptor](class_mip_protectiondescriptor.md) que descreve a configuração da proteção 


* **Opções de**: Opções de criação 


* **context**: Contexto de cliente que será passado de forma opaca para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicenseasync-function"></a>Função de CreateProtectionHandlerFromPublishingLicenseAsync
Cria um manipulador de proteção a partir de uma licença de publicação serializada.

Parâmetros:  
* **serializedPublishingLicense**: Uma licença de publicação serializada 


* **Opções de**: Opções de criação 


* **observer**: Implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **context**: Contexto de cliente que será forma opaca com êxito para observadores e opcional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="createprotectionhandlerfrompublishinglicense-function"></a>Função de CreateProtectionHandlerFromPublishingLicense
Cria um manipulador de proteção a partir de uma licença de publicação serializada.

Parâmetros:  
* **serializedPublishingLicense**: Uma licença de publicação serializada 


* **Opções de**: Opções de criação 


* **observer**: Implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **context**: Contexto de cliente que será passado de forma opaca para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfromprotectioninfoasync-function"></a>Função de CreateProtectionHandlerFromProtectionInfoAsync
Cria um manipulador de proteção a partir de uma licença de publicação serializada e uma informação de proteção serializada.

Parâmetros:  
* **serializedPublishingLicense**: Uma licença de publicação serializada 


* **serializedProtectionInfo**: Informações de proteção serializados 


* **observer**: Implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **context**: Contexto de cliente que irá ser transmitido de forma opaca para observadores


  
### <a name="createprotectionhandlerfromprotectioninfo-function"></a>Função de CreateProtectionHandlerFromProtectionInfo
Cria um manipulador de proteção a partir de uma licença de publicação serializada e uma informação de proteção serializada.

Parâmetros:  
* **serializedPublishingLicense**: Uma licença de publicação serializada 


* **serializedProtectionInfo**: Informações de proteção serializados 


* **context**: Contexto de cliente que irá ser transmitido de forma opaca para observadores



  
**Devolve**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicensecontextasync-function"></a>Função de CreateProtectionHandlerFromPublishingLicenseContextAsync
Cria um manipulador de proteção de um contexto de licença de publicação.

Parâmetros:  
* **publishingLicenseContext**: Uma forma de pré-processada de licença de publicação serializada 


* **Opções de**: Opções de criação 


* **observer**: Implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **context**: Contexto de cliente que será forma opaca com êxito para observadores e opcional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="createprotectionhandlerfrompublishinglicensecontext-function"></a>Função de CreateProtectionHandlerFromPublishingLicenseContext
Cria um manipulador de proteção de um contexto de licença de publicação.

Parâmetros:  
* **publishingLicenseContext**: Uma forma de pré-processada de licença de publicação serializada 


* **Opções de**: Opções de criação 


* **observer**: Implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **context**: Contexto de cliente que será passado de forma opaca para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: [ProtectionHandler](class_mip_protectionhandler.md)