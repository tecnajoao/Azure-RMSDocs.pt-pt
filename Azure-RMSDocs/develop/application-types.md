---
title: Tipos de aplicações | Azure RMS
description: Este tópico inclui os tipos de aplicações que pode escolher para criar com capacidade para direitos.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 97169FC3-1395-4433-A632-7B0F020FABFE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 744a5648bc436bb903cf1b8feb47ca91b19bb7fc
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071663"
---
# <a name="application-types"></a>Tipos de aplicação


Este tópico inclui os tipos de aplicações que pode escolher para criar com capacidade para direitos.

Os seguintes tipos de aplicação são atualmente suportados pelo SDK Rights Management Services 2.1

## <a name="simple-applications"></a>Aplicações simples

Uma aplicação simples pode ser uma ferramenta de linha de comandos criada para encriptar um ficheiro fornecido. Para obter um exemplo de uma aplicação simples e com capacidade para direitos, consulte a nossa implementação de *IPCHelloWorld*, descrita em [Desenvolver a sua aplicação](developing-your-application.md).

### <a name="server-mode-applications"></a>Aplicações de modo de servidor

O *modo de servidor* destina-se às aplicações não interativas que consomem, protegem ou processam conteúdo protegido por RMS. Um exemplo seria uma aplicação de *Prevenção de Perda de Dados* que é executada como um serviço num servidor de ficheiros e protege automaticamente documentos confidenciais. Consulte o [Exemplo de IpcDlp](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcDlpApp) para obter um exemplo deste tipo de aplicação.

Se a sua aplicação utilizar o *modo de servidor*, deve autenticar para o servidor do RMS silenciosamente. Ao contrário do *modo de cliente*, o SDK RMS 2.1 não irá abrir um pedido de credenciais quando não conseguir autenticar silenciosamente. Além disso, quando executar no *modo de servidor*, não é necessário nenhum manifesto de aplicação.

Para obter mais informações sobre a definição do modo de segurança da API, consulte [Definir o modo de segurança de API](setting-the-api-security-mode-api-mode.md).

### <a name="rich-client-applications"></a>Aplicações de clientes avançados

Uma aplicação de cliente avançado permite que os utilizadores visualizem e manipulem dados através de uma interface gráfica (GUI). Os dados apresentados nesta GUI são frequentemente de elevado valor e passíveis de roubo ou exposição acidental. O suporte para proteção de informações normalmente melhora os cenários existentes; no entanto, não é a motivação primária para o desenvolvimento da aplicação.

Utilizar o SDK RMS 2.1 com aplicações de cliente avançado ajuda-o:

-   Garantir que estes dados são sempre encriptados.

-   Impedir que os utilizadores extraiam dados num formato não protegido (por exemplo, impedir a utilização da área de transferência para copiar e colar).

O Bloco de Notas da Microsoft é uma aplicação simples de cliente avançado. O Microsoft Office é uma aplicação de cliente avançado mais complexa.

Para obter mais informações acerca de como proteger a sua aplicação, consulte [Compreender as restrições de utilização](understanding-usage-restrictions.md).

## <a name="related-topics"></a>Tópicos relacionados

- [Exemplo de IpcDlp](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)
- [Desenvolver a sua aplicação](developing-your-application.md)
- [Definir o modo de segurança de API](setting-the-api-security-mode-api-mode.md)
- [Compreender as restrições de utilização](understanding-usage-restrictions.md)
