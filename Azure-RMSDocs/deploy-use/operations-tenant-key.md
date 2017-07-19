---
title: "Operações para a sua chave de inquilino do Azure Information Protection"
description: "Conheça os diferentes níveis de controlo e responsabilidade disponíveis para a sua chave de inquilino do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 10ce24e72dae1225505592508d4bf88cadb131a2
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="operations-for-your-azure-information-protection-tenant-key"></a>Operações para a sua chave de inquilino do Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Consoante a topologia da sua chave de inquilino (gerida pela Microsoft ou pelo cliente), terá diferentes níveis de controlo e responsabilidade para a chave de inquilino do Azure Information Protection após esta ser implementada.

Quando gere a sua própria chave de inquilino no Cofre de Chaves do Azure, isto é frequentemente referido como BYOK (traga a sua própria chave). Para obter mais informações sobre este cenário e como escolher entre as duas topologias de chave de inquilino, consulte [Planear e implementar a chave de inquilino do Azure Rights Management](../plan-design/plan-implement-tenant-key.md).

A tabela seguinte identifica as operações que pode efetuar, consoante a topologia que escolheu para a chave de inquilino do Azure Information Protection.

|Operação de ciclo de vida|Gerida pela Microsoft (predefinição)|Gerida pelo cliente (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Revogar a chave de inquilino|Não (automático)|Sim|
|Efetuar arecodificação da chave de inquilino|Sim|Sim|
|Efetuar cópia de segurança e recuperar a chave de inquilino|Não|Sim|
|Exportar a chave de inquilino|Sim|Não|
|Responder a uma violação|Sim|Sim|

Após identificar a topologia que implementou, selecione uma das seguintes opções para obter mais informações sobre estas operações para a sua chave de inquilino do Azure Information Protection:

- [Chave de inquilino gerida pela Microsoft](operations-microsoft-managed-tenant-key.md)
- [Chave de inquilino gerida pelo cliente](operations-customer-managed-tenant-key.md)

No entanto, se quiser criar uma chave de inquilino do Azure Information Protection ao importar um domínio de publicação fiável (TPD) dos Serviços de Gestão de Direitos do Active Directory, esta operação de importação faz parte da [Migração do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
