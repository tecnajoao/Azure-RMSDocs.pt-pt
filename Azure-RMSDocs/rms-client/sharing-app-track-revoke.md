---
title: Controlar e revogar documentos com a aplicação de partilha RMS – AIP
description: Após proteger os seus documentos utilizando a aplicação de partilha RMS, pode controlar como as pessoas utilizam os seus documentos protegidos. Se necessário, também pode revogar o acesso a esses documentos quando pretender deixar de os partilhar.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 61f349ce-bdd2-45c1-acc5-bc83937fb187
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d6d53635a7f86c9ecc27f654885f9d66569f2b1e
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39374244"
---
# <a name="track-and-revoke-your-documents-when-you-use-the-rms-sharing-application"></a>Controlar e revogar os documentos quando utiliza a aplicação de partilha RMS

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 com SP1, Windows 8, Windows 8.1*

Depois de proteger os documentos com a aplicação de partilha RMS, se a sua organização utilizar o Azure Information Protection em vez dos Serviços de Gestão de Direitos do Active Directory, pode controlar a forma como as pessoas utilizam os seus documentos protegidos. Se necessário, também pode revogar o acesso a esses documentos quando pretender deixar de os partilhar. Para tal, utilize o **site de controlo de documentos**, ao qual pode aceder a partir de computadores com o Windows, computadores Mac e até mesmo telemóveis e tablets.

