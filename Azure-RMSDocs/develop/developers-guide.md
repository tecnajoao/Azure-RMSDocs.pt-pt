---
title: Guia para Programadores | Azure RMS
description: "Descrição geral da utilização de ferramentas de programação; SDKs, bibliotecas adicionais e exemplos de código."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a22e6bd0-8ce8-45b4-9a32-273126ab831e
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c50775c43aea8950ca9c560c61712ffbbede8599
ms.openlocfilehash: 442dd2e6b3487964d5740c533894aa4de30f00ab


---

# <a name="developers-guide"></a>Guia para Programadores

## <a name="overview"></a>Descrição Geral ##
Este guia descreve o nosso conjunto de aplicações dos SDKs Rights Management e um conjunto crescente de ferramentas e exemplos de código que abrange todas as plataformas suportadas.

## <a name="software-development-kits"></a>Kits de Programação de Software ##
Neste momento estão disponíveis três gerações de SDK RMS, descritas na tabela seguinte.

| SDK | Descrição |
|------|---------|
| [SDK RMS 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Um conjunto de ferramentas simplificado e de última geração que fornece uma experiência de desenvolvimento simples para ativar as aplicações de dispositivos Android, iOS, Mac OS X, Windows Phone/RT e Linux/C++ com a proteção de informações através de serviços Microsoft Rights Management Services |
| [SDK RMS 2.1](microsoft-information-protection-and-control-client-portal.md) | Uma oferta de SDK potente para os programadores de aplicações de ambiente de trabalho do Windows e fornecedores de soluções baseadas em servidores ativarem os seus produtos com a gestão de direitos|
|[SDK AD RMS](https://msdn.microsoft.com/library/cc530379.aspx)|** NOTA ** – a funcionalidade de aproveitamento do SDK AD RMS exposta pelo cliente no Msdrm.dll está disponível para utilização no Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows Server 2008 e Windows Vista. Pode ser alterada ou não estar disponível em versões posteriores. Em alternativa, utilize o SDK Microsoft Rights Management Services 2.1, que tira partido da funcionalidade exposta pelo cliente no Msipc.dll.|
|[API de Scripting do AD RMS](https://msdn.microsoft.com/en-us/library/bb968797.aspx)| Utilizada para criar scripts para administrar uma instalação do AD RMS|

## <a name="powershell-guidance"></a>Orientações do PowerShell

Os [cmdlets do Azure Rights Management](https://msdn.microsoft.com/library/azure/dn629398.aspx) permitem-lhe administrar o Azure RMS a partir da linha de comandos. Apesar de isto ativar a automatização, também dá suporte a processos fiáveis e repetidos para ajudar a reduzir as sobrecargas administrativas. Além disso, algumas configurações e operações avançadas do Azure RMS necessitam do Azure PowerShell.

Os [cmdlets de Proteção RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx) podem ser utilizados com a proteção de dados do Azure Rights Management (Azure RMS) do Azure Information Protection ou com os Serviços de Gestão de Direitos do Active Directory (AD RMS) e complementar outros módulos do PowerShell nestas implementações do Rights Management. Utilize estes cmdlets de Proteção RMS para proteger e desproteger em volume ficheiros de qualquer tipo.

## <a name="code-samples-and-tools"></a>Exemplos de Código e Ferramentas
Esta coleção de ferramentas de suporte de programação e de exemplos de código do RMS fornecidos pela Microsoft abrange todos os sistemas operativos suportados; Android, iOS/OS X, Windows Phone e Ambiente de Trabalho do Windows e é atualizada periodicamente para manter a compatibilidade com o SDK suportado.

### <a name="android"></a>Android

Os seguintes são executados no Android suportado pelo [SDK RMS 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) e versões posteriores do SDK 4.x.

- [Biblioteca da IU e Aplicação de exemplo](https://github.com/AzureAD/rms-sdk-ui-for-android) no GitHub para que possa começar rapidamente e reutilizar a nossa IU padrão nas suas aplicações.
- Os [cenários de utilização do Android](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) em Java representam cenários de desenvolvimento importantes para o ajudar a habituar-se ao SDK RMS. Os exemplos incluem a utilização do formato de Ficheiro Protegido da Microsoft, formatos de ficheiros protegidos personalizados e controlos de IU personalizados.

### <a name="ios-os-x"></a>iOS/OS X

Os seguintes são executados no iOS/OS X suportado pelo [SDK RMS 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) e versões posteriores do SDK 4.x.

- Os [cenários de utilização do iOS/OS X](https://msdn.microsoft.com/en-us/library/dn758307(v=vs.85).aspx) em Objective C representam cenários de desenvolvimento importantes para o ajudar a habituar-se ao SDK RMS. Os exemplos incluem a utilização do formato de Ficheiro Protegido da Microsoft, formatos de ficheiros protegidos personalizados e controlos de IU personalizados.
- [Biblioteca da IU e Aplicação de exemplo](https://github.com/AzureAD/rms-sdk-ui-for-ios) no GitHub para que possa começar rapidamente e reutilizar a nossa IU padrão nas suas aplicações. Suportado **apenas em iOS**.

### <a name="windows-desktop"></a>Ambiente de Trabalho do Windows

Os seguintes são executados no Ambiente de Trabalho do Windows suportado pelo [SDK RMS 2.1](microsoft-information-protection-and-control-client-portal.md) e versões posteriores do SDK 2.x.

- [Ler PDF PFILE protegido](https://blogs.msdn.microsoft.com/rms/2015/11/09/reading-a-pfile-protected-pdf/) é um exemplo de código simples no blogue Área para Programadores do RMS que utiliza a API de Ficheiros MSIPC para desencriptar e abrir um documento PDF PFILE protegido.
- [IpcManagedAPI](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma representação de .NET (C#) do SDK RMS 2.1 para que a sua aplicação gerida esteja facilmente preparada para RMS.
- [IPCNotepad](https://code.msdn.microsoft.com/ipcnotepad-sample-f67dae80) é uma aplicação preparada para RMS de exemplo que descreve os passos básicos que cada aplicação preparada para RMS deve efetuar quando proteger e consumir conteúdo restrito.
- [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma aplicação de Proteção de Fuga de Dados preparada para RMS de exemplo que descreve os passos básicos que uma aplicação preparada para RMS DLP deve efetuar ao utilizar a API de Ficheiros para proteger e consumir conteúdo restrito.
- [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma amostra que demonstra como utilizar o SDK RMS na aplicação Azure para proteger os dados no Armazenamento de Blobs do Azure.
- [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma ferramenta que pode fornecer informações sobre qualquer ficheiro de RMS protegido, tal como ID de conteúdo ou direitos de utilizador.
- [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma amostra que demonstra como criar uma aplicação do Windows que monitoriza os diretórios no sistema de ficheiros e aplica políticas de proteção RMS em todas as alterações, por exemplo, em ficheiros adicionados ou modificados.

### <a name="windows-store-and-phone"></a>Loja Windows e Windows Phone

- [Biblioteca da interface de utilizador para Loja Windows](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore) – Uma Biblioteca da interface de utilizador do SDK Microsoft RMS v4.1 para Aplicações da Loja Windows. Esta biblioteca é opcional e um programador pode optar por criar a sua própria interface de utilizador quando utiliza o SDK Microsoft RMS v4.1

- [Biblioteca da interface de utilizador para Windows Phone](https://github.com/AzureAD/rms-sdk-ui-for-winphone) – Uma Biblioteca da interface de utilizador do SDK Microsoft RMS v4.1 para Aplicações do Windows Phone. Esta biblioteca é opcional e um programador pode optar por criar a sua própria interface de utilizador quando utiliza o SDK Microsoft RMS v4.1

- [Aplicação de exemplo](https://github.com/Azure-Samples/active-directory-dotnet-rms-windowsstore) – O Exemplo do SDK Microsoft RMS v4.1 para Aplicações da Loja Windows proporciona um exemplo de consumo de documento básico para a plataforma.



<!--HONumber=Oct16_HO5-->


