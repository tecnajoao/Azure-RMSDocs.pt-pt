---
title: Operações para a sua chave de inquilino do Azure Information Protection
description: Conheça os diferentes níveis de controlo e responsabilidade disponíveis para a sua chave de inquilino do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/31/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 15d203ffc45de5cd5bee613bf6cb7e56a1d1f5bf
ms.sourcegitcommit: 99b33cee47bc4588174d44e90ade16edba12ee44
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43380536"
---
# <a name="operations-for-your-azure-information-protection-tenant-key"></a>Operações para a sua chave de inquilino do Azure Information Protection

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Consoante a topologia de chave inquilino do Azure Information Protection, tem diferentes níveis de controlo e responsabilidade para a sua chave de inquilino do Azure Information Protection. As duas topologias de chave são **gerida pela Microsoft** e **gerida pelo cliente**.

Quando gere a sua própria chave de inquilino no Cofre de Chaves do Azure, isto é frequentemente referido como BYOK (traga a sua própria chave). Para obter mais informações sobre este cenário e como escolher entre as topologias de chave de dois inquilino, consulte [planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

A tabela seguinte identifica as operações que pode fazer, consoante a topologia que escolheu para a sua chave de inquilino do Azure Information Protection.

|Operação de ciclo de vida|Gerida pela Microsoft (predefinição)|Gerida pelo cliente (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Revogar a chave de inquilino|Não (automático)|Sim|
|Recodificar a sua chave de inquilino|Sim|Sim|
|Efetuar cópia de segurança e recuperar a chave de inquilino|Não|Sim|
|Exportar a chave de inquilino|Sim|Não|
|Responder a uma violação|Sim|Sim|

Após ter identificado a topologia que implementou, selecione uma das ligações seguintes para obter mais informações sobre estas operações para a sua chave de inquilino do Azure Information Protection:

- [Chave de inquilino gerida pela Microsoft](operations-microsoft-managed-tenant-key.md)
- [Chave de inquilino gerida pelo cliente](operations-customer-managed-tenant-key.md)

No entanto, se quiser criar uma chave de inquilino do Azure Information Protection ao importar um domínio de publicação fiável (TPD) dos Serviços de Gestão de Direitos do Active Directory, esta operação de importação faz parte da [Migração do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).  

