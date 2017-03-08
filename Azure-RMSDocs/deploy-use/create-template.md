---
title: Configurar e publicar um modelo personalizado do Azure RMS
description: "Instruções para criar e gerir modelos personalizados no portal clássico do Azure. Os modelos facilitam a aplicação de políticas adequadas para proteger documentos e e-mails por parte de utilizadores finais e outros administradores."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d6e9aa0c-1694-4a53-8898-4939f31cc13f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 11971a176b9c5f413bbe6daa208c062a131343be
ms.openlocfilehash: 5ab725294d93540f35c395eca08f5f3fbc6ae392
ms.lasthandoff: 02/24/2017


---


# <a name="create-configure-and-publish-a-custom-template"></a>Criar, configurar e publicar um modelo personalizado

>*Aplica-se a: Azure Information Protection, Office 365*


Criar e gerir modelos personalizados no portal clássico do Azure. Pode fazê-lo diretamente a partir do portal clássico do Azure ou pode iniciar sessão no centro de administração do Office 365 e escolher as **funcionalidades avançadas** do Rights Management que, em seguida, redireciona para o portal clássico do Azure.

Tem de ser um administrador global para criar e gerir modelos no portal clássico do Azure. Se tiver atribuído a função de administrador global para o serviço Azure Rights Management a outros utilizadores, estes também podem criar e gerir modelos, mas têm de utilizar o [PowerShell](configure-templates-with-powershell.md). Para obter mais informações, veja [Tenho de ser um administrador global para configurar o Azure RMS ou posso delegar noutros administradores?](../get-started/faqs-rms.md#do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators) 

Utilize os seguintes procedimentos para criar, configurar e publicar modelos personalizados do Rights Management.

## <a name="to-create-a-custom-template"></a>Para criar um modelo personalizado

1.  Consoante opte por iniciar sessão no centro de administração do Office 365 ou no portal clássico do Azure, efetue um dos seguintes procedimentos:

    -   No **centro de administração do Office 365**, a navegação varia conforme esteja a utilizar a pré-visualização do centro de administração do Office 365 (e qual a versão) ou o centro de administração clássico do Office 365. No entanto, em todas as versões, pode aceder diretamente à página [rights management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx): 

        1.  Na secção **configuração adicional**, clique em **funcionalidades avançadas**.

            > [!NOTE]
            > Se o serviço Rights Management não estiver ativado, primeiro clique em **Ativar** e confirme a ação. Para obter mais informações, veja [Ativar o Azure Rights Management](activate-service.md).
            > 
            > Se não clicou em **funcionalidades avançadas** anteriormente, depois de o Rights Management ser ativado, siga as instruções no ecrã para obter uma subscrição gratuita do Azure, pois é necessária para aceder ao portal clássico do Azure.

            Clicar em **funcionalidades avançadas** carrega o portal clássico do Azure, onde pode gerir a **RIGHTS MANAGEMENT** do Azure Active Directory da sua organização.

    -   No [portal clássico do Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081):

        1.  No painel esquerdo, clique em **ACTIVE DIRECTORY**.

        2.  Na página **active directory**, clique em **RIGHTS MANAGEMENT**.

        3.  Selecione o diretório em que pretende gerir o Rights Management.

        4.  Se ainda não ativou o Rights Management, primeiro clique em **ATIVAR** e confirme a ação.

            > [!NOTE]
            > Para obter mais informações, veja [Ativar o Azure Rights Management](activate-service.md).

2.  Criar um novo modelo:

    -   No portal clássico do Azure, a partir da página de início rápido **Introdução ao Rights Management**, clique em **Criar um novo modelo de política de direitos**.

        Se não vir logo esta página depois de seguir as instruções do Office 365, utilize as instruções de navegação acima para aceder ao portal clássico do Azure.

3. Na página **Adicionar um novo modelo de política de direitos**, selecione o idioma no qual irá escrever o nome do modelo e a descrição que será vista pelos utilizadores (pode adicionar mais idiomas posteriormente). Em seguida, escreva um nome exclusivo e uma descrição e clique no botão Concluir.

    Não inclua uma vírgula ou ponto e vírgula no nome ou descrição do seu modelo. Nem todos os serviços e aplicações que utilizam modelos do Rights Management conseguem suportar estes carateres para estes modelos. Neste cenário, estes serviços e aplicações poderão não conseguir obter ou utilizar estes modelos do Azure Rights Management.

4. Na página de início rápido **Introdução ao Rights Management**, clique em **Gerir modelos de política de direitos**. Verá o modelo criado recentemente adicionado à lista de modelos, com o estado **Arquivado**. Nesta fase, o modelo é criado mas não é configurado nem é visível para os utilizadores.

## <a name="to-configure-and-publish-a-custom-template"></a>Para configurar e publicar um modelo personalizado

1.  Selecione o modelo criado recentemente na página **MODELOS** do portal clássico do Azure.

2.  Na página de início rápido **O seu modelo foi adicionado**, clique em **Começar** no passo 1, **Configurar os direitos dos utilizadores e grupos,** clique em **COMEÇAR AGORA** ou **ADICIONAR** e, em seguida, selecione os utilizadores e grupos que irão ter o direito a utilizar os conteúdos protegidos pelo novo modelo.

    > [!NOTE]
    > Os utilizadores ou grupos que selecionou têm de possuir um endereço de e-mail. Num ambiente de produção, este será quase sempre o caso, mas num ambiente de teste simples poderá ter de adicionar endereços de e-mail às contas de utilizador ou grupos.

    De acordo com as melhores práticas, utilize grupos em vez de utilizadores, pois simplifica a gestão dos modelos. No entanto, se fizer alterações ao grupo, tenha em atenção que, por motivos de desempenho, o Azure Rights Management [coloca a associação do grupo em cache](../plan-design/prepare.md#group-membership-caching). 
    
    Se tiver o Active Directory no local e estiver a sincronizar com o Azure AD, pode utilizar grupos com capacidade de correio (grupos de segurança ou grupos de distribuição). Para conceder direitos a todos os utilizadores na organização, um método mais eficiente será copiar um dos modelos predefinidos em vez de especificar múltiplos grupos. Para mais informações, veja [Como copiar um modelo](copy-template.md).

    > [!TIP]
    > Pode adicionar utilizadores fora da sua organização ("utilizadores externos") ao modelo selecionando um grupo com capacidade de correio que contém os contactos do Office 365 ou Exchange Online. Isto permite-lhe atribuir direitos a estes utilizadores da mesma forma que pode atribuir direitos aos utilizadores na sua organização. Por exemplo, pode impedir os clientes de editar uma lista de preços que lhes enviou. Não utilize esta configuração de modelo para proteger e-mails se os utilizadores fora da sua organização forem ler os e-mails protegidos utilizando o Outlook Web App.
    > 
    > Além disso, pode adicionar mais tarde utilizadores de fora da sua organização ao modelo, por **utilizadores específicos**, **grupos** ou **todos os utilizadores dessa organização**. Para tal, utilize o [Módulo do Windows PowerShell para o Azure Rights Management](install-powershell.md) e um dos seguintes métodos:
    > 
    > -  **Utilizar um objeto de definição de direitos para atualizar um modelo**: especifique os utilizadores externos (por endereço de e-mail dos utilizadores, endereço de e-mail do grupo ou por um domínio para todos os utilizadores nessa organização) e os seus direitos num objeto de definição de direitos. Em seguida, utilize este objeto de definição de direitos para atualizar o modelo. Deve especificar o objeto de definição de direitos com o cmdlet [New-AadrmRightsDefinition](/powershell/aadrm/vlatest/new-aadrmrightsdefinition) para criar uma variável e, em seguida, fornecer esta variável ao parâmetro -RightsDefinition com o cmdlet [Set-AadrmTemplateProperty](/powershell/aadrm/vlatest/set-aadrmtemplateproperty) para modificar um modelo existente. No entanto, se estiver a adicionar estes utilizadores a um modelo existente, também terá de definir os objetos de definição de direitos dos grupos existentes nos modelos e não apenas dos utilizadores externos novos.
    > -  **Exportar, editar e importar o modelo atualizado**: utilize o cmdlet [Export-AadrmTemplate](/powershell/aadrm/vlatest/export-aadrmtemplate) para exportar o modelo para um ficheiro que possa editar para adicionar os utilizadores externos (por endereço de e-mail dos utilizadores, endereço de e-mail do grupo ou por um domínio para todos os utilizadores nessa organização) e os seus direitos aos grupos e direitos existentes. Em seguida, utilize o cmdlet [Import-AadrmTemplate](/powershell/aadrm/vlatest/import-aadrmtemplate) para importar esta alteração novamente para o Azure RMS.

3.  Clique no botão Seguinte e atribua um dos direitos indicados aos seus utilizadores e grupos selecionados.

    Utilize a descrição apresentada para obter mais informações sobre cada direito (e para direitos personalizados). Também estão disponíveis mais informações detalhadas no tópico [Configurar direitos de utilização para o Azure Rights Management](configure-usage-rights.md). No entanto, a forma como as aplicações que suportam o Rights Management implementam estes direitos pode variar. Veja a respetiva documentação e faça os seus próprios testes com as aplicações que os utilizadores usam para verificar o comportamento antes de implementar o modelo para os utilizadores. Para tornar este modelo visível apenas para os administradores no âmbito deste teste, torne o modelo num modelo departamental (passo 6).

4.  Se tiver selecionado **Personalizado**, clique no botão Seguinte e selecione esses direitos personalizados.

    Apesar de poder utilizar todas as combinações de direitos individuais disponíveis, em algumas aplicações, alguns direitos podem ter dependências noutros direitos individuais. Quando for este o caso, os direitos dependentes são automaticamente selecionados por si.

    > [!TIP]
    > Considere adicionar o direito **Copiar e Extrair Conteúdo** e conceder o mesmo aos administradores ou pessoal nas outras funções que tenham responsabilidades de recuperação de informações. A concessão deste direito permite-lhes remover a proteção, se necessário, de ficheiros e e-mails que serão protegidos com este modelo. Esta possibilidade de remover a proteção ao nível do modelo fornece um controlo mais detalhado do que quando utilizam a funcionalidade de superutilizador.

5.  Clique no botão Concluir.

6.  Se quiser que o modelo seja visível apenas para um subconjunto de utilizadores quando veem uma lista de modelos de aplicações: clique em **ÂMBITO** para configurar este modelo como um modelo departamental e clique em **COMEÇAR AGORA**. Caso contrário, avance para o passo 9.

    Mais informações sobre modelos departamentais: por predefinição, todos os utilizadores no seu diretório do Azure veem todos os modelos publicados e podem, em seguida, selecioná-los a partir das aplicações quando pretendem proteger conteúdos. Se quiser que apenas determinados utilizadores vejam alguns dos modelos publicados, deve definir o âmbito dos modelos para estes utilizadores. Assim, só esses utilizadores poderão selecionar estes modelos. Os outros utilizadores que não especificou não verão os modelos e, por isso, não poderão selecioná-los. Esta técnica pode facilitar a escolha do modelo correto para os utilizadores, principalmente quando cria modelos concebidos para serem utilizados por grupos ou departamentos específicos. Deste modo, os utilizadores só veem os modelos que foram concebidos para eles.

    Por exemplo, se criou um modelo para o departamento de Recursos Humanos que aplica a permissão Só de Leitura aos membros do departamento Financeiro. Deverá definir o âmbito do modelo para o grupo com permissões de e-mail denominado RecursosHumanos para que apenas os membros do departamento de Recursos Humanos possam aplicar este modelo quando estiverem a utilizar o cliente do Azure Information Protection. Assim, apenas os membros deste grupo poderão aplicar este modelo. Além disso, se os utilizadores executarem o cliente do Azure Information Protection no [modo apenas de proteção](../rms-client/client-protection-only-mode.md), não verão este modelo.

7.  Na página **VISIBILIDADE DO MODELO**, selecione os utilizadores e grupos que vão conseguir ver e selecionar o modelo a partir das aplicações suportadas pelo RMS. Como anteriormente, de acordo com as melhores práticas, utilize grupos em vez de utilizadores e os grupos ou utilizadores que selecionar têm de ter um endereço de e-mail.

8.  Clique no botão Seguinte e decida se precisa de configurar a compatibilidade aplicacional para o seu modelo departamental. Se o fizer, clique em **COMPATIBILIDADE APLICACIONAL**, selecione a caixa de verificação e clique em **Concluir**.

    Por que razão poderá ser necessário configurar a compatibilidade aplicacional? Nem todas as aplicações conseguem suportar modelos departamentais. Para fazê-lo, a aplicação primeiro tem de efetuar a autenticação com o serviço RMS antes de transferir os modelos. Se o processo de autenticação não ocorrer, por predefinição, nenhum dos modelos departamentais serão transferidos. Pode substituir este comportamento ao especificar que todos os modelos departamentais deverão ser transferidos, ao configurar a compatibilidade aplicacional e selecionar a caixa de verificação **Mostrar este modelo a todos os utilizadores quando as aplicações não suportam a identidade de utilizador**.

    Por exemplo, se não configurar a compatibilidade aplicacional para o modelo departamental no nosso exemplo de Recursos Humanos, apenas os utilizadores do departamento de Recursos Humanos veem o modelo departamental quando utilizarem o cliente do Azure Information Protection no [modo apenas de proteção](../rms-client/client-protection-only-mode.md), mas nenhum utilizador verá o modelo departamental quando utilizar o Outlook Web Access (OWA) do Exchange Server 2013, porque o OWA do Exchange e o Exchange ActiveSync atualmente não suportam modelos departamentais. Se substituir este comportamento predefinido ao configurar a compatibilidade aplicacional, apenas os utilizadores do departamento de Recursos Humanos poderão ver o modelo departamental quando utilizarem o cliente do Azure Information Protection, mas todos os utilizadores poderão ver o modelo departamental quando utilizarem o Outlook Web Access (OWA). Se os utilizadores utilizarem o OWA ou o Exchange ActiveSync do Exchange Online, todos os utilizadores irão ver os modelos departamentais ou nenhum utilizador verá os modelos departamentais, com base no estado do modelo (arquivado ou publicado) no Exchange Online.

    O Office 2016 suporta nativamente modelos departamentais, assim como o Office 2013 a partir da versão 15.0.4727.1000, lançada em junho de 2015 como parte do [KB 3054853](https://support.microsoft.com/kb/3054853).

    > [!NOTE]
    > Se tiver aplicações que ainda não suportam de forma nativa os modelos departamentais, pode utilizar um script de transferência de modelos do RMS personalizado ou outras ferramentas para implementar estes modelos na pasta de cliente do RMS local. Em seguida, estas aplicações apresentarão corretamente os modelos departamentais apenas para os utilizadores e grupos que selecionou para o âmbito do modelo:
    > 
    > -   Para o Office 2010, a pasta do cliente é **%localappdata%\Microsoft\DRM\Templates**.
    > -   A partir de um computador cliente que tenha transferido todos os modelos, pode copiar e, em seguida, colar os ficheiros dos modelos para outros computadores.
    > 
    > Pode [Transferir o script de modelo do RMS personalizado a partir do site Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=524506). Se vir um erro quando clicar nesta ligação é porque, provavelmente, ainda não está registado no Microsoft Connect. Para se registar:
    > 
    > 1.  Aceda ao [site Microsoft Connect](http://www.connect.microsoft.com) e inicie sessão com a sua Conta Microsoft.
    > 2.  Clique em **Diretório** e selecione a categoria **Ver produtos Connect que não estão a aceitar feedback atualmente**.
    > 3.  Procure **Serviços de Gestão de Direitos** e para o programa **Funcionalidades Empresariais do Microsoft RMS**, clique em **Aderir**.

9. Clique em **CONFIGURAR** e adicione outros idiomas usados pelos utilizadores, juntamente com o nome e descrição deste modelo nesse idioma. Se tiver utilizadores multilingues, é importante adicionar todos os idiomas que eles utilizam e fornecer um nome e descrição nesse idioma. Assim, os utilizadores verão o nome e descrição do modelo no mesmo idioma utilizado pelo seu sistema operativo de cliente, garantindo que compreendem a política aplicada a um documento ou mensagem de e-mail. Se não houver nenhuma correspondência com os respetivos sistemas operativos de cliente, o nome e descrição que veem é revertido para o idioma e descrição que você definiu quando criou o modelo.

    Em seguida, verifique se quer fazer alterações às seguintes definições:

    |Definição|Mais informações| Definição recomendada
    |-----------|--------------------|--------------------|
    |**expiração de conteúdos**|Defina uma data ou número de dias para este modelo que represente o tempo durante o qual não é possível abrir o modelo quando os ficheiros estão protegidos. Pode especificar uma data ou um número de dias, começando pelo momento em que a proteção foi aplicada ao ficheiro.<br /><br />Quando especificar uma data, a mesma é efetiva a partir da meia-noite no seu fuso horário atual.|**O conteúdo nunca expira** exceto se o conteúdo tiver um requisito controlado por um tempo específico.|
    |**acesso offline**|Utilize esta definição para adaptar todos os seus requisitos de segurança de acordo com o requisito de que os utilizadores têm de conseguir abrir ficheiros protegidos quando não têm uma ligação à Internet.<br /><br />Se especificar que os conteúdos não estão disponíveis sem uma ligação à Internet ou que os conteúdos só estão disponíveis para um número especificado de dias, quando esse limiar for atingido, os utilizadores têm de ser novamente autenticados e o respetivo acesso é registado. Quando isto acontecer, se as respetivas credenciais não estiverem colocadas em cache, é pedido aos utilizadores que iniciem sessão antes de poderem abrir o ficheiro.<br /><br />Além da reautenticação, a política e a associação a grupos de utilizadores são reavaliadas. Isto significa que os utilizadores podem experienciar resultados de acesso diferentes para o mesmo ficheiro, se existirem alterações na associação de política ou grupo resultantes da última vez a que acederam ao ficheiro.|Dependendo do nível de confidencialidade do conteúdo:<br /><br />- **Número de dias em que o conteúdo está disponível sem ligação à Internet** = **7** para dados empresariais confidenciais que podem causar danos ao negócio se forem partilhados com pessoas não autorizadas. Esta recomendação proporciona um bom equilíbrio entre flexibilidade e segurança. Por exemplo: contratos, relatórios de segurança, resumos de previsões e dados de conta de vendas.<br /><br />- **O conteúdo está disponível apenas com uma ligação à Internet** para dados empresariais muito confidenciais que podem causar danos ao negócio se forem partilhados com pessoas não autorizadas. Esta recomendação dá mais prioridade à segurança do que à flexibilidade. Exemplos: informações dos funcionários e clientes, palavras-passe, código de origem e relatórios financeiros previamente anunciados.|

10. Quando tiver a certeza de que o modelo está configurado corretamente para os seus utilizadores, clique em **PUBLICAR** para tornar o modelo visível para os utilizadores e, em seguida, clique em **GUARDAR**.

11. Clique no botão Anterior no portal clássico para voltar à página **MODELOS**, onde agora o seu modelo tem o estado atualizado **Publicado**.

Para fazer alterações ao seu modelo, selecione-o e, em seguida, utilize os passos de início rápido novamente. Em alternativa, selecione uma das seguintes opções:

-   Para adicionar mais utilizadores e grupos e definir os direitos desses utilizadores e grupos: clique em **DIREITOS** e, em seguida, clique em **ADICIONAR**.

-   Para remover utilizadores ou grupos que selecionou anteriormente: clique em **DIREITOS**, selecione o utilizador ou grupo da lista e, em seguida, clique em **ELIMINAR**.

-   Para alterar que utilizadores podem ver os modelos para selecioná-los a partir de aplicações: clique em **ÂMBITO**, em seguida, clique em **ADICIONAR**, **ELIMINAR**, ou **COMPATIBILIDADE APLICACIONAL**.

-   Para fazer com que o modelo deixe de estar visível para todos os utilizadores: clique em **CONFIGURAR**, clique em **ARQUIVAR** e, em seguida, clique em **GUARDAR**.

-   Para fazer outras alterações de configuração: clique em **CONFIGURAR**, faça as alterações pretendidas e, em seguida, clique em **GUARDAR**.

> [!WARNING]
> Quando fizer alterações a um modelo que foi guardado anteriormente, os clientes não irão ver essas alterações feitas ao modelo até que os modelos sejam atualizados nos respetivos computadores. Para mais informações, veja [Atualizar modelos para os utilizadores](refresh-templates.md).

## <a name="see-also"></a>Veja Também
[Configurar modelos personalizados para o Azure Rights Management](configure-custom-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
