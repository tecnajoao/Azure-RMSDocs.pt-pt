---
title: "Migrar chave protegida por HSM para chave protegida por HSM – AIP"
description: "Instruções que fazem parte do caminho de migração do AD RMS para o Azure Information Protection e só são aplicáveis se a sua chave do AD RMS estiver protegida por HSM e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por HSM no Azure Key Vault."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 936b6e66c7ca0f94e437b91847166b51cf939b3f
ms.sourcegitcommit: 384461f0e3fccd73cd7eda3229b02e51099538d4
translationtype: HT
---
# <a name="step-2-hsm-protected-key-to-hsm-protected-key-migration"></a>Passo 2: migração de chave protegida por HSM para chave protegida por HSM

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection*


Estas instruções fazem parte do [caminho de migração do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) e só são aplicáveis se a sua chave do AD RMS estiver protegida por HSM e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por HSM no Azure Key Vault. 

Se este não for o cenário de configuração escolhido, regresse ao [Passo 4. Exporte os dados de configuração do AD RMS, importe-os para o Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) e escolha uma configuração diferente.

> [!NOTE]
> Estas instruções partem do princípio de que a sua chave do AD RMS está protegida por um módulo. Este é o caso mais habitual. 

A importação da sua chave HSM e da configuração do AD RMS para o Azure Information Protection é feita em duas partes, de forma a resultar na chave de inquilino do Azure Information Protection gerida por si (BYOK).

Uma vez que a chave de inquilino do Azure Information Protection será armazenada e gerida pelo Azure Key Vault, esta parte da migração requer administração no Azure Key Vault, além do Azure Information Protection. Se o Azure Key Vault for gerido por um administrador diferente de si para a sua organização, irá precisar de coordenar e trabalhar com esse administrador para concluir estes procedimentos.

Antes de começar, certifique-se de que a sua organização tem um cofre de chaves criado no Azure Key Vault e que suporta chaves protegidas por HSM. Embora não seja necessário, recomendamos que tenha um cofre de chaves dedicado para o Azure Information Protection. Este cofre de chaves será configurado de forma a permitir que o serviço Azure Rights Management aceda ao mesmo, pelo que este cofre de chaves deve armazenar apenas chaves do Azure Information Protection.


> [!TIP]
> Se for efetuar os passos de configuração do Azure Key Vault e não estiver familiarizado com este serviço do Azure, poderá considerar útil primeiro rever [Introdução ao Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/). 


## <a name="part-1-transfer-your-hsm-key-to-azure-key-vault"></a>Parte 1: transferir a chave HSM para o Azure Key Vault

Estes procedimentos são efetuados pelo administrador para o Azure Key Vault.

1.  Siga as instruções da documentação do Azure Key Vault, utilizando [Implementar o BYOK (Bring Your Own Key – Traga a Sua Própria Chave)](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) com a seguinte exceção:

    - Não efetue os passos para **Gerar a chave de inquilino**, porque já tem o equivalente da sua implementação do AD RMS. Em vez disso, identifique a chave utilizada pelo servidor do AD RMS na instalação da Thales e utilize esta chave durante a migração. Os ficheiros de chave encriptados da Thales são normalmente denominados **key<*keyAppName*><*keyIdentifier*>** localmente no servidor.

    Quando a chave é carregada para o Azure Key Vault, pode ver as respetivas propriedades apresentadas, incluindo o ID da chave. Terá um aspeto semelhante a https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Tome nota deste URL, porque o administrador do Azure Information Protection irá precisar dele para indicar ao serviço Azure Rights Management que utilize esta chave para a respetiva chave de inquilino.

2. Na estação de trabalho com ligação à Internet, numa sessão do PowerShell, utilize o cmdlet [Set-AzureRmKeyVaultAccessPolicy](/powershell/resourcemanager/azurerm.keyvault/v2.7.0/set-azurermkeyvaultaccesspolicy) para autorizar o principal do serviço Azure Rights Management para aceder ao cofre de chaves que armazenará a chave de inquilino do Azure Information Protection. As permissões necessárias são decrypt, encrypt, unwrapkey, wrapkey, verify e sign.
    
    Por exemplo, se o cofre de chaves que criou para o Azure Information Protection tiver o nome contoso-byok-ky e o grupo de recursos tiver o nome contoso-byok-rg, execute o seguinte comando:
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get


Agora que já preparou a sua chave HSM no Azure Key Vault para o serviço Azure Rights Management do Azure Information Protection, está pronto para importar os dados de configuração do AD RMS.

## <a name="part-2-import-the-configuration-data-to-azure-information-protection"></a>Parte 2: importar os dados de configuração para o Azure Information Protection

Estes procedimentos são efetuados pelo administrador para o Azure Information Protection.

1.  Na estação de trabalho ligada à Internet e na sessão do PowerShell, ligue ao serviço Azure Rights Management com o cmdlet [Connnect AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice).
    
    Em seguida, carregue o primeiro ficheiro de domínio de publicação fidedigno exportado (.xml) utilizando o cmdlet [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd). Se tiver mais do que um ficheiro .xml, porque tinha vários domínios de publicação fidedignos, escolha o ficheiro que contém o domínio de publicação fidedigno exportado que corresponde à chave de HSM que pretende utilizar no Azure RMS para proteger o conteúdo após a migração. 
    
    Para executar este cmdlet, precisará do URL para a chave identificada no passo anterior.
    
    Por exemplo, utilizando o nosso valor de URL da chave do passo anterior e um ficheiro TDP de C:\contoso-tpd1.xml, executaria:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```
    
    Quando for solicitado, introduza a palavra-passe que especificou anteriormente e confirme que pretende efetuar esta ação.

2.  Quando o comando for concluído, repita o passo 1 para cada ficheiro .xml restante que criou ao exportar os seus domínios de publicação fidedignos. Por exemplo, deverá ter pelo menos um ficheiro adicional para importar se tiver atualizado o seu cluster AD RMS para o Modo Criptográfico 2. No entanto, para esses ficheiros, defina **-Active** para **false** ao executar o comando Import.  

3.  Utilize o cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) para desligar do serviço Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Se tiver de confirmar mais tarde qual a chave de inquilino do Azure Information Protection utilizada no Azure Key Vault, utilize o cmdlet [Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys) do Azure RMS.

Agora está pronto para ir para o [Passo 5. Ative o seu inquilino do Azure Information Protection](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
