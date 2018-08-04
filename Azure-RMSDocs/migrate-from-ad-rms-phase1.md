---
title: Migrar do AD RMS para o Azure Information Protection – fase 1
description: Fase 1 da migração do AD RMS para o Azure Information Protection, que abrange os passos 1 a 3 de Migrar do AD RMS para o Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d954d3ee-3c48-4241-aecf-01f4c75fa62c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 43b5af3397fe87e01578830fa5b7299edec501b9
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491453"
---
# <a name="migration-phase-1---preparation"></a>Fase 1 da migração – preparação

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize as seguintes informações para a Fase 1 da migração do AD RMS para o Azure Information Protection. Estes procedimentos abrangem os passos 1 a 3 de [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) e preparam o seu ambiente para a migração sem qualquer impacto para os seus utilizadores.


## <a name="step-1-install-the-aadrm-powershell-module-and-identify-your-tenant-url"></a>Passo 1: Instalar o módulo PowerShell do AADRM e identificar o URL de inquilino

Instale o módulo do AADRM para que possa configurar e gerir o serviço que fornece a proteção de dados do Azure Information Protection.

Para obter instruções, consulte [instalar o módulo do PowerShell do AADRM](./install-powershell.md).

> [!NOTE]
> Se já transferiu anteriormente este módulo do Windows PowerShell, execute o seguinte comando para verificar se tem a versão número **2.9.0.0** ou posterior: `(Get-Module aadrm -ListAvailable).Version`

Para concluir algumas das instruções de migração, terá de saber o URL do serviço Azure Rights Management do seu inquilino para que possa substituí-lo quando vir as referências para *\<URL de Inquilino\>*. O URL do serviço Azure Rights Management tem o formato seguinte: **{GUID}.rms.[Região].aadrm.com**.

Por exemplo: **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

### <a name="to-identify-your-azure-rights-management-service-url"></a>Para identificar o URL do serviço Azure Rights Management

1. Ligue ao serviço Azure Rights Management e quando lhe for pedido, introduza as credenciais de administrador global do inquilino:
    
        Connect-AadrmService
    
2. Obtenha a configuração do seu inquilino:
    
        Get-AadrmConfiguration
    
3. Copie o valor apresentado em **LicensingIntranetDistributionPointUrl** e, em seguida, a partir desta cadeia, remova `/_wmcs\licensing`. 
    
    O que permanece é o URL do serviço Azure Rights Management para o seu inquilino do Azure Information Protection. Este valor é muitas vezes abreviado para *o URL de inquilino* nas seguintes instruções de migração.
    
    Pode verificar se tem o valor correto ao executar o seguinte comando do PowerShell:
    
            (Get-AadrmConfiguration).LicensingIntranetDistributionPointUrl -match "https:\/\/[0-9A-Za-z\.-]*" | Out-Null; $matches[0]

## <a name="step-2-prepare-for-client-migration"></a>Passo 2. preparar a migração de clientes

Na maioria das migrações, não é prático migrar todos os clientes de uma só vez, por isso irá migrar os clientes em lotes. O que significa que durante um período de tempo, alguns clientes irão utilizar o Azure Information Protection e alguns ainda irão utilizar o AD RMS. Para suportar os utilizadores pré-migrados e migrados, utilize os controlos de inclusão e implemente um script de pré-migração. Este passo é obrigatório durante o processo de migração para que os utilizadores que ainda não migraram possam consumir conteúdos que foram protegidos pelos utilizadores migrados que estão agora a utilizar o Azure Rights Management.

1. Crie um grupo, por exemplo, com o nome **AIPMigrated**. Este grupo pode ser criado no Active Directory e sincronizado com a cloud ou pode ser criado no Office 365 ou no Azure Active Directory. Não atribua utilizadores a este grupo neste momento. Num passo posterior, quando os utilizadores forem migrados, irá adicioná-los ao grupo.

    Tome nota do ID do objeto deste grupo. Para o fazer, pode utilizar o PowerShell do Azure AD – por exemplo, para a versão 1.0 do módulo, utilize o comando [Get-MsolGroup](/powershell/msonline/v1/Get-MsolGroup). Em alternativa, pode copiar o ID do objeto do grupo a partir do portal do Azure.

