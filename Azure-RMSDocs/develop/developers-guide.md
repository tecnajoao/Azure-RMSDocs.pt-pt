---
title: "Guia para Programadores – AIP"
description: Os programadores podem utilizar o Azure Information Protection para proteger e gerir ficheiros de todos os tipos
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a53c2df2-a0a2-4f1f-995b-75ba55e4489b
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: 3268b175b2e029c55ec5488a8c4ace8ad92fcb18
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="azure-information-protection-developers-guide"></a>Guia para Programadores do Azure Information Protection

Este guia irá direcioná-lo para ferramentas para alargar e integrar com o serviço de gestão de direitos do Azure Information Protection. Este guia tem como objetivo permitir aos programadores que pretendem tirar partido do sistema de gestão de direitos criar diferentes tipos de aplicações para um intervalo de plataformas suportadas.

>O SDK do Azure Information Protection atual possui o componente de gestão de direitos, por sua vez, a classificação e a etiquetagem estão em desenvolvimento.

## <a name="service-applications"></a>Aplicações de Serviço

As aplicações de serviço fornecem capacidades para proteger informação durante a exportação a partir de um sistema de gestão de conteúdos de empresa, uma aplicação empresarial ou uma solução de negócios baseada na cloud. As aplicações Prevenção de Perda de Dados (DLP) e Cloud Application Security (CAS) são exemplos de aplicações de serviço. O nosso SDK para o desenvolvimento de aplicações de serviço está disponível através de dois modelos de programação.

