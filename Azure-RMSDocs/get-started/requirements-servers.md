---
title: "Suporte do servidor para a proteção de dados do Azure RMS – AIP"
description: "Identifique os produtos de servidor no local que podem utilizar o serviço Azure Rights Management a partir do Azure Information Protection ao utilizar o conector do Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0278d07ae5afdfc95ffdf3945e5d3df7eae2f459
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Servidores no local que suportam a proteção de dados do Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

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

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Uma vez que os servidores de ficheiros que executam o Windows Server 2008 R2 não têm uma ação de tarefa de gestão de ficheiros incorporados para aplicar a proteção do Rights Management, não pode utilizar o conector Rights Management para este cenário. No entanto, pode utilizar a Infraestrutura de Classificação de Ficheiros e o Azure RMS nestes sistemas operativos se configurar uma tarefa de gestão de ficheiros personalizada para executar um executável ou um script que possa proteger ficheiros ao utilizar o Azure RMS. Por exemplo, um script do Windows PowerShell que utiliza os [cmdlets AzureInformationProtection](/powershell/azureinformationprotection/vlatest/aip).
    > 
    > Também pode utilizar estes cmdlets com servidores a executar versões posteriores do Windows Server, com a vantagem de estes cmdlets poderem proteger todos os tipos de ficheiro. O conector RMS protege apenas os ficheiros do Office. Para obter instruções sobre como utilizar, consulte [Proteção RMS com Infraestrutura de Classificação de Ficheiros do Windows Server &#40;FCI&#41;](../rms-client/configure-fci.md).

O conector Rights Management é suportado no Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 e no Windows Server 2008 R2.

Para mais informações sobre como configurar o conector Rights Management para estes servidores no local, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).

## <a name="next-steps"></a>Passos seguintes
Para verificar outros requisitos, consulte [Requisitos do Azure Rights Management](requirements-azure-rms.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]