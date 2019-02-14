---
title: SDK do Microsoft Information Protection C# descrição geral de Wrapper
description: Uma visão geral sobre como começar com o wrapper MIP SDK .NET e as diferenças entre o .NET wrapper e C++ SDK.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 01/04/2019
ms.author: tommos
ms.openlocfilehash: 6b2f26a61cd491574fd9f4a1e74fbfab4752257a
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252321"
---
# <a name="getting-started-with-the-microsoft-information-protection-net-wrapper"></a>Guia de introdução o Wrapper de .NET de proteção de informações da Microsoft

O Wrapper de .NET SDK de proteção de informações de Microsoft permite aos programadores integrar a experiência do Microsoft Information Protection para seus próprios serviços e aplicações. O SDK classificação, etiquetagem e a ajuda de funcionalidades de proteção para garantir que informações são classificadas, o nome e protegidos, independentemente de onde ele viaja. 

O invólucro gerenciado e todas as dependências podem ser instaladas por meio do NuGet no Visual Studio.

## <a name="supported-platforms"></a>Plataformas Suportadas

O Wrapper de .NET de proteção de informações do Microsoft é suportado nas seguintes plataformas .NET:

* .NET Standard 2.0
* .NET 4.0

## <a name="installing-the-package"></a>Instalação do pacote

Na consola do Gestor de pacotes no Visual Studio 2017, instale o pacote ao executar:

`install-package Microsoft.InformationProtection.File`

Não existem pacotes adicionais são necessários. Todas as bibliotecas de terceiros estão incluídas e irão copiar para a pasta de saída na compilação.

## <a name="wrapper-details"></a>Detalhes de wrapper

O wrapper .NET é uma [SWIG](https://swig.org/) invólucro gerenciado gerado. O wrapper utiliza compiladas bibliotecas C++ do SDK do Microsoft Information Protection. Essas DLLs são as mesmas DLLs que estão incluídas com a versão de C++ do SDK.

## <a name="concept-overlap"></a>Sobreposição de conceito

Existem algumas diferenças fundamentais entre a versão de C++ do SDK e o invólucro gerenciado.

* O wrapper .NET não requer a utilização de observadores de operações assíncronas. As operações assíncronas são implementadas através da [padrão assíncrono baseado em tarefa](https://docs.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap).
* O wrapper .NET requer os delegados que fazem parte do C++ SDK: AuthDelegate e ConsentDelegate. Esses delegados são implementados por meio das interfaces `IAuthDelegate` e `IConsentDelegate`

## <a name="next-steps"></a>Próximos Passos

Em seguida, reveja [início rápido – inicialização para o Microsoft Information Protection (MIP) SDK C# ](quick-app-initialization-csharp.md) para começar a utilizar na criação de um aplicativo de console básico, MIP habilitado.
