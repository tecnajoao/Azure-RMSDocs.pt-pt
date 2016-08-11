---
title: "Como configurar uma etiqueta para aplicar a proteção Rights Management | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: 00b4cd2b1e7b1196cedd39d7052db534e781bb13
ms.openlocfilehash: 7a20b59c404959c4ec209e8c29ac61ab71233e87


---

# Como configurar uma etiqueta para aplicar a proteção Rights Management

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Pode proteger os seus documentos e e-mails mais confidenciais utilizando o Azure Rights Management, que utiliza políticas de encriptação, identidade e autorização para ajudar a evitar perda de dados. Esta proteção é aplicada ao configurar uma etiqueta para utilizar um modelo do Rights Management. 

Este modelo pode ser um dos modelos predefinidos que são criados automaticamente ao ativar o Azure Rights Management ou pode ser um modelo personalizado. Os modelos departamentais são suportados mas apenas aplicam a proteção quando o autor do documento ou do e-mail estiver dentro do âmbito configurado do modelo. Se o utilizador não estiver dentro do âmbito, este vê uma mensagem informando que o Azure Rights Management não pode aplicar a etiqueta.

## Como funciona a proteção

Quando um documento ou correio eletrónico está protegido pelo Azure Rights Management, este é encriptado em descanso e em trânsito e só pode ser desencriptado por utilizadores autorizados. Esta encriptação permanece com o documento ou com o e-mail, mesmo que o nome seja alterado. Além disso, pode configurar direitos e restrições de utilização, tal como nos exemplos seguintes:

- Apenas os utilizadores dentro da organização podem abrir o documento ou o e-mail.

- Apenas os utilizadores do departamento de marketing podem editar e imprimir o documento ou o e-mail, enquanto todos os outros utilizadores na organização apenas podem ver o documento ou o e-mail.

- Os utilizadores não podem reencaminhar e-mails.

- Depois de uma data especificada, não é possível abrir documentos ou e-mails que sejam enviados para parceiros de negócios.

Para obter mais informações sobre os modelos e sobre como configurar estes direitos e restrições de utilização, consulte [Configurar modelos personalizados para o Azure Rights Management](../deploy-use/configure-custom-templates.md).

Para mais informações sobre o Azure Rights Management e para saber como funciona, consulte [O que é o Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Para configurar uma etiqueta de modo a aplicar a proteção Rights Management, o serviço Azure Rights Management tem de ser ativado para a organização. Se ainda não o fez, consulte [Ativar o Azure Rights Management](../deploy-use/activate-service.md).


## Para configurar uma etiqueta de modo a aplicar a proteção Rights Management

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
 
2. No menu Hub, clique em **Procurar** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

3. No painel do **Azure Information Protection**, selecione a etiqueta que pretende configurar para aplicar a proteção Rights Management.

4. No painel **Etiqueta**, na secção **Definir modelo RMS para proteger documentos e e-mails que contêm esta etiqueta**, configure as seguintes opções:

    - Se vir **Selecionar modelo RMS a partir de**: Selecione **Azure RMS**. 
    
        Não selecione **AD RMS** e as opções de configuração associadas sem assistência da Microsoft. Se estiver interessado em testar o Azure Information Protection com Serviços de Gestão de Direitos do Active Directory , envie um e-mail para askipteam@microsoft.com. 
    
    - Para **Selecionar o modelo RMS**: clique na caixa pendente e selecione o modelo que pretende utilizar para proteger os documentos e os e-mails com esta etiqueta.

        > [!NOTE] Se criar um novo modelo depois de abrir o painel **Etiqueta**, feche este painel e volte ao passo 3, para que o modelo criado recentemente seja obtido a partir do Azure de modo a poder selecioná-lo.

5. Clique em **Guardar**.

6. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy).  



<!--HONumber=Jul16_HO5-->


