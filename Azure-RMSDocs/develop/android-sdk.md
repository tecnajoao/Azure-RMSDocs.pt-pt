---
title: Configuração do Android | Azure RMS
description: Aplicações Android podem utilizar o Microsoft Rights Management SDK 4.2 para ativar a proteção de informações integrada nas respetivas aplicações.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 986f6932-159b-4791-bd1a-7640a83ee792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 2c7ef53f48f1207afa5cb22b0623230fbd191729
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259454"
---
# <a name="android-setup"></a>Configuração do Android

Aplicações Android podem utilizar o Microsoft Rights Management SDK 4.2 para ativar a proteção de informações integrada nas respetivas aplicações ao utilizar o Azure Active Directory Rights Management (AAD RM).

Este tópico descreve como configurar o ambiente para criar as suas novas aplicações.

-   [Pré-requisitos](#prerequisites)
-   [Opcional](#optional)
-   [Configurar o ambiente de desenvolvimento](#configuring-your-development-environment)
-   [Consulte também](#see-also)

## <a name="prerequisites"></a>Pré-requisitos

Recomendamos o seguinte software no sistema de desenvolvimento:

-   Sistema operativo Windows ou OS X para executar o ambiente de desenvolvimento [Eclipse](https://www.oracle.com/technetwork/java/javase/downloads/jre7-downloads-1880261.html).
-   Este guia pressupõe que está a utilizar o SDK Eclipse com o Eclipse Juno 4.2 ou superior e que está a utilizar uma instalação predefinida.
-   Java 1.6 ou superior.
-   [Plug-in Ferramentas do Programador do Android (ADT)](https://developer.android.com/studio/install). NOTA – poderá ser-lhe pedido para reiniciar o Eclipse para concluir a instalação.

     

-   O pacote do SDK MS RMS 4.2 para Android. Para obter mais informações, consulte [Introdução](get-started.md).

    Este SDK pode ser utilizado para desenvolver para o Android 4.0.3 (nível de API 15) e posterior.

-   Biblioteca de autenticação: Recomendamos que utilize o [do Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx). No entanto, outras bibliotecas de autenticação que suportem o OAuth 2.0 também podem ser utilizadas.

    Para obter mais informações, consulte [ADAL para Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)

    **Tenha em atenção**  se o seu aplicativo não esteja a utilizar a biblioteca ADAL como a biblioteca de autenticação OAuth 2.0, deve rever esta orientação do Android, [algumas ideias Securerandom](https://android-developers.blogspot.com/2013/08/some-securerandom-thoughts.html).

     

Consulte o tópico [Novidades](release-notes.md) para obter informações sobre atualizações de API, notas de versão e perguntas mais frequentes (FAQ).

## <a name="optional"></a>Opcional

A nossa biblioteca da interface de utilizador fornece uma IU reutilizável para operações de consumo e proteção para programadores que não pretendem criar a sua IU personalizada – [Biblioteca da IU e Aplicação de exemplo para Android](https://github.com/AzureAD/rms-sdk-ui-for-android).

## <a name="configuring-your-development-environment"></a>Configurar o ambiente de desenvolvimento

**Tenha em atenção**  versão de pré-visualização do SDK do MS RMS 4.2: Nesta versão de pré-visualização, as capturas de ecrã não foram atualizadas para mostrar a alteração no nome dos caminhos de com/microsoft/protection para com/microsoft/rightsmanagment. No entanto, o texto foi atualizado.

 
-   Abra o ambiente de desenvolvimento Eclipse.
-   Para criar um novo projeto de Aplicação Android, no menu **Ficheiro**, clique em **Novo**, clique em **Projeto** e selecione **Projeto de Aplicação Android**.

    ![Criar uma nova aplicação Android](../media/Android-setup-01c.png)

-   Introduza o nome da aplicação. O nome do projeto e o nome do pacote é preenchido com base no nome da aplicação.
-   Clique em **Seguinte** e selecione onde pretende criar a área de trabalho.

    ![Introduzir o nome da aplicação](../media/Android-setup-02a.jpg)

-   Clique em **Seguinte** e selecione um ícone para a aplicação.

    ![Selecionar um ícone para a aplicação](../media/Android-setup-03.png)

-   Clique em **Seguinte** e selecione **Atividade em Branco** para criar a atividade.

    ![Criar a atividade](../media/Android-setup-04.png)

-   Clique em **Seguinte** e atribua um nome à atividade. Pode deixar *MainActivity* como o nome predefinido com um nome de esquema de *activity\_main*.

    ![Atribuir um nome à atividade](../media/Android-setup-05a.jpg)

-   Clique em **Concluir**.

    ![Concluir a criação](../media/Android-setup-06.jpg)

-   O projeto foi criado, em conjunto com a classe de atividade principal *MainActivity.java*.

**Referenciar o SDK**

- Navegue para a pasta onde extraiu o *adrms\_android\_sdk.zip*. Na pasta “SDK > com > microsoft > rightsmanagement”, certifique-se de que os ficheiros *.classpath*, *.project* e *project.properties* não estão marcados como só de leitura.
- Para referenciar o SDK, tem de importá-lo para área de trabalho.

  No Eclipse, clique em **Ficheiro**. No menu **Ficheiro**, clique em **Importar**. Na caixa de diálogo **Importar**, selecione **Android/Código Android existente na Área de Trabalho**.

  ![Importá-lo para a área de trabalho](../media/Android-setup-07.png)

- Clique em **Seguinte**. Navegue para a pasta onde extraiu o *adrms\_android\_sdk.zip*. O SDK deve aparecer na lista de como **com.microsoft.rightsmanagement**.

  ![Navegar para selecionar a pasta](../media/Android-setup-08c.jpg)

- Quando clica em **Concluir**, o projeto do SDK aparece como colateral da sua aplicação criada anteriormente.

  ![O projeto do SDK aparece como colateral da aplicação](../media/Android-setup-09.jpg)

- Clique no botão direito do rato no ícone **Projeto** e veja as propriedades do projeto.
- Navegue para o separador **Android**.
- Clique em **Adicionar** e selecione a biblioteca *com.microsoft.rightsmanagement* na área de trabalho.

  ![Adicionar a biblioteca](../media/Android-setup-10b.jpg)

- Clique em **OK**.

  Uma vez que o SDK MS RMS 4.2 liga ao AAD RM, é necessário conceder **INTERNET** e **ACCESS\_NETWORK\_STATE** à aplicação. Para tal, abra o ficheiro *AndroidManifest.xml* na raiz do projeto.

  Para adicionar as permissões, clique em **Adicionar** e selecione **Utiliza Permissões**.

  ![Adicionar permissões](../media/Android-setup-11d.jpg)

- Pode verificar o passo do manifesto ao visualizar o manifesto na vista de editor de texto. Certifique-se de que as linhas seguintes são apresentadas:

  ```
  <uses-sdk
       android:minSdkVersion="15"
       android:targetSdkVersion="19"/>
  <uses-permission android:name="android.permission.INTERNET"/>
  <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
  <uses-permission/>
  ```

**Tenha em atenção**  o SDK utiliza o *android.support.v4*

-   Agora, está pronto para criar as suas novas aplicações Android.

### <a name="see-also"></a>Veja Também

[Introdução](get-started.md)

[Novidades](release-notes.md)

[Conceitos e termos de programador](core-concepts.md)

[Referência da API do Android](https://msdn.microsoft.com/library/dn758245.aspx)


