---
title: Configuração do Windows Phone | Azure RMS
description: Aplicativos do Windows Phone podem utilizar o Microsoft Rights Management SDK 4.2 para ativar a proteção de informações integrada na respetiva aplicação.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e25a446e-b977-4736-9c65-7711171fb0e1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8591e48a9d90f893c1158e4c8b582ad759356a8f
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56257761"
---
# <a name="windows-phone-setup"></a>Configuração do Windows Phone


Aplicativos do Windows Phone podem utilizar o Microsoft Rights Management SDK 4.2 para ativar a proteção de informações integrada na respetiva aplicação utilizando o Azure Active Directory Rights Management (AAD RM).

Este tópico descreve como configurar o ambiente para criar as suas novas aplicações.

-   [Pré-requisitos](#prerequisites)
-   [Configurar o ambiente de desenvolvimento](#configuring-your-development-environment)
-   [Consulte também](#see-also)

## <a name="prerequisites"></a>Pré-requisitos


Tem de possuir o seguinte software no sistema de desenvolvimento:

-   O sistema operativo [Windows 8.1](https://windows.microsoft.com/windows-8/meet).
-   [Ferramentas de Desenvolvimento do Windows Phone 8.1 (SDK)](https://developer.microsoft.com/windows/downloads/sdk-archive)
-   Microsoft [Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/) ou superior, ou Visual Studio Express 2012, que está incluído no Windows Phone SDK 8.0/8.1
-   O pacote do SDK MS RMS 4.2 para Windows Phone. Para obter mais informações, consulte [Introdução](get-started.md).
-   Biblioteca de autenticação: Recomendamos que utilize o [do Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx) e outras bibliotecas de autenticação podem ser utilizadas.

Consulte o tópico [Novidades](release-notes.md) para obter informações acerca de atualizações de API, informações de dispositivos e de ambiente, notas de versão e perguntas mais frequentes (FAQ).

Reveja as informações no guia de [desenvolvimento do Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/ff402535.aspx) no Windows Phone Dev Center.

## <a name="configuring-your-development-environment"></a>Configurar o ambiente de desenvolvimento


-   Abra o *Visual Studio*.
-   Clique em **Ficheiro**. No menu **Ficheiro**, clique em **Novo** e, em seguida, em **Projeto**.
-   Na caixa de diálogo **Novo Projeto**, selecione **Visual C\#**, selecione **Aplicação em Branco (Windows Phone)** e, em seguida, clique em **OK**.

    ![Criar novo projeto](../media/wpsetup-newproj.png)

-   No Explorador de Soluções, clique com o botão direito do rato no projeto e, em seguida, selecione **Adicionar Referência** para abrir a caixa de diálogo **Adicionar Referência**.

    ![Adicionar referência](../media/wpsetup-addref.png)

-   Clique em **Procurar** na parte inferior esquerda da caixa de diálogo **Adicionar Referência** e selecione o ficheiro *Microsoft.RightsManagment.dll*, situado na pasta da qual extraiu o pacote.
-   **Aplicações Geridas** – para criar uma aplicação gerida, terá de adicionar esta referência; selecione **Windows 8.1**-&gt;**Extensões** e selecione a caixa **Pacote do Windows Visual C++ Runtime para Windows**

    ![Adicionar extensões](../media/wpsetup-refmngr.png)

-   **Adicionar Capacidades** – A sua aplicação necessitará da capacidade “Internet (Cliente e Servidor)” para utilizar o SDK. Para adicionar esta capacidade à sua aplicação, abra o ficheiro *Package.appxmanifest* no projeto e navegue para o separador **Capacidades** a adicionar.

Agora, está pronto para criar as suas novas aplicações do Windows Phone.

### <a name="see-also"></a>Veja Também

[Introdução](get-started.md)

[Novidades](release-notes.md)

[Conceitos principais](core-concepts.md)

[Desenvolvimento do Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/ff402535.aspx)

[Referência da API do Windows](https://msdn.microsoft.com/library/dn891914.aspx)

[Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/)

[Windows Phone SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)
