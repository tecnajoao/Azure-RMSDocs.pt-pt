---
title: Controlar e revogar os documentos protegidos quando utiliza o Azure Information Protection | Azure Information Protection
description: "Depois de ter protegido os seus documentos, pode controlar a forma como as pessoas os utilizam. Se necessário, também poderá revogar o acesso a esses documentos se não pretender que as pessoas continuem a poder lê-los."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1107f484f204e64d76c389daef4d9decbfbb20e8
ms.openlocfilehash: e83d0352003fa3790fd4f8d5c59f4f7b40ef4265


---

# <a name="track-and-revoke-your-documents-when-you-use-azure-information-protection"></a>Controlar e revogar os documentos quando utiliza o Azure Information Protection

>*Aplica-se a: Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

**[Esta versão do cliente está em pré-visualização e está sujeita a alterações.]**

Após proteger os seus documentos com o Azure Information Protection, pode controlar como as pessoas utilizam esses documentos. Se necessário, também poderá revogar o acesso a estes se não pretender que as pessoas continuem a poder lê-los. Para tal, utilize o **site de controlo de documentos**, ao qual pode aceder a partir de computadores com o Windows, computadores Mac e até mesmo telemóveis e tablets.

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation/player" frameborder="0" allowfullscreen></iframe>
</div>

Ao aceder a este site, inicie sessão para controlar os seus documentos. Desde que a sua organização tenha uma [subscrição que suporte a revogação e o controlo de documentos](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) e lhe tenha sido atribuída uma licença para esta subscrição, pode ver quem tentou abrir os ficheiros que protegeu e se o fizeram com êxito (se a autenticação foi efetuada com êxito) ou não. Também pode ver todas as vezes que alguém tentou aceder ao documento e a respetiva localização nesse momento. Além disso:

-   Se precisar deixar de partilhar um documento: clique em **Revogar acesso**, tome nota do período de tempo durante o qual o documento continuará disponível, decida se pretende informar as pessoas de que está a revogar o acesso ao documento partilhado anteriormente e forneça uma mensagem personalizada. Ao revogar um documento, não elimina o documento que partilhou, mas os utilizadores autorizados deixam de o poder abrir.

-   Se pretender exportar para Excel: clique em **Exportar para CSV**, para que possa modificar os dados e criar as suas próprias vistas e gráficos.

-   Se pretender configurar notificações por e-mail: clique em **Definições** e selecione como e se deve receber um e-mail quando alguém aceder ao documento.

- Se quiser controlar e revogar documentos partilhados para outras pessoas: os administradores do Azure Information Protection podem controlar e revogar documentos protegidos para outras pessoas ao clicar no ícone Administrador. Apenas os administradores veem este ícone.

-   Se tiver dúvidas ou quiser fornecer feedback sobre o site de controlo de documentos: clique no ícone de Ajuda para aceder às [FAQ acerca do Controlo de Documentos](http://go.microsoft.com/fwlink/?LinkId=523977).

## <a name="using-office-to-access-the-document-tracking-site"></a>Utilizar o Office para aceder ao site de controlo de documentos

-   Para as aplicações do Office, Word, Excel, PowerPoint e Outlook: no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em  > **Controlar a utilização**.

Se não vir estas opções nas suas aplicações do Office, é provável que o cliente do Azure Information Protection não esteja instalado no seu computador, as aplicações do Office tenham de ser reiniciadas ou que seja necessário reiniciar o computador para concluir a instalação. Para obter mais informações sobre como instalar o cliente do Azure Information Protection, veja [Transferir e instalar o cliente do Azure Information Protection](install-client-app.md).


### <a name="other-ways-to-track-and-revoke-your-documents"></a>Outras formas de controlar e revogar os documentos
Além de controlar os seus documentos protegidos em computadores com o Windows através da utilização de aplicações do Office, também pode utilizar estas alternativas:

-   **Utilizar um browser**: este método funciona para todos os dispositivos suportados.

-   **Utilizar o Explorador de Ficheiros**: este método funciona para os computadores com o Windows.

#### <a name="using-a-web-browser-to-access-the-doc-tracking-site"></a>Utilizar um browser para aceder ao site de controlo de documentos

-   Num browser suportado, aceda ao [site de controlo de documentos](https://go.microsoft.com/fwlink/?LinkId=529562).

    Browsers suportados: recomendamos que utilize, pelo menos, a versão 10 do Internet Explorer, mas pode utilizar qualquer um dos seguintes browsers para aceder ao site de controlo de documentos:

    -   Internet Explorer: pelo menos, versão 10

    -   Internet Explorer 9 com, pelo menos, MS12-037: Atualização de Segurança Cumulativa para o Internet Explorer: 12 de junho de 2012

    -   Mozilla Firefox: pelo menos, versão 12

    -   Apple Safari 5: pelo menos, versão 5

    -   Google Chrome: pelo menos, versão 18

#### <a name="using-file-explorer-to-access-the-doc-tracking-site"></a>Utilizar o Explorador de Ficheiros para aceder ao site de controlo de documentos

-   Clique com o botão direito do rato no ficheiro, selecione **Classificar e proteger (pré-visualização)** e, em seguida, no **Visualizador do Azure Information Protection**, selecione o ícone Controlar a Utilização.


## <a name="other-instructions"></a>Outras instruções
Para obter instruções sobre os procedimentos, veja as secções seguintes do guia do utilizador do Azure Information Protection:

-   [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)





<!--HONumber=Dec16_HO1-->


