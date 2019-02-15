---
title: Utilizar o PowerShell com o cliente do Azure Information Protection
description: As instruções e as informações para os administradores gerirem o cliente do Azure Information Protection através do PowerShell.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/25/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4f9d2db7-ef27-47e6-b2a8-d6c039662d3c
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 0222a3ad5beaaae01d0da42d869ef2241c3af21a
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254021"
---
# <a name="admin-guide-using-powershell-with-the-azure-information-protection-client"></a>Guia do administrador: Utilizar o PowerShell com o cliente do Azure Information Protection

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Quando instalar o cliente do Azure Information Protection, comandos do PowerShell são instalados automaticamente. Isto permite-lhe gerir o cliente ao executar comandos que pode colocar em scripts para automação.

Os cmdlets são instalados com o módulo do PowerShell **AzureInformationProtection**. Este módulo inclui todos os cmdlets do Rights Management da ferramenta de proteção RMS (já não é suportada). Também existem cmdlets que utilizam o Azure Information Protection para etiquetagem. Por exemplo:

|Cmdlet de etiquetagem|Utilização de exemplo|
|----------------|---------------|
|[Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus)|Para uma pasta partilhada, identifique todos os ficheiros com uma etiqueta específica.|
|[Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification)|Para uma pasta partilhada, inspecione o conteúdo do ficheiro e etiquete automaticamente os ficheiros sem etiqueta, de acordo com as condições que especificou.|
|[Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel)|Para uma pasta partilhada, aplique uma etiqueta especificada a todos os ficheiros que não têm uma etiqueta.|
|[Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)|Etiqueta ficheiros de forma não interativa, por exemplo, utilizando um script que é executada com base numa agenda.|

> [!TIP]
> Para utilizar os cmdlets com comprimentos de caminhos superiores a 260 carateres, utilize o seguinte procedimento [definição de política de grupo](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/) ou seja disponíveis inicial do Windows 10, versão 1607:<br /> **Política de computador local** > **configuração do computador** > **modelos administrativos** > **todas as definições**  >  **NTFS** > **caminhos longos do Win32 ativar** 
> 
> Para o Windows Server 2016, pode utilizar a mesma definição de política de grupo ao instalar os modelos administrativos mais recentes (ADMX) para o Windows 10.
>
> Para obter mais informações, consulte a [limitação de comprimento máximo do caminho](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) secção da documentação do desenvolvedor do Windows 10.

O [scanner do Azure Information Protection](../deploy-aip-scanner.md) utiliza cmdlets do módulo AzureInformationProtection para instalar e configurar um serviço no Windows Server. Este scanner, em seguida, permite-lhe detetar, classificar e proteger ficheiros em arquivos de dados.

Para obter uma lista de todos os cmdlets e o artigo de ajuda correspondente, veja [AzureInformationProtection Module (Módulo AzureInformationProtection)](/powershell/module/azureinformationprotection). Dentro de uma sessão do PowerShell, escreva `Get-Help <cmdlet name> -online` para ver a ajuda mais recente.  

Este módulo é instalado em **ProgramFiles (x86) \Microsoft Azure Information Protection** e adiciona esta pasta à variável do sistema **PSModulePath**. O ficheiro .dll deste módulo é denominado **AIP.dll**.

Atualmente, se instalar o módulo como um usuário e executar os cmdlets no mesmo computador como outro utilizador, tem de executar primeiro o `Import-Module AzureInformationProtection` comando. Neste cenário, o módulo não autoload quando o primeiro de executar um cmdlet.

A versão atual do módulo AzureInformationProtection tem as seguintes limitações:

- Pode desproteger pastas pessoais do Outlook (ficheiros .pst). No entanto, atualmente, não pode proteger nativamente estes ficheiros ou outros ficheiros de contentor através deste módulo do PowerShell.

- Pode desproteger mensagens de e-mail protegidas do Outlook (ficheiros .rpmsg) quando estiverem numa pasta pessoal do Outlook (.pst), mas não pode desproteger ficheiros .rpmsg fora de uma pasta pessoal.

Antes de começar a utilizar estes cmdlets, veja os pré-requisitos e as instruções adicionais que correspondem à sua implementação:

