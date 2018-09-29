---
title: classe mip Stream
description: Referência para a classe mip Stream
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e6296c5e15590741e008979dcf12373ff5fcdf00
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445228"
---
# <a name="class-mipstream"></a>classe mip::Stream 
Uma classe que define a interface entre o SDK de MIP e baseada em fluxo conteúdo de mensagens em fila.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público int64_t leitura (uint8_t * buffer, int64_t bufferLength)  |  Ler num buffer do fluxo.
 público int64_t escrever (const uint8_t * buffer, int64_t bufferLength)  |  Escreva para o fluxo de uma memória intermédia.
 bool pública Flush)  |  esvaziar o fluxo.
 Seek void pública (posição int64_t)  |  Posição específica dentro do fluxo de procura.
 bool pública CanRead() const  |  Uma verificação se o fluxo pode ser lidos na.
 bool pública CanWrite() const  |  Verifique se o fluxo pode ser escrito para.
 público int64_t Position()  |  Obter a posição atual dentro do fluxo.
 público int64_t Size()  |  Obter o tamanho do conteúdo dentro do fluxo.
 Tamanho da void pública (int64_t valor)  |  Defina o tamanho do fluxo.
  
## <a name="members"></a>Membros
  
### <a name="read"></a>Ler
Ler num buffer do fluxo.

Parâmetros:  
* **memória intermédia**: aponta para um buffer 


* **bufferLength**: tamanho da memória intermédia. 



  
**Devolve**: número de bytes lidos.
  
### <a name="write"></a>Escrever
Escreva para o fluxo de uma memória intermédia.

Parâmetros:  
* **memória intermédia**: aponta para um buffer 


* **bufferLength**: tamanho da memória intermédia. 



  
**Devolve**: número de bytes escritos.
  
### <a name="flush"></a>Remoção da cache
esvaziar o fluxo.

  
**Devolve**: false outra VERDADEIRO se for bem sucedida.
  
### <a name="seek"></a>Procurar
Posição específica dentro do fluxo de procura.

Parâmetros:  
* **posição**: Procurar no fluxo.


  
### <a name="canread"></a>CanRead
Uma verificação se o fluxo pode ser lidos na.

  
**Devolve**: false outra True se legível.
  
### <a name="canwrite"></a>CanWrite
Verifique se o fluxo pode ser escrito para.

  
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

