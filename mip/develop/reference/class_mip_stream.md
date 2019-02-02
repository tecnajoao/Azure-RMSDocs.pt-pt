---
title: classe mip::Stream
description: Documenta a classe mip::stream da Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 4289b39ba454b19c6836a7eaccb6333cbb9000b4
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651705"
---
# <a name="class-mipstream"></a>classe mip::Stream 
Uma classe que define a interface entre o SDK de MIP e baseada em fluxo conteúdo de mensagens em fila.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
public int64_t Read(uint8_t* buffer, int64_t bufferLength)  |  Ler num buffer do fluxo.
public int64_t Write(const uint8_t* buffer, int64_t bufferLength)  |  Escreva para o fluxo de uma memória intermédia.
bool pública Flush)  |  esvaziar o fluxo.
Seek void pública (posição int64_t)  |  Posição específica dentro do fluxo de procura.
bool pública CanRead() const  |  Uma verificação se o fluxo pode ser lidos na.
bool pública CanWrite() const  |  Verifique se o fluxo pode ser escrito para.
público int64_t Position()  |  Obter a posição atual dentro do fluxo.
público int64_t Size()  |  Obter o tamanho do conteúdo dentro do fluxo.
Tamanho da void pública (int64_t valor)  |  Defina o tamanho do fluxo.
  
## <a name="members"></a>Membros
  
### <a name="read-function"></a>Função de leitura
Ler num buffer do fluxo.

Parâmetros:  
* **memória intermédia**: aponta para um buffer 


* **bufferLength**: tamanho da memória intermédia. 



  
**Devolve**: Número de bytes lidos.
  
### <a name="write-function"></a>Criar função
Escreva para o fluxo de uma memória intermédia.

Parâmetros:  
* **memória intermédia**: aponta para um buffer 


* **bufferLength**: tamanho da memória intermédia. 



  
**Devolve**: Número de bytes escritos.
  
### <a name="flush-function"></a>Remover função
esvaziar o fluxo.

  
**Devolve**: VERDADEIRO se for bem-sucedido false outra.
  
### <a name="seek-function"></a>Função de procura
Posição específica dentro do fluxo de procura.

Parâmetros:  
* **posição**: Procurar no fluxo.


  
### <a name="canread-function"></a>Função de CanRead
Uma verificação se o fluxo pode ser lidos na.

  
**Devolve**: VERDADEIRO se legível false outra.
  
### <a name="canwrite-function"></a>Função de CanWrite
Verifique se o fluxo pode ser escrito para.

  
**Devolve**: VERDADEIRO se gravável false outra.
  
### <a name="position-function"></a>Função de posição
Obter a posição atual dentro do fluxo.

  
**Devolve**: Posição dentro do fluxo.
  
### <a name="size-function"></a>Função de tamanho
Obter o tamanho do conteúdo dentro do fluxo.

  
**Devolve**: O tamanho de fluxos.
  
### <a name="size-function"></a>Função de tamanho
Defina o tamanho do fluxo.

Parâmetros:  
* **Stream**: tamanho.