- [C++](https://www.microsoft.com/en-us/download/details.aspx?id=38397)
- [API Gerida de C#](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcManagedAPI)

### <a name="examples-of-service-applications"></a>Exemplos de aplicações de serviço

- O [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma aplicação DLP preparada para RMS de exemplo que descreve os passos básicos que uma aplicação preparada para RMS DLP deve efetuar ao utilizar a API de Ficheiros RMS para proteger e consumir conteúdo restrito.
- O [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma amostra que demonstra como utilizar o SDK RMS em aplicações Azure para proteger dados num Armazenamento de Blobs do Azure.
- O [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma amostra que demonstra como criar uma aplicação do Windows que monitoriza os diretórios no sistema de ficheiros e aplica políticas de proteção RMS em todas as alterações, por exemplo, em ficheiros adicionados ou modificados.
- O [ProtectFilesInDir](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/ProtectFilesInDir) é um exemplo de aplicação de consola simples que utiliza um diretório como dados de entrada e protege todos os ficheiros contidos apenas nesse diretório, sem recursão.

## <a name="powershell-guides"></a>Guias do PowerShell

Estes scripts, normalmente utilizados por administradores de Azure Rights Management, são úteis para desenvolver e testar as aplicações de serviço.

- Os [cmdlets do Azure Rights Management](https://msdn.microsoft.com/library/azure/dn629398.aspx) permitem-lhe administrar o Azure RMS a partir da linha de comandos. Apesar de isto ativar a automatização, também dá suporte a processos fiáveis e repetidos para ajudar a reduzir as sobrecargas administrativas. Além disso, algumas configurações e operações avançadas do Azure RMS necessitam do Azure PowerShell.
- Os [cmdlets de Proteção RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx) podem ser utilizados com a proteção de dados do Azure Rights Management (Azure RMS) do Azure Information Protection ou com os Serviços de Gestão de Direitos do Active Directory (AD RMS) e complementar outros módulos do PowerShell nestas implementações do Rights Management. Utilize estes cmdlets de Proteção RMS para proteger e desproteger em volume ficheiros de qualquer tipo.

## <a name="user-applications"></a>Aplicações de utilizador

As aplicações de utilizador podem ser criadas com o SDK RMS 2.1 ou SDK RMS 4.2.
A versão 4.2 é baseada em clientes REST com APIs específicas de sistema operativo para vários SO populares: iOS/OSX, Android, Linux, Windows. A versão 2.1 é utilizada para compilar aplicações nativas baseadas em Windows.

### <a name="user-application-development-guides"></a>Guias de desenvolvimento de aplicações de utilizador

- [Desenvolver a sua aplicação](developing-your-application.md)
- [Testar a sua aplicação](how-to-set-up-your-test-environment.md)
- [Implementar a aplicação](deploying-your-application.md)

### <a name="user-application-samples"></a>Exemplos de aplicações de utilizador

- O [Teste AzureIP](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test) é uma aplicação da consola de exemplo que lhe permite encriptar documentos com um modelo Azure ou uma política ad hoc.
- O [IPCNotepad](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test) é uma aplicação preparada para RMS de exemplo que descreve os passos básicos que cada aplicação preparada para RMS deve executar quando proteger e consumir conteúdo restrito.
- [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma ferramenta que pode fornecer informações sobre qualquer ficheiro de RMS protegido, tal como ID de conteúdo ou direitos de utilizador.

## <a name="development-environment-setup"></a>Configuração do ambiente de desenvolvimento

Os guias seguintes vão orientá-lo pelos passos de configuração específicos do SO para um ambiente de desenvolvimento de aplicações através de ferramentas comuns.

[![Configuração do iOS/OSX](../media/develop/ios-icon.png)](ios-sdk.md)
[![Configuração do Android](../media/develop/android-icon.png)](android-sdk.md)
[![Configuração do Windows Phone](../media/develop/windows-phone-icon.png)](windows-phone-apps.md)
[![Configuração do Windows Service](../media/develop/windows-icon.png)](install-the-rms-sdk.md)
[![Configuração do Linux](../media/develop/linux-icon.png)](linux-setup.md)


## <a name="how-tos"></a>Procedimentos

Cada um dos seguintes tópicos apresenta instruções específicas para um aspeto da implementação da sua aplicação. As aplicações de serviço são compiladas com o SDK RMS 2.x. As aplicações de utilizador são compiladas com o SDK RMS 4.x. A ligação do artigo é atribuída com o tipo de aplicação, o serviço e o utilizador.

### <a name="general"></a>Geral

- [Como ativar o controlo e a revogação de documentos (serviço)](tracking-content.md)
- [Como implementar o seu cliente](../rms-client/client-deployment-notes.md)
- [Como implementar a aplicação de serviço num inquilino diferente] (how-to-deploy-app.md)
- [Como instalar e configurar um Servidor RMS (serviço)](how-to-install-and-configure-an-rms-server.md)
- [Como utilizar o controlo de documentos (utilizador)](how-to-use-document-tracking.md)
- [Como renovar uma chave simétrica no Azure Information Protection](how-to-renew-symmetric-key.md)

### <a name="security-and-authentication"></a>Segurança e autenticação

- [How to configure your app service application to use Azure Active Directory login (Como configurar a sua aplicação de serviço de aplicações para utilizar o início de sessão do Azure Active Directory)](https://docs.microsoft.com/en-us/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication)
- [Como utilizar a autenticação ADAL (Azure Active Directory Authentication)](how-to-use-adal-authentication.md)
- [Configurar o Azure RMS para a autenticação (serviço)](adal-auth.md)
- [Como definir o modo de segurança da API (serviço)](setting-the-api-security-mode-api-mode.md)
- [Permitir que as suas aplicações utilizem o Azure RMS (serviço)](how-to-use-file-api-with-aadrm-cloud.md)
- [Como registar-se e ativar o RMS na aplicação com o Azure AD (utilizador)](authentication-integration.md)

### <a name="configuration-and-performance-management"></a>Gestão de desempenho e configuração

- [Como adicionar direitos de proprietário explícitos (serviço)](add-explicit-owner-rights.md)
- [Configuração da API de Ficheiros (serviço)](file-api-configuration.md)
- [Como utilizar direitos incorporados (utilizador)](built-in-rights-usage-restriction-reference.md)
- [Como ativar registo de erros e de desempenho (utilizador)](enabling-logging.md)

## <a name="videos"></a>Vídeos

Dan Plastina da Microsoft apresenta esta [Introdução ao Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)

Estes vídeos são da conferência Microsoft Ignite 2016

- [Email security inside your org (Segurança de e-mails na sua organização)](https://myignite.microsoft.com/videos/2787)
- [Adopt a comprehensive identity-driven solution for protecting and sharing data securely (Adotar uma solução condicionada por identidade abrangente para proteger e partilhar dados de forma segura)](https://myignite.microsoft.com/videos/2784)
- [Learn how classification, labeling and protection delivers persistent data protection (Saiba como a classificação, etiquetagem e proteção proporcionam uma proteção de dados persistente)](https://myignite.microsoft.com/videos/2786)

## <a name="other-resources"></a>Outros recursos

- [Guia de procedimentos recomendados de segurança](security-guidelines.md)
- [Área para Programadores do RMS (blog)](https://blogs.msdn.microsoft.com/rms/)
- [Perguntas Mais Frequentes sobre o Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/get-started/faqs)

### <a name="support-articles"></a>Artigos de suporte

- [Formatos de ficheiro suportados](supported-file-formats.md)
- [Plataformas suportadas](supported-platforms.md)
- [Compreender as restrições de utilização](understanding-usage-restrictions.md)

### <a name="api-reference"></a>Referência da API

- [Referência da API do Windows](https://msdn.microsoft.com/en-us/library/hh535292.aspx)
  - [Windows SDK Error Codes (Códigos de Erro do Windows SDK)](https://msdn.microsoft.com/library/hh535248.aspx)
- [Windows Phone and Windows Store API reference (Referência da API do Windows Phone e da Loja Windows)](https://msdn.microsoft.com/library/dn891914.aspx)
- [iOS/OSX API reference (Referência da API do iOS/OSX)](https://msdn.microsoft.com/en-us/library/dn758306.aspx)
- [Android API reference (Referência da API do Android)](https://msdn.microsoft.com/en-us/library/dn758245.aspx)
- [Referência da API do Linux](http://azuread.github.io/rms-sdk-for-cpp/annotated.html)

### <a name="previous-versions"></a>Versões anteriores

- O [SDK AD RMS](https://msdn.microsoft.com/en-us/library/cc530379.aspx) é a primeira versão do SDK RMS.
- A [Ferramenta de scripting do AD RMS](https://msdn.microsoft.com/en-us/library/bb968797.aspx) é uma ferramenta administrativa para uma instalação do AD RMS.

### <a name="see-also"></a>Consulte também

- [Terminologia do programador](terms.md)
- [Terminologia do Azure Information Protection – ITPro](../get-started/terminology.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]