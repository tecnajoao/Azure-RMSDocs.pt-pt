---
title: "Passo 2&colon; Migração de chave protegida por software para chave protegida por HSM | Azure RMS"
description: "Estas instruções fazem parte do caminho de migração do AD RMS para o Azure Rights Management e são aplicáveis apenas se a sua chave do AD RMS estiver protegida por software e se pretender migrar para o Azure Rights Management com uma chave de inquilino protegida por HSM no Cofre de Chaves do Azure."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: e470b5b5542536e812749f77353aaf34922d4985


---

# Passo 2: migração de chave protegida por software para chave protegida por HSM

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Rights Management*


Estas instruções fazem parte do [caminho de migração do AD RMS para o Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) e são aplicáveis apenas se a sua chave de AD RMS estiver protegida por software e pretender migrar para o Azure Rights Management com uma chave de inquilino protegida por HSM no Cofre de Chaves do Azure. 

Se este não for o cenário de configuração escolhido, volte ao [Passo 2. Exporte os dados de configuração do AD RMS, importe-os para o Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) e escolha uma configuração diferente.

Trata-se de um procedimento de quatro partes para importar a configuração do AD RMS para o Azure RMS, que resultará na sua chave de inquilino do Azure RMS que é gerida por si (BYOK) no Cofre de Chaves do Azure.

Primeiro, deve extrair a chave do certificado de licenciante para servidor (SLC) dos dados de configuração do AD RMS e transferir a chave para um HSM da Thales no local, compactar e transferir a chave HSM para o Cofre de Chaves do Azure, autorizar o Azure RMS para aceder ao cofre de chaves e, em seguida, importar os dados de configuração.

Uma vez que a chave de inquilino do Azure RMS irá ser armazenada e gerida pelo Cofre de Chaves do Azure, esta parte da migração requer administração no Cofre de Chaves do Azure, além do Azure RMS. Se o Cofre de Chaves do Azure for gerido por um administrador diferente de si para a sua organização, irá precisar de coordenar e trabalhar com esse administrador para concluir estes procedimentos.

Antes de começar, certifique-se de que a sua organização tem um cofre de chaves criado no Cofre de Chaves do Azure e que suporta chaves protegidas por HSM. Embora não seja necessário, recomendamos que tenha um cofre de chaves dedicado para o Azure RMS. Este cofre de chaves será configurado para permitir ao Azure RMS aceder ao mesmo, pelo que as chaves armazenadas por este cofre de chaves devem estar limitadas apenas às chaves do Azure RMS.


