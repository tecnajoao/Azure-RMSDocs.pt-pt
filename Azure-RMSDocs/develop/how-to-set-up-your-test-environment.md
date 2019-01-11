---
title: Testar a sua aplicação | Azure RMS
description: Instruções sobre como configurar a sua aplicação para fins de teste.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 323816b04f59d8a18015157052f097531b34cf03
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071782"
---
# <a name="testing-your-application"></a>Testar a sua aplicação

Aqui, irá aprender a se preparar para teste de aplicativos.

## <a name="instructions"></a>Instruções

Pode testar com o Azure RMS ou um servidor RMS em execução no Windows Server.  Iniciar os testes com o Azure RMS e teste com o RMS Server (se for necessário para a sua implementação).

- Para fins de teste com o Azure RMS, consulte o artigo [Procedimentos: utilizar a autenticação ADAL](how-to-use-adal-authentication.md).
- Para fins de teste com o RMS Server, consulte o artigo [Procedimentos: instalar e configurar um servidor RMS](how-to-install-and-configure-an-rms-server.md).
- Para instalar o runtime de programador:

   Tem de ter o Rights Management Service Client 2.1 instalado no computador no qual irá testar a aplicação.
   - Para testar a aplicação num computador diferente do seu computador de desenvolvimento, instalar o RMS Client 2.1 nesse computador a partir da [página de transferência do cliente de AD RMS](https://www.microsoft.com/download/details.aspx?id=38396).
   - O computador de desenvolvimento deve ter o Rights Management Services SDK 2.1, que foi anteriormente instalado.

   Para ajudar a instalar o SDK RMS 2.1, consulte [instalar o SDK](install-the-rms-sdk.md).

## <a name="remarks"></a>Observações

Esta orientação não é abrangente. Para saber como configurar o RMS Client 2.1, consulte [notas de implementação do RMS Client 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx).

## <a name="related-topics"></a>Tópicos relacionados

* [Procedimentos: instalar e configurar um servidor RMS](how-to-install-and-configure-an-rms-server.md)
* [Procedimentos: utilizar a autenticação ADAL](how-to-use-adal-authentication.md)
* [Instalar o SDK](install-the-rms-sdk.md)
* [Notas de Implementação do RMS Client 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx)

