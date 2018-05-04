# <a name="class-mipcustomprotectedstream"></a>classe mip::CustomProtectedStream 
Encapsula num wrapper uma transmissão em fluxo para fornecer a encriptação transparente e desencriptação na leitura e escrita.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
std::shared_future pública < int64_t > ReadAsync (uint8_t * pbBuffer int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Lê um bloco de dados a partir do fluxo no modo assíncrono.
std::shared_future pública < int64_t > WriteAsync (const uint8_t * cpbBuffer int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Escreve um bloco de dados no fluxo no modo assíncrono.
std::future pública<bool> FlushAsync (std::launch launchType)  |  Esvaziamentos da memória intermédia de fluxo de saída no modo assíncrono.
pública int64_t leitura (uint8_t * pbBuffer, int64_t cbBuffer)  |  Lê um bloco de dados a partir do fluxo de forma síncrona.
inline pública virtual std::vector < uint8_t > leitura (uint64_t u64size)  |  Lê um bloco de dados a partir do fluxo de forma síncrona.
int64_t pública escrever (const uint8_t * cpbBuffer, int64_t cbBuffer)  |  Escreve um bloco de dados na sequência de forma síncrona.
bool pública Flush()  |  Esvaziamentos da memória intermédia de fluxo de saída forma síncrona.
pública SharedStream clone)  |  Fluxo de clones.
Procura void pública (uint64_t u64Position)  |  Procura uma posição na sequência.
bool pública CanRead() const  |  Obtém ou não pode ser lidos fluxo.
bool pública CanWrite() const  |  Obtém ou não pode escrever no fluxo.
pública uint64_t Position()  |  Obtém a posição atual do fluxo de início (em bytes)
pública uint64_t Size()  |  Obtém o tamanho da transmissão em fluxo (em bytes)
Tamanho void pública (uint64_t u64Value)  |  Define o tamanho da transmissão em fluxo (em bytes)
  
## <a name="members"></a>Membros
  
### <a name="readasync"></a>ReadAsync
Lê um bloco de dados a partir do fluxo no modo assíncrono.
  
#### <a name="parameters"></a>Parâmetros
* memória intermédia pbBuffer no qual deve ser lida fluxo 
* cbBuffer tamanho da memória intermédia 
* cbOffset deslocamento de início do fluxo de entrada onde deve começar a ler 
* launchType Async tipo de iniciação
  
#### <a name="returns"></a>Devolve
Async futura que contém o número real de bytes lidos de memória intermédia de Certifique-se de que existe até que o resultado é retreived de std::future
  
### <a name="writeasync"></a>WriteAsync
Escreve um bloco de dados no fluxo no modo assíncrono.
  
#### <a name="parameters"></a>Parâmetros
* cpbBuffer da memória intermédia de dados a escrever 
* cbBuffer tamanho da memória intermédia 
* cbOffset deslocamento de início do fluxo de saída para onde deve começar a escrever 
* launchType Async tipo de iniciação
  
#### <a name="returns"></a>Devolve
Async futura que contém o número real de bytes escritos memória intermédia de Certifique-se de que existe até que o resultado é retreived de std::future
  
### <a name="flushasync"></a>FlushAsync
Esvaziamentos da memória intermédia de fluxo de saída no modo assíncrono.
  
#### <a name="parameters"></a>Parâmetros
* launchType Async tipo de iniciação
  
#### <a name="returns"></a>Devolve
Async futura que contém se ou não esvaziamento foi concluída com êxito
  
### <a name="read"></a>Ler
Lê um bloco de dados a partir do fluxo de forma síncrona.
  
#### <a name="parameters"></a>Parâmetros
* memória intermédia pbBuffer no qual deve ser lida fluxo 
* cbBuffer tamanho da memória intermédia
  
#### <a name="returns"></a>Devolve
Número atual de bytes lidos
  
### <a name="read"></a>Ler
Lê um bloco de dados a partir do fluxo de forma síncrona.
  
#### <a name="parameters"></a>Parâmetros
* u64size tamanho dos dados para ler (em bytes)
  
#### <a name="returns"></a>Devolve
Vetor de dados reais de leitura
  
### <a name="write"></a>Escrever
Escreve um bloco de dados na sequência de forma síncrona.
  
#### <a name="parameters"></a>Parâmetros
* cpbBuffer da memória intermédia de dados a escrever 
* cbBuffer tamanho da memória intermédia
  
#### <a name="returns"></a>Devolve
Número atual de bytes escritos
  
### <a name="flush"></a>Remover da cache
Esvaziamentos da memória intermédia de fluxo de saída forma síncrona.
  
#### <a name="returns"></a>Devolve
Se pretende ou não esvaziamento foi concluída com êxito
  
### <a name="sharedstream"></a>SharedStream
Fluxo de clones.
  
#### <a name="returns"></a>Devolve
Fluxo clonado
  
### <a name="seek"></a>Pesquisa
Procura uma posição na sequência.
  
#### <a name="parameters"></a>Parâmetros
* deslocamento de Byte u64Position desde o início do fluxo
  
### <a name="canread"></a>CanRead
Obtém ou não pode ser lidos fluxo.
  
#### <a name="returns"></a>Devolve
Se pretende ou não pode ser lidos fluxo
  
### <a name="canwrite"></a>CanWrite
Obtém ou não pode escrever no fluxo.
  
#### <a name="returns"></a>Devolve
Se pretende ou não pode ser escrever no fluxo
  
### <a name="position"></a>Posição
Obtém a posição atual do fluxo de início (em bytes)
  
#### <a name="returns"></a>Devolve
Positition atual do fluxo de início (em bytes)
  
### <a name="size"></a>Size
Obtém o tamanho da transmissão em fluxo (em bytes)
  
#### <a name="returns"></a>Devolve
Tamanho da transmissão em fluxo (em bytes)
  
### <a name="size"></a>Size
Define o tamanho da transmissão em fluxo (em bytes)
  
#### <a name="parameters"></a>Parâmetros
* u64Value tamanho da transmissão em fluxo (em bytes)