# <a name="class-mipstream"></a>classe mip::Stream 
Uma classe que define a interface entre o mip sdk e o fluxo com base em conteúdo.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público int64_t leitura (uint8_t * buffer, int64_t bufferLength)  |  Ler num buffer do fluxo.
 público int64_t escrever (const uint8_t * buffer, int64_t bufferLength)  |  Escreva para o fluxo de uma memória intermédia.
 bool pública Flush)  |  esvaziar o fluxo.
 Seek void pública (posição uint64_t)  |  Posição específica dentro do fluxo de procura.
 bool pública CanRead() const  |  Verifique se o fluxo é legível.
 bool pública CanWrite() const  |  Verifique se o fluxo é gravável.
 público uint64_t Position()  |  Obter a posição atual dentro do fluxo.
 público uint64_t Size()  |  Obter o tamanho do conteúdo dentro do fluxo.
 Tamanho da void pública (uint64_t valor)  |  Defina o tamanho do fluxo.
  
## <a name="members"></a>Membros
  
### <a name="read"></a>Ler
Ler num buffer do fluxo.

Parâmetros:  
* **memória intermédia**: aponta para um buffer 


* **bufferLength**: tamanho da memória intermédia. 



  
**Devolve**: número de bytes realmente lidos.
  
### <a name="write"></a>Escrever
Escreva para o fluxo de uma memória intermédia.

Parâmetros:  
* **memória intermédia**: aponta para um buffer 


* **bufferLength**: tamanho da memória intermédia. 



  
**Devolve**: número de bytes gravados.
  
### <a name="flush"></a>Remoção da cache
esvaziar o fluxo.

  
**Devolve**: false outra VERDADEIRO se for bem sucedida.
  
### <a name="seek"></a>Procurar
Posição específica dentro do fluxo de procura.

Parâmetros:  
* **posição**: Procurar no fluxo.


  
### <a name="canread"></a>CanRead
Verifique se o fluxo é legível.

  
**Devolve**: false outra True se legível.
  
### <a name="canwrite"></a>CanWrite
Verifique se o fluxo é gravável.

  
**Devolve**: false outra True se gravável.
  
### <a name="position"></a>Posição
Obter a posição atual dentro do fluxo.

  
**Devolve**: posição dentro do fluxo.
  
### <a name="size"></a>Size
Obter o tamanho do conteúdo dentro do fluxo.

  
**Devolve**: O tamanho de fluxos.
  
### <a name="size"></a>Size
Defina o tamanho do fluxo.

Parâmetros:  
* **Stream**: tamanho.

