---
title: "Passo 2&colon; migração de chave protegida por software para chave protegida por software | Azure Information Protection"
description: "Instruções que fazem parte do caminho de migração do AD RMS para o Azure Information Protection e só são aplicáveis se a sua chave do AD RMS estiver protegida por software e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por software."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 931642ea9070a7581b428bcd04756048673fe3c0
ms.openlocfilehash: e6bffd31e7f198a767531fb343b8146246078004


---


# Passo 2: migração de chave protegida por software para chave protegida por software

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*


Estas instruções fazem parte do [caminho de migração do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) e só são aplicáveis se a sua chave do AD RMS estiver protegida por software e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por software. 

Se este não for o cenário de configuração escolhido, volte ao [Passo 2. Exporte os dados de configuração do AD RMS, importe-os para o Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) e escolha uma configuração diferente.

Utilize o seguinte procedimento para importar a configuração do AD RMS para o Azure Information Protection, que resultará na sua chave de inquilino do Azure Information Protection que é gerida pela Microsoft.

## Para importar os dados de configuração para o Azure Information Protection

1.  Numa estação de trabalho com ligação à Internet, transfira e instale o módulo do Windows PowerShell para o Azure Rights Management (versão mínima 2.5.0.0), que inclui o cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx). O serviço Azure Rights Management (Azure RMS) fornece o serviço de proteção para o Azure Information Protection.

    > [!TIP]
    > Se já transferiu e instalou o módulo anteriormente, verifique o número da versão ao executar: `(Get-Module aadrm -ListAvailable).Version`

    Para obter instruções de instalação, consulte [Installing Windows PowerShell for Azure Rights Management (Instalar o Windows PowerShell para o Azure Rights Management – em inglês)](../deploy-use/install-powershell.md).

2.  Inicie o Windows PowerShell com a opção **Executar como administrador** e utilize o cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) para efetuar uma ligação ao serviço do Azure RMS:

    ```
    Connect-AadrmService
    ```
    Quando for solicitado, introduza as credenciais de administrador de inquilinos do [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (normalmente, utilizará uma conta de um administrador global do Azure Active Directory ou do Office 365).

3.  Utilize o cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) para carregar o primeiro ficheiro de domínio de publicação fidedigno exportado (.xml). Se tiver mais do que um ficheiro .xml porque tinha múltiplos domínios de publicação fidedignos, selecione o ficheiro que contém o domínio de publicação fidedigno exportado que pretende utilizar com o Azure Information Protection para proteger conteúdos após a migração. Utilize o seguinte comando:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword <secure string> -Active $True -Verbose
    ```
    Pode utilizar [ConvertTo-SecureString -AsPlaintext](https://technet.microsoft.com/library/hh849818.aspx) ou [Read-Host](https://technet.microsoft.com/library/hh849945.aspx) para especificar a palavra-passe como uma cadeia segura. Quando utilizar ConvertTo-SecureString e a palavra-passe tiver carateres especiais, introduza a palavra-passe entre plicas ou remova os carateres especiais.
    
    Por exemplo: primeiro, execute **$TPD_Password = Read-Host -AsSecureString** e introduza a palavra-passe que especificou anteriormente. Em seguida, execute **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Active $true -Verbose**. Quando lhe for pedido, confirme que pretende efetuar esta ação.
    
4.  Quando o comando for concluído, repita o passo 3 para cada ficheiro .xml restante que criou ao exportar os seus domínios de publicação fidedignos. No entanto, para esses ficheiros, defina **-Active** para **false** ao executar o comando Import. Por exemplo: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword $TPD_Password -Active $false -Verbose**

5.  Utilize o cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) para desligar do serviço Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```


Agora está pronto para ir para o [Passo 3. Ative o seu inquilino do Azure Information Protection](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).





<!--HONumber=Sep16_HO4-->


