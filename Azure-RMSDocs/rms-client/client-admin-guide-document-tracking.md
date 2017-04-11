---
title: Controlo de documentos do Azure Information Protection
description: "Instruções e informações para os administradores configurarem e utilizarem o controlo de documentos do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: f47b177ece91f775d53c72d379d6ffa3a2f3c98b
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="configuring-and-using-document-tracking-for-azure-information-protection"></a>Configurar e utilizar o controlo de documentos do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8 e Windows 7 com SP1*

Se tiver uma [subscrição que suporta o controlo de documentos](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), o site de controlo de documentos é ativado por predefinição para todos os utilizadores da sua organização. O controlo de documentos apresenta informações como os endereços de e-mail das pessoas que tentaram aceder a documentos protegidos partilhados por utilizadores, quando essas pessoas tentaram aceder aos mesmos e a sua localização. Se a apresentação deste tipo de informações é proibida dentro da sua organização devido a requisitos de privacidade, pode desativar o acesso ao site de controlo de documentos através do cmdlet [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032). Pode reativar o acesso ao site em qualquer altura através de [Enable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) e ainda verificar se o acesso ao site está ativado ou desativado com [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

Para executar estes cmdlets, tem de ter no mínimo a versão **2.3.0.0** do módulo do Azure Rights Management para o Windows PowerShell. Para obter instruções de instalação, consulte [Installing Windows PowerShell for Azure Rights Management (Instalar o Windows PowerShell para o Azure Rights Management – em inglês)](../deploy-use/install-powershell.md).

> [!TIP]
> Se já transferiu e instalou o módulo anteriormente, verifique o número da versão ao executar: `(Get-Module aadrm –ListAvailable).Version`

Os URLs seguintes são utilizados para o controlo de documentos e têm de ser permitidos (por exemplo, adicione-os à sua lista de Sites Fidedignos se estiver a utilizar o Internet Explorer com Segurança Avançada):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Este URL é destinado aos mapas Bing.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

## <a name="tracking-and-revoking-documents-for-users"></a>Controlar e revogar documentos para utilizadores

Quando os utilizadores iniciam sessão no site de controlo de documentos, podem controlar e revogar documentos que protegeram através do cliente do Azure Information Protection ou que partilharam através da aplicação de partilha Rights Management. Quando inicia sessão como administrador do Azure Information Protection (administrador global), pode clicar no ícone de Administração, que muda para o modo de Administrador para que possa ver os documentos que foram partilhados pelos utilizadores na sua organização:

![Ícone Administrador no site de controlo de documentos](../media/tracking-site-admin-icon.png)

As ações que executar no modo de Administrador são auditadas e registadas nos ficheiros de registo de utilização e tem de confirmar para continuar. Para obter mais informações sobre este registo, veja a secção seguinte.

Quando estiver no modo de Administrador, pode procurar por utilizador ou documento. Se procurar por utilizador, verá todos os documentos partilhados pelo utilizador especificado. Se procurar por documento, verá todos os utilizadores na sua organização que partilharam esse documento. Em seguida, pode explorar os resultados da pesquisa para controlar os documentos que os utilizadores partilharam e revogar estes documentos, se necessário. 

Para sair do modo de Administrador, clique no **X** junto a **Sair do modo de administrador**:

![Sair do modo de administrador no site de controlo de documentos](../media/tracking-site-exit-admin-icon.png)

Para obter instruções sobre como utilizar o site de controlo de documentos, veja [Controlar e revogar documentos](client-track-revoke.md) no guia de utilizador.

## <a name="usage-logging-for-the-document-tracking-site"></a>Registo de utilização para o site de controlo de documentos

São aplicáveis dois campos nos ficheiros de registo de utilização ao controlo de documentos: **AdminAction** e **ActingAsUser**.

**AdminAction** - Este campo tem um valor de true quando um administrador utiliza o site de controlo de documentos no modo de Administrador, por exemplo, para revogar um documento em nome de um utilizador ou para ver quando foi partilhado. Este campo está vazio quando um utilizador inicia sessão no site de controlo de documentos.

**ActingAsUser** - Quando o campo AdminAction tiver o valor de true, este campo contém o nome do utilizador sobre o qual o administrador está a agir quando procurar por utilizador ou proprietário do documento. Este campo está vazio quando um utilizador inicia sessão no site de controlo de documentos. 

Também existem tipos de pedido que registam a forma como os utilizadores e os administradores estão a utilizar o site de controlo de documentos. Por exemplo, **RevokeAccess** é o tipo de pedido quando um utilizador ou um administrador em nome de um utilizador revogou um documento no site de controlo de documentos. Utilize este tipo de pedido juntamente com o campo AdminAction para determinar se o utilizador revogou o seu próprio documento (o campo AdminAction está vazio) ou um administrador revogou um documento em nome de um utilizador (AdminAction é true).


Para obter mais informações sobre o registo de utilização, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md)



## <a name="next-steps"></a>Passos seguintes
Agora que configurou o site de controlo de documentos do cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
