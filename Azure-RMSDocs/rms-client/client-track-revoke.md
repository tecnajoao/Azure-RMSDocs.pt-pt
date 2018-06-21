---
title: Controlar e revogar documentos – AIP
description: Depois de ter protegido os seus documentos, pode controlar a forma como as pessoas os utilizam. Se necessário, também poderá revogar o acesso a esses documentos se não pretender que as pessoas continuem a poder lê-los.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e4e35659ab964a636c6ca0c7066b1c809cc5958b
ms.sourcegitcommit: 6a67fc50bd8b8a06974de647c15115a673f0217c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33823532"
---
# <a name="user-guide-track-and-revoke-your-documents-when-you-use-azure-information-protection"></a>Guia do utilizador: Controlar e revogar os documentos quando utiliza o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

Após proteger os seus documentos com o Azure Information Protection, pode controlar como as pessoas utilizam esses documentos. Se necessário, também poderá revogar o acesso a estes se não pretender que as pessoas continuem a poder lê-los. Para tal, utilize o **site de controlo de documentos**. Pode aceder a este site a partir de computadores com o Windows, computadores Mac e até mesmo tablets e telemóveis.

Ao aceder a este site, inicie sessão para controlar os seus documentos. Desde que a sua organização tenha uma [subscrição que suporte a revogação e o controlo de documentos](https://www.microsoft.com/cloud-platform/azure-information-protection-features) e lhe tenha sido atribuída uma licença para esta subscrição, pode ver quem tentou abrir os ficheiros que protegeu e se o fizeram com êxito (se a autenticação foi efetuada com êxito) ou não. Também pode ver todas as vezes que alguém tentou aceder ao documento e a respetiva localização nesse momento. No entanto, em casos raros, a localização comunicada poderá não ser exata. Por exemplo, quando um utilizador ao abrir um documento protegido está a utilizar uma ligação VPN ou o respetivo computador tem um endereço IPv6.

Ações que pode tomar no site de controlo de documentos:

- Caso necessite de parar de partilhar um documento: 
    
    - Clique em **Revogar acesso**. Tenha em atenção o período de tempo durante o qual o documento fica disponível. Decida se quer permitir que as pessoas saibam que está a revogar o acesso ao documento que partilhou anteriormente com uma mensagem personalizada. Ao revogar um documento, não elimina o documento que partilhou, mas os utilizadores autorizados deixam de o poder abrir:
        
        ![Ícone Revogar acesso no site de controlo de documentos](../media/tracking-site-revoke-access-icon.png)
        
- Caso pretenda exportar para o Excel: 
    
    - Clique em **Exportar para o CSV**, para que consiga modificar os dados e criar as suas próprias vistas e gráficos:
         
        ![Ícone Exportar para CSV no site de controlo de documentos](../media/tracking-site-export-icon.png)
         
- Caso pretenda configurar notificações por e-mail: 
     
    - Clique em **Definições** e selecione como e se pretende receber notificações por e-mail caso o documento seja acedido:
        
        ![Ícone Exportar para CSV no site de controlo de documentos](../media/tracking-site-settings-email.png)

- Se deseja controlar e revogar documentos partilhados com outras pessoas:
    
    - Os administradores do Azure Information Protection podem clicar no ícone Administrador para controlar e revogar documentos protegidos de utilizadores quando esses utilizadores registarem os seus documentos no site de controlo de documentos. Apenas os administradores veem este ícone:
        
        ![Ícone Administrador no site de controlo de documentos](../media/tracking-site-admin-icon.png)
        
        Se não vir este ícone, apesar de ser um administrador global, é porque ainda não partilhou documentos. Neste caso, utilize o seguinte URL para aceder ao site de controlo de documentos: https://portal.azurerms.com/#/admin

A menos que seja um administrador, pode controlar e revogar apenas os documentos protegidos. Não pode controlar os seus e-mails protegidos com o site de controlo de documentos.

> [!NOTE] 
> Se o administrador tiver configurado os controlos de privacidade para o site de controlo de documentos, talvez não veja quando os utilizadores da sua organização acederam a um documento que controla. Um administrador pode isentar todos os utilizadores ou apenas alguns. No entanto, pode sempre revogar o acesso aos documentos que controla.

Para controlar um documento que protegeu, deve utilizar o seu computador Windows para o registar no site de controlo de documentos. Para tal, utilize o Explorador de Ficheiros ou as aplicações do Office.

## <a name="using-office-to-track-or-revoke-the-document"></a>Utilizar o Office para controlar ou revogar o documento

Nas aplicações do Office, Word, Excel, PowerPoint e Outlook: 

1. Abra o documento protegido que pretende controlar ou revogar.

2. No separador **Base**, no grupo **Proteção**, clique em **Proteger** > **Controlar e Revogar**:

    ![Opção Controlar Utilização](../media/track-usage-callout.png)
    
    Se não vir estas opções nas suas aplicações do Office, poderá ser devido a um dos seguintes motivos:
    
    - O cliente do Azure Information Protection não está instalado no seu computador.
    
    - As suas aplicações do Office têm de ser reiniciadas.
    
    - O seu computador tem de ser reiniciado para concluir a instalação.
    
Para obter mais informações sobre como instalar o cliente do Azure Information Protection, veja [Transferir e instalar o cliente do Azure Information Protection](install-client-app.md).

## <a name="using-file-explorer-to-track-or-revoke-the-document"></a>Utilizar o Explorador de Ficheiros para controlar ou revogar o documento

1. Clique com o botão direito do rato no ficheiro protegido e selecione **Classificar e proteger**.

2. Em seguida, na caixa de diálogo **Classificar e proteger – Azure Information Protection**, selecione **Controlar e revogar**.

    ![Ícone Controlar e revogar na caixa de diálogo Classificar e proteger – Azure Information Protection](../media/track-and-revoke.png)


### <a name="using-a-web-browser-to-track-and-revoke-documents-that-you-have-registered"></a>Controlar e revogar documentos registados através de um browser

Depois de ter registado o documento protegido através das aplicações do Office ou do Explorador de Ficheiros, pode controlar e revogar estes documentos através de um browser suportado:

- No PC Windows, computador Mac ou dispositivo móvel, visite o [site de controlo de documentos](https://go.microsoft.com/fwlink/?LinkId=529562).

    **Browsers suportados**: recomendamos que utilize, pelo menos, a versão 10 do Internet Explorer, mas pode utilizar qualquer um dos seguintes browsers para aceder ao site de controlo de documentos:

    - Internet Explorer: pelo menos, versão 10

    - Internet Explorer 9 com, pelo menos, MS12-037: Atualização de Segurança Cumulativa para o Internet Explorer: 12 de junho de 2012

    - Mozilla Firefox: pelo menos, versão 12

    - Apple Safari 5: pelo menos, versão 5

    - Google Chrome: pelo menos, versão 18


## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

- [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Informações adicionais para administradores    
Consulte [configurar e utilizar o controlo de documentos para o Azure Information Protection](client-admin-guide-document-tracking.md) do [Guia do administrador](client-admin-guide.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]