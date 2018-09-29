---
title: classe mip ProtectionHandler
description: Referência para a classe mip ProtectionHandler
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6fbae05030f56d3c9e680e6de9c8177a11b2f1e2
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446758"
---
# <a name="class-mipprotectionhandler"></a>classe mip::ProtectionHandler 
Gere as ações relacionadas com a proteção para uma configuração de proteção específico.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::shared_ptr<Stream> CreateProtectedStream (const std::shared_ptr<Stream>& backingStream, contentSize de int64_t int64_t contentStartPosition,)  |  Crie um fluxo protegido que irá permitir a encriptação/desencriptação de conteúdo.
 público int64_t EncryptBuffer (int64_t offsetFromStart, const uint8_t * inputBuffer, int64_t inputBufferSize, uint8_t * outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Encripte uma memória intermédia.
 público int64_t DecryptBuffer (int64_t offsetFromStart, const uint8_t * inputBuffer, int64_t inputBufferSize, uint8_t * outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Descriptografar uma memória intermédia.
 público int64_t GetProtectedContentLength (int64_t unprotectedLength, bool includesFinalBlock)  |  Calcula o tamanho (em bytes) de conteúdo se fosse sendo criptografados com isso [ProtectionHandler](class_mip_protectionhandler.md).
 público int64_t GetBlockSize()  |  Obtém o tamanho do bloco (em bytes) para o modo de cifra utilizado por este [ProtectionHandler](class_mip_protectionhandler.md).
público Std:: vector Std:: < String > GetRights() const  |  Obtém os direitos concedidos a/identidade do utilizador associada a este [ProtectionHandler](class_mip_protectionhandler.md).
 bool pública AccessCheck (const Std:: String & direita) const  |  Verifica se o manipulador de proteção concede acesso de utilizador especificado certo.
 público const Std:: String GetIssuedTo()  |  Obtém o utilizador associado ao manipulador de proteção.
 público const Std:: String GetOwner()  |  Obtém endereço de e-mail do proprietário do conteúdo.
 bool pública IsIssuedToOwner()  |  Obtém o se o utilizador atual é o proprietário do conteúdo ou não.
público std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor()  |  Obtém os detalhes de proteção.
 público const Std:: String GetContentId()  |  Obtém o identificador exclusivo para o/conteúdo do documento.
 bool pública DoesUseDeprecatedAlgorithms()  |  Obtém se utiliza do manipulador de proteção preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores, ou não.
 bool pública IsAuditedExtractAllowed()  |  Obtém se o manipulador de proteção concede o utilizador 'auditado extrair"à direita ou não.
público const Std:: vector < uint8_t > GetSerializedPublishingLicense()  |  Serializar [ProtectionHandler](class_mip_protectionhandler.md) numa licença de publicação (PL)
  
## <a name="members"></a>Membros
  
### <a name="stream"></a>Stream
Crie um fluxo protegido que irá permitir a encriptação/desencriptação de conteúdo.

Parâmetros:  
* **backingStream**: fluxo de segurança do que de leitura/escrita 


* **contentStartPosition**: a iniciar a posição (em bytes) dentro do fluxo de segurança onde começa a conteúdo protegido 


* **contentSize**: tamanho (em bytes) de conteúdos protegidos dentro do fluxo de segurança



  
**Devolve**: stream protegido
  
### <a name="encryptbuffer"></a>EncryptBuffer
Encripte uma memória intermédia.

Parâmetros:  
* **offsetFromStart**: posição relativa de inputBuffer desde o início do conteúdo de texto simples 


* **inputBuffer**: memória intermédia de conteúdo de texto simples que será encriptado 


* **inputBufferSize**: tamanho (em bytes) da memória intermédia de entrada 


* **outputBuffer**: Buffer no qual será copiado conteúdo encriptado 


* **outputBufferSize**: tamanho (em bytes) da memória intermédia de saída 


* **isFinal**: se a memória intermédia de entrada contém os bytes de texto simples final ou não



  
**Devolve**: tamanho real (em bytes) de conteúdo encriptado
  
### <a name="decryptbuffer"></a>DecryptBuffer
Descriptografar uma memória intermédia.

Parâmetros:  
* **offsetFromStart**: posição relativa de inputBuffer desde o início do conteúdo encriptado 


* **inputBuffer**: memória intermédia de conteúdo encriptado que irá ser desencriptado 


* **inputBufferSize**: tamanho (em bytes) da memória intermédia de entrada 


* **outputBuffer**: Buffer no qual será copiado desencriptado conteúdo 


* **outputBufferSize**: tamanho (em bytes) da memória intermédia de saída 


* **isFinal**: se a memória intermédia de entrada contém os bytes encriptados finais ou não



  
**Devolve**: tamanho real (em bytes) de conteúdo desencriptado
  
### <a name="getprotectedcontentlength"></a>GetProtectedContentLength
Calcula o tamanho (em bytes) de conteúdo se fosse sendo criptografados com isso [ProtectionHandler](class_mip_protectionhandler.md).

Parâmetros:  
* **unprotectedLength**: tamanho (em bytes) de conteúdo não protegido 


* **includesFinalBlock**: descreve se o conteúdo não protegido em questão inclui o bloco final, ou não. Por exemplo, no modo de encriptação CBC4k, blocos de protegido não final são o mesmo tamanho que blocos não protegidos, mas blocos protegidos finais são maiores do que suas contrapartes não protegidos.



  
**Devolve**: tamanho (em bytes) de conteúdo protegido
  
### <a name="getblocksize"></a>GetBlockSize
Obtém o tamanho do bloco (em bytes) para o modo de cifra utilizado por este [ProtectionHandler](class_mip_protectionhandler.md).

  
**Devolve**: Bloquear tamanho (em bytes)
  
### <a name="getrights"></a>GetRights
Obtém os direitos concedidos a/identidade do utilizador associada a este [ProtectionHandler](class_mip_protectionhandler.md).

  
**Devolve**: direitos concedidos ao utilizador
  
### <a name="accesscheck"></a>AccessCheck
Verifica se o manipulador de proteção concede acesso de utilizador especificado certo.

Parâmetros:  
* **certo**: direito para verificar



  
**Devolve**: se o manipulador de proteção concede acesso de utilizador especificado, à direita ou não
  
### <a name="getissuedto"></a>GetIssuedTo
Obtém o utilizador associado ao manipulador de proteção.

  
**Devolve**: utilizador associado o manipulador de proteção
  
### <a name="getowner"></a>GetOwner
Obtém endereço de e-mail do proprietário do conteúdo.

  
**Devolve**: endereço de E-Mail do proprietário do conteúdo
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Obtém o se o utilizador atual é o proprietário do conteúdo ou não.

  
**Devolve**: se o utilizador atual é o proprietário do conteúdo ou não
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Obtém os detalhes de proteção.

  
**Devolve**: detalhes de proteção
  
### <a name="getcontentid"></a>GetContentId
Obtém o identificador exclusivo para o/conteúdo do documento.

  
**Devolve**: Identificador exclusivo de conteúdo
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Obtém se utiliza do manipulador de proteção preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores, ou não.

  
**Devolve**: se utiliza de manipulador de proteção preterido algoritmos criptográficos ou não
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Obtém se o manipulador de proteção concede o utilizador 'auditado extrair"à direita ou não.

  
**Devolve**: se o manipulador de proteção concede o utilizador 'auditado extrair"à direita ou não
  
### <a name="getserializedpublishinglicense"></a>GetSerializedPublishingLicense
Serializar [ProtectionHandler](class_mip_protectionhandler.md) numa licença de publicação (PL)

  
**Devolve**: licença serializada de publicação