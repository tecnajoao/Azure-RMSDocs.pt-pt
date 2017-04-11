---
title: Utilizar o PowerShell com o cliente do Azure Information Protection
description: "As instruções e as informações para os administradores gerirem o cliente do Azure Information Protection através do PowerShell."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4f9d2db7-ef27-47e6-b2a8-d6c039662d3c
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 90b26239979b42eadb008b11a963e35a74698910
ms.sourcegitcommit: 16fec44713c7064959ebb520b9f0857744fecce9
translationtype: HT
---
# <a name="using-powershell-with-the-azure-information-protection-client"></a>Utilizar o PowerShell com o cliente do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8 e Windows 7 com SP1*

Quando instala o cliente do Azure Information Protection, os comandos do PowerShell são instalados automaticamente para que possa gerir o cliente ao executar comandos que pode colocar em scripts para a automatização.

Os cmdlets são instalados com o módulo do PowerShell **AzureInformationProtection**, que substitui o módulo RMSProtection que foi instalado com a Ferramenta de Proteção RMS. Se tiver a ferramenta RMSProtection instalada ao instalar o cliente do Azure Information Protection, o módulo RMSProtection é automaticamente desinstalado.

O módulo AzureInformationProtection inclui todos os cmdlets do Rights Management da Ferramenta de Proteção RMS e dois cmdlets novos que utilizam o serviço Azure Information Protection (AIP) para etiquetar:

|Cmdlet de etiquetagem|Utilização de exemplo|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/azureinformationprotection/vlatest/get-aipfilestatus)|Para uma pasta partilhada, identifique todos os ficheiros com uma etiqueta específica.|
|[Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel)|Para uma pasta partilhada, aplique uma etiqueta especificada a todos os ficheiros que não têm uma etiqueta.|

Para obter uma lista de todos os cmdlets e o artigo de ajuda correspondente, veja [AzureInformationProtection Module (Módulo AzureInformationProtection)](/powershell/azureinformationprotection/vlatest/aip).

Este módulo é instalado em **ProgramFiles (x86) \Microsoft Azure Information Protection** e adiciona esta pasta à variável do sistema **PSModulePath**. O ficheiro .dll deste módulo é denominado **AIP.dll**.

Como com o módulo RMSProtection, a versão atual do módulo AzureInformationProtection tem as seguintes limitações:

- Pode desproteger pastas pessoais do Outlook (ficheiros .pst). No entanto, atualmente, não pode proteger nativamente estes ficheiros ou outros ficheiros de contentor através deste módulo do PowerShell.

- Pode desproteger mensagens de e-mail protegidas do Outlook (ficheiros .rpmsg) quando estiverem numa pasta pessoal do Outlook (.pst), mas não pode desproteger ficheiros .rpmsg fora de uma pasta pessoal.

Antes de começar a utilizar estes cmdlets, veja os pré-requisitos e as instruções adicionais que correspondem à sua implementação:

