---
title: Migrar chave protegida por software para chave protegida por HSM – AIP
description: Instruções que fazem parte do caminho de migração do AD RMS para o Azure Information Protection e são aplicáveis apenas se a sua chave do AD RMS estiver protegida por software e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por HSM no Azure Key Vault.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: eccaf8570704ee5adf13bf3f3d4426fecaa5e08e
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491474"
---
# <a name="step-2-software-protected-key-to-hsm-protected-key-migration"></a>Passo 2: migração de chave protegida por software para chave protegida por HSM

>*Aplica-se a: serviços de gestão de direitos do Active Directory [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*


Estas instruções fazem parte do [caminho de migração do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) e são aplicáveis apenas se a sua chave do AD RMS estiver protegida por software e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por HSM no Azure Key Vault. 

Se este não for o cenário de configuração escolhido, regresse ao [Passo 4. Exporte os dados de configuração do AD RMS, importe-os para o Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) e escolha uma configuração diferente.

Este é um procedimento dividido em quatro partes para importar a configuração do AD RMS para o Azure Information Protection, de modo a criar a chave de inquilino do Azure Information Protection gerida por si (BYOK) no Azure Key Vault.

Primeiro tem de extrair a sua chave de certificado de licenciante para servidor (SLC) dos dados de configuração do AD RMS e transferir a chave para um HSM da Thales no local. Em seguida, tem de transferir a sua chave HSM para o Azure Key Vault, autorizar o acesso do serviço Azure Rights Management do Azure Information Protection ao seu cofre de chaves e, em seguida, importar os dados de configuração.

Uma vez que a chave de inquilino do Azure Information Protection será armazenada e gerida pelo Azure Key Vault, esta parte da migração requer administração no Azure Key Vault, além do Azure Information Protection. Se o Azure Key Vault da sua organização for gerido por um administrador diferente de si, tem de se coordenar e trabalhar com esse administrador para concluir estes procedimentos.

Antes de começar, certifique-se de que a sua organização tem um cofre de chaves criado no Azure Key Vault e que suporta chaves protegidas por HSM. Embora não seja necessário, recomendamos que tenha um cofre de chaves dedicado para o Azure Information Protection. Este cofre de chaves será configurado para permitir o acesso ao serviço Azure Rights Management do Azure Information Protection, de forma a que as chaves armazenadas neste cofre de chaves sejam limitadas apenas a chaves do Azure Information Protection.


> [!TIP]
> Se for efetuar os passos de configuração do Azure Key Vault e não estiver familiarizado com este serviço do Azure, poderá considerar útil primeiro rever [Introdução ao Azure Key Vault](/azure/key-vault/key-vault-get-started). 


## <a name="part-1-extract-your-slc-key-from-the-configuration-data-and-import-the-key-to-your-on-premises-hsm"></a>Parte 1: extrair a chave SLC dos dados de configuração e importar a chave para o seu HSM no local

1.  Administrador do Azure Key Vault: para cada chave SLC exportada que pretende armazenar no Azure Key Vault, siga os seguintes passos na secção [Implementing bring your own key (BYOK) for Azure Key Vault (Implementar o BYOK (Bring Your Own Key – Traga a sua Própria Chave))](/azure/key-vault/key-vault-hsm-protected-keys#implementing-bring-your-own-key-byok-for-azurekey-vault) da documentação do Azure Key Vault:

    -   **Gerar e transferir a sua chave para o HSM do Azure Key Vault**: [Passo 1: preparar a estação de trabalho ligada à Internet](/azure/key-vault-hsm-protected-keys/#step-1-prepare-your-internet-connected-workstation)

    -   **Gerar e transferir a chave de inquilino – através da Internet**: [Passo 2: preparar a estação de trabalho desligada](/azure/key-vault-hsm-protected-keys/#step-2-prepare-your-disconnected-workstation)

    Não siga os passos para gerar a chave de inquilino, porque já tem o equivalente no ficheiro dos dados de configuração exportados (.xml). Em vez disso, deverá executar uma ferramenta para extrair esta chave do ficheiro e importá-la para o seu HSM no local. A ferramenta cria dois ficheiros ao ser executada:

    - Um novo ficheiro de configuração de dados sem a chave, que está pronto para ser importado para o seu inquilino do Azure Information Protection.

    - Um ficheiro PEM (contentor de chaves) com a chave, que está pronto para ser importado para o seu HSM no local.

2. Administrador do Azure Information Protection ou do Azure Key Vault: na estação de trabalho desligada, execute a ferramenta TpdUtil a partir do [Toolkit de migração do Azure RMS](https://go.microsoft.com/fwlink/?LinkId=524619). Por exemplo, se a ferramenta for instalada na unidade E para a qual copia o ficheiro de dados de configuração com o nome ContosoTPD.xml:

    ```
        E:\TpdUtil.exe /tpd:ContosoTPD.xml /otpd:ContosoTPD.xml /opem:ContosoTPD.pem
    ```

    Se tiver mais do que um ficheiro de dados de configuração de RMS, execute esta ferramenta para o resto dos ficheiros.

    Para ver a Ajuda desta ferramenta, que inclui uma descrição, a utilização e exemplos, execute TpdUtil.exe sem parâmetros

    Informações adicionais para este comando:

    - **/tpd**: especifica o caminho e o nome completos do ficheiro de dados de configuração do AD RMS exportado. O nome do parâmetro completo é **TpdFilePath**.

    - **/otpd**: especifica o nome de ficheiro de saída para o ficheiro de dados de configuração sem a chave. O nome do parâmetro completo é **OutPfxFile**. Se não especificar este parâmetro, o ficheiro de saída é predefinido para o nome do ficheiro original com o sufixo **_keyless** e é armazenado na pasta atual.

    - **/opem**: especifica o nome do ficheiro de saída para o ficheiro PEM, o qual contém a chave extraída. O nome do parâmetro completo é **OutPemFile**. Se não especificar este parâmetro, o ficheiro de saída é predefinido para o nome do ficheiro original com o sufixo **_key** e é armazenado na pasta atual.

    - Se não especificar a palavra-passe ao executar este comando (ao utilizar o nome do parâmetro completo **TpdPassword** ou o nome do parâmetro curto **pwd**), será solicitado que a especifique.

3. Na mesma estação de trabalho desligada, anexe e configure o seu HSM da Thales, de acordo com a documentação da Thales. Agora, pode importar a chave para o seu HSM da Thales anexado ao utilizar o seguinte comando, em que terá de substituir o seu próprio nome de ficheiro para ContosoTPD.pem:

        generatekey --import simple pemreadfile=e:\ContosoTPD.pem plainname=ContosoBYOK protect=module ident=contosobyok type=RSA

    > [!NOTE]
    >Se tiver mais do que um ficheiro, escolha o ficheiro que corresponde à chave HSM que pretende utilizar no Azure RMS para proteger o conteúdo após a migração.

    Esta ação irá gerar uma apresentação de saída semelhante à seguinte:

    **parâmetros de geração de chaves:**

    **operation &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Operação a efetuar &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; import**

    **application &nbsp;&nbsp;&nbsp;&nbsp;Aplicação&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; simple**

    **verify &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Verificar segurança da chave de configuração&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; yes**

    **type &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Tipo de chave &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RSA**

    **pemreadfile &nbsp;&nbsp; Ficheiro PEM que contém a chave RSA&nbsp;&nbsp; e:\ContosoTPD.pem**

    **ident &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Identificador de chave &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contosobyok**

    **plainname &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Nome da chave &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ContosoBYOK**

    **Chave importada com êxito.**

    **Caminho para a chave: C:\ProgramData\nCipher\Key Management Data\local\key_simple_contosobyok**

Esta saída confirma que a chave privada foi agora migrada para o seu dispositivo HSM da Thales no local com uma cópia encriptada guardada numa chave (no nosso exemplo, "key_simple_contosobyok"). 

Agora que a chave SLC foi extraída e importada para o seu HSM no local, está pronto para empacotar a chave protegida por HSM e transferi-la para o Azure Key Vault.

> [!IMPORTANT]
> Quando tiver concluído este passo, apague em segurança estes ficheiros PEM da estação de trabalho desligada para assegurar que não podem ser acedidos por pessoas não autorizadas. Por exemplo, execute "cipher /w:E" para eliminar em segurança todos os ficheiros da unidade E:.

## <a name="part-2-package-and-transfer-your-hsm-key-to-azure-key-vault"></a>Parte 2: compactar e transferir a chave HSM para o Azure Key Vault

Administrador do Azure Key Vault: para cada chave SLC exportada que pretende armazenar no Azure Key Vault, siga os seguintes passos na secção [Implementing bring your own key (BYOK) for Azure Key Vault (Implementar o BYOK (Bring Your Own Key – Traga a sua Própria Chave))](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azurekey-vault) da documentação do Azure Key Vault:

- [Passo 4: preparar a transferência da chave](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-4-prepare-your-key-for-transfer)

- [Passo 5: transferir a chave para o Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-5-transfer-your-key-to-azurekey-vault)

Não siga os passos para gerar o par de chaves, uma vez que já tem a chave. Em vez disso, executará um comando para transferir esta chave (no nosso exemplo, o parâmetro KeyIdentifier utiliza "contosobyok") a partir do seu HSM no local.

Antes de transferir a chave para o Azure Key Vault, certifique-se de que o utilitário KeyTransferRemote.exe devolve **Result: SUCCESS** (Resultado: ÊXITO) quando cria uma cópia da sua chave com permissões reduzidas (passo 4.1) e ao encriptar a chave (passo 4.3).

Quando a chave é carregada para o Azure Key Vault, pode ver as propriedades da chave apresentadas, incluindo o ID da chave. Ele será semelhante **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Anote este URL, uma vez que o administrador do Azure Information Protection irá precisar do mesmo para indicar ao serviço Azure Rights Management do Azure Information Protection para utilizar esta chave na respetiva chave de inquilino.

Em seguida, utilize o cmdlet [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) para autorizar o principal do serviço do Azure Rights Management a aceder ao cofre de chaves. As permissões necessárias são decrypt, encrypt, unwrapkey, wrapkey, verify e sign.

Por exemplo, se o cofre de chaves que criou para o Azure Information Protection tiver o nome contosorms-byok-kv e o seu grupo de recursos tiver o nome contosorms-byok-rg, execute o seguinte comando:
    
    Set-AzureRmKeyVaultAccessPolicy -VaultName "contosorms-byok-kv" -ResourceGroupName "contosorms-byok-rg" -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get

Agora que já transferiu a chave HSM para o Azure Key Vault, está pronto para importar os dados de configuração do AD RMS.

## <a name="part-3-import-the-configuration-data-to-azure-information-protection"></a>Parte 3: importar os dados de configuração para o Azure Information Protection

1. Administrador do Azure Information Protection: na estação de trabalho ligada à Internet e na sessão do PowerShell, copie o seu novo ficheiro de configuração de dados (.xml) com a chave SLC removida depois de executar a ferramenta TpdUtil.

2. Carregue cada ficheiro .xml, ao utilizar o cmdlet [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd). Por exemplo, deverá ter pelo menos um ficheiro adicional para importar se tiver atualizado o seu cluster AD RMS para o Modo Criptográfico 2.

    Para executar este cmdlet, precisará da palavra-passe que especificou anteriormente para o ficheiro de dados de configuração e o URL da chave que foi identificada no passo anterior.

    Por exemplo, através de um ficheiro de dados de configuração de C:\contoso_keyless.xml e do nosso valor de URL da chave do passo anterior, execute primeiro o seguinte para armazenar a palavra-passe:
    
    ```
    $TPD_Password = Read-Host -AsSecureString
    ```
    
   Introduza a palavra-passe que especificou para exportar o ficheiro de dados de configuração. Em seguida, execute o seguinte comando e confirme que pretende realizar esta ação:

    ```
    Import-AadrmTpd -TpdFile "C:\contoso_keyless.xml" -ProtectionPassword $TPD_Password –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Verbose
    ```

    Como parte desta importação, a chave SLC é importada e definida automaticamente como arquivada.

3. Depois de carregar todos os ficheiros, execute [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) para especificar a chave importada que corresponde à chave SLC atualmente ativa no cluster do AD RMS.

4. Utilize o cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) para desligar do serviço Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```

Se tiver de confirmar mais tarde qual a chave de inquilino do Azure Information Protection utilizada no Azure Key Vault, utilize o cmdlet [Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys) do Azure RMS.


Agora está pronto para ir para o [Passo 5. Ativar o serviço Azure Rights Management](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).


