---
title: A sua chave de inquilino do Azure Information Protection
description: Informações para o ajudar a planear e gerir a sua chave de inquilino do Azure Information Protection. Em vez de a sua chave de inquilino ser gerida pela Microsoft (predefinição), poderá querer gerir a sua própria chave de inquilino para cumprir os regulamentos específicos que se aplicam à sua organização. A gestão da sua própria chave de inquilino também é referida como Bring Your Own Key (Traga a Sua Própria Chave) ou BYOK.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/26/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 05aee77b60b5fd5a7239b51665e2afb122704afb
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491320"
---
# <a name="planning-and-implementing-your-azure-information-protection-tenant-key"></a>Planear e implementar a sua chave de inquilino do Azure Information Protection

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize as informações deste artigo para o ajudar a planear e gerir a sua chave de inquilino do Azure Information Protection. Por exemplo, em vez de a sua chave de inquilino ser gerida pela Microsoft (predefinição), poderá querer gerir a sua própria chave de inquilino para cumprir os regulamentos específicos que se aplicam à sua organização. A gestão da sua própria chave de inquilino também é referida como Bring Your Own Key (Traga a Sua Própria Chave) ou BYOK.

O que é a chave de inquilino do Azure Information Protection?

- A chave de inquilino do Azure Information Protection é uma chave de raiz para a sua organização. Outras chaves podem derivar desta chave de raiz, como chaves de utilizador, chaves de computador e as chaves de encriptação de documentos. Sempre que o Azure Information Protection utiliza estas chaves para a sua organização, eles criptograficamente à sua chave de inquilino do Azure Information Protection.

- A chave de inquilino do Azure Information Protection é o equivalente online da chave do certificado de licenciante para servidor (SLC) do Active Directory Rights Management Services (AD RMS). 

**Resumindo:** utilize a seguinte tabela como um guia rápido para a sua topologia de chaves de inquilino recomendada. Em seguida, utilize a documentação adicional para obter mais informações.

