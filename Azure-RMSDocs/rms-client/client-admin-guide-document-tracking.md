---
title: Controlo de documentos do Azure Information Protection
description: Instruções e informações para os administradores configurarem e utilizarem o controlo de documentos do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/06/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: ae3600be6093321499a6202a08612daad8bd0ae3
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804608"
---
# <a name="admin-guide-configuring-and-using-document-tracking-for-azure-information-protection"></a>Guia do administrador: Configurar e utilizar o controlo de documentos do Azure Information Protection

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Se tiver uma [subscrição que suporta o controlo de documentos](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), o site de controlo de documentos é ativado por predefinição para todos os utilizadores da sua organização. O controlo de documentos dispõe de informações para utilizadores e administradores sobre quando um documento protegido foi acedido e, se necessário, um documento controlado pode ser revogado.

## <a name="using-powershell-to-manage-the-document-tracking-site"></a>Com o PowerShell para gerir o site de controlo de documentos

As secções seguintes contêm informações sobre como pode gerir o site de controlo através do PowerShell de documentos. Para obter instruções de instalação para o módulo do PowerShell, consulte [instalar o módulo do PowerShell do AADRM](../install-powershell.md). Se já transferiu e instalou o módulo anteriormente, verifique o número da versão ao executar: `(Get-Module aadrm –ListAvailable).Version`

Para obter mais informações sobre cada um dos cmdlets, utilize as ligações fornecidas.

### <a name="privacy-controls-for-your-document-tracking-site"></a>Controlos de privacidade para o site de controlo de documentos

Se a apresentação de informações de controlo de documentos for proibida dentro da sua organização devido a requisitos de privacidade, pode desativar o controlo de documentos através do cmdlet [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature). 

Este cmdlet desativa o acesso ao site de controlo de documentos, para que todos os utilizadores na sua organização não possam controlar ou revogar o acesso a documentos que tenham protegido. Pode reativar o controlo de documentos em qualquer altura através de [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature) e ainda verificar se o controlo de documentos está ativado ou desativado com [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature). Para executar estes cmdlets, tem de ter, pelo menos, versão **2.3.0.0** do módulo do AADRM para o PowerShell. 

Quando o site de controlo de documentos está ativado, por predefinição, apresenta informações como os endereços de e-mail das pessoas que tentaram aceder a documentos protegidos, quando essas pessoas tentaram aceder aos mesmos e a sua localização. Este nível de informações pode ser útil para determinar como os documentos partilhados são utilizados e se devem ser revogados quando for detetada uma atividade suspeita. No entanto, por motivos de privacidade, talvez seja necessário desativar estas informações de utilizador para alguns ou para todos os utilizadores. 

Se tiver utilizadores que não devem ter esta atividade controlada por outros utilizadores, adicioná-los a um grupo que é armazenado no Azure AD e especifique este grupo com o [Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Set-AadrmDoNotTrackUserGroup) cmdlet. Ao executar este cmdlet, deve especificar um único grupo. No entanto, o grupo pode conter grupos aninhados. 

Para estes membros do grupo, os utilizadores não podem ver todas as atividades no site de controlo quando o que a atividade está relacionada aos documentos que são partilhados com eles de documentos. Além disso, não são enviadas notificações de e-mail para o utilizador que partilhou o documento.

Ao utilizar esta configuração, todos os utilizadores ainda podem utilizar o site de controlo de documentos e revogar o acesso a documentos que tenham protegido. No entanto, não verão a atividade dos utilizadores que especificou através do cmdlet Set-AadrmDoNotTrackUserGroup.

