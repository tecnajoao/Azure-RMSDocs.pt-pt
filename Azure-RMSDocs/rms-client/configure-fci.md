---
title: Proteção do Azure RMS com o Windows Server FCI – AIP
description: Instruções para utilizar o cliente de Rights Management (RMS) com o cliente do Azure Information Protection para configurar o Gestor de recursos do servidor de ficheiros e a infraestrutura de classificação de ficheiros (FCI).
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/12/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: fa836d25fa779d53ada2448a4a9d01144e24e1e6
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56255500"
---
# <a name="rms-protection-with-windows-server-file-classification-infrastructure-fci"></a>Proteção RMS com Infraestrutura de Classificação de Ficheiros (FCI) do Windows Server

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012, Windows Server 2012 R2*

Utilize este artigo para obter instruções e um script para utilizar o cliente do Azure Information Protection e o PowerShell para configurar o Gestor de Recursos do Servidor de Ficheiros e a Infraestrutura de Classificação de Ficheiros (FCI).

Esta solução permite-lhe proteger automaticamente todos os ficheiros numa pasta num servidor de ficheiros com o Windows Server ou proteger automaticamente ficheiros que cumpram critérios específicos. Por exemplo, ficheiros que tenham sido classificados como contendo informações confidenciais. Esta solução liga-se diretamente ao serviço Azure Rights Management do Azure Information Protection para proteger os ficheiros, pelo que tem de ter este serviço implementado na sua organização.

> [!NOTE]
> Embora o Azure Information Protection inclua um [conector](../deploy-rms-connector.md) que suporta a Infraestrutura de Classificação de Ficheiros, essa solução só suporta a proteção nativa — por exemplo, ficheiros do Office.
> 
> Para suportar vários tipos de ficheiro com a infraestrutura de classificação de ficheiros do Windows Server, tem de utilizar o módulo **AzureInformationProtection** do PowerShell, conforme documentado neste artigo. Os cmdlets do Azure Information Protection, tal como o cliente do Azure Information Protection, suportam a proteção genérica, bem como a proteção nativa, o que significa que os tipos de ficheiro diferentes dos documentos do Office podem ser protegidos. Para obter mais informações, veja [Tipos de ficheiro suportados pelo cliente do Azure Information Protection](client-admin-guide-file-types.md) no guia do administrador do cliente do Azure Information Protection.

As instruções que se seguem aplicam-se ao Windows Server 2012 R2 ou Windows Server 2012. Se utilizar outras versões suportadas do Windows, poderá ter de adaptar alguns dos passos devido às diferenças entre a versão do seu sistema operativo e a descrita neste artigo.

## <a name="prerequisites-for-azure-rights-management-protection-with-windows-server-fci"></a>Pré-requisitos para a proteção do Azure Rights Management com a FCI do Windows Server
Pré-requisitos para estas instruções:

