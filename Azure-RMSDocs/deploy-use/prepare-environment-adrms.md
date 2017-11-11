---
title: Preparar o ambiente para o Azure RMS e o AD RMS
description: "Orientações para o caso de ter o Azure Rights Management com o AD RMS implementado."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b20bbc1fe0de90b9b0151098e1b77d3c7a98c431
ms.sourcegitcommit: e9a24fc5303b21f5eeebf16afed44db0d163ac77
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/11/2017
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>Preparar o ambiente para o Azure Rights Management quando também tem os Serviços de Gestão de Direitos do Active Directory (AD RMS)

>*Aplica-se a: Azure Information Protection, Office 365*

Orientações importantes se já estiver a utilizar os Serviços de Gestão de Direitos do Active Directory (AD RMS) e o seguinte cenário se aplicar:

## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Verá uma opção para ativar a proteção, quando configurar o Azure Information Protection

O **Azure Information Protection - ativação da proteção** painel tem uma opção para ativar o serviço Azure Rights Management (Azure RMS). 

Se também estiver a utilizar os Serviços de Gestão de Direitos do Active Directory (AD RMS), não selecione a opção **Ativar**. Se tiver o AD RMS, a ativação do Azure Rights Management também não é uma opção compatível. Este cenário não é suportado e tem resultados pouco fiáveis, pelo que é importante que não ative o Azure Rights Management nesta fase. 

Quando estiver pronto para mudar os computadores do AD RMS para o serviço Azure Rights Management, pode iniciar um processo de migração. Um dos passos da migração é ativar o serviço. No entanto, só deve fazê-lo depois de exportar as informações de configuração do AD RMS para o serviço Azure Rights Management. Este processo garante que continua a poder abrir os e-mails e documentos que foram protegidos pelo AD RMS.

Quando o serviço Azure Rights Management não está ativado, continua a poder utilizar o Azure Information Protection apenas para etiquetas que aplicam classificação. É criada uma política predefinida especial que não inclui a proteção de dados. Essas opções de configuração permanecem indisponíveis até ativar o serviço Azure Rights Management.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Passo 1: configurar a política do Azure Information Protection para classificação e etiquetagem (sem proteção)

No painel inicial **Azure Information Protection**, selecione **Política global** para ver e configurar a sua política predefinida que não inclui opções de proteção de dados. Para mais informações, veja [Configurar a política do Azure Information Protection](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Passo 2: começar a planear a migração

Siga as orientações de migração: [migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

### <a name="step-3-start-to-configure-labels-for-protection"></a>Passo 3: começar a configurar as etiquetas para a proteção

Depois de ativar o serviço Azure Rights Management como parte do processo de migração, pode configurar as etiquetas para a proteção de dados. No entanto, se migrar utilizadores em lotes, certifique-se de que as etiquetas que aplicam a proteção [visam](configure-policy-scope.md) apenas os utilizadores migrados.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


