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

Parâmetros:  
* **memória intermédia**: ponteiro numa memória intermédia 


* **bufferLength**: memória intermédia de tamanho. 



  
**Devolve**: número de bytes lidos realmente.
  
### <a name="write"></a>Escrever
Escreva ino o fluxo a partir de uma memória intermédia.

Parâmetros:  
* **memória intermédia**: ponteiro numa memória intermédia 


* **bufferLength**: memória intermédia de tamanho. 



  
**Devolve**: número de bytes lidos realmente.
  
### <a name="flush"></a>Remover da cache
remover o fluxo da cache.

  
**Devolve**: false pessoa True se com êxito.
  
### <a name="seek"></a>Pesquisa
Posição específica dentro do fluxo de procura.

Parâmetros:  
* **posição**: para procurar o ressarcimento no stream.


  
### <a name="canread"></a>CanRead
Verifique se a sequência é legível.

  
**Devolve**: True se legível false pessoa.
  
### <a name="canwrite"></a>CanWrite
Verifique se o fluxo é passível de escrita.

  
**Devolve**: True se gravável false pessoa.
  
### <a name="position"></a>Posição
Obter a posição atual no fluxo.

  
**Devolve**: posição dentro do fluxo.
  
### <a name="size"></a>Size
Obter o tamanho do conteúdo na sequência.

  
**Devolve**: O tamanho da sequência.
  
### <a name="size"></a>Size
Defina o tamanho da sequência.

Parâmetros:  
* **fluxo**: tamanho.


  
### <a name="stream"></a>Fluxo
O fluxo de clone.

  
**Devolve**: novo fluxo.