---
title: "Como configurar uma etiqueta para aplicar a proteção Rights Management | Azure Rights Management"
description: "Pode proteger os seus documentos e e-mails mais confidenciais utilizando um serviço de Gestão de Direitos, que utiliza políticas de encriptação, identidade e autorização para ajudar a evitar perda de dados. Esta proteção é aplicada ao configurar uma etiqueta para utilizar um modelo do Rights Management."
manager: mbaldwin
ms.date: 08/15/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: 23e62c82a38e696b0708f3b599d24f3a0f337fd8


---

# Como configurar uma etiqueta para aplicar a proteção Rights Management

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Pode proteger os seus documentos e e-mails mais confidenciais utilizando um serviço de Gestão de Direitos, que utiliza políticas de encriptação, identidade e autorização para ajudar a evitar perda de dados. Esta proteção é aplicada ao configurar uma etiqueta para utilizar um modelo do Rights Management. 

Este modelo pode ser um dos modelos predefinidos que são criados automaticamente ao ativar o Azure Rights Management ou pode ser um modelo personalizado. Os modelos departamentais do Azure Rights Management são suportados mas apenas aplicam a proteção quando o autor do documento ou do e-mail estiver dentro do âmbito configurado do modelo. Se o utilizador não estiver dentro do âmbito, este vê uma mensagem informando que o Azure Rights Management não pode aplicar a etiqueta.

## Como funciona a proteção

Quando um documento ou correio eletrónico está protegido pelo Azure Rights Management, este é encriptado em descanso e em trânsito e só pode ser desencriptado por utilizadores autorizados. Esta encriptação permanece com o documento ou com o e-mail, mesmo que o nome seja alterado. Além disso, pode configurar direitos e restrições de utilização, tal como nos exemplos seguintes:

- Apenas os utilizadores dentro da organização podem abrir o documento ou o e-mail confidencial da empresa.

- Apenas os utilizadores do departamento de marketing podem editar e imprimir o documento ou o e-mail de anúncio de promoção, enquanto todos os outros utilizadores na organização apenas podem ler o documento ou o e-mail.

- Os utilizadores não podem reencaminhar um e-mail com notícias sobre uma reorganização interna.

- A lista de preços atual enviada para os parceiros de negócios não pode ser aberta após uma data especificada.

Para obter mais informações sobre os modelos do Azure Rights Management e como configurar estes direitos e restrições de utilização, veja [Configurar modelos personalizados para o Azure Rights Management](../deploy-use/configure-custom-templates.md).

Para mais informações sobre o Azure Rights Management e para saber como funciona, consulte [O que é o Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Para configurar uma etiqueta de modo a aplicar a proteção do Azure Rights Management, o serviço Azure Rights Management tem de ser ativado para a organização. Se ainda não o fez, consulte [Ativar o Azure Rights Management](../deploy-use/activate-service.md).


## Para configurar uma etiqueta de modo a aplicar a proteção Rights Management

1. Se ainda não o fez, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global para que possa obter os modelos do Azure Rights Management. Em seguida, navegue para o painel **Azure Information Protection**. 

    Por exemplo, no menu do hub, clique em **Procurar** e comece a escrever **Information** na caixa Filtro. Selecione **Azure Information Protection**.

2. No painel do **Azure Information Protection**, selecione a etiqueta que pretende configurar para aplicar a proteção Rights Management.

3. No painel **Etiqueta**, na secção **Definir modelo RMS para proteger documentos e e-mails que contêm esta etiqueta**, para **Selecionar modelo RMS a partir de**, selecione **Azure RMS** ou **AD RMS (PRÉ-VISUALIZAÇÃO)**.
    
    Na maioria dos casos, irá selecionar **Azure RMS**. Não selecione AD RMS, a menos que tenha lido e compreendido os pré-requisitos e as restrições que acompanham esta configuração, por vezes referido como "*tenha a sua própria chave*" (HYOK). Para obter mais informações, veja [Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS](configure-adrms-restrictions.md).
    
4. Se tiver selecionado o Azure RMS: para **Selecionar modelo RMS**, clique na caixa pendente e selecione o modelo que pretende utilizar para proteger os documentos e os e-mails com esta etiqueta.

    > [!NOTE] 
    > Se criar um novo modelo depois de abrir o painel **Etiqueta**, feche este painel e volte ao passo 2, para que o modelo criado recentemente seja obtido a partir do Azure de modo a poder selecioná-lo.
    
    Tenha em atenção que, se selecionar um modelo departamental ou se tiver configurado [controlos de inclusão](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
    - Os utilizadores que estão fora do âmbito configurado do modelo ou que estão excluídos de aplicarem a proteção do Azure Rights Management continuarão a ver a etiqueta mas não poderão aplicá-la. Se selecionarem a etiqueta, verão a seguinte mensagem: **O Azure Information Protection não pode aplicar esta etiqueta. Se este problema persistir, contacte o seu administrador.**
    
5. Se tiver selecionado o AD RMS: forneça o GUID do modelo e o URL de licenciamento do cluster do AD RMS. [Mais informações](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

6. Clique em **Guardar**.

7. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organization-s-policy).  



<!--HONumber=Aug16_HO4-->


