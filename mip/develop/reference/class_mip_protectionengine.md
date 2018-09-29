---
title: classe mip ProtectionEngine
description: Referência para a classe mip ProtectionEngine
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: ddc8cfd58acb2a80d024978084b625f3d3728c87
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446741"
---
# <a name="class-mipprotectionengine"></a>classe mip::ProtectionEngine 
Gere as ações relacionadas com a proteção relacionados com uma identidade específica.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Obtém as definições de motor.
GetTemplatesAsync void pública (std::shared_ptr const < ProtectionEngine::Observer > & observador, const std::shared_ptr<void>& contexto)  |  Obter coleção de modelos disponíveis para um utilizador.
público Std:: vector Std:: < String > GetTemplates (const std::shared_ptr<void>& contexto)  |  Obter coleção de modelos disponíveis para um utilizador.
GetRightsForLabelIdAsync void pública (const Std:: String & documentId, const Std:: String & labelId, const Std:: String ownerEmail, const std::shared_ptr < ProtectionEngine::Observer > & observador, const std::shared_ptr<void>& contexto)  |  Obter coleção de direitos disponíveis a um utilizador para um ID de etiqueta.
público Std:: vector Std:: < String > GetRightsForLabelId (Std:: String const & documentId, Std:: String const & labelId, Std:: String const & ownerEmail, const std::shared_ptr<void>& contexto)  |  Obter coleção de direitos disponíveis a um utilizador para um labelId.
GetGrantingLabelIdsAsync void pública (std::shared_ptr const < ProtectionEngine::Observer > & observador, const std::shared_ptr<void>& contexto)  |  Obter coleção de disponíveis de IDs de etiqueta a um utilizador.
público Std:: vector Std:: < String > GetGrantingLabelIds (const std::shared_ptr<void>& contexto)  |  Obter coleção de disponíveis de IDs de etiqueta a um utilizador.
CreateProtectionHandlerFromDescriptorAsync void pública (const std::shared_ptr<ProtectionDescriptor>& descritor, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr < ProtectionHandler::Observer > e observador, Const std::shared_ptr<void>& contexto)  |  Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.
público std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromDescriptor (const std::shared_ptr<ProtectionDescriptor>& descritor, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr<void>& contexto)  |  Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.
CreateProtectionHandlerFromPublishingLicenseAsync void pública (const Std:: vector < uint8_t > & serializedPublishingLicense, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr < ProtectionHandler::Observer > & observador, const std::shared_ptr<void>& contexto)  |  Cria um manipulador de proteção a partir de uma licença de publicação serializada.
público std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromPublishingLicense (const Std:: vector < uint8_t > & serializedPublishingLicense, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr<void>& contexto)  |  Cria um manipulador de proteção a partir de uma licença de publicação serializada.
CreateProtectionHandlerFromPublishingLicenseContextAsync void pública (const std::shared_ptr PublishingLicenseContext & publishingLicenseContext, const ProtectionHandlerCreationOptions e opções, const < ProtectionHandler::O bserver > & observador, const std::shared_ptr<void>& contexto)  |  Cria um manipulador de proteção de um contexto de licença de publicação.
público std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromPublishingLicenseContext (const PublishingLicenseContext & publishingLicenseContext, const ProtectionHandlerCreationOptions e opções, const std::shared_ptr<void>& contexto)  |  Cria um manipulador de proteção de um contexto de licença de publicação.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obtém as definições de motor.

  
**Devolve**: o motor de definições
  
### <a name="gettemplatesasync"></a>GetTemplatesAsync
Obter coleção de modelos disponíveis para um utilizador.

