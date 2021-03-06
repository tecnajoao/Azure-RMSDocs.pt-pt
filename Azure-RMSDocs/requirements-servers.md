---
title: Suporte do servidor para a proteção de dados do Azure RMS – AIP
description: Identifique os produtos de servidor no local que podem utilizar o serviço Azure Rights Management a partir do Azure Information Protection ao utilizar o conector do Rights Management.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/12/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e298fc08c610e5587aa6b8e4007f64aae2b0da42
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56251388"
---
# <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Servidores no local que suportam a proteção de dados do Azure Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Os seguintes produtos de servidor no local são suportados com o Azure Information Protection quando utiliza o conector do Azure Rights Management. Este conector funciona como uma interface de comunicação (um reencaminhador) entre os servidores no local e o serviço Azure Rights Management que é utilizado pelo Azure Information Protection para proteger e-mails e documentos do Office. 

Para utilizar este conector, tem de configurar a sincronização de diretórios entre as suas florestas do Active Directory e o Azure Active Directory.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Servidores de ficheiros que executam o Windows Server e utilizam a Infraestrutura de Classificação de Ficheiros (FCI)**:

    -   Windows Server 2016

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Uma vez que os servidores de ficheiros que executam o Windows Server 2008 R2 não têm uma ação de tarefa de gestão de ficheiros incorporados para aplicar a proteção do Rights Management, não pode utilizar o conector Rights Management para este cenário. No entanto, pode utilizar a Infraestrutura de Classificação de Ficheiros e o Azure RMS nestes sistemas operativos se configurar uma tarefa de gestão de ficheiros personalizada para executar um executável ou um script que possa proteger ficheiros ao utilizar o Azure RMS. Por exemplo, um script do Windows PowerShell que utiliza os [cmdlets AzureInformationProtection](/powershell/azureinformationprotection/vlatest/aip).
    > 
    > Também pode utilizar estes cmdlets com servidores a executar versões posteriores do Windows Server, com a vantagem de estes cmdlets poderem proteger todos os tipos de ficheiro. O conector RMS protege apenas os ficheiros do Office. Para obter instruções sobre como utilizar, consulte [Proteção RMS com Infraestrutura de Classificação de Ficheiros do Windows Server &#40;FCI&#41;](./rms-client/configure-fci.md).

O conector Rights Management é suportado no Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 e no Windows Server 2008 R2.

Para mais informações sobre como configurar o conector Rights Management para estes servidores no local, consulte [Implementar o conector do Azure Rights Management](deploy-rms-connector.md).

## <a name="next-steps"></a>Passos Seguintes
Para verificar outros requisitos, consulte [Requisitos do Azure Rights Management](requirements.md).
