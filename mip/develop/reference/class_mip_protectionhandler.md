---
title: classe mip::ProtectionHandler
description: Documenta a classe mip::protectionhandler da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 017268be0b3ea71b021b6a8d775dcb7bd69e8dc6
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56253089"
---
# <a name="class-mipprotectionhandler"></a>classe mip::ProtectionHandler 
Gere as ações relacionadas com a proteção para uma configuração de proteção específico.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public std::shared_ptr\<Stream\> CreateProtectedStream(const std::shared_ptr\<Stream\>& backingStream, int64_t contentStartPosition, int64_t contentSize)  |  Crie um fluxo protegido que irá permitir a encriptação/desencriptação de conteúdo.
public int64_t EncryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Encripte uma memória intermédia.
public int64_t DecryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Descriptografar uma memória intermédia.
public int64_t GetProtectedContentLength(int64_t unprotectedLength, bool includesFinalBlock)  |  Calcula o tamanho (em bytes) de conteúdo se fosse sendo criptografados com isso [ProtectionHandler](class_mip_protectionhandler.md).
public int64_t GetBlockSize()  |  Obtém o tamanho do bloco (em bytes) para o modo de cifra utilizado por este [ProtectionHandler](class_mip_protectionhandler.md).
público Std:: vector\<Std:: String\> GetRights() const  |  Obtém os direitos concedidos a/identidade do utilizador associada a este [ProtectionHandler](class_mip_protectionhandler.md).
bool pública AccessCheck (const Std:: String & direita) const  |  Verifica se o manipulador de proteção concede acesso de utilizador especificado certo.
public const std::string GetIssuedTo()  |  Obtém o utilizador associado ao manipulador de proteção.
public const std::string GetOwner()  |  Obtém endereço de e-mail do proprietário do conteúdo.
bool pública IsIssuedToOwner()  |  Obtém o se o utilizador atual é o proprietário do conteúdo ou não.
public std::shared_ptr\<ProtectionDescriptor\> GetProtectionDescriptor()  |  Obtém os detalhes de proteção.
public const std::string GetContentId()  |  Obtém o identificador exclusivo para o/conteúdo do documento.
bool pública DoesUseDeprecatedAlgorithms()  |  Obtém se utiliza do manipulador de proteção preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores, ou não.
bool pública IsAuditedExtractAllowed()  |  Obtém se o manipulador de proteção concede o utilizador 'auditado extrair"à direita ou não.
público const Std:: vector\<uint8_t\> GetSerializedPublishingLicense()  |  Serializar [ProtectionHandler](class_mip_protectionhandler.md) numa licença de publicação (PL)
public const std::vector\<uint8_t\> GetSerializedProtectionInfo()  |  Obtém as informações de proteção.
  
## <a name="members"></a>Membros
  
### <a name="createprotectedstream-function"></a>Função de CreateProtectedStream
Crie um fluxo protegido que irá permitir a encriptação/desencriptação de conteúdo.

Parâmetros:  
* **backingStream**: Fluxo de segurança do que de leitura/escrita 


* **contentStartPosition**: A iniciar a posição (em bytes) dentro do fluxo de segurança onde começa a conteúdo protegido 


* **contentSize**: Tamanho (em bytes) de conteúdos protegidos dentro do fluxo de segurança



  
**Devolve**: Stream protegido
  
### <a name="encryptbuffer-function"></a>Função de EncryptBuffer
Encripte uma memória intermédia.

Parâmetros:  
* **offsetFromStart**: Posição relativa de inputBuffer desde o início do conteúdo de texto simples 


* **inputBuffer**: Memória intermédia de conteúdo de texto simples que será encriptado 


* **inputBufferSize**: Tamanho (em bytes) da memória intermédia de entrada 


* **outputBuffer**: Buffer no qual será copiado conteúdo encriptado 


* **outputBufferSize**: Tamanho (em bytes) da memória intermédia de saída 


* **isFinal**: Se a memória intermédia de entrada contém os bytes de texto simples final ou não



  
**Devolve**: Tamanho real (em bytes) de conteúdo encriptado
  
### <a name="decryptbuffer-function"></a>Função de DecryptBuffer
Descriptografar uma memória intermédia.

