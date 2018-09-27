# <a name="class-mipistream"></a>classe mip::IStream 
Interface base para os fluxos protegidos.
Portado do Windows::Storage::Streams::IRandomAccessStream::IRandomAccessStream e Windows::Storage::Streams::FileRandomAccessStream::FileRandomAccessStream. [https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx)[https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.filerandomaccessstream.aspx](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.filerandomaccessstream.aspx)
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
std::shared_future público < int64_t > ReadAsync (uint8_t * pbBuffer, int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Lê um bloco de dados do fluxo de forma assíncrona.
std::shared_future público < int64_t > WriteAsync (const uint8_t * cpbBuffer, int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Escreve um bloco de dados em fluxo de forma assíncrona.
público std::future<bool> FlushAsync (std::launch launchType)  |  Esvaziamentos da memória intermédia de fluxo de saída forma assíncrona.
 público int64_t leitura (uint8_t * pbBuffer, int64_t cbBuffer)  |  Lê um bloco de dados do fluxo de forma síncrona.
 público int64_t escrever (const uint8_t * cpbBuffer, int64_t cbBuffer)  |  Escreve um bloco de dados em fluxo de forma síncrona.
 bool pública Flush)  |  Esvaziamentos da memória intermédia de fluxo de saída forma síncrona.
 público SharedStream clone)  |  Fluxo de clones.
 Seek void pública (uint64_t u64Position)  |  Procura uma posição dentro do fluxo.
 bool pública CanRead() const  |  Obtém se ou não pode ser ler o fluxo.
 bool pública CanWrite() const  |  Obtém se ou não pode ser escrito stream.
 público uint64_t Position()  |  Obtém a posição atual do fluxo de início (em bytes)
 público uint64_t Size()  |  Obtém o tamanho da transmissão em fluxo (em bytes)
 Tamanho da void pública (uint64_t u64Value)  |  Define o tamanho da transmissão em fluxo (em bytes)
público virtual Std:: vector < uint8_t > leitura (uint64_t u64size)  |  Lê um bloco de dados do fluxo de forma síncrona.
  
## <a name="members"></a>Membros
  
### <a name="readasync"></a>ReadAsync
Lê um bloco de dados do fluxo de forma assíncrona.

Parâmetros:  
* **pbBuffer**: Buffer no qual o fluxo deve ser lida 


* **cbBuffer**: tamanho da memória intermédia 


* **cbOffset**: deslocamento de início do fluxo de entrada onde deve começar a ler 


* **launchType**: tipo de lançamento de Async



  
**Devolve**: Async futura que contém o número real de bytes lidos buffer Certifique-se de que existe até que o resultado é retreived de std::future
  
### <a name="writeasync"></a>WriteAsync
Escreve um bloco de dados em fluxo de forma assíncrona.

Parâmetros:  
* **cpbBuffer**: memória intermédia de dados para escrever 


* **cbBuffer**: tamanho da memória intermédia 


* **cbOffset**: deslocamento de início do fluxo de saída para onde deve começar a escrever 


* **launchType**: tipo de lançamento de Async



  
**Devolve**: Async futura que contém o número real de bytes escritos buffer Certifique-se de que existe até que o resultado é retreived de std::future
  
### <a name="flushasync"></a>FlushAsync
Esvaziamentos da memória intermédia de fluxo de saída forma assíncrona.

Parâmetros:  
* **launchType**: tipo de lançamento de Async



  
**Devolve**: Async futuras que contêm quer ou não a remoção da cache foi concluída com êxito
  
### <a name="read"></a>Ler
Lê um bloco de dados do fluxo de forma síncrona.

Parâmetros:  
* **pbBuffer**: Buffer no qual o fluxo deve ser lida 


* **cbBuffer**: tamanho da memória intermédia



  
**Devolve**: número real de bytes lidos
  
### <a name="write"></a>Escrever
Escreve um bloco de dados em fluxo de forma síncrona.

Parâmetros:  
* **cpbBuffer**: memória intermédia de dados para escrever 


* **cbBuffer**: tamanho da memória intermédia



  
**Devolve**: número real de bytes escritos
  
### <a name="flush"></a>Remoção da cache
Esvaziamentos da memória intermédia de fluxo de saída forma síncrona.

  
**Devolve**: se é ou não a remoção da cache foi concluída com êxito
  
### <a name="sharedstream"></a>SharedStream
Fluxo de clones.

  
**Devolve**: stream clonado
  
### <a name="seek"></a>Procurar
Procura uma posição dentro do fluxo.

Parâmetros:  
* **u64Position**: deslocamento de Byte de início da transmissão em fluxo


  
### <a name="canread"></a>CanRead
Obtém se ou não pode ser ler o fluxo.

  
**Devolve**: se deve ou não pode ser lidos de fluxo
  
### <a name="canwrite"></a>CanWrite
Obtém se ou não pode ser escrito stream.

  
**Devolve**: se deve ou não pode ser escrito de fluxo
  
### <a name="position"></a>Posição
Obtém a posição atual do fluxo de início (em bytes)

  
**Devolve**: positition atual do fluxo de início (em bytes)
  
### <a name="size"></a>Size
Obtém o tamanho da transmissão em fluxo (em bytes)

  
**Devolve**: tamanho da transmissão em fluxo (em bytes)
  
### <a name="size"></a>Size
Define o tamanho da transmissão em fluxo (em bytes)

Parâmetros:  
* **u64Value**: tamanho da transmissão em fluxo (em bytes)


  
### <a name="read"></a>Ler
Lê um bloco de dados do fluxo de forma síncrona.

Parâmetros:  
* **u64size**: tamanho dos dados para ler (em bytes)



  
**Devolve**: Vetor real de ler dados