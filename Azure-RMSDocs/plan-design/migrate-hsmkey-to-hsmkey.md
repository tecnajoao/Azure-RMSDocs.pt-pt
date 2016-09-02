---
title: "Passo 2&colon; Migração de chave protegida por HSM para chave protegida por HSM | Azure RMS"
description: "Estas instruções fazem parte do caminho de migração do AD RMS para o Azure Rights Management e são aplicáveis apenas se a sua chave do AD RMS estiver protegida por HSM e pretender migrar para o Azure Rights Management com uma chave de inquilino protegida por HSM no Cofre de Chaves do Azure."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 690729d16358b7b997d9cd1fd8cabed22ce78df4


---

# Passo 2: migração de chave protegida por HSM para chave protegida por HSM

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Rights Management*


Estas instruções fazem parte do [caminho de migração do AD RMS para o Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) e são aplicáveis apenas se a sua chave de AD RMS estiver protegida por HSM e pretender migrar para o Azure Rights Management com uma chave de inquilino protegida por HSM no Cofre de Chaves do Azure. 

Se este não for o cenário de configuração escolhido, volte ao [Passo 2. Exporte os dados de configuração do AD RMS, importe-os para o Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) e escolha uma configuração diferente.

> [!NOTE]
> Estas instruções partem do princípio de que a sua chave do AD RMS está protegida por um módulo. Este é o caso mais habitual. 

Trata-se de um procedimento de duas partes para importar a sua chave HSM e a configuração do AD RMS para o Azure RMS, que resultará na sua chave de inquilino do Azure RMS que é gerida por si (BYOK).

Uma vez que a chave de inquilino do Azure RMS irá ser armazenada e gerida pelo Cofre de Chaves do Azure, esta parte da migração requer administração no Cofre de Chaves do Azure, além do Azure RMS. Se o Cofre de Chaves do Azure for gerido por um administrador diferente de si para a sua organização, irá precisar de coordenar e trabalhar com esse administrador para concluir estes procedimentos.

Antes de começar, certifique-se de que a sua organização tem um cofre de chaves criado no Cofre de Chaves do Azure e que suporta chaves protegidas por HSM. Embora não seja necessário, recomendamos que tenha um cofre de chaves dedicado para o Azure RMS. Este cofre de chaves será configurado para permitir ao Azure RMS aceder ao mesmo, pelo que as chaves armazenadas por este cofre de chaves devem estar limitadas apenas às chaves do Azure RMS.


> [!TIP]
> Se for efetuar os passos de configuração do Cofre de Chaves do Azure e não estiver familiarizado com este serviço do Azure, poderá considerar útil primeiro rever [Introdução ao Cofre de Chaves do Azure](https://azure.microsoft.com/documentation/articles/key-vault-get-started/). 


## Parte 1: transferir a chave HSM para o Cofre de Chaves do Azure

Estes procedimentos são efetuados pelo administrador para o Cofre de Chaves do Azure.

1.  Siga as instruções da documentação do Cofre de Chaves do Azure, utilizando [Implementar o BYOK (Bring Your Own Key – Traga a Sua Própria Chave)](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) com a seguinte exceção:

    - Não efetue os passos para **Gerar a chave de inquilino**, porque já tem o equivalente da sua implementação do AD RMS. Em vez disso, identifique a chave utilizada pelo servidor do AD RMS na instalação da Thales e utilize esta chave durante a migração. Os ficheiros de chave encriptados da Thales são normalmente denominados **key<*keyAppName*><*keyIdentifier*>** localmente no servidor.

    Quando a chave é carregada para o Cofre de Chaves do Azure, pode ver as respetivas propriedades apresentadas, incluindo o ID da chave. Terá um aspeto semelhante a https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Tome nota deste URL, porque o administrador do Azure RMS irá precisar dele para indicar ao Azure RMS que utilize esta chave para a respetiva chave de inquilino.

2. Na estação de trabalho ligada à Internet, numa sessão do PowerShell, utilize o cmdlet [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx ) para autorizar o principal do serviço Azure RMS (Microsoft.Azure.RMS) para aceder ao cofre de chaves que armazenará a chave de inquilino do Azure RMS. As permissões necessárias são decrypt, encrypt, unwrapkey, wrapkey, verify e sign.
    
    Por exemplo, se o cofre de chaves que criou para o Azure RMS tiver o nome contoso-byok-ky e o grupo de recursos tiver o nome contoso-byok-rg, execute o seguinte comando:
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName Microsoft.Azure.RMS -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign


Agora que já preparou a chave HSM no Cofre de Chaves do Azure para o Azure RMS, está pronto para importar os dados de configuração do AD RMS.

## Parte 2: importar os dados de configuração para o Azure RMS

Estes procedimentos são efetuados pelo administrador para o Azure RMS.

1.  Na estação de trabalho ligada à Internet e na sessão do PowerShell, ligue ao Azure RMS utilizando o cmdlet [Connnect AadrmService](https://msdn.microsoft.com/library/dn629415.aspx ).
    
    Em seguida, carregue o primeiro ficheiro de domínio de publicação fidedigno exportado (.xml) utilizando o cmdlet [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx). Se tiver mais do que um ficheiro .xml, porque tinha vários domínios de publicação fidedignos, escolha o ficheiro que contém o domínio de publicação fidedigno exportado que corresponde à chave de HSM que pretende utilizar no Azure RMS para proteger o conteúdo após a migração. 
    
    Para executar este cmdlet, precisará do URL para a chave identificada no passo anterior.
    
    Por exemplo, utilizando o nosso valor de URL da chave do passo anterior e um ficheiro TDP de C:\contoso-tpd1.xml, executaria:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```
    
    Quando for solicitado, introduza a palavra-passe que especificou anteriormente e confirme que pretende efetuar esta ação.

2.  Quando o comando for concluído, repita o passo 1 para cada ficheiro .xml restante que criou ao exportar os seus domínios de publicação fidedignos. No entanto, para esses ficheiros, defina **-Active** para **false** ao executar o comando Import.  

3.  Utilize o cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) para desligar do serviço do Azure RMS:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Se tiver de confirmar mais tarde qual a chave de inquilino do Azure RMS utilizada no Cofre de Chaves do Azure, utilize o cmdlet do Azure RMS [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx).

Agora está pronto para ir para o [Passo 3. Ativar o seu inquilino do RMS](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).




<!--HONumber=Aug16_HO4-->