2. Configure controlos de inclusão neste grupo para permitir que apenas as pessoas neste grupo utilizem o Azure Rights Management para proteger conteúdo. Para o fazer, numa sessão do PowerShell, ligue ao serviço Azure Rights Management e quando lhe for pedido, especifique as credenciais de administrador global:

        Connect-Aadrmservice

    Em seguida, configure os controlos de inclusão deste grupo, ao substituir o ID do objeto do grupo pelo deste exemplo e introduza **Y** para confirmar quando lhe for pedido:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fba99fed-32a0-44e0-b032-37b419009501" -Scope WindowsApp

3. [Transfira o ficheiro seguinte](https://go.microsoft.com/fwlink/?LinkId=524619) que contém scripts de migração de clientes:
    
    **Migration-Scripts.zip**
    
4. Extraia os ficheiros e siga as instruções em **preparar Client.cmd** para que ele contém o nome do servidor para o AD RMS cluster extranet URL de licenciamento. 
    
    Para localizar este nome: na consola dos Serviços de Gestão de Direitos do Active Directory, clique no nome do cluster. Nas informações em **Detalhes do Cluster**, copie o nome de servidor do valor **Licensing** da secção de URLs do cluster da extranet. Por exemplo: **rmscluster.contoso.com**.

    > [!IMPORTANT]
    > As instruções incluem a substituição de endereços de exemplo de **adrms.contoso.com** pelos endereços de servidor do AD RMS. Ao fazê-lo, certifique-se de que não existem espaços adicionais antes ou depois dos endereços, uma vez que estes interrompem o script de migração e são muito difíceis de identificar como a causa de raiz do problema. Algumas ferramentas de edição adicionam automaticamente um espaço depois do texto colado.
    >

5. Implemente este script em todos os computadores Windows para se certificar de que quando começar a migrar os clientes, os clientes que ainda não foram migrados continuam a comunicar com o AD RMS mesmo se consumirem conteúdos que estão protegidos por clientes migrados que estão agora a utilizar o serviço Azure Rights Management.

    Pode utilizar a Política de Grupo ou outro mecanismo de implementação de software para implementar este script.

## <a name="step-3-prepare-your-exchange-deployment-for-migration"></a>Passo 3: preparar a implementação do Exchange para a migração

Se estiver a utilizar o Exchange no local ou o Exchange Online, poderá ter integrado anteriormente o Exchange com a sua implementação do AD RMS. Neste passo irá configurá-los para utilizarem a configuração do AD RMS existente para suportar conteúdos protegidos pelo Azure RMS. 

Certifique-se de que tem o [URL do serviço Azure Rights Management do seu inquilino](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url) para que possa substituir este valor por *&lt;YourTenantURL&gt;* nos comandos seguintes. 

**Se tiver integrado o Exchange Online com o AD RMS**: abra uma sessão do PowerShell do Exchange Online e execute os seguintes comandos do PowerShell individualmente ou num script:

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -internallicensingenabled $true 

**Se tiver integrado o Exchange no local com o AD RMS**: para cada organização do Exchange, adicione primeiro os valores de registo em cada servidor do Exchange e, em seguida, execute os comandos do PowerShell: 

Valores de registo para o Exchange 2013 e o Exchange 2016:

**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Valor:** https://\<URL de Inquilino\>/_wmcs/licensing

**Dados:** https://\<URL de Licenciamento na Extranet do AD RMS\>/_wmcs/licensing

---

Valores de registo para o Exchange 2010:

**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Valor:** https://\<URL de Inquilino\>/_wmcs/licensing

**Dados:** https://\<URL de Licenciamento na Extranet do AD RMS>/_wmcs/licensing

---

Comandos do PowerShell para executar individualmente ou num script

    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation
    $list += "<YourTenantURL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    Set-IRMConfiguration -internallicensingenabled $false
    Set-IRMConfiguration -RefreshServerCertificates
    Set-IRMConfiguration -internallicensingenabled $true
    IISReset


Após executar estes comandos para o Exchange Online ou o Exchange no local, se a sua implementação do Exchange tiver sido configurada para suportar conteúdo protegido pelo AD RMS, também suportará conteúdo protegido pelo Azure RMS após a migração. A implementação do Exchange continuará a utilizar o AD RMS para suportar conteúdo protegido até um passo posterior na migração.


## <a name="next-steps"></a>Passos Seguintes
Avance para a [fase 2 – configuração do lado do servidor](migrate-from-ad-rms-phase2.md).

