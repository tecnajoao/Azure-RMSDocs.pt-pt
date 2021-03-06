---
title: Guia para Programadores do RMS | Azure RMS
description: Estão agora disponíveis três gerações do SDK do Rights Management.
keywords: ''
author: msmbaldwin
manager: barbkess
ms.author: mbaldwin
ms.date: 12/11/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 0510ead4-2fe7-4269-885b-fe16bcc69888
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 82582497fccec063ad23e157780f871681dc0bb8
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57331805"
---
# <a name="rms-developers-guide"></a>Guia para Programadores do RMS

## <a name="overview"></a>Descrição geral ##
Estão agora disponíveis três gerações do SDK do Rights Management: **SDK Microsoft Rights Management 4.2** para Android, iOS/OS X, dispositivos Windows e Linux, **SDK Microsoft Rights Management 2.1** para o Cliente do Ambiente de Trabalho do Windows e o **SDK AD RMS** substituído.

## <a name="software-development-kits"></a>Kits de Programação de Software ##
| SDK | Descrição |
|------|---------|
| [SDK RMS 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Um conjunto de ferramentas simplificado e de última geração que fornece uma experiência de desenvolvimento simples para ativar as aplicações de dispositivos Android, iOS, Mac OS X, Windows Phone/RT e Linux/C++ com a proteção de informações através de serviços Microsoft Rights Management Services |
| [SDK RMS 2.1](microsoft-information-protection-and-control-client-portal.md) | Uma oferta de SDK potente para os programadores de aplicações de ambiente de trabalho do Windows e fornecedores de soluções baseadas em servidores ativarem os seus produtos com a gestão de direitos|
|[SDK AD RMS](/azure/information-protection/develop/) |** NOTA ** – a funcionalidade de aproveitamento do AD RMS SDK exposta pelo cliente no Msdrm.dll está disponível para utilização no Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows Server 2008 e Windows Vista. Pode ser alterada ou não estar disponível em versões posteriores. Em alternativa, utilize o SDK Microsoft Rights Management Services 2.1, que tira partido da funcionalidade exposta pelo cliente no Msipc.dll.|
|[API de Scripting do AD RMS](/azure/information-protection/develop/) | Utilizada para criar scripts para administrar uma instalação do AD RMS|

## <a name="code-samples-and-tools"></a>Exemplos de Código e Ferramentas ##
Esta coleção de ferramentas de suporte de programação e de exemplos de código do RMS fornecidos pela Microsoft abrange todos os sistemas operativos suportados; Android, iOS/OS X, Windows Phone e Ambiente de Trabalho do Windows e é atualizada periodicamente para manter a compatibilidade com o SDK suportado.

| Item | Sistema Operativo | Suporte da Versão do SDK | Descrição |
|------|------------------|------------------------|-------------|
| [IpcManagedAPI](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Ambiente de Trabalho do Windows | [SDK RMS 2.1](microsoft-information-protection-and-control-client-portal.md) e versões posteriores do SDK 2.x | **IpcManagedAPI** é uma representação de .NET (C#) do SDK RMS 2.1 para que a sua aplicação gerida esteja facilmente preparada para RMS.|
| [IPCNotepad](https://code.msdn.microsoft.com/ipcnotepad-sample-f67dae80) | Ambiente de Trabalho do Windows | [SDK RMS 2.1](microsoft-information-protection-and-control-client-portal.md) e versões posteriores do SDK 2.x| **IPCNotepad** é uma aplicação preparada para RMS de exemplo que descreve os passos básicos que cada aplicação preparada para RMS deve efetuar quando proteger e consumir conteúdo restrito.|
| [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms)|Ambiente de Trabalho do Windows|[SDK RMS 2.1](microsoft-information-protection-and-control-client-portal.md) e versões posteriores do SDK 2.x|**IpcDlp** é uma aplicação de Proteção de Fuga de Dados preparada para RMS de exemplo que descreve os passos básicos que uma aplicação preparada para RMS DLP deve efetuar ao utilizar a API de Ficheiros para proteger e consumir conteúdo restrito.|
| [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Ambiente de Trabalho do Windows|[SDK RMS 2.1](microsoft-information-protection-and-control-client-portal.md) e versões posteriores do SDK 2.x|**IpcAzureApp** é uma amostra que demonstra como utilizar o SDK RMS na aplicação Azure para proteger os dados no Armazenamento de Blobs do Azure.|
| [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Ambiente de Trabalho do Windows|[SDK RMS 2.1](microsoft-information-protection-and-control-client-portal.md) e versões posteriores do SDK 2.x|**RmsDocumentInspector** é uma ferramenta que pode fornecer informações sobre qualquer ficheiro de RMS protegido, tal como ID de conteúdo ou direitos de utilizador.|
| [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Ambiente de Trabalho do Windows|[SDK RMS 2.1](microsoft-information-protection-and-control-client-portal.md) e versões posteriores do SDK 2.x|O **RmsFileWatcher** é uma amostra que demonstra como criar uma aplicação do Windows que monitoriza os diretórios no sistema de ficheiros e aplica políticas de proteção RMS em todas as alterações, por exemplo, em ficheiros adicionados ou modificados.|
| [Cenários de utilização no iOS/OS X](https://msdn.microsoft.com/library/dn758307(v=vs.85).aspx) |iOS/OS X|[SDK RMS 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) e versões posteriores do SDK 4.x|Exemplos de código do **Objetivo C** que representam cenários de desenvolvimento importantes para o ajudar a habituar-se ao SDK RMS. Os exemplos incluem a utilização do formato de Ficheiro Protegido da Microsoft, formatos de ficheiros protegidos personalizados e controlos de IU personalizados.|
| [Aplicação de Exemplo e Biblioteca da IU](https://github.com/AzureAD/rms-sdk-ui-for-ios) |iOS|[SDK RMS 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) e versões posteriores do SDK 4.x|**Bibliotecas da IU e aplicação de exemplo para iOS** no GitHub para que possa começar rapidamente e reutilizar a nossa IU padrão nas suas aplicações.|
| [Aplicação de Exemplo e Biblioteca da IU](https://github.com/AzureAD/rms-sdk-ui-for-android) |Android|[SDK RMS 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) e versões posteriores do SDK 4.x|**Bibliotecas da IU e aplicação de exemplo para Android** no GitHub para que possa começar rapidamente e reutilizar a nossa IU padrão nas suas aplicações.|
| [Cenários de utilização no Android](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) |Android|[SDK RMS 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) e versões posteriores do SDK 4.x|**Exemplos de código Java** que representam cenários de desenvolvimento importantes para o ajudar a habituar-se ao SDK RMS. Os exemplos incluem a utilização do formato de Ficheiro Protegido da Microsoft, formatos de ficheiros protegidos personalizados e controlos de IU personalizados.|
