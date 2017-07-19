---
title: "Tarefas realizadas com a aplicação de partilha RMS – AIP"
description: "Instruções para utilizadores que atualizaram da aplicação de partilha RMS para o cliente do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d7bc2478-c22f-4e19-9992-012658362b25
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: f3384e7cd049120b76a408cb761a0bb5ad34bf8b
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="tasks-that-you-used-to-do-with-the-rms-sharing-application"></a>Tarefas que costumava realizar com a aplicação de partilha RMS

Atualizou recentemente da aplicação de partilha Rights Management (também conhecida apenas como “aplicação de partilha RMS”) para o cliente do Azure Information Protection? 

Utilize as seguintes informações para colocar o serviço a funcionar rapidamente.

|A aplicação de partilha RMS|Para realizar esta ação com o cliente do Azure Information Protection
|-----------|--------------------|
|Proteger um ficheiro num dispositivo <br /><br />Também conhecido como “proteger no local”|Para aplicações do Office: selecione uma etiqueta que aplique a proteção exigida ou defina permissões personalizadas.<br /><br />Para outros ficheiros: utilize a opção de menu do Explorador de Ficheiros **Classificar e proteger** para abrir a caixa de diálogo **Classificar e proteger – Azure Information Protection**. Em seguida, selecione uma etiqueta que aplique a proteção exigida ou especifique as suas próprias permissões personalizadas. <br /><br />Para obter mais informações, veja [Classificar e proteger um ficheiro ou e-mail](client-classify-protect.md).
|Proteger um ficheiro que partilha por e-mail <br /><br />Também conhecido como “partilha protegida”|Se estiver a partilhar internamente: aplique uma etiqueta com a proteção exigida à sua mensagem de e-mail ou documento, ou selecione o opção do Outlook **Não Reencaminhar**. <br /><br /> Se estiver a partilhar externamente: ao utilizar uma cópia do ficheiro, utilize permissões personalizadas para proteger o ficheiro dentro da sua aplicação do Office ou através do Explorador de Ficheiros. Em seguida, partilhe o ficheiro através do mecanismo de partilha padrão, tal como um anexo de e-mail ou um convite para um documento do SharePoint Online. Considere incluir a ligação https://aka.ms/rms-signup como as instruções para a primeira utilização. <br /><br />Para obter mais informações sobre como partilhar externamente, veja a secção [Partilhar um ficheiro de forma segura com pessoas fora da sua organização](client-classify-protect.md#safely-share-a-file-with-people-outside-your-organization) no guia de utilizador.
|Alterar as permissões em ficheiros protegidos <br /><br />Também conhecido como “voltar a proteger”|Para aplicações do Office que apresentem a barra do Azure Information Protection: selecione uma etiqueta que aplica a proteção necessária.<br /><br />Para outros ficheiros e, se o cliente do Azure Information Protection estiver no [modo apenas de proteção](client-protection-only-mode.md): utilize a opção de menu do Explorador de Ficheiros **Classificar e proteger** para abrir a caixa de diálogo **Classificar e proteger – Azure Information Protection**. Em seguida, selecione uma etiqueta que aplique a proteção exigida ou especifique as suas próprias permissões personalizadas.<br /><br />Para obter mais informações, veja [Classificar e proteger um ficheiro ou e-mail](client-classify-protect.md).
|Controlar e revogar documentos|Para aplicações do Office: abra o documento e, em seguida, no separador **Base** > grupo **Proteção** > **Proteger** > **Controlar e revogar**<br /><br />No Explorador de Ficheiros: clique com o botão direito do rato num ficheiro ou pasta > **Classificar e proteger**. Em seguida, na caixa de diálogo **Classificar e proteger – Azure Information Protection**, clique em **Controlar e revogar**. <br /><br />Para obter mais informações, veja [Controlar e revogar os documentos](client-track-revoke.md).
|Ver e utilizar ficheiros que foram protegidos|O Visualizador do Azure Information Protection consegue abrir ficheiros protegidos para que os possa ler, imprimir e guardar, se tiver permissões para realizar estas ações. Este visualizador é instalado automaticamente com o cliente ou pode instalá-lo em separado.<br /><br />Para obter mais informações, veja artigo [Abrir ficheiros que foram protegidos](client-view-use-files.md).
|Remover a proteção de ficheiros|Utilize a opção de menu do Explorador de Ficheiros **Classificar e proteger** para abrir a caixa de diálogo **Classificar e proteger – Azure Information Protection**. <br /><br />Em seguida, para um único ficheiro, desmarque a opção **Proteger com permissões personalizadas**. Para vários ficheiros ou uma pasta, clique em **Remover permissões personalizadas**.<br /><br />Para obter mais informações, veja [Remover etiquetas e a proteção de ficheiros e e-mails](client-remove-label-protection.md).|

## <a name="cant-find-the-option-youre-looking-for"></a>Não consegue localizar a opção que procura?

Se estiver à procura de uma opção específica que está habituado a selecionar com a aplicação de partilha RMS, veja a tabela seguinte.

|Opção na aplicação de partilha RMS|Informações
|-----------|--------------------|
|**Partilhar Protegido**|Esta opção já não está disponível no friso do Office. Em vez de partilhar diretamente na sua aplicação do Office, utilize a opção de clique com o botão direito do rato do Explorador de Ficheiros **Classificar e proteger** para proteger uma cópia do documento com permissões personalizadas e, em seguida, partilhe o ficheiro através do cliente de e-mail à sua escolha ou da partilha de localização. Considere incluir a ligação https://aka.ms/rms-signup como as instruções para a primeira utilização. <br /><br />Para obter mais informações sobre como partilhar externamente, veja a secção [Partilhar um ficheiro de forma segura com pessoas fora da sua organização](#safely-share-a-file-with-people-outside-your-organization) no guia de utilizador.
|**Enviar-me um e-mail quando alguém tentar abrir estes documentos**|Utilize o site de controlo de documentos para configurar a definição de notificação por e-mail preferencial: localize o documento protegido que partilhou > **Definições** > **Notificações por e-mail**
|**Permitir a revogação instantânea do acesso a estes documentos**|Esta opção já não está disponível. Configure modelos que não permitem o acesso offline. Além disso, considere se precisa de reduzir o período de validade da licença de utilização para seu inquilino ao executar [Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime).







[!INCLUDE[Commenting house rules](../includes/houserules.md)]  
