---
title: "Migrar chave protegida por software para chave protegida por software – AIP"
description: "Instruções que fazem parte do caminho de migração do AD RMS para o Azure Information Protection e só são aplicáveis se a sua chave do AD RMS estiver protegida por software e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por software."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 60370cc34184b28f5cdecf6ad51f9ba58dd4816a
ms.sourcegitcommit: 77b0936bea2700eb12b580e5738e077d447d5686
translationtype: HT
---
# <a name="step-2-software-protected-key-to-software-protected-key-migration"></a>Passo 2: migração de chave protegida por software para chave protegida por software

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*


Estas instruções fazem parte do [caminho de migração do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) e só são aplicáveis se a sua chave do AD RMS estiver protegida por software e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por software. 

Se este não for o cenário de configuração escolhido, regresse ao [Passo 4. Exporte os dados de configuração do AD RMS, importe-os para o Azure RMS](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) e escolha uma configuração diferente.

Utilize o seguinte procedimento para importar a configuração do AD RMS para o Azure Information Protection, que resultará na sua chave de inquilino do Azure Information Protection que é gerida pela Microsoft.

## <a name="to-import-the-configuration-data-to-azure-information-protection"></a>Para importar os dados de configuração para o Azure Information Protection

1. Numa estação de trabalho com ligação à Internet, utilize o cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) para ligar ao serviço Azure Rights Management:

    ```
    Connect-AadrmService
    ```
    Quando for solicitado, introduza as credenciais de administrador de inquilinos do [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (normalmente, utilizará uma conta de um administrador global do Azure Active Directory ou do Office 365).

2. Utilize o cmdlet [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd) para carregar o primeiro ficheiro de domínio de publicação fidedigno exportado (.xml). Se tiver mais do que um ficheiro .xml porque tinha múltiplos domínios de publicação fidedignos, selecione o ficheiro que contém o domínio de publicação fidedigno exportado que pretende utilizar com o Azure Information Protection para proteger conteúdos após a migração. Utilize o seguinte comando:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword <secure string> -Active $True -Verbose
    ```
    Pode utilizar [ConvertTo-SecureString -AsPlaintext](https://technet.microsoft.com/library/hh849818.aspx) ou [Read-Host](https://technet.microsoft.com/library/hh849945.aspx) para especificar a palavra-passe como uma cadeia segura. Quando utilizar ConvertTo-SecureString e a palavra-passe tiver carateres especiais, introduza a palavra-passe entre plicas ou remova os carateres especiais.
    
    Por exemplo: primeiro, execute **$TPD_Password = Read-Host -AsSecureString** e introduza a palavra-passe que especificou anteriormente. Em seguida, execute **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Active $true -Verbose**. Quando lhe for pedido, confirme que pretende efetuar esta ação.
    
3.  Quando o comando for concluído, repita o passo 3 para cada ficheiro .xml restante que criou ao exportar os seus domínios de publicação fidedignos. Por exemplo, deverá ter pelo menos um ficheiro adicional para importar se tiver atualizado o seu cluster AD RMS para o Modo Criptográfico 2. No entanto, para esses ficheiros, defina **-Active** para **false** ao executar o comando Import. Por exemplo: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword $TPD_Password -Active $false -Verbose**

4.  Utilize o cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) para desligar do serviço Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```


Agora está pronto para ir para o [Passo 5. Ative o seu inquilino do Azure Information Protection](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