Parâmetros:  
* **offsetFromStart**: Posição relativa de inputBuffer desde o início do conteúdo encriptado 


* **inputBuffer**: Memória intermédia de conteúdo encriptado que irá ser desencriptado 


* **inputBufferSize**: Tamanho (em bytes) da memória intermédia de entrada 


* **outputBuffer**: Buffer no qual será copiado desencriptado conteúdo 


* **outputBufferSize**: Tamanho (em bytes) da memória intermédia de saída 


* **isFinal**: Se a memória intermédia de entrada contém os bytes encriptados finais ou não



  
**Devolve**: Tamanho real (em bytes) de conteúdo desencriptado
  
### <a name="getprotectedcontentlength-function"></a>Função de GetProtectedContentLength
Calcula o tamanho (em bytes) de conteúdo se fosse sendo criptografados com isso [ProtectionHandler](class_mip_protectionhandler.md).

Parâmetros:  
* **unprotectedLength**: Tamanho (em bytes) de conteúdo não protegido 


* **includesFinalBlock**: Descreve se o conteúdo não protegido em questão inclui o bloco final, ou não. Por exemplo, no modo de encriptação CBC4k, blocos de protegido não final são o mesmo tamanho que blocos não protegidos, mas blocos protegidos finais são maiores do que suas contrapartes não protegidos.



  
**Devolve**: Tamanho (em bytes) de conteúdo protegido
  
### <a name="getblocksize-function"></a>Função de GetBlockSize
Obtém o tamanho do bloco (em bytes) para o modo de cifra utilizado por este [ProtectionHandler](class_mip_protectionhandler.md).

  
**Devolve**: Tamanho do bloco (em bytes)
  
### <a name="getrights-function"></a>Função de GetRights
Obtém os direitos concedidos a/identidade do utilizador associada a este [ProtectionHandler](class_mip_protectionhandler.md).

  
**Devolve**: Direitos concedidos ao utilizador
  
### <a name="accesscheck-function"></a>Função de AccessCheck
Verifica se o manipulador de proteção concede acesso de utilizador especificado certo.

Parâmetros:  
* **right**: Direito para verificar



  
**Devolve**: Se o manipulador de proteção concede acesso de utilizador especificado, à direita ou não
  
### <a name="getissuedto-function"></a>Função de GetIssuedTo
Obtém o utilizador associado ao manipulador de proteção.

  
**Devolve**: Utilizador associado o manipulador de proteção
  
### <a name="getowner-function"></a>Função de GetOwner
Obtém endereço de e-mail do proprietário do conteúdo.

  
**Devolve**: Endereço de e-mail do proprietário do conteúdo
  
### <a name="isissuedtoowner-function"></a>Função de IsIssuedToOwner
Obtém o se o utilizador atual é o proprietário do conteúdo ou não.

  
**Devolve**: Se o utilizador atual é o proprietário do conteúdo ou não
  
### <a name="getprotectiondescriptor-function"></a>Função de GetProtectionDescriptor
Obtém os detalhes de proteção.

  
**Devolve**: Detalhes de proteção
  
### <a name="getcontentid-function"></a>GetContentId function
Obtém o identificador exclusivo para o/conteúdo do documento.

  
**Devolve**: Identificador exclusivo de conteúdo
  
### <a name="doesusedeprecatedalgorithms-function"></a>Função de DoesUseDeprecatedAlgorithms
Obtém se utiliza do manipulador de proteção preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores, ou não.

  
**Devolve**: Se o manipulador de proteção usa criptografia algoritmos preteridos ou não
  
### <a name="isauditedextractallowed-function"></a>Função de IsAuditedExtractAllowed
Obtém se o manipulador de proteção concede o utilizador 'auditado extrair"à direita ou não.

  
**Devolve**: Se o manipulador de proteção concede o utilizador 'auditado extrair"à direita ou não
  
### <a name="getserializedpublishinglicense-function"></a>Função de GetSerializedPublishingLicense
Serializar [ProtectionHandler](class_mip_protectionhandler.md) numa licença de publicação (PL)

  
**Devolve**: Licença serializada de publicação
  
### <a name="getserializedprotectioninfo-function"></a>Função de GetSerializedProtectionInfo
Obtém as informações de proteção.

  
**Devolve**: Informações de proteção serializados
