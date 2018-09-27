# <a name="class-mipprotectionhandler"></a>classe mip::ProtectionHandler 
Executa ações relacionadas com a proteção para uma configuração de proteção específico (ou seja, os usuários, direitos, funções, etc.)
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::shared_ptr<Stream> CreateProtectedStream (const std::shared_ptr<Stream>& backingStream, contentSize de int64_t int64_t contentStartPosition,)  |  Crie um fluxo protegido que lhe irão permitir de encriptação/desencriptação de conteúdo.
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
 bool pública DoesUseDeprecatedAlgorithms()  |  Obtém se ou não utiliza de manipulador de proteção preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores.
 bool pública IsAuditedExtractAllowed()  |  Obtém independentemente do manipulador de proteção concede o direito de 'auditado extrair' de utilizador.
público const Std:: vector < uint8_t > GetSerializedPublishingLicense()  |  Serializar [ProtectionHandler](class_mip_protectionhandler.md) numa licença de publicação (PL)
  
## <a name="members"></a>Membros
  
### <a name="stream"></a>Stream
Crie um fluxo protegido que lhe irão permitir de encriptação/desencriptação de conteúdo.

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


* **isFinal**: se é ou não a memória intermédia de entrada contém os bytes de texto simples final



  
**Devolve**: tamanho real (em bytes) de conteúdo encriptado
  
### <a name="decryptbuffer"></a>DecryptBuffer
Descriptografar uma memória intermédia.

Parâmetros:  
* **offsetFromStart**: posição relativa de inputBuffer desde o início do conteúdo encriptado 


* **inputBuffer**: memória intermédia de conteúdo encriptado que irá ser desencriptado 


* **inputBufferSize**: tamanho (em bytes) da memória intermédia de entrada 


* **outputBuffer**: Buffer no qual será copiado desencriptado conteúdo 


* **outputBufferSize**: tamanho (em bytes) da memória intermédia de saída 


* **isFinal**: se é ou não a memória intermédia de entrada contém os bytes encriptados finais



  
**Devolve**: tamanho real (em bytes) de conteúdo desencriptado
  
### <a name="getprotectedcontentlength"></a>GetProtectedContentLength
Calcula o tamanho (em bytes) de conteúdo se fosse sendo criptografados com isso [ProtectionHandler](class_mip_protectionhandler.md).

Parâmetros:  
* **unprotectedLength**: tamanho (em bytes) de conteúdo não protegido 


* **includesFinalBlock**: descreve se é ou não o conteúdo não protegido em questão inclui o bloco final. Por exemplo, no modo de encriptação CBC4k, blocos de protegido não final são o mesmo tamanho que blocos não protegidos, mas blocos protegidos finais são maiores do que suas contrapartes não protegidos.



  
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



  
**Devolve**: se é ou não o manipulador de proteção concede acesso de utilizador especificado certo
  
### <a name="getissuedto"></a>GetIssuedTo
Obtém o utilizador associado ao manipulador de proteção.

  
**Devolve**: utilizador associado o manipulador de proteção
  
### <a name="getowner"></a>GetOwner
Obtém endereço de e-mail do proprietário do conteúdo.

  
**Devolve**: endereço de E-Mail do proprietário do conteúdo
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Obtém o se o utilizador atual é o proprietário do conteúdo ou não.

  
**Devolve**: se o utilizador atual é o proprietário do conteúdo
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Obtém os detalhes de proteção.

  
**Devolve**: detalhes de proteção
  
### <a name="getcontentid"></a>GetContentId
Obtém o identificador exclusivo para o/conteúdo do documento.

  
**Devolve**: Identificador exclusivo de conteúdo
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Obtém se ou não utiliza de manipulador de proteção preterido algoritmos criptográficos (ECB) para compatibilidade com versões anteriores.

  
**Devolve**: se deve ou não utiliza o manipulador de proteção preterido algoritmos criptográficos
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Obtém independentemente do manipulador de proteção concede o direito de 'auditado extrair' de utilizador.

  
**Devolve**: ou não o manipulador de proteção concede o direito de usuário "auditado extract"
  
### <a name="getserializedpublishinglicense"></a>GetSerializedPublishingLicense
Serializar [ProtectionHandler](class_mip_protectionhandler.md) numa licença de publicação (PL)

  
**Devolve**: licença serializada de publicação