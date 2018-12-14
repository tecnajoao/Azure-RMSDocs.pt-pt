---
title: Tarefas realizadas com a aplicação de partilha RMS – AIP
description: Instruções para utilizadores que atualizaram da aplicação de partilha RMS para o cliente do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: d7bc2478-c22f-4e19-9992-012658362b25
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: c882c917a3a612b3fa362661cdcd94e77ec145f1
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305527"
---
# <a name="user-guide-tasks-that-you-used-to-do-with-the-rms-sharing-application"></a>Guia de utilizador: Tarefas que costumava realizar com a aplicação de partilha RMS

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Atualizou recentemente da aplicação de partilha Rights Management (também conhecida apenas como “aplicação de partilha RMS”) para o cliente do Azure Information Protection? 

Utilize as seguintes informações para colocar o serviço a funcionar rapidamente.

|A aplicação de partilha RMS|Para realizar esta ação com o cliente do Azure Information Protection
|-----------|--------------------|
|Proteger um ficheiro num dispositivo <br /><br />Também conhecido como “proteger no local”|Para aplicações do Office: Selecione uma etiqueta que aplique a proteção exigida ou definir permissões personalizadas.<br /><br />Para outros ficheiros: Utilize a opção de menu do Explorador de Ficheiros **Classificar e proteger** para abrir a caixa de diálogo **Classificar e proteger – Azure Information Protection**. Em seguida, selecione uma etiqueta que aplique a proteção exigida ou especifique as suas próprias permissões personalizadas. <br /><br />Para obter mais informações, veja [Classificar e proteger um ficheiro ou e-mail](client-classify-protect.md).
|Proteger um ficheiro que partilha por e-mail <br /><br />Também conhecido como “partilha protegida”|Usando o Outlook, aplique uma etiqueta com a proteção exigida à sua mensagem de e-mail ou selecione o Outlook **não reencaminhar** opção. Desprotegidos anexos que tem um [tipo de ficheiro suportado](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) são automaticamente protegidos.<br /><br />Nota: Para controlar um documento protegido que enviar por e-mail, protegê-lo primeiro e, em seguida, anexá-lo para a mensagem de e-mail.<br /><br />Para obter mais informações, veja [Classificar e proteger um ficheiro ou e-mail](client-classify-protect.md).
|Alterar as permissões em ficheiros protegidos <br /><br />Também conhecido como “voltar a proteger”|Para aplicações do Office que apresentem a barra do Azure Information Protection: Selecione uma etiqueta que aplique a proteção exigida.<br /><br />Para outros ficheiros, e se o cliente do Azure Information Protection se encontra num [modo apenas de proteção](client-protection-only-mode.md): Utilize a opção de menu do Explorador de Ficheiros Classificar e proteger para abrir a caixa de diálogo **Classificar e proteger – Azure Information Protection**. Em seguida, selecione uma etiqueta que aplique a proteção exigida ou especifique as suas próprias permissões personalizadas.<br /><br />Para obter mais informações, veja [Classificar e proteger um ficheiro ou e-mail](client-classify-protect.md).
|Controlar e revogar documentos|Do Word, Excel e PowerPoint: Abra o documento e, em seguida, no **home page** separador > **proteção** grupo > **proteger** > **controlar e revogar**<br /><br />No Explorador de ficheiros: Clique com o botão direito do rato num arquivo ou pasta > **classificar e proteger**. Em seguida, na caixa de diálogo **Classificar e proteger – Azure Information Protection**, clique em **Controlar e revogar**. <br /><br />Para obter mais informações, veja [Controlar e revogar os documentos](client-track-revoke.md).
|Ver e utilizar ficheiros que foram protegidos|Tem de ter o Office instalado para documentos do Office protegidos. O Visualizador do Azure Information Protection pode abrir a muitos outros ficheiros protegidos, para que lê-los e também pode imprimir e guardar, se tiver permissões para realizar estas ações. Este visualizador é instalado automaticamente com o cliente ou pode instalá-lo em separado.<br /><br />Para obter mais informações, veja artigo [Abrir ficheiros que foram protegidos](client-view-use-files.md).
|Remover a proteção de ficheiros|Utilize a opção de menu do Explorador de Ficheiros **Classificar e proteger** para abrir a caixa de diálogo **Classificar e proteger – Azure Information Protection**. <br /><br />Em seguida, para um único ficheiro, desmarque a opção **Proteger com permissões personalizadas**. Para vários ficheiros ou uma pasta, clique em **Remover permissões personalizadas**.<br /><br />Para obter mais informações, veja [Remover etiquetas e a proteção de ficheiros e e-mails](client-remove-label-protection.md).|

## <a name="cant-find-the-option-youre-looking-for"></a>Não consegue localizar a opção que procura?

Se estiver à procura de uma opção específica que está habituado a selecionar com a aplicação de partilha RMS, veja a tabela seguinte.

|Opção na aplicação de partilha RMS|Informações
|-----------|--------------------|
|**Partilhar Protegido**|Esta opção já não está disponível no friso do Office. Em vez de partilhar diretamente na sua aplicação do Office, utilize a opção de clique com o botão direito do rato do Explorador de Ficheiros **Classificar e proteger** para proteger uma cópia do documento com permissões personalizadas e, em seguida, partilhe o ficheiro através do cliente de e-mail à sua escolha ou da partilha de localização. <br /><br /> Também pode anexar um documento do Office não protegido a uma mensagem de e-mail que protege, e o documento está protegido automaticamente com as mesmas restrições. No entanto, não é possível controlar e revogar este documento.
|**Enviar-me um e-mail quando alguém tentar abrir estes documentos**|Utilize o site de controlo de documentos para configurar a definição de notificação de e-mail preferencial: Localize o documento protegido que partilhou > **configurações** > **notificações por E-Mail**
|**Permitir a revogação instantânea do acesso a estes documentos**|Esta opção já não está disponível. Utilize as definições de proteção definidos pelo administrador que não permitem o acesso offline. Além disso, um administrador pode reduzir o período de validade de licença de utilização para o seu inquilino, executando [Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime).
|**Controlar a utilização** no Outlook|A capacidade de acessar o site de controlo do Outlook de documentos já não está disponível. Em alternativa, utilize o **controlar e revogar** opção do Word, PowerPoint, Excel ou Explorador de ficheiros. Ou, usando um navegador, pode ir diretamente para o [site de controlo de documentos](https://go.microsoft.com/fwlink/?LinkId=529562).

## <a name="next-steps"></a>Passos Seguintes
Pode obter mais instruções sobre os procedimentos no guia do utilizador do Azure Information Protection:

- [O que pretende fazer?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Informações adicionais para administradores    
Consulte a [Guia do administrador do Azure Information Protection](client-admin-guide.md).

  