Ao aceder a este site, inicie sessão para controlar os seus documentos. Desde que a sua organização tenha uma [subscrição que suporte a revogação e o controlo de documentos](https://www.microsoft.com/cloud-platform/azure-information-protection-features) e lhe tenha sido atribuída uma licença para esta subscrição, pode ver quem tentou abrir os ficheiros que protegeu e se o fizeram com êxito (se a autenticação foi efetuada com êxito) ou não. Também pode ver todas as vezes que alguém tentou aceder ao documento e a respetiva localização nesse momento. No entanto, em casos raros, a localização comunicada poderá não ser precisa. Por exemplo, quando um utilizador abrir um documento protegido está a utilizar uma ligação VPN ou o computador tem um endereço IPv6.

Ações que pode realizar no site de controlo de documentos:

- Se precisar deixar de partilhar um documento: clique em **Revogar acesso**, tome nota do período de tempo durante o qual o documento continuará disponível, decida se pretende informar as pessoas de que está a revogar o acesso ao documento partilhado anteriormente e forneça uma mensagem personalizada. Ao revogar um documento, não elimina o documento que partilhou, mas os utilizadores autorizados deixam de o poder abrir.

- Se pretender exportar para Excel: clique em **Exportar para CSV**, para que possa modificar os dados e criar as suas próprias vistas e gráficos.

- Se pretender configurar notificações por e-mail: clique em **Definições** e selecione como e se deve receber um e-mail quando alguém aceder ao documento.

- Se quiser controlar e revogar documentos partilhados para outras pessoas: os administradores do Azure Information Protection podem controlar e revogar documentos para outras pessoas ao clicar no ícone Administrador. Apenas os administradores veem este ícone.
    
    Nota: Se não vir este ícone, apesar de ser um administrador global, é porque ainda não partilhou documentos. Neste caso, utilize o seguinte URL para aceder ao site de controlo de documentos: https://portal.azurerms.com/#/admin

- Se tiver dúvidas ou quiser fornecer feedback sobre o site de controlo de documentos: clique no ícone de Ajuda para aceder às [FAQ acerca do Controlo de Documentos](http://go.microsoft.com/fwlink/?LinkId=523977).

## <a name="using-office-to-access-the-document-tracking-site"></a>Utilizar o Office para aceder ao site de controlo de documentos

- Para as aplicações do Office, Word, Excel e PowerPoint: no separador **Base**, no grupo **RMS**, clique em **Partilhar Protegido** e, em seguida, clique em **Controlar a Utilização**.

    ![Controlar a utilização de aplicações do Office ao utilizar a aplicação de partilha RMS ](../media/ADRMS_MSRMSApp_OfficeToolbarTrackUsage.png)

- Para o Outlook: no separador **Base**, no grupo **RMS**, clique em **Controlar a Utilização**:

    ![Selecionar Controlar a Utilização do Outlook ao utilizar a aplicação de partilha RMS ](../media/ADRMS_MSRMSApp_OutlookTrackUsage.png)

Se não vir estas opções do RMS, é provável que a aplicação de partilha RMS não esteja instalada no seu computador, que a versão mais recente não esteja instalada ou que seja necessário reiniciar o computador para concluir a instalação. Para obter mais informações sobre como instalar a aplicação de partilha, consulte [Transferir e instalar a aplicação de partilha Rights Management](install-sharing-app.md).

> [!NOTE] 
> Se tiver instalado o [cliente do Azure Information Protection](../rms-client/info-protect-client.md), também pode aceder ao site de controlo de documentos através do botão **Proteger**: 
> 
> - Numa aplicação do Office, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em  > **Controlar utilização**. 

### <a name="other-ways-to-track-and-revoke-your-documents"></a>Outras formas de controlar e revogar os documentos
Além de controlar os seus documentos em computadores com o Windows através da utilização de aplicações do Office, também pode utilizar estas alternativas:

-   **Utilizar um browser**: este método funciona para todos os dispositivos suportados.

-   **Utilizar o Explorador de Ficheiros**: este método funciona para os computadores com o Windows.

-   **Utilizar uma mensagem de e-mail do Outlook**: este método funciona para os computadores com o Windows.

#### <a name="using-a-web-browser-to-access-the-doc-tracking-site"></a>Utilizar um browser para aceder ao site de controlo de documentos

- Num browser suportado, aceda ao [site de controlo de documentos](http://go.microsoft.com/fwlink/?LinkId=529562).

    Browsers suportados: recomendamos que utilize, pelo menos, a versão 10 do Internet Explorer, mas pode utilizar qualquer um dos seguintes browsers para aceder ao site de controlo de documentos:

    -   Internet Explorer: pelo menos, versão 10

    -   Internet Explorer 9 com, pelo menos, MS12-037: Atualização de Segurança Cumulativa para o Internet Explorer: 12 de junho de 2012

    -   Mozilla Firefox: pelo menos, versão 12

    -   Apple Safari 5: pelo menos, versão 5

    -   Google Chrome: pelo menos, versão 18

#### <a name="using-file-explorer-to-access-the-doc-tracking-site"></a>Utilizar o Explorador de Ficheiros para aceder ao site de controlo de documentos

- Clique com o botão direito do rato no ficheiro, selecione **Proteger com RMS** e, em seguida, selecione **Controlar a Utilização**:

    ![Selecionar Controlar a Utilização do Explorador ao utilizar a aplicação de partilha RMS](../media/ADRMS_MSRMSApp_ExplorerTrackUsage.png)

#### <a name="using-an-outlook-email-message-to-access-the-doc-tracking-site"></a>Utilizar uma mensagem de e-mail do Outlook para aceder ao site de controlo de documentos

- Numa mensagem de e-mail, no separador **Mensagem**, no grupo **RMS**, clique em **Partilhar Protegido** e, em seguida, clique em **Controlar a Utilização**:

    ![Selecionar Controlar a Utilização do Outlook ao utilizar a aplicação de partilha RMS](../media/ADRMS_MSRMSApp_OutlookMessageTrackUsage.png)

## <a name="examples-and-other-instructions"></a>Exemplos e outras instruções
Para obter exemplos de como pode utilizar a aplicação de partilha Rights Management e instruções sobre como proceder, veja as secções seguintes do guia do utilizador da aplicação de partilha Rights Management:

-   [Exemplos de utilização da aplicação de partilha RMS](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [O que pretende fazer?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Consulte Também
[Guia do utilizador da aplicação de partilha Rights Management](sharing-app-user-guide.md)
