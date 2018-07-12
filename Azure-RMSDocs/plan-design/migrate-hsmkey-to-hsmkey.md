---
title: Migrar chave protegida por HSM para chave protegida por HSM – AIP
description: Instruções que fazem parte do caminho de migração do AD RMS para o Azure Information Protection e só são aplicáveis se a sua chave do AD RMS estiver protegida por HSM e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por HSM no Azure Key Vault.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 757b3af36fb15c3069c5bef7ca4509ff92cee1f9
ms.sourcegitcommit: 0fda9ea4a7b91d4bb3a9e4f9d5cc4106ce1e2d43
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38973329"
---
# <a name="step-2-hsm-protected-key-to-hsm-protected-key-migration"></a>Passo 2: migração de chave protegida por HSM para chave protegida por HSM

>*Aplica-se a: serviços de gestão de direitos do Active Directory [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*


Estas instruções fazem parte do [caminho de migração do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) e só são aplicáveis se a sua chave do AD RMS estiver protegida por HSM e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por HSM no Azure Key Vault. 

Se este não for o cenário de configuração escolhido, regresse ao [Passo 4. Exporte os dados de configuração do AD RMS, importe-os para o Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) e escolha uma configuração diferente.

> [!NOTE]
> Estas instruções partem do princípio de que a sua chave do AD RMS está protegida por um módulo. Este é o caso mais habitual. 

A importação da sua chave HSM e da configuração do AD RMS para o Azure Information Protection é feita em duas partes, de forma a resultar na chave de inquilino do Azure Information Protection gerida por si (BYOK).

Uma vez que a chave de inquilino do Azure Information Protection será armazenada e gerida pelo Azure Key Vault, esta parte da migração requer administração no Azure Key Vault, além do Azure Information Protection. Se o Azure Key Vault da sua organização for gerido por um administrador diferente de si, tem de se coordenar e trabalhar com esse administrador para concluir estes procedimentos.

Antes de começar, certifique-se de que a sua organização tem um cofre de chaves criado no Azure Key Vault e que suporta chaves protegidas por HSM. Embora não seja necessário, recomendamos que tenha um cofre de chaves dedicado para o Azure Information Protection. Este cofre de chaves será configurado de forma a permitir que o serviço Azure Rights Management aceda ao mesmo, pelo que este cofre de chaves deve armazenar apenas chaves do Azure Information Protection.


> [!TIP]
> Se for efetuar os passos de configuração do Azure Key Vault e não estiver familiarizado com este serviço do Azure, poderá considerar útil primeiro rever [Introdução ao Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/). 


## <a name="part-1-transfer-your-hsm-key-to-azure-key-vault"></a>Parte 1: transferir a chave HSM para o Azure Key Vault

Estes procedimentos são efetuados pelo administrador para o Azure Key Vault.

1. Para cada chave SLC exportada que pretende armazenar no Azure Key Vault, siga as instruções apresentadas na secção [Implementing bring your own key (BYOK) for Azure Key Vault (Implementar o BYOK (Bring Your Own Key – Traga a sua Própria Chave))](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azurekey-vault) da documentação do Azure Key Vault, com a seguinte exceção:

    - Não efetue os passos para **Gerar a chave de inquilino**, porque já tem o equivalente da sua implementação do AD RMS. Em vez disso, identifique a chave utilizada pelo servidor do AD RMS na instalação da Thales e utilize esta chave durante a migração. Ficheiros de chave encriptados são normalmente denominados de Thales **key <*keyAppName*><*keyIdentifier* >**  localmente no servidor.

    Quando a chave é carregada para o Azure Key Vault, pode ver as propriedades da chave apresentadas, incluindo o ID da chave. Ela terá um aspeto semelhante ao https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Tome nota deste URL, porque o administrador do Azure Information Protection irá precisar dele para indicar ao serviço Azure Rights Management que utilize esta chave para a respetiva chave de inquilino.

2. Na estação de trabalho com ligação à Internet, numa sessão do PowerShell, utilize o cmdlet [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) para autorizar o principal do serviço Azure Rights Management para aceder ao cofre de chaves que armazenará a chave de inquilino do Azure Information Protection. As permissões necessárias são decrypt, encrypt, unwrapkey, wrapkey, verify e sign.
    
    Por exemplo, se o cofre de chaves que criou para o Azure Information Protection tiver o nome contoso-byok-ky e o grupo de recursos tiver o nome contoso-byok-rg, execute o seguinte comando:
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get


Agora que já preparou a sua chave HSM no Azure Key Vault para o serviço Azure Rights Management do Azure Information Protection, está pronto para importar os dados de configuração do AD RMS.

## <a name="part-2-import-the-configuration-data-to-azure-information-protection"></a>Parte 2: importar os dados de configuração para o Azure Information Protection

Estes procedimentos são efetuados pelo administrador para o Azure Information Protection.

1. Na estação de trabalho ligada à Internet e na sessão do PowerShell, ligue ao serviço Azure Rights Management com o cmdlet [Connnect AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice).
    
    Em seguida, carregue cada ficheiro de domínio de publicação fidedigno exportado (.xml) com o cmdlet [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd). Por exemplo, deverá ter pelo menos um ficheiro adicional para importar se tiver atualizado o seu cluster AD RMS para o Modo Criptográfico 2.
    
    Para executar este cmdlet, precisará da palavra-passe que especificou anteriormente para cada ficheiro de dados de configuração e o URL da chave que foi identificada no passo anterior.
    
    Por exemplo, através de um ficheiro de dados de configuração de C:\contoso-tpd1.xml e do nosso valor de URL da chave do passo anterior, execute primeiro o seguinte para armazenar a palavra-passe:
    
    ```
    $TPD_Password = Read-Host -AsSecureString
    ```
    
    Introduza a palavra-passe que especificou para exportar o ficheiro de dados de configuração. Em seguida, execute o seguinte comando e confirme que pretende realizar esta ação:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword $TPD_Password –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Verbose
    ```
    
    Como parte desta importação, a chave SLC é importada e definida automaticamente como arquivada.

2.  Depois de carregar todos os ficheiros, execute [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) para especificar a chave importada que corresponde à chave SLC atualmente ativa no cluster do AD RMS. Esta chave tornar-se-á a chave de inquilino ativa para o seu serviço Azure Rights Management.

3.  Utilize o cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) para desligar do serviço Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```

Se tiver de confirmar mais tarde qual a chave de inquilino do Azure Information Protection utilizada no Azure Key Vault, utilize o cmdlet [Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys) do Azure RMS.

Agora está pronto para ir para o [Passo 5. Ativar o serviço Azure Rights Management](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

