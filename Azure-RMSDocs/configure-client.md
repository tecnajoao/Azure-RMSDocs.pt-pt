---
title: Cliente do Azure Information Protection&colon; instalar e configurar
description: Informações para administradores sobre como implementar o cliente do Azure Information Protection em dispositivos móveis e computadores Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/17/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 10fc4c158cd4669b67c28e4968b0a3c4e7b889ad
ms.sourcegitcommit: b1e08bc29d50187532f00dc215ab331e0a7dbebe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/28/2019
ms.locfileid: "55146847"
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Cliente do Azure Information Protection: Instalação e configuração para clientes

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Os computadores que executam o Office 2010 requerem o cliente do Azure Information Protection (ou a aplicação de partilha Rights Management) para se autenticarem no serviço Azure Rights Management e no serviço Azure Information Protection. Este cliente também é recomendado para todos os computadores Windows e dispositivos iOS e Android que suportam o serviço Azure Rights Management e o Azure Information Protection. 

O cliente do Azure Information Protection integra-se com aplicações do Office através da instalação de um suplemento do Office para que os utilizadores possam facilmente etiquetar e proteger documentos e e-mails diretamente do friso. De igual modo, este cliente proporciona proteção e etiquetagem a tipos de ficheiro que não são suportados nativamente pelo serviço Azure Rights Management, um visualizador para ficheiros protegidos e um site de controlo de documentos para os utilizadores controlarem e revogarem ficheiros protegidos por eles.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>O cliente do Azure Information Protection para Windows: Instalação e configuração
Para uma instalação e configuração empresariais do cliente para o Windows, veja [Guia do administrador do Azure Information Protection](./rms-client/client-admin-guide.md).

> [!TIP]
> Se pretender instalar rapidamente e testar o cliente do Azure Information Protection para um único computador, veja [Transferir e instalar o cliente do Azure Information Protection](./rms-client/install-client-app.md)no [Guia do utilizador do cliente do Azure Information Protection](./rms-client/client-user-guide.md).

## <a name="the-azure-information-protection-client-for-ios-and-android-installation-and-management"></a>O cliente do Azure Information Protection para iOS e Android: Instalação e gestão
Para instalar o cliente do Azure Information Protection para estas plataformas móveis populares, pode transferir a aplicação relevante através das ligações na [página do Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970). Não é necessária qualquer configuração.

> [!NOTE]
> Para computadores Mac, ligações a partir desta página transferem as aplicações para dispositivos móveis de partilha RMS. Estes computadores não suportam o cliente do Azure Information Protection.

**Se tiver o Microsoft Intune**: Uma vez que a aplicação Azure Information Protection foi criada usando o Microsoft Intune App Software Development Kit, quando os dispositivos iOS e Android forem inscritos pelo Intune, pode implementar e gerir a aplicação Azure Information Protection para estes dispositivos:

- Para implementar a aplicação, [adicionar a aplicação Azure Information Protection ao Intune](/intune/apps-add) e [atribuí-la aos utilizadores](/intune/apps-deploy).

- Para gerir a aplicação, utilize do Intune [políticas de proteção de aplicações](/intune/app-protection-policies).

## <a name="next-steps"></a>Passos Seguintes

Depois de ter instalado e configurado o cliente do Azure Information Protection, poderá ter de obter mais informações sobre como o cliente interpreta os direitos de utilização diferentes que podem ser utilizados para proteger documentos e e-mails. Para obter mais informações, veja [Configuração de direitos de utilização para o Azure Rights Management](configure-usage-rights.md).
