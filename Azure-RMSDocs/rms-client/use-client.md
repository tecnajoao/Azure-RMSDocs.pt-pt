---
title: O cliente do Azure Information Protection
description: O Microsoft Azure Information Protection fornece uma solução de servidor cliente que ajuda a proteger os dados de uma organização. O cliente (o cliente do Azure Information Protection ou o cliente Rights Management) está integrado nas aplicações executadas em computadores e dispositivos móveis.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 11/19/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a6fa85be-f92a-4e00-9efc-9dbfd4dfbfcb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 878d00d941a85f62982d9e23db36da8c5ad70078
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56251845"
---
# <a name="the-client-side-of-azure-information-protection"></a>O lado do cliente do Azure Information Protection

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

O Azure Information Protection fornece uma solução de servidor cliente que ajuda a proteger os documentos e os e-mails de uma organização:

- O cliente pode ser o cliente do Azure Information Protection ou do Rights Management e está integrado nas aplicações executadas em computadores e dispositivos móveis. 

- O serviço reside na cloud (Azure Information Protection, que utiliza o serviço Azure Rights Management para a proteção de dados) ou no local (Serviços de Gestão de Direitos do Active Directory). 

O cliente do Azure Information Protection suporta classificação e etiquetagem, bem como proteção. Este cliente está integrado nas aplicações do Office e tem de ser instalado em separado.

O cliente Rights Management (RMS) é instalado automaticamente com algumas aplicações, tais como as aplicações do Office, o cliente do Azure Information Protection, a aplicação de partilha RMS e as aplicações otimizadas para o RMS de fornecedores de software. No entanto, também pode ser instalado individualmente para suportar cenários como programadores que pretendam integrar a proteção Rights Management nas suas aplicações de linha de negócio.

Utilize a seguinte documentação quando precisar de mais informações sobre como implementar e utilizar estes clientes, que podem ser utilizados com o Azure Information Protection e os Serviços de Gestão de Direitos do Active Directory para ajudar a proteger os dados da sua organização:

- [Cliente do Azure Information Protection](AIP-client.md)

- [Notas de implementação do cliente RMS](client-deployment-notes.md)

- [Proteção RMS com Infraestrutura de Classificação de Ficheiros (FCI) do Windows Server](configure-fci.md)


## <a name="see-also"></a>Consulte também
[Comparar o Azure Information Protection e o AD RMS](../compare-on-premise.md)
