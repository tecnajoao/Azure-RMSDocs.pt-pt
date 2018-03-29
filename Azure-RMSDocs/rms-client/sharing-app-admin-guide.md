---
title: Guia do administrador da aplicação de partilha RMS – AIP
description: Instruções e informações para administradores numa rede empresarial responsáveis por implementar a aplicação de partilha Microsoft Rights Management para Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/27/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e1f3520a74b3ae57984e635ca68ba429dd6ad131
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="rights-management-sharing-application-administrator-guide"></a>Guia do administrador da aplicação de partilha Rights Management

>*Aplica-se a: serviços de gestão de direitos do Active Directory [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 com SP1, Windows 8, Windows 8.1*

> [!IMPORTANT]
> **Notificação de fim do suporte**: a aplicação de partilha Rights Management para Windows está a ser substituída pelo [cliente do Azure Information Protection](aip-client.md). Suporte para esta aplicação anterior irá parar 31 de Janeiro de 2019. 

Utilize as seguintes informações se for o responsável pela aplicação de partilha Microsoft Rights Management numa rede empresarial ou se quiser obter mais informações técnicas além das que se encontram no [Guia do utilizador da aplicação de partilha Rights Management](sharing-app-user-guide.md) ou nas [FAQ sobre a Aplicação de Partilha Microsoft Rights Management do Windows](http://go.microsoft.com/fwlink/?LinkId=303971).

A aplicação de partilha RMS funciona melhor com o Azure Information Protection, porque esta configuração de implementação suporta o envio de anexos protegidos para utilizadores de outra organização e opções como notificações por e-mail e o controlo de documentos com revogação. No entanto, a aplicação também funciona com a versão no local, o AD RMS, embora com algumas limitações. Para ver uma comparação detalhada das funcionalidades suportadas pelo Azure Information Protection e pelo AD RMS, consulte [Comparar o Azure Information Protection e o AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). Se tiver o AD RMS e quiser migrar para o Azure Information Protection, consulte [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

Para obter uma descrição geral técnica da aplicação Rights Management, informações sobre a proteção nativa e genérica, e os tipos de ficheiro suportados, as extensões de nome de ficheiro e como pode alterar o nível de proteção predefinido, consulte [Descrição geral técnica e detalhes de proteção da aplicação de partilha Rights Management](sharing-app-admin-guide-technical.md). 

## <a name="automatic-deployment-for-the-microsoft-rights-management-sharing-application"></a>Implementação automática da aplicação de partilha Microsoft Rights Management
A versão para Windows da aplicação de partilha RMS suporta uma instalação com script, o que a torna adequada para implementações empresariais.

Os únicos pré-requisitos de instalação são que os computadores consigam executar pelo menos o Windows 7 Service Pack 1 ou superior e que esteja instalada a versão 4.0 ou superior do Microsoft Framework. Se precisar de instalar o Microsoft .NET Framework 4.0, pode [transferi-lo no Centro de Transferências da Microsoft](http://www.microsoft.com/download/details.aspx?id=17718).

### <a name="to-download-the-rms-sharing-application-for-automatic-deployment"></a>Para transferir a aplicação de partilha RMS para implementações automáticas

1.  Aceda à página da [aplicação de partilha Microsoft Rights Management para Windows](http://www.microsoft.com/download/details.aspx?id=40857) no Centro de Transferências da Microsoft e clique em **Transferir**.

2.  Selecione e transfira os ficheiros de que precisa. Existem dois pacotes de instalação de clientes: um para o Windows de 64 bits (Microsoft Rights Management sharing application x64.zip) e outro para o Windows de 32 bits (Microsoft Rights Management sharing application x86.zip).

3.  Pode extrair os ficheiros dos pacotes de instalação comprimidos ao fazer duplo clique sobre os mesmos, por exemplo. Em seguida, copie os ficheiros extraídos para uma localização na rede à qual os computadores cliente possam aceder.

Os pacotes de configuração para a aplicação de partilha RMS suportam diferentes cenários de implementação e incluem o seguinte:

|Descrição|Cenário de implementação|
|---------------|-----------------------|
|Assistente de Início de Sessão Online da Microsoft|Office 2010 e Azure Information Protection<br /><br />Office 2013 e Azure Information Protection se não tiver instalado a [atualização do Office 2013 de 9 de junho de 2015](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Correção para o Office (KB 2596501)|Office 2010 e Azure Information Protection<br /><br />Office 2010 e Active Directory RMS|
|Correção para permitir que o AD RMS Client 1.0 funcione com o Azure Information Protection (KB 2843630)|Office 2010 e Azure Information Protection<br /><br />Office 2010 e Active Directory RMS|
|Cliente de AD RMS e a aplicação de partilha RMS|Office 2016 ou Office 2013 e Azure Information Protection ou Active Directory RMS<br /><br />Office 2010 e Azure Information Protection<br /><br />Office 2010 e Active Directory RMS<br /><br />Apenas a aplicação de partilha RMS e o suplemento do Office|
|Suplemento do Office para o friso|Office 2016 ou Office 2013 e Azure Information Protection ou Active Directory RMS<br /><br />Office 2010 e Azure Information Protection<br /><br />Office 2010 e Active Directory RMS<br /><br />Apenas a aplicação de partilha RMS e o suplemento do Office|
|Ferramenta de preparação do Azure Active Directory Rights Management|Office 2010 e Azure Information Protection|
Utilize os seguintes procedimentos para identificar os comandos necessários para implementar a aplicação de partilha RMS nestes cenários de implementação:

-   **Office 2016 ou Office 2013 e Azure Information Protection ou Active Directory RMS**

    Os seus utilizadores têm o Office 2016 ou 2013, a sua organização utiliza o Azure Information Protection ou o Active Directory RMS e os utilizadores colaboram com outras organizações que utilizam o Azure Information Protection ou o Active Directory RMS.

-   **Office 2010 e Azure Information Protection**

    Os seus utilizadores têm o Office 2010, a sua organização utiliza o Azure Information Protection e os utilizadores colaboram com outras organizações que utilizam o Azure Information Protection ou o Active Directory RMS.

-   **Office 2010 e Active Directory RMS**

    Os seus utilizadores têm o Office 2010, a sua organização utiliza o AD RMS e os utilizadores colaboram com outras organizações que utilizam o Azure Information Protection.

-   **Apenas a aplicação de partilha RMS e o suplemento do Office**

    Os seus utilizadores têm o Office 2016, o Office 2013 ou o Office 2010, a sua organização utiliza o AD RMS e os utilizadores não precisam de colaborar com outras organizações que utilizam o Azure Information Protection. Esta instalação permite-lhe instalar apenas a aplicação de partilha e o suplemento do Office.

> [!NOTE]
> Nestes cenários, se a sua organização estiver a executar o AD RMS, os seus utilizadores podem receber conteúdos protegidos de outras organizações que utilizam o Azure Information Protection, mas não podem enviar conteúdos protegidos para outros utilizadores de uma organização que utilize o Azure Information Protection. No entanto, se a sua organização estiver a executar o Azure Information Protection, os seus utilizadores podem enviar e receber conteúdos protegidos de outras organizações.

Para concluir a instalação em cada procedimento, é necessário reiniciar o computador. Pode fazer um reinício automático através de um comando como o **shutdown /i**.

### <a name="to-deploy-the-rms-sharing-application-for-office-2016-or-office-2013-and-azure-information-protection-or-active-directory-rms"></a>Para implementar a aplicação de partilha RMS para o Office 2016 ou o Office 2013 e o Azure Information Protection ou Active Directory RMS

-   Nos computadores em que pretende instalar a aplicação de partilha RMS e os componentes relacionados, execute o seguinte comando com privilégios elevados:

    ```
    setup.exe /s
    ```

Para confirmar o êxito da operação, consulte a secção [Confirmar o êxito da instalação](#verifying-installation-success) neste artigo.

### <a name="to-deploy-the-rms-sharing-application-for-office-2010-and-azure-information-protection"></a>Para implementar a aplicação de partilha RMS para o Office 2010 e o Azure Information Protection

1.  Tem de ser o administrador global do seu inquilino do Office 365 ou do Azure Active Directory para obter o URL do serviço de certificação da sua organização ao executar a ferramenta de preparação do Azure Active Directory Rights Management. Só precisa de executar esta ferramenta uma única vez num computador. O URL do serviço de certificação será utilizado quando instalar a aplicação de partilha RMS em cada computador:

    1.  Inicie sessão num computador com uma conta de administrador local.

    2.  Nesse computador, [transfira e instale o Assistente de Início de Sessão Online da Microsoft](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Execute o seguinte comando para apresentar no ecrã o URL do serviço de certificação, que poderá copiar e guardar para o próximo passo:

        -   Para o Windows 8.1 e o Windows 8 de 64 bits:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Para o Windows 8.1 e o Windows 8 de 32 bits:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Para o Windows 7 de 64 bits:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Este comando poderá pedir-lhe para introduzir as suas credenciais do Azure. Se o computador não estiver associado a um domínio, o pedido será apresentado. Se o computador estiver associado a um domínio, a ferramenta poderá utilizar credenciais em cache.

2.  Nos computadores em que pretende instalar a aplicação de partilha RMS, execute o seguinte comando uma vez com privilégios elevados:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Nos computadores em que pretende instalar a aplicação de partilha RMS, cada utilizador que utilizar o computador deve executar o seguinte comando (não são necessários privilégios elevados). Existem várias formas de realizar esta operação. Pode pedir aos utilizadores para executarem o comando (por exemplo, através de uma ligação numa mensagem de e-mail ou de uma ligação no portal de suporte técnico) ou pode adicioná-lo ao script de início de sessão dos mesmos:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Para confirmar o êxito da operação, consulte a secção [Confirmar o êxito da instalação](#verifying-installation-success) neste artigo.

### <a name="to-deploy-the-rms-sharing-application-for-office-2010-and-active-directory-rms"></a>Para implementar a aplicação de partilha RMS para o Office 2010 e o Active Directory RMS

1.  Nos computadores em que pretende instalar a aplicação de partilha RMS, execute o seguinte comando com privilégios elevados:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Nos computadores em que pretende instalar a aplicação de partilha RMS, os utilizadores têm de executar os seguintes comandos (não são necessários privilégios elevados). Existem várias formas de realizar esta operação. Pode pedir aos utilizadores para executarem os comandos (por exemplo, através de uma ligação numa mensagem de e-mail ou de uma ligação no portal de suporte técnico) ou pode adicioná-lo ao script de início de sessão dos mesmos:

    -   Para o Windows 10, Windows 8.1 e Windows 8 de 64 bits:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Para o Windows 10, Windows 8.1 e Windows 8 de 32 bits:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Para o Windows 7 de 64 bits:

            pushd x64\win7
            aadrmpep.exe /configureO2010
            popd

    -   Para o Windows 7 de 32 bits:

            pushd x86\win7
            aadrmpep.exe /configureO2010
            popd


Para confirmar o êxito da operação, consulte a secção [Confirmar o êxito da instalação](#verifying-installation-success) neste artigo.

### <a name="to-install-the-rms-sharing-application-and-office-add-in-only"></a>Para instalar apenas a aplicação de partilha RMS e o suplemento do Office

1.  Instale o Cliente do AD RMS e a aplicação de partilha RMS através do seguinte comando, especificando uma pasta existente para criar o ficheiro de registo:

    -   Para o Windows de 64 bits:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Para o Windows de 32 bits:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`
    
    Se este comando não conseguir executar com êxito, não visualizará quaisquer mensagens de erro porque o **lightweightserver /quiet** parâmetro. Para ajudar a apurar o motivo pelo qual a instalação falhou, volte a executar o comando sem /quiet para ver as mensagens de erro.

2.  Instale o suplemento do Office através dos seguintes comandos, especificando uma pasta existente para criar o ficheiro de registo:

    -   Para a versão de 64 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Para a versão de 32 bits do Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Por exemplo: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`
    
    Se este comando não conseguir executar com êxito, não visualizará quaisquer mensagens de erro porque o **lightweightserver /quiet** parâmetro. Para ajudar a apurar o motivo pelo qual a instalação falhou, volte a executar o comando sem /quiet para ver as mensagens de erro.

Para confirmar o êxito da operação, consulte a secção [Confirmar o êxito da instalação](#verifying-installation-success) neste artigo.

## <a name="verifying-installation-success"></a>Confirmar o êxito da instalação
Pode utilizar os ficheiros de registo da instalação para verificar se a instalação foi concluída com êxito.

### <a name="to-verify-installation-success-for-the-rms-sharing-application-for-office-2016-or-office-2013-and-azure-information-protection-or-active-directory-rms"></a>Para confirmar o êxito da instalação da aplicação de partilha RMS para o Office 2016 ou o Office 2013 e o Azure Information Protection ou o Active Directory RMS

-   Para confirmar o êxito do comando Setup.exe, em cada computador, procure o ficheiro de registo de instalação **RMInstaller.log** na pasta *%temp%\RMS_installer_&lt;guid&gt;* e, em seguida, identifique o código de saída.

    Uma instalação com êxito apresenta um código de saída com o valor 0 e todos os outros números indicam uma falha na instalação.

    Exemplo de nome de ficheiro de registo: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

### <a name="to-verify-installation-success-for-the-rms-sharing-application-for-office-2010-and-azure-information-protection"></a>Para confirmar o êxito da instalação da aplicação de partilha RMS para o Office 2010 e o Azure Information Protection

1.  Para confirmar o êxito do comando Setup.exe, em cada computador, procure o ficheiro de registo de instalação **RMInstaller.log** na pasta *%temp%\RMS_installer_&lt;guid&gt;* e, em seguida, identifique o código de saída.

    Uma instalação com êxito apresenta um código de saída com o valor 0 e todos os outros números indicam uma falha na instalação.

    Exemplo de nome de ficheiro de registo: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Para confirmar o êxito do comando RMSSetup.exe, o utilizador deve ter os seguintes ficheiros criados na pasta *%localappdata%\microsoft\drm*:

    -   CERT-Machine-2048.drm

    -   CERT-Machine.drm

    -   CLC-&#42;.drm

    -   GIC-&#42;.drm

    Exemplo de um ficheiro CLC-&#42;.drm:

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm**

### <a name="to-verify-installation-success-for-the-rms-sharing-application-for-office-2010-and-active-directory-rms"></a>Para confirmar o êxito da instalação da aplicação de partilha RMS para o Office 2010 e o Active Directory RMS

1.  Para confirmar o êxito do comando Setup.exe, em cada computador, procure o ficheiro de registo de instalação na pasta *%temp%\RMS_installer_&lt;guid&gt;* e identifique o código de saída.

    Uma instalação com êxito apresenta um código de saída com o valor 0 e todos os outros números indicam uma falha na instalação.

    Exemplo de nome de ficheiro de registo: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Para confirmar o êxito do comando aadrmprep.exe, em cada computador, procure o seguinte texto no ficheiro de registo de instalação: **aadrmprep.exe saiu com o estado ÊXITO**

    > [!NOTE]
    > Por vezes, a instalação pode ser executada duas vezes; a primeira ocorrência resulta em falha e a segunda é concluída com êxito.

    Se quiser verificar manualmente as alterações de registo feitas pela ferramenta, estas são as seguintes:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @="&lt;certification url&gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser="&lt;default_user&gt;"

### <a name="to-verify-installation-success-for-the-rms-sharing-application-and-office-add-in-only"></a>Para confirmar o êxito da instalação apenas para a aplicação de partilha RMS e o suplemento do Office

1.  Para confirmar o êxito do comando Setup_ipviewer.exe, procure o seguinte texto no ficheiro de registo de instalação: **Installation success or error status: 0**

    Exemplos de linhas de uma instalação concluída com êxito:

    **MSI (s) (F0:B8) [14:19:57:854]: Product: Active Directory Rights Management Services Client 2.1 – Installation completed successfully.**

    **MSI (s) (F0:B8) [14:19:57:854]: Windows Installer installed the product. Product Name: Active Directory Rights Management Services Client 2.1. Product Version: 1.0.1179.1. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.**

2.  Para confirmar o êxito da instalação do suplemento do Office, procure em cada computador o seguinte texto no ficheiro de registo de instalação: **Installation success or error status: 0**

    Exemplos de linhas de uma instalação concluída com êxito:

    **MSI (s) (9C:88) [18:49:04:007]: Product: Microsoft RMS Office Addins – Installation completed successfully.**

    **MSI (s) (9C:88) [18:49:04:007]: Windows Installer installed the product. Product Name: Microsoft RMS Office Addins. Product Version: 1.0.7. Product Language: 1033. Manufacturer: Microsoft. Installation success or error status: 0.**

## <a name="uninstall-commands"></a>Comandos de desinstalação
Nem todos os comandos de instalação necessários para efetuar estas implementações suportam um comando de desinstalação. Pode desinstalar o cliente e a aplicação de partilha AD RMS, bem como o suplemento do Office. Utilize os seguintes comandos para desinstalar estes elementos.

### <a name="to-uninstall-the-ad-rms-client-and-the-rms-sharing-application"></a>Para desinstalar o Cliente AD RMS e a aplicação de partilha RMS

-   Utilize os seguintes comandos:

    -   Para o Windows de 64 bits:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Para o Windows de 32 bits:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

### <a name="to-uninstall-the-office-add-in"></a>Para desinstalar o suplemento do Office

-   Utilize os seguintes comandos:

    -   Para o Windows de 64 bits:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Para o Windows de 32 bits:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

## <a name="suppressing-automatic-updates"></a>Suprimir as atualizações automáticas
Por predefinição, os utilizadores recebem uma notificação quando existe uma versão mais recente da aplicação de partilha RMS e é-lhes pedido que a transfiram. Pode suprimir esta notificação ao fazer a seguinte edição de registo:

1.  Navegue para **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** e, se esta ainda não existir, crie uma nova chave com o nome **RmsSharingApp**.

2.  Selecione **RmsSharingApp**, crie um novo Valor DWORD para **AllowUpdatePrompt** e defina o valor para **0**.

Dado que a aplicação de partilha RMS não é suportada pelo WSUS, pode utilizar o seguinte método para testar as novas versões da aplicação de partilha RMS antes de as implementar para todos os utilizadores:

1.  Execute um script nos computadores de todos os utilizadores para suprimir as atualizações automáticas. Não execute este script nos computadores utilizados pelos administradores para testar novas versões.

2.  Quando uma nova versão se encontra disponível, os administradores devem transferi-la e testá-la.

3.  Após a conclusão dos testes e a resolução de eventuais problemas, implemente a versão mais recente para todos os utilizadores através das instruções de implementação automática existentes neste guia.

## <a name="azure-information-protection-only-configuring-document-tracking"></a>Apenas Azure Information Protection: configurar o controlo de documentos
Se tiver uma [subscrição que suporta o controlo de documentos](https://www.microsoft.com/cloud-platform/azure-information-protection-features), o site de controlo de documentos é ativado por predefinição para todos os utilizadores da sua organização. O controlo de documentos apresenta informações como os endereços de e-mail das pessoas que tentaram aceder a documentos protegidos partilhados por utilizadores, quando essas pessoas tentaram aceder aos mesmos e a sua localização. Se a apresentação deste tipo de informações for proibida dentro da sua organização devido a requisitos de privacidade, pode desativar o acesso ao site de controlo de documentos através do cmdlet [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature). Pode reativar o acesso ao site em qualquer altura através de [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature) e ainda verificar se o acesso ao site está ativado ou desativado com [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature).

Para executar estes cmdlets, tem de ter no mínimo a versão **2.3.0.0** do módulo do Azure Rights Management para o Windows PowerShell. Para obter instruções de instalação, consulte [instalar o módulo do AADRM PowerShell](../deploy-use/install-powershell.md).

> [!TIP]
> Se já transferiu e instalou o módulo anteriormente, verifique o número da versão ao executar: `(Get-Module aadrm –ListAvailable).Version`

Os URLs seguintes são utilizados para o controlo de documentos e têm de ser permitidos (por exemplo, adicione-os à sua lista de Sites Fidedignos se estiver a utilizar o Internet Explorer com Segurança Avançada):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Este URL é destinado aos mapas Bing.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="tracking-and-revoking-documents-for-users"></a>Controlar e revogar documentos para utilizadores

Quando os utilizadores iniciam sessão no site de controlo de documentos, podem controlar e revogar documentos que partilharam utilizando a aplicação de partilha RMS. Quando inicia sessão como administrador do Azure Information Protection (administrador global), pode clicar no ícone de Administração no canto superior direito da página, que muda para o modo de Administrador para que possa ver os documentos que foram partilhados pelos utilizadores na sua organização.

As ações que executar no modo de Administrador são auditadas e registadas nos ficheiros de registo de utilização e tem de confirmar para continuar. Para obter mais informações sobre este registo, veja a secção seguinte.

Quando estiver no modo de Administrador, pode procurar por utilizador ou documento. Se procurar por utilizador, verá todos os documentos partilhados pelo utilizador especificado. Se procurar por documento, verá todos os utilizadores na sua organização que partilharam esse documento. Em seguida, pode explorar os resultados da pesquisa para controlar os documentos que os utilizadores partilharam e revogar estes documentos, se necessário. 

Para sair do modo de Administrador, clique em **X** junto a **Sair do modo de administrador**.

Para obter instruções sobre como utilizar o site de controlo de documentos, veja [Controlar e revogar documentos](sharing-app-track-revoke.md) no guia de utilizador.



### <a name="usage-logging-for-the-document-tracking-site"></a>Registo de utilização para o site de controlo de documentos

São aplicáveis dois campos nos ficheiros de registo de utilização ao controlo de documentos: **AdminAction** e **ActingAsUser**.

**AdminAction** - Este campo tem um valor de true quando um administrador utiliza o site de controlo de documentos no modo de Administrador, por exemplo, para revogar um documento em nome de um utilizador ou para ver quando foi partilhado. Este campo está vazio quando um utilizador inicia sessão no site de controlo de documentos.

**ActingAsUser** - Quando o campo AdminAction tiver o valor de true, este campo contém o nome do utilizador sobre o qual o administrador está a agir quando procurar por utilizador ou proprietário do documento. Este campo está vazio quando um utilizador inicia sessão no site de controlo de documentos. 

Também existem tipos de pedido que registam a forma como os utilizadores e os administradores estão a utilizar o site de controlo de documentos. Por exemplo, **RevokeAccess** é o tipo de pedido quando um utilizador ou um administrador em nome de um utilizador revogou um documento no site de controlo de documentos. Utilize este tipo de pedido juntamente com o campo AdminAction para determinar se o utilizador revogou o seu próprio documento (o campo AdminAction está vazio) ou um administrador revogou um documento em nome de um utilizador (AdminAction é true).


Para obter mais informações sobre o registo de utilização, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md)

## <a name="ad-rms-only-support-for-multiple-email-domains-within-your-organization"></a>Apenas AD RMS: suporte para múltiplos domínios de e-mail dentro da sua organização
Se utilizar o AD RMS e os utilizadores da sua organização tiverem múltiplos domínios de e-mail, possivelmente como resultado de uma fusão ou aquisição, tem de criar a seguinte edição de registo:

1.  Navegue para **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** e, se esta ainda não existir, crie uma nova chave com o nome **RmsSharingApp**.

2.  Selecione **RmsSharingApp**, crie um novo Valor de Múltiplas Cadeias com o nome **FederatedDomains** e, em seguida, adicione todos os domínios e subdomínios utilizados pela sua organização. Os carateres universais não são suportados.

    Por exemplo: a empresa Coho Vineyard &amp; Winery tem o domínio de e-mail padrão **cohovineyardandwinery.com** mas, devido a fusões, também utilizam os domínios de e-mail **cohowinery.com**, **eastcoast.cohowinery.com** e **cohovineyard**. Para os dados do valor **FederatedDomains**, o administrador deve introduzir: **cohowinery.com;eastcoast.cohowinery.com;cohovineyard**

Se não fizer esta alteração de registo, é possível que os utilizadores não consigam consumir conteúdos que foram protegidos por outros utilizadores da organização. Esta edição de registo não é necessária se utilizar o Azure Information Protection.


## <a name="next-steps"></a>Próximos passos
Para obter informações técnicas adicionais com explicações sobre os diferentes níveis de proteção (nativa e genérica), os tipos de ficheiro e as extensões de nome de ficheiro suportados e como pode alterar o nível de proteção predefinido, consulte [Descrição geral técnica da aplicação de partilha Rights Management](sharing-app-admin-guide-technical.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
