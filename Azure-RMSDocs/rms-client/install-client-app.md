---
title: Transferir e instalar o cliente do Azure Information Protection | Azure Information Protection
description: "Instruções para os utilizadores instalarem o cliente do Azure Information Protection para Windows, para que possa classificar e proteger os seus documentos e e-mails."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 22af60687ad030e686ba843ced6d450487353a0e
ms.openlocfilehash: 72266181c5334ed7e03b2022df61c4065f1c3ac7


---

# <a name="download-and-install-the-azure-information-protection-client"></a>Transferir e instalar o cliente do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8 e Windows 7 com SP1*

**[Esta versão do cliente está em pré-visualização e está sujeita a alterações.]**

Se o seu administrador não lhe instalar o Azure Information Protection, pode fazê-lo por si mesmo. Tem de ser um administrador local no seu PC para instalar este cliente. 

### <a name="office-2010-only"></a>Apenas para Office 2010

Quando utilizar esta versão do Office, o cliente do Azure Information Protection tem de configurar chaves de registo que requerem permissões de administrador: 

Utilize as instruções para transferir e instalar o cliente e, em seguida, utilize as instruções na secção seguinte para o Office 2010.

## <a name="to-download-and-install-the-azure-information-protection-client"></a>Para transferir e instalar o cliente do Azure Information Protection

1.  Aceda ao [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018) e transfira a versão de **pré-visualização** do cliente do Azure Information Protection.

2. Faça duplo clique no ficheiro executável transferido. 

3. Na página **Instalar o cliente do Azure Information Protection**: 
    
    - Selecione a opção para instalar uma política de demonstração se não puder ligar-se à nuvem, mas pretender ver e experimentar o lado do cliente do Azure Information Protection com uma política local para efeitos de demonstração. Quando o cliente se liga a um serviço do Azure Information Protection, esta política de demonstração é substituída pela política do Azure Information Protection da organização.
    
    - Clique em **Concordo** quando tiver lido os termos e as condições de licenciamento.

4. Se lhe for pedido para continuar, clique em **Sim**e aguarde a conclusão da instalação.

3. Clique em **Fechar**. Antes de começar a utilizar o cliente do Azure Information Protection:

    - Se o computador estiver a executar o Office 2010, reinicie o computador e, em seguida, avance para a próxima secção para o seu passo final.
    
    - Para outras versões do Office, reinicie todas as aplicações do Office e todas as instâncias do Explorador de Ficheiros. A instalação está agora concluída e pode utilizar o cliente para identificar e proteger os seus documentos e e-mails.

> [!NOTE]
> Se tiver o Windows 7 SP1, o cliente do Azure Information Protection precisa de uma atualização específica [KB 2533623](https://support.microsoft.com/en-us/kb/2533623). Se o seu PC precisar dessa atualização, mas não estiver instalada, quando tentar utilizar o cliente, verá uma mensagem a informar que é preciso instalar essa atualização antes de poder utilizar todas as funcionalidades do cliente do Azure Information Protection.

### <a name="installing-the-azure-information-protection-client-with-office-2010"></a>Instalar o cliente do Azure Information Protection com o Office 2010

Depois de ter instalado o cliente do Azure Information Protection através das instruções anteriores:

1. Abra o Microsoft Word. Se esta for a primeira vez que executa uma aplicação do Office 2010 após ter instalado o cliente do Azure Information Protection, verá uma caixa de diálogo **Microsoft Azure Information Protection**. A caixa de diálogo indica que são necessárias credenciais de administrador para concluir o processo de início de sessão.

2. Na caixa de diálogo **Microsoft Azure Information Protection**, clique em **OK**.

2. Se vir a caixa de diálogo **Controlo de Acesso do Utilizador** clique em **Sim** para o cliente do Azure Information Protection poder atualizar o registo.

A instalação está agora concluída e pode utilizar o Azure Information Protection para identificar e proteger os seus documentos e e-mails.

## <a name="other-instructions"></a>Outras instruções
Para obter instruções sobre os procedimentos, veja as secções seguintes do guia do utilizador do Azure Information Protection:

-   [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Informações adicionais para administradores
[Instalar o cliente do Azure Information Protection](info-protect-client.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


