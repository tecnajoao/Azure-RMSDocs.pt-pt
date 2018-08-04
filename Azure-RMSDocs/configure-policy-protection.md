---
title: Configurar uma etiqueta do Azure Information Protection para proteção
description: Pode proteger os seus documentos e e-mails mais confidenciais ao configurar uma etiqueta para utilizar a proteção do Rights Management.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/02/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: b41add3430fbf00a372a5ec54d1ecd8c27fa7fa6
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491705"
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Como configurar uma etiqueta para a proteção do Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Pode proteger os documentos e e-mails mais confidenciais utilizando um serviço de Rights Management. Este serviço utiliza políticas de encriptação, identidade e autorização para ajudar a evitar perda de dados. A proteção foi aplicada com uma etiqueta que está configurada para utilizar a proteção do Rights Management para documentos e e-mails e os utilizadores também podem selecionar o **não reencaminhar** botão no Outlook.

Quando a sua etiqueta está configurada com a definição de proteção do **Azure (chave da cloud)**, nos bastidores, esta ação cria e configura um modelo de proteção que pode ser acedido por serviços e aplicações que se integram Modelos de gestão de direitos. Por exemplo, Exchange Online e as regras de fluxo de correio e o Outlook na web. 

## <a name="how-the-protection-works"></a>Como funciona a proteção

Quando um documento ou e-mail é protegido por um serviço de Rights Management, são encriptado em descanso e em trânsito. Em seguida, podem ser descriptografado somente por utilizadores autorizados. Esta encriptação permanece com o documento ou com o e-mail, mesmo que o nome seja alterado. Além disso, pode configurar direitos e restrições de utilização, tal como nos exemplos seguintes:

- Apenas os utilizadores dentro da organização podem abrir o documento ou o e-mail confidencial da empresa.

- Apenas os utilizadores do departamento de marketing podem editar e imprimir o documento de anúncio de promoção ou e-mail, enquanto todos os outros utilizadores na sua organização apenas podem ler este documento ou e-mail.

- Os utilizadores não podem reencaminhar um e-mail ou copiar informações do mesmo com notícias sobre uma reorganização interna.

- A lista de preços atual enviada para os parceiros de negócios não pode ser aberta após uma data especificada.

Para obter mais informações sobre a proteção Azure Rights Management e como ele funciona, consulte [o que é o Azure Rights Management?](what-is-azure-rms.md)

> [!IMPORTANT]
> Para configurar uma etiqueta para aplicar esta proteção, o serviço Azure Rights Management tem de ser ativado para a sua organização. Para obter mais informações, veja [Ativar o Azure Rights Management](activate-service.md).

Quando a etiqueta aplicar proteção, um documento protegido não é adequado para serem salvos no SharePoint ou o OneDrive. Estas localizações não suportam as seguintes funcionalidades para ficheiros protegidos: coautoria, Office Online, pesquisa, pré-visualização do documento, miniatura, deteção de dados Eletrónicos e prevenção de perda de dados (DLP). 

Exchange tem de ser configurada para o Azure Information Protection antes dos utilizadores podem aplicar etiquetas no Outlook para protegerem os seus e-mails. No entanto, até que o Exchange seja configurado para o Azure Information Protection, não obtém todas as funcionalidades de utilizar a proteção Azure Rights Management com o Exchange. Por exemplo, os utilizadores não podem ver e-mails protegidos no telemóvel ou com o Outlook na web, não é possível indexar os e-mails protegidos para pesquisa, e não é possível configurar o Exchange Online DLP para a proteção Rights Management. Para garantir que o Exchange pode suportar estes cenários adicionais, consulte os seguintes recursos:

- Para o Exchange Online, veja as instruções de [Exchange Online: configuração de IRM](configure-office365.md#exchange-online-irm-configuration).

- Para o Exchange no local, tem de implementar o [conector RMS e configurar os servidores do Exchange](deploy-rms-connector.md). 

## <a name="to-configure-a-label-for-protection-settings"></a>Para configurar uma etiqueta para as definições de proteção

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. Do **classificações** > **etiquetas** opção de menu: no **do Azure Information Protection – etiquetas** painel, selecione a etiqueta que pretende alterar. 

3. Sobre o **etiqueta** painel, localize **definir permissões para documentos e e-mails que contenham esta etiqueta**e selecione uma das seguintes opções:
    
    - **Não configurada**: selecione esta opção se a etiqueta estiver configurada para aplicar a proteção e já não quiser que a etiqueta selecionada aplique a proteção. Em seguida, avance para o passo 11.
        
        De volta para a proteção configurada anteriormente, as definições são mantidas como um modelo de proteção arquivados e vão a ser apresentadas se alterar a opção **Protect**. Não vê este modelo no portal do Azure, mas se for necessário, pode continuar a gerir o modelo usando [PowerShell](configure-templates-with-powershell.md). Isso significa de comportamento que o conteúdo permanece acessível se tiver esta etiqueta com as definições de proteção aplicada anteriormente.
    
    - **Proteger**: selecione esta opção para aplicar a proteção e, em seguida, avance para o passo 5 para configurar definições de proteção.
    
    Nota: Foi possível guardar uma nova etiqueta nesse estágio sem configuração adicional. Se o fizer, a etiqueta é configurada para aplicar a proteção, de modo a que apenas a pessoa que aplica-se a etiqueta pode abrir o documento ou e-mail sem restrições de utilização. Em alguns casos, isso pode ser o resultado necessário, para que um usuário pode salvar um arquivo para qualquer localização e ter a garantia de que apenas estes poderão abri-lo. Se esse resultado corresponde aos seus requisitos e outros não são necessárias para colaborar em conteúdos protegidos, vá diretamente para o passo de 12 em vez do passo 5.
    
    - **Remover a proteção**: selecione esta opção para remover a proteção se um documento ou e-mail é protegido. Em seguida, avance para o passo 11.
        
        De volta para a proteção configurada anteriormente, as definições são mantidas como um modelo de proteção arquivados e vão a ser apresentadas se alterar a opção **Protect**. Não vê este modelo no portal do Azure, mas se for necessário, pode continuar a gerir o modelo usando [PowerShell](configure-templates-with-powershell.md). Isso significa de comportamento que o conteúdo permanece acessível se tiver esta etiqueta com as definições de proteção aplicada anteriormente.
        
        Tenha em atenção que para os utilizadores aplicarem uma etiqueta com esta opção, eles têm de ter permissões para remover a proteção do Rights Management. Este requisito, significa que os utilizadores têm de ter o **exportar** ou **controlo total** [direito de utilização](configure-usage-rights.md). Em alternativa, eles têm de ser o proprietário do Rights Management (que concede automaticamente o direito de utilização controlo total) ou ser um [Superutilizador do Azure Rights Management](configure-super-users.md). Os modelos do Azure Rights Management predefinidos não incluem os direitos de utilização que permitem que os utilizadores removam a proteção. 
        
        Se utilizadores não têm permissões para remover a proteção do Rights Management e selecionarem uma etiqueta que está configurada com esta **remover proteção** opção, verão a seguinte mensagem: **do Azure Information Protection Não é possível aplicar esta etiqueta. Se este problema persistir, contacte o seu administrador.**

4. Se selecionou **Proteger**, agora selecione **Proteção** para abrir o painel **Proteção**:
    
    ![Configurar a proteção para uma etiqueta do Azure Information Protection](./media/info-protect-protection-bar-configured.png)

5. Sobre o **proteção** painel, selecione **(chave da cloud) do Azure** ou **HYOK (AD RMS)**.
    
    Na maioria dos casos, selecione **Azure (chave da cloud)** para as definições de permissão. Não selecione **HYOK (AD RMS)**, a menos que tenha lido e compreendido os pré-requisitos e as restrições que acompanham esta configuração de "*tenha a sua própria chave*" (HYOK). Para obter mais informações, veja [Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS](configure-adrms-restrictions.md). Para continuar a configuração para HYOK (AD RMS), avance para o passo 9.
    
6. Selecione uma das seguintes opções:
    
    - **Definir permissões**: definir novas definições de proteção neste portal.
    
    - **Definir permissões definidas pelo utilizador (pré-visualização)**: para permitir aos utilizadores especificar que deve ser concedido permissões e quais são essas permissões. Em seguida, pode refinar esta opção e escolha apenas, o Outlook ou Word, Excel, PowerPoint e o Explorador de ficheiros. Esta opção não é suportada e não funcionam, quando uma etiqueta está configurada para [a classificação automática](configure-policy-classification.md).
        
        Se escolher a opção do Outlook: A etiqueta é apresentada no Outlook e o comportamento resultante quando os utilizadores de aplicar a etiqueta é o mesmo que a opção não reencaminhar.
        
        Se escolher a opção para Word, Excel, PowerPoint e o Explorador de ficheiros: quando esta opção estiver definida, a etiqueta é apresentada nesses aplicativos. O comportamento resultante quando os utilizadores de aplicar a etiqueta é exibir a caixa de diálogo para os utilizadores selecionarem permissões personalizadas. Na caixa de diálogo, os utilizadores tem de especificar as permissões, os utilizadores ou grupos e qualquer data de expiração. Certifique-se de que os utilizadores têm instruções e orientações sobre como fornecer estes valores.
    
    - **Selecione um modelo predefinido**: para utilizar um dos modelos predefinidos ou um modelo personalizado que configurou. Tenha em atenção que esta opção não é apresentada para novas etiquetas, ou se estiver a editar uma etiqueta que tenha utilizado o **definir permissões** opção.
    
    Para selecionar um modelo predefinido, o modelo tem de ser publicado (não arquivado) e não deve ser vinculado já a outra etiqueta. Quando seleciona esta opção, pode utilizar um **Editar modelo** botão [converter o modelo numa etiqueta](configure-policy-templates.md#to-convert-templates-to-labels).
    
    Sugestão: Se forem utilizados para a criação e edição de modelos personalizados, poderá considerar útil para referência [tarefas que costumava realizar com o portal clássico do Azure](migrate-portal.md).

7. Se tiver selecionado **definir permissões** para **Azure (chave da cloud)**, esta opção permite-lhe configurar as definições que pode configurar num modelo. 
    
    Selecione **adicionar permissões**e, no **adicionar permissões** painel, selecione o primeiro conjunto de utilizadores e grupos que terão direitos a utilizar os conteúdos que serão protegidos pela etiqueta selecionada:
    
    - Escolher **selecione na lista** onde pode, em seguida, adicionar todos os utilizadores da sua organização ao selecionar **Add \<nome da organização >-todos os membros**. Esta definição exclui as contas de convidado. Em alternativa, pode selecionar **adicionar utilizadores autenticados (pré-visualização)**, ou procure o diretório.
        
        Quando escolher todos os membros ou procurar o diretório, os utilizadores ou grupos têm de ter um endereço de e-mail. Num ambiente de produção, utilizadores e grupos quase sempre tem um endereço de e-mail, mas num ambiente de teste simple, poderá ter de adicionar endereços de e-mail a contas de utilizador ou grupos.
        
        ###### <a name="more-information-about-add-any-authenticated-users"></a>Obter mais informações sobre **adicionar utilizadores autenticados** 
        Esta definição não restringe quem pode aceder o conteúdo que a etiqueta protege, enquanto ainda encriptar o conteúdo e fornecer-lhe opções para restringir a como o conteúdo pode ser utilizadas (permissões) e acedidos (expiração e acesso offline). No entanto, o aplicativo abrindo o conteúdo protegido tem de ser capaz de suportar a autenticação a ser utilizada. Por esse motivo, federados fornecedores de redes sociais como o Google e autenticação de código de acesso onetime devem ser utilizados apenas para e-mails, e somente quando usar o Exchange Online e as novas capacidades de encriptação de mensagens do Office 365. Contas da Microsoft podem ser utilizadas com o Visualizador do Azure Information Protection e o Office 2016 Click-to-Run. 
        
        Alguns cenários comuns para quaisquer autenticado a definição de usuários: – não se quem vê o conteúdo, mas pretender restringir a sua utilização. Por exemplo, não pretender que o conteúdo a ser editado, copiados ou impressos.
            -Não é necessário restringir quem acessa o conteúdo, mas quer poder controlar quem abre-se e potencialmente, revogue.
            -Tem um requisito que o conteúdo tem de estar encriptado em descanso e em trânsito, mas ele não requer controlos de acesso.     
        
    - Escolher **introduza os detalhes** especificar manualmente o e-mail endereços para utilizadores individuais ou grupos (interno ou externo). Em alternativa, utilize esta opção para especificar todos os utilizadores na sua organização ao introduzir qualquer nome de domínio dessa organização. Também pode utilizar esta opção para fornecedores de redes sociais, introduzindo o respetivo nome de domínio, tal como **gmail.com**, **hotmail.com**, ou **outlook.com**.
        
    >[!NOTE]
    >Se um endereço de e-mail for alterado depois de selecionar o utilizador ou grupo, consulte a [considerações em caso de alteração de endereços de e-mail](prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) secção da documentação de planejamento.
    
    Como melhor prática, utilize grupos em vez de utilizadores. Esta estratégia mantém a sua configuração mais simples e torna menos provável que precisa atualizar a configuração de etiqueta mais tarde e, em seguida, voltar a proteger conteúdo. No entanto, se fizer alterações ao grupo, tenha em atenção que, por motivos de desempenho, o Azure Rights Management [coloca a associação do grupo em cache](prepare.md#group-membership-caching-by-azure-information-protection). 
    
    Quando especificar o primeiro conjunto de utilizadores e grupos, selecione as permissões a conceder estes utilizadores e grupos. Para obter mais informações sobre as permissões que pode selecionar, veja [Configuração de direitos de utilização para o Azure Rights Management](configure-usage-rights.md). No entanto, as aplicações que suportam esta proteção podem variar na forma como implementam essas permissões. Veja a respetiva documentação e faça os seus próprios testes com as aplicações que os utilizadores usam para verificar o comportamento antes de implementar o modelo para os utilizadores.
    
    Se for necessário, agora pode adicionar um segundo conjunto de utilizadores e grupos com direitos de utilização. Repita até especificar todos os utilizadores e grupos com as suas respectivas permissões.

    >[!TIP]
    >Considere adicionar o **guardar como, exportar (EXPORTAR)** permissão personalizada e conceder esta permissão para administradores de recuperação de dados ou pessoal nas outras funções que tenham responsabilidades de recuperação de informações. Se for necessário, estes utilizadores, em seguida, podem remover a proteção de ficheiros e e-mails que serão protegidos com esta etiqueta ou modelo. Esta capacidade para remover a proteção ao nível de permissão para um documento ou e-mail fornece um controlo mais detalhado do que o [funcionalidade de Superutilizador](configure-super-users.md).
    
    Para todos os utilizadores e grupos que especificou, diante a **proteção** painel, agora, verifique se deseja fazer alterações às seguintes definições. Note que estas definições, assim como acontece com as permissões, não se aplicam ao [Emissor ou proprietário do Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner), ou qualquer [super utilizador](configure-super-users.md) que atribuiu.
    
    ###### <a name="information-about-the-protection-settings"></a>Informações sobre as definições de proteção
    
    |Definição|Mais informações|Definição recomendada
    |-----------|--------------------|--------------------|
    |**expiração de conteúdos**|Defina uma data ou número de dias para quando documentos ou e-mails protegidos por estas definições não devem ser aberto para os utilizadores selecionados. Pode especificar uma data ou um número de dias, começando pelo momento em que a proteção foi aplicada ao conteúdo.<br /><br />Quando especificar uma data, a mesma é efetiva a partir da meia-noite no seu fuso horário atual.|**O conteúdo nunca expira** exceto se o conteúdo tiver um requisito controlado por um tempo específico.|
    |**Permitir acesso offline**|Utilize esta definição para equilibrar quaisquer requisitos de segurança que tem (. / inclui acesso após revogação) com a capacidade dos utilizadores selecionados abrir conteúdo protegido quando não têm uma ligação à Internet.<br /><br />Se especificar que o conteúdo não está disponível sem uma ligação à Internet ou que os conteúdos só estão disponíveis para um número especificado de dias, quando esse limiar for atingido, estes utilizadores têm possível reautenticar e respetivo acesso é registado. Quando isto acontecer, se as respetivas credenciais não estiverem colocadas em cache, é pedido aos utilizadores que iniciem sessão antes de poderem abrir o documento ou e-mail.<br /><br />Para além da reautenticação, a política e a associação de grupo do utilizador é reavaliada. Isto significa que os utilizadores podem experienciar resultados de acesso diferentes para o mesmo documento ou e-mail, se existirem alterações na associação de política ou grupo resultantes da última vez a que acederam ao conteúdo. Tal pode retirar o acesso se o documento tiver sido [revogado](./rms-client/client-track-revoke.md).|Dependendo do nível de confidencialidade do conteúdo:<br /><br />- **Número de dias em que o conteúdo está disponível sem ligação à Internet** = **7** para dados empresariais confidenciais que podem causar danos ao negócio se forem partilhados com pessoas não autorizadas. Esta recomendação proporciona um bom equilíbrio entre flexibilidade e segurança. Os exemplos incluem contratos, relatórios de segurança, resumos de previsões e dados de conta de vendas.<br /><br />- **Nunca** para dados empresariais altamente confidenciais que iriam causar danos à empresa se fossem partilhados com pessoas não autorizadas. Esta recomendação prioriza a segurança sobre a flexibilidade e garante que se o documento tiver sido revogado, todos os utilizadores autorizados imediatamente não podem abrir o documento. Exemplos: informações dos funcionários e clientes, palavras-passe, código de origem e relatórios financeiros previamente anunciados.|
    
    Quando terminar de configurar as permissões e definições, clique em **OK**. 
    
    Este agrupamento de definições cria um modelo personalizado para o serviço Azure Rights Management. Estes modelos podem ser utilizados com aplicações e serviços que se integram no Azure Rights Management. Para obter mais informações sobre como os computadores e os serviços transferem e atualizam estes modelos, veja [Atualizar modelos para utilizadores e serviços](refresh-templates.md).

8. Se tiver selecionado **selecionar um modelo predefinido** para **(chave da cloud) do Azure**, clique na caixa pendente e selecione o [modelo](configure-policy-templates.md) que pretende utilizar para proteger documentos e e-mails com esta etiqueta. Não ver modelos arquivados ou modelos que já estão selecionados para outra etiqueta.
    
    Se selecionar uma **modelo departamental**, ou se tiver configurado [controlos de inclusão](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
    - Os utilizadores que estão fora do âmbito configurado do modelo ou que são excluídos de aplicarem a proteção Azure Rights Management ainda veem a etiqueta mas não é possível aplicá-la. Se selecionarem a etiqueta, verão a seguinte mensagem: **O Azure Information Protection não pode aplicar esta etiqueta. Se este problema persistir, contacte o seu administrador.**
        
        Tenha em atenção que todos os modelos publicados são sempre apresentados, mesmo se estiver a configurar uma política de âmbito. Por exemplo, está a configurar uma política de âmbito para o grupo de Marketing. Os modelos que pode selecionar não são restringidos aos modelos que estão no âmbito do grupo de Marketing e é possível selecionar um modelo departamental que os utilizadores selecionados não podem utilizar. Para facilitar a configuração e para minimizar a resolução de problemas, considere atribuir ao modelo departamental o mesmo nome da etiqueta na sua política de âmbito. 

9. Se tiver selecionado **HYOK (AD RMS)**, selecione **detalhes de modelos de conjunto de AD RMS** ou **definida de utilizador do conjunto de permissões (pré-visualização)**. Em seguida, especifique o URL de licenciamento do cluster do AD RMS.
    
    Para obter instruções especificar um modelo de GUID e seu URL de licenciamento, consulte [localizar as informações para especificar proteção do AD RMS com uma etiqueta do Azure Information Protection](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    A opção de permissões definidas pelo utilizador permite aos utilizadores especificar que deve ser concedido permissões e quais são essas permissões. Em seguida, pode refinar esta opção e escolher apenas Outlook (predefinição), ou Word, Excel, PowerPoint e o Explorador de ficheiros. Esta opção não é suportada e não funcionam, quando uma etiqueta está configurada para [a classificação automática](configure-policy-classification.md).
    
    Se escolher a opção do Outlook: A etiqueta é apresentada no Outlook e o comportamento resultante quando os utilizadores de aplicar a etiqueta é o mesmo que a opção não reencaminhar.
    
    Se escolher a opção para Word, Excel, PowerPoint e o Explorador de ficheiros: A etiqueta é apresentada nesses aplicativos. O comportamento resultante quando os utilizadores de aplicar a etiqueta é exibir a caixa de diálogo para os utilizadores selecionarem permissões personalizadas. Na caixa de diálogo, os utilizadores tem de especificar as permissões, os utilizadores ou grupos e qualquer data de expiração. Certifique-se de que os utilizadores têm instruções e orientações sobre como fornecer estes valores.

10. Clique em **OK** para fechar a **proteção** painel e ver a sua opção **definidas pelo utilizador** ou o seu modelo que escolheu apresentado para o **proteção** opção de **etiqueta** painel.

11. No painel **Etiqueta**, clique em **Guardar**.

12. Sobre o **do Azure Information Protection** painel, utilize o **PROTEÇÃO** coluna para confirmar que a etiqueta mostra agora a definição de proteção que pretende:
    
    - Uma marca de verificação se tiver configurado a proteção. 
    
    - Uma marca x para denotar cancelamento se tiver configurado uma etiqueta para remover a proteção.
    
    - Um campo em branco quando a proteção não está definida. 

Quando clicado **guardar**, as suas alterações estão automaticamente disponíveis para utilizadores e serviços. Já não existe uma opção de publicar separado.


## <a name="example-configurations"></a>Configurações de exemplo

O **todos os funcionários** e **destinatários apenas** sublabels do **confidencial** e **elevada confidenciais** etiquetas a partir do [política predefinida](configure-policy-default.md) fornecer exemplos de como pode configurar as etiquetas que aplicam a proteção. Também pode utilizar os exemplos seguintes para o ajudar a configurar a proteção para diferentes cenários. 

Para cada exemplo que se segue, no seu \< *nome da etiqueta*> painel, selecione **proteger** e, em seguida, selecione **proteção** para abrir o  **Proteção** painel.

### <a name="example-1-label-that-applies-do-not-forward-to-send-a-protected-email-to-a-gmail-account"></a>Exemplo 1: Etiqueta que aplica-se não reencaminhar para enviar um e-mail protegido para uma conta do Gmail

Esta etiqueta só está disponível no Outlook e é adequada quando o Exchange Online está configurado para o [novas capacidades de encriptação de mensagens do Office 365](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Indique aos utilizadores para selecionarem esta etiqueta quando precisam de enviar um e-mail protegido para as pessoas a utilizar uma conta do Gmail (ou qualquer outra conta de e-mail fora da sua organização). 

Os utilizadores escrevem o endereço de e-mail do Gmail no **para** caixa.  Em seguida, selecionarem a etiqueta e a opção não reencaminhar é adicionada automaticamente à mensagem de e-mail. O resultado é que os destinatários não é possível reencaminhar o e-mail, imprimi-lo, copiá-lo ou guardar anexos ou guardar o e-mail como um nome diferente. 

1. Sobre o **proteção** painel, certifique-se de que **Azure (chave da cloud)** está selecionada.
    
2. Selecione **definir permissões definidas pelo utilizador (pré-visualização)**.

3. Certifique-se de que a seguinte opção está selecionada: **no Outlook aplicam-se não reencaminhar**.

4. Se selecionada, desmarque a opção seguinte: **no Word, Excel, PowerPoint e o Explorador de ficheiros pedir ao utilizador para permissões personalizadas**.

5. Clique em **OK** sobre o **proteção** painel e clique em **guardar** no **etiqueta** painel.


### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization-and-that-supports-immediate-revocation"></a>Exemplo 2: Etiqueta que restringe a permissão só de leitura a todos os utilizadores noutra organização, oferecendo suporte a revogação imediata

Esta etiqueta é adequada para a partilha (só de leitura) documentos altamente confidenciais que necessitam sempre de uma ligação à Internet para exibi-la. Se revogadas, os utilizadores não será capazes de exibir o documento na próxima vez que tentam abri-lo.

Esta etiqueta não é adequada para e-mails.

1. Sobre o **proteção** painel, certifique-se de que **Azure (chave da cloud)** está selecionada.
    
2. Certifique-se de que o **definir permissões** opção está selecionada e, em seguida, selecione **adicionar permissões**.

3. Sobre o **adicionar permissões** painel, selecione **introduza os detalhes**.

4. Introduza o nome de um domínio a partir de outra organização, por exemplo, **fabrikam.com**. Em seguida, selecione **adicionar**.

5. Partir **escolha as permissões da configuração predefinida**, selecione **Visualizador**e, em seguida, selecione **OK**.

6. Novamente o **proteção** painel, para **permitir que a definição de acesso offline**, selecione **Never**.

7. Clique em **OK** sobre o **proteção** painel e clique em **guardar** no **etiqueta** painel.


### <a name="example-3-add-external-users-to-an-existing-label"></a>Exemplo 3: Adicionar utilizadores externos para uma etiqueta existente

Os novos utilizadores que adicionar serão capazes de documentos abertos e e-mails que já foram protegidos com esta etiqueta. As permissões que conceder a estes utilizadores podem ser diferentes das permissões que têm dos utilizadores existentes.

1. Sobre o **proteção** painel, certifique-se **Azure (chave da cloud)** está selecionada.
    
2. Certifique-se de que **definir permissões** está selecionado e, em seguida, selecione **adicionar permissões**.

3. Sobre o **adicionar permissões** painel, selecione **introduza os detalhes**.

4. Introduza o endereço de e-mail do primeiro usuário (ou grupo) para adicionar e, em seguida, selecione **adicionar**.

5. Selecione as permissões para este utilizador (ou grupo).

6. Repita os passos 4 e 5 para cada utilizador (ou grupo) que pretende adicionar a esta etiqueta. Em seguida, clique em **OK**.

7. Clique em **OK** sobre o **proteção** painel e clique em **guardar** no **etiqueta** painel.

### <a name="example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward"></a>Exemplo 4: Etiqueta de e-mail protegidas que suporte permissões menos restritivas do que não reencaminhar

Esta etiqueta não pode ser restringida ao Outlook, mas fornece controles menos restritivos do que a utilização não reencaminhar. Por exemplo, pretende que os destinatários para poder copiar a partir do e-mail ou um anexo, ou salvar e editar um anexo.

Se especificar utilizadores externos que não tem uma conta no Azure AD:

- A etiqueta é adequada para e-mail ao Exchange Online está a utilizar o [novas capacidades de encriptação de mensagens do Office 365](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). 
 
- Para os anexos do Office são automaticamente protegidos, esses documentos estão disponíveis para ver num browser. Para editar estes documentos, transferir e edite-los com o Office 2016 Click-to-Run e uma conta Microsoft que utiliza o mesmo endereço de e-mail. [Mais informações](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)


> [!NOTE]
> Exchange Online está a implementar uma nova opção [só de criptografar](configure-usage-rights.md#encrypt-only-option-for-emails). Esta opção não está disponível para configuração de etiqueta. No entanto, quando sabe que os destinatários serão, pode utilizar este exemplo para configurar uma etiqueta com o mesmo conjunto de direitos de utilização. 

Quando os utilizadores, especifique os endereços de e-mail no **para** caixa, os endereços tem de ser para os mesmos utilizadores que especificou para esta configuração de etiqueta. Uma vez que os utilizadores podem pertencer a grupos e tem mais do que um endereço de e-mail, o endereço de e-mail especificam não tem de corresponder ao endereço de e-mail que especificar para as permissões. No entanto, especificando o mesmo que o endereço de e-mail é a maneira mais fácil para se certificar de que o destinatário irá ser autorizado com êxito. Para obter mais informações sobre como os utilizadores estão autorizados para permissões, consulte [preparar utilizadores e grupos do Azure Information Protection](prepare.md). 

1. Sobre o **proteção** painel, certifique-se de que **Azure (chave da cloud)** está selecionada.
    
2. Certifique-se **definir permissões** está selecionado e selecione **adicionar permissões**.

3. Sobre o **adicionar permissões** painel: para conceder permissões a utilizadores na sua organização, selecione **Add \<nome da organização >-todos os membros** para selecionar todos os utilizadores no seu inquilino. Esta definição exclui as contas de convidado. Em alternativa, selecione **procurar diretório** para selecionar um grupo específico. Para conceder permissões a utilizadores externos ou se digitar o endereço de e-mail, selecione **introduza os detalhes** e escreva o endereço de e-mail do utilizador, ou grupo do Azure AD ou um nome de domínio.
    
    Repita este passo para especificar os utilizadores adicionais que devem ter as mesmas permissões.

4. Para **escolha as permissões da configuração predefinida**, selecione **Coproprietário**, **Coautor**, **revisor**, ou **personalizado**para selecionar as permissões que pretende conceder.
    
    Nota: Não selecione **Visualizador** para e-mails e se selecionar **personalizada**, certifique-se de que inclui **editar e guardar**.
    
    Para selecionar as mesmas permissões que corresponder ao novo **só Encrypt** opção do Exchange Online, selecione **personalizado**. Em seguida, selecione todas as permissões, exceto **guardar como, exportar (EXPORTAR)** e **controlo total (proprietário)**.

5. Para especificar os utilizadores adicionais que devem ter permissões diferentes, repita os passos 3 e 4.

6. Clique em **OK** sobre o **adicionar permissões** painel.

7. Clique em **OK** sobre o **proteção** painel e clique em **guardar** no **etiqueta** painel.


### <a name="example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it"></a>Exemplo 5: Etiqueta, que criptografa o conteúdo, mas não restringe quem pode acessá-lo

Esta configuração tem a vantagem de que não tem de especificar os utilizadores, grupos ou domínios para proteger um e-mail ou documento. O conteúdo ainda será encriptado e pode especificar direitos de utilização, uma data de expiração e acesso offline. Utilize esta configuração apenas quando não é necessário restringir quem pode abrir o documento protegido ou o e-mail. [Obter mais informações sobre esta definição](#more-information-about-add-any-authenticated-users)

1. Sobre o **proteção** painel, certifique-se **Azure (chave da cloud)** está selecionada.
    
2. Certifique-se **definir permissões** está selecionado e, em seguida, selecione **adicionar permissões**.

3. Sobre o **adicionar permissões** painel, no **selecione na lista** separador, selecione **adicionar utilizadores autenticados (pré-visualização)**.

4. Selecione as permissões que pretende e clique em **OK**.

5. Novamente o **proteção** painel, configurar definições para **expiração de conteúdo** e **permitir o acesso offline**, se necessário e, em seguida, clique em **OK**.

6. Sobre o **rótulo** painel, selecione **guardar**.


## <a name="next-steps"></a>Passos Seguintes

Para mais informações sobre como configurar a política do Azure Information Protection, utilize as ligações na secção [Configurar política da organização](configure-policy.md#configuring-your-organizations-policy). 

As regras de fluxo de correio do Exchange também podem aplicar a proteção, com base em suas etiquetas. Para obter mais informações e exemplos, consulte [configurar o Exchange Online regras de fluxo de correio etiquetas do Azure Information Protection](configure-exo-rules.md).  