- [Serviço Azure Information Protection e serviço Azure Rights Management](#azure-information-protection-service-and-azure-rights-management-service)

    - Aplicável se utilizar apenas a classificação ou a classificação com a proteção Rights Management: tem uma subscrição que inclui o Azure Information Protection (por exemplo, Enterprise Mobility + Security).
    - Aplicável se utilizar apenas a proteção com o serviço Azure Rights Management: tem uma subscrição que inclui o serviço Azure Rights Management (por exemplo, o Office 365 E3 e o Office 365 E5).

- [Serviços de Gestão de Direitos do Active Directory](#active-directory-rights-management-services)

    - Aplicável se utilizar apenas a proteção com a versão no local do Azure Rights Management; Serviços de Gestão de Direitos do Active Directory (AD RMS).


## <a name="azure-information-protection-service-and-azure-rights-management-service"></a>Serviço Azure Information Protection e serviço Azure Rights Management

Leia esta secção antes de começar a utilizar os comandos do PowerShell se a sua organização utilizar o Azure Information Protection e o serviço de proteção de dados do Azure Rights Management ou apenas o serviço Azure Rights Management.


### <a name="prerequisites-for-aip-and-azure-rms"></a>Pré-requisitos para o AIP e o Azure RMS

Além dos pré-requisitos para instalar o módulo AzureInformationProtection, existem pré-requisitos adicionais para o serviço Azure Information Protection e o serviço de proteção de dados do Azure Rights Management:

1. O Serviço Azure Rights Management tem de ser ativado.

2. Para remover a proteção dos ficheiros para os outros utilizadores que utilizam a sua conta: tem de estar ativada a funcionalidade de superutilizador para a sua organização e a sua conta tem de estar configurada para ser um superutilizador do Azure Rights Management.

3. Para proteger ou desproteger ficheiros diretamente sem a interação do utilizador: crie uma conta do principal de serviço, execute Set-RMSServerAuthentication e considere fazer este principal de serviço um superutilizador do Azure Rights Management.

4. Para regiões fora da América do Norte: edite o registo para a autenticação no serviço.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Pré-requisito 1: o serviço Azure Rights Management tem de ser ativado

Este pré-requisito aplica-se quer aplique a proteção de dados através da utilização de etiquetas ou da ligação direta ao serviço Azure Rights Management. Configurado para aplicar a proteção de dados.

Se o seu inquilino do Azure Information Protection não estiver ativado, veja as instruções para [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Pré-requisito 2: para remover a proteção dos ficheiros para os outros utilizadores que utilizam a sua conta

Os cenários típicos para remover a proteção dos ficheiros para os outros utilizadores incluem a recuperação de dados ou a deteção de dados. Se estiver a utilizar etiquetas para aplicar a proteção, poderá remover a proteção através da definição de uma nova etiqueta que não aplica a proteção ou da remoção da etiqueta. Porém, é mais provável que se ligue diretamente ao serviço Azure Rights Management para remover a proteção.

Tem de ter permissões do Rights Management para remover a proteção de ficheiros ou ser um superutilizador. A funcionalidade de superutilizador é normalmente utilizada para a deteção ou a recuperação de dados. Para ativar esta funcionalidade e configurar a sua conta para ser um superutilizador, veja [Configurar superutilizadores para o Azure Rights Management e Serviços de Deteção ou Recuperação de Dados](../deploy-use/configure-super-users.md).

#### <a name="prerequisite-3-to-protect-or-unprotect-files-without-user-interaction"></a>Pré-requisito 3: para proteger ou desproteger ficheiros sem interação do utilizador

Atualmente, não pode aplicar etiquetas de forma não interativa, mas pode ligar diretamente ao serviço Azure Rights Management não interativamente para proteger ou desproteger ficheiros.

Tem de utilizar um principal de serviço para estabelecer ligação ao serviço Azure Rights Management não interativamente. Para tal, utilize o cmdlet `Set-RMSServerAuthentication`. Tem de o fazer para cada sessão do Windows PowerShell que executa cmdlets que se ligam diretamente ao serviço Azure Rights Management. Antes de executar este cmdlet, verifique se tem estes três identificadores:

- BposTenantId

- AppPrincipalId

- Chave Simétrica

As secções seguintes explicam como obter estes identificadores.

##### <a name="to-get-the-bpostenantid"></a>Para obter o BposTenantId

Execute o cmdlet Get-AadrmConfiguration a partir do módulo do Windows PowerShell do Azure RMS:

1. Se este módulo ainda não estiver instalado no computador, veja [Instalar o Windows PowerShell para o Azure Rights Management](../deploy-use/install-powershell.md).

2. Inicie o Windows PowerShell com a opção **Executar como Administrador**.

3. Utilize o cmdlet `Connect-AadrmService` para ligar ao serviço Azure Rights Management:
    
        Connect-AadrmService
    
    Quando for solicitado, introduza as credenciais de administrador de inquilinos do Azure Information Protection (normalmente, utilizará uma conta de um administrador global do Azure Active Directory ou do Office 365).
    
4. Execute `Get-AadrmConfiguration` e faça uma cópia do valor BPOSId.
    
    O exemplo abaixo mostra a saída de Get-AadrmConfiguration:
    
            BPOSId                                   : 23976bc6-dcd4-4173-9d96-dad1f48efd42
        
            RightsManagement ServiceId               : 1a302373-f233-440600909-4cdf305e2e76
        
            LicensingIntranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
            LicensingExtranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing
        
            CertificationIntranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification
        
            CertificationExtranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification

5. Encerre o serviço:
    
        Disconnect-AadrmService

##### <a name="to-get-the-appprincipalid-and-symmetric-key"></a>Para obter o AppPrincipalId e a Chave Simétrica

Crie um novo principal de serviço, ao executar o cmdlet `New-MsolServicePrincipal` no módulo do MSOnline PowerShell do Azure Active Directory: 

1. Se este módulo ainda não estiver instalado no computador, veja [Instalar o Módulo Azure AD](/powershell/azuread/#install-the-azure-ad-module).

2. Inicie o Windows PowerShell com a opção **Executar como Administrador**.

3. Utilize o cmdlet **Connect-MsolService** para ligar ao Azure AD:
    
        Connect-MsolService
    
    Quando lhe for pedido, introduza as credenciais de administrador de inquilinos do Azure AD (normalmente, utilizará uma conta de um administrador global do Azure Active Directory ou do Office 365).

4. Execute o cmdlet New-MsolServicePrincipal para criar um novo principal de serviço:
    
        New-MsolServicePrincipal
    
    Quando lhe for pedido, introduza um nome a apresentar à sua escolha para este principal de serviço que o irá ajudar a identificar o objetivo mais tarde como uma conta para estabelecer ligação ao serviço Azure Rights Management para que possa proteger e desproteger ficheiros.
    
    Um exemplo de saída do New-MsolServicePrincipal:
    
        Supply values for the following parameters:
        
        DisplayName: AzureRMSProtectionServicePrincipal
        The following symmetric key was created as one was not supplied
        zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=
        
        Display Name: AzureRMSProtectionServicePrincipal
        ServicePrincipalNames: (b5e3f7g1-b5c2-4c96-a594-a0807f65bba4)
        ObjectId: 23720996-593c-4122-bfc7-1abb5a0b5109
        AppPrincialId: b5e3f76a-b5c2-4c96-a594-a0807f65bba4
        TrustedForDelegation: False
        AccountEnabled: True
        Addresses: ()
        KeyType: Symmetric
        KeyId: 8ef61651-ca11-48ea-a350-25834a1ba17c
        StartDate: 3/7/2014 4:43:59 AM
        EndDate: 3/7/2014 4:43:59 AM
        Usage: Verify

5. A partir desta saída, anote a chave simétrica e o AppPrincialId.

    É especialmente importante que faça uma cópia da chave simétrica, uma vez não pode recuperá-la na íntegra mais tarde. Como tal, se não a souber, terá de criar um novo principal de serviço da próxima vez que precisar de fazer a autenticação no serviço Azure Rights Management.

Com estas instruções e os nossos exemplos, temos os três identificadores necessários para a execução do Set-RMSServerAuthentication:

- ID do inquilino: **23976bc6-dcd4-4173-9d96-dad1f48efd42**

- Chave simétrica: **zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=**

- AppPrincipalId: **b5e3f76a-b5c2-4c96-a594-a0807f65bba4**

O nosso comando de exemplo teria um aspeto semelhante ao seguinte:

    Set-RMSServerAuthentication -Key zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=-AppPrincipalId b5e3f76a-b5c2-4c96-a594-a0807f65bba4-BposTenantId 23976bc6-dcd4-4173-9d96-dad1f48efd42

Tal como apresentado no comando anterior, pode indicar os valores com um comando único, ou apenas escrever Set-RMSServerAuthentication, e indicar os valores individualmente quando lhe for pedido. Quando o comando estiver concluído, verá “**O RmsServerAuthentication está definido como LIGADO**”, que significa que agora pode proteger e desproteger ficheiros através do seu principal de serviço.

Considere tornar este principal de serviço um superutilizador: para garantir que este principal de serviço pode sempre desproteger ficheiros para outros utilizadores, pode ser configurado para ser um superutilizador. Da mesma forma que configura uma conta de utilizador padrão para ser um superutilizador, utilize o mesmo cmdlet do Azure RMS [Add-AadrmSuperUser](/powershell/aadrm/vlatest/Add-AadrmSuperUser.md), mas especifique o parâmetro **-ServicePrincipalId** com o valor de AppPrincipalId.

Para obter mais informações sobre superutilizadores, veja [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md).

> [!NOTE]
> Para utilizar a sua própria conta para a autenticação no serviço Azure Rights Management, não precisa de executar Set-RMSServerAuthentication antes de proteger ou desproteger ficheiros ou de obter modelos.

#### <a name="prerequisite-4-for-regions-outside-north-america"></a>Pré-requisito 4: para regiões fora da América do Norte

Para a autenticação fora da região da América do Norte do Azure, tem de editar o registo da seguinte forma. Se o seu inquilino do Azure Information Protection estiver na América do Norte, não siga este passo:

1. Execute o cmdlet Get-AadrmConfiguration novamente e tome nota dos valores para **CertificationExtranetDistributionPointUrl** e **LicensingExtranetDistributionPointUrl**.

2. Em cada computador onde irá executar os cmdlets AzureInformationProtection, abra o editor de registo e navegue para:`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC`

3. Se não vir uma chave **ServiceLocation**, crie-a para que o caminho do registo mostre **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation**

4. Para a chave **ServiceLocation**, crie duas chaves, caso não existam, com o nome **EnterpriseCertification** e **EnterprisePublishing**. 
    
    Quando cria estas chaves REG_SZ, não altere o Nome de “(Predefinição)”, mas edite-as para definir os Dados do valor:

    - Para **EnterpriseCertification**, cole o valor de CertificationExtranetDistributionPointUrl.
    
    - Para **EnterpriseCertification**, cole o valor de LicensingExtranetDistributionPointUrl.

5. Feche o editor de registo. Não é preciso reiniciar o computador. No entanto, se estiver a utilizar uma conta do principal de serviço em vez da sua própria conta de utilizador, terá de executar o comando Set-RMSServerAuthentication depois desta edição do registo.

### <a name="example-scenarios-for-using-the-cmdlets-for-azure-information-protection-and-the-azure-rights-management-service"></a>Cenários de exemplo para utilizar os cmdlets para o Azure Information Protection e o serviço Azure Rights Management

É mais eficiente utilizar etiquetas para classificar e proteger ficheiros, uma vez que apenas precisa de dois cmdlets, que podem ser executados individualmente ou em conjunto: [Get-AIPFileStatus](/powershell/azureinformationprotection/vlatest/get-aipfilestatus) e [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel). Utilize a ajuda de ambos os cmdlets para obter mais informações e exemplos.

No entanto, para proteger ou desproteger ficheiros ligando-se diretamente ao serviço Azure Rights Management, tem geralmente de executar uma série de cmdlets conforme descrito em seguida.

Em primeiro lugar, se precisar de se autenticar no serviço Azure Rights Management com um principal de serviço em vez de utilizar a sua própria conta, numa sessão do Powershell, escreva:

    Set-RMSServerAuthentication

Quando lhe for pedido, introduza os três identificadores conforme descrito em [Pré-requisito 3: para proteger ou desproteger ficheiros sem a interação do utilizador](client-admin-guide-powershell.md#prerequisite-3-to-protect-or-unprotect-files-without-user-interaction).

Para poder proteger ficheiros, terá de transferir os modelos do Rights Management para o computador e identificar qual utilizar e o número de ID correspondente. A partir da saída, pode copiar o ID do modelo:

    Get-RMSTemplate
    
A saída pode ser semelhante ao seguinte:

    TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content cannot be modified.
    Name              : Contoso, Ltd - Confidential View Only
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    
    TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content can be modified but cannot be copied and printed.
    Name              : Contoso, Ltd - Confidential
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    FromTemplate      : True

Tenha em atenção que se não executou o comando Set-RMSServerAuthentication, será autenticado para o serviço Azure Rights Management através da sua própria conta de utilizador. Se estiver num computador associado a um domínio, as suas credenciais atuais serão sempre utilizadas automaticamente. Se estiver num computador de grupo de trabalho, será solicitado a iniciar sessão no Azure e estas credenciais serão armazenadas em cache para comandos subsequentes. Neste cenário, se mais tarde tiver de iniciar sessão como um utilizador diferente, utilize o cmdlet `Clear-RMSAuthentication`.

Agora que sabe o ID do modelo, pode utilizá-lo com o cmdlet `Protect-RMSFile` para proteger um ficheiro individual ou todos os ficheiros numa pasta. Por exemplo, se quiser proteger apenas um único ficheiro e substituir o original, ao utilizar o modelo “Contoso, Lda. – Confidencial”:

    Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

A saída pode ser semelhante ao seguinte:

    InputFile             EncryptedFile
    ---------             -------------
    C:\Test.docx          C:\Test.docx

Para proteger todos os ficheiros numa pasta, utilize o parâmetro **-Folder** com uma letra de unidade e caminho ou caminho UNC. Por exemplo:

    Protect-RMSFile -Folder \Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

A saída pode ser semelhante ao seguinte:

    InputFile                          EncryptedFile
    ---------                          -------------
    \Server1\Documents\Test1.docx     \Server1\Documents\Test1.docx
    \Server1\Documents\Test2.docx     \Server1\Documents\Test2.docx
    \Server1\Documents\Test3.docx     \Server1\Documents\Test3.docx
    \Server1\Documents\Test4.docx     \Server1\Documents\Test4.docx

Quando a extensão de nome de ficheiro não é alterada depois de a proteção ser aplicada, pode sempre utilizar o cmdlet `Get-RMSFileStatus` mais tarde para verificar se o ficheiro está protegido. Por exemplo:

    Get-RMSFileStatus -File \Server1\Documents\Test1.docx

A saída pode ser semelhante ao seguinte:

    FileName                              Status
    --------                              ------
    \Server1\Documents\Test1.docx         Protected

Para desproteger um ficheiro, terá de ter direitos de Proprietário ou de Extração a partir do momento em que o ficheiro foi protegido ou terá de executar os cmdlets como um superutilizador. Em seguida, utilize o cmdlet Desproteger. Por exemplo:

    Unprotect-RMSFile C:\test.docx -InPlace

A saída pode ser semelhante ao seguinte:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

Tenha em atenção que se os modelos do Rights Management forem alterados, terá de os transferir novamente com `Get-RMSTemplate -force`. 

## <a name="active-directory-rights-management-services"></a>Serviços de Gestão de Direitos do Active Directory

Leia esta secção antes de começar a utilizar os comandos do PowerShell para proteger ou desproteger ficheiros quando a sua organização utiliza apenas Serviços de Gestão de Direitos do Active Directory.


### <a name="prerequisites-for-ad-rms"></a>Pré-requisitos do AD RMS

Além dos pré-requisitos para instalar o módulo AzureInformationProtection, a sua conta tem de ter permissões de Leitura e Execução para aceder a ServerCertification.asmx:

1. Inicie sessão num servidor AD RMS.

2. Clique em **Iniciar** e, em seguida, em **Computador**.

3. No Explorador de Ficheiros, navegue até %systemdrive%\Initpub\wwwroot\_wmsc\Certification.

4. Clique com o botão direito do rato em **ServerCertification.asmx** e, em seguida, clique em **Propriedades**.

5. Na caixa de diálogo **Propriedades de ServerCertification.asmx**, clique no separador **Segurança**. 

6. Clique no botão **Continuar** ou no botão **Editar**. 

7. Na caixa de diálogo **Permissões para ServerCertification.asmx**, clique em **Adicionar**. 

8. Adicione o nome da sua conta. Se outros administradores do AD RMS também forem utilizar estes cmdlets para proteger e desproteger ficheiros, adicione também os nomes deles.

9. Na coluna **Permitir**, confirme que as caixas de verificação **Leitura e Execução**e **Leitura** estão selecionadas.

10. Clique em **OK** duas vezes.

### <a name="example-scenarios-for-using-the-cmdlets-for-active-directory-rights-management-services"></a>Cenários de exemplo para utilizar os cmdlets para os Serviços de Gestão de Direitos do Active Directory

Um cenário típico para estes cmdlets é proteger todos os ficheiros numa pasta ao utilizar um modelo de política de direitos ou para desproteger um ficheiro. 

Em primeiro lugar, se tiver mais de uma implementação do AD RMS, precisará dos nomes dos servidores do AD RMS, o que pode fazer ao utilizar o cmdlet Get-RMSServer para apresentar uma lista de servidores disponíveis:

    Get-RMSServer

A saída pode ser semelhante ao seguinte:

    Number of RMS Servers that can provide templates: 2 
    ConnectionInfo             DisplayName          AllowFromScratch
    --------------             -------------        ----------------
    Microsoft.InformationAnd…  RmsContoso                       True
    Microsoft.InformationAnd…  RmsFabrikam                      True

Antes de poder proteger os ficheiros, terá de obter uma lista de modelos do Rights Management para identificar qual utilizar e o número de ID correspondente. Só quando tiver mais do que uma implementação do AD RMS é que terá de especificar também o servidor RMS. 

A partir da saída, pode copiar o ID do modelo:

    Get-RMSTemplate -RMSServer RmsContoso

A saída pode ser semelhante ao seguinte:

    TemplateId        : {82bf3474-6efe-4fa1-8827-d1bd93339119}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content cannot be modified.
    Name              : Contoso, Ltd - Confidential View Only
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    
    
    TemplateId        : {e6ee2481-26b9-45e5-b34a-f744eacd53b0}
    CultureInfo       : en-US
    Description       : This content is proprietary information intended for internal users only. This content can be modified but cannot be copied and printed.
    Name              : Contoso, Ltd - Confidential
    IssuerDisplayName : Contoso, Ltd
    FromTemplate      : True
    FromTemplate      : True

Agora que sabe o ID do modelo, pode utilizá-lo com o cmdlet Protect-RMSFile para proteger um ficheiro individual ou todos os ficheiros numa pasta. Por exemplo, se quiser proteger apenas um único ficheiro e substituir o original, ao utilizar o modelo “Contoso, Lda. – Confidencial”:

    Protect-RMSFile -File C:\Test.docx -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

A saída pode ser semelhante ao seguinte:

    InputFile             EncryptedFile
    ---------             -------------
    C:\Test.docx          C:\Test.docx   

Para proteger todos os ficheiros numa pasta, utilize o parâmetro -Folder com uma letra de unidade e caminho ou caminho UNC. Por exemplo:

    Protect-RMSFile -Folder \\Server1\Documents -InPlace -TemplateId e6ee2481-26b9-45e5-b34a-f744eacd53b0

A saída pode ser semelhante ao seguinte:

    InputFile                          EncryptedFile
    ---------                          -------------
    \\Server1\Documents\Test1.docx     \\Server1\Documents\Test1.docx   
    \\Server1\Documents\Test2.docx     \\Server1\Documents\Test2.docx   
    \\Server1\Documents\Test3.docx     \\Server1\Documents\Test3.docx   
    \\Server1\Documents\Test4.docx     \\Server1\Documents\Test4.docx   

Quando a extensão de nome de ficheiro não é alterada depois de a proteção de RMS ser aplicada, pode sempre utilizar o cmdlet Get-RMSFileStatus mais tarde para verificar se o ficheiro está protegido. Por exemplo: 

    Get-RMSFileStatus -File \\Server1\Documents\Test1.docx

A saída pode ser semelhante ao seguinte:

    FileName                              Status
    --------                              ------
    \\Server1\Documents\Test1.docx        Protected

Para desproteger um ficheiro, terá de ter direitos de Proprietário ou de Extração a partir do momento em que o ficheiro foi protegido ou ser um superutilizador do AD RMS. Em seguida, utilize o cmdlet Desproteger. Por exemplo:

    Unprotect-RMSFile C:\test.docx -InPlace

A saída pode ser semelhante ao seguinte:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx


## <a name="next-steps"></a>Passos seguintes
Para obter ajuda com o cmdlet quando estiver numa sessão do PowerShell, utilize o cmdlet Get-Help <cmdlet name>, em que <cmdlet name> é o nome do cmdlet que pretende pesquisar. Por exemplo: 

    Get-Help Get-RMSTemplate

Veja o seguinte para obter informações adicionais que poderá precisar para suportar o cliente do Azure Information Protection:

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
