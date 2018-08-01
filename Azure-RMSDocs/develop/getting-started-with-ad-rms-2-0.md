---
title: Introdução | Azure RMS
description: A plataforma SDK RMS 2.1 permite aos programadores criarem aplicações que tiram partido da proteção de informações do RMS.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 728113C9-FCF9-4280-BE1D-6AF5C15E449E
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: d62621cca53132a872958a38365a621c7bb8ece4
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39370732"
---
# <a name="getting-started"></a>Introdução

A plataforma do SDK Rights Management Services 2.1 permite aos programadores criar aplicações que tiram partido da proteção de informações do RMS através de um RMS Server ou do Azure RMS. A plataforma processa práticas de segurança complexas tais como a gestão de chaves, o processamento de encriptação e desencriptação e oferece uma API simplificada para a programação de aplicações fácil.

## <a name="get-started-with-rms-sdk-21"></a>Introdução ao SDK RMS 2.1

Este tópico descreve o processo de configuração e execução da aplicação com permissão para direitos num ambiente de teste. Os tópicos seguintes analisam como configurar o ambiente de desenvolvimento, sendo listados pela ordem de execução das tarefas.

## <a name="in-this-sections"></a>Nestas secções

| Tópico | Descrição |
|-------|-------------|
| [Notas de Versão](release-notes-rtm.md) | Este tópico contém informações importantes sobre isto e sobre versões anteriores do SDK RMS 2.1.|
| [Instalar o SDK](install-the-rms-sdk.md) | Este tópico descreve o processo de instalação das ferramentas de programação.|
| [Configurar o Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md) | Este tópico contém instruções sobre como configurar um projeto do Visual Studio para utilizar o SDK RMS 2.1.|
| [Desenvolver a sua aplicação](developing-your-application.md) | Este tópico contém documentação de orientação essencial sobre os aspetos base de uma aplicação com permissão para RMS e pode servir de ponto de partida para o desenvolvimento da sua aplicação.|
| [Testar a sua aplicação](how-to-set-up-your-test-environment.md) |Este tópico contém instruções sobre como configurar o teste de aplicações.|
| [Implementar em produção](deploying-your-application.md) |Este tópico descreve as opções de implementação da sua aplicação com permissão para direitos.|


Tente utilizar o SDK RMS 2.1 ao seguir as orientações nos seguintes tópicos:

- [Instalar o SDK](install-the-rms-sdk.md)
- [Configurar o Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)
- [Desenvolver a sua aplicação](developing-your-application.md)
- [Testar a sua aplicação](how-to-set-up-your-test-environment.md)
- [Implementar em produção](deploying-your-application.md)

### <a name="why-use-rms-sdk-21-for-protecting-your-content"></a>Por que motivo deve utilizar o SDK RMS 2.1 para proteger o seu conteúdo

Para programadores que pretendem adicionar o suporte do RMS às suas aplicações novas e existentes, o SDK RMS 2.1 facilita:

-   Criar aplicações geríveis, compatíveis, robustas e com suporte para RMS.
-   Encriptar dados do utilizador de forma persistente. Os dados permanecem encriptados independentemente do ambiente, do dispositivo ou do sistema operativo.
-   Impor um conjunto completo de restrições de utilização, tais como impedir as capturas de ecrã dos dados confidenciais.
-   Apoiar políticas de proteção geridas por empresas.
-   Suportar novos mecanismos de autenticação e algoritmos de encriptação à medida que ficam disponíveis.

O SDK RMS 2.1 suporta uma gama de plataformas de clientes e servidores importantes. Para obter mais informações, consulte [Plataformas suportadas](supported-platforms.md).

## <a name="core-principles"></a>Princípios fundamentais

**Simplicidade** – foram analisados padrões de comentários e de utilização do SDK AD RMS 1.0 e esses dados foram utilizados para simplificar ou automatizar as tarefas de programação mais difíceis. Normalmente, as aplicações do RMS criadas utilizando o SDK RMS 2.1 necessitam de 5 a 10 vezes menos linhas de código do RMS do que as aplicações do RMS escritas utilizando o SDK AD RMS 1.0.
**Escrita única** – as aplicações do SDK RMS 2.1 não necessitam de uma alteração de código ou de uma recompilação para funcionar com as funcionalidades do RMS mais recentes. As novas funcionalidades do RMS ficarão disponíveis na sua aplicação existente conforme forem adicionadas ao servidor RMS.
**Consistência** – o SDK RMS 2.1 faz com que seja mais fácil escrever as aplicações que respeitam de forma consistente diferentes configurações do RMS. Além disso, reduz significativamente a quantidade da interface de utilizador do RMS que o programador da aplicação precisa para criar, incentivando um aspeto e funcionalidade consistentes, e reduzindo a necessidade da educação do utilizador.

## <a name="related-topics"></a>Tópicos relacionados

* [Guia para Programadores do RMS](developers-guide.md)
* [Área para Programadores do AD RMS](http://blogs.msdn.com/b/rms/)
