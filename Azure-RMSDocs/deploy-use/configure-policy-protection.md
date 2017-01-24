---
title: "Como configurar uma etiqueta para aplicar a proteção de Gestão de Direitos| Azure Information Protection"
description: "Pode proteger os seus documentos e e-mails mais confidenciais utilizando um serviço de Gestão de Direitos, que utiliza políticas de encriptação, identidade e autorização para ajudar a evitar perda de dados. Esta proteção é aplicada ao configurar uma etiqueta para utilizar um modelo da Gestão de Direitos."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 659f8d79a0ed0146fb94040ab7328e7b9530460a


---

# <a name="how-to-configure-a-label-to-apply-rights-management-protection"></a>Como configurar uma etiqueta para aplicar a proteção de Gestão de Direitos

>*Aplica-se a: Azure Information Protection*

Pode proteger os seus documentos e e-mails mais confidenciais utilizando um serviço de Gestão de Direitos, que utiliza políticas de encriptação, identidade e autorização para ajudar a evitar perda de dados. Esta proteção é aplicada ao configurar uma etiqueta para utilizar um modelo de Gestão de Direitos. 

Este modelo pode ser um dos modelos predefinidos que são criados automaticamente ao ativar o Azure Rights Management ou pode ser um modelo personalizado. Os modelos departamentais do Azure Rights Management são suportados mas apenas aplicam a proteção quando o autor do documento ou do e-mail estiver dentro do âmbito configurado do modelo. Se o utilizador não estiver dentro do âmbito, este vê uma mensagem informando que o Azure Rights Management não pode aplicar a etiqueta.

## <a name="how-the-protection-works"></a>Como funciona a proteção

Quando um documento ou correio eletrónico está protegido pelo Azure Rights Management, este é encriptado em descanso e em trânsito e só pode ser desencriptado por utilizadores autorizados. Esta encriptação permanece com o documento ou com o e-mail, mesmo que o nome seja alterado. Além disso, pode configurar direitos e restrições de utilização, tal como nos exemplos seguintes:

- Apenas os utilizadores dentro da organização podem abrir o documento ou o e-mail confidencial da empresa.

- Apenas os utilizadores do departamento de marketing podem editar e imprimir o documento ou o e-mail de anúncio de promoção, enquanto todos os outros utilizadores na organização apenas podem ler o documento ou o e-mail.

- Os utilizadores não podem reencaminhar um e-mail com notícias sobre uma reorganização interna.

- A lista de preços atual enviada para os parceiros de negócios não pode ser aberta após uma data especificada.

Para mais informações sobre os modelos do Azure Rights Management e como configurar estes direitos e restrições de utilização, consulte [Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md).

