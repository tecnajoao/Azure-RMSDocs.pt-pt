---
title: Ver e utilizar ficheiros protegidos | Azure Information Protection
description: "Instruções para ver e utilizar um ficheiro protegido que requer que tenha o cliente do Azure Information Protection instalado."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/10/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5fcd31a570fbd22a488d0a016dd3d3887918f755
ms.openlocfilehash: 123fc7078e29ca59174d349efb2366df2f39e023


---

# <a name="view-and-use-files-that-have-been-protected-by-rights-management"></a>Ver e utilizar ficheiros que foram protegidos pelo Rights Management

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8 e Windows 7 com SP1*

Na maioria das vezes, pode ver um ficheiro protegido. Para tal, basta abri-lo. Por exemplo, pode fazer duplo clique num anexo numa mensagem de e-mail ou num ficheiro no Explorador de Ficheiros ou pode clicar numa ligação para um ficheiro.

Se o ficheiro não abrir, pode utilizar o **Visualizador do Azure Information Protection** para o abrir. Este visualizador é instalado automaticamente como parte do cliente do Azure Information Protection ou pode instalá-lo em separado. Pode instalar o cliente e o visualizador a partir da página [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft. Para obter mais informações sobre como instalar o cliente, veja [Transferir e instalar o cliente do Azure Information Protection](install-client-app.md).

> [!NOTE]
> Apesar de a instalação do cliente proporcionar mais funcionalidades, requer permissões de administrador local e a funcionalidade completa requer um serviço correspondente para a sua organização:
> 
> - Azure Information Protection
> 
> - Azure Rights Management
> 
> - Serviços de Gestão de Direitos do Active Directory 
> 
> Instale o visualizador se lhe tiver sido enviado um documento protegido por alguém de outra organização ou se não tiver permissões de administrador local no seu PC.

## <a name="prompts-for-authentication"></a>Pedidos de autenticação

Para poder ver o ficheiro protegido, o serviço Rights Management que foi utilizado para proteger o ficheiro tem de confirmar primeiro que está autorizado a ver o ficheiro. O serviço fá-lo ao verificar o seu nome de utilizador e palavra-passe. Em alguns casos, estas informações podem estar em cache e não lhe são pedidas as suas credenciais. Noutros casos, ser-lhe-á pedido que forneça as credenciais.

Se a sua organização não tiver uma conta baseada na cloud que possa utilizar (para o Office 365 ou Azure) e não utilizar uma versão no local equivalente (AD RMS), pode candidatar-se a uma conta gratuita que aceitará as suas credenciais para que possa abrir ficheiros que estão protegidos pelo Rights Management:

-   Para se candidatar a esta conta, clique na ligação para aderir ao [RMS para indivíduos](http://go.microsoft.com/fwlink/?LinkId=309469).
    
    Quando se inscrever, utilize o seu endereço de e-mail da empresa em vez de um endereço de e-mail pessoal. Caso se esteja a inscrever porque recebeu um anexo protegido, utilize o mesmo endereço de e-mail que foi utilizado para lhe enviar a mensagem de e-mail.
    
-   Para obter mais informações, consulte [RMS para indivíduos e Azure Rights Management](../understand-explore/rms-for-individuals.md).

## <a name="to-view-and-use-a-protected-file"></a>Para ver e utilizar um ficheiro protegido

1. Abra o ficheiro protegido (por exemplo, ao fazer duplo clique no ficheiro ou anexo ou ao clicar na ligação para o ficheiro). Se lhe for pedido que selecione uma aplicação, selecione **Visualizador do Azure Information Protection**. 

2. Se vir uma página para **Iniciar sessão** ou **Inscrever-se**: clique em **Iniciar sessão** e introduza as suas credenciais. Se o ficheiro protegido tiver sido enviado para si como um anexo, especifique o mesmo endereço de e-mail que foi utilizado para enviar o ficheiro.
    
    Se não tiver uma conta válida, veja a secção [Pedidos de autenticação](#prompts-for-authentication) nesta página. Inscreva-se para obter uma conta gratuita e regresse a estas instruções.

3. Uma versão só de leitura do ficheiro é aberta no **Visualizador do Azure Information Protection**. Se tiver permissões suficientes, pode imprimir o ficheiro e editá-lo. 

    Pode verificar as suas permissões para o ficheiro clicar em **Permissões**. Na caixa de diálogo **Permissões**, também pode identificar o proprietário do ficheiro para o contactar caso pretenda solicitar uma nova versão do ficheiro com permissões adicionais.
    
    Para obter mais informações detalhadas sobre as permissões e os direitos de utilização de cada um, veja [Direitos incluídos nos níveis de permissões](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels).

4. Para editar o ficheiro, clique em **Guardar como**, o que lhe permite guardar o ficheiro sem proteção na sua extensão de nome de ficheiro original. Em seguida, pode editar o ficheiro com a aplicação associada a esse tipo de ficheiro.

5. Se tiver ficheiros protegidos adicionais para abrir, pode navegar diretamente até aos mesmos a partir do visualizador, através da opção **Abrir**. O ficheiro selecionado substitui o ficheiro original no visualizador. 

> [!TIP]
> Se o ficheiro protegido não abrir, transfira e utilize a [Ferramenta RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Siga as instruções na ferramenta para verificar se existem problemas no seu computador que possam impedir que um documento protegido seja aberto.


## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

-   [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Feb17_HO2-->


