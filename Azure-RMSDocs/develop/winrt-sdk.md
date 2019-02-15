---
title: Configuração da Loja Windows | Azure RMS
description: Aplicativos da Windows Store podem utilizar o Microsoft Rights Management SDK 4.2 para ativar a proteção de informações integrada na respetiva aplicação.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 2720aa0e-0d37-469f-be99-678bf95a9c51
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 18da97a07e7d65c69f88167cf440e864d3b29631
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56257608"
---
# <a name="windows-store-setup"></a>Configuração da Loja Windows

Aplicativos da Windows Store podem utilizar o Microsoft Rights Management SDK 4.2 para ativar a proteção de informações integrada na respetiva aplicação utilizando o Azure Active Directory Rights Management (AAD RM).

Este tópico descreve como configurar o ambiente para criar as suas novas aplicações.

-   [Pré-requisitos](#prerequisites)
-   [Opcional](#optional)
-   [Configurar o ambiente de desenvolvimento](#configuring-your-development-environment)
-   [Consulte também](#see-also)

## <a name="prerequisites"></a>Pré-requisitos


Tem de possuir o seguinte software no sistema de desenvolvimento:

-   O sistema operativo [Windows 8.1](https://windows.microsoft.com/windows-8/meet)
-   O [Windows SDK para Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)
-   Microsoft [Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/) ou superior, ou Visual Studio Express 2012, que está incluído no Windows SDK para Windows 8.0/8.1
-   O pacote do SDK MS RMS 4.2 para aplicações do Windows Store. Para obter mais informações, consulte [Introdução](get-started.md).
-   Biblioteca de autenticação: Recomendamos que utilize o [do Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx) e outras bibliotecas de autenticação podem ser utilizadas.

Consulte o tópico [Novidades](release-notes.md) para obter informações acerca de atualizações de API, informações de dispositivos e de ambiente, notas de versão e perguntas mais frequentes (FAQ).

## <a name="optional"></a>Opcional

A nossa biblioteca da interface de utilizador fornece uma IU reutilizável para operações de consumo e proteção para programadores que não pretendem criar a sua IU personalizada – [Biblioteca da IU para aplicações da Loja Windows](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore). Fornecemos também uma aplicação de exemplo de aplicação da Loja Windows – [Aplicação de exemplo do RMS para a Loja Windows](https://github.com/AzureADSamples/rms-samples-for-windowsstore).

## <a name="configuring-your-development-environment"></a>Configurar o ambiente de desenvolvimento


-   Abra o Visual Studio.
-   Clique em **Ficheiro**, clique em **Novo** e, em seguida, em **Projeto**.
-   Na caixa de diálogo **Novo Projeto**, clique em **Visual C\#** e selecione **Aplicação em Branco (Windows)** e, em seguida, clique em **OK**.

    ![Criar novo projeto](../media/winrtsetup-newproj.png)

-   No **Explorador de Soluções**, clique com o botão direito do rato no projeto e selecione **Adicionar Referência** para abrir a caixa de diálogo **Adicionar Referência**.

    ![Adicionar referência](../media/winrtsetup-addref.png)

-   Na caixa de diálogo **Adicionar Referência**, clique em **Procurar** e selecione o ficheiro *Microsoft.RightsManagment.dll*, situado na pasta da qual extraiu o pacote SDK.
-   **Aplicações Geridas** – para criar uma aplicação gerida, terá de adicionar esta referência; selecione **Windows 8.1**-&gt;**Extensões** e selecione a caixa **Pacote do Windows Visual C++ Runtime para Windows**

    ![Adicionar extensões](../media/winrtsetup-refmngr.png)

-   **Adicionar Capacidades** – A sua aplicação necessitará da capacidade “Internet (Cliente e Servidor)” para utilizar o SDK. Para adicionar esta capacidade à sua aplicação, abra o ficheiro *Package.appxmanifest* no projeto e navegue para o separador **Capacidades** a adicionar.

Agora, está pronto para criar as suas novas aplicações da Loja Windows.

### <a name="see-also"></a>Consulte Também

[Introdução](get-started.md)

[Novidades](release-notes.md)

[Conceitos e termos de programador](core-concepts.md)

[Windows 8](https://windows.microsoft.com/windows-8/meet)

[Visual Studio 2012](https://visualstudio.microsoft.com/vs/older-downloads/)

[Referência da API do Windows](https://msdn.microsoft.com/library/dn891914.aspx)
