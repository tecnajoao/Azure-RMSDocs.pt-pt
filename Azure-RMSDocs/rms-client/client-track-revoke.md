---
title: "Controlar e revogar documentos – AIP"
description: "Depois de ter protegido os seus documentos, pode controlar a forma como as pessoas os utilizam. Se necessário, também poderá revogar o acesso a esses documentos se não pretender que as pessoas continuem a poder lê-los."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 710e614f9ba6e5732046cfb85d3463875ab34566
ms.sourcegitcommit: d5ce1bce5e63b3e510033ff9d4d246dd3511ed7c
translationtype: HT
---
# <a name="track-and-revoke-your-documents-when-you-use-azure-information-protection"></a>Controlar e revogar os documentos quando utiliza o Azure Information Protection

>*Aplica-se a: Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

Após proteger os seus documentos com o Azure Information Protection, pode controlar como as pessoas utilizam esses documentos. Se necessário, também poderá revogar o acesso a estes se não pretender que as pessoas continuem a poder lê-los. Para tal, utilize o **site de controlo de documentos**, ao qual pode aceder a partir de computadores com o Windows, computadores Mac e até mesmo telemóveis e tablets.

Ao aceder a este site, inicie sessão para controlar os seus documentos. Desde que a sua organização tenha uma [subscrição que suporte a revogação e o controlo de documentos](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) e lhe tenha sido atribuída uma licença para esta subscrição, pode ver quem tentou abrir os ficheiros que protegeu e se o fizeram com êxito (se a autenticação foi efetuada com êxito) ou não. Também pode ver todas as vezes que alguém tentou aceder ao documento e a respetiva localização nesse momento. Além disso:

-   Se precisar deixar de partilhar um documento: clique em **Revogar acesso**, tome nota do período de tempo durante o qual o documento continuará disponível, decida se pretende informar as pessoas de que está a revogar o acesso ao documento partilhado anteriormente e forneça uma mensagem personalizada. Ao revogar um documento, não elimina o documento que partilhou, mas os utilizadores autorizados deixam de o poder abrir:
    
    ![Ícone Revogar acesso no site de controlo de documentos](../media/tracking-site-revoke-access-icon.png)

-   Se pretender exportar para Excel: clique em **Exportar para CSV** para que possa modificar os dados e criar as suas próprias vistas e gráficos:
    
    ![Ícone Exportar para CSV no site de controlo de documentos](../media/tracking-site-export-icon.png)

-   Se pretender configurar notificações por e-mail: clique em **Definições** e selecione como e se deve receber um e-mail quando alguém aceder ao documento:
    
    ![Ícone Exportar para CSV no site de controlo de documentos](../media/tracking-site-settings-email.png)

- Se quiser controlar e revogar documentos partilhados para outras pessoas: os administradores do Azure Information Protection podem controlar e revogar documentos protegidos para outras pessoas ao clicar no ícone Administrador. Apenas os administradores veem este ícone:
    
    ![Ícone Administrador no site de controlo de documentos](../media/tracking-site-admin-icon.png)

Para controlar um documento protegido, tem de estar registado no site de controlo de documentos. Para tal, utilize o Explorador de Ficheiros ou as aplicações do Office.

## <a name="using-office-to-track-or-revoke-the-document"></a>Utilizar o Office para controlar ou revogar o documento

Nas aplicações do Office, Word, Excel, PowerPoint e Outlook: 

1. Abra o documento protegido que pretende controlar ou revogar.

2. No separador **Base**, no grupo **Proteção**, clique em **Proteger** > **Controlar e Revogar**:

    ![Opção Controlar Utilização](../media/track-usage-callout.png)

Se não vir estas opções nas suas aplicações do Office, é provável que o cliente do Azure Information Protection não esteja instalado no seu computador, as aplicações do Office tenham de ser reiniciadas ou que seja necessário reiniciar o computador para concluir a instalação. Para obter mais informações sobre como instalar o cliente do Azure Information Protection, veja [Transferir e instalar o cliente do Azure Information Protection](install-client-app.md).

## <a name="using-file-explorer-to-track-or-revoke-the-document"></a>Utilizar o Explorador de Ficheiros para controlar ou revogar o documento

1. Clique com o botão direito do rato no ficheiro protegido e selecione **Classificar e proteger**.

2. Em seguida, na caixa de diálogo **Classificar e proteger – Azure Information Protection**, selecione **Controlar e revogar**.

    ![Ícone Controlar e revogar na caixa de diálogo Classificar e proteger – Azure Information Protection](../media/track-and-revoke.png)


### <a name="using-a-web-browser-track-and-revoke-documents-that-you-have-registered"></a>Controlar e revogar documentos registados através de um browser

Depois de ter registado o documento protegido através das aplicações do Office ou do Explorador de Ficheiros, pode controlar e revogar estes documentos através de um browser suportado:

- No PC Windows, computador Mac ou dispositivo móvel, visite o [site de controlo de documentos](https://go.microsoft.com/fwlink/?LinkId=529562).

    **Browsers suportados**: recomendamos que utilize, pelo menos, a versão 10 do Internet Explorer, mas pode utilizar qualquer um dos seguintes browsers para aceder ao site de controlo de documentos:

    -   Internet Explorer: pelo menos, versão 10

    -   Internet Explorer 9 com, pelo menos, MS12-037: Atualização de Segurança Cumulativa para o Internet Explorer: 12 de junho de 2012

    -   Mozilla Firefox: pelo menos, versão 12

    -   Apple Safari 5: pelo menos, versão 5

    -   Google Chrome: pelo menos, versão 18


## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

- [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]