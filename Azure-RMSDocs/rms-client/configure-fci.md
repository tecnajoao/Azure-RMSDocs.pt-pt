---
title: "Proteção do Azure RMS com o Windows Server FCI – AIP"
description: "Instruções para utilizar o cliente de Gestão de Direitos (RMS) com a ferramenta RMS Protection para configurar o Gestor de Recursos do Servidor de Ficheiros e a infraestrutura de classificação de ficheiros (FCI)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/22/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: dfa751ef7cd4c8405fa02299576cb57083d63495
ms.sourcegitcommit: 228953e96609b3c5ec8deddaab91be59650d9006
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2017
---
# <a name="rms-protection-with-windows-server-file-classification-infrastructure-fci"></a>Proteção RMS com Infraestrutura de Classificação de Ficheiros (FCI) do Windows Server

>*Aplica-se a: Azure Information Protection, Windows Server 2016, Windows Server 2012, Windows Server 2012 R2*

Utilize este artigo para obter instruções e um script para utilizar o cliente do Azure Information Protection e o PowerShell para configurar o Gestor de Recursos do Servidor de Ficheiros e a Infraestrutura de Classificação de Ficheiros (FCI).

Esta solução permite-lhe proteger automaticamente todos os ficheiros numa pasta num servidor de ficheiros com o Windows Server ou proteger automaticamente ficheiros que cumpram critérios específicos. Por exemplo, ficheiros que tenham sido classificados como contendo informações confidenciais. Esta solução liga-se diretamente ao serviço Azure Rights Management do Azure Information Protection para proteger os ficheiros, pelo que tem de ter este serviço implementado na sua organização.

> [!NOTE]
> Embora o Azure Information Protection inclua um [conector](../deploy-use/deploy-rms-connector.md) que suporta a Infraestrutura de Classificação de Ficheiros, essa solução só suporta a proteção nativa — por exemplo, ficheiros do Office.
> 
> Para suportar vários tipos de ficheiro com a infraestrutura de classificação de ficheiros do Windows Server, tem de utilizar o módulo **AzureInformationProtection** do PowerShell, conforme documentado neste artigo. Os cmdlets do Azure Information Protection, tal como o cliente do Azure Information Protection, suportam a proteção genérica, bem como a proteção nativa, o que significa que os tipos de ficheiro diferentes dos documentos do Office podem ser protegidos. Para obter mais informações, veja [Tipos de ficheiro suportados pelo cliente do Azure Information Protection](client-admin-guide-file-types.md) no guia do administrador do cliente do Azure Information Protection.

As instruções que se seguem aplicam-se ao Windows Server 2012 R2 ou Windows Server 2012. Se utilizar outras versões suportadas do Windows, poderá ter de adaptar alguns dos passos devido às diferenças entre a versão do seu sistema operativo e a descrita neste artigo.

## <a name="prerequisites-for-azure-rights-management-protection-with-windows-server-fci"></a>Pré-requisitos para a proteção do Azure Rights Management com a FCI do Windows Server
Pré-requisitos para estas instruções:

