---
title: "Configurar uma etiqueta do Azure Information Protection para proteção"
description: "Pode proteger os seus documentos e e-mails mais confidenciais ao configurar uma etiqueta para utilizar a proteção do Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: f5c4e2f7513832a884820ec0c57c7da2dec5f04e
ms.sourcegitcommit: 8b768e7e249e124f24acdf630d165eaf743f9c21
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/05/2017
---
<a id="how-to-configure-a-label-for-rights-management-protection" class="xliff"></a>

# Como configurar uma etiqueta para a proteção do Rights Management

>*Aplica-se a: Azure Information Protection*

Pode proteger os seus documentos e e-mails mais confidenciais utilizando um serviço de Gestão de Direitos, que utiliza políticas de encriptação, identidade e autorização para ajudar a evitar perda de dados. Esta proteção é aplicada quando configurar uma etiqueta para utilizar um modelo do Rights Management para documentos e e-mails ou a opção **Não reencaminhar** para mensagens de e-mail do Outlook. 

O modelo pode ser um dos modelos predefinidos que são criados automaticamente ao ativar o Azure Rights Management ou um modelo personalizado. Os modelos departamentais do Azure Rights Management são suportados mas apenas aplicam a proteção quando o autor do documento ou do e-mail estiver dentro do âmbito configurado do modelo. Se o utilizador não estiver dentro do âmbito, este vê uma mensagem informando que o Azure Rights Management não pode aplicar a etiqueta.

<a id="how-the-protection-works" class="xliff"></a>

## Como funciona a proteção

Quando um documento ou correio eletrónico está protegido pelo Azure Rights Management, este é encriptado em descanso e em trânsito e só pode ser desencriptado por utilizadores autorizados. Esta encriptação permanece com o documento ou com o e-mail, mesmo que o nome seja alterado. Além disso, pode configurar direitos e restrições de utilização, tal como nos exemplos seguintes:

- Apenas os utilizadores dentro da organização podem abrir o documento ou o e-mail confidencial da empresa.

- Apenas os utilizadores do departamento de marketing podem editar e imprimir o documento ou o e-mail de anúncio de promoção, enquanto todos os outros utilizadores na organização apenas podem ler este documento ou e-mail.

- Os utilizadores não podem reencaminhar um e-mail ou copiar informações do mesmo com notícias sobre uma reorganização interna.

- A lista de preços atual enviada para os parceiros de negócios não pode ser aberta após uma data especificada.

Para mais informações sobre os modelos do Azure Rights Management e como configurá-los no portal clássico do Azure, veja [Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md).

