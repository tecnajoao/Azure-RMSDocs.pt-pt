---
title: Ver e utilizar documentos protegidos com o cliente do AIP
description: Instruções para ver e utilizar um documento protegido que requer que tenha o cliente do Azure Information Protection instalado.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/17/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: eb631b0153ce047177ef12887c025303acfac1db
ms.sourcegitcommit: c207a2f592d167a4a0b6c4427259683e2087f143
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/18/2018
ms.locfileid: "31441867"
---
# <a name="user-guide-view-and-use-files-that-have-been-protected-by-rights-management"></a>Guia do utilizador: Ver e utilizar ficheiros que foram protegidos pelo Rights Management

>*Aplica-se a: serviços de gestão de direitos do Active Directory [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

Na maioria das vezes, pode ver um documento protegido. Para tal, basta abri-lo. Por exemplo, pode fazer duplo clique num anexo numa mensagem de e-mail ou num ficheiro no Explorador de Ficheiros ou pode clicar numa ligação para um ficheiro.

Se os ficheiros não abrem imediatamente, o **Visualizador do Azure Information Protection** poderá abri-lo. Este visualizador pode abrir ficheiros de texto protegido, ficheiros de imagem protegidos, ficheiros PDF protegidos e todos os ficheiros que têm uma extensão de nome de ficheiro **.pfile**.

O visualizador é instalado automaticamente como parte do cliente do Azure Information Protection ou pode instalá-lo em separado. Pode instalar o cliente e o visualizador a partir da página [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft. Para obter mais informações sobre como instalar o cliente, veja [Transferir e instalar o cliente do Azure Information Protection](install-client-app.md).

> [!NOTE]
> Apesar de a instalação do cliente proporcionar mais funcionalidades, requer permissões de administrador local e a funcionalidade completa requer um serviço correspondente para a sua organização:
> 
>-Azure Information Protection
> 
>-As do azure Rights Management
> 
>-Serviços de gestão de direitos do Active Active Directory 
> 
> Instale o visualizador se lhe tiver sido enviado um documento protegido por alguém de outra organização ou se não tiver permissões de administrador local no seu PC.

Para poder abrir um documento protegido, a aplicação deve ser "Habilitada para RMS". As aplicações do Office e o Visualizador do Azure Information Protection são exemplos de aplicações habilitadas para RMS. Para ver uma lista de aplicações por tipo e os dispositivos suportados, veja a tabela [Aplicações habilitadas para RMS](../get-started/requirements-applications.md#rms-enlightened-applications).  
## <a name="messagerpmsg-as-an-email-attachment"></a>Message.rpmsg como um anexo de e-mail

Se vir **message.rpmsg** como um anexo de ficheiro num e-mail, este ficheiro não é um documento protegido, mas uma mensagem de e-mail protegida apresentada como um anexo. Não pode utilizar o Visualizador do Azure Information Protection para Windows para ver esta mensagem de e-mail protegida no seu PC Windows. Em vez disso, terá uma aplicação de e-mail para o Windows que suporta a proteção Rights Management, como o Outlook do Office. Ou pode utilizar o Outlook na Web.

No entanto, se tiver um dispositivo iOS ou Android, pode utilizar a aplicação do Azure Information Protection para abrir estas mensagens de e-mail protegidas. Pode transferir esta aplicação para estes dispositivos móveis a partir da página [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft.

## <a name="prompts-for-authentication"></a>Pedidos de autenticação

Para poder ver o ficheiro protegido, o serviço Rights Management que foi utilizado para proteger o ficheiro tem de confirmar primeiro que está autorizado a ver o ficheiro. O serviço não esta confirmação verificando o seu nome de utilizador e palavra-passe. Em alguns casos, estas credenciais podem ser colocadas em cache e não vir uma linha de comandos pede-lhe para iniciar sessão. Noutros casos, lhe for pedido para fornecer as suas credenciais.

Se a sua organização tiver uma conta baseada na nuvem para a utilização (para Office 365 ou do Azure) e não utiliza uma versão equivalente no local (AD RMS), tem duas opções:

- Se foi enviada uma mensagem de e-mail protegida, siga as instruções para iniciar sessão com o fornecedor de identidade sociais (tais como o Google para uma conta do Gmail) ou aplicar para um código de acesso único.

- Pode aplicar-se numa conta gratuita que aceitará as suas credenciais para que pode abrir documentos que estão protegidos pelo Rights Management. Para se candidatar a esta conta, clique na ligação para se candidatar [RMS para indivíduos](http://go.microsoft.com/fwlink/?LinkId=309469) e utilizar o seu endereço de e-mail da empresa em vez de um endereço de e-mail pessoal. 

## <a name="to-view-and-use-a-protected-document"></a>Para ver e utilizar um documento protegido

1. Abra o ficheiro protegido (por exemplo, ao fazer duplo clique no ficheiro ou anexo ou ao clicar na ligação para o ficheiro). Se lhe for pedido que selecione uma aplicação, selecione **Visualizador do Azure Information Protection**. 

2. Se vir uma página para **Iniciar sessão** ou **Inscrever-se**: clique em **Iniciar sessão** e introduza as suas credenciais. Se o ficheiro protegido tiver sido enviado para si como um anexo, especifique o mesmo endereço de e-mail que foi utilizado para enviar o ficheiro.
    
    Se não tiver uma conta válida, veja a secção [Pedidos de autenticação](#prompts-for-authentication) nesta página.

3. Uma versão só de leitura do ficheiro é aberta no **Visualizador do Azure Information Protection**. Se tiver permissões suficientes, pode imprimir o ficheiro e editá-lo. 

    Pode verificar as suas permissões para o ficheiro clicar em **Permissões**. Na caixa de diálogo **Permissões**, também pode identificar o proprietário do ficheiro para o contactar caso pretenda solicitar uma nova versão do ficheiro com permissões adicionais.
    
    Para obter mais informações detalhadas sobre as permissões e os direitos de utilização de cada um, veja [Direitos incluídos nos níveis de permissões](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels).

4. Para editar o ficheiro, clique em **guardar como**, que lhe permite guardar o ficheiro sem a etiqueta e com sem proteção para a extensão de nome de ficheiro original. Em seguida, pode editar o ficheiro com a aplicação associada a esse tipo de ficheiro. 
    
    Quando acabar de editar o ficheiro no Explorador de ficheiros, faça duplo clique no ficheiro para voltar a aplicar a etiqueta, que por sua vez volta a proteção.

5. Se tiver ficheiros protegidos adicionais para abrir, pode navegar diretamente até aos mesmos a partir do visualizador, através da opção **Abrir**. O ficheiro selecionado substitui o ficheiro original no visualizador. 

> [!TIP]
> Se o ficheiro protegido não for aberto e tenham o cliente Azure Information Protection completo instalado, tente o **repor definições** opção. Para aceder a esta opção, a partir de uma aplicação do Office, selecione o **proteger** botão > **ajuda e comentários** > **repor definições**. 
> 
> [Obter mais informações sobre a opção Repor definições](client-admin-guide.md#more-information-about-the-reset-settings-option)

## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

-   [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]