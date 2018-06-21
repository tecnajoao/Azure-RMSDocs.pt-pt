---
title: Cliente do Azure Information Protection&colon; instalar e configurar
description: Informações para administradores sobre como implementar o cliente do Azure Information Protection em dispositivos móveis e computadores Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 54e66d8ffde33e3e73b24e39fa609686fa2601b0
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
ms.locfileid: "30204803"
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Cliente do Azure Information Protection: instalação e configuração para clientes

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Os computadores que executam o Office 2010 requerem o cliente do Azure Information Protection (ou a aplicação de partilha Rights Management) para se autenticarem no serviço Azure Rights Management e no serviço Azure Information Protection. Este cliente também é recomendado para todos os computadores Windows e dispositivos iOS e Android que suportam o serviço Azure Rights Management e o Azure Information Protection. 

O cliente do Azure Information Protection integra-se com aplicações do Office através da instalação de um suplemento do Office para que os utilizadores possam facilmente etiquetar e proteger documentos e e-mails diretamente do friso. De igual modo, este cliente proporciona proteção e etiquetagem a tipos de ficheiro que não são suportados nativamente pelo serviço Azure Rights Management, um visualizador para ficheiros protegidos e um site de controlo de documentos para os utilizadores controlarem e revogarem ficheiros protegidos por eles.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>O cliente do Azure Information Protection: instalação e configuração
Para uma instalação e configuração empresariais do cliente para o Windows, veja [Guia do administrador do Azure Information Protection](../rms-client/client-admin-guide.md).

> [!TIP]
> Se pretender instalar rapidamente e testar o cliente do Azure Information Protection para um único computador, veja [Transferir e instalar o cliente do Azure Information Protection](../rms-client/install-client-app.md)no [Guia do utilizador do cliente do Azure Information Protection](../rms-client/client-user-guide.md).

## <a name="the-azure-information-protection-client-for-ios-and-android-installation-and-management"></a>Cliente do Azure Information Protection para iOS e Android: instalação e configuração
Para instalar o cliente do Azure Information Protection para estas plataformas móveis populares, pode transferir a aplicação relevante através das ligações na [página do Microsoft Azure Information Protection](http://go.microsoft.com/fwlink/?LinkId=303970). Não é necessária qualquer configuração.

> [!NOTE]
> Para computadores Mac e dispositivos Windows Phone, as ligações a partir desta página transferem as aplicações de partilha RMS para dispositivos móveis. Estes dispositivos não suportam atualmente o cliente do Azure Information Protection.

**Se tiver o Microsoft Intune**: uma vez que a aplicação Azure Information Protection inclui o Microsoft Intune App Software Development Kit, quando os dispositivos iOS e Android forem inscritos pelo Intune, poderá implementar e gerir o Visualizador do Azure Information Protection para esses dispositivos. Para obter mais informações, consulte [Configurar e implementar políticas de gestão de aplicações móveis na consola do Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) na documentação do Intune. Para o Passo 2, utilize as instruções para publicar uma aplicação gerida por política.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


