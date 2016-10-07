---
title: "Operações para a sua chave de inquilino do Azure Rights Management | Azure Information Protection"
description: "Conheça os diferentes níveis de controlo e responsabilidade disponíveis para a sua chave de inquilino do Azure Information Protection."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d5b6a1fc3fa0a19f3a6b65aa7b8815eda7432cd7
ms.openlocfilehash: 780c4db3e791dd427828550e428ec4ea18d55fd5


---

# Operações para a sua chave de inquilino do Azure Information Protection

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







<!--HONumber=Sep16_HO4-->


