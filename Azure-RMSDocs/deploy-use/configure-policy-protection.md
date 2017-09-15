---
title: "Configurar uma etiqueta do Azure Information Protection para proteção"
description: "Pode proteger os seus documentos e e-mails mais confidenciais ao configurar uma etiqueta para utilizar a proteção do Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/12/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: fce3c905f2f48c2723ee7f0b55ff5ddb77f6258a
ms.sourcegitcommit: 94a9b6714c555b95f6064088e77ed94f08224a15
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2017
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Como configurar uma etiqueta para a proteção do Rights Management

>*Aplica-se a: Azure Information Protection*

Pode proteger os seus documentos e e-mails mais confidenciais utilizando um serviço de gestão de direitos. Este serviço utiliza políticas de encriptação, identidade e autorização para ajudar a evitar perda de dados. A proteção é aplicada ao configurar uma etiqueta para utilizar a proteção Rights Management para documentos e e-mails, ou o **não reencaminhar** opção para mensagens de e-mail do Outlook. 

## <a name="how-the-protection-works"></a>Como funciona a proteção

Quando um documento ou correio eletrónico está protegido pelo Azure Rights Management, este é encriptado em descanso e em trânsito e só pode ser desencriptado por utilizadores autorizados. Esta encriptação permanece com o documento ou com o e-mail, mesmo que o nome seja alterado. Além disso, pode configurar direitos e restrições de utilização, tal como nos exemplos seguintes:

- Apenas os utilizadores dentro da organização podem abrir o documento ou o e-mail confidencial da empresa.

- Apenas os utilizadores do departamento de marketing podem editar e imprimir o documento ou o e-mail de anúncio de promoção, enquanto todos os outros utilizadores na organização apenas podem ler este documento ou e-mail.

- Os utilizadores não podem reencaminhar um e-mail ou copiar informações do mesmo com notícias sobre uma reorganização interna.

- A lista de preços atual enviada para os parceiros de negócios não pode ser aberta após uma data especificada.