|Necessidade comercial|Topologia de chaves de inquilino recomendada|
|------------------------|-----------------------------------|
|Implemente o Azure Information Protection rapidamente e sem hardware especial, software adicional ou uma subscrição do Azure.<br /><br />Por exemplo: testar ambientes e quando a sua organização não tem os requisitos regulamentares de gestão de chaves.|Gerida pela Microsoft|
|Normas de conformidade, segurança adicional e controle sobre todas as operações de ciclo de vida. <br /><br />Por exemplo: A chave deve ser protegida por um módulo de segurança de hardware (HSM).|BYOK [[1]](#footnote-1)|


Se for necessário, pode alterar a topologia da sua chave de inquilino após a implementação, utilizando o cmdlet [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties).


## <a name="choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok"></a>Selecione a sua topologia de chaves de inquilino: gerida pela Microsoft (predefinição) ou gerida por si (BYOK)
Decida que topologia de chaves de inquilino é melhor para a sua organização. Por predefinição, o Azure Information Protection gera a sua chave de inquilino e gere a maioria dos aspetos do ciclo de vida da chave de inquilino. Esta é a opção mais simples e com menos tarefas administrativas adicionais. Na maioria dos casos, nem precisa de saber que tem uma chave de inquilino. Basta inscrever-se no Azure Information Protection e o processo de gestão de chaves restante será processado pela Microsoft.

Decida que topologia de chave de inquilino é melhor para sua organização:

- **Gerida pela Microsoft**: Microsoft gera automaticamente uma chave de inquilino para a sua organização e esta chave é usada exclusivamente para o Azure Information Protection. Por predefinição, a Microsoft utiliza esta chave para o seu inquilino e gere a maioria dos aspetos do seu ciclo de vida de chave de inquilino. 
    
    Esta é a opção mais simples e com menos tarefas administrativas adicionais. Na maioria dos casos, nem precisa de saber que tem uma chave de inquilino. Basta inscrever-se no Azure Information Protection e o processo de gestão de chaves restante será processado pela Microsoft.

- **Gerido por si (BYOK)**: para obter controle completo sobre a sua chave de inquilino, utilize [do Azure Key Vault](https://azure.microsoft.com/services/key-vault/) com o Azure Information Protection. Para esta topologia de chave de inquilino, criar a chave, diretamente no Key Vault, ou criá-lo no local. Se criá-lo no local, seguinte transfere ou importar esta chave para o Cofre de chaves. Em seguida, configure o Azure Information Protection para utilizar esta chave, e geri-la no Azure Key Vault.
    

### <a name="more-information-about-byok"></a>Obter mais informações sobre o BYOK
Para criar sua própria chave, tem as seguintes opções:

- **Uma chave que criar no local e transferir ou importar para o Key Vault**:
    
    - Uma chave protegida por HSM que criar no local e transferir para o Cofre de chave como uma chave protegida por HSM.
    
    - Uma chave protegida por software que criar no local, converter e, em seguida, transferir para o Cofre de chave como uma chave protegida por HSM. Esta opção é suportada apenas quando [migrar a partir do Active Directory Rights Management Services (AD RMS)](migrate-from-ad-rms-to-azure-rms.md).
    
    - Uma chave protegida por software que criar no local e importar para o Cofre de chaves como uma chave protegida por software. Esta opção requer um. Ficheiro de certificado PFX.
    
- **Uma chave que criar no Key Vault**:
    
    - Uma chave protegida por HSM que criar no Key Vault.
    
    - Uma chave protegida por software que criar no Key Vault.

Uma destas opções do BYOK, o mais comum é uma chave protegida por HSM que criar no local e transferir para o Cofre de chave como uma chave protegida por HSM. Embora esta opção tem as maiores tarefas administrativas adicionais, poderá ser necessário para a sua organização estar em conformidade com regulamentos específicos. Os HSMs que são utilizados pelo Azure Key Vault têm a certificação FIPS 140-2 de nível 2 validada.

Quando esta opção é selecionada, ocorre o seguinte:

1. Gera a chave de inquilino no local, de acordo com as suas políticas de TI e de segurança. Esta chave é a cópia principal. Permanece no local e é responsável por realizar cópias de segurança.

2. Criar uma cópia desta chave e transfere com segurança esta cópia do seu HSM para o Azure Key Vault. Ao longo deste processo, a cópia principal desta chave nunca sai do limite de proteção de hardware.

3. A cópia da chave está protegida pelo Azure Key Vault.

> [!NOTE]

> Como medida de proteção adicional, o Azure Key Vault utiliza domínios de segurança separados nos seus centros de dados em regiões como a América do Norte, EMEA (Europa, Médio Oriente e África) e Ásia. O Azure Key Vault também utiliza diferentes instâncias do Azure, como o Microsoft Azure Alemanha e o Azure Government. 

Embora seja opcional, provavelmente também irá querer utilizar os registos de utilização quase em tempo real do Azure Information Protection, para saber exatamente como e quando a sua chave de inquilino está a ser utilizada.

### <a name="when-you-have-decided-your-tenant-key-topology"></a>Quando tenha decidido a topologia de chave de inquilino

Se optar por permitir que a Microsoft gerir a sua chave de inquilino: 

- A menos que estiver a migrar do AD RMS, nenhuma ação adicional é necessária para a gerar a chave para o seu inquilino e pode ir diretamente para [próximos passos](plan-implement-tenant-key.md#next-steps).

- Se atualmente tiver o AD RMS e quiser migrar para o Azure Information Protection, utilize as instruções de migração: migração do AD RMS para o Azure Information Protection. 

Se optar por gerir a sua chave de inquilino, leia as secções seguintes para obter mais informações.

## <a name="implementing-byok-for-your-azure-information-protection-tenant-key"></a>Implementar o BYOK para a sua chave de inquilino do Azure Information Protection

Utilize as informações e os procedimentos desta secção, se tiver decidido gerar e gerir a sua chave de inquilino – o cenário BYOK (Bring Your Own Key – Traga a Sua Própria Chave):

> [!NOTE]
> Se tiver começado a utilizar o Azure Information Protection com uma chave de inquilino gerida pela Microsoft e quiser agora gerir a sua chave de inquilino (mudar para o BYOK), os seus documentos e e-mails anteriormente protegidos continuarão acessíveis através da utilização de uma chave arquivada. 

### <a name="prerequisites-for-byok"></a>Pré-requisitos para o BYOK
Consulte a seguinte tabela para obter uma lista de pré-requisitos para o BYOK (Bring Your Own Key – Traga a Sua Própria Chave).

|Requisito|Mais informações|
|---------------|--------------------|
|O inquilino do Azure Information Protection tem de ter uma subscrição do Azure. Se não tiver uma, pode inscrever-se para obter um [conta gratuita](https://azure.microsoft.com/pricing/free-trial/). <br /><br /> Para utilizar uma chave protegida por HSM, tem de ter a camada de serviços do Azure Key Vault Premium.|A subscrição gratuita do Azure que fornece acesso para configurar o Azure Active Directory e a configuração dos modelos personalizados do Azure Rights Management (**Aceder ao Azure Active Directory**) não são suficientes para utilizar o Azure Key Vault. Para confirmar se tem uma subscrição do Azure que pode utilizar para o BYOK, utilize os cmdlets [Azure Resource Manager](https://msdn.microsoft.com/library/azure/mt786812\(v=azure.300\).aspx) do PowerShell: <br /><br /> 1. Inicie uma sessão do PowerShell do Azure com a opção **Executar como administrador** e inicie sessão como um administrador global do seu inquilino do Azure Information Protection com o seguinte comando: `Login-AzureRmAccount`<br /><br />2. Escreva o que se segue e confirme se os valores apresentados para o nome e ID da sua subscrição, o ID do seu inquilino do Azure Information Protection e o estado estão ativos: `Get-AzureRmSubscription`<br /><br />Se não forem apresentados valores e regressar ao pedido, significa que não tem uma subscrição do Azure que possa ser utilizada para o BYOK. <br /><br />**Nota**: além dos pré-requisitos para BYOK, se estiver a migrar do AD RMS para o Azure Information Protection através da utilização de chave de software para chave de hardware, tem de ter uma versão de firmware da Thales igual ou superior à 11.62.|
|Para utilizar uma chave protegida por HSM que criar no local: <br /><br />-Todos os pré-requisitos listados para BYOK do Cofre de chaves. |Veja [Pré-requisitos para BYOK](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok) na documentação do Azure Key Vault. <br /><br /> **Nota**: além dos pré-requisitos para BYOK, se estiver a migrar do AD RMS para o Azure Information Protection através da utilização de chave de software para chave de hardware, tem de ter uma versão de firmware da Thales igual ou superior à 11.62.|
|Se o Cofre de chaves para conter a chave de inquilino utiliza pontos finais de serviço de rede Virtual para o Key Vault (atualmente em pré-visualização): <br /><br />-Selecione a opção para permitir que os serviços Microsoft fidedignos contornem esta firewall.|Para obter mais informações, consulte [anunciando Virtual rede pontos finais de serviço para o Key Vault (pré-visualização)](https://blogs.technet.microsoft.com/kv/2018/06/25/announcing-virtual-network-service-endpoints-for-key-vault-preview/).|
|O módulo de administração do Azure Rights Management para o Windows PowerShell.|Para obter instruções de instalação, consulte [instalar o módulo do PowerShell do AADRM](./install-powershell.md). <br /><br />Caso já tenha instalado este módulo do Windows PowerShell, execute o seguinte comando para verificar se o seu número de versão é, pelo menos, **2.9.0.0**: `(Get-Module aadrm -ListAvailable).Version`|

Para obter mais informações sobre HSMs da Thales e como são utilizados com o Azure Key Vault, consulte o [site da Thales](https://www.thales-esecurity.com/msrms/cloud).

### <a name="choosing-your-key-vault-location"></a>Escolher a localização do Cofre de chaves

Quando cria um cofre de chaves para conter a chave a ser utilizado como a chave de inquilino para obter informações do Azure, tem de especificar uma localização. Esta localização é uma região do Azure, ou instância do Azure.

Tornar a sua primeira choice de conformidade e, em seguida, para minimizar a latência de rede:

- Se tiver escolhido a topologia de chave de BYOK por motivos de conformidade, esses requisitos de conformidade podem impor a região do Azure ou a instância do Azure que armazena a chave de inquilino do Azure Information Protection.

- Uma vez que todas as chamadas de criptografia para a proteção da cadeia para a chave de inquilino do Azure Information Protection, deseja minimizar a latência de rede que essas chamadas incorrem. Para fazer isso, crie o seu Cofre de chaves na mesma região do Azure ou instância como seu inquilino do Azure Information Protection.

Para identificar a localização do seu inquilino do Azure Information Protection, utilize o [Get-AadrmConfiguration](/powershell/module/aadrm/get-aadrmconfiguration) cmdlet do PowerShell e a identificar a região a partir dos URLs. Por exemplo:

    LicensingIntranetDistributionPointUrl : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing

A região é a identificação da **rms.na.aadrm.com**, e para este exemplo, é na América do Norte.

Utilize a seguinte tabela para identificar qual instância ou região do Azure, é recomendada para minimizar a latência de rede.

|Instância ou região do Azure|Localização recomendada para o seu Cofre de chaves|
|---------------|--------------------|
|rms.**na**.aadrm.com|**Centro-Norte** ou **E.U.A. leste**|
|rms.**eu**.aadrm.com|**Europa do Norte** ou **Europa Ocidental**|
|rms.**ap**.aadrm.com|**Ásia Oriental** ou **Sudeste asiático**|
|rms.**sa**.aadrm.com|**E.U.A. oeste** ou **E.U.A. leste**|
|rms.**govus**.aadrm.com|**Centro dos E.U.A.** ou **E.U.A. Leste 2**|


### <a name="instructions-for-byok"></a>Instruções para BYOK

Utilize a documentação do Azure Key Vault para criar um cofre de chaves e a chave de que pretende utilizar para o Azure Information Protection. Por exemplo, veja [introdução ao Azure Key Vault](/azure/key-vault/key-vault-get-started).

Certifique-se de que o comprimento da chave é 2048 bits (recomendados) ou de 1024 bits. Outros comprimentos de chave não são suportados pelo Azure Information Protection.

Para criar um protegida por HSM chave no local e transferi-la para o seu Cofre de chaves como uma chave protegida por HSM, siga os procedimentos [como gerar e transferir chaves protegidas por HSM para o Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/).

Uma chave armazenada no Cofre de chaves tem uma chave de ID. Esta chave de ID é um URL que contém o nome do Cofre de chaves, o contentor de chaves, o nome da chave e a versão da chave. Por exemplo: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Tem de configurar o Azure Information Protection para utilizar esta chave, especificando o URL do Key Vault.

Antes de utilizar a chave do Azure Information Protection, o serviço Azure Rights Management tem de estar autorizado a utilizar a chave no Cofre de chaves da sua organização. Para tal, o administrador do Azure Key Vault utiliza o cmdlet do PowerShell do Key Vault [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) e concede permissões ao principal de serviço do Azure Rights Management ao utilizar o GUID 00000012-0000-0000-c000-000000000000. Por exemplo:

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,sign,get

Agora está pronto para configurar o Azure Information Protection para utilizar esta chave como chave de inquilino do Azure Information Protection da sua organização. Através dos cmdlets do Azure RMS, ligue primeiro ao serviço Azure Rights Management e inicie sessão:

    Connect-AadrmService

Em seguida, execute o [cmdlet Use-AadrmKeyVaultKey](/powershell/module/aadrm/use-aadrmkeyvaultkey) e especifique o URL da chave. Por exemplo:

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

> [!IMPORTANT]
> Neste exemplo, "aaaabbbbcccc111122223333" é a versão da chave a utilizar. Se não especificar a versão, a versão atual da chave é utilizada sem aviso e o comando parece funcionar. No entanto, se a chave no Cofre de Chaves for atualizada mais tarde (renovada), o serviço Azure Rights Management deixará de funcionar para o seu inquilino, mesmo que execute novamente o comando Use-AadrmKeyVaultKey.
>
>Quando executar este comando, certifique-se de que especifica a versão da chave, bem como o nome da chave. Pode utilizar o comando do Azure Key Vault ([Get-AzureKeyVaultKey](/powershell/module/azurerm.keyvault\get-azurekeyvaultkey)) para obter o número da versão da chave atual. Por exemplo: `Get-AzureKeyVaultKey -VaultName 'contosorms-kv' -KeyName 'contosorms-byok'`

Se tiver de confirmar que a chave de URL está definida corretamente para o Azure Information Protection: no Azure Key Vault, execute [Get-AzureKeyVaultKey](/powershell/module/azurerm.keyvault\get-azurekeyvaultkey) para ver a chave de URL.

Por fim, se o serviço Azure Rights Management já estiver ativado, execute [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) para dizer ao Azure Information Protection para utilizar esta chave como chave de inquilino ativa para o serviço Azure Rights Management. Se não efetuar este passo, o Azure Information Protection irá continuar a utilizar a chave de gerida pela Microsoft de predefinida, que foi criada automaticamente para o seu inquilino.


## <a name="next-steps"></a>Passos Seguintes

Agora que já planeou e, se necessário, criado e configurado a sua chave de inquilino, faça o seguinte:

1.  Comece a utilizar a sua chave de inquilino:
    
    - Se ainda não o fez, tem agora de ativar o serviço de Gestão de Direitos para que a sua organização possa começar a utilizar o Azure Information Protection. Os utilizadores imediatamente começam a utilizar a sua chave de inquilino (gerida pela Microsoft ou gerida por si no Azure Key Vault).
    
        Para obter mais informações sobre a ativação, consulte [Ativar o Azure Rights Management](./activate-service.md).
        
    - Se já tinha ativado o serviço Gestão de Direitos e depois decidiu gerir a sua própria chave de inquilino, a transição dos utilizadores da chave de inquilino antiga para a nova chave de inquilino será efetuada gradualmente. A conclusão desta transição escalonada poderá demorar algumas semanas. Os documentos e ficheiros que foram protegidos com a chave de inquilino antiga permanecem acessíveis aos utilizadores autorizados.
        
2. Pondere utilizar registos de utilização, que lhe permitem registar todas as transações efetuadas pelo serviço Azure Rights Management.
    
    Se decidiu gerir a sua própria chave de inquilino, o registo incluirá informações sobre como utilizar a sua chave de inquilino. Veja o seguinte fragmento de um ficheiro de registo apresentado no Excel onde os tipos de pedido **KeyVaultDecryptRequest** e **KeyVaultSignRequest** mostram que a chave de inquilino está a ser utilizada.
    
    ![ficheiro de registo no Excel onde a chave de inquilino está a ser utilizada](./media/RMS_Logging.png)
    
    Para obter mais informações sobre o registo de utilização, consulte [Registar e analisar a utilização do serviço Azure Rights Management](./log-analyze-usage.md).
    
3.  Gerir a sua chave de inquilino.
    
    Para obter mais informações sobre as operações de ciclo de vida para a sua chave de inquilino, consulte [operações para a chave de inquilino do Azure Information Protection](./operations-tenant-key.md).
