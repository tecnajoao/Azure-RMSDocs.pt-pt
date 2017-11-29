---
title: "Implementar a análise do Azure Information Protection"
description: "Instruções para instalar, configurar e executar o Verificador de Azure Information Protection para detetar, classificar e proteger os ficheiros nos arquivos de dados."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 20d29079-2fc2-4376-b5dc-380597f65e8a
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 3bdaf11d6d20e0f162ba27fd0844fd6f43a333be
ms.sourcegitcommit: 230eac207dc2276246db7997804644c9930051a6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>O scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente a implementar

>*Aplica-se a: Azure Information Protection, o Windows Server 2016, o Windows Server 2012 R2*

> [!NOTE]
> Esta funcionalidade está atualmente em pré-visualização e está sujeito a alterações.

Utilize estas informações para saber mais sobre a análise do Azure Information Protection e, em seguida, como instalar, configurar e executá-lo com êxito. 

Esta análise é executada como um serviço no Windows Server e permite-lhe Deteta, classifica e proteger ficheiros nos arquivos de dados seguintes:

- Pastas locais no computador do servidor do Windows que executa o verificador.

- Utilize caminhos UNC para partilhas de rede que utilizam o protocolo Common Internet File System (CIFS).

- Sites e bibliotecas para SharePoint Server 2016 e o SharePoint Server 2013.

## <a name="overview-of-the-azure-information-protection-scanner"></a>Descrição geral do scanner Azure Information Protection

Quando tiver configurado o [política do Azure Information Protection](configure-policy.md) para etiquetas que se aplicam a classificação automática, ficheiros de que este scanner Deteta, em seguida, podem ser etiqueta. As etiquetas aplicam classificação e, opcionalmente, aplicarem a proteção ou remova a proteção:

![Descrição geral de análise do Azure Information Protection](../media/infoprotect-scanner.png)

O scanner pode inspecionar ficheiros que o Windows pode indexar, utilizando os iFilters que estão instalados no computador. Em seguida, para determinar se os ficheiros têm de etiquetagem, scanner utiliza o Office 365 incorporada perda prevenção (DLP) sensibilidade informações tipos de dados e deteção de padrão ou padrões de regex do Office 365. Uma vez scanner utiliza o cliente Azure Information Protection, pode classificar e proteger o mesmo [tipos de ficheiros](../rms-client/client-admin-guide-file-types.md).

Pode executar o verificador no modo de deteção apenas, onde utiliza os relatórios para verificar o que acontece se os ficheiros foram etiqueta. Em alternativa, pode executar o verificador para aplicar automaticamente as etiquetas.

Tenha em atenção que não Deteta scanner e a etiqueta em tempo real. Esta pesquisa sistematicamente através de ficheiros nos arquivos de dados que especificar e pode configurar este ciclo para executar uma vez ou repetidamente.

## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Pré-requisitos para a análise do Azure Information Protection
Antes de instalar o scanner do Azure Information Protection, certifique-se de que os seguintes requisitos são cumpridos.

