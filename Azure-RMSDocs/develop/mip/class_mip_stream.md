# <a name="class-mipstream"></a>classe mip::Stream 
Uma classe que define a interface entre o sdk de mip e fluxo com base no conteúdo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública int64_t leitura (uint8_t * da memória intermédia, int64_t bufferLength)  |  Leitura para uma memória intermédia do fluxo.
int64_t pública escrever (const uint8_t * memória intermédia, int64_t bufferLength)  |  Escreva ino o fluxo a partir de uma memória intermédia.
bool pública Flush()  |  remover o fluxo da cache.
Procura void pública (uint64_t posição)  |  Posição específica dentro do fluxo de procura.
bool pública CanRead() const  |  Verifique se a sequência é legível.
bool pública CanWrite() const  |  Verifique se o fluxo é passível de escrita.
pública uint64_t Position()  |  Obter a posição atual no fluxo.
pública uint64_t Size()  |  Obter o tamanho do conteúdo na sequência.
Tamanho void pública (uint64_t valor)  |  Defina o tamanho da sequência.
std::shared_ptr pública<Stream> clone)  |  O fluxo de clone.
  
## <a name="members"></a>Membros
  
### <a name="read"></a>Ler
Leitura para uma memória intermédia do fluxo.
  
#### <a name="parameters"></a>Parâmetros
* ponteiro de memória intermédia para uma memória intermédia 
* tamanho de memória intermédia bufferLength. 
  
#### <a name="returns"></a>Devolve
número de bytes, na verdade, de leitura.
  
### <a name="write"></a>Escrever
Escreva ino o fluxo a partir de uma memória intermédia.
  
#### <a name="parameters"></a>Parâmetros
* ponteiro de memória intermédia para uma memória intermédia 
* tamanho de memória intermédia bufferLength. 
  
#### <a name="returns"></a>Devolve
número de bytes, na verdade, de leitura.
  
### <a name="flush"></a>Remover da cache
remover o fluxo da cache.
  
#### <a name="returns"></a>Devolve
VERDADEIRO se tiver êxito false pessoa.
  
### <a name="seek"></a>Pesquisa
Posição específica dentro do fluxo de procura.
  
#### <a name="parameters"></a>Parâmetros
* posição procurar o ressarcimento no stream.
  
### <a name="canread"></a>CanRead
Verifique se a sequência é legível.
  
#### <a name="returns"></a>Devolve
TRUE se legível false pessoa.
  
### <a name="canwrite"></a>CanWrite
Verifique se o fluxo é passível de escrita.
  
#### <a name="returns"></a>Devolve
TRUE se gravável false pessoa.
  
### <a name="position"></a>Posição
Obter a posição atual no fluxo.
  
#### <a name="returns"></a>Devolve
posição dentro do fluxo.
  
### <a name="size"></a>Size
Obter o tamanho do conteúdo na sequência.
  
#### <a name="returns"></a>Devolve
o tamanho da sequência.
  
### <a name="size"></a>Size
Defina o tamanho da sequência.
  
#### <a name="parameters"></a>Parâmetros
* tamanho do Stream.
  
### <a name="stream"></a>Fluxo
O fluxo de clone.
  
#### <a name="returns"></a>Devolve
novo fluxo.