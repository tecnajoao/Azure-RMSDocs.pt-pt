---
title: Testar a sua aplicação | Azure RMS
description: Instruções sobre como configurar a sua aplicação para fins de teste.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8f99338daf79b2a59ddacb914d424da81d2b630b
ms.sourcegitcommit: 8e622a93ff8d07a180e3be6e8b14748354e640bd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/29/2018
ms.locfileid: "30258974"
---
# <a name="testing-your-application"></a>Testar a sua aplicação

Aqui, irá aprender a preparar o teste de aplicações.

## <a name="instructions"></a>Instruções

Pode testar com o Azure RMS ou um servidor RMS em execução no Windows Server.  Começar a testar com o Azure RMS e testar com o RMS Server (se for necessário para a sua implementação).

- Para fins de teste com o Azure RMS, consulte o artigo [Procedimentos: utilizar a autenticação ADAL](how-to-use-adal-authentication.md).
- Para fins de teste com o RMS Server, consulte o artigo [Procedimentos: instalar e configurar um servidor RMS](how-to-install-and-configure-an-rms-server.md).
- Para instalar o runtime de programador:

   Tem de ter o Rights Management Service Client 2.1 instalado no computador no qual irá testar a aplicação.
   - Para testar a aplicação num computador diferente do seu computador de desenvolvimento, instale o RMS Client 2.1 nesse computador a partir de [página de transferência do cliente de AD RMS](http://www.microsoft.com/en-us/download/details.aspx?id=38396).
   - O computador de desenvolvimento deve ter o SDK Rights Management Services 2.1, que foi anteriormente instalado.

   Para ajudar a instalar o SDK RMS 2.1, consulte [instalar o SDK](install-the-rms-sdk.md).

## <a name="remarks"></a>Observações

Esta orientação não é abrangente. Para saber como configurar o RMS Client 2.1, consulte [notas de implementação do RMS Client 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx).

## <a name="related-topics"></a>Tópicos relacionados

* [Procedimentos: instalar e configurar um servidor RMS](how-to-install-and-configure-an-rms-server.md)
* [Procedimentos: utilizar a autenticação ADAL](how-to-use-adal-authentication.md)
* [Instalar o SDK](install-the-rms-sdk.md)
* [Notas de Implementação do RMS Client 2.1](https://technet.microsoft.com/library/jj159267(WS.10).aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