|Requisito|Mais informações|
|---------------|--------------------|
|Computador Windows Server para executar o serviço de análise:<br /><br />-4 processos<br /><br />-4 GB de RAM|Windows Server 2016 ou o Windows Server 2012 R2. <br /><br />Nota: Para fins de teste ou avaliação num ambiente de não produção, pode utilizar um sistema de operativo de cliente Windows é [suportadas pelo cliente Azure Information Protection](../get-started/requirements.md#client-devices).<br /><br />Este computador pode ser um computador físico ou virtual que tenha uma ligação de rede rápida e fiável para os arquivos de dados ser analisados. <br /><br />Certifique-se de que este computador tem o [conectividade à Internet](../get-started/requirements.md#firewalls-and-network-infrastructure) que necessita para o Azure Information Protection. Em alternativa, tem de o configurar como um [computadores desligados](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers). |
|SQL Server para armazenar a configuração de scanner:<br /><br />-Instância local ou remota|SQL Server 2012 é a versão mínima para as seguintes edições:<br /><br />-SQL Server para empresas<br /><br />-SQL Server Standard<br /><br />-SQL Server Express|
|Conta de serviço para executar o serviço de análise|Esta conta tem de ser uma conta do Active Directory que está sincronizada com o Azure AD, com os seguintes requisitos adicionais:<br /><br />- **Iniciar sessão localmente** à direita. Este direito é necessário para a instalação e configuração do scanner, mas não para a operação. Tem de conceder este direito para a conta de serviço, mas pode remover este direito depois de confirmar que o verificador pode detetar, classificar e proteger os ficheiros.<br /><br />- **Inicie sessão como um serviço** à direita. Este direito é concedido automaticamente para a conta de serviço durante a instalação do scanner e este direito é necessário para a instalação, configuração e operação do scanner. <br /><br />-Permissões para os repositórios de dados: tem de conceder **leitura** e **escrever** permissões para analisar os ficheiros e, em seguida, aplicar classificação e a proteção para os ficheiros que cumprem as condições no Política de proteção de informações do Azure. Para executar o verificador no modo de deteção apenas, **leitura** permissão é suficiente.<br /><br />-Para etiquetas que proteja novamente ou remova a proteção: para se certificar de que o verificador tem sempre acesso aos ficheiros protegidos, tornar esta conta um [Superutilizador](configure-super-users.md) para o Azure Rights Management service e certifique-se de que a funcionalidade de Superutilizador é ativada . Para obter mais informações sobre os requisitos de conta para aplicar a proteção, consulte [preparar os utilizadores e grupos do Azure Information Protection](../plan-design/prepare.md).|
|O cliente Azure Information Protection está instalado no computador do servidor do Windows|Atualmente, a análise do Azure Information Protection requer a versão de pré-visualização do cliente Azure Information Protection.<br /><br />Se preferencial, pode instalar o cliente com apenas o módulo do PowerShell (AzureInformationProtection) que é utilizado para instalar e Configurar scanner.<br /><br />Para obter instruções de instalação de cliente, consulte o [Guia do administrador](../rms-client/client-admin-guide.md).|
|Configurado etiquetas que se aplicam a classificação automática e, opcionalmente, a proteção|Para obter mais informações sobre como configurar as condições, consulte [como configurar condições para classificação automática e recomendada para o Azure Information Protection](configure-policy-classification.md).<br /><br />Para obter mais informações sobre como configurar as etiquetas para aplicar proteção aos ficheiros, consulte [como configurar uma etiqueta para a proteção Rights Management](configure-policy-protection.md).<br /><br />Estas etiquetas podem ser política global, ou um ou mais [âmbito políticas](configure-policy-scope.md).|


## <a name="install-the-azure-information-protection-scanner"></a>Instalar o scanner do Azure Information Protection

1. Utilizando a conta de serviço que criou para executar o verificador, inicie sessão no computador do servidor do Windows que irão executar o verificador.

2. Abra uma sessão do Windows PowerShell com o **executar como administrador** opção.

3. Execute o [instalação AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) cmdlet, especificar a instância do SQL Server em que pretende criar uma base de dados para a análise do Azure Information Protection. Quando lhe for pedido, forneça as credenciais da conta de serviço de análise (\<nome de domínio \ utilizador >) e palavra-passe: 
    
    ```
    Install-AIPScanner -SqlServerInstance <database name>
    ```
    
    Exemplos:
        
    - Para uma instância predefinida:`Install-AIPScanner -SqlServerInstance SQLSERVER1`
    
    - Para uma instância nomeada:`Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER`
    
    - Para SQL Server Express:`Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS`

4. Certifique-se de que o serviço está agora instalado utilizando **ferramentas administrativas** > **serviços**. 
    
    O serviço instalado é denominado **Scanner de proteção de informações do Azure** e está configurado para ser executado utilizando a conta de serviço de análise que criou.

Agora que instalou scanner, terá de obter um Azure AD token para a conta de serviço de análise autenticar para que possam executar em modo automático. 

## <a name="get-an-azure-ad-token-for-the-scanner-service-account-to-authenticate-to-the-azure-information-protection-service"></a>Obtenha o token para a conta de serviço para se autenticar o serviço do Azure Information Protection scanner de um Azure AD

1. No mesmo computador do Windows Server ou do ambiente de trabalho, inicie sessão no portal do Azure para criar duas aplicações do Azure AD que são necessários para especificar um token de acesso para a autenticação. Após um inicial interativa início de sessão, este token permite scanner executar de forma não interativa.
    
    Para criar estas aplicações, siga as instruções em [como ficheiros de etiqueta forma não interativa do Azure Information Protection](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) do guia de administração.

2. A partir do computador do servidor do Windows, ainda com sessão iniciado com a conta de serviço de análise, execute [conjunto AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), especificar os valores que copiou no passo anterior:
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application>  -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application >
    ```

3. Quando lhe for pedido, especifique a palavra-passe para as credenciais da conta de serviço para o Azure AD e, em seguida, clique em **aceitar**.

Scanner tem agora um token para autenticar com o Azure AD, que é válido durante um ano, dois anos, ou nunca expira, de acordo com a configuração do **Web app /API** no Azure AD. Quando o token expira, terá de repetir os passos 1 a 3.

Agora, está pronto para especificar os arquivos de dados para análise. 

## <a name="specify-data-stores-for-the-azure-information-protection-scanner"></a>Especifique os arquivos de dados para a análise do Azure Information Protection

Utilize o [adicionar AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository) cmdlet para especificar os dados armazena ser analisados por scanner Azure Information Protection. Pode especificar os URLs de servidor do SharePoint, caminhos UNC e pastas locais para sites do SharePoint e bibliotecas. 

Versões suportadas do SharePoint: SharePoint Server 2016 e o SharePoint Server 2013.

1. No mesmo computador do Windows Server, na sessão do PowerShell, adicione que os primeiros dados armazenam executando o seguinte comando:
    
        Add-AIPScannerRepository -Path <path>
    
    Por exemplo: `Add-AIPScannerRepository -Path \\NAS\Documents`
    
    Para obter outros exemplos, consulte o [ajuda online](/powershell/module/azureinformationprotection/Add-AIPScannerRepository#examples) para este cmdlet.

2. Repita este comando para todos os dados armazena que pretende analisar. Se precisar de remover um arquivo de dados que adicionou, utilize o [remover AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository) cmdlet.

3. Confirme que especificou todos os arquivos de dados corretamente, executando o [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository) cmdlet:
    
        Get-AIPScannerRepository

Com a configuração predefinida da análise, agora, está pronto para executar a sua primeira análise no modo de deteção.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-azure-information-protection-scanner"></a>Executar um ciclo de deteção e ver relatórios para a análise do Azure Information Protection

1. Utilizar **ferramentas administrativas** > **serviços**, iniciar a **Scanner de proteção de informações do Azure** serviço.

2. Aguarde scanner concluir o respetivo ciclo. Quando o verificador tem pesquisado através de todos os ficheiros nos arquivos de dados que especificou, interrompe o serviço. Pode utilizar o Windows local **aplicações e serviços** registo de eventos, **Azure Information Protection**, para confirmar se o serviço está parado. Procure o ID de evento informativo **911**.

3. Reveja os relatórios que são armazenados em %*localappdata*%\Microsoft\MSIP\Scanner\Reports e que têm um formato de ficheiro. csv. A configuração predefinida do scanner, apenas os ficheiros que cumprem as condições para classificação automática estão incluídos nestes relatórios.
    
    Se os resultados não estão como esperado, poderá ter de otimizar as condições que especificou na política de Azure Information Protection. Se for esse o caso, repita os passos 1 a 3 até estar pronto para alterar a configuração para aplicar a classificação e, opcionalmente, a proteção. Sempre que repita estes passos, primeiro execute o seguinte comando do PowerShell no computador do servidor do Windows:
    
        Set-AIPScannerConfiguration -Schedule OneTime

Quando estiver pronto para etiquetar automaticamente os ficheiros que Deteta scanner, avance para o procedimento seguinte. 

## <a name="configure-the-azure-information-protection-scanner-to-apply-classification-and-protection-to-discovered-files"></a>Configurar o scanner do Azure Information Protection para aplicar a classificação e a proteção aos ficheiros detetados

Na sua predefinição, a análise é executada uma hora e no modo só de relatórios. Para alterar estas definições, execute o [conjunto AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet.

1. No computador Windows Server, na sessão do PowerShell, execute o seguinte comando:
    
        Set-AIPScannerConfiguration -ScanMode Enforce -Schedule Continuous
    
    Existem outras definições de configuração que queira alterar. Por exemplo, se os atributos de ficheiro são alterados e o que é registado nos relatórios. Além disso, se a política do Azure Information Protection inclui a definição que necessita de uma mensagem de justificação ao reduzir o nível de classificação ou remova a proteção, especifique essa mensagem utilizando este cmdlet. Utilize o [ajuda online](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration#parameters) para obter mais informações sobre cada definição de configuração. 

2. Utilizar **ferramentas administrativas** > **serviços**, reinicie o **Scanner de proteção de informações do Azure** serviço.

3. Como anteriormente, monitorize o registo de eventos e os relatórios para ver os ficheiros que foram etiqueta, que classificação foi aplicada e se foi aplicada proteção.

Porque configurámos o agendamento para ser executada continuamente, quando a analista trabalhou a forma através de todos os ficheiros, inicia um ciclo de novo para que os ficheiros de novos e alterados são detetados.

## <a name="when-files-are-rescanned-by-the-azure-information-protection-scanner"></a>Quando os ficheiros estão a ser reanalisados por scanner Azure Information Protection

O ciclo de análise primeiro, scanner inspeciona todos os ficheiros nos arquivos de dados configurados e, em seguida, para análises subsequentes, ficheiros novos ou modificados apenas serão inspecionados. 

Pode forçar scanner inspecionar todos os ficheiros novamente executando [conjunto AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) com o `-Type` parâmetro definido como **completa**. Esta configuração é útil quando pretender que os relatórios para incluir todos os ficheiros e é normalmente utilizado quando a análise é executada no modo de deteção. Quando uma análise completa estiver concluída, o tipo de análise altera automaticamente a incremental para que para análises subsequentes, são analisados ficheiros apenas novos ou modificados.

Além disso, todos os ficheiros serão inspecionados quando scanner transfere uma política do Azure Information Protection com condições novas ou alteradas. O scanner atualiza a política de cada hora e quando inicia o serviço.

## <a name="optimizing-the-performance-of-the-azure-information-protection-scanner"></a>Otimizar o desempenho do scanner Azure Information Protection

Para maximizar o desempenho de scanner:

- **Ter uma alta velocidade e a ligação de rede fiável entre o computador de scanner e o arquivo de dados digitalizados**
    
    Por exemplo, coloque o computador de scanner no mesma LAN ou (preferencial) no mesmo segmento de rede, como o arquivo de dados digitalizados.
    
    A qualidade da ligação de rede afeta o desempenho de scanner porque para inspecionar os ficheiros, scanner transfere o conteúdo dos ficheiros para o computador que executa o serviço de análise. Quando reduzir (ou eliminar) o número de saltos de rede que tem de viajam estes dados, também reduzir a carga na sua rede. 

- **Certifique-se que o computador de scanner tem recursos do processador disponíveis**
    
    A inspecionar os conteúdos do ficheiro para uma correspondência com as condições configuradas e encriptar e desencriptar ficheiros são ações de processador intensivas. Monitorizar típicos ciclos de análise para os arquivos de dados especificado identificar se uma falta de recursos do processador é afetar negativamente o desempenho de análise.
    
- **Não analisarão a pastas locais no computador que executa o serviço de análise**
    
    Se tiver pastas para análise num servidor Windows, instale scanner num computador diferente e configurar essas pastas como partilhas de análise de rede. Separar as duas funções que alojem ficheiros e análise de ficheiros significa que os recursos informáticos para estes serviços não competir com outro.

Outros fatores que afetam o desempenho de scanner:

- A carga atual e os tempos de resposta de arquivos de dados que contêm os ficheiros para analisar

- Indica se o verificador é executado no modo de deteção ou impor modo
    
    Modo de deteção, normalmente, tem uma maior impor a taxa de análise que impor modo porque a deteção necessita de um único ficheiro ler ação, enquanto que requer o modo de leitura e escrita ações.

- Alterar as condições em que o Azure Information Protection
    
    O ciclo de análise primeiro quando scanner tem Inspecione cada ficheiro obviamente irá demorar mais que ciclos de análise subsequentes que, por predefinição, inspecionar ficheiros apenas novos e alterados. No entanto, se alterar as condições de política do Azure Information Protection, todos os ficheiros são analisados novamente, conforme descrito no [anterior a secção](#when-files-are-rescanned-by-the-azure-information-protection-scanner).

- O nível de registo que escolheu
    
    Pode escolher entre **depurar**, **informações**, **erro** e **desativar** para os relatórios de análise. **Desativar** resulta numa melhor desempenho; **Depurar** consideravelmente atrasar scanner e deve ser utilizado apenas para resolução de problemas. Para obter mais informações, consulte o *ReportLevel* parâmetro para o [conjunto AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet.

- Próprios ficheiros:
    
    - Ficheiros do Office são mais rapidamente digitalizados que ficheiros PDF.
    
    - Ficheiros não protegidos são mais rápidos de verificar que os ficheiros protegidos.
    
    - Ficheiros grandes obviamente demorar mais tempo a análise de ficheiros pequenos.

## <a name="list-of-cmdlets-for-the-azure-information-protection-scanner"></a>Lista de cmdlets para a análise do Azure Information Protection 

Outros cmdlets para scanner permitem-lhe alterar a conta de serviço e a base de dados para scanner, obter as definições atuais scanner e desinstale o serviço de análise. O scanner utiliza os seguintes cmdlets:

- [AIPScannerRepository adicionar](/powershell/module/azureinformationprotection/Add-AIPScannerRepository)

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository)

- [Instalação AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Remover AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository)

- [Conjunto AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Conjunto AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [AIPScanner desinstalar](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)


## <a name="event-log-ids-and-descriptions"></a>IDs e descrições do registo de eventos

Utilize as secções seguintes para identificar os IDs de eventos possíveis e as descrições de scanner. Estes eventos são registados no servidor que executa o serviço de análise, nas janelas **aplicações e serviços** registo de eventos, **Azure Information Protection**.

-----

Informações **910**

**Iniciar o ciclo de análise.**

Este evento é registado quando o serviço de análise é iniciado e começa a analisar ficheiros de repositórios de dados que especificou.

----

Informações **911**

**Ciclo de análise foi concluída.**

Este evento é registado quando scanner concluiu a respetiva única análise, uma vez que o servidor foi iniciado ou scanner foi concluído um ciclo numa base contínua.

----

Informações **913**

**Scanner está parada porque scanner está definida para nunca.**

Este evento é registado quando scanner está configurado para ser executada uma vez em vez de continuamente, e o serviço de análise do Azure Information Protection tiver sido manualmente reiniciado desde que o computador foi iniciado.  

Analise os ficheiros novamente, tem de definir a agenda **OneTime** ou **Continuous**e, em seguida, reinicie manualmente o serviço. Para alterar a agenda, utilize o [conjunto AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet e os **agenda** parâmetro.

----

Erro **912**

**Ocorreu um erro desconhecido.**

Obter mais informações, são registadas no relatório de detalhado que esteja armazenado em % localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_YYYY_MM_DD_HH_MM.csv.

Contacte [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support) se este evento continua a ter sessão iniciada. 

----

Erro **914**

**Serviço automaticamente foi parado devido a configuração danificado: ficheiro de política está em falta ou danificado.**

Este evento é registado quando o cliente Azure Information Protection não tem um ficheiro de política válido para a análise executar.

A política do Azure Information Protection é armazenada na %localappdata%\Microsoft\MSIP e tem de ser configurado com etiquetas com condições para aplicar a classificação automática. Em alternativa, a política tem de ser configurada para uma etiqueta predefinida.

Certifique-se de que as firewalls não estão a bloquear a conectividade à Internet necessária. Para obter mais informações, consulte o [infraestrutura de rede e Firewalls](../get-started/requirements.md#firewalls-and-network-infrastructure) requisitos do Azure Information Protection. Se a conectividade à Internet não for possível, siga as instruções para suportar [desligado computadores](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers).


## <a name="next-steps"></a>Próximos passos

Poderá estar a pensar: [qual é a diferença entre a FCI do Windows Server e a análise do Azure Information Protection?](../get-started/faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

Também pode utilizar o PowerShell para classificar e proteger ficheiros do seu computador de ambiente de trabalho de forma interativa. Para obter mais informações acerca desta e de outros cenários que utilizam o PowerShell, consulte [utilizando o PowerShell com o cliente Azure Information Protection](../rms-client/client-admin-guide-powershell.md).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]