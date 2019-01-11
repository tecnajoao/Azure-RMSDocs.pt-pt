---
title: Configurar o Visual Studio | Azure RMS
description: Instruções sobre como configurar um projeto do Visual Studio para utilizar o SDK RMS 2.1.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: f26400ba1230ef1b274fa04120c22995d2f6620c
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071493"
---
# <a name="configure-visual-studio"></a>Configurar o Visual Studio

Este tópico contém instruções sobre como configurar um projeto do Visual Studio para utilizar o Rights Management Services SDK 2.1.

## <a name="prerequisites"></a>Pré-requisitos

-   [Instalar o SDK](install-the-rms-sdk.md)

**Instruções**

### <a name="step-1-configure-a-visual-studio-project-to-use-rmssdk21"></a>Passo 1: Configurar um projeto do Visual Studio para utilizar o SDK RMS 2.1

Estas instruções são específicas para o Microsoft Visual Studio 2010. Se estiver a utilizar uma versão diferente do Microsoft Visual Studio, as caixas de diálogo das definições podem ter um aspeto ligeiramente diferente.

Estas instruções aplicam-se à criação de uma aplicação de 32 bits nativa.

1.  Adicione o SDK RMS 2.1 incluem o diretório ao seu projeto do Visual Studio 2010.

    Sob **propriedades de configuração** selecionar **VC + + Directories** e adicione o diretório, de inclusão do RMS SDK 2.1 **$ (msipcsdkdir)\\inc**, para o **Incluir diretórios** campo.

    ![Campo de diretórios de inclusão das propriedades de configuração](../media/include_directories.png)

2.  Adicione o diretório de bibliotecas do SDK RMS 2.1 ao projeto do Visual Studio 2010.

    Sob **propriedades de configuração** selecionar **VC + + Directories** e adicione o diretório de bibliotecas do SDK RMS 2.1, para o **Library Directories** campo para a sua plataforma.

    -   Para o Win32, utilize **$(MSIPCSDKDIR)\\lib**
    -   Para o x64, utilize **$(MSIPCSDKDIR)\\lib\\x64**

    ![Campo de diretórios de bibliotecas das propriedades de configuração](../media/library_directories.png)

3.  Adicione os ficheiros de biblioteca do SDK RMS 2.1 como dependências do Visual Studio 2010.

    Sob **Linker**, selecione **entrada** e adicione os ficheiros de biblioteca do SDK RMS 2.1 **Msipc. lib** e **Msipc\_s. lib**, para o **dependências adicionais** campo.

    ![Campo de dependências da biblioteca do linker](../media/additional_dependencies.png)

4.  Adicione o RMS SDK 2.1 dinâmica Link Library (DLL) como um DLL carregado com atraso.

    Sob **vinculador**, selecione **entrada**e adicione o ficheiro de RMS SDK 2.1 DLL **msipc. dll**para o **dll carregado com atraso** campo.

    ![Campo de bibliotecas carregadas com atraso do linker](../media/delay_loaded.png)

5.  Crie informações da versão para o binário resultante.

    Em **Explorador de Soluções**, selecione **Ficheiros de Recurso** e adicione o nome binário ao campo **NomeFicheiroOriginal**.

    ![Campo de ficheiros de recurso do explorador de soluções](../media/original_file_name.png)

## <a name="related-topics"></a>Tópicos relacionados

* [Instalar o SDK](install-the-rms-sdk.md)