Para mais informações sobre o Azure Rights Management e para saber como funciona, consulte [O que é o Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Para configurar uma etiqueta de modo a aplicar a proteção do Azure Rights Management, o serviço Azure Rights Management tem de ser ativado para a organização. Se ainda não o fez, consulte [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

Os utilizadores podem aplicar etiquetas no Outlook para protegerem os seus e-mails mesmo que o Exchange não esteja configurado para a gestão de direitos de informação (IRM). No entanto, até que o Exchange seja configurado para IRM, não tem acesso a todas as funcionalidades associadas à utilização da proteção do Azure Rights Management com o Exchange. Por exemplo, os utilizadores não podem ver e-mails protegidos no telemóvel ou com o Outlook Web Access, não é possível indexar os e-mails protegidos para pesquisa e não pode configurar o Exchange Online DLP para a proteção de gestão de direitos. Para configurar o Exchange para suportar estes cenários adicionais, veja os seguintes recursos:

- Para o Exchange Online, veja as instruções de [Exchange Online: configuração de IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Para o Exchange no local, tem de implementar o [conector RMS e configurar os servidores do Exchange](../deploy-use/deploy-rms-connector.md). 


## <a name="to-configure-a-label-to-apply-rights-management-protection"></a>Para configurar uma etiqueta de modo a aplicar a proteção de Gestão de Direitos

1. Caso ainda não o tenha feito, abra uma nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador global e navegue para o painel **Azure Information Protection**. 

    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a etiqueta que pretende configurar se aplicar a todos os utilizadores, selecione a etiqueta a alterar no painel **Política:Global**. 

     Se a etiqueta que pretende configurar estiver numa [política de âmbito](configure-policy-scope.md) para ser aplicada apenas a utilizadores selecionados, selecione primeiro essa política de âmbito no painel inicial do **Azure Information Protection**.

3. No painel **Etiqueta**, na secção **Defina o modelo do RMS para a proteção de documentos e e-mails que contenham esta etiqueta**, para **Selecionar modelo do RMS a partir de**, selecione **Azure RMS** ou **AD RMS**.
    
    Na maioria dos casos, irá selecionar **Azure RMS**. Não selecione AD RMS, a menos que tenha lido e compreendido os pré-requisitos e as restrições que acompanham esta configuração, por vezes referido como "*tenha a sua própria chave*" (HYOK). Para obter mais informações, veja [Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS](configure-adrms-restrictions.md).
    
4. Se tiver selecionado o Azure RMS: em **Selecionar modelo RMS**, clique na caixa pendente e selecione o [modelo](../deploy-use/configure-custom-templates.md) ou a opção de gestão de direitos que pretende utilizar para proteger os documentos e os e-mails com esta etiqueta.
    
    Mais informações sobre as opções:
    
    - Criou um novo modelo após abrir o painel **Etiqueta**? Feche este painel e regresse ao passo 2. Desta forma, o modelo que criou recentemente será obtido a partir do Azure para que o possa selecionar.
    
    - Se selecionar um **modelo departamental** ou se tiver configurado [controlos de inclusão](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
        - Os utilizadores que estão fora do âmbito configurado do modelo ou que estão excluídos de aplicarem a proteção do Azure Rights Management continuarão a ver a etiqueta mas não poderão aplicá-la. Se selecionarem a etiqueta, verão a seguinte mensagem: **O Azure Information Protection não pode aplicar esta etiqueta. Se este problema persistir, contacte o seu administrador.**
        
            Tenha em atenção que todos os modelos são sempre apresentados, mesmo que esteja a configurar uma política de âmbito. Por exemplo, está a configurar uma política de âmbito para o grupo de Marketing. Os modelos do Azure RMS que pode selecionar não serão restringidos aos modelos que estão no âmbito do grupo de Marketing e é possível selecionar um modelo departamental que os utilizadores selecionados não podem utilizar. Para facilitar a configuração e para minimizar a resolução de problemas, considere atribuir ao modelo departamental o mesmo nome da etiqueta na sua política de âmbito. 
            
    - Se selecionar **Remover Proteção**:
        
        - Os utilizadores têm de ter permissões para remover a proteção de Gestão d eDireitos para aplicar uma etiqueta que tenha esta opção. Esta opção requer que os utilizadores tenham o [direito de utilização](../deploy-use/configure-usage-rights.md) **Exportar** (para documentos do Office) ou **Controlo Total**, que sejam os proprietários da Gestão de Direitos (concede automaticamente o direito de utilização Controlo Total) ou que sejam [superutilizadores do Azure Rights Management](../deploy-use/configure-super-users.md). Os modelos de gestão de direitos predefinidos não incluem os direitos de utilização que permitem que os utilizadores removam a proteção. 

            Se os utilizadores não tiverem permissões para remover a proteção de Righta Management e selecionarem esta etiqueta com a opção **Remover Proteção**, verão a seguinte mensagem: **O Azure Information Protection não pode aplicar esta etiqueta. Se este problema persistir, contacte o seu administrador.**

5. Se tiver selecionado o AD RMS: forneça o GUID do modelo e o URL de licenciamento do cluster do AD RMS. [Mais informações](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

6. Clique em **Guardar**.

7. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

## <a name="next-steps"></a>Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


