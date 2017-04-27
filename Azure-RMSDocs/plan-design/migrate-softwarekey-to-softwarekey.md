---
title: "Migrar chave protegida por software para chave protegida por software – AIP"
description: "Instruções que fazem parte do caminho de migração do AD RMS para o Azure Information Protection e só são aplicáveis se a sua chave do AD RMS estiver protegida por software e quiser migrar para o Azure Information Protection com uma chave de inquilino protegida por software."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ef3b3f08dfc73703f2bb05943645176c22134a02
ms.sourcegitcommit: 237ce3a0cc4921da5a08ed5753e6491403298194
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

2. Utilize o cmdlet [Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd) para carregar cada ficheiro de domínio de publicação fidedigno exportado (.xml). Por exemplo, deverá ter pelo menos um ficheiro adicional para importar se tiver atualizado o seu cluster AD RMS para o Modo Criptográfico 2. 
    
    Para executar este cmdlet, precisará da palavra-passe que especificou anteriormente para cada ficheiro de dados de configuração. 
    
    Por exemplo, execute primeiro o seguinte para armazenar a palavra-passe:
    
        $TPD_Password = Read-Host -AsSecureString
    
    Introduza a palavra-passe que especificou para exportar o primeiro ficheiro de dados de configuração. Em seguida, ao utilizar E:\contosokey1.xml como exemplo para esse ficheiro de configuração, execute o seguinte comando e confirme que pretende realizar esta ação:
    ```
    Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword $TPD_Password -Verbose
    ```
    
3. Depois de carregar todos os ficheiros, execute [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) para identificar a chave importada que corresponde à chave SLC atualmente ativa no AD RMS. Esta chave tornar-se-á a chave de inquilino ativa para o seu serviço Azure Rights Management.

4.  Utilize o cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice) para desligar do serviço Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```

Agora está pronto para ir para o [Passo 5. Ativar o serviço Azure Rights Management](migrate-from-ad-rms-phase2.md#step-5-activate-the-azure-rights-management-service).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

