---
title: Ver e utilizar documentos protegidos com o cliente do AIP
description: Instruções para ver e utilizar um documento protegido que requer que tenha o cliente do Azure Information Protection instalado.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/08/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3b4dfc62950166ca7221002169005fa3693a5998
ms.sourcegitcommit: e70bb1a02e96d701fd5ae2a25536fa485bbf2e87
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/08/2018
ms.locfileid: "48862096"
---
# <a name="user-guide-view-and-use-files-that-have-been-protected-by-rights-management"></a>Guia de utilizador: Ver e utilizar ficheiros que foram protegidos pelo Rights Management

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1*

Na maioria das vezes, pode ver um documento protegido. Para tal, basta abri-lo. Por exemplo, pode fazer duplo clique num anexo numa mensagem de e-mail ou num ficheiro no Explorador de Ficheiros ou pode clicar numa ligação para um ficheiro.

Se os ficheiros não abrem imediatamente, o **Visualizador do Azure Information Protection** poderá conseguir abri-lo. Este visualizador pode abrir ficheiros de texto protegido, ficheiros de imagem protegidos, ficheiros PDF protegidos e todos os ficheiros que têm uma extensão de nome de ficheiro **.pfile**.

O visualizador é instalado automaticamente como parte do cliente do Azure Information Protection ou pode instalá-lo em separado. Pode instalar o cliente e o visualizador a partir da página [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft. Para obter mais informações sobre como instalar o cliente, veja [Transferir e instalar o cliente do Azure Information Protection](install-client-app.md).

> [!NOTE]
> Embora a instalação do cliente proporciona mais funcionalidades, requer permissões de administrador local e a funcionalidade completa requer um serviço correspondente para a sua organização. Por exemplo, o Azure Information Protection ou serviços de gestão de direitos do Active Directory.
> 
> Instale o visualizador se lhe tiver sido enviado um documento protegido por alguém de outra organização ou se não tiver permissões de administrador local no seu PC.

Para poder abrir um documento protegido, a aplicação deve ser "Habilitada para RMS". Aplicações do Office e o Visualizador do Azure Information Protection são exemplos de aplicações otimizadas por RMS. Para ver uma lista de aplicações por tipo e os dispositivos suportados, veja a tabela [Aplicações habilitadas para RMS](../requirements-applications.md#rms-enlightened-applications).  
## <a name="messagerpmsg-as-an-email-attachment"></a>Message.rpmsg como um anexo de e-mail

Se vir **message.rpmsg** como um anexo de ficheiro num e-mail, este ficheiro não é um documento protegido, mas uma mensagem de e-mail protegida apresentada como um anexo. Não é possível utilizar o Visualizador do Azure Information Protection para Windows para ver esta mensagem de e-mail protegida no seu PC Windows. Em vez disso, precisa de uma aplicação de e-mail para o Windows que suporta a proteção do Rights Management, como o Outlook do Office. Ou pode utilizar o Outlook na Web.

No entanto, se tiver um dispositivo iOS ou Android, pode utilizar a aplicação do Azure Information Protection para abrir estas mensagens de e-mail protegidas. Pode transferir esta aplicação para estes dispositivos móveis a partir da página [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft.

## <a name="prompts-for-authentication"></a>Pedidos de autenticação

Para poder ver o ficheiro protegido, o serviço Rights Management que foi utilizado para proteger o ficheiro tem de confirmar primeiro que está autorizado a ver o ficheiro. O serviço faz essa confirmação ao verificar o seu nome de utilizador e palavra-passe. Em alguns casos, estas credenciais podem ser colocados em cache e não vir uma linha de comandos que lhe pede para iniciar sessão. Em outros casos, é solicitado que forneça as credenciais.

Se a sua organização não tiver uma conta com base na cloud para que possa utilizar (para o Office 365 ou Azure) e utilizar uma versão no local equivalente (AD RMS), tem duas opções:

- Se foram enviados um e-mail protegido, siga as instruções para iniciar sessão com o seu fornecedor de identidade social (por exemplo, o Google para uma conta do Gmail) ou Inscreva-se um código de acesso único.

- Pode aplicar-se numa conta gratuita que aceitará as suas credenciais, para que possa abrir documentos que estão protegidos pelo Rights Management. Para se candidatar a esta conta, clique na ligação para se candidatar [RMS para indivíduos](http://go.microsoft.com/fwlink/?LinkId=309469) e usar seu endereço de e-mail da empresa, em vez de um endereço de e-mail pessoal. 

## <a name="to-view-and-use-a-protected-document"></a>Para ver e utilizar um documento protegido

1. Abra o ficheiro protegido (por exemplo, ao fazer duplo clique no ficheiro ou anexo ou ao clicar na ligação para o ficheiro). Se lhe for pedido que selecione uma aplicação, selecione **Visualizador do Azure Information Protection**. 

2. Se vir uma página para **Iniciar sessão** ou **Inscrever-se**: clique em **Iniciar sessão** e introduza as suas credenciais. Se o ficheiro protegido tiver sido enviado para si como um anexo, especifique o mesmo endereço de e-mail que foi utilizado para enviar o ficheiro.
    
    Se não tiver uma conta válida, veja a secção [Pedidos de autenticação](#prompts-for-authentication) nesta página.

3. Uma versão só de leitura do ficheiro é aberta no **Visualizador do Azure Information Protection**. Se tiver permissões suficientes, pode imprimir o ficheiro e editá-lo. 

    Pode verificar as suas permissões para o ficheiro clicar em **Permissões**. Na caixa de diálogo **Permissões**, também pode identificar o proprietário do ficheiro para o contactar caso pretenda solicitar uma nova versão do ficheiro com permissões adicionais.
    
    Para obter mais informações detalhadas sobre as permissões e os direitos de utilização de cada um, veja [Direitos incluídos nos níveis de permissões](../configure-usage-rights.md#rights-included-in-permissions-levels).

4. Para editar o ficheiro, clique em **guardar como**, que lhe permite guardar o ficheiro protegido para a extensão de nome de ficheiro original. Em seguida, pode editar o ficheiro com a aplicação associada a esse tipo de ficheiro. Neste momento, o rótulo e a proteção do ficheiro é removido.
    
    Observe que, dado que o Visualizador para ficheiros protegidos, o **guardar como** botão está habilitado apenas para ficheiros protegidos.
    
5. Quando terminar de editar o ficheiro no Explorador de ficheiros, faça duplo clique no ficheiro para voltar a aplicar a etiqueta. Esta ação volta a aplicar a proteção.

6. Se tiver ficheiros protegidos adicionais para abrir, pode navegar diretamente até aos mesmos a partir do visualizador, através da opção **Abrir**. O ficheiro selecionado substitui o ficheiro original no visualizador. 

> [!TIP]
> Se o ficheiro protegido não abre, pelo que tenham o cliente do Azure Information Protection completo instalado, experimente o **repor definições** opção. Para aceder a esta opção, a partir de uma aplicação do Office, selecione o **Protect** botão > **ajuda e Feedback** > **repor definições**. 
> 
> [Obter mais informações sobre a opção de repor definições](client-admin-guide.md#more-information-about-the-reset-settings-option)

## <a name="other-instructions"></a>Outras instruções
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

-   [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