Parâmetros:  
* **observador**: implementar uma classe a [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interface 


* **contexto**: o contexto de cliente que será forma opaca com êxito para observadores e opcional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="gettemplates"></a>GetTemplates
Obter coleção de modelos disponíveis para um utilizador.

Parâmetros:  
* **contexto**: o contexto de cliente que será forma opaca passado para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: lista de IDs de modelo
  
### <a name="getrightsforlabelidasync"></a>GetRightsForLabelIdAsync
Obter coleção de direitos disponíveis a um utilizador para um ID de etiqueta.

Parâmetros:  
* **documentId**: ID de documento associado com os metadados de documento 


* **labelId**: [etiqueta](class_mip_label.md) ID associado o metadados de documentos com a qual o documento criado 


* **ownerEmail**: proprietário do documento 


* **observador**: implementar uma classe a [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interface 


* **contexto**: este mesmo contexto será encaminhado ao [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) ou [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure)


  
### <a name="getrightsforlabelid"></a>GetRightsForLabelId
Obter coleção de direitos disponíveis a um utilizador para um labelId.

Parâmetros:  
* **documentId**: ID de documento associado com os metadados de documento 


* **labelId**: [etiqueta](class_mip_label.md) ID associado o metadados de documentos com a qual o documento criado 


* **ownerEmail**: proprietário do documento 


* **contexto**: este mesmo contexto será reencaminhado para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: lista de direitos
  
### <a name="getgrantinglabelidsasync"></a>GetGrantingLabelIdsAsync
Obter coleção de disponíveis de IDs de etiqueta a um utilizador.

Parâmetros:  
* **observador**: implementar uma classe a [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) interface 


* **contexto**: este mesmo contexto será encaminhado ao [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) ou ProtectionEngine::Observer::OnGrantingLabelIdsFailure


  
### <a name="getgrantinglabelids"></a>GetGrantingLabelIds
Obter coleção de disponíveis de IDs de etiqueta a um utilizador.

Parâmetros:  
* **contexto**: este mesmo contexto será reencaminhado para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: lista de IDs de etiqueta
  
### <a name="createprotectionhandlerfromdescriptorasync"></a>CreateProtectionHandlerFromDescriptorAsync
Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.

Parâmetros:  
* **descritor**: A [ProtectionDescriptor](class_mip_protectiondescriptor.md) que descreve a configuração da proteção 


* **Opções de**: opções de criação 


* **observador**: implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **contexto**: o contexto de cliente que será forma opaca com êxito para observadores e opcional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="protectionhandler"></a>ProtectionHandler
Cria um manipulador de proteção em que os direitos/funções são atribuídas a utilizadores específicos.

Parâmetros:  
* **descritor**: A [ProtectionDescriptor](class_mip_protectiondescriptor.md) que descreve a configuração da proteção 


* **Opções de**: opções de criação 


* **contexto**: o contexto de cliente que será passado de forma opaca para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicenseasync"></a>CreateProtectionHandlerFromPublishingLicenseAsync
Cria um manipulador de proteção a partir de uma licença de publicação serializada.

Parâmetros:  
* **serializedPublishingLicense**: serializada de uma licença de publicação 


* **Opções de**: opções de criação 


* **observador**: implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **contexto**: o contexto de cliente que será forma opaca com êxito para observadores e opcional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="protectionhandler"></a>ProtectionHandler
Cria um manipulador de proteção a partir de uma licença de publicação serializada.

Parâmetros:  
* **serializedPublishingLicense**: serializada de uma licença de publicação 


* **Opções de**: opções de criação 


* **observador**: implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **contexto**: o contexto de cliente que será passado de forma opaca para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicensecontextasync"></a>CreateProtectionHandlerFromPublishingLicenseContextAsync
Cria um manipulador de proteção de um contexto de licença de publicação.

Parâmetros:  
* **publishingLicenseContext**: uma forma de pré-processada de licença de publicação serializada 


* **Opções de**: opções de criação 


* **observador**: implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **contexto**: o contexto de cliente que será forma opaca com êxito para observadores e opcional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="protectionhandler"></a>ProtectionHandler
Cria um manipulador de proteção de um contexto de licença de publicação.

Parâmetros:  
* **publishingLicenseContext**: uma forma de pré-processada de licença de publicação serializada 


* **Opções de**: opções de criação 


* **observador**: implementar uma classe a [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) interface 


* **contexto**: o contexto de cliente que será passado de forma opaca para opcional [HttpDelegate](class_mip_httpdelegate.md)



  
**Devolve**: [ProtectionHandler](class_mip_protectionhandler.md)