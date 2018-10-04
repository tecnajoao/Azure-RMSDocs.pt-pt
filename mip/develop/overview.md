---
title: Descrição geral - a projeção de informações da Microsoft SDK.
description: Proteção de informações da Microsoft (MIP) é unificação dos serviços de classificação, etiquetagem e proteção da Microsoft, num único administração experiência e o software development kit (SDK).
author: BryanLa
ms.service: information-protection
ms.topic: overview
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 775ae3d524947c8300de0e011b92c2cad106905a
ms.sourcegitcommit: d677088db8588fb2cc4a5d7dd296e76d0d9a2e9c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251731"
---
# <a name="overview"></a>Descrição geral

## <a name="microsoft-information-protection"></a>Microsoft Information Protection

Proteção de informações da Microsoft (MIP) é unificação dos serviços de classificação, etiquetagem e proteção da Microsoft, num único administração experiência e o software development kit (SDK). Administração unificada é fornecida no Office 365, Azure Information Protection, Windows Information Protection e outros serviços Microsoft. Terceiros pode utilizar o SDK para integrar com aplicações, utilizando uma etiquetagem o serviço de esquema e a proteção de dados padrão e consistentes.

* [O que é o Centro de conformidade e de segurança do Office 365?](https://docs.microsoft.com/office365/securitycompliance/)
* [O que é o Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection)
* [Como funciona a proteção no Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

## <a name="microsoft-information-protection-sdk"></a>SDK do Microsoft Information Protection

O SDK de MIP expõe os serviços de etiquetagem e proteção de segurança do Office 365 e do Centro de conformidade aos serviços e aplicações de terceiros. Os programadores podem utilizar o SDK para criar o suporte nativo para aplicar etiquetas e proteção a ficheiros. Os desenvolvedores podem razão pós-falha quais ações deverão ser executadas quando são detetadas etiquetas específicas e ter em conta encriptada MIP informações. 

As etiquetas e a proteção aplicada a informações do conjunto de serviços da Microsoft são **consistente**. Consistência permite que aplicações e serviços MIP esse suporte ler e escrever as etiquetas de uma maneira comum e previsível.

Casos de utilização do SDK de MIP alto nível incluem:

* Uma aplicação de linha de negócio que aplica etiquetas de classificação aos ficheiros durante a exportação.
* Um aplicativo de design CAD/CAM fornece suporte nativo para etiquetagem Microsoft Information Protection.
* Uma cloud acesso mediador ou dados perda prevenção solução motivos de segurança sobre os dados encriptados com o Azure Information Protection.

Para obter uma lista mais completa, consulte [conceitos de API](concept-apis-use-cases.md).

## <a name="next-steps"></a>Passos Seguintes

Agora está pronto para começar a utilizar com o SDK. A primeira coisa que precisará fazer, é [conclua os passos de instalação e configuração do SDK de MIP](setup-configure-mip.md), para se certificar de que a subscrição do Office 365 e a máquina de cliente estão configuradas corretamente.

