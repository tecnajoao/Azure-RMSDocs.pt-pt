---
title: Terminologia para Programadores do AIP | Documentos da Microsoft
description: Uma coleção de definições terminológicas para programadores específicas dos Serviços de Gestão de Direitos.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8ddf0b8722111ff2cd4c433337c4e0c930b02009
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151562"
---
# <a name="terms"></a>Termos

Uma coleção de definições terminológicas para programadores específicas do Azure Information Protection.

**Algoritmo Preterido**  
Uma definição modal que implementa um esquema de proteção de conteúdo mais antigo, referenciando especificamente o modo de cifra ECB (Electronic Codebook). Neste SDK, a definição permite-lhe gerar licenças compatíveis com a biblioteca MSDRM utilizada pelo [SDK dos Serviços de Gestão de Direitos do AD](https://msdn.microsoft.com/library/windows/desktop/cc530379.aspx).

Esta definição pode fazer com que a sua aplicação proteja conteúdo de uma forma que não esteja em conformidade com as normas dos seus clientes para proteção de conteúdo.

Esta definição irá impedir que a sua aplicação tire partido de quaisquer melhorias criptográficas adicionadas ao SDK Microsoft Rights Management 3.0 ou posterior.

**Formato de ficheiro protegido da Microsoft**

Também conhecido como formato PFile, é o formato de ficheiro predefinido do AD RMS e funciona como um padrão em aplicações preparadas para RMS.

O formato PFile é transparente para o programador de aplicações, já que está incorporado na forma como o SDK Microsoft Rights Management 4.2 é concebido.

