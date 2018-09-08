---
title: Guia para Programadores do Azure Information Protection
description: Os programadores podem utilizar o Azure Information Protection para proteger e gerir ficheiros de todos os tipos
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 10/11/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: a53c2df2-a0a2-4f1f-995b-75ba55e4489b
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: 21564a219a05efb0d47a12755d4334cc9ac2a559
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44150352"
---
# <a name="azure-information-protection-developers-guide"></a>Guia para Programadores do Azure Information Protection

Este guia irá direcioná-lo para ferramentas para alargar e integrar com o serviço de gestão de direitos do Azure Information Protection.

>O SDK do Azure Information Protection atual possui o componente de gestão de direitos. Uma classificação e etiquetagem componentes estão em desenvolvimento.

## <a name="service-applications"></a>Aplicações de Serviço

Aplicações de serviço fornecem capacidades para proteger as informações ao exportar a partir de um sistema de gerenciamento de conteúdo empresarial, um aplicativo de negócios ou uma solução de negócios baseado na cloud. As aplicações Prevenção de Perda de Dados (DLP) e Cloud Application Security (CAS) são exemplos de aplicações de serviço. O nosso SDK para o desenvolvimento de aplicações de serviço está disponível através de dois modelos de programação.

- [C++](https://www.microsoft.com/download/details.aspx?id=38397)
- [API Gerida de C#](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcManagedAPI)

### <a name="examples-of-service-applications"></a>Exemplos de aplicações de serviço

- O [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma aplicação DLP preparada para RMS de exemplo que descreve os passos básicos que uma aplicação preparada para RMS DLP deve efetuar ao utilizar a API de Ficheiros RMS para proteger e consumir conteúdo restrito.
- O [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma amostra que demonstra como utilizar o SDK RMS em aplicações Azure para proteger dados num Armazenamento de Blobs do Azure.
- O [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) é uma amostra que demonstra como criar uma aplicação do Windows que monitoriza os diretórios no sistema de ficheiros e aplica políticas de proteção RMS em todas as alterações, por exemplo, em ficheiros adicionados ou modificados.
- O [ProtectFilesInDir](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/ProtectFilesInDir) é um exemplo de aplicação de consola simples que utiliza um diretório como dados de entrada e protege todos os ficheiros contidos apenas nesse diretório, sem recursão.

## <a name="powershell-guides"></a>Guias do PowerShell

Usado por administradores de gestão de direitos do Azure, PowerShell cmdlets também são úteis para desenvolver e testar seus aplicativos de serviço. Para obter mais informações, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](/azure/information-protection/rms-client/client-admin-guide-powershell).

## <a name="user-applications"></a>Aplicações de utilizador

As aplicações de utilizador podem ser criadas com o SDK RMS 2.1 ou SDK RMS 4.2.
A versão 4.2 é baseada em clientes REST com APIs específicas de sistema operativo para vários SO populares: iOS/OSX, Android, Linux, Windows. A versão 2.1 é utilizada para a criação de aplicativos nativos com base em Windows.

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

- [How to configure your app service application to use Azure Active Directory login (Como configurar a sua aplicação de serviço de aplicações para utilizar o início de sessão do Azure Active Directory)](https://docs.microsoft.com/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication)
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

## <a name="introduction-and-datasheets"></a>Introdução e folhas de dados

[Introdução ao Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)

## <a name="other-resources"></a>Outros recursos

- [Guia de procedimentos recomendados de segurança](security-guidelines.md)
- [Área para Programadores do RMS (blog)](https://blogs.msdn.microsoft.com/rms/)
- [Perguntas Mais Frequentes sobre o Azure Information Protection](https://docs.microsoft.com/information-protection/get-started/faqs)

### <a name="support-articles"></a>Artigos de suporte

- [Formatos de ficheiro suportados](supported-file-formats.md)
- [Plataformas suportadas](supported-platforms.md)
- [Compreender as restrições de utilização](understanding-usage-restrictions.md)

### <a name="message-protocol-and-file-formats"></a>Formatos de arquivo e protocolo de mensagens

- [Protocolo de cliente-servidor](https://msdn.microsoft.com/library/cc243191.aspx)
- [Protocolo de objetos geridos de direitos de E-Mail](https://msdn.microsoft.com/library/cc463909(v=EXCHG.80).aspx)
- [Componha o formato de arquivo binário de ficheiro](https://msdn.microsoft.com/library/dd942138.aspx)

#### <a name="rights-managed-email-message"></a>Mensagem de e-mail gerido de direitos

- [. Formato de arquivo de mensagem (parte 1)](https://blogs.msdn.microsoft.com/openspecification/2009/11/06/msg-file-format-part-1/)
- [. Formato de arquivo de mensagem (parte 2)](https://blogs.msdn.microsoft.com/openspecification/2010/06/20/msg-file-format-rights-managed-email-message-part-2/)

### <a name="api-reference"></a>Referência da API

- [Referência da API do Windows](https://msdn.microsoft.com/library/hh535292.aspx)
  - [Windows SDK Error Codes (Códigos de Erro do Windows SDK)](https://msdn.microsoft.com/library/hh535248.aspx)
- [Windows Phone and Windows Store API reference (Referência da API do Windows Phone e da Loja Windows)](https://msdn.microsoft.com/library/dn891914.aspx)
- [iOS/OSX API reference (Referência da API do iOS/OSX)](https://msdn.microsoft.com/library/dn758306.aspx)
- [Android API reference (Referência da API do Android)](https://msdn.microsoft.com/library/dn758245.aspx)
- [Referência da API do Linux](http://azuread.github.io/rms-sdk-for-cpp/annotated.html)

### <a name="previous-versions"></a>Versões anteriores

- O [SDK AD RMS](https://msdn.microsoft.com/library/cc530379.aspx) é a primeira versão do SDK RMS.
- A [Ferramenta de scripting do AD RMS](https://msdn.microsoft.com/library/bb968797.aspx) é uma ferramenta administrativa para uma instalação do AD RMS.

### <a name="see-also"></a>Consulte também

- [Terminologia para programadores](terms.md)
- [Terminologia do Azure Information Protection – ITPro](../terminology.md)