- Nos servidores de ficheiros em que executará o Gestor de Recursos de Ficheiros com a infraestrutura de classificação de ficheiros:
    
  - Instalou o Gestor de Recursos do Servidor de Ficheiros como um dos serviços de função para a função Serviços de Ficheiros.
    
  - Identificou uma pasta local que contém ficheiros que pretende proteger com a Gestão de Direitos. Por exemplo, C:\FileShare.
    
  - Instalou o módulo AzureInformationProtection do PowerShell e configurou os pré-requisitos deste módulo para ligar ao serviço Azure Rights Management.
    
    O módulo AzureInformationProtection do PowerShell é incluído com o cliente do Azure Information Protection. Para obter instruções de instalação, consulte [instalar o cliente do Azure Information Protection para utilizadores](client-admin-guide-install.md) no Guia do administrador do Azure Information Protection. Se for necessário, pode instalar apenas o módulo do PowerShell com o parâmetro `PowerShellOnly=true`.
    
    Os [pré-requisitos para utilizar este módulo do PowerShell](client-admin-guide-powershell.md#azure-information-protection-and-azure-rights-management-service) incluem a ativação do serviço Azure Rights Management, a criação de um principal de serviço e a edição do registo se o seu inquilino estiver fora da América do Norte. Antes de iniciar as instruções neste artigo, confirme se tem valores para **BposTenantId**, **AppPrincipalId** e **Chave simétrica**, conforme documentado nestes pré-requisitos. 
    
  - Se quiser alterar o nível predefinido da proteção (nativo ou genérico) para extensões de nome de ficheiro específicas, terá de editar o registo, conforme descrito na página [Alterar o nível de proteção predefinido dos ficheiros](client-admin-guide-file-types.md#changing-the-default-protection-level-of-files) no guia do administrador.
    
  - Tem uma ligação à Internet e que configurou as definições de computador, se elas são necessárias para um servidor proxy. Por exemplo: `netsh winhttp import proxy source=ie`
    
- Sincronizou as suas contas de utilizador do Active Directory no local com o Azure Active Directory ou o Office 365, incluindo os endereços de e-mail. Isto é necessário para todos os utilizadores que possam necessitar de aceder a ficheiros protegidos pela FCI e pelo serviço Azure Rights Management. Se não efetuar este passo (por exemplo, num ambiente de teste), os utilizadores poderão ficar bloqueados de aceder a estes ficheiros. Se precisar de mais informações sobre este requisito, veja [Preparar utilizadores e grupos para o Azure Information Protection](../prepare.md).
    
- Este cenário não suporta modelos departamentais, pelo que deve utilizar um modelo que não esteja configurado para um âmbito ou utilizar o [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet e os *EnableInLegacyApps* parâmetro.

## <a name="instructions-to-configure-file-server-resource-manager-fci-for-azure-rights-management-protection"></a>Instruções para configurar a FCI do Gestor de Recursos do Servidor de Ficheiros para a proteção do Azure Rights Management
Siga estas instruções para proteger automaticamente todos os ficheiros numa pasta, através de um script do PowerShell como uma tarefa personalizada. Efetue estes procedimentos pela seguinte ordem:

1. Guardar o script do PowerShell

2. Criar uma propriedade de classificação para a Gestão de Direitos (RMS)

3. Criar uma regra de classificação (Classificar para RMS)

4. Configurar a agenda de classificação

5. Criar uma tarefa de gestão de ficheiros personalizada (Proteger ficheiros com o RMS)

6. Testar a configuração ao executar manualmente a regra e a tarefa

No final destas instruções, todos os ficheiros na sua pasta selecionada serão classificados com a propriedade personalizada do RMS e estes ficheiros estarão assim protegidos pela Gestão de Direitos. Para uma configuração mais complexa que protege seletivamente alguns ficheiros e não outros, pode criar ou utilizar uma propriedade e regra de classificação diferente, com uma tarefa de gestão de ficheiros que protege apenas esses ficheiros.

Tenha em atenção que se fizer alterações ao modelo de Rights Management que utiliza para a FCI, a conta de computador que executa o script para proteger os ficheiros não recebem automaticamente o modelo atualizado. Para tal, no script, localize o comentado horizontalmente `Get-RMSTemplate -Force` de comandos e remover o `#` caractere de comentário. Quando é transferido o modelo atualizado (o script tem de executar, pelo menos, uma vez), pode comentar este comando adicional para que os modelos não são transferidos desnecessariamente cada vez. Se as alterações ao modelo forem suficientemente importantes para voltar a proteger os ficheiros no servidor de ficheiros, pode fazer isso interativamente ao executar o cmdlet Protect-RMSFile com uma conta que tenha os direitos de utilização de exportação ou controlo total para os ficheiros. Terá também de executar `Get-RMSTemplate -Force` se publicar um novo modelo que pretende utilizar para a FCI.

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

3.  Assine o script. Se não assinar o script (mais seguro), tem de configurar o Windows PowerShell nos servidores que o executam. Por exemplo, executar uma sessão do Windows PowerShell com o **executar como administrador** opção e escreva: **Set-ExecutionPolicy RemoteSigned**. No entanto, esta configuração permite executar todos os scripts não assinados quando estes estão armazenados neste servidor (menos seguro).

    Para obter mais informações sobre como assinar os scripts do Windows PowerShell, veja [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) na biblioteca de documentação do PowerShell.

4.  Guarde o ficheiro localmente em cada servidor de ficheiros que executa o Gestor de recursos de ficheiros com a infraestrutura de classificação de ficheiros. Por exemplo, guarde o ficheiro em **C:\RMS-Protection**. Se utilizar um caminho ou nome de pasta diferente, escolha um caminho e uma pasta que não incluam espaços. Proteja este ficheiro com permissões NTFS para que os utilizadores não autorizados não o possam modificar.

Agora está pronto para iniciar a configuração do Gestor de Recursos do Servidor de Ficheiros.

### <a name="create-a-classification-property-for-rights-management-rms"></a>Criar uma propriedade de classificação para a Gestão de Direitos (RMS)

-   No Gestor de Recursos do Servidor de Ficheiros, em Gestão de Classificação, crie uma nova propriedade local:

    -   **Nome**: Type **RMS**

    -   **Descrição**:   Tipo de **proteção do Rights Management**

    -   **Tipo de propriedade**: Selecione **Sim/não**

    -   **Valor**: Selecione **Sim**

Agora podemos criar uma regra de classificação que utiliza esta propriedade.

### <a name="create-a-classification-rule-classify-for-rms"></a>Criar uma regra de classificação (Classificar para RMS)

-   Crie uma nova regra de classificação:

    -   No separador **Geral**:

        -   **Nome**: Tipo de **classificar para RMS**

        -   **Ativado**: Mantenha a predefinição, o que é que esta caixa de verificação está selecionada.

        -   **Descrição**: Tipo **classificar todos os ficheiros nos &lt;nome da pasta&gt; pasta para o Rights Management**.

            Substitua *&lt;nome da pasta&gt;* pelo nome da pasta que escolheu. Por exemplo, **Classificar todos os ficheiros na pasta C:\FileShare para a Gestão de Direitos**

        -   **Âmbito**: Adicione a pasta escolhida. Por exemplo, **C:\FileShare**.

            Não selecione as caixas de verificação.

    -   Clique no separador **Classificação**:

    -   **Método de classificação**: Selecione **classificador de pastas**

    -   **Propriedade** nome: Selecione **RMS**

    -   Propriedade **valor**: Selecione **Sim**

Embora seja possível executar as regras de classificação manualmente, para operações em curso, pretende que esta regra sejam executados com base numa agenda, para que os novos ficheiros são classificados com a propriedade do RMS.

### <a name="configure-the-classification-schedule"></a>Configurar a agenda de classificação

-   No separador **Classificação Automática**:

    -   **Ativar agenda fixa**: Selecione esta caixa de verificação.

    -   Configure a agenda para todas as regras de classificação a executar, o que inclui a nossa nova regra para classificar ficheiros com a propriedade do RMS.

    -   **Permitir classificação contínua para novos ficheiros**: Selecione esta caixa de verificação para que os novos ficheiros são classificados.

    -   Opcional: Faça outras alterações que pretende, como configurar as opções de relatórios e notificações.

Agora que concluiu a configuração de classificação, está pronto para configurar uma tarefa de gestão para aplicar a proteção RMS aos ficheiros.

### <a name="create-a-custom-file-management-task-protect-files-with-rms"></a>Criar uma tarefa de gestão de ficheiros personalizada (Proteger ficheiros com o RMS)

-   Em **Tarefas de Gestão de Ficheiros**, crie uma nova tarefa de gestão de ficheiros:

    -   No separador **Geral**:

        -   **Nome da tarefa**: Tipo de **proteger ficheiros com RMS**

        -   Mantenha a caixa de verificação **Ativar** selecionada.

        -   **Descrição**: Tipo **proteger ficheiros numa &lt;nome da pasta&gt; com a gestão de direitos e um modelo ao utilizar um script do Windows PowerShell.**

            Substitua *&lt;nome da pasta&gt;* pelo nome da pasta que escolheu. Por exemplo, **Proteger ficheiros em C:\FileShare com a Gestão de Direitos e um modelo ao utilizar um script do Windows PowerShell**

        -   **Âmbito**: Selecione sua pasta selecionada. Por exemplo, **C:\FileShare**.

            Não selecione as caixas de verificação.

    -   No separador **Ação**:

        -   **Tipo de**: Selecione **personalizado**

        -   **Executável**: Especifique o seguinte:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Se o Windows não estiver na sua unidade C:, modifique este caminho ou navegue até este ficheiro.

        -   **Argument**: Especifique o seguinte, fornecendo os seus próprios valores para &lt;caminho&gt; e &lt;ID do modelo&gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail '[Source File Owner Email]'"
            ```
            Por exemplo, se tiver copiado o script para C:\RMS-Protection e o ID de modelo que identificou a partir dos pré-requisitos for e6ee2481-26b9-45e5-b34a-f744eacd53b0, especifique o seguinte:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail '[Source File Owner Email]'"`

            Neste comando, **[Source File Path]** e **[Source File Owner Email]** são ambas variáveis específicas da FCI, por isso, escreva-as exatamente tal como aparecem no comando anterior. A primeira variável é utilizada pela FCI para especificar automaticamente o ficheiro identificado na pasta e a segunda variável é para a FCI obtenha automaticamente o endereço de e-mail do proprietário mencionado do ficheiro identificado. Este comando é repetido para cada ficheiro na pasta, o que, no nosso exemplo, significa cada ficheiro que se encontre na pasta C:\FileShare e tenha o RMS como uma propriedade de classificação de ficheiros.

            > [!NOTE]
            > O valor e o parâmetro **-OwnerMail [Source File Owner Email (E-mail do Proprietário do Ficheiro de Origem)]** garantem que os direitos de proprietário de Gestão de Direitos do ficheiro são concedidos ao proprietário original do ficheiro após este ser protegido. Esta configuração garante que o proprietário do ficheiro original tem todos os direitos de gestão de direitos dos seus ficheiros. Quando os ficheiros são criados por um utilizador de domínio, o endereço de e-mail é obtido automaticamente a partir do Active Directory através do nome de conta de utilizador na propriedade Proprietário do ficheiro. Para fazer isto, o servidor de ficheiros tem de se encontrar no mesmo domínio ou domínio fidedigno que o utilizador.
            > 
            > Sempre que possível, atribua os proprietários originais aos documentos protegidos, para garantir que estes utilizadores continuam a ter controlo total sobre os ficheiros que criaram. No entanto, se utilizar a variável [Source File Owner Email] como no comando anterior e um ficheiro não tem um utilizador de domínio definido como o proprietário (por exemplo, uma conta local foi usada para criar o arquivo, para que o proprietário apresentado for SYSTEM), o script falhar.
            > 
            > Para ficheiros que não dispõem de um utilizador de domínio como proprietário, pode copiar e guardá-los como um utilizador de domínio, de modo a ser o proprietário apenas destes ficheiros. Em alternativa, se tiver as permissões, pode alterar manualmente o proprietário.  Ou, em alternativa, pode fornecer um endereço de e-mail específico (tal como o seu próprio ou um endereço de grupo para o departamento de TI) em vez da variável [Source File Owner Email], que significa que todos os ficheiros que proteger com este script utiliza este endereço de e-mail para definir a nova proprietário.

    -   **Execute o comando como**: Selecione **Sistema Local**

    -   No separador **Condição**:

        -   **Propriedade**: Selecione **RMS**

        -   **Operador**: Selecione **igual**

        -   **Valor**: Selecione **Sim**

    -   No separador **Agenda**:

        -   **Executar às**: Configure o horário da sua preferência.

            Reserve bastante tempo para que o script seja concluído. Embora esta solução proteja todos os ficheiros na pasta, o script é executado uma vez para cada ficheiro, de cada vez. Apesar de este processo ser mais demorado do que proteger todos os ficheiros ao mesmo tempo, o que é suportado pelo cliente do Azure Information Protection, esta configuração ficheiro-a-ficheiro para a FCI é mais eficiente. Por exemplo, os ficheiros protegidos podem ter diferentes proprietários (manter o proprietário original) quando utiliza a variável [Source File Owner Email] e esta ação ficheiro-a-ficheiro é necessária se posteriormente alterar a configuração para proteger ficheiros em vez de todos os de forma seletiva ficheiros numa pasta.

        -   **Executar continuamente em ficheiros novos**: Selecione esta caixa de verificação.

### <a name="test-the-configuration-by-manually-running-the-rule-and-task"></a>Testar a configuração ao executar manualmente a regra e a tarefa

1.  Executar a regra de classificação:

    1.  Clique em **Regras de Classificação** &gt; **Executar Classificação Com Todas as Regras Agora**

    2.  Clique em **Aguardar conclusão da classificação** e, em seguida, clique em **OK**.

2.  Aguarde que a caixa de diálogo **A Executar Classificação** seja fechada e, em seguida, veja os resultados no relatório que é automaticamente apresentado. Deverá ver **1** no campo **Propriedades** e o número de ficheiros existentes na sua pasta. Utilize o Explorador de Ficheiros para confirmar e verificar as propriedades dos ficheiros na pasta escolhida. No separador **Classificação**, deverá ver **RMS** como um nome de propriedade e **Sim** para o respetivo **Valor**.

3.  Execute a tarefa de gestão de ficheiros:

    1.  Clique em **Tarefas de Gestão de Ficheiros** &gt; **Proteger os ficheiros com RMS** &gt; **Executar Ficheiro de Gestão de Tarefas Agora**

    2.  Clique em **Aguardar a conclusão da tarefa** e, em seguida, clique em **OK**.

4.  Aguarde que a caixa de diálogo **A Executar Tarefa de Gestão de Ficheiros** seja fechada e, em seguida, veja os resultados no relatório que é automaticamente apresentado. Deverá ver o número de ficheiros que estão na pasta selecionada no campo **Ficheiros**. Confirme que os ficheiros na sua pasta selecionada estão agora protegidos pelo Rights Management. Por exemplo, se sua pasta selecionada for C:\FileShare, escreva o seguinte comando numa sessão do Windows PowerShell e confirme que não existem ficheiros com um estado **desprotegido**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Algumas dicas para a resolução de problemas:
    > 
    > -   Se vir **0** no relatório, em vez do número de ficheiros na sua pasta, este resultado indica que o script não foi executado. Em primeiro lugar, verifique o próprio script ao carregá-lo no ISE do Windows PowerShell para validar o conteúdo de script e tente executá-lo uma vez na mesma sessão do PowerShell, para ver se são apresentados erros. Sem especificar argumentos, o script tenta estabelecer ligação e autenticar para o serviço Azure Rights Management.
    > 
    >     -   Se o script anunciar que não foi possível ligar ao serviço Azure Rights Management (Azure RMS), verifique os valores que este apresenta para a conta do principal do serviço que especificou no script. Para obter mais informações sobre como criar esta conta do principal de serviço, consulte [pré-requisito 3: Para proteger ou desproteger ficheiros sem interação](client-admin-guide-powershell.md#prerequisite-3-to-protect-or-unprotect-files-without-user-interaction) no Guia do administrador de cliente do Azure Information Protection.
    >     -   Se o script anunciar que pode ligar ao Azure RMS, em seguida verifique se pode encontrar o modelo especificado ao executar [Get-RMSTemplate](/powershell/azureinformationprotection/vlatest/get-rmstemplate) diretamente a partir do Windows PowerShell no servidor. Deverá ver o modelo que especificou devolvido nos resultados.
    > -   Se o script for automaticamente executado no ISE do Windows PowerShell sem erros, tente executá-lo da seguinte maneira a partir de uma sessão do PowerShell, especificando um nome de ficheiro a proteger e sem o parâmetro -OwnerEmail:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '<full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Se o script for executado com êxito nesta sessão do Windows PowerShell, verifique as suas entradas para **Executivo** e **Argumento** na ação de tarefa de gestão de ficheiros.  Se tiver especificado **-OwnerEmail [Source File Owner Email (E-mail de Proprietário do Ficheiro de Origem)]**, experimente remover este parâmetro.
    > 
    >         Se a tarefa de gestão de ficheiros funcionar com êxito sem **-OwnerEmail [Source File Owner Email (E-mail de Proprietário do Ficheiro de Origem)]**, verifique se os ficheiros não protegidos têm um utilizador de domínio listado como o proprietário do ficheiro, em vez de **SYSTEM**.  Para tornar esta verificação, utilize o **Security** separador de propriedades do ficheiro e, em seguida, clique em **avançadas**. O valor **Proprietário** é apresentado imediatamente a seguir ao **Nome** do ficheiro. Além disso, certifique-se de que o servidor de ficheiros está no mesmo domínio ou num domínio fidedigno para procurar o endereço de e-mail do utilizador dos serviços de domínio do Active Directory.
    > -   Se vir o número correto de ficheiros no relatório, mas os ficheiros não estiverem protegidos, experimente proteger os ficheiros manualmente com o cmdlet [Protect-RMSFile](/powershell/azureinformationprotection/vlatest/protect-rmsfile), para ver se são apresentados erros.

Após confirmar que estas tarefas foram executadas com êxito, pode fechar o Gestor de Recursos de Ficheiros. Novos ficheiros são classificados e protegidos quando as tarefas agendadas são executadas automaticamente. 

## <a name="action-required-if-you-make-changes-to-the-rights-management-template"></a>Ação necessária se fizer alterações ao modelo de Rights Management

Se fizer alterações ao modelo de Rights Management que as referências de script, a conta de computador que executa o script para proteger os ficheiros não recebem automaticamente o modelo atualizado. No script, localize o comentado horizontalmente `Get-RMSTemplate -Force` na função RMSConnection do conjunto de comandos e remover o caractere de comentário no início da linha. Da próxima vez que o script é executado, o modelo atualizado é baixado. Para otimizar o desempenho, de modo a que os modelos não transferir desnecessariamente, pode, em seguida, comente esta linha novamente. 

Se as alterações ao modelo forem suficientemente importantes para voltar a proteger os ficheiros no servidor de ficheiros, pode fazer isso interativamente ao executar o cmdlet Protect-RMSFile com uma conta que tenha os direitos de utilização de exportação ou controlo total para os ficheiros. 

Também execute esta linha no script se publicar um novo modelo que pretende utilizar para a FCI e alterar o ID de modelo na linha de argumento para a tarefa de gestão de ficheiros personalizados.

## <a name="modifying-the-instructions-to-selectively-protect-files"></a>Modificar as instruções para proteger ficheiros de forma seletiva
Quando tiver implementado as instruções anteriores, em seguida, é fácil modificá-las para uma configuração mais complexa. Por exemplo, pode proteger ficheiros com o mesmo script, mas apenas para ficheiros que contenham informações pessoais, e talvez selecionar um modelo que possua direitos mais restritivos.

Para tornar essa modificação, utilize uma das propriedades de classificação incorporadas (por exemplo, **informações de identificação pessoal**) ou criar nova propriedade. Em seguida, crie uma nova regra que utilize esta propriedade. Por exemplo, poderá selecionar o **Classificador de Conteúdos**, selecionar a propriedade **Informações Pessoais** com o valor **Elevado** e configurar o padrão de expressão ou cadeia que identifica o ficheiro a ser configurado para esta propriedade (tais como a cadeia "**Data de Nascimento**").

Agora, tudo o que precisa de fazer é criar uma nova tarefa de gestão de ficheiros que utilize o mesmo script, mas talvez com um modelo diferente, e configurar a condição da propriedade de classificação que acabou de configurar. Por exemplo, em vez da condição que configurámos anteriormente (propriedade **RMS**, **Igual**, **Sim**), selecione a propriedade **Informações Pessoais** com o valor **Operador** definido como **Igual** e o **Valor** **Elevado**.

## <a name="next-steps"></a>Passos Seguintes

Deve estar pensando: [O que é a diferença entre a FCI do Windows Server e o scanner do Azure Information Protection?](../faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner) 

