---
title: Transferir e instalar o cliente etiquetagem unificado (pré-visualização) do Azure Information Protection
description: Instruções para os utilizadores instalarem a versão de pré-visualização do Azure Information Protection unified cliente etiquetagem para o Windows, para que possa classificar e proteger os seus documentos e e-mails.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/17/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 5d2f5c07ebc7f4844b0d35879ae00c7b9066cb6d
ms.sourcegitcommit: 6a732226a3c97fc06fcf815fbbb24a2e2faae209
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2018
ms.locfileid: "49359044"
---
# <a name="download-and-install-the-azure-information-protection-unified-labeling-client-preview"></a>Transferir e instalar o cliente etiquetagem unificado (pré-visualização) do Azure Information Protection

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

> [!NOTE]
> Este cliente está em pré-visualização e está sujeitas a alterações. Ele utiliza o armazenamento de etiquetagem unificado e transfere a política com as etiquetas de sensibilidade do Centro de conformidade e segurança do Office 365. Para utilizar estas etiquetas, eles devem primeiro ser publicados a partir do Centro de conformidade e segurança do. [Mais informações](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492)

Tem de ser um administrador local no seu PC para instalar este cliente de pré-visualização, para que o mesmo possa Etiquetar e proteger os seus documentos e e-mails.

Além disso:

- O cliente de etiquetagem unificado do Azure Information Protection requer a versão mínima do Microsoft .NET Framework 4.6.2 e se esta estiver em falta, o instalador tentará transferir e instalar este pré-requisito. Quando este pré-requisito é instalado como parte da instalação do cliente, o seu computador tem de ser reiniciado.

- Se tiver o Windows 7 SP1, o cliente de etiquetagem unificado do Azure Information Protection requer uma atualização específica, KB 2533623. Se seu PC precisa desta atualização, mas não estiver instalado, a instalação estiver concluída, mas com uma mensagem que o Azure Information Protection unified cliente etiquetagem requer esta atualização. Até que esta atualização é instalada, não será possível utilizar todas as funcionalidades do cliente etiquetagem unificada do Azure Information Protection. 

## <a name="to-download-and-install-the-azure-information-protection-unified-labeling-client"></a>Para transferir e instalar o cliente de etiquetagem unificado do Azure Information Protection

Antes de instalar o cliente de etiquetagem unificado do Azure Information Protection, confirme se tem etiquetas de sensibilidade no Centro de conformidade de segurança do Office 365 e que são publicadas para utilizadores. 

Se tiver etiquetas que são publicadas atualmente a partir do portal do Azure para o Azure Information Protection, pode [migrar estas etiquetas](../configure-policy-migrate-labels.md) para o Centro de conformidade e segurança.

1. Transferir o cliente de pré-visualização a partir da [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=57440).

2. Execute o ficheiro executável que foi transferido **AzInfoProtection_For_Unified_Labeling.exe**. Se lhe for pedido para continuar, clique em **Sim**.    

3. Na página **Instalar o cliente do Azure Information Protection**:     
    - Selecione a opção para instalar uma política de demonstração se não puder ligar-se à cloud, mas pretender ver e experimentar o lado do cliente do Azure Information Protection com uma política local para efeitos de demonstração. Quando o cliente liga-se para o Centro de conformidade e segurança do Office 365, esta política de demonstração é substituída com a política de etiqueta da sua organização.

    - Clique em **Concordo** quando tiver lido os termos e as condições de licenciamento.    

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

## <a name="next-steps"></a>Próximos passos

Para saber mais sobre a etiquetagem unificada armazenam que a segurança do Office 365 e a conformidade center utiliza agora, leia a seguinte mensagem de blogue: [anunciar a disponibilidade do unified a etiquetagem de gestão no Centro de conformidadeeasegurança](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492).

