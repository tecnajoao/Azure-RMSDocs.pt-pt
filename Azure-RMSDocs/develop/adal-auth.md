---
title: Configurar a autenticação ADAL na aplicação – AIP
description: Passos para configurar a aplicação Azure Information Protection para utilizar a autenticação baseada em ADAL do Azure
keywords: autenticação, RMS, ADAL, Information Protection,
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: dd988c808de661b025d23e5fe73fb9f453fced10
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54070643"
---
# <a name="configure-your-app-for-adal-authentication"></a>Configurar a autenticação ADAL na sua aplicação

Este tópico descreve os passos para configurar a sua aplicação para a autenticação baseada no Azure Active Directory Authentication Library (ADAL).

## <a name="azure-authentication-setup"></a>Configuração da autenticação do Azure

Será necessário o seguinte:

- Uma [subscrição do Microsoft Azure](https://azure.microsoft.com/) (uma avaliação gratuita é suficiente). Para obter mais informações, consulte [como os utilizadores inscrevem no RMS para indivíduos](../rms-for-individuals-user-sign-up.md)
- Uma subscrição do Microsoft Azure Rights Management (uma conta [RMS para Indivíduos](https://technet.microsoft.com/library/dn592127.aspx) gratuita é suficiente).

> [!NOTE]
> Pergunte ao seu Administrador de TI se possui ou não uma subscrição do Microsoft Azure Rights Management e, em seguida, peça ao Administrador de TI para realizar os passos abaixo. Se a sua organização não tiver uma subscrição, deve pedir ao seu administrador de TI para criar uma. Além disso, o Administrador de TI deve subscrever com uma conta *Escolar ou profissional*, em vez de uma *conta Microsoft* (por exemplo, Hotmail).

Após a inscrição no Microsoft Azure:

- Inicie sessão no [Portal de Gestão do Azure](https://manage.windowsazure.com) para a organização que utiliza uma conta com privilégios administrativos.

![Início de sessão no Azure](../media/AzurePortalLogin.png)

- Navegue para baixo até à aplicação do **Active Directory**, no lado esquerdo do portal.

![Selecionar Active Directory](../media/AzureADPick.png)

- Se ainda não tiver criado um diretório, escolha o botão **Novo**, situado no canto inferior esquerdo do portal.

![Selecionar NOVO](../media/AzureNewBtn.png)

- Selecione o separador **Rights Management** e certifique-se de que o **Estado do Rights Management** é **Ativo**, **Desconhecido** ou **Não Autorizado**. Se o estado for **Inativo**, escolha o botão **Ativar**, na parte inferior central do portal, e confirme a seleção.

![Escolher ATIVAR](../media/RMTab.png)

- Agora, crie uma nova *Aplicação Nativa* no diretório ao selecionar o diretório e ao escolher Aplicações.

![Selecionar APLICAÇÕES](../media/CreateNativeApp.png)

- Em seguida, escolha o botão **Adicionar** situado na parte inferior central do portal.

![Selecionar ADICIONAR](../media/AddAppBtn.png)

- Na linha de comandos, escolha **Adicionar uma aplicação que a minha organização está a desenvolver**.

![Selecionar Adicionar uma aplicação que a minha organização está a desenvolver](../media/AddAnAppPick.png)

- Atribua um nome à aplicação ao selecionar **APLICAÇÃO CLIENTE NATIVA** e escolher o botão **Seguinte**.

![Atribuir um nome à aplicação](../media/TellUsInput.png)

- Adicione um URI de redirecionamento e selecione seguinte.
  O URI redirecionamento tem de ser um URI válido e exclusivo para o seu diretório. Por exemplo, pode utilizar algo como `https://contoso.azurewebsites.net/.auth/login/done`.

![Adicionar URI de redirecionamento](../media/RedirectURI.png)

- Selecione a aplicação no diretório e escolha **CONFIGURAR**.

![Escolher CONFIGURAR](../media/ConfigYourApp.png)

>[!NOTE]
> Copie a **ID DE CLIENTE** e o **URI DE REDIRECIONAMENTO** e armazene-os para utilização futura quando configurar o cliente RMS.

- Navegue até à parte inferior das definições da aplicação e escolha o botão **Adicionar aplicação** em **permissões para outras aplicações**.

>[!NOTE]
> As **Permissões de Delegado** apresentadas para o Windows Azure Active Directory estão corretas por predefinição – deve ser selecionada apenas a opção **Iniciar sessão e ler o perfil de utilizador**.

![Selecionar Adicionar aplicação](../media/PermissionsToOtherBtn.png)

- Selecione o sinal de adição junto de **Microsoft Rights Management**.

![Selecionar o botão +](../media/ChoosePlusBtn.png)

- Agora, selecione a marca de verificação situada no canto inferior esquerdo da caixa de diálogo.

![Escolher a marca de verificação](../media/choosecheck01.png)

- Está agora preparado para adicionar uma dependência à sua aplicação do Azure RMS. Para adicionar a dependência, selecione a nova entrada do **Microsoft Rights Management Services** em **permissões para outras aplicações** e escolha a caixa de verificação **Criar e aceder a conteúdo protegido para utilizadores** na pasta de depósito **Permissões delegadas:**.

![Permissões de configuração](../media/AddDependency.png)

- Guarde a aplicação para manter as alterações escolhendo o ícone **Guardar** situado na parte inferior central do portal.

![Selecionar GUARDAR](../media/SaveApplication.png)