-  Nos servidores de ficheiros em que executará o Gestor de Recursos de Ficheiros com a infraestrutura de classificação de ficheiros:
    
    - Instalou o Gestor de Recursos do Servidor de Ficheiros como um dos serviços de função para a função Serviços de Ficheiros.
    
    - Identificou uma pasta local que contém ficheiros que pretende proteger com a Gestão de Direitos. Por exemplo, C:\FileShare.
    
    - Instalou o módulo AzureInformationProtection do PowerShell e configurou os pré-requisitos deste módulo para ligar ao serviço Azure Rights Management.
    
    O módulo AzureInformationProtection do PowerShell é incluído com o cliente do Azure Information Protection. Para obter instruções de instalação, consulte [instalar o cliente Azure Information Protection para os utilizadores](client-admin-guide-install.md) do Guia do administrador do Azure Information Protection. Se for necessário, pode instalar apenas o módulo do PowerShell com o parâmetro `PowerShellOnly=true`.
    
    Os [pré-requisitos para utilizar este módulo do PowerShell](client-admin-guide-powershell.md#azure-information-protection-and-azure-rights-management-service) incluem a ativação do serviço Azure Rights Management, a criação de um principal de serviço e a edição do registo se o seu inquilino estiver fora da América do Norte. Antes de iniciar as instruções neste artigo, confirme se tem valores para **BposTenantId**, **AppPrincipalId** e **Chave simétrica**, conforme documentado nestes pré-requisitos. 
    
    - Se quiser alterar o nível predefinido da proteção (nativo ou genérico) para extensões de nome de ficheiro específicas, terá de editar o registo, conforme descrito na página [Alterar o nível de proteção predefinido dos ficheiros](client-admin-guide-file-types.md#changing-the-default-protection-level-of-files) no guia do administrador.
    
    - Tiver uma ligação à Internet e configurou as definições do computador se forem necessários para um servidor proxy. Por exemplo: `netsh winhttp import proxy source=ie`
    
- Sincronizou as suas contas de utilizador do Active Directory no local com o Azure Active Directory ou o Office 365, incluindo os endereços de e-mail. Isto é necessário para todos os utilizadores que possam necessitar de aceder a ficheiros protegidos pela FCI e pelo serviço Azure Rights Management. Se não efetuar este passo (por exemplo, num ambiente de teste), os utilizadores poderão ficar bloqueados de aceder a estes ficheiros. Se precisar de mais informações sobre este requisito, veja [Preparar utilizadores e grupos para o Azure Information Protection](../plan-design/prepare.md).
    
- Transferiu os modelos do Rights Management para o servidor de ficheiros e identificou o ID do modelo que irá proteger os ficheiros. Para o fazer, utilize o cmdlet [Get-RMSTemplate](/powershell/azureinformationprotection/vlatest/get-rmstemplate). Este cenário não suporta modelos departamentais, pelo que tem de utilizar um modelo que não esteja configurado para um âmbito ou a configuração do âmbito tem de incluir a opção de compatibilidade de aplicações para marcar a caixa de verificação **Mostrar este modelo a todos os utilizadores quando as aplicações não suportam a identidade de utilizador**.

## <a name="instructions-to-configure-file-server-resource-manager-fci-for-azure-rights-management-protection"></a>Instruções para configurar a FCI do Gestor de Recursos do Servidor de Ficheiros para a proteção do Azure Rights Management
Siga estas instruções para proteger automaticamente todos os ficheiros numa pasta, através de um script do PowerShell como uma tarefa personalizada. Efetue estes procedimentos pela seguinte ordem:

1. Guardar o script do PowerShell

2. Criar uma propriedade de classificação para a Gestão de Direitos (RMS)

3. Criar uma regra de classificação (Classificar para RMS)

4. Configurar a agenda de classificação

5. Criar uma tarefa de gestão de ficheiros personalizada (Proteger ficheiros com o RMS)

6. Testar a configuração ao executar manualmente a regra e a tarefa

No final destas instruções, todos os ficheiros na sua pasta selecionada serão classificados com a propriedade personalizada do RMS e estes ficheiros estarão assim protegidos pela Gestão de Direitos. Para uma configuração mais complexa que protege seletivamente alguns ficheiros e não outros, pode criar ou utilizar uma propriedade e regra de classificação diferente, com uma tarefa de gestão de ficheiros que protege apenas esses ficheiros.

Tenha em atenção que se fizer alterações ao modelo do Rights Management que utiliza para a FCI, terá de executar `Get-RMSTemplate -Force` no computador do servidor de ficheiros para obter o modelo atualizado. O modelo atualizado, em seguida, é utilizado para proteger ficheiros novos. Se as alterações ao modelo são suficientemente importantes para voltar a proteger os ficheiros no servidor de ficheiros, pode fazê-lo executando o cmdlet Protect-RMSFile interativamente com uma conta que possui os direitos de utilização de exportação ou controlo total para os ficheiros. Terá também de executar `Get-RMSTemplate -Force` neste computador do servidor de ficheiros se publicar um novo modelo que pretenda utilizar para a FCI.

### <a name="save-the-windows-powershell-script"></a>Guardar o script do Windows PowerShell

1.  Copie os conteúdos do [script do Windows PowerShell](fci-script.md) para a proteção do Azure RMS através do Gestor de Recursos do Servidor de Ficheiros. Cole os conteúdos do script e atribua o nome **RMS-Protect-FCI.ps1** ao ficheiro no seu computador.

2.  Reveja o script e efetue as seguintes alterações:
    
    - Procure a seguinte cadeia e substitua-a pela AppPrincipalId, que utiliza com o cmdlet [Set-RMSServerAuthentication](/powershell/azureinformationprotection/vlatest/set-rmsserverauthentication) para ligar ao serviço Azure Rights Management:

        ```
        <enter your AppPrincipalId here>
        ```
        Por exemplo, o script poderá ter o seguinte aspeto:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)]             [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Procure a seguinte cadeia e substitua-a pela sua chave simétrica, que utiliza com o cmdlet [Set-RMSServerAuthentication](/powershell/azureinformationprotection/vlatest/set-rmsserverauthentication) para ligar ao serviço Azure Rights Management:

        ```
        <enter your key here>
        ```
        Por exemplo, o script poderá ter o seguinte aspeto:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Procure a seguinte cadeia e substitua-a pelo seu BposTenantId (ID de inquilino) que utiliza com o cmdlet [Set-RMSServerAuthentication](/powershell/azureinformationprotection/vlatest/set-rmsserverauthentication) para ligar ao serviço Azure Rights Management:

        ```
        <enter your BposTenantId here>
        ```
        Por exemplo, o script poderá ter o seguinte aspeto:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

3.  Assine o script. Se não assinar o script (mais seguro), tem de configurar o Windows PowerShell nos servidores que o executam. Por exemplo, execute uma sessão do Windows PowerShell com a opção **Executar como Administrador** e escreva: **Set-ExecutionPolicy RemoteSigned**. No entanto, esta configuração permite executar todos os scripts não assinados quando estes estão armazenados neste servidor (menos seguro).

    Para obter mais informações sobre como assinar os scripts do Windows PowerShell, veja [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) na biblioteca de documentação do PowerShell.

4.  Guarde o ficheiro localmente em cada servidor de ficheiros que executa o Gestor de recursos de ficheiros com a infraestrutura de classificação de ficheiros. Por exemplo, guarde o ficheiro em **C:\RMS-Protection**. Se utilizar um caminho ou nome de pasta diferente, escolha um caminho e uma pasta que não incluam espaços. Proteja este ficheiro com permissões NTFS para que os utilizadores não autorizados não o possam modificar.

Agora está pronto para iniciar a configuração do Gestor de Recursos do Servidor de Ficheiros.

### <a name="create-a-classification-property-for-rights-management-rms"></a>Criar uma propriedade de classificação para a Gestão de Direitos (RMS)

-   No Gestor de Recursos do Servidor de Ficheiros, em Gestão de Classificação, crie uma nova propriedade local:

    -   **Nome**: escreva **RMS**

    -   **Descrição**:   escreva **Proteção da Gestão de Direitos**

    -   **Tipo de Propriedade**: selecione **Sim/Não**

    -   **Valor**: selecione **Sim**

Agora podemos criar uma regra de classificação que utiliza esta propriedade.

### <a name="create-a-classification-rule-classify-for-rms"></a>Criar uma regra de classificação (Classificar para RMS)

-   Crie uma nova regra de classificação:

    -   No separador **Geral**:

        -   **Nome**: escreva **Classificar para RMS**

        -   **Ativado**: mantenha esta caixa de verificação selecionada, que é a predefinição.

        -   **Descrição**: escreva **Classificar todos os ficheiros na pasta &lt;nome da pasta&gt; para a Gestão de Direitos**.

            Substitua *&lt;nome da pasta&gt;* pelo nome da pasta que escolheu. Por exemplo, **Classificar todos os ficheiros na pasta C:\FileShare para a Gestão de Direitos**

        -   **Âmbito**: adicione a pasta escolhida. Por exemplo, **C:\FileShare**.

            Não selecione as caixas de verificação.

    -   Clique no separador **Classificação**:

    -   **Método de classificação**: selecione **Classificador de Pastas**

    -   Nome da **Propriedade**: selecione **RMS**

    -   Valor da **Propriedade**: selecione **Sim**

Pode executar as regras de classificação manualmente, para operações em curso, pretende que esta regra para executar com base numa agenda, para que os novos ficheiros são classificados com a propriedade do RMS.

### <a name="configure-the-classification-schedule"></a>Configurar a agenda de classificação

-   No separador **Classificação Automática**:

    -   **Ativar agenda fixa**: selecione esta caixa de verificação.

    -   Configure a agenda para todas as regras de classificação a executar, o que inclui a nossa nova regra para classificar ficheiros com a propriedade do RMS.

    -   **Permitir classificação contínua para novos ficheiros**: selecione esta caixa de verificação para que os novos ficheiros são classificados.

    -   Opcional: faça todas as alterações que quiser, como configurar as opções de relatórios e notificações.

Agora que concluiu a configuração de classificação, está pronto para configurar uma tarefa de gestão para aplicar a proteção RMS aos ficheiros.

### <a name="create-a-custom-file-management-task-protect-files-with-rms"></a>Criar uma tarefa de gestão de ficheiros personalizada (Proteger ficheiros com o RMS)

-   Em **Tarefas de Gestão de Ficheiros**, crie uma nova tarefa de gestão de ficheiros:

    -   No separador **Geral**:

        -   **Nome da tarefa**: escreva **Proteger ficheiros com RMS**

        -   Mantenha a caixa de verificação **Ativar** selecionada.

        -   **Descrição**: escreva **Proteger ficheiros em &lt;nome da pasta&gt; com a Gestão de Direitos e um modelo ao utilizar um script do Windows PowerShell.**

            Substitua *&lt;nome da pasta&gt;* pelo nome da pasta que escolheu. Por exemplo, **Proteger ficheiros em C:\FileShare com a Gestão de Direitos e um modelo ao utilizar um script do Windows PowerShell**

        -   **Âmbito**: selecione a pasta à sua escolha. Por exemplo, **C:\FileShare**.

            Não selecione as caixas de verificação.

    -   No separador **Ação**:

        -   **Tipo**: selecione **Personalizado**

        -   **Executável**: Especifique o seguinte:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Se o Windows não estiver na sua unidade C:, modifique este caminho ou navegue até este ficheiro.

        -   **Argumento**: Especifique o seguinte, fornecendo os seus próprios valores para &lt;path&gt; e &lt;template ID&gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Por exemplo, se tiver copiado o script para C:\RMS-Protection e o ID de modelo que identificou a partir dos pré-requisitos for e6ee2481-26b9-45e5-b34a-f744eacd53b0, especifique o seguinte:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            Neste comando, **[Source File Path]** e **[Source File Owner Email]** são ambas variáveis específicas da FCI, por isso escreva-as exatamente tal como aparecem no comando anterior. A variável primeira é utilizada pela FCI para especificar automaticamente o ficheiro identificado na pasta e a variável segundo é para a FCI obtenha automaticamente o endereço de e-mail do proprietário mencionado do ficheiro identificado. Este comando é repetido para cada ficheiro na pasta, o que, no nosso exemplo, significa cada ficheiro que se encontre na pasta C:\FileShare e tenha o RMS como uma propriedade de classificação de ficheiros.

            > [!NOTE]
            > O valor e o parâmetro **-OwnerMail [Source File Owner Email (E-mail do Proprietário do Ficheiro de Origem)]** garantem que os direitos de proprietário de Gestão de Direitos do ficheiro são concedidos ao proprietário original do ficheiro após este ser protegido. Esta configuração assegura que o proprietário do ficheiro original tem todos os direitos de gestão de direitos para os seus próprios ficheiros. Quando os ficheiros são criados por um utilizador de domínio, o endereço de e-mail é obtido automaticamente a partir do Active Directory através do nome de conta de utilizador na propriedade Proprietário do ficheiro. Para fazer isto, o servidor de ficheiros tem de se encontrar no mesmo domínio ou domínio fidedigno que o utilizador.
            > 
            > Sempre que possível, atribua os proprietários originais aos documentos protegidos, para garantir que estes utilizadores continuam a ter controlo total sobre os ficheiros que criaram. No entanto, se utilizar a variável [Source File Owner Email] como o comando anterior e um ficheiro não tem um utilizador de domínio definido como o proprietário (por exemplo, uma conta local foi utilizada para criar o ficheiro de, pelo que o proprietário apresentado for SYSTEM), o script falha.
            > 
            > Para ficheiros que não dispõem de um utilizador de domínio como proprietário, pode copiar e guardá-los como um utilizador de domínio, de modo a ser o proprietário apenas destes ficheiros. Em alternativa, se tiver as permissões, pode alterar manualmente o proprietário.  Ou, em alternativa, pode fornecer um endereço de e-mail específico (tal como o seu próprio ou um endereço de grupo para o departamento de TI) em vez da variável [Source File Owner Email], o que significa que todos os ficheiros a protege os utilizando este script utiliza este endereço de e-mail para definir o novo proprietário.

    -   **Executar o comando como**: selecione **Sistema Local**

    -   No separador **Condição**:

        -   **Propriedade**: selecione **RMS**

        -   Em **Operador**, selecione **Igual**

        -   **Valor**: selecione **Sim**

    -   No separador **Agenda**:

        -   **Executar em**: configure o horário da sua preferência.

            Reserve bastante tempo para que o script seja concluído. Embora esta solução proteja todos os ficheiros na pasta, o script é executado uma vez para cada ficheiro, de cada vez. Apesar de este processo ser mais demorado do que proteger todos os ficheiros ao mesmo tempo, o que é suportado pelo cliente do Azure Information Protection, esta configuração ficheiro-a-ficheiro para a FCI é mais eficiente. Por exemplo, os ficheiros protegidos podem ter diferentes proprietários (manter o proprietário original) quando utiliza a variável [Source File Owner Email], e esta ação ficheiro-a-ficheiro não é necessária se posteriormente alterar a configuração para proteger de forma seletiva os ficheiros em vez de todos os ficheiros numa pasta.

        -   **Executar continuamente em ficheiros novos**: selecione esta caixa de verificação.

### <a name="test-the-configuration-by-manually-running-the-rule-and-task"></a>Testar a configuração ao executar manualmente a regra e a tarefa

1.  Executar a regra de classificação:

    1.  Clique em **Regras de Classificação** &gt; **Executar Classificação Com Todas as Regras Agora**

    2.  Clique em **Aguardar conclusão da classificação** e, em seguida, clique em **OK**.

2.  Aguarde que a caixa de diálogo **A Executar Classificação** seja fechada e, em seguida, veja os resultados no relatório que é automaticamente apresentado. Deverá ver **1** no campo **Propriedades** e o número de ficheiros existentes na sua pasta. Utilize o Explorador de Ficheiros para confirmar e verificar as propriedades dos ficheiros na pasta escolhida. No separador **Classificação**, deverá ver **RMS** como um nome de propriedade e **Sim** para o respetivo **Valor**.

3.  Execute a tarefa de gestão de ficheiros:

    1.  Clique em **Tarefas de Gestão de Ficheiros** &gt; **Proteger os ficheiros com RMS** &gt; **Executar Ficheiro de Gestão de Tarefas Agora**

    2.  Clique em **Aguardar a conclusão da tarefa** e, em seguida, clique em **OK**.

4.  Aguarde que a caixa de diálogo **A Executar Tarefa de Gestão de Ficheiros** seja fechada e, em seguida, veja os resultados no relatório que é automaticamente apresentado. Deverá ver o número de ficheiros que estão na pasta selecionada no campo **Ficheiros**. Confirme que os ficheiros na sua pasta selecionada estão agora protegidos pelo Rights Management. Por exemplo, se a pasta que escolheu for C:\FileShare, escreva o seguinte comando numa sessão do Windows PowerShell e confirme que não existem ficheiros com um Estado de **desprotegido**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Algumas dicas para a resolução de problemas:
    > 
    > -   Se vir **0** no relatório, em vez do número de ficheiros na sua pasta, este resultado indica que o script não foi executado. Em primeiro lugar, verifique o próprio script ao carregá-lo no ISE do Windows PowerShell para validar os conteúdos do script e tente executá-lo para ver se são apresentados erros. Sem especificar argumentos, o script tenta estabelecer ligação e autenticar para o serviço Azure Rights Management.
    > 
    >     -   Se o script anunciar que não foi possível ligar ao serviço Azure Rights Management (Azure RMS), verifique os valores que este apresenta para a conta do principal do serviço que especificou no script. Para obter mais informações sobre como criar esta conta do principal do serviço, veja [Pré-requisito 3: para proteger ou desproteger ficheiros sem interação](client-admin-guide-powershell.md#prerequisite-3-to-protect-or-unprotect-files-without-user-interaction) no guia do administrador do cliente do Azure Information Protection.
    >     -   Se o script anunciar que pode ligar ao Azure RMS, em seguida verifique se pode encontrar o modelo especificado ao executar [Get-RMSTemplate](/powershell/azureinformationprotection/vlatest/get-rmstemplate) diretamente a partir do Windows PowerShell no servidor. Deverá ver o modelo que especificou devolvido nos resultados.
    > -   Se o script for automaticamente executado no ISE do Windows PowerShell sem erros, tente executá-lo da seguinte maneira a partir de uma sessão do PowerShell, especificando um nome de ficheiro a proteger e sem o parâmetro -OwnerEmail:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '<full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Se o script for executado com êxito nesta sessão do Windows PowerShell, verifique as suas entradas para **Executivo** e **Argumento** na ação de tarefa de gestão de ficheiros.  Se tiver especificado **-OwnerEmail [Source File Owner Email (E-mail de Proprietário do Ficheiro de Origem)]**, experimente remover este parâmetro.
    > 
    >         Se a tarefa de gestão de ficheiros funcionar com êxito sem **-OwnerEmail [Source File Owner Email (E-mail de Proprietário do Ficheiro de Origem)]**, verifique se os ficheiros não protegidos têm um utilizador de domínio listado como o proprietário do ficheiro, em vez de **SYSTEM**.  Para efetuar esta verificação, utilize o **segurança** separador Propriedades do ficheiro e, em seguida, clique em **avançadas**. O valor **Proprietário** é apresentado imediatamente a seguir ao **Nome** do ficheiro. Além disso, certifique-se de que o servidor de ficheiros está no mesmo domínio ou num domínio fidedigno para procurar um endereço de correio eletrónico do utilizador dos serviços de domínio do Active Directory.
    > -   Se vir o número correto de ficheiros no relatório, mas os ficheiros não estiverem protegidos, experimente proteger os ficheiros manualmente com o cmdlet [Protect-RMSFile](/powershell/azureinformationprotection/vlatest/protect-rmsfile), para ver se são apresentados erros.

Após confirmar que estas tarefas foram executadas com êxito, pode fechar o Gestor de Recursos de Ficheiros. Novos ficheiros são classificados automaticamente e protegidos quando executam as tarefas agendadas. 

## <a name="modifying-the-instructions-to-selectively-protect-files"></a>Modificar as instruções para proteger ficheiros de forma seletiva
Quando tiver implementado as instruções anteriores, em seguida, é fácil modificá-las para uma configuração mais complexa. Por exemplo, pode proteger ficheiros com o mesmo script, mas apenas para ficheiros que contenham informações pessoais, e talvez selecionar um modelo que possua direitos mais restritivos.

Para efetuar esta alteração, utilize uma das propriedades de classificação incorporadas (por exemplo, **informações de identificação pessoal**) ou criar uma nova propriedade. Em seguida, crie uma nova regra que utilize esta propriedade. Por exemplo, poderá selecionar o **Classificador de Conteúdos**, selecionar a propriedade **Informações Pessoais** com o valor **Elevado** e configurar o padrão de expressão ou cadeia que identifica o ficheiro a ser configurado para esta propriedade (tais como a cadeia "**Data de Nascimento**").

Agora, tudo o que precisa de fazer é criar uma nova tarefa de gestão de ficheiros que utilize o mesmo script, mas talvez com um modelo diferente, e configurar a condição da propriedade de classificação que acabou de configurar. Por exemplo, em vez da condição que configurámos anteriormente (propriedade **RMS**, **Igual**, **Sim**), selecione a propriedade **Informações Pessoais** com o valor **Operador** definido como **Igual** e o **Valor** **Elevado**.

## <a name="next-steps"></a>Próximos passos

Poderá estar a pensar: [qual é a diferença entre a FCI do Windows Server e a análise do Azure Information Protection?](../get-started/faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner) 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
