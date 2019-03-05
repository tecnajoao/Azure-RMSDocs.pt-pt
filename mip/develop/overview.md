---
title: Descrição geral - a projeção de informações da Microsoft SDK.
description: Proteção de informações da Microsoft (MIP) é unificação dos serviços de classificação, etiquetagem e proteção da Microsoft, num único administração experiência e o software development kit (SDK).
author: msmbaldwin
ms.service: information-protection
ms.topic: overview
ms.collection: M365-security-compliance
ms.date: 01/18/2019
ms.author: mbaldwin
ms.openlocfilehash: d8efb7ceef890d0c2a0ea72f64d3047e0cfb25a5
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57329612"
---
# <a name="overview"></a>Descrição geral

## <a name="microsoft-information-protection"></a>Microsoft Information Protection

Proteção de informações da Microsoft (MIP) é unificação de classificação da Microsoft, etiquetagem e proteção de serviços:

- Administração unificada é fornecida no Office 365, Azure Information Protection, Windows Information Protection e outros serviços Microsoft. 
- Terceiros pode utilizar o SDK de MIP para integração com aplicativos, usando uma etiquetagem o serviço de esquema e a proteção de dados padrão e consistentes.

* [O que é o Centro de conformidade e de segurança do Office 365?](https://docs.microsoft.com/office365/securitycompliance/)
* [O que é o Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection)
* [Como funciona a proteção no Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

## <a name="microsoft-information-protection-sdk"></a>SDK do Microsoft Information Protection

O SDK de MIP expõe os serviços de etiquetagem e proteção de segurança do Office 365 e do Centro de conformidade, aos serviços e aplicações de terceiros. Os programadores podem utilizar o SDK para criar o suporte nativo para aplicar etiquetas e proteção a ficheiros. Os desenvolvedores podem razão pós-falha quais ações deverão ser executadas quando são detetadas etiquetas específicas e ter em conta encriptada MIP informações. 

As etiquetas e a proteção aplicada a informações do conjunto de serviços da Microsoft são **consistente**. Consistência permite que aplicações e serviços MIP esse suporte ler e escrever as etiquetas de uma maneira comum e previsível.

Casos de utilização do SDK de MIP alto nível incluem:

* Uma aplicação de linha de negócio que aplica etiquetas de classificação aos ficheiros durante a exportação.
* Um aplicativo de design CAD/CAM fornece suporte nativo para etiquetagem Microsoft Information Protection.
* Uma cloud acesso mediador ou dados perda prevenção solução motivos de segurança sobre os dados encriptados com o Azure Information Protection.

Para obter uma lista mais completa, consulte [conceitos de API](concept-apis-use-cases.md).

O SDK de MIP é suportado nas seguintes plataformas:

[!INCLUDE [MIP SDK platform support](../includes/mip-sdk-platform-support.md)]

## <a name="next-steps"></a>Próximos Passos

Agora está pronto para começar a utilizar com o SDK. A primeira coisa que precisará fazer é [conclua os passos de instalação e configuração do SDK de MIP](setup-configure-mip.md). Estes passos irão garantir que a sua subscrição do Office 365 e o computador cliente estão configuradas corretamente.

