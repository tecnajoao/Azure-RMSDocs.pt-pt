---
title: Transferir e instalar o cliente do Azure Information Protection | Azure Information Protection
description: "Instruções para os utilizadores instalarem o cliente do Azure Information Protection para Windows, para que possa classificar e proteger os seus documentos e e-mails."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 633f3dfe12828a21943bb5faf6ad9f69b98fc70b
ms.openlocfilehash: 303ca72fa8753e417b4a06b4cad475559295eb2a


---

# <a name="download-and-install-the-azure-information-protection-client"></a>Transferir e instalar o cliente do Azure Information Protection

Se o seu administrador não lhe instalar o Azure Information Protection, pode fazê-lo por si mesmo. Tem de ser um administrador local no seu PC para instalar este cliente. 

Além disso:

- O cliente do Azure Information Protection requer a versão mínima do Microsoft .NET Framework 4.6.2. Se esta versão estiver em falta, o instalador tentará transferir e instalar este pré-requisito. Quando este pré-requisito é instalado como parte da instalação do cliente, o seu computador tem de ser reiniciado.

- Se tiver o Windows 7 SP1, o cliente do Azure Information Protection precisa de uma atualização específica [KB 2533623](https://support.microsoft.com/kb/2533623). Se o seu PC precisar desta atualização, mas não estiver instalada, a instalação é concluída, mas verá uma mensagem a informar que é preciso instalar esta atualização antes de poder utilizar todas as funcionalidades do Azure Information Protection. 

## <a name="to-download-and-install-the-azure-information-protection-client"></a>Para transferir e instalar o cliente do Azure Information Protection    

1.  Aceda à página do [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) no Web site da Microsoft.    
2. Clique no ícone do Windows para o **cliente do Azure Information Protection** e guarde o ficheiro **AzInfoProtection.exe** para instalar o cliente do Azure Information Protection.     

2. Faça duplo clique no ficheiro executável transferido. Se lhe for pedido para continuar, clique em **Sim**.    

3. Na página **Instalar o cliente do Azure Information Protection**:     
    - Selecione a opção para instalar uma política de demonstração se não puder ligar-se à nuvem, mas pretender ver e experimentar o lado do cliente do Azure Information Protection com uma política local para efeitos de demonstração. Quando o cliente se liga a um serviço do Azure Information Protection, esta política de demonstração é substituída pela política do Azure Information Protection da organização.    

    - Clique em **Concordo** quando tiver lido os termos e as condições de licenciamento.    

4. Se lhe for pedido para continuar, clique em **Sim**e aguarde a conclusão da instalação.    

3. Clique em **Fechar**. Antes de começar a utilizar o cliente do Azure Information Protection:    

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
Veja [Como instalar o cliente do Azure Information Protection para os utilizadores](client-admin-guide.md#how-to-install-the-azure-information-protection-client-for-users) no guia do administrador.
 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]  



<!--HONumber=Feb17_HO2-->


