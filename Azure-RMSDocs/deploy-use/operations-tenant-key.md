---
title: Operações para a sua chave de inquilino do Azure Information Protection
description: Conheça os diferentes níveis de controlo e responsabilidade disponíveis para a sua chave de inquilino do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/22/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f459504f43c8e361e36832b19011f93d1cbaccc4
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="operations-for-your-azure-information-protection-tenant-key"></a>Operações para a sua chave de inquilino do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Consoante a topologia de chave inquilino do Azure Information Protection, tem diferentes níveis de controlo e responsabilidade para a sua chave de inquilino do Azure Information Protection. As duas topologias de chave são **gerida pela Microsoft** e **gerida pelo cliente**.

Quando gere a sua própria chave de inquilino no Cofre de Chaves do Azure, isto é frequentemente referido como BYOK (traga a sua própria chave). Para obter mais informações sobre este cenário e como escolher entre as topologias de chave de dois inquilino, consulte [planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md).

A tabela seguinte identifica as operações que pode fazer, consoante a topologia que escolheu para a sua chave de inquilino do Azure Information Protection.

|Operação de ciclo de vida|Gerida pela Microsoft (predefinição)|Gerida pelo cliente (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Revogar a chave de inquilino|Não (automático)|Sim|
|Recodificar a sua chave de inquilino|Sim|Sim|
|Efetuar cópia de segurança e recuperar a chave de inquilino|Não|Sim|
|Exportar a chave de inquilino|Sim|Não|
|Responder a uma violação|Sim|Sim|

Depois de identificar que topologia que implementou, selecione uma das ligações seguintes para obter mais informações sobre estas operações para a sua chave de inquilino do Azure Information Protection:

- [Chave de inquilino gerida pela Microsoft](operations-microsoft-managed-tenant-key.md)
- [Chave de inquilino gerida pelo cliente](operations-customer-managed-tenant-key.md)

No entanto, se quiser criar uma chave de inquilino do Azure Information Protection ao importar um domínio de publicação fiável (TPD) dos Serviços de Gestão de Direitos do Active Directory, esta operação de importação faz parte da [Migração do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
