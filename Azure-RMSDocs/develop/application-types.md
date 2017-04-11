---
title: "Tipos de aplicações | Azure RMS"
description: "Este tópico inclui os tipos de aplicações que pode escolher para criar com capacidade para direitos."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 97169FC3-1395-4433-A632-7B0F020FABFE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: f93df5f204350a56f8280f299c04478cc1b5dfba
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="application-types"></a>Tipos de aplicações


Este tópico inclui os tipos de aplicações que pode escolher para criar com capacidade para direitos.

Os tipos de aplicações que se seguem são atualmente suportados pelo SDK Rights Management Services 2.1

## <a name="simple-applications"></a>Aplicações simples

Uma aplicação simples pode ser uma ferramenta de linha de comandos criada para encriptar um ficheiro fornecido. Para obter um exemplo de uma aplicação simples e com capacidade para direitos, consulte a nossa implementação de *IPCHelloWorld*, descrita em [Desenvolver a sua aplicação](developing-your-application.md).

### <a name="server-mode-applications"></a>Aplicações de modo de servidor

O *modo de servidor* destina-se às aplicações não interativas que consomem, protegem ou processam conteúdo protegido por RMS. Um exemplo seria uma aplicação de *Prevenção de Perda de Dados* que é executada como um serviço num servidor de ficheiros e protege automaticamente documentos confidenciais. Consulte o [Exemplo de IpcDlp](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d) para obter um exemplo deste tipo de aplicação.

Se a sua aplicação utilizar o *modo de servidor*, deve autenticar para o servidor do RMS silenciosamente. Ao contrário do *modo de cliente*, o SDK RMS 2.1 não irá abrir um pedido de credenciais quando não conseguir autenticar silenciosamente. Além disso, quando executar no *modo de servidor*, não é necessário nenhum manifesto de aplicação.

Para obter mais informações sobre a definição do modo de segurança da API, consulte [Definir o modo de segurança de API](setting-the-api-security-mode-api-mode.md).

### <a name="rich-client-applications"></a>Aplicações de clientes avançados

Uma aplicação de cliente avançado permite que os utilizadores visualizem e manipulem dados através de uma interface gráfica (GUI). Os dados apresentados nesta GUI são frequentemente de elevado valor e passíveis de roubo ou exposição acidental. O suporte para proteção de informações normalmente melhora os cenários existentes; no entanto, não é a motivação primária para o desenvolvimento da aplicação.

Utilizar o SDK RMS 2.1 com aplicações de cliente avançado ajuda-o a:

-   Garantir que estes dados são sempre encriptados.

-   Impedir que os utilizadores extraiam dados num formato não protegido (por exemplo, impedir a utilização da área de transferência para copiar e colar).

O Bloco de Notas da Microsoft é uma aplicação simples de cliente avançado. O Microsoft Office é uma aplicação de cliente avançado mais complexa.

Para obter mais informações acerca de como proteger a sua aplicação, consulte [Compreender as restrições de utilização](understanding-usage-restrictions.md).

## <a name="related-topics"></a>Tópicos relacionados

- [Exemplo de IpcDlp](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)
- [Desenvolver a sua aplicação](developing-your-application.md)
- [Definir o modo de segurança de API](setting-the-api-security-mode-api-mode.md)
- [Compreender as restrições de utilização](understanding-usage-restrictions.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]