---
# required metadata

title: Notas do programador | Azure RMS
description: Este tópico inclui orientações específicas para vários cenários de desenvolvimento importantes. 
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Notas do programador

Esta secção inclui orientações específicas para vários cenários de desenvolvimento importantes. Os cenários nesta secção são específicos desta versão do SDK Rights Management Services 2.1 e poderão ser alterados em versões posteriores.

- [Adicionar direitos de proprietário explícitos](add-explicit-owner-rights.md) – A aplicação deve adicionar explicitamente direitos de &quot;Proprietário&quot; quando criar uma licença do zero ([IpcCreateLicenseFromScratch](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)).
- [Condições de erro comuns e soluções](common-error-conditions-and-solutions.md) – Este tópico inclui as mensagens de erro mais comuns que poderá encontrar ao utilizar as ferramentas de programador do SDK RMS 2.1.
- [Permitir notificação por e-mail](how-to-enable-email-notification.md) – A notificação por e-mail permite que um proprietário de conteúdo protegido seja notificado quando o respetivo conteúdo for acedido.
- [Configuração da API de ficheiros](file-api-configuration.md) – O comportamento da API de ficheiros pode ser configurado através de definições no registo.
- [IPCHelloWorld – uma aplicação de exemplo](how-to-build-your-first-application.md) – Este tópico contém instruções para criar uma aplicação com capacidade para direitos.
- [Definir o modo de segurança de API](setting-the-api-security-mode-api-mode.md) – Pode escolher em que modo de segurança a sua aplicação de API de Ficheiros é executada ao utilizar a função [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty).
- [Formatos de ficheiro suportados](supported-file-formats.md) – A API de Ficheiros suporta formatos nativos e Pfile.
- [Controlar conteúdo](tracking-content.md) – Este tópico inclui orientações básicas para implementar o controlo de documentos de conteúdo protegido com o SDK RMS 2.1.
- [Trabalhar com encriptação](working-with-encryption.md) – Este tópico descreve os nossos pacotes de encriptação e mostra como é possível utilizar alguns recortes de código.

 

## Tópicos relacionados ##
* [Descrição Geral](ad-rms-overview.md)
* [Como utilizar](how-to-use-msipc.md)
 

 


<!--HONumber=Apr16_HO4-->


