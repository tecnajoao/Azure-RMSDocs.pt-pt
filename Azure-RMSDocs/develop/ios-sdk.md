---
title: Configuração do iOS e OS X | Azure RMS
description: aplicações iOS e OS X podem utilizar o SDK RMS 4.2 para ativar a proteção de informações integrada na respetiva aplicação utilizando o AAD RM.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b31e5b72-e65e-450a-b1b8-d46e81e9fb34
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 6b3fe0994c27e26c505974cd4f5d96df252f2aa0
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259325"
---
# <a name="ios-and-os-x-setup"></a>Configuração do iOS e OS X

aplicações iOS e OS X podem utilizar o Microsoft Rights Management SDK 4.2 para ativar a proteção de informações integrada na respetiva aplicação utilizando o Azure Rights Management (Azure RMS).

Este tópico descreve como configurar o ambiente para criar as suas novas aplicações.

**Tenha em atenção**  este SDK não suporta o iPod Touch.


-   [Pré-requisitos](#prerequisites)
-   [Opcional](#optional)
-   [Configurar o ambiente de desenvolvimento](#configuring-your-development-environment)
-   [Consulte também](#see-also)

## <a name="prerequisites"></a>Pré-requisitos

Recomendamos o seguinte software no sistema de desenvolvimento:

-   O OS X é necessário para toda a programação iOS.
-   Xcode versão 6.0 e posterior

    O Xcode está disponível na [Mac App Store](https://developer.apple.com/technologies/mac/).

-   O pacote do SDK MS RMS 4.2 para iOS e OS X. Para obter mais informações, consulte [começar](get-started.md).

    Este SDK pode ser utilizado para a programação do iOS 7.0 e OS X 10.8 e posterior.

-   Biblioteca de autenticação: Recomendamos que utilize o [do Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx). No entanto, outras bibliotecas de autenticação que suportem o OAuth 2.0 também podem ser utilizadas.

    Para obter mais informações, consulte [ADAL para iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios) ou [ADAL para OS X](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/tree/OSXUniversal)

Consulte o tópico [Novidades](release-notes.md) para obter informações sobre atualizações de API, notas de versão e perguntas mais frequentes (FAQ).

## <a name="optional"></a>Opcional

A nossa biblioteca da interface de utilizador fornece uma IU reutilizável para operações de consumo e proteção para programadores que não pretendem criar a sua IU personalizada – [Biblioteca da IU e Aplicação de exemplo para iOS](https://github.com/AzureAD/rms-sdk-ui-for-ios).

## <a name="configuring-your-development-environment"></a>Configurar o ambiente de desenvolvimento

-   Para criar um novo projeto, no menu **Ficheiro**, clique em **Novo** e, em seguida, em **Projeto**.
-   Selecione **Aplicação de Vista Única**.

    ![Criar um novo projeto](../media/iOS-Project.png)

-   Introduza um nome e identificador para o novo projeto.

    ![Dar um nome ao projeto](../media/iOS-project-options.png)

-   Clique em **Seguinte** e selecione a localização do seu projeto.
-   Para adicionar a estrutura **MSRightsManagement** às Estruturas iOS, arraste a pasta .framework da pasta de instalação do SDK para a secção **Estruturas** do **Navegador de Projetos**.

    ![Definir localização](../media/ios-add-dependencies-01a.png)

-   Selecione o botão da opção **Criar grupos para quaisquer pastas adicionadas** e desmarque a caixa de verificação **Copiar itens para a pasta do grupo de destino (se necessário)**.

    Esta ação mantém a referência à pasta de instalação do SDK em vez de criar uma cópia.

    ![Definir a referência à pasta de instalação do SDK](../media/iOS-create-groups.png)

-   Para adicionar o SDK MS RMS 4.2 ao pacote de recursos, arraste o ficheiro Msrightsmanagementresources Bundle da pasta do Framework/Resources para o **estruturas** secção do seu navegador de projetos.

    ![Adicionar pacote de recursos](../media/iOS-add-resource-bundle-02a.png)

-   Tal como fez quando copiou a Estrutura, selecione o botão da opção **Criar grupos para quaisquer pastas adicionadas** e desmarque a caixa de verificação **Copiar itens para a pasta do grupo de destino (se necessário)**.
-   O SDK depende de outras estruturas, incluindo: **CoreData**, **MessageUI**, **SystemConfiguration**, **Libresolv** e **segurança**. Para adicionar estas estruturas, navegue até à secção **Estruturas e Bibliotecas Ligadas** do painel **Resumo** e expanda essa secção para as adicionar.

    As estruturas **UIKit** e **Foundation** são necessárias e estão geralmente presentes por predefinição.

    ![Adicionar recursos](../media/iOS-add-libraries.png)

-   Adicione o sinalizador **- ObjC** a **Outros Sinalizadores do Linker** nas **Definições de Criação** de destino.

    ![Adicionar definições de criação](../media/iOS-linker-flags.png)

-   Agora, o **Navegador de Projetos** deve ter um aspeto semelhante a esta árvore.

    ![Rever projeto](../media/iOS-verify-setup-01a.png)

-   Agora, está pronto para criar as suas novas aplicações iOS/OS X.

### <a name="see-also"></a>Consulte Também

* [Introdução](get-started.md)

* [Novidades](release-notes.md)

* [Conceitos e termos de programador](core-concepts.md)

* [Referência da API do iOS/OS X](https://msdn.microsoft.com/library/dn758306.aspx)
