---
title: Cliente de proteção de informações do Azure - instalar & Configurar
description: Informações para administradores sobre como implementar o cliente do Azure Information Protection em dispositivos móveis e computadores Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/05/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 8b6735715bbd7ac86e75838683e14efb8864ffc3
ms.sourcegitcommit: e8b4a09db9aad7f6540b4c2fd92b1e8008c999b1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737244"
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Cliente do Azure Information Protection: Instalação e configuração para clientes

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Computadores que executam o Office 2010 requerem o cliente do Azure Information Protection autenticar para o serviço Azure Rights Management e o serviço Azure Information Protection. Este cliente também é recomendado para todos os computadores Windows e dispositivos iOS e Android que suportam o serviço Azure Rights Management e o Azure Information Protection. 

O cliente do Azure Information Protection integra-se com aplicações do Office através da instalação de um suplemento do Office para que os utilizadores possam facilmente etiquetar e proteger documentos e e-mails diretamente do friso. De igual modo, este cliente proporciona proteção e etiquetagem a tipos de ficheiro que não são suportados nativamente pelo serviço Azure Rights Management, um visualizador para ficheiros protegidos e um site de controlo de documentos para os utilizadores controlarem e revogarem ficheiros protegidos por eles.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>O cliente do Azure Information Protection para Windows: Instalação e configuração

Para uma instalação e configuração empresariais do cliente para o Windows, veja [Guia do administrador do Azure Information Protection](./rms-client/client-admin-guide.md).

> [!TIP]
> Se pretender instalar rapidamente e testar o cliente do Azure Information Protection para um único computador, veja [Transferir e instalar o cliente do Azure Information Protection](./rms-client/install-client-app.md)no [Guia do utilizador do cliente do Azure Information Protection](./rms-client/client-user-guide.md).

## <a name="the-azure-information-protection-client-for-ios-and-android-installation-and-management"></a>O cliente do Azure Information Protection para iOS e Android: Instalação e gestão

Para instalar o cliente do Azure Information Protection para estas plataformas móveis populares, pode transferir a aplicação relevante através das ligações na [página do Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970). Não é necessária qualquer configuração.

> [!NOTE]
> Para computadores Mac, ligações a partir desta página transferem a aplicação de partilha RMS. Estes computadores não suportam o cliente do Azure Information Protection.

### <a name="integration-with-intune"></a>Integração com o Intune

Uma vez que a aplicação Azure Information Protection utiliza o Microsoft Intune App Software Development Kit, quando os dispositivos iOS e Android forem inscritos pelo Intune, pode implementar e gerir a aplicação Azure Information Protection para estes dispositivos:

1. [Adicionar o Azure Information Protection aplicação ao Intune](/intune/apps-add) 

2. Efetue uma ou ambas das seguintes ações:
    
    - Implementar a aplicação por [atribuí-lo para os utilizadores](/intune/apps-deploy)
    
    - Gerir a aplicação com [políticas de proteção de aplicações](/intune/app-protection-policies)

Informações adicionais sobre o quando adicionar a aplicação Azure Information Protection para o Intune:

- Para iOS: Procurar e adicionar a aplicação do Intune.

- Para Android: Ao adicionar a aplicação, utilize o seguinte procedimento **URL da Appstore**:
        
        https://play.google.com/store/apps/details?id=com.microsoft.ipviewer

Quando a aplicação Azure Information Protection está configurada para uma política de proteção de aplicações para dispositivos Android, além de abertura de texto protegido, imagens e documentos PDF, esta aplicação também pode abrir arquivos de áudio e vídeo. Para obter mais informações, consulte [visualizar os arquivos de suporte de dados com a aplicação Azure Information Protection](/intune/end-user-mam-apps-android#view-media-files-with-the-azure-information-protection-app).

## <a name="next-steps"></a>Passos Seguintes

Depois de ter instalado e configurado o cliente do Azure Information Protection, poderá ter de obter mais informações sobre como o cliente interpreta os direitos de utilização diferentes que podem ser utilizados para proteger documentos e e-mails. Para obter mais informações, veja [Configuração de direitos de utilização para o Azure Rights Management](configure-usage-rights.md).
