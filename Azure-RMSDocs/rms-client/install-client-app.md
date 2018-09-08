---
title: Transferir e instalar o cliente do Azure Information Protection
description: Instruções para os utilizadores instalarem o cliente do Azure Information Protection para Windows, para que possa classificar e proteger os seus documentos e e-mails.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/31/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: be7ae3dd29034813e9b0b4475407f68c8685c167
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44147933"
---
# <a name="user-guide-download-and-install-the-azure-information-protection-client"></a>Guia de utilizador: Transferir e instalar o cliente do Azure Information Protection

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

Se o seu administrador não lhe instalar o Azure Information Protection, pode fazê-lo por si mesmo. Tem de ser administrador local do seu PC para instalar este cliente, de forma a que o mesmo possa etiquetar e proteger os seus documentos e e-mails.

Além disso:

- O cliente do Azure Information Protection requer a versão mínima do Microsoft .NET Framework 4.6.2. Se esta versão estiver em falta, o instalador tentará transferir e instalar este pré-requisito. Quando este pré-requisito é instalado como parte da instalação do cliente, o seu computador tem de ser reiniciado.

- Se tiver o Windows 7 SP1, o cliente do Azure Information Protection precisará de uma atualização específica, KB 2533623. Se o PC precisar desta atualização, mas não estiver instalada, a instalação será concluída, mas com uma mensagem a indicar que o cliente do Azure Information Protection precisa desta atualização. Até esta atualização estar instalada, não poderá utilizar todas as funcionalidades do cliente do Azure Information Protection. 

## <a name="to-download-and-install-the-azure-information-protection-client"></a>Para transferir e instalar o cliente do Azure Information Protection    

1.  Aceda à página do [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) no Web site da Microsoft.

    Esta página tem ligações para todos os dispositivos populares que poderá utilizar, para poder transferir facilmente uma aplicação de visualização, se for necessária para abrir os ficheiros protegidos. Se não for administrador local do seu PC, pode sempre instalar a aplicação de visualizador para Windows. No entanto, estas instruções são para instalar o cliente completo, o qual lhe permite etiquetar e proteger ficheiros. 

2. Localize a secção **cliente do Azure Information Protection** e clique no ícone do Windows. Clique em **Transferir** e guarde o ficheiro **AzInfoProtection.exe**.     

3. Execute o ficheiro executável que foi transferido. Se lhe for pedido para continuar, clique em **Sim**.    

4. Na página **Instalar o cliente do Azure Information Protection**:     
    - Selecione a opção para instalar uma política de demonstração se não puder ligar-se à cloud, mas pretender ver e experimentar o lado do cliente do Azure Information Protection com uma política local para efeitos de demonstração. Quando o cliente se liga a um serviço Azure Information Protection, esta política de demonstração é substituída pela política do Azure Information Protection da organização.    

    - Clique em **Concordo** quando tiver lido os termos e as condições de licenciamento.    

5. Se lhe for pedido para continuar, clique em **Sim**e aguarde a conclusão da instalação.    

6. Clique em **Fechar**. Antes de começar a utilizar o cliente do Azure Information Protection:    

    - Se o computador estiver a executar o Office 2010, reinicie o computador e, em seguida, avance para a próxima secção para o seu passo final.    
        
    - Para outras versões do Office, reinicie todas as aplicações do Office e todas as instâncias do Explorador de Ficheiros. A instalação está agora concluída e pode utilizar o cliente para identificar e proteger os seus documentos e e-mails.    

### <a name="installing-the-azure-information-protection-client-with-office-2010"></a>Instalar o cliente do Azure Information Protection com o Office 2010    
Depois de ter instalado o cliente do Azure Information Protection através das instruções anteriores:    

1. Abra o Microsoft Word. Se esta for a primeira vez que executa uma aplicação do Office 2010 após ter instalado o cliente do Azure Information Protection, verá uma caixa de diálogo **Microsoft Azure Information Protection**. A caixa de diálogo indica que são necessárias credenciais de administrador para concluir o processo de início de sessão.

2. Na caixa de diálogo **Microsoft Azure Information Protection**, clique em **OK**.

3. Se vir a caixa de diálogo **Controlo de Acesso do Utilizador** clique em **Sim** para o cliente do Azure Information Protection poder atualizar o registo.

A instalação está agora concluída e pode utilizar o Azure Information Protection para identificar e proteger os seus documentos e e-mails.

## <a name="other-instructions"></a>Outras instruções    
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

- [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Informações adicionais para administradores    
Ver [instalar o cliente do Azure Information Protection para os utilizadores](client-admin-guide-install.md) partir a [Guia do administrador](client-admin-guide.md).
 
  
