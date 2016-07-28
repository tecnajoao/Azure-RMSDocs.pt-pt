---
title: "Tutorial de início rápido do Azure Information Protection, passo 1 | Azure Rights Management"
description: "Passo 1 de um tutorial de apresentação para experimentar rapidamente o Microsoft Azure Information Protection na sua organização com apenas 4 passos que devem demorar menos de 10 minutos."
author: cabailey
manager: mbaldwin
ms.date: 07/11/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
translationtype: Human Translation
ms.sourcegitcommit: 78f0f07271414fb646f996e7273343f2abf8852b
ms.openlocfilehash: 633b24d0c23cbbee88a2647aaa9defe376ccb40e


---

# Passo 1: ativar o serviço Rights Management
 
*Aplica-se a: pré-visualização do Azure Information Protection*

> [!NOTE]
>Se pretender apenas classificar os dados e não protegê-lo com o Azure Rights Management, ou se já tiver ativado o Azure Rights Management para o seu inquilino - vá diretamente para o [passo seguinte](infoprotect-tutorial-step2.md). 

Quando o Azure Rights Management é ativado, pode proteger os seus documentos e ficheiros mais confidenciais depois de terem sido classificados. Para ativar o Azure Rights Management, pode utilizar o centro de administração do Office 365 ou o portal clássico do Azure:

-   Se tiver uma subscrição do Office 365 que inclua o Azure Rights Management ou uma subscrição do Office 365 que exclua o Azure Rights Management, mas tiver uma subscrição do Azure RMS Premium: **utilize o centro de administração do Office 365**.

-   Se não tiver uma subscrição do Office 365: **utilize o portal clássico do Azure**.

### Para ativar o Rights Management a partir do centro de administração clássico do Office 365

> [!NOTE]
> Se estiver a utilizar o **pré-visualização do centro de administração do Office 365** em vez do centro de administração clássico do Office 365, pode utilizar as instruções em [Como ativar o Azure Rights Management a partir da pré-visualização do centro de administração do Office 365](../deploy-use/activate-office365-preview.md) ou mudar para a versão clássica para utilizar estas instruções. Para mudar, clique em **Ir para o centro de administração antigo** na página **Base** após ter iniciado sessão.

1.  Vá para o [portal do Office 365](https://portal.office.com/) e inicie sessão com a sua conta de administrador global do Office 365.

2.  Se o centro de administração do Office 365 não for apresentado automaticamente, selecione o ícone do iniciador de aplicações no canto superior esquerdo e escolha **Administrador**. O mosaico **Administrador** só é apresentado para os administradores do Office 365.

  > [!TIP]
  > Para obter ajuda acerca do centro de administração, consulte [Acerca do centro de administração do Office 365 – Ajuda de Administração](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  No painel esquerdo, expanda **DEFINIÇÕES DE SERVIÇO**.

4.  Clique em **Rights Management**.

5.  Na página **RIGHTS MANAGEMENT**, clique em **Gerir**.

6.  Na página **rights management**, clique em **ativar**.

7.  Quando lhe for perguntado **Pretende ativar o Rights Management?**, clique em **ativar**.

Já deverá estar visível **O Rights Management encontra-se ativado** e a opção para desativar (poderá ter de atualizar manualmente a página)

Neste momento, não clique em **funcionalidades avançadas**. Isto leva-o para o portal clássico do Azure onde poderá configurar modelos personalizados, que não são necessários para este tutorial. Em vez disso, pode fechar o centro de administração do Office 365.

### Para ativar o Rights Management a partir do portal clássico do Azure

1.  Vá para o [portal clássico do Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081) e inicie sessão com a sua conta de administrador global do Azure Active Directory.

2.  No painel esquerdo, clique em **ACTIVE DIRECTORY**.

3.  Na página **active directory**, clique em **RIGHTS MANAGEMENT**.

4.  Selecione o diretório a gerir para o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], clique em **ATIVAR** e confirme a ação.

O **ESTADO DO RIGHTS MANAGEMENT** deverá agora apresentar **Ativo** e a opção **ATIVAR** é substituída por **DESATIVAR**.

Embora seja possível configurar outras opções do Rights Management no portal, estas não são necessárias para este tutorial, pelo que pode fechar o portal clássico do Azure.

É tudo o que precisa de fazer neste primeiro passo. O serviço de Azure Rights Management está ativado para que mais tarde, durante o tutorial, possa selecionar um dos modelos predefinidos do Azure Rights Management para proteger documentos e e-mails classificados como confidenciais.

Para uma implementação de produção, provavelmente, será útil configurar modelos personalizados como suplemento ou em vez de modelos predefinidos do Azure Rights Management. No entanto, os modelos personalizados não são necessários para este tutorial, pelo que pode ir para o passo 2.

|Se pretender mais informações|Informações adicionais|
|--------------------------------|--------------------------|
|Como ativar o Azure Rights Management|[Ativar o Azure Rights Management](../deploy-use/activate-service.md)|
|Acerca dos modelos predefinidos e de como criar modelos novos e personalizados|[Configurar modelos personalizados para o Azure Rights Management](../deploy-use/configure-custom-templates.md)|

>[!div class="step-by-step"]
[&#171; Introdução](infoprotect-quick-start-tutorial.md)
[Passo 2 &#187;](infoprotect-tutorial-step2.md)



<!--HONumber=Jul16_HO3-->