Para obter mais informações sobre a proteção do Azure Rights Management e como funciona, consulte [que é o Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Para configurar uma etiqueta para aplicar esta proteção, o serviço Azure Rights Management tem de ser ativado para a sua organização. Se ainda não o fez, veja [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

Quando a etiqueta aplica-se a proteção, um documento protegido não é adequado ser guardada no SharePoint ou OneDrive. Estas localizações não suportam o seguinte para os ficheiros protegidos: criação conjunta, Office Online, pesquisa, pré-visualização do documento, miniatura, deteção de dados Eletrónicos e prevenção de perda de dados (DLP). 

Os utilizadores podem aplicar etiquetas no Outlook para protegerem os seus e-mails mesmo que o Exchange não esteja configurado para a gestão de direitos de informação (IRM). No entanto, até que o Exchange seja configurado para IRM, não tem acesso a todas as funcionalidades associadas à utilização da proteção do Azure Rights Management com o Exchange. Por exemplo, os utilizadores não podem ver e-mails protegidos no telemóvel ou com o Outlook na Web, não é possível indexar os e-mails protegidos para pesquisa e não pode configurar o Exchange Online DLP para a proteção de gestão de direitos. Para configurar o Exchange para suportar estes cenários adicionais, veja os seguintes recursos:

- Para o Exchange Online, veja as instruções de [Exchange Online: configuração de IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Para o Exchange no local, tem de implementar o [conector RMS e configurar os servidores do Exchange](../deploy-use/deploy-rms-connector.md). 

## <a name="to-configure-a-label-for-rights-management-protection"></a>Para configurar uma etiqueta para a proteção do Rights Management

1. Se ainda não o tiver feito, abra uma nova janela do browser e inicie sessão para o [portal do Azure](https://portal.azure.com) como um administrador de segurança ou um administrador global. Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no menu do hub, clique em **Mais serviços** e comece a escrever **Information** na caixa Filtrar. Selecione **Azure Information Protection**.

2. Se a etiqueta que pretende configurar será aplicada a todos os utilizadores, permaneça o **Azure Information Protection - política Global** painel. No entanto, se a etiqueta que pretende configurar está a ser um [âmbito política](configure-policy-scope.md) para que o se aplica apenas a utilizadores selecionados do **políticas** selecção de menu, selecione **âmbito políticas**. Em seguida, selecione a política de âmbito do **políticas do Azure Information Protection - âmbito** painel.

3. Selecione a etiqueta que pretende configurar, que abre o **etiqueta** painel. 

4. No **etiqueta** painel, localize **definir as permissões para documentos e e-mails que contêm esta etiqueta** e selecione uma das seguintes opções:
    
    - **Não configurada**: selecione esta opção se a etiqueta estiver configurada para aplicar a proteção e já não quiser que a etiqueta selecionada aplique a proteção. Em seguida, avance para o passo 11.
    
    - **Proteger**: selecione esta opção para aplicar a proteção e, em seguida, avance para o passo 5.
    
    - **Remova a proteção**: selecione esta opção para remover a proteção se um documento ou correio eletrónico está protegido. Em seguida, avance para o passo 11.
        
        Tenha em atenção que para os utilizadores aplicarem uma etiqueta que tem esta opção, têm de ter permissões para remover a proteção Rights Management. Este requisito, significa que os utilizadores têm de ter o **exportar** ou **controlo total** [direito de utilização](../deploy-use/configure-usage-rights.md). Ou, tem de ser o proprietário de Rights Management (que automaticamente concede o direito de utilização do controlo total) ou ser um [Superutilizador do Azure Rights Management](../deploy-use/configure-super-users.md). Os modelos do Azure Rights Management predefinido não incluem os direitos de utilização que permitem que os utilizadores a remover a proteção. 
        
        Se utilizadores não têm permissões para remover a proteção Rights Management e estes selecionam uma etiqueta que está configurada com esta **remover proteção** opção, verá a seguinte mensagem: **Azure Information Protection Não é possível aplicar esta etiqueta. Se este problema persistir, contacte o seu administrador.**

5. Se selecionou **Proteger**, agora selecione **Proteção** para abrir o painel **Proteção**:
    
    ![Configurar a proteção para uma etiqueta do Azure Information Protection](../media/info-protect-protection-bar-configured.png)

6. No **proteção** painel, selecione **Azure RMS** ou **Azure (chave de nuvem)**, ou selecione **HYOK (AD RMS)**. A primeira opção está no processo de ser mudado.
    
    Na maioria dos casos, selecione **Azure RMS** ou **Azure (chave de nuvem)** para as suas definições de permissão. Não selecione **HYOK (AD RMS)**, a menos que tenha lido e compreendido os pré-requisitos e as restrições que acompanham esta configuração de "*tenha a sua própria chave*" (HYOK). Para obter mais informações, veja [Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS](configure-adrms-restrictions.md). Para continuar a configuração para HYOK (AD RMS), avance para o passo 10.
    
7. Selecione uma das seguintes opções:
    
    - **Selecione um modelo predefinido**: para utilizar um dos modelos predefinidos ou um modelo personalizado que configurou. Este modelo tem de ser publicado (não arquivado) e não deve ser ligado já a outra etiqueta. Quando seleciona esta opção, pode utilizar o **Editar modelo** botão para [converter o modelo para uma etiqueta](configure-policy-templates.md#to-convert-templates-to-labels).
    
    - **Definir permissões**: definir as definições de proteção novo neste portal.
    
    - **Definido de utilizador do conjunto de permissões (pré-visualização)**: para permitir que os utilizadores que especifique que devem ser concedidas permissões e quais são essas permissões. Em seguida, pode refinar esta opção e escolha apenas Outlook (predefinição), ou Word, Excel, PowerPoint e Explorador de ficheiros. 
        
        Se escolher a opção para o Outlook: A etiqueta é apresentada no Outlook e o comportamento resultante quando os utilizadores aplicam a etiqueta é o mesmo que a opção não reencaminhar.
        
        Se escolher a opção para Word, Excel, PowerPoint e Explorador de ficheiros: esta opção requer a versão de pré-visualização do cliente Azure Information Protection. Quando esta opção é definida e os utilizadores têm o cliente de pré-visualização, a etiqueta é apresentada nestas aplicações. O comportamento resultante quando os utilizadores aplicam a etiqueta é para apresentar a caixa de diálogo aos utilizadores selecionar permissões personalizadas. Na caixa de diálogo, os utilizadores tem de especificar as permissões, os utilizadores ou grupos e quaisquer data de expiração. Certifique-se de que os utilizadores têm instruções e orientações sobre como fornecer estes valores.

8. Se tiver selecionado **selecionar um modelo predefinido** para **Azure RMS** ou **Azure (chave de nuvem)**, clique na caixa pendente e selecione o [modelo](../deploy-use/configure-policy-templates.md)que pretende utilizar para proteger documentos e e-mails com esta etiqueta. Não veem modelos arquivados ou modelos que já estão selecionados para outra etiqueta.
    
    Se selecionar um **modelo departamental**, ou se tiver configurado [controlos de inclusão](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
    - Os utilizadores que estão fora do âmbito configurado do modelo ou que estão excluídos de aplicarem a proteção do Azure Rights Management continuarão a ver a etiqueta mas não poderão aplicá-la. Se selecionarem a etiqueta, verão a seguinte mensagem: **O Azure Information Protection não pode aplicar esta etiqueta. Se este problema persistir, contacte o seu administrador.**
        
        Tenha em atenção que todos os modelos publicados são sempre apresentados, mesmo se estiver a configurar uma política de âmbito. Por exemplo, está a configurar uma política de âmbito para o grupo de Marketing. Os modelos que pode selecionar não estão limitados a modelos que estão no âmbito do grupo de Marketing e é possível selecionar um modelo departamental que não é possível utilizar os seus utilizadores selecionados. Para facilitar a configuração e para minimizar a resolução de problemas, considere atribuir ao modelo departamental o mesmo nome da etiqueta na sua política de âmbito. 
            
9. Se tiver selecionado **definir permissões** para **Azure RMS** ou **Azure (chave de nuvem)**, esta opção permite-lhe configurar as mesmas definições que pode configurar num modelo. 
    
    Selecione **adicionar permissões**e o **adicionar permissões** painel, selecione o primeiro conjunto de utilizadores e grupos que irão ter direitos para utilizar o conteúdo que será protegido pela etiqueta selecionada:
    
    - Escolha **selecione na lista** para adicionar todos os utilizadores da sua organização ou procurar o diretório.
        
        Os utilizadores ou grupos tem de ter um endereço de e-mail. Num ambiente de produção, este é quase sempre ser a caso, mas num ambiente de teste simple, poderá ter de adicionar endereços de e-mail a contas de utilizador ou grupos.
        
    - Escolha **Introduza detalhes** especificar manualmente o e-mail endereços para utilizadores individuais ou grupos (internos ou externos). Em alternativa, especificar todos os utilizadores noutra organização por introduzir um nome de domínio da organização. 
        
    >[!NOTE]
    >Se um endereço de e-mail for alterada depois de selecionar o utilizador ou grupo, consulte o [considerações se a alteração de endereços de e-mail](../plan-design/prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) secção na documentação do planeamento.
    
    Como melhor prática, utilize grupos em vez de utilizadores. Este stratetegy mantém a configuração mais simples e torna menos provável que tem de atualizar a configuração de etiqueta mais tarde e, em seguida, voltar a proteger conteúdo. No entanto, se fizer alterações ao grupo, tenha em atenção que, por motivos de desempenho, o Azure Rights Management [coloca a associação do grupo em cache](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management ). 
    
    Quando especificar o primeiro conjunto de utilizadores e grupos, selecione as permissões a conceder estes utilizadores e grupos. Para obter mais informações sobre as permissões que pode selecionar, veja [Configuração de direitos de utilização para o Azure Rights Management](configure-usage-rights.md). No entanto, as aplicações que suportam esta proteção podem variar na forma como implementam estas permissões. Veja a respetiva documentação e faça os seus próprios testes com as aplicações que os utilizadores usam para verificar o comportamento antes de implementar o modelo para os utilizadores.
    
    Se necessário, agora pode adicionar um segundo conjunto de utilizadores e grupos com direitos de utilização. Repita até que especificou todos os utilizadores e grupos com as suas respetivas permissões.

    >[!TIP]
    >Considere adicionar o **copiar e extrair conteúdo** permissão personalizada e conceder o mesmo aos administradores de recuperação de dados ou pessoal nas outras funções que tenham responsabilidades de recuperação de informações. Se for necessário, estes utilizadores, em seguida, podem remover a proteção de ficheiros e e-mails que irão ser protegidos utilizando esta etiqueta ou modelo. Esta capacidade para remover a proteção ao nível da permissão para um documento ou e-mail fornece controlo mais detalhado do que o [funcionalidade de Superutilizador](configure-super-users.md).
    
    Para todos os utilizadores e grupos que especificou, no **proteção** painel, agora, verifique se pretende efetuar alterações às seguintes definições. Note que estas definições, assim como acontece com as permissões, não se aplicam ao [Emissor ou proprietário do Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner), ou qualquer [super utilizador](configure-super-users.md) que atribuiu.
    
    |Definição|Mais informações|Definição recomendada
    |-----------|--------------------|--------------------|
    |**expiração de conteúdos**|Defina uma data ou número de dias para este modelo que represente o tempo durante o qual não é possível abrir o modelo quando os documentos ou e-mails estão protegidos para os utilizadores selecionados. Pode especificar uma data ou um número de dias, começando pelo momento em que a proteção foi aplicada ao conteúdo.<br /><br />Quando especificar uma data, a mesma é efetiva a partir da meia-noite no seu fuso horário atual.|**O conteúdo nunca expira** exceto se o conteúdo tiver um requisito controlado por um tempo específico.|
    |**Permitir acesso offline**|Utilize esta definição para equilibrar quaisquer requisitos de segurança que tem (inclui acesso após revogação) com a capacidade de os utilizadores selecionados abrirem o conteúdo protegido quando não têm uma ligação à Internet.<br /><br />Se especificar que o conteúdo não está disponível sem uma ligação à Internet ou esse conteúdo está disponível apenas para um número especificado de dias, quando esse limiar for atingido, estes utilizadores têm de ser reautenticar e o respetivo acesso é registado. Quando isto acontecer, se as respetivas credenciais não estiverem colocadas em cache, é pedido aos utilizadores que iniciem sessão antes de poderem abrir o documento ou e-mail.<br /><br />Para além da reautenticação, a política e a associação ao grupo de utilizadores são reavaliadas. Isto significa que os utilizadores podem experienciar resultados de acesso diferentes para o mesmo documento ou e-mail, se existirem alterações na associação de política ou grupo resultantes da última vez a que acederam ao conteúdo. Tal pode retirar o acesso se o documento tiver sido [revogado](../rms-client/client-track-revoke.md).|Dependendo do nível de confidencialidade do conteúdo:<br /><br />- **Número de dias em que o conteúdo está disponível sem ligação à Internet** = **7** para dados empresariais confidenciais que podem causar danos ao negócio se forem partilhados com pessoas não autorizadas. Esta recomendação proporciona um bom equilíbrio entre flexibilidade e segurança. Os exemplos incluem contratos, relatórios de segurança, resumos de previsões e dados de conta de vendas.<br /><br />- **Nunca** para dados empresariais altamente confidenciais que iriam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Esta recomendação prioriza a segurança sobre a flexibilidade e garante que se o documento tiver sido revogado, todos os utilizadores autorizados imediatamente não podem abrir o documento. Os exemplos incluem informações dos funcionários e clientes, palavras-passe, código de origem e relatórios financeiros previamente anunciados.|
    
    Quando terminar de configurar as permissões, clique em **OK**. 
    
    Este agrupamento de definições cria um modelo personalizado para o serviço Azure Rights Management. Estes modelos podem ser utilizados com aplicações e serviços que se integram no Azure Rights Management. Para obter mais informações sobre como os computadores e os serviços transferem e atualizam estes modelos, veja [Atualizar modelos para utilizadores e serviços](refresh-templates.md).

10. Se tiver selecionado **HYOK (AD RMS)**, selecione **detalhes de modelos de conjunto de AD RMS** ou **definido de utilizador do conjunto de permissões (pré-visualização)**, e, em seguida, especifique o URL de licenciamento do seu AD RMS cluster.
    
    Para obter instruções para especificar um modelo GUID e o URL de licenciamento, consulte [localizar as informações para especificar proteção do AD RMS com uma etiqueta de Azure Information Protection](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    Para utilizar a opção de permissões definidas pelo utilizador, tem de ter a versão de pré-visualização do cliente Azure Information Protection. Esta opção permite aos utilizadores que especifique que devem ser concedidas permissões e quais são essas permissões. Em seguida, pode refinar esta opção e escolha apenas Outlook (predefinição), ou Word, Excel, PowerPoint e Explorador de ficheiros. 
    
    Se escolher a opção para o Outlook: A etiqueta é apresentada no Outlook e o comportamento resultante quando os utilizadores aplicam a etiqueta é o mesmo que a opção não reencaminhar.
    
    Se escolher a opção para Word, Excel, PowerPoint e Explorador de ficheiros: A etiqueta é apresentada nestas aplicações. O comportamento resultante quando os utilizadores aplicam a etiqueta é para apresentar a caixa de diálogo aos utilizadores selecionar permissões personalizadas. Na caixa de diálogo, os utilizadores tem de especificar as permissões, os utilizadores ou grupos e quaisquer data de expiração. Certifique-se de que os utilizadores têm instruções e orientações sobre como fornecer estes valores. Atualmente, esta opção sempre no Explorador de ficheiros utiliza a proteção Azure RMS em vez de proteção de HYOK (AD RMS).

11. Clique em **OK** para fechar o painel **Proteção** e ver a sua opção **Não reencaminhar** ou a apresentação do modelo selecionado da opção **Proteção** no painel **Etiqueta**.

12. No painel **Etiqueta**, clique em **Guardar**.

13. No **Azure Information Protection** painel, utilize o **PROTEÇÃO** coluna para confirmar que a etiqueta apresenta agora a definição de proteção que pretende:
    
    - **O Azure RMS** ou **HYOK (AD RMS)**, ou uma marca de verificação se tiver configurado a proteção. 
    
    - **Remova a proteção** ou uma marca de x para denotar cancelamento se tiver configurado uma etiqueta para remover a proteção.
    
    - Um campo em branco quando a proteção não está definida. 

13. Para disponibilizar as alterações aos utilizadores, clique em **Publicar**.

## <a name="next-steps"></a>Passos seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]