---
title: Orientação para programadores sobre o SDK 2.1 do Azure Information Protection | Documentos da Microsoft
description: Uma coleção de tópicos com instruções sobre como programar o SDK 2.1 do AIP
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 5e85005cd497be45a2b92631a682121482e5997f
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44147486"
---
# <a name="developer-guidance"></a>Orientação para programadores

Esta secção inclui documentação de orientação específica para diversos cenários de desenvolvimento importantes, bem como informações gerais sobre a desenvolvimento este SDK. Os cenários nesta secção são específicos desta versão do SDK Rights Management Services 2.1 e poderão ser alterados em versões posteriores.
- [Procedimentos: utilizar a autenticação ADAL](how-to-use-adal-authentication.md) - Autenticação com o Azure RMS para a sua aplicação com o ADAL (Azure Active Directory Authentication Library).
- [Procedimentos: adicionar direitos de proprietário explícitos](add-explicit-owner-rights.md) – a sua aplicação deve adicionar explicitamente direitos de "Proprietário" quando cria uma licença de raiz ([IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)).
- [Procedimentos: depurar uma aplicação com capacidade para direitos](debugging-applications-that-use-ad-rms.md) - Este tópico mostra como depurar a aplicação e utilizar o Registo de Eventos do Windows.
- [Procedimentos: implementar uma aplicação no inquilino de um cliente](how-to-deploy-app.md) – descreve os passos para implementar uma aplicação, desde o seu inquilino de desenvolvimento do Azure AD ao inquilino de produção do Azure AD.
- [Procedimentos: ativar o controlo e a revogação de documentos](tracking-content.md) -Este tópico inclui a documentação de orientação básica para implementação do controlo de documento do conteúdo, bem como código de exemplo para atualizações de metadados e criação de um botão **Controlar Utilização** para a sua aplicação.
- [Procedimentos: ativar a notificação por e-mail](how-to-enable-email-notification.md) – a notificação por e-mail permite que um proprietário de conteúdo protegido seja notificado quando esse conteúdo for acedido.
- [Procedimentos: permitir que a aplicação de serviço funcione com o RMS baseado na cloud](how-to-use-file-api-with-aadrm-cloud.md) – este tópico descreve os passos para configurar a sua aplicação de serviço para utilizar o Azure Rights Management.
- [Procedimentos: instalar e configurar um servidor RMS](how-to-install-and-configure-an-rms-server.md) - este tópico inclui os passos para ligação a um Servidor RMS ou ao Azure RMS para fins de testar da sua aplicação com capacidade para direitos.
- [Procedimentos: definir o modo de segurança da API](setting-the-api-security-mode-api-mode.md) – pode escolher em que modo de segurança a sua aplicação de API de Ficheiros é executada utilizando a função [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx).
- [Procedimentos: trabalhar com definições de encriptação](working-with-encryption.md) – este tópico descreve os nossos pacotes de encriptação e mostra alguns fragmentos de código para utilização.
- [Tipos de aplicação](application-types.md) – este tópico inclui os tipos de aplicações que pode escolher para criar com capacidade para direitos.
- [Configuração da API de ficheiros](file-api-configuration.md) – o comportamento da API de ficheiros pode ser configurado através de definições no registo.
- [Diretrizes de segurança](security-guidelines.md) – disponibiliza orientação e instruções para os programadores de aplicações para que estes trabalhem bem no ecossistema do AIP.
- [Formatos de ficheiro suportados](supported-file-formats.md) – a API de Ficheiros suporta formatos nativos e Pfile
- [Plataformas suportadas](supported-platforms.md) - este tópico identifica as plataformas de cliente e de servidor suportadas pelo SDK RMS 2.1.
- [Compreender restrições de utilização](understanding-usage-restrictions.md) – todas as aplicações com suporte RMS têm de impor restrições de utilização, que são definidas pelas constantes indicadas neste tópico.

 
## <a name="related-topics"></a>Tópicos relacionados
* [Descrição Geral](ad-rms-overview.md)
