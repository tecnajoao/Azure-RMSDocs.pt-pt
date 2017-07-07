---
title: "Testar a sua aplicação | Azure RMS"
description: "Instruções sobre como configurar a sua aplicação para fins de teste."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: b88fa08e17ab2fdc78809c24eb665a2cf44fa3ec
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="testing-your-application"></a>Testar a sua aplicação

Este tópico contém instruções sobre como configurar o teste de aplicações.

## <a name="instructions"></a>Instruções

### <a name="step-1-setup-for-testing"></a>Passo 1: Configuração para teste

Pode testar com o Azure RMS ou um servidor RMS em execução no Windows Server. Sugerimos que inicie os testes no Azure RMS e, em seguida, se for necessário para a implementação, efetue o teste com o RMS Server.

1. Para fins de teste com o Azure RMS, consulte o artigo [Procedimentos: utilizar a autenticação ADAL](how-to-use-adal-authentication.md).
2. Para fins de teste com o RMS Server, consulte o artigo [Procedimentos: instalar e configurar um servidor RMS](how-to-install-and-configure-an-rms-server.md).
3. O seguinte procedimento descreve como instalar o runtime de programador.

   Tem de ter o Rights Management Service Client 2.1 instalado no computador no qual irá testar a aplicação.
   - Se testar a aplicação num computador diferente do seu computador de desenvolvimento, pode instalar o RMS Client 2.1 nesse computador a partir da [página de transferência do AD RMS Client](http://www.microsoft.com/en-us/download/details.aspx?id=38396).
   - Se testar a aplicação no seu computador de desenvolvimento, deve ter previamente instalado o SDK Rights Management Services 2.1. O RMS Client 2.1 terá já sido instalado silenciosamente.

    Para obter informações sobre como instalar o SDK RMS 2.1, consulte [Instalar o SDK](install-the-rms-sdk.md).

## <a name="remarks"></a>Observações

As orientações neste tópico não são abrangentes. Para obter informações detalhadas sobre como configurar o RMS Client 2.1, consulte as [Notas de Implementação do RMS Client 2.1](https://technet.microsoft.com/en-us/library/jj159267(WS.10).aspx).

### <a name="related-topics"></a>Tópicos relacionados

* [Procedimentos: instalar e configurar um servidor RMS](how-to-install-and-configure-an-rms-server.md)
* [Procedimentos: utilizar a autenticação ADAL](how-to-use-adal-authentication.md)
* [Instalar o SDK](install-the-rms-sdk.md)
* [Notas de Implementação do RMS Client 2.1](https://technet.microsoft.com/en-us/library/jj159267(WS.10).aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]