- [Serviço do Azure Information Protection e o Azure Rights Management](#azure-information-protection-and-azure-rights-management-service)

    - Aplicável se utilizar apenas a classificação ou a classificação com proteção do Rights Management: Tem uma subscrição que inclui o Azure Information Protection (por exemplo, Enterprise Mobility + Security).
    - Aplicável se utilizar apenas a proteção com o serviço Azure Rights Management: Tem uma subscrição que inclui o serviço Azure Rights Management (por exemplo, o Office 365 E3 e o Office 365 E5).

- [Serviços de Gestão de Direitos do Active Directory](#active-directory-rights-management-services)

    - Aplicável se utilizar apenas a proteção com a versão no local do Azure Rights Management; Serviços de Gestão de Direitos do Active Directory (AD RMS).


## <a name="azure-information-protection-and-azure-rights-management-service"></a>Serviço do Azure Information Protection e o Azure Rights Management

Leia esta secção antes de começar a utilizar os comandos do PowerShell, se sua organização utiliza o Azure Information Protection para classificação e proteção ou apenas o serviço Azure Rights Management para proteção de dados.


### <a name="prerequisites"></a>Pré-requisitos

Além dos pré-requisitos para instalar o módulo AzureInformationProtection, existem pré-requisitos adicionais para a etiquetagem de Azure Information Protection e o serviço de proteção de dados do Azure Rights Management:

1. O Serviço Azure Rights Management tem de ser ativado.

2. Para remover a proteção dos ficheiros para os outros utilizadores que utilizam a conta: 

    - A funcionalidade de superutilizador tem de estar ativada para a sua organização e a conta tem de estar configurada para ser um superutilizador do Azure Rights Management.

3. Para proteger ou desproteger ficheiros diretamente sem a interação do utilizador: 

    - Crie uma conta do principal de serviço, execute Set-RMSServerAuthentication e considere tornar este principal de serviço um superutilizador do Azure Rights Management.

4. Para regiões fora da América do Norte: 

    - Edite o registo de deteção do serviço.

#### <a name="prerequisite-1-the-azure-rights-management-service-must-be-activated"></a>Pré-requisito 1: O serviço Azure Rights Management tem de ser ativado

Este pré-requisito aplica-se quer aplique a proteção de dados através da utilização de etiquetas ou da ligação direta ao serviço Azure Rights Management para a aplicação da proteção de dados.

Se o seu inquilino do Azure Information Protection não estiver ativado, veja as instruções para [Ativar o Azure Rights Management](../activate-service.md).

#### <a name="prerequisite-2-to-remove-protection-from-files-for-others-using-your-own-account"></a>Pré-requisito 2: Para remover a proteção de ficheiros para outros utilizadores que utilizam a sua conta

Os cenários típicos para remover a proteção dos ficheiros para os outros utilizadores incluem a recuperação de dados ou a deteção de dados. Se estiver a utilizar etiquetas para aplicar a proteção, poderá remover a proteção através da definição de uma nova etiqueta que não aplica a proteção ou da remoção da etiqueta. Porém, é mais provável que se ligue diretamente ao serviço Azure Rights Management para remover a proteção.

Tem de ter um direito de utilização do Rights Management para remover a proteção de ficheiros ou ser um superutilizador. A funcionalidade de superutilizador é normalmente utilizada para a deteção ou a recuperação de dados. Para ativar esta funcionalidade e configurar a sua conta para ser um superutilizador, veja [Configurar superutilizadores para o Azure Rights Management e Serviços de Deteção ou Recuperação de Dados](../configure-super-users.md).

#### <a name="prerequisite-3-to-protect-or-unprotect-files-without-user-interaction"></a>Pré-requisito 3: Para proteger ou desproteger ficheiros sem interação do utilizador

Pode ligar diretamente ao serviço Azure Rights Management não interativamente para proteger ou desproteger ficheiros.

Tem de utilizar uma serviço principal conta para ligar ao serviço Azure Rights Management não interativamente, que pode fazer ao utilizar o `Set-RMSServerAuthentication` cmdlet. Tem de o fazer para cada sessão do Windows PowerShell que executa cmdlets que se ligam diretamente ao serviço Azure Rights Management. Antes de executar este cmdlet, tem de ter estes três identificadores:

- BposTenantId

- AppPrincipalId

- Chave Simétrica

Pode utilizar os seguintes comandos do PowerShell e instruções comentadas para obter automaticamente os valores para os identificadores e execute o cmdlet Set-RMSServerAuthentication. Em alternativa, pode obter e especifique os valores manualmente.

Para obter os valores e execute Set-RMSServerAuthentication automaticamente:

````
# Make sure that you have the AADRM and MSOnline modules installed

$ServicePrincipalName="<new service principal name>"
Connect-AadrmService
$bposTenantID=(Get-AadrmConfiguration).BPOSId
Disconnect-AadrmService
Connect-MsolService
New-MsolServicePrincipal -DisplayName $ServicePrincipalName

# Copy the value of the generated symmetric key

$symmetricKey="<value from the display of the New-MsolServicePrincipal command>"
$appPrincipalID=(Get-MsolServicePrincipal | Where { $_.DisplayName -eq $ServicePrincipalName }).AppPrincipalId
Set-RMSServerAuthentication -Key $symmetricKey -AppPrincipalId $appPrincipalID -BposTenantId $bposTenantID
````

As secções seguintes explicam como obter e especificar estes valores, com mais informações sobre cada um deles manualmente.

##### <a name="to-get-the-bpostenantid"></a>Para obter o BposTenantId

Execute o cmdlet Get-AadrmConfiguration a partir do módulo do Windows PowerShell do Azure RMS:

1. Se este módulo ainda não estiver instalado no seu computador, consulte [instalar o módulo do PowerShell do AADRM](../install-powershell.md).

2. Inicie o Windows PowerShell com a opção **Executar como Administrador**.

3. Utilize o cmdlet `Connect-AadrmService` para ligar ao serviço Azure Rights Management:

        Connect-AadrmService

    Quando lhe for pedido, introduza as suas credenciais de administrador de inquilino do Azure Information Protection. Normalmente, utiliza uma conta que seja um administrador global do Azure Active Directory ou Office 365.

4. Execute `Get-AadrmConfiguration` e faça uma cópia do valor BPOSId.

    Um exemplo de saída de Get-AadrmConfiguration:

            BPOSId                                   : 23976bc6-dcd4-4173-9d96-dad1f48efd42

            RightsManagement ServiceId               : 1a302373-f233-440600909-4cdf305e2e76

            LicensingIntranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing

            LicensingExtranetDistributionPointUrl    : https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/licensing

            CertificationIntranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification

            CertificationExtranetDistributionPointUrl: https://1s302373-f233-4406-9090-4cdf305e2e76.rms.na.aadrm.com/_wmcs/certification

5. Encerre o serviço:

        Disconnect-AadrmService

##### <a name="to-get-the-appprincipalid-and-symmetric-key"></a>Para obter o AppPrincipalId e a Chave Simétrica

Crie um novo principal de serviço ao executar o cmdlet `New-MsolServicePrincipal` no módulo MSOnline PowerShell do Azure Active Directory e utilize as instruções seguintes. 

> [!IMPORTANT]
> Não utilize o cmdlet mais recente do Azure AD PowerShell, New-AzureADServicePrincipal, para criar este principal de serviço. O serviço Azure Rights Management não suporta o cmdlet New-AzureADServicePrincipal. 

1. Se o módulo MSOnline ainda não estiver instalado no computador, execute `Install-Module MSOnline`.

2. Inicie o Windows PowerShell com a opção **Executar como Administrador**.

3. Utilize o cmdlet **Connect-MsolService** para ligar ao Azure AD:

        Connect-MsolService

    Quando lhe for pedido, introduza as suas credenciais de administrador de inquilino do Azure AD (normalmente, utiliza uma conta que seja um administrador global do Azure Active Directory ou Office 365).

4. Execute o cmdlet New-MsolServicePrincipal para criar um novo principal de serviço:

        New-MsolServicePrincipal

    Quando lhe for pedido, introduza um nome a apresentar à sua escolha para este principal de serviço que o ajuda a identificar o objetivo mais tarde como uma conta para estabelecer ligação ao serviço Azure Rights Management para que possa proteger e desproteger ficheiros.

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

    É importante que faça uma cópia desta chave simétrica, agora. Não é possível obter esta chave mais tarde, se não souber quando, em seguida tem de autenticar para o serviço Azure Rights Management, terá de criar um novo principal de serviço.

Com estas instruções e os nossos exemplos, temos os três identificadores necessários para a execução do Set-RMSServerAuthentication:

- Id do inquilino: **23976bc6-dcd4-4173-9d96-dad1f48efd42**

- Chave simétrica: **zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=**

- AppPrincipalId: **b5e3f76a-b5c2-4c96-a594-a0807f65bba4**

O nosso comando de exemplo teria um aspeto semelhante ao seguinte:

    Set-RMSServerAuthentication -Key zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA=-AppPrincipalId b5e3f76a-b5c2-4c96-a594-a0807f65bba4-BposTenantId 23976bc6-dcd4-4173-9d96-dad1f48efd42

Conforme mostrado no comando anterior, pode fornecer os valores com um comando único, o que faria num script para executar de forma não interativa. Mas para fins de teste, pode apenas escrever Set-RMSServerAuthentication e indicar os valores-individualmente quando lhe for pedido. Quando o comando for concluído, o cliente está agora a funcionar no "modo de servidor", que é adequado para utilização não interativa, como scripts e a infraestrutura de classificação de ficheiros do Windows Server.

Considere tornar esta conta do principal de serviço um Superutilizador: Para garantir que esta conta do principal de serviço pode sempre desproteger ficheiros para outros, ele pode ser configurado para ser um Superutilizador. Da mesma forma como configurar uma conta de usuário padrão para ser um Superutilizador, é usar o mesmo cmdlet do Azure RMS [Add-AadrmSuperUser](/powershell/module/aadrm/add-aadrmsuperuser), mas especifique o **ServicePrincipalId** parâmetro com o seu Valor de AppPrincipalId.

Para obter mais informações sobre superutilizadores, veja [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../configure-super-users.md).

> [!NOTE]
> Para utilizar a sua própria conta para a autenticação no serviço Azure Rights Management, não precisa de executar Set-RMSServerAuthentication antes de proteger ou desproteger ficheiros ou de obter modelos.

#### <a name="prerequisite-4-for-regions-outside-north-america"></a>Pré-requisito 4: Para regiões fora da América do Norte

Quando utiliza uma conta do principal de serviço para proteger ficheiros e transferir modelos fora da região da América do Norte do Azure, tem de editar o registo: 

1. Execute o cmdlet Get-AadrmConfiguration novamente e tome nota dos valores para **CertificationExtranetDistributionPointUrl** e **LicensingExtranetDistributionPointUrl**.

2. Em cada computador onde irá executar os cmdlets AzureInformationProtection, abra o editor de registo.

3. Navegue para o seguinte caminho: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation`. 

    Se não vir a **MSIPC** chave ou **ServiceLocation** da chave, criá-los.

4. Para a chave **ServiceLocation**, crie duas chaves, caso não existam, com o nome **EnterpriseCertification** e **EnterprisePublishing**. 

    Para o valor de cadeia de caracteres que é criado automaticamente para essas chaves, não altere o nome de "(predefinição)", mas editar a cadeia de caracteres para definir os dados do valor:

   - Para **EnterpriseCertification**, cole o valor de CertificationExtranetDistributionPointUrl.

   - Para **EnterpriseCertification**, cole o valor de LicensingExtranetDistributionPointUrl.

     Por exemplo, sua entrada de registo para EnterpriseCertification deve ter um aspeto semelhante ao seguinte:

     ![Editar o registo de módulo do PowerShell de proteção de informações do Azure para regiões fora da América do Norte](../media/registry-example-rmsprotection.png)

5. Feche o editor de registo. Não é preciso reiniciar o computador. No entanto, se estiver a utilizar uma conta do principal de serviço em vez da sua própria conta de utilizador, terá de executar o comando Set-RMSServerAuthentication depois desta edição do registo.

### <a name="example-scenarios-for-using-the-cmdlets-for-azure-information-protection-and-the-azure-rights-management-service"></a>Cenários de exemplo para utilizar os cmdlets para o Azure Information Protection e o serviço Azure Rights Management

É mais eficiente utilizar etiquetas para classificar e proteger ficheiros, uma vez que existem apenas dois cmdlets que precisa, e que podem ser executados individualmente ou em conjunto: [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) e [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel). Utilize a ajuda de ambos os cmdlets para obter mais informações e exemplos.

No entanto, para proteger ou desproteger ficheiros ligando-se diretamente ao serviço Azure Rights Management, tem geralmente de executar uma série de cmdlets conforme descrito em seguida.

Em primeiro lugar, se tiver de autenticar para o serviço Azure Rights Management com uma conta do principal de serviço, em vez de utilizar a sua própria conta, numa sessão do PowerShell, escreva:

    Set-RMSServerAuthentication

Quando lhe for pedido, introduza os três identificadores, conforme descrito em [pré-requisito 3: Para proteger ou desproteger ficheiros sem interação do utilizador](client-admin-guide-powershell.md#prerequisite-3-to-protect-or-unprotect-files-without-user-interaction).

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

Tenha em atenção que se não executou o comando Set-RMSServerAuthentication, é autenticado para o serviço Azure Rights Management através da sua própria conta de utilizador. Se estiver num computador associado a um domínio, as suas credenciais atuais são sempre utilizadas automaticamente. Se estiver num computador de grupo de trabalho, é solicitado a iniciar sessão no Azure e estas credenciais são armazenadas em cache para comandos subsequentes. Neste cenário, se mais tarde tiver de iniciar sessão como um utilizador diferente, utilize o cmdlet `Clear-RMSAuthentication`.

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

Para desproteger um ficheiro, tem de ter direitos de proprietário ou de extração de quando o ficheiro foi protegido. Em alternativa, tem de executar os cmdlets como um Superutilizador. Em seguida, utilize o cmdlet Desproteger. Por exemplo:

    Unprotect-RMSFile C:\test.docx -InPlace

A saída pode ser semelhante ao seguinte:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

Tenha em atenção que se os modelos do Rights Management forem alterados, terá de os transferir novamente com `Get-RMSTemplate -force`. 

## <a name="active-directory-rights-management-services"></a>Serviços de Gestão de Direitos do Active Directory

Leia esta secção antes de começar a utilizar os comandos do PowerShell para proteger ou desproteger ficheiros quando a sua organização utiliza apenas Serviços de Gestão de Direitos do Active Directory.


### <a name="prerequisites"></a>Pré-requisitos

Além dos pré-requisitos para instalar o módulo AzureInformationProtection, a conta utilizada para proteger ou desproteger ficheiros tem de ter permissões de leitura e execução para aceder a ServerCertification:

1. Inicie sessão num servidor AD RMS.

2. Clique em **Iniciar** e, em seguida, em **Computador**.

3. No Explorador de Ficheiros, navegue até %systemdrive%\Initpub\wwwroot\_wmsc\Certification.

4. Clique com o botão direito do rato em **ServerCertification.asmx** e, em seguida, clique em **Propriedades**.

5. Na caixa de diálogo **Propriedades de ServerCertification.asmx**, clique no separador **Segurança**. 

6. Clique no botão **Continuar** ou no botão **Editar**. 

7. Na caixa de diálogo **Permissões para ServerCertification.asmx**, clique em **Adicionar**. 

8. Adicione o nome da sua conta. Se outros administradores do AD RMS ou contas de serviço também irão utilizar estes cmdlets para proteger e desproteger ficheiros, adicione essas contas também. 

    Para proteger ou desproteger ficheiros de forma não interativa, adicione a conta de computador relevantes ou contas. Por exemplo, adicione a conta de computador do computador Windows Server que está configurado para a infraestrutura de classificação de ficheiros e usará um script do PowerShell para proteger ficheiros.

9. Na coluna **Permitir**, confirme que as caixas de verificação **Leitura e Execução**e **Leitura** estão selecionadas.

10. Clique em **OK** duas vezes.

### <a name="example-scenarios-for-using-the-cmdlets-for-active-directory-rights-management-services"></a>Cenários de exemplo para utilizar os cmdlets para os Serviços de Gestão de Direitos do Active Directory

Um cenário típico para estes cmdlets é proteger todos os ficheiros numa pasta ao utilizar um modelo de política de direitos ou para desproteger um ficheiro. 

Em primeiro lugar, se tiver mais de uma implementação do AD RMS, precisa dos nomes dos servidores do AD RMS, o que pode fazer ao utilizar o cmdlet Get-RMSServer para apresentar uma lista de servidores disponíveis:

    Get-RMSServer

A saída pode ser semelhante ao seguinte:

    Number of RMS Servers that can provide templates: 2 
    ConnectionInfo             DisplayName          AllowFromScratch
    --------------             -------------        ----------------
    Microsoft.InformationAnd…  RmsContoso                       True
    Microsoft.InformationAnd…  RmsFabrikam                      True

Antes de poder proteger os ficheiros, terá de obter uma lista de modelos do Rights Management para identificar qual utilizar e o número de ID correspondente. Só quando tiver mais do que uma implementação do AD RMS é que tem de especificar também o servidor RMS. 

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

Quando a extensão de nome de ficheiro não é alterada depois da proteção é aplicada, pode sempre utilizar o cmdlet Get-RMSFileStatus mais tarde para verificar se o ficheiro está protegido. Por exemplo: 

    Get-RMSFileStatus -File \\Server1\Documents\Test1.docx

A saída pode ser semelhante ao seguinte:

    FileName                              Status
    --------                              ------
    \\Server1\Documents\Test1.docx        Protected

Para desproteger um ficheiro, tem de ter direitos de utilização de proprietário ou de extração de quando o ficheiro foi protegido ou ser Superutilizador do AD RMS. Em seguida, utilize o cmdlet Desproteger. Por exemplo:

    Unprotect-RMSFile C:\test.docx -InPlace

A saída pode ser semelhante ao seguinte:

    InputFile                             DecryptedFile
    ---------                             -------------
    C:\Test.docx                          C:\Test.docx

## <a name="how-to-label-files-non-interactively-for-azure-information-protection"></a>Como etiquetar ficheiros de forma não interativa para o Azure Information Protection

Pode executar os cmdlets de etiquetagem de forma não interativa através do **Set-AIPAuthentication** cmdlet. Operação não interativa também é necessária para o scanner do Azure Information Protection.

Por predefinição, quando executa os cmdlets de etiquetagem, os comandos são executados no seu próprio contexto de utilizador numa sessão interativa do PowerShell. Para executá-los de modo autónomo, crie uma nova conta de utilizador do Azure AD para este fim. Em seguida, no contexto desse utilizador, execute o cmdlet Set-AIPAuthentication para definir e armazenar credenciais através de um token de acesso do Azure AD. Esta conta de utilizador é, em seguida, autenticada e reiniciada para o serviço Azure Rights Management. A conta transfere a política do Azure Information Protection e quaisquer modelos do Rights Management utilizados pelas etiquetas.

> [!NOTE]
> Se usar [políticas de âmbito](../configure-policy-scope.md), lembre-se de que poderá ter de adicionar esta conta para políticas de âmbito.

Na primeira vez que executar este cmdlet, é pedido que inicie sessão no Azure Information Protection. Especifique o nome de conta de utilizador e palavra-passe que criou para o utilizador autónomo. Em seguida, esta conta pode executar os cmdlets de etiquetagem de forma não interativa até o token de autenticação expirar. 

Para a conta de utilizador conseguir iniciar sessão interativamente pela primeira vez, a conta deve ter o **iniciar sessão localmente** certo. Este direito é o padrão para contas de utilizador, mas as políticas da empresa podem proibir esta configuração para contas de serviço. Se for esse o caso, pode executar Set-AIPAuthentication com o *Token* parâmetro, de modo que a autenticação é concluída sem o pedido de início de sessão. Pode executar este comando como uma tarefa agendada e conceder à conta a parte inferior direita da **iniciar sessão como tarefa batch**. Para obter mais informações, consulte as secções seguintes. 

Quando o token expira, execute o cmdlet novamente para comprar um novo token.

Se executar este cmdlet sem parâmetros, a conta compra um token de acesso que é válido durante 90 dias ou até a sua palavra-passe expirar.  

Para controlar quando o token de acesso expira, execute este cmdlet com parâmetros. Tal permite-lhe configurar o token de acesso para um ano, dois anos ou para nunca expirar. Esta configuração requer que tenha duas aplicações registadas no Azure Active Directory: R **aplicação Web / API** aplicação e um **aplicativo nativo**. Os parâmetros para este cmdlet utilizam valores destas aplicações.

Após ter executado este cmdlet, pode executar os cmdlets de etiquetagem no contexto da conta de utilizador que criou.

### <a name="to-create-and-configure-the-azure-ad-applications-for-set-aipauthentication"></a>Para criar e configurar as aplicações do Azure AD para Set-AIPAuthentication

1. Numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com/).

2. Para o inquilino do Azure AD que utiliza com o Azure Information Protection, navegue para **Azure Active Directory** > **Registos das aplicações**. 

3. Selecione **Novo registo de aplicação** para criar a aplicação Web/aplicação API. Na etiqueta **Criar**, especifique os seguintes valores e, em seguida, clique em **Criar**:

   - Nome: **AIPOnBehalfOf**

     Se preferir, especifique um nome diferente. Tem de ser exclusivo por inquilino.

   - Tipo de aplicação: **Aplicação Web/API**

   - URL de início de sessão: **http://localhost**

4. Selecione a aplicação que acabou de criar, por exemplo, **AIPOnBehalfOf**. Em seguida, no painel **Definições**, selecione **Propriedades**. No painel **Propriedades**, copie o valor para o **ID da Aplicação** e, em seguida, feche este painel. 

    Este valor é utilizado para o parâmetro `WebAppId` quando executa o cmdlet Set-AIPAuthentication. Cole e guarde-o para futura referência.

5. Volta a **definições** painel, selecione **permissões obrigatórias**. Sobre o **permissões obrigatórias** painel, selecione **conceder permissões**, clique em **Sim** para confirmar e, em seguida, feche este painel.

6. Novamente o **configurações** painel mais uma vez, selecione **chaves**. Adicione uma nova chave especificando uma descrição e a sua escolha de duração (1 ano, 2 anos ou nunca expira). Em seguida, selecione **Guardar**e copie a cadeia para o **Valor** que é apresentado. É importante que guarde esta cadeia, uma vez que não é novamente apresentada e não pode obtê-la. Tal como com qualquer chave que utiliza, armazene o valor guardado de forma segura e restrinja o acesso ao mesmo.

    Este valor é utilizado para o parâmetro `WebAppKey` quando executa o cmdlet Set-AIPAuthentication.

7. De novo no painel **Registos das aplicações**, selecione **Novo registo de aplicação** para criar a aplicação nativa. Na etiqueta **Criar**, especifique os seguintes valores e, em seguida, clique em **Criar**:

   - Nome: **AIPClient**

     Se preferir, especifique um nome diferente. Tem de ser exclusivo por inquilino.

   - Tipo de aplicação: **Native**

   - URL de início de sessão: **http://localhost**

8. Selecione a aplicação que acabou de criar, por exemplo, **AIPClient**. Em seguida, no painel **Definições**, selecione **Propriedades**. No painel **Propriedades**, copie o valor para o **ID da Aplicação** e, em seguida, feche este painel.

    Este valor é utilizado para o parâmetro `NativeAppId` quando executa o cmdlet Set-AIPAuthentication. Cole e guarde-o para futura referência.

9. No painel **Definições**, selecione **Permissões obrigatórias**. 

10. No painel **Permissões obrigatórias**, clique em **Adicionar**e, de seguida, em **Selecionar uma API**. Na caixa de pesquisa, escreva **AIPOnBehalfOf**. Selecione este valor na caixa de listagem e, em seguida, clique em **Selecionar**.

11. No painel **Ativar Acesso**, selecione **AIPOnBehalfOf**, clique em **Selecionar**e, de seguida, em **Concluído**.

12. Volta a **permissões obrigatórias** painel, selecione **conceder permissões**, clique em **Sim** para confirmar e, em seguida, feche este painel.


Concluiu agora a configuração das duas aplicações e tem os valores que precisa executar [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) com os parâmetros *WebAppId*, *WebAppKey* e *NativeAppId*. Por exemplo:

`Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f"`

Execute este comando no contexto da conta que irá identificar e proteger os documentos de forma não interativa. Por exemplo, uma conta de utilizador para os scripts do PowerShell ou a conta de serviço para executar o scanner do Azure Information Protection.  

Quando executar este comando pela primeira vez, lhe for pedido para iniciar sessão, que cria e armazena com segurança o token de acesso para a sua conta % localappdata%\Microsoft\MSIP. Depois deste inicial início de sessão, pode Etiquetar e proteger ficheiros de forma não interativa no computador. No entanto, o se utilizar uma conta de serviço para identificar e proteger ficheiros e esta conta de serviço não pode iniciar sessão interativamente, utilize as instruções na secção seguinte para que a conta de serviço pode ser autenticado através de um token.

### <a name="specify-and-use-the-token-parameter-for-set-aipauthentication"></a>Especificar e utilizar o parâmetro de Token para Set-AIPAuthentication

Utilize os seguintes passos adicionais e as instruções para evitar o inicial interativo início de sessão para uma conta que etiquetas e protege os arquivos. Normalmente, estes são necessários passos adicionais apenas se esta conta não é possível conceder a **iniciar sessão localmente** com o botão direito, mas é concedida a **iniciar sessão como uma tarefa do batch** certo. Por exemplo, isso pode ser o caso para a sua conta de serviço que executa o scanner do Azure Information Protection.

Passos de alto nível:

1. Crie um script do PowerShell no seu computador local.

2. Execute Set-AIPAuthentication para obter um acesso de token e copie-o para a área de transferência.

3. Modificar o script do PowerShell para incluir o token.

4. Crie uma tarefa que executa o script do PowerShell no contexto da conta de serviço que será Etiquetar e proteger ficheiros.

5. Confirme que o token é guardado para a conta de serviço e eliminar o script do PowerShell.

#### <a name="step-1-create-a-powershell-script-on-your-local-computer"></a>Passo 1: Criar um script do PowerShell no seu computador local

1. No seu computador, crie um novo script de PowerShell chamado Aipauthentication.ps1.

2. Copie e cole o seguinte comando para este script:

         Set-AIPAuthentication -WebAppId <ID of the "Web app / API" application> -WebAppKey <key value generated in the "Web app / API" application> -NativeAppId <ID of the "Native" application > -Token <token value>

3. Com as instruções na secção anterior, modifique este comando, especificando os seus próprios valores para o **WebAppId**, **WebAppkey**, e **NativeAppId** parâmetros. Neste momento, não tem o valor para o **Token** parâmetro, que pode especificar mais tarde. 

    Por exemplo: `Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f -Token <token value>`

#### <a name="step-2-run-set-aipauthentication-to-get-an-access-token-and-copy-it-to-the-clipboard"></a>Passo 2: Execute Set-AIPAuthentication para obter um acesso de token e copie-o para a área de transferência

1. Abra uma sessão do Windows PowerShell.

2. Utilizar os mesmos valores especificados no script, execute o seguinte comando:

        (Set-AIPAuthentication -WebAppId <ID of the "Web app / API" application>  -WebAppKey <key value generated in the "Web app / API" application> -NativeAppId <ID of the "Native" application >).token | clip

    Por exemplo: `(Set-AIPAuthentication -WebAppId "57c3c1c3-abf9-404e-8b2b-4652836c8c66" -WebAppKey "sc9qxh4lmv31GbIBCy36TxEEuM1VmKex5sAdBzABH+M=" -NativeAppId "8ef1c873-9869-4bb1-9c11-8313f9d7f76f").token | clip`

#### <a name="step-3-modify-the-powershell-script-to-supply-the-token"></a>Passo 3: Modificar o script do PowerShell para fornecer o token

1. No seu script de PowerShell, especifique o valor do token ao colar a cadeia de caracteres da área de transferência e guarde o ficheiro.

2. Assine o script. Se não assinar o script (mais seguro), tem de configurar o Windows PowerShell no computador que irá executar os comandos de etiquetas. Por exemplo, executar uma sessão do Windows PowerShell com o **executar como administrador** opção e tipo: `Set-ExecutionPolicy RemoteSigned`. No entanto, esta configuração permite que scripts tudo não assinados executados quando eles são armazenados neste computador (menos seguro).

    Para obter mais informações sobre como assinar os scripts do Windows PowerShell, veja [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing) na biblioteca de documentação do PowerShell.

3. Copie este script do PowerShell para o computador que irá Etiquetar e proteger ficheiros e eliminar o original no seu computador. Por exemplo, copie o script do PowerShell para C:\Scripts\Aipauthentication.ps1 num computador Windows Server.

#### <a name="step-4-create-a-task-that-runs-the-powershell-script"></a>Passo 4: Criar uma tarefa que executa o script do PowerShell

1. Certifique-se de que a conta de serviço que será Etiquetar e proteger ficheiros tem o **iniciar sessão como uma tarefa do batch** certo.

2. No computador que irá identificar e proteger ficheiros, abra o agendador de tarefas e criar uma nova tarefa. Configure esta tarefa para ser executado como conta de serviço que será Etiquetar e proteger ficheiros e, em seguida, configure os seguintes valores para o **ações**:

   - **Ação**: `Start a program`
   - **Programa/script**: `Powershell.exe`
   - **Adicione argumentos (opcional)**: `-NoProfile -WindowStyle Hidden -command "&{C:\Scripts\Aipauthentication.ps1}"` 

     Para a linha de argumento, especifique o seu próprio nome de ficheiro e caminho, se estes são diferentes do exemplo.

3. Executar manualmente esta tarefa.

#### <a name="step-4-confirm-that-the-token-is-saved-and-delete-the-powershell-script"></a>Passo 4: Confirme que o token é guardado e eliminar o script do PowerShell

1. Confirme que o token agora é armazenado na pasta %localappdata%\Microsoft\MSIP para o perfil de conta de serviço. Este valor está protegido pela conta de serviço.

2. Elimine o script do PowerShell que contém o valor do token (por exemplo, Aipauthentication.ps1).

    Opcionalmente, elimine a tarefa. Se o token expirar, terá de repetir este processo, nesse caso, poderá ser mais conveniente deixar a tarefa configurada para que fique pronto para voltar a executar quando copia sobre o novo PowerShell script com o novo valor de token.

## <a name="next-steps"></a>Passos Seguintes
Para obter a ajuda do cmdlet quando estiver numa sessão do PowerShell, escreva `Get-Help <cmdlet name> cmdlet` e utilize o parâmetro online para ler as informações mais atualizadas. Por exemplo: 

    Get-Help Get-RMSTemplate -online

Veja o seguinte para obter informações adicionais que poderá precisar para suportar o cliente do Azure Information Protection:

- [Personalizações](client-admin-guide-customizations.md)

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)