Esta definição afeta apenas a utilizadores finais. Os administradores do Azure Information Protection sempre podem controlar atividades de todos os utilizadores, mesmo quando esses utilizadores são especificados com Set-AadrmDoNotTrackUserGroup. Para obter mais informações sobre como os administradores podem controlar os documentos para utilizadores, consulte a [controlar e revogar documentos para utilizadores](#tracking-and-revoking-documents-for-users) secção.


### <a name="logging-information-from-the-document-tracking-site"></a>Registo de informações do site de controlo de documentos

Se tiver uma versão mínima do **2.13.0.0** para o módulo do AADRM, pode utilizar os seguintes cmdlets para transferir informações de registo a partir do site de controlo de documentos:

- [Get-AadrmTrackingLog](/powershell/module/aadrm/Get-AadrmTrackingLog)
    
    Este cmdlet devolve informações de controlo sobre os documentos protegidos para um utilizador especificado quem protegeu documentos (o emissor do Rights Management) ou quem acedeu a documentos protegidos. Utilize este cmdlet para o ajudar a responder à pergunta "quais documentos protegidos fizeram um utilizador especificado controlar ou acessar?"

- [Get-AadrmDocumentLog](/powershell/module/aadrm/Get-AadrmDocumentLog)
    
    Este cmdlet devolve informações de proteção sobre os documentos rastreados para um utilizador especificado se esse utilizador (o emissor do Rights Management) de documentos protegidos fosse o proprietário do Rights Management para documentos ou documentos protegidos foram configurados para conceder acesso diretamente para o utilizador. Utilize este cmdlet para o ajudar a responder à pergunta "Como são documentos protegidos para um utilizador especificado?"
 
## <a name="destination-urls-used-by-the-document-tracking-site"></a>URLs de destino utilizados pelo site de controlo de documentos

Os seguintes URLs são utilizados para controlo de documentos e devem ser permitidos em todos os dispositivos e serviços entre os clientes que executam o cliente do Azure Information Protection e a Internet. Por exemplo, adicione estes URLs a firewalls ou aos seus Sites Fiáveis se estiver a utilizar o Internet Explorer com Segurança Avançada.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Estes URLs são standard para o serviço Azure Rights Management, com a exceção do URL virtualearth.net, que é utilizado para os mapas do Bing, para apresentar a localização do utilizador.

## <a name="tracking-and-revoking-documents-for-users"></a>Controlar e revogar documentos para utilizadores

Quando os utilizadores iniciam sessão no site de controlo de documentos, podem controlar e revogar documentos que protegeram através do cliente do Azure Information Protection ou que partilharam através da aplicação de partilha Rights Management. Quando iniciar sessão como administrador global do Azure AD para o seu inquilino, pode clicar no ícone de administração, que muda para o modo de administrador. Outras funções de administrador não suporta este modo para o site de controlo de documentos. 

![Ícone Administrador no site de controlo de documentos](../media/tracking-site-admin-icon.png)

O modo de administrador permite-lhe ver os documentos que os utilizadores na sua organização selecionaram para controlar com o cliente do Azure Information Protection ou partilharam com a aplicação de partilha Rights Management.

> [!NOTE] 
> Se não vir este ícone, apesar de ser um administrador global, é porque não ainda partilhou todos os documentos por conta própria. Neste caso, utilize o seguinte URL para aceder ao site de controlo de documentos: https://portal.azurerms.com/#/admin

As ações que executar no modo de Administrador são auditadas e registadas nos ficheiros de registo de utilização e tem de confirmar para continuar. Para obter mais informações sobre este registo, veja a secção seguinte.

Quando estiver no modo de Administrador, pode procurar por utilizador ou documento. Se procurar por utilizador, verá todos os documentos que o utilizador especificado selecionou para controlar com o cliente do Azure Information Protection ou partilhou com a aplicação de partilha Rights Management. 

Se procurar por documento verá todos os utilizadores na sua organização que controlaram esse documento com o cliente do Azure Information Protection ou o partilharam com a aplicação de partilha Rights Management. Em seguida, pode explorar os resultados da pesquisa para controlar os documentos que os utilizadores protegeram e revogar esses documentos, se necessário. 

Para sair do modo de Administrador, clique no **X** junto a **Sair do modo de administrador**:

![Sair do modo de administrador no site de controlo de documentos](../media/tracking-site-exit-admin-icon.png)

Para obter instruções sobre como utilizar o site de controlo de documentos, veja [Controlar e revogar documentos](client-track-revoke.md) no guia de utilizador.

## <a name="usage-logging-for-the-document-tracking-site"></a>Registo de utilização para o site de controlo de documentos

São aplicáveis dois campos nos ficheiros de registo de utilização ao controlo de documentos: **AdminAction** e **ActingAsUser**.

**AdminAction** - Este campo tem um valor de true quando um administrador utiliza o site de controlo de documentos no modo de Administrador, por exemplo, para revogar um documento em nome de um utilizador ou para ver quando foi partilhado. Este campo está vazio quando um utilizador inicia sessão no site de controlo de documentos.

**ActingAsUser** - Quando o campo AdminAction tiver o valor de true, este campo contém o nome do utilizador sobre o qual o administrador está a agir quando procurar por utilizador ou proprietário do documento. Este campo está vazio quando um utilizador inicia sessão no site de controlo de documentos. 

Também existem tipos de pedido que registam a forma como os utilizadores e os administradores estão a utilizar o site de controlo de documentos. Por exemplo, **RevokeAccess** é o tipo de pedido quando um utilizador ou um administrador em nome de um utilizador revogou um documento no site de controlo de documentos. Utilize este tipo de pedido juntamente com o campo AdminAction para determinar se o utilizador revogou o seu próprio documento (o campo AdminAction está vazio) ou um administrador revogou um documento em nome de um utilizador (AdminAction é true).


Para obter mais informações sobre o registo de utilização, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../log-analyze-usage.md)



## <a name="next-steps"></a>Passos Seguintes
Agora que configurou o site de controlo de documentos do cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)

