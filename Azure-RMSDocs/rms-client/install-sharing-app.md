---
title: Transferir e instalar a aplicação de partilha RMS – AIP
description: Instruções para instalar interativamente a aplicação de partilha RMS para Windows, para que possa partilhar documentos com outras pessoas de forma segura.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 89900a1231ec4a5a6458287cf5580bf0ad5f28b1
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804538"
---
# <a name="download-and-install-the-rights-management-sharing-application"></a>Transferir e instalar a aplicação de partilha Rights Management

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 com SP1, Windows 8, Windows 8.1*

> [!IMPORTANT]
> **Notificação de fim do suporte**: a aplicação de partilha Rights Management para Windows está a ser substituída pelo [cliente do Azure Information Protection](aip-client.md). O suporte para esta aplicação mais antiga será interrompido 31 de Janeiro de 2019.

Não é necessário ser um administrador local para instalar a aplicação de partilha RMS. No entanto, se não for e utilizar o Office 2010, existem algumas limitações. Para obter mais informações, consulte a secção [Se não for um administrador local e utilizar o Office 2010](#if-you-are-not-a-local-administrator-and-use-office-2010) nesta página.

## <a name="to-download-and-install-the-rights-management-sharing-application"></a>Para transferir e instalar a aplicação de partilha Rights Management

1.  Aceda à página do [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) no site da Microsoft.

2.  Na secção **Computadores**, clique no ícone da **aplicação RMS para Windows** e guarde o ficheiro **Setup.exe** para instalar a aplicação de partilha Microsoft Rights Management.

3.  Faça duplo clique no ficheiro Setup.exe transferido. Se lhe for pedido para continuar, clique em **Sim**.

4.  Na página **Configurar o Microsoft RMS**, clique em **Seguinte** e aguarde até que a instalação esteja concluída.

    > [!NOTE]
    > A aplicação de partilha RMS requer o Microsoft .NET Framework, versão mínima 4.0. A configuração verifica se isto foi instalado e, em caso negativo, verá uma mensagem com uma ligação para a instalação.

5.  Quando a instalação estiver concluída, clique em **Reiniciar** para reiniciar o computador e concluir a instalação. Em alternativa, pode clicar em **Fechar** e reiniciar o computador mais tarde para concluir a instalação.

Agora, está pronto para começar a proteger os ficheiros ou ler ficheiros que outras pessoas protegeram.

## <a name="if-you-are-not-a-local-administrator-and-use-office-2010"></a>Se não for um administrador local e utilizar o Office 2010
Se iniciar sessão no computador e não tiver direitos administrativos locais e a Configuração detetar que tem o Office 2010 instalado, verá uma mensagem de aviso a indicar que alguns cenários não funcionarão com esta configuração. Os cenários são:

-   Se a sua organização utiliza o serviço Azure Rights Management do Azure Information Protection em vez de uma versão no local do Rights Management:

    -   As funcionalidades da Gestão de Direitos de Informação (IRM) do Office não estarão disponíveis. Por exemplo, a opção **Não Reencaminhar** para e-mails e as permissões **Restringir Acesso** que pode definir no menu **Ficheiro** no Word e Excel. Pode utilizar a opção Partilhar Protegido no friso e as opções de clique com o botão direito do rato do Explorador de Ficheiros.

-   Se a sua organização utiliza uma versão no local do Rights Management em vez do serviço Azure Rights Management do Azure Information Protection:

    -   Não poderá ler um documento protegido que lhe tenha sido enviado por alguém de outra organização que esteja a utilizar o serviço Azure Rights Management.

Se não for um administrador local e utilizar o Office 365 ou Office 2013, não verá esta mensagem e estes cenários serão suportados.

Pode continuar a instalação com estas limitações conhecidas. Em alternativa, pode interromper a instalação e voltar a executá-la com a opção **Executar como administrador** quando executar Setup.exe no passo 3 ou pedir a um administrador que o instale por si. Os administradores podem [efetuar o script desta instalação](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application) para instalar automaticamente.

## <a name="examples-and-other-instructions"></a>Exemplos e outras instruções
Para obter exemplos de como pode utilizar a aplicação de partilha Rights Management e instruções sobre como proceder, veja as secções seguintes do guia do utilizador da aplicação de partilha Rights Management:

-   [Exemplos de utilização da aplicação de partilha RMS](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [O que pretende fazer?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Consulte Também
[Guia do utilizador da aplicação de partilha Rights Management](sharing-app-user-guide.md)

