---
title: "Aplicação de partilha Rights Management&colon; instalação e configuração para clientes | Azure Information Protection"
description: "Informações para administradores sobre como implementar a aplicação de partilha Rights Management (RMS) em dispositivos móveis e computadores Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b9af5dc3-73d4-4147-b7ef-f6803b0d5216
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: f96641355da46eee85a828a6e5e417282883bac7


---

# <a name="rights-management-sharing-application-installation-and-configuration-for-clients"></a>Aplicação de partilha Rights Management: instalação e configuração para clientes

>*Aplica-se a: Azure Information Protection, Office 365*

A aplicação de partilha Rights Management (RMS) é necessária para os computadores cliente utilizarem o serviço Azure Rights Management com o Office 2010 e é recomendada para todos os computadores e dispositivos móveis que suportam o serviço Azure Rights Management a partir do Azure Information Protection. A aplicação de partilha RMS integra-se com aplicações do Office através da instalação de um suplemento do Office para que os utilizadores possam facilmente proteger ficheiros e e-mails diretamente do friso. De igual modo, proporciona proteção genérica a tipos de ficheiros que não são suportados nativamente pelo serviço Azure Rights Management e possibilita um site de controlo de documentos para os utilizadores controlarem e revogarem ficheiros protegidos por eles.

## <a name="the-rms-sharing-application-for-windows-installation-and-configuration"></a>A aplicação de partilha RMS para o Windows: instalação e configuração
Para instalar e configurar a aplicação de partilha RMS para Windows para uma implementação empresarial, consulte o [Guia do administrador da aplicação de partilha Rights Management](../rms-client/sharing-app-admin-guide.md).

> [!TIP]
> Se pretender instalar rapidamente e testar a aplicação de partilha RMS para um único computador, consulte [Transferir e instalar a aplicação de partilha Rights Management](../rms-client/install-sharing-app.md) no [Guia do utilizador da aplicação de partilha Rights Management](../rms-client/sharing-app-user-guide.md).

## <a name="the-rms-sharing-application-for-mobile-platforms-installation-and-management"></a>A aplicação de partilha RMS para plataformas móveis: instalação e gestão
Para instalar a aplicação de partilha RMS para plataformas móveis, pode transferir a aplicação relevante utilizando as ligações na [página Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970). Não é necessária nenhuma configuração para utilizar o serviço Azure Rights Management com esta aplicação.

> [!NOTE]
> A aplicação de partilha RMS para iOS e Android foi substituída pela aplicação Azure Information Protection.

**Se tiver o Microsoft Intune**: uma vez que a aplicação Azure Information Protection inclui o Microsoft Intune App Software Development Kit, quando os dispositivos iOS e Android forem inscritos pelo Intune, poderá implementar e gerir a aplicação Azure Information Protection para esses dispositivos. Para obter mais informações, consulte [Configurar e implementar políticas de gestão de aplicações móveis na consola do Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) na documentação do Intune. Para o Passo 2, utilize as instruções para publicar uma aplicação gerida por política.






<!--HONumber=Nov16_HO2-->