Para mais informações sobre o Azure Rights Management e para saber como funciona, veja [O que é o Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Para configurar uma etiqueta de modo a aplicar a proteção do Azure Rights Management, o serviço Azure Rights Management tem de ser ativado para a organização. Se ainda não o fez, veja [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

Os utilizadores podem aplicar etiquetas no Outlook para protegerem os seus e-mails mesmo que o Exchange não esteja configurado para a gestão de direitos de informação (IRM). No entanto, até que o Exchange seja configurado para IRM, não tem acesso a todas as funcionalidades associadas à utilização da proteção do Azure Rights Management com o Exchange. Por exemplo, os utilizadores não podem ver e-mails protegidos no telemóvel ou com o Outlook na Web, não é possível indexar os e-mails protegidos para pesquisa e não pode configurar o Exchange Online DLP para a proteção de gestão de direitos. Para configurar o Exchange para suportar estes cenários adicionais, veja os seguintes recursos:

- Para o Exchange Online, veja as instruções de [Exchange Online: configuração de IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Para o Exchange no local, tem de implementar o [conector RMS e configurar os servidores do Exchange](../deploy-use/deploy-rms-connector.md). 


<a id="to-configure-a-label-for-rights-management-protection" class="xliff"></a>

## Para configurar uma etiqueta para a proteção do Rights Management

1. Caso ainda não o tenha feito, abra uma nova janela de browser e inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global e, em seguida, navegue para o painel **Azure Information Protection**. 

    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a etiqueta que pretende configurar se aplicar a todos os utilizadores, selecione **Global** no painel **Azure Information Protection**. Contudo, se a etiqueta que pretende configurar estiver numa [política de âmbito](configure-policy-scope.md) para ser aplicada apenas a utilizadores selecionados, selecione antes essa política de âmbito.

3. No painel **Política**, selecione a etiqueta que pretende configurar, o que abre o painel **Etiqueta**. 

4. No painel **Etiqueta**, localize **Defina permissões para documentos e e-mails que contenham esta etiqueta** e selecione uma das seguintes opções.
    
    - **Não configurada**: selecione esta opção se a etiqueta estiver configurada para aplicar a proteção e já não quiser que a etiqueta selecionada aplique a proteção. Em seguida, avance para o passo 11.
    
    - **Proteger**: selecione esta opção para aplicar a proteção e, em seguida, avance para o passo 5.
    
    - **Remover Proteção**: selecione esta opção para remover a proteção se estiver configurada para um documento ou e-mail. Em seguida, avance para o passo 11.
        
        Tenha em atenção que os utilizadores têm de ter permissões para remover a proteção do Rights Management para aplicar uma etiqueta com esta opção. Esta opção requer que os utilizadores tenham o [direito de utilização](../deploy-use/configure-usage-rights.md) **Exportar** ou **Controlo Total**, que sejam os proprietários do Rights Management (que concede automaticamente o direito de utilização Controlo Total) ou que sejam [superutilizadores do Azure Rights Management](../deploy-use/configure-super-users.md). Os modelos predefinidos do Azure Rights Management não incluem os direitos de utilização que permitem que os utilizadores removam a proteção. 
        
        Se os utilizadores não tiverem permissões para remover a proteção do Rights Management e selecionarem uma etiqueta configurada com a opção **Remover Proteção**, verão a seguinte mensagem: **O Azure Information Protection não pode aplicar esta etiqueta. Se este problema persistir, contacte o seu administrador.**

5. Se selecionou **Proteger**, agora selecione **Proteção** para abrir o painel **Proteção**:
    
    ![Configurar a proteção para uma etiqueta do Azure Information Protection](../media/info-protect-protection-bar.png)

6. No painel **Proteção**, selecione **Azure RMS** ou **HYOK (AD RMS)**. 
    
    Na maioria dos casos, irá selecionar **Azure RMS** para as definições de permissão. Não selecione **HYOK (AD RMS)**, a menos que tenha lido e compreendido os pré-requisitos e as restrições que acompanham esta configuração de "*tenha a sua própria chave*" (HYOK). Para obter mais informações, veja [Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS](configure-adrms-restrictions.md). Para continuar a configuração para HYOK (AD RMS), avance para o passo 10.
    
7. Selecione uma das seguintes opções:
    
    - **Não encaminhar**: para definir esta opção do Outlook para e-mails.
    
    - **Selecione um modelo predefinido**: para utilizar um dos modelos predefinidos ou um modelo personalizado que configurou.
    
    - **Definir permissões (Pré-visualização)** para definir novas definições de proteção neste portal.

8. Se tiver selecionado **Selecionar um modelo predefinido** para **Azure RMS**, clique na caixa pendente e selecione o [modelo](../deploy-use/configure-custom-templates.md) que pretende utilizar para proteger os documentos e os e-mails com esta etiqueta.
    
    Se selecionar um **modelo departamental** ou se tiver configurado [controlos de inclusão](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
    - Os utilizadores que estão fora do âmbito configurado do modelo ou que estão excluídos de aplicarem a proteção do Azure Rights Management continuarão a ver a etiqueta mas não poderão aplicá-la. Se selecionarem a etiqueta, verão a seguinte mensagem: **O Azure Information Protection não pode aplicar esta etiqueta. Se este problema persistir, contacte o seu administrador.**
    
        Tenha em atenção que todos os modelos são sempre apresentados, mesmo que esteja a configurar uma política de âmbito. Por exemplo, está a configurar uma política de âmbito para o grupo de Marketing. Os modelos do Azure RMS que pode selecionar não serão restringidos aos modelos que estão no âmbito do grupo de Marketing e é possível selecionar um modelo departamental que os utilizadores selecionados não podem utilizar. Para facilitar a configuração e para minimizar a resolução de problemas, considere atribuir ao modelo departamental o mesmo nome da etiqueta na sua política de âmbito. 
            
9. Se selecionou **Definir permissões (Pré-visualização)** para **Azure RMS**, esta opção tem a maioria das opções de configuração para [modelos personalizados](configure-custom-templates.md) que pode configurar no portal clássico do Azure. Além disso, pode adicionar facilmente todos os utilizadores da sua organização e especificar endereços de e-mail externos para utilizadores individuais ou de grupo ou para todos os utilizadores noutra organização quando especificar um nome de domínio. 
    
    Para obter mais informações sobre a configuração desta pré-visualização, veja a publicação do blogue [Azure Information Protection unified administration now in Preview (Administração unificada do Azure Information Protection agora na Pré-visualização)](https://blogs.technet.microsoft.com/enterprisemobility/2017/04/26/azure-information-protection-unified-administration-now-in-preview/). 
    
    Para obter mais informações sobre as permissões que pode selecionar, veja [Configuração de direitos de utilização para o Azure Rights Management](configure-usage-rights.md).
    
    Incluído na opção **Definir permissões (Pré-visualização)**, verifique se quer fazer alterações às seguintes definições. Note que estas definições, assim como acontece com as permissões, não se aplicam ao [Emissor ou proprietário do Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner), ou qualquer [super utilizador](configure-super-users.md) que atribuiu.
    
    |Definição|Mais informações|Definição recomendada
    |-----------|--------------------|--------------------|
    |**expiração de conteúdos**|Defina uma data ou número de dias para este modelo que represente o tempo durante o qual não é possível abrir o modelo quando os documentos ou e-mails estão protegidos para os utilizadores selecionados. Pode especificar uma data ou um número de dias, começando pelo momento em que a proteção foi aplicada ao conteúdo.<br /><br />Quando especificar uma data, a mesma é efetiva a partir da meia-noite no seu fuso horário atual.|**O conteúdo nunca expira** exceto se o conteúdo tiver um requisito controlado por um tempo específico.|
    |**Permitir acesso offline**|Utilize esta definição para equilibrar quaisquer requisitos de segurança que tem (inclui acesso após revogação) com a capacidade de os utilizadores selecionados abrirem o conteúdo protegido quando não têm uma ligação à Internet.<br /><br />Se especificar que os conteúdos não estão disponíveis sem uma ligação à Internet ou que os conteúdos só estão disponíveis para um número especificado de dias, quando esse limiar for atingido, estes utilizadores têm de ser novamente autenticados e o respetivo acesso é registado. Quando isto acontecer, se as respetivas credenciais não estiverem colocadas em cache, é pedido aos utilizadores que iniciem sessão antes de poderem abrir o documento ou e-mail.<br /><br />Além da reautenticação, a política e a associação a grupos de utilizadores são reavaliadas. Isto significa que os utilizadores podem experienciar resultados de acesso diferentes para o mesmo documento ou e-mail, se existirem alterações na associação de política ou grupo resultantes da última vez a que acederam ao conteúdo. Tal pode retirar o acesso se o documento tiver sido [revogado](../rms-client/client-track-revoke.md).|Dependendo do nível de confidencialidade do conteúdo:<br /><br />- **Número de dias em que o conteúdo está disponível sem ligação à Internet** = **7** para dados empresariais confidenciais que podem causar danos ao negócio se forem partilhados com pessoas não autorizadas. Esta recomendação proporciona um bom equilíbrio entre flexibilidade e segurança. Os exemplos incluem contratos, relatórios de segurança, resumos de previsões e dados de conta de vendas.<br /><br />- **Nunca** para dados empresariais altamente confidenciais que iriam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Esta recomendação prioriza a segurança sobre a flexibilidade e garante que se o documento tiver sido revogado, todos os utilizadores autorizados imediatamente não podem abrir o documento. Os exemplos incluem informações dos funcionários e clientes, palavras-passe, código de origem e relatórios financeiros previamente anunciados.|
    
    Este agrupamento de definições cria um modelo personalizado para o serviço Azure Rights Management. Estes modelos podem ser utilizados com aplicações e serviços que se integram no Azure Rights Management. Para obter mais informações sobre como os computadores e os serviços transferem e atualizam estes modelos, veja [Atualizar modelos para utilizadores e serviços](refresh-templates.md).

10. Se tiver selecionado **Selecionar modelo** para **HYOK (AD RMS)**: forneça o GUID do modelo e o URL de licenciamento do cluster do AD RMS. [Mais informações](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

11. Clique em **OK** para fechar o painel **Proteção** e ver a sua opção **Não reencaminhar** ou a apresentação do modelo selecionado da opção **Proteção** no painel **Etiqueta**.

12. No painel **Etiqueta**, clique em **Guardar**.

13. Para disponibilizar as alterações aos utilizadores, no painel **Azure Information Protection**, clique em **Publicar**.

<a id="next-steps" class="xliff"></a>

## Próximos passos

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]