> [!TIP]
> Se for efetuar os passos de configuração do Cofre de Chaves do Azure e não estiver familiarizado com este serviço do Azure, poderá considerar útil primeiro rever [Introdução ao Cofre de Chaves do Azure](https://azure.microsoft.com/documentation/articles/key-vault-get-started/). 


## Parte 1: extrair a chave SLC dos dados de configuração e importar a chave para o seu HSM no local

1.  Administrador do Cofre de Chaves do Azure: siga os seguintes passos na secção [Implementar o BYOK (Bring Your Own Key – Traga a Sua Própria Chave)](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) da documentação do Cofre de Chaves do Azure:

    -   **Gerar e transferir a sua chave para o HSM do Cofre de Chaves do Azure**: [Passo 1: preparar a estação de trabalho ligada à Internet](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-1-prepare-your-internet-connected-workstation)

    -   **Gerar e transferir a chave de inquilino – através da Internet**: [Passo 2: preparar a estação de trabalho desligada](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-2-prepare-your-disconnected-workstation)

    Não siga os passos para gerar a chave de inquilino, porque já tem o equivalente no ficheiro dos dados de configuração exportados (.xml). Em vez disso, deverá executar uma ferramenta para extrair esta chave do ficheiro e importá-la para o seu HSM no local. A ferramenta cria dois ficheiros ao ser executada:

    - Um novo ficheiro de dados de configuração sem a chave, que está pronto para ser importado para o inquilino do Azure RMS.

    - Um ficheiro PEM (contentor de chaves) com a chave, que está pronto para ser importado para o seu HSM no local.

2. Administrador do Azure RMS ou administrador do Cofre de Chaves do Azure: na estação de trabalho desligada, execute a ferramenta TpdUtil a partir do [Toolkit de migração do Azure RMS](https://go.microsoft.com/fwlink/?LinkId=524619). Por exemplo, se a ferramenta for instalada na unidade E para a qual copia o ficheiro de dados de configuração com o nome ContosoTPD.xml:

    ```
        E:\TpdUtil.exe /tpd:ContosoTPD.xml /otpd:ContosoTPD.xml /opem:ContosoTPD.pem
    ```

    Se tiver mais do que um ficheiro de dados de configuração de RMS, execute esta ferramenta para o resto dos ficheiros.

    Para ver a Ajuda desta ferramenta, que inclui uma descrição, a utilização e exemplos, execute TpdUtil.exe sem parâmetros

    Informações adicionais para este comando:

    - **/tpd**: especifica o caminho e o nome completos do ficheiro de dados de configuração do AD RMS exportado. O nome do parâmetro completo é **TpdFilePath**.

    - **/otpd**: especifica o nome de ficheiro de saída para o ficheiro de dados de configuração sem a chave. O nome do parâmetro completo é **OutPfxFile**. Se não especificar este parâmetro, o ficheiro de saída é predefinido para o nome do ficheiro original com o sufixo **_keyless** e é armazenado na pasta atual.

    - **/opem**: especifica o nome do ficheiro de saída para o ficheiro PEM, o qual contém a chave extraída. O nome do parâmetro completo é **OutPemFile**. Se não especificar este parâmetro, o ficheiro de saída é predefinido para o nome do ficheiro original com o sufixo **_key** e é armazenado na pasta atual.

    - Se não especificar a palavra-passe quando executa este comando (utilizando o nome do parâmetro completo **TpdPassword** ou o nome do parâmetro curto **pwd**), será solicitado que a especifique.

3. Na mesma estação de trabalho desligada, anexe e configure o seu HSM da Thales, de acordo com a documentação da Thales. Agora, pode importar a chave para o seu HSM da Thales anexado utilizando o seguinte comando em que terá de substituir o nome de ficheiro para ContosoTPD.pem:

        generatekey --import simple pemreadfile=e:\ContosoTPD.pem plainname=ContosoBYOK protect=module ident=contosobyok type=RSA

    > [!NOTE]
    >Se tiver mais do que um ficheiro, escolha o ficheiro que corresponde à chave HSM que pretende utilizar no Azure RMS para proteger o conteúdo após a migração.

    Esta ação irá gerar uma apresentação de saída semelhante à seguinte:

    **parâmetros de geração de chaves:**

    **operation &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Operação a efetuar &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; import**

    **application &nbsp;&nbsp;&nbsp;&nbsp;Aplicação&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; simple**

    **verify &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Verificar segurança da chave de configuração&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; yes**

    **type &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Tipo de chave &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RSA**

    **pemreadfile &nbsp;&nbsp; ficheiro PEM que contém a chave RSA &nbsp;&nbsp; e:\ContosoTPD.pem**

    **ident &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Identificador da chave &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contosobyok**

    **plainname &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Nome da chave &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ContosoBYOK**

    **Chave importada com êxito.**

    **Caminho para a chave: C:\ProgramData\nCipher\Key Management Data\local\key_simple_contosobyok**

Esta saída confirma que a chave privada foi agora migrada para o seu dispositivo HSM da Thales no local com uma cópia encriptada guardada numa chave (no nosso exemplo, "key_simple_contosobyok"). 

Agora que a chave SLC foi extraída e importada para o seu HSM no local, está pronto para empacotar a chave protegida por HSM e transferi-la para o Cofre de Chaves do Azure.

> [!IMPORTANT]
> Quando tiver concluído este passo, apague em segurança estes ficheiros PEM da estação de trabalho desligada para assegurar que não podem ser acedidos por pessoas não autorizadas. Por exemplo, execute "cipher /w:E" para eliminar em segurança todos os ficheiros da unidade E:.

## Parte 2: compactar e transferir a chave HSM para o Cofre de Chaves do Azure

1.  Administrador do Cofre de Chaves do Azure: utilize os seguintes passos da secção [Implementar o BYOK (Bring Your Own Key – Traga a Sua Própria Chave)](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) da documentação do Cofre de Chaves do Azure:

    -   [Passo 4: preparar a transferência da chave](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-4-prepare-your-key-for-transfer)

    -   [Passo 5: transferir a chave para o Cofre de Chaves do Azure](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-5-transfer-your-key-to-azure-key-vault)

    Não siga os passos para gerar o par de chaves, uma vez que já tem a chave. Em vez disso, executará um comando para transferir esta chave (no nosso exemplo, o parâmetro KeyIdentifier utiliza "contosobyok") a partir do seu HSM no local.

    Antes de transferir a chave para o Cofre de Chaves do Azure, certifique-se de que o utilitário KeyTransferRemote.exe devolve **Result: SUCCESS** (Resultado: ÊXITO) quando cria uma cópia da sua chave com permissões reduzidas (passo 4.1) e ao encriptar a chave (passo 4.3).

    Quando a chave é carregada para o Cofre de Chaves do Azure, pode ver as propriedades da chave apresentadas, incluindo o ID da chave. Terá um aspeto semelhante a **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Tome nota deste URL, porque o administrador do Azure RMS irá precisar dele para indicar ao Azure RMS que utilize esta chave para a respetiva chave de inquilino.

    Agora que já transferiu a chave HSM para o Cofre de Chaves do Azure, está pronto para importar os dados de configuração do AD RMS.

## Parte 3: importar os dados de configuração para o Azure RMS

1.  Administrador do Azure RMS: na estação de trabalho ligada à Internet e na sessão do PowerShell, copie os novos ficheiros de dados de configuração (.xml) que têm a chave SLC removida depois de executar a ferramenta TpdUtil.

2. Carregue primeiro o ficheiro .xml, utilizando o cmdlet [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx). Se tiver mais do que um destes ficheiros, porque tinha vários domínios de publicação fidedignos, escolha o ficheiro que corresponde à chave HSM que pretende utilizar no Azure RMS para proteger o conteúdo após a migração.

    Para executar este cmdlet, precisará do URL para a chave identificada no passo anterior.

    Por exemplo, utilizando o nosso valor de URL da chave do passo anterior e um ficheiro de dados de configuração de C:\contoso_keyless.xml, executaria:

    ```
    Import-AadrmTpd -TpdFile "C:\contoso_keyless.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```

    Quando for solicitado, introduza a palavra-passe que especificou anteriormente para o ficheiro de dados de configuração e confirme que pretende efetuar esta ação.

    Se tiver mais do que um ficheiro de dados de configuração, repita este comando para o resto dos ficheiros. No entanto, para esses ficheiros, defina **-Active** para **false** ao executar o comando Import.



3.  Utilize o cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) para desligar do serviço do Azure RMS:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Se tiver de confirmar mais tarde qual a chave de inquilino do Azure RMS utilizada no Cofre de Chaves do Azure, utilize o cmdlet do Azure RMS [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx).


Agora está pronto para ir para o [Passo 3. Ativar o seu inquilino do RMS](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).






<!--HONumber=Aug16_HO4-->


