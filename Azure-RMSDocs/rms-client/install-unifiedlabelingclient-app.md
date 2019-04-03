---
title: Transferir e instalar o cliente etiquetagem unificado (pré-visualização) do Azure Information Protection
description: Instruções para os utilizadores instalarem a versão de pré-visualização do Azure Information Protection unified cliente etiquetagem para o Windows, para que possa classificar e proteger os seus documentos e e-mails.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/02/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: a48bb16bd2b4a0b15df0086c1eba3c14766ee9a2
ms.sourcegitcommit: 8da0aa8f9bb9f91375580a703682d23a81a441bf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58809901"
---
# <a name="download-and-install-the-azure-information-protection-unified-labeling-client-preview"></a>Transferir e instalar o cliente etiquetagem unificado (pré-visualização) do Azure Information Protection

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

> [!NOTE]
> Este cliente está em pré-visualização e está sujeitas a alterações. Ele utiliza o armazenamento de etiquetagem unificado e transfere a política com as etiquetas de sensibilidade de centros de administração: A segurança do Office 365 e Centro de conformidade, o Centro de segurança do Microsoft 365 e o Centro de conformidade do Microsoft 365. Para utilizar estas etiquetas, eles tem primeiro de ser publicados a partir de um nestes centros de administração. [Mais informações](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492)

Tem de ser um administrador local no seu PC para instalar este cliente de pré-visualização, para que o mesmo possa Etiquetar e proteger os seus documentos e e-mails.

Além disso:

- O cliente de etiquetagem unificado do Azure Information Protection requer a versão mínima do Microsoft .NET Framework 4.6.2 e se esta estiver em falta, o instalador tentará transferir e instalar este pré-requisito. Quando este pré-requisito é instalado como parte da instalação do cliente, o seu computador tem de ser reiniciado.

- Se tiver o Windows 7 SP1, o cliente de etiquetagem unificado do Azure Information Protection requer uma atualização específica, KB 2533623. Se seu PC precisa desta atualização, mas não estiver instalado, a instalação estiver concluída, mas com uma mensagem que o Azure Information Protection unified cliente etiquetagem requer esta atualização. Até que esta atualização é instalada, não será possível utilizar todas as funcionalidades do cliente etiquetagem unificada do Azure Information Protection. 

## <a name="to-download-and-install-the-azure-information-protection-unified-labeling-client"></a>Para transferir e instalar o cliente de etiquetagem unificado do Azure Information Protection

Antes de instalar o cliente de etiquetagem unificado do Azure Information Protection, certifique-se que publicou etiquetas de sensibilidade na segurança do Office 365 e o Centro de conformidade, ou o Centro de segurança do Microsoft 365 e o Centro de conformidade do Microsoft 365. 

Se tiver etiquetas que são publicadas atualmente a partir do portal do Azure para o Azure Information Protection, pode [migrar estas etiquetas](../configure-policy-migrate-labels.md) para o administrador de datacenters.

1. Transferir o cliente de pré-visualização a partir da [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=57440).

2. Execute o ficheiro executável que foi transferido **AzInfoProtection_For_Unified_Labeling.exe**. Se lhe for pedido para continuar, clique em **Sim**.    

3. Sobre o **instalar o cliente do Azure Information Protection** página, clique em **concordo** quando tiver lido os termos de licenciamento e condições.

4. Se lhe for pedido para continuar, clique em **Sim**e aguarde a conclusão da instalação.

6. Clique em **Fechar**. Antes de começar a utilizar o Azure Information Protection unified cliente etiquetagem:

    - Se o computador estiver a executar o Office 2010, reinicie o computador e, em seguida, avance para a próxima secção para o seu passo final.    
        
    - Para outras versões do Office, reinicie todas as aplicações do Office e todas as instâncias do Explorador de Ficheiros. A instalação está agora concluída e pode utilizar o cliente para identificar e proteger os seus documentos e e-mails.

### <a name="installing-the-azure-information-protection-unified-labeling-client-with-office-2010"></a>Instalar o Azure Information Protection unified etiquetagem cliente com o Office 2010

Depois de instalar o Azure Information Protection unified etiquetagem cliente ao utilizar as instruções anteriores:

1. Abra o Microsoft Word. Se esta for a primeira vez que executa uma aplicação do Office 2010 após ter instalado o cliente do Azure Information Protection, verá uma caixa de diálogo **Microsoft Azure Information Protection**. A caixa de diálogo indica que são necessárias credenciais de administrador para concluir o processo de início de sessão.

2. Na caixa de diálogo **Microsoft Azure Information Protection**, clique em **OK**.

3. Se vir a caixa de diálogo **Controlo de Acesso do Utilizador** clique em **Sim** para o cliente do Azure Information Protection poder atualizar o registo.

A instalação está agora concluída e pode utilizar o cliente de etiquetagem unificado do Azure Information Protection para identificar e proteger os seus documentos e e-mails.

## <a name="next-steps"></a>Passos Seguintes

Para saber que mais sobre a etiquetagem unificada armazenam que no Centro de administração utilização, leia a seguinte mensagem de blogue: [Anunciando a disponibilidade do unified a etiquetagem de gestão no Centro de conformidade e segurança do](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492).
