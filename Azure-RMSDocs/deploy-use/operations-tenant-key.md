---
title: "Operações para a sua chave de inquilino do Azure Rights Management | Azure RMS"
description: "Dependendo da topologia da chave de inquilino (gerida pela Microsoft ou pelo cliente), tem diferentes níveis de controlo e responsabilidade para a chave de inquilino do Microsoft Azure Rights Management (Azure RMS) após estar implementada."
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: bcd7a03c7eb0c40893bc37d0d5f108c2389dcc3f


---

# Operações para a sua chave de inquilino do Azure Rights Management

>*Aplica-se a: Azure Rights Management, Office 365*

Dependendo da topologia da chave de inquilino (gerida pela Microsoft ou pelo cliente), tem diferentes níveis de controlo e responsabilidade para a chave de inquilino do Microsoft Azure Rights Management (Azure RMS) após estar implementada.

Quando gere a sua própria chave de inquilino no Cofre de Chaves do Azure, isto é frequentemente referido como BYOK (traga a sua própria chave). Para obter mais informações sobre este cenário e como escolher entre as duas topologias de chave de inquilino, consulte [Planear e implementar a chave de inquilino do Azure Rights Management](../plan-design/plan-implement-tenant-key.md).

A tabela seguinte identifica as operações que pode fazer, consoante a topologia que escolheu para a chave de inquilino do Azure RMS.

|Operação de ciclo de vida|Gerida pela Microsoft (predefinição)|Gerida pelo cliente (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|Revogar a chave de inquilino|Não (automático)|Sim|
|Efetuar o rechaveamento da chave de inquilino|Sim|Sim|
|Efetuar cópia de segurança e recuperar a chave de inquilino|Não|Sim|
|Exportar a chave de inquilino|Sim|Não|
|Responder a uma violação|Sim|Sim|

Após ter identificado a topologia que implementou, selecione uma das seguintes opções para obter mais informações sobre estas operações para a sua chave de inquilino do Azure RMS:


- [Chave de inquilino gerida pela Microsoft](operations-microsoft-managed-tenant-key.md)
- [Chave de inquilino gerida pelo cliente](operations-customer-managed-tenant-key.md)







<!--HONumber=Aug16_HO4-->


