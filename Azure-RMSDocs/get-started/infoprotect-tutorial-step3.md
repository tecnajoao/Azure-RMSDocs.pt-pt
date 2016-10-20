---
title: "Passo 3 do tutorial de início rápido | Azure Information Protection"
description: "Passo 3 de um tutorial de introdução com uma duração de aproximadamente 30 minutos, para experimentar rapidamente o Microsoft Azure Information Protection na sua organização."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: b5c87669c965d1e67b47dcfbd8ba97f1da41d104
ms.openlocfilehash: 042e168452d2b5cbc1eeec4fc06a3b0f137a5caf


---

# Passo 3: instalar o cliente e a aplicação 

>*Aplica-se a: Azure Information Protection*

Neste passo, irá começar por instalar o cliente do Azure Information Protection, para que a política que acabou de configurar seja transferida para um PC com Windows e apresente as etiquetas em aplicações do Office.

Em segundo lugar, irá instalar a aplicação de partilha Rights Management, para poder partilhar de forma segura um documento por e-mail e, em seguida, controlar como este é utilizado. 

Ambas as instalações integram-se com as aplicações do Office e, atualmente, tem de as instalar em separado.


## Instalar o cliente do Azure Information Protection

1. Num PC com o Office instalado (mas sem o Word aberto), [transfira o cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) a partir do Centro de transferências da Microsoft. 

2. Execute o ficheiro **AzInfoProtection.exe** e siga as instruções para instalar o cliente.

    Para este tutorial, não interessa se selecionou a opção para instalar uma política de demonstração, porque a nossa política que transferimos vai ser transferida do Azure e substituir a política de demonstração, caso esteja instalada. No entanto, pode utilizar a opção de política de demonstração caso pretenda experimentar as etiquetas predefinidas sem ligar ao Azure Information Protection. 

## Instalar a aplicação de partilha Rights Management 

1. Aceda à página do [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft.

2. Na secção **Computadores**, clique no ícone da **Aplicação RMS para Windows** e guarde o ficheiro **Setup.exe** para instalar a aplicação de partilha Microsoft Rights Management.

3. Na página **Configurar o Microsoft RMS**, clique em **Seguinte** e aguarde até que a instalação esteja concluída. Em seguida, clique em **Reiniciar** se lhe for pedido para reiniciar o computador ou clique em **Fechar** para concluir a instalação.


## Verificar as instalações

Verifique se estas instalações foram bem-sucedidas ao abrir o Word e um novo documento em branco (não o guarde por agora). Se lhe for pedido para introduzir o seu nome de utilizador e palavra-passe, introduza os detalhes da sua conta de administrador global. 

Quando o documento for carregado, verá três novas opções:

- No separador **Base**, um novo grupo **Proteção**, com um botão com a etiqueta **Proteger**.

    Clique em **Proteger** > **Ajuda e comentários** e, na caixa de diálogo **Microsoft Azure Information Protection**, confirme o estado do cliente. Deverá ser apresentado **A política de Information Protection está instalada** e um tempo de ligação recente. Verifique se o seu nome de utilizador apresentado está correto para o seu inquilino.

- Além disso, no separador **Base**, um novo grupo **RMS**, com um botão com a etiqueta **Partilhar Protegido**.

- Uma nova barra abaixo do friso; a barra do Information Protection. Apresenta o título **Sensibilidade** e a etiqueta predefinida que configurámos de **Interna**. 
    
    ![Tutorial de início rápido do Azure Information Protection, passo 3 - cliente instalado](../media/word2013-callouts2.png)

Agora está pronto para ver o Azure Information Protection em ação.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Sobre instalar o cliente do Azure Information Protection|[Instalar o cliente do Azure Information Protection](../rms-client/info-protect-client.md)|
|Acerca da instalação da aplicação de partilha do Rights Management e instruções de utilizador|[Guia do utilizador da aplicação de partilha Rights Management](../rms-client/sharing-app-user-guide.md)|
|Acerca de uma instalação com script da aplicação de partilha Rights Management para Windows e mais informações técnicas|[Guia do administrador da aplicação de partilha Rights Management](../rms-client/sharing-app-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; Passo 2](infoprotect-tutorial-step2.md)
[Passo 4 &#187;](infoprotect-tutorial-step4.md)


<!--HONumber=Sep16_HO4-->


