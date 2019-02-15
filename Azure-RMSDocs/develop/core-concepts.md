---
title: Orientação para programadores sobre o SDK 4.2 do Azure Information Protection | Documentos da Microsoft
description: Uma coleção de tópicos com instruções sobre como programar o SDK 4.2 do AIP
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 01/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ae67523a-c094-44da-86b8-739bedba7111
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 4e4ded66c7372f6bbc4d737a3b0275de8237cbe5
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56255528"
---
# <a name="developer-guidance"></a>Orientação para programadores
O foco do SDK Microsoft Rights Management 4.2 é ajudá-lo a criar AD aplicativos habilitados para RMS que tiram partido dos Active Directory Right Management Services (AD RMS), a forma mais simples possível.

Os tópicos seguintes destinam-se a suportar o processo de estruturação para desenvolver aplicações com suporte para o RMS.

- [Como registar e ativar o RMS na aplicação com o Azure AD](authentication-integration.md) – Descreve as noções básicas da autenticação de utilizador para a sua aplicação com capacidade para RMS.
- [Como ativar o registo de desempenho de erros e](enabling-logging.md) -SDK RMS 4.2 gere o diagnóstico e de desempenho o carregamento de registos através de uma propriedade de único dispositivo.
- [Como utilizar direitos incorporados](built-in-rights-usage-restriction-reference.md) -descreve os direitos incorporados que o SDK RMS 4.2 concede e as restrições de utilização que uma aplicação deve impor para respeitar essas restrições.
- [Como utilizar controlo de documentos](how-to-use-document-tracking.md) – A utilização da funcionalidade de controlo de documentos requer alguns conhecimentos simples sobre a gestão dos metadados associados e o registo do serviço.
