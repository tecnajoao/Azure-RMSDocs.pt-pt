---
title: Tarefas realizadas com a aplicação de partilha RMS – AIP
description: Instruções para utilizadores que atualizaram da aplicação de partilha RMS para o cliente do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d7bc2478-c22f-4e19-9992-012658362b25
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 58b0ab62b260e407aa9ae6a36b4a063fe147889b
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="user-guide-tasks-that-you-used-to-do-with-the-rms-sharing-application"></a>Guia de utilizador: Tarefas que utilizou para fazer com a aplicação de partilha RMS

>*Aplica-se a: serviços de gestão de direitos do Active Directory [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
>Atualizou recentemente da aplicação de partilha Rights Management (também conhecida apenas como “aplicação de partilha RMS”) para o cliente do Azure Information Protection? 

Utilize as seguintes informações para colocar o serviço a funcionar rapidamente.

|A aplicação de partilha RMS|Para realizar esta ação com o cliente do Azure Information Protection
|-----------|--------------------|
|Proteger um ficheiro num dispositivo <br /><br />Também conhecido como “proteger no local”|Para aplicações do Office: selecione uma etiqueta que aplique a proteção exigida ou defina permissões personalizadas.<br /><br />Para outros ficheiros: utilize a opção de menu do Explorador de Ficheiros **Classificar e proteger** para abrir a caixa de diálogo **Classificar e proteger – Azure Information Protection**. Em seguida, selecione uma etiqueta que aplique a proteção exigida ou especifique as suas próprias permissões personalizadas. <br /><br />Para obter mais informações, veja [Classificar e proteger um ficheiro ou e-mail](client-classify-protect.md).
|Proteger um ficheiro que partilha por e-mail <br /><br />Também conhecido como “partilha protegida”|Utilizar o Outlook, aplicar uma etiqueta com a proteção necessária para a sua mensagem de e-mail ou selecione o Outlook **não reencaminhar** opção. Desprotegidos anexos que tenham um [suportada de tipo de ficheiro](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) são automaticamente protegidos.<br /><br />Nota: Para controlar um documento protegido que tem de e-mail, primeiro a protegê-lo e, em seguida, ligue-a mensagem de e-mail.<br /><br />Para obter mais informações, veja [Classificar e proteger um ficheiro ou e-mail](client-classify-protect.md).
|Alterar as permissões em ficheiros protegidos <br /><br />Também conhecido como “voltar a proteger”|Para aplicações do Office que apresentem a barra do Azure Information Protection: selecione uma etiqueta que aplica a proteção necessária.<br /><br />Para outros ficheiros e, se o cliente do Azure Information Protection estiver no [modo apenas de proteção](client-protection-only-mode.md): utilize a opção de menu do Explorador de Ficheiros **Classificar e proteger** para abrir a caixa de diálogo **Classificar e proteger – Azure Information Protection**. Em seguida, selecione uma etiqueta que aplique a proteção exigida ou especifique as suas próprias permissões personalizadas.<br /><br />Para obter mais informações, veja [Classificar e proteger um ficheiro ou e-mail](client-classify-protect.md).
|Controlar e revogar documentos|Para aplicações do Office: abra o documento e, em seguida, no separador **Base** > grupo **Proteção** > **Proteger** > **Controlar e revogar**<br /><br />No Explorador de Ficheiros: clique com o botão direito do rato num ficheiro ou pasta > **Classificar e proteger**. Em seguida, na caixa de diálogo **Classificar e proteger – Azure Information Protection**, clique em **Controlar e revogar**. <br /><br />Para obter mais informações, veja [Controlar e revogar os documentos](client-track-revoke.md).
|Ver e utilizar ficheiros que foram protegidos|Tem de ter o Office instalado para documentos do Office protegidos. O Visualizador de proteção de informações do Azure pode abrir muitos outros ficheiros protegidos, para que lê-los e também pode imprimir e guardar estes ficheiros, se tem permissões para efetuar estas ações. Este visualizador é instalado automaticamente com o cliente ou pode instalá-lo em separado.<br /><br />Para obter mais informações, veja artigo [Abrir ficheiros que foram protegidos](client-view-use-files.md).
|Remover a proteção de ficheiros|Utilize a opção de menu do Explorador de Ficheiros **Classificar e proteger** para abrir a caixa de diálogo **Classificar e proteger – Azure Information Protection**. <br /><br />Em seguida, para um único ficheiro, desmarque a opção **Proteger com permissões personalizadas**. Para vários ficheiros ou uma pasta, clique em **Remover permissões personalizadas**.<br /><br />Para obter mais informações, veja [Remover etiquetas e a proteção de ficheiros e e-mails](client-remove-label-protection.md).|

## <a name="cant-find-the-option-youre-looking-for"></a>Não consegue localizar a opção que procura?

Se estiver à procura de uma opção específica que está habituado a selecionar com a aplicação de partilha RMS, veja a tabela seguinte.

|Opção na aplicação de partilha RMS|Informações
|-----------|--------------------|
|**Partilhar Protegido**|Esta opção já não está disponível no friso do Office. Em vez de partilhar diretamente na sua aplicação do Office, utilize a opção de clique com o botão direito do rato do Explorador de Ficheiros **Classificar e proteger** para proteger uma cópia do documento com permissões personalizadas e, em seguida, partilhe o ficheiro através do cliente de e-mail à sua escolha ou da partilha de localização. <br /><br /> Também pode anexar um documento protegido a um e-mail que protege e o documento está protegido automaticamente com as restrições. No entanto, não é possível controlar e revogar neste documento.
|**Enviar-me um e-mail quando alguém tentar abrir estes documentos**|Utilize o site de controlo de documentos para configurar a definição de notificação por e-mail preferencial: localize o documento protegido que partilhou > **Definições** > **Notificações por e-mail**
|**Permitir a revogação instantânea do acesso a estes documentos**|Esta opção já não está disponível. Configure modelos que não permitem o acesso offline. Além disso, considere se precisa de reduzir o período de validade da licença de utilização para seu inquilino ao executar [Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime).







[!INCLUDE[Commenting house rules](../includes/houserules.md)]  
