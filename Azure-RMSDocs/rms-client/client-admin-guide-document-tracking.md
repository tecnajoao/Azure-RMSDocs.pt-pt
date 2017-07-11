---
title: Controlo de documentos do Azure Information Protection
description: "Instruções e informações para os administradores configurarem e utilizarem o controlo de documentos do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 3b7ed22afea6b8575d12f6f83dcfc8419200c003
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
<a id="configuring-and-using-document-tracking-for-azure-information-protection" class="xliff"></a>

# Configurar e utilizar o controlo de documentos do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Se tiver uma [subscrição que suporta o controlo de documentos](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), o site de controlo de documentos é ativado por predefinição para todos os utilizadores da sua organização. O controlo de documentos dispõe de informações para utilizadores e administradores sobre quando um documento protegido foi acedido e, se necessário, um documento controlado pode ser revogado.

<a id="privacy-controls-for-your-document-tracking-site" class="xliff"></a>

## Controlos de privacidade para o site de controlo de documentos

Se a apresentação de informações de controlo de documentos for proibida dentro da sua organização devido a requisitos de privacidade, pode desativar o controlo de documentos através do cmdlet [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature). 

Este cmdlet desativa o acesso ao site de controlo de documentos, para que todos os utilizadores na sua organização não possam controlar ou revogar o acesso a documentos que tenham protegido. Pode reativar o controlo de documentos em qualquer altura através de [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature) e ainda verificar se o controlo de documentos está ativado ou desativado com [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature). Para executar estes cmdlets, tem de ter no mínimo a versão **2.3.0.0** do módulo do Azure Rights Management (AADRM) para o PowerShell. 

Quando o site de controlo de documentos está ativado, por predefinição, apresenta informações como os endereços de e-mail das pessoas que tentaram aceder a documentos protegidos, quando essas pessoas tentaram aceder aos mesmos e a sua localização. Este nível de informações pode ser muito útil para determinar como os documentos partilhados são utilizados e se devem ser revogados se uma atividade suspeita for vista. No entanto, por motivos de privacidade, talvez seja necessário desativar estas informações de utilizador para alguns ou para todos os utilizadores. 

Se tiver utilizadores que não devem ter esta atividade controlada, adicione-os a um grupo que é armazenado no Azure AD e especifique este grupo com o cmdlet [Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Set-AadrmDoNotTrackUserGroup). Ao executar este cmdlet, deve especificar um único grupo. No entanto, o grupo pode conter grupos aninhados. 

Para estes membros do grupo, as suas atividades relacionadas com documentos que outras pessoas partilharam com eles não estão ligadas ao seu site de controlo de documentos. Além disso, não são enviadas notificações de e-mail para o utilizador que partilhou o documento.

Ao utilizar esta configuração, todos os utilizadores ainda podem utilizar o site de controlo de documentos e revogar o acesso a documentos que tenham protegido. No entanto, eles não verão atividade para os utilizadores que especificou através do cmdlet Set-AadrmDoNotTrackUserGroup.

Pode utilizar o cmdlet [Clear-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Clear-AadrmDoNotTrackUserGroup) se já não precisar desta opção. Ou para remover seletivamente os utilizadores, remova-os do grupo, mas lembre-se da [colocação em cache de grupo](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management). Pode verificar se esta opção está atualmente em utilização através do [Get-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/get-AadrmDoNotTrackUserGroup). Para executar os cmdlets para esta configuração de grupo, tem de ter no mínimo a versão **2.10.0.0** do módulo do Azure Rights Management (AADRM) para o PowerShell.

Para obter mais informações sobre cada um destes cmdlets, utilize as ligações apresentadas. Para obter instruções de instalação do módulo do PowerShell, veja [Instalar o Windows PowerShell para o Azure Rights Management](../deploy-use/install-powershell.md). Se já transferiu e instalou o módulo anteriormente, verifique o número da versão ao executar: `(Get-Module aadrm –ListAvailable).Version`


<a id="destination-urls-used-by-the-document-tracking-site" class="xliff"></a>

## URLs de destino utilizados pelo site de controlo de documentos

Os seguintes URLs são utilizados para controlo de documentos e devem ser permitidos em todos os dispositivos e serviços entre os clientes que executam o cliente do Azure Information Protection e a Internet. Por exemplo, adicione estes URLs a firewalls ou aos seus Sites Fiáveis se estiver a utilizar o Internet Explorer com Segurança Avançada.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Estes URLs são standard para o serviço Azure Rights Management, com a exceção do URL virtualearth.net, que é utilizado para os mapas do Bing, para apresentar a localização do utilizador.

<a id="tracking-and-revoking-documents-for-users" class="xliff"></a>

## Controlar e revogar documentos para utilizadores

Quando os utilizadores iniciam sessão no site de controlo de documentos, podem controlar e revogar documentos que protegeram através do cliente do Azure Information Protection ou que partilharam através da aplicação de partilha Rights Management. Quando inicia sessão como administrador do Azure Information Protection (administrador global), pode clicar no ícone de Administração, que muda para o modo de Administrador para que possa ver os documentos que foram partilhados pelos utilizadores na sua organização:

![Ícone Administrador no site de controlo de documentos](../media/tracking-site-admin-icon.png)

As ações que executar no modo de Administrador são auditadas e registadas nos ficheiros de registo de utilização e tem de confirmar para continuar. Para obter mais informações sobre este registo, veja a secção seguinte.

Quando estiver no modo de Administrador, pode procurar por utilizador ou documento. Se procurar por utilizador, verá todos os documentos partilhados pelo utilizador especificado. Se procurar por documento, verá todos os utilizadores na sua organização que partilharam esse documento. Em seguida, pode explorar os resultados da pesquisa para controlar os documentos que os utilizadores partilharam e revogar estes documentos, se necessário. 

Para sair do modo de Administrador, clique no **X** junto a **Sair do modo de administrador**:

![Sair do modo de administrador no site de controlo de documentos](../media/tracking-site-exit-admin-icon.png)

Para obter instruções sobre como utilizar o site de controlo de documentos, veja [Controlar e revogar documentos](client-track-revoke.md) no guia de utilizador.

<a id="usage-logging-for-the-document-tracking-site" class="xliff"></a>

## Registo de utilização para o site de controlo de documentos

São aplicáveis dois campos nos ficheiros de registo de utilização ao controlo de documentos: **AdminAction** e **ActingAsUser**.

**AdminAction** - Este campo tem um valor de true quando um administrador utiliza o site de controlo de documentos no modo de Administrador, por exemplo, para revogar um documento em nome de um utilizador ou para ver quando foi partilhado. Este campo está vazio quando um utilizador inicia sessão no site de controlo de documentos.

**ActingAsUser** - Quando o campo AdminAction tiver o valor de true, este campo contém o nome do utilizador sobre o qual o administrador está a agir quando procurar por utilizador ou proprietário do documento. Este campo está vazio quando um utilizador inicia sessão no site de controlo de documentos. 

Também existem tipos de pedido que registam a forma como os utilizadores e os administradores estão a utilizar o site de controlo de documentos. Por exemplo, **RevokeAccess** é o tipo de pedido quando um utilizador ou um administrador em nome de um utilizador revogou um documento no site de controlo de documentos. Utilize este tipo de pedido juntamente com o campo AdminAction para determinar se o utilizador revogou o seu próprio documento (o campo AdminAction está vazio) ou um administrador revogou um documento em nome de um utilizador (AdminAction é true).


Para obter mais informações sobre o registo de utilização, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md)



<a id="next-steps" class="xliff"></a>

## Passos seguintes
Agora que configurou o site de controlo de documentos do cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
