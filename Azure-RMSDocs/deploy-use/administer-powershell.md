---
title: Administrar o Azure Rights Management com o PowerShell – AIP
description: Saiba como pode utilizar o módulo do PowerShell do serviço Azure Rights Management (AADRM) para o Azure Information Protection para administrar este serviço na sua organização.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/13/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6e8c45c2ff7ae70dc321e2486151fddaf5791ccf
ms.sourcegitcommit: affda7572064edaf9e3b63d88f4a18d0d6932b13
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31009173"
---
# <a name="administering-the-azure-rights-management-service-by-using-windows-powershell"></a>Administrar o serviço Azure Rights Management através do Windows PowerShell

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Precisa de utilizar o PowerShell para administrar o serviço Azure Rights Management para o Azure Information Protection? Não poderá ter de se toda a sua configuração pode ser efetuada no portal do Azure ou no portal do Office 365. No entanto, terá de utilizar o PowerShell para algumas configurações avançadas e também poderá preferir utilizar o PowerShell para o controlo mais eficiente de linha de comandos e idioma de scripting.

A tabela na secção seguinte inclui alguns dos cenários de configuração avançada que utilizam o PowerShell. Quando a configuração também puder ser concluída sem utilizar o PowerShell, esta informação também é incluída na tabela.

Para obter uma lista completa dos cmdlets disponíveis para este módulo com mais informações acerca de cada um deles, veja [AADRM](/powershell/module/aadrm/?view=azureipps#aadrm).

> [!NOTE]
> Para instalar este módulo do PowerShell, consulte [instalar o módulo do AADRM PowerShell](install-powershell.md).

Para além deste módulo do PowerShell do lado do serviço, o cliente do Azure Information Protection instala o módulo do PowerShell suplementar **AzureInformationProtection**. Este módulo cliente suporta a classificação e a proteção de vários ficheiros de modo a, por exemplo, poder proteger em massa todos os ficheiros numa pasta. Para obter mais informações, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](../rms-client/client-admin-guide-powershell.md) no guia do administrador.

## <a name="cmdlets-grouped-by-administration-task"></a>Cmdlets agrupados por tarefa de administração

|Se precisar de...|...utilize os seguintes cmdlets|
|-------------------|------------------------------|
|Migrar do Rights Management no local (AD RMS ou Windows RMS) para o Azure Information Protection.|[Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd)<br /><br />[Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)|
|Ligar ou desligar o serviço [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] para a sua organização.|[Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice)<br /><br />[Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice)|
|Gerar e gerir sua própria chave de inquilino – o cenário traga a sua própria chave (BYOK).|[Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)<br /><br />[Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey)<br /><br />[Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys)|
|Ativar ou desativar o serviço [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] para a sua organização.<br /><br />Também pode realizar estas ações a partir dos portais de gestão. Para obter mais informações, veja [Ativar o serviço Azure Rights Management](activate-service.md).|[Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm)<br /><br />[Disable-Aadrm](/powershell/aadrm/vlatest/disable-aadrm)|
|Gerir o documento de site de controlo para o Azure Information Protection.|[Disable-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/disable-aadrmdocumenttrackingfeature)<br /><br />[Enable-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/enable-aadrmdocumenttrackingfeature)<br /><br />[Get-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/get-aadrmdocumenttrackingfeature)<br /><br />[Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/set-aadrmdonottrackusergroup)<br /><br />[Clear-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Clear-AadrmDoNotTrackUserGroup)<br /><br />[Get-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/get-AadrmDoNotTrackUserGroup)<br /><br />[Get-AadrmTrackingLog](/powershell/module/aadrm/Get-AadrmTrackingLog)<br /><br />[Get-AadrmDocumentLog](/powershell/module/aadrm/Get-AadrmDocumentLog)|
|Configurar os controlos de inclusão de uma implementação faseada do serviço Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/get-aadrmonboardingcontrolpolicy)<br /><br />[Set-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/set-aadrmonboardingcontrolpolicy)|
|Criar e gerir modelos do Rights Management para a sua organização.<br /><br />Também pode efetuar a maioria destas ações do portal do Azure, embora PowerShell oferece um controlo mais Cativação. Para obter mais informações, consulte [configurar e gerir modelos do Azure Information Protection](configure-policy-templates.md).|[Add-AadrmTemplate](/powershell/aadrm/vlatest/add-aadrmtemplate)<br /><br />[Export-AadrmTemplate](/powershell/aadrm/vlatest/export-aadrmtemplate)<br /><br />[Get-AadrmTemplate](/powershell/aadrm/vlatest/get-aadrmtemplate)<br /><br />[Get-AadrmTemplateProperty](/powershell/aadrm/vlatest/get-aadrmtemplateproperty)<br /><br />[Import-AadrmTemplate](/powershell/aadrm/vlatest/import-aadrmtemplate)<br /><br />[New-AadrmRightsDefinition](/powershell/aadrm/vlatest/new-aadrmrightsdefinition)<br /><br />[Remove-AadrmTemplate](/powershell/aadrm/vlatest/remove-aadrmtemplate)<br /><br />[Set-AadrmTemplateProperty](/powershell/aadrm/vlatest/set-aadrmtemplateproperty)|
|Configurar o número máximo de dias durante os quais é possível aceder ao conteúdo protegido pela sua organização sem uma ligação à Internet (o período de validade da licença de utilização).|[Get-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/get-aadrmmaxuselicensevaliditytime)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime)|
|Gerir a funcionalidade de superutilizador do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] para a sua organização.|[Enable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/enable-aadrmsuperuserfeature)<br /><br />[Disable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/disable-aadrmsuperuserfeature)<br /><br />[Add-AadrmSuperUser](/powershell/aadrm/vlatest/add-aadrmsuperuser)<br /><br />[Get-AadrmSuperUser](/powershell/aadrm/vlatest/get-aadrmsuperuser)<br /><br />[Remove-AadrmSuperUser](/powershell/aadrm/vlatest/remove-aadrmsuperuser)<br /><br />[Set-AadrmSuperUserGroup](/powershell/aadrm/vlatest/set-aadrmsuperusergroup)<br /><br />[Get-AadrmSuperUserGroup](/powershell/aadrm/vlatest/get-aadrmsuperusergroup)<br /><br />[Clear-AadrmSuperUserGroup](/powershell/aadrm/vlatest/clear-aadrmsuperusergroup)|
|Gerir utilizadores e grupos que estão autorizados a administrar o serviço [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] da sua organização.|[Add-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/add-aadrmrolebasedadministrator)<br /><br />[Get-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/get-aadrmrolebasedadministrator)<br /><br />[Remove-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/remove-aadrmrolebasedadministrator)|
|Obter um registo das tarefas administrativas do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] da sua organização.|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Registe e analise o registo de utilização do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|[Get-AadrmUserLog](/powershell/aadrm/vlatest/get-aadrmuserlog)|
|Apresentar a configuração atual do serviço [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] da sua organização.|[Get-AadrmConfiguration](/powershell/aadrm/vlatest/get-aadrmconfiguration)|
|Migrar a sua organização do Azure Information Protection para uma implementação do AD RMS no local.|[Set-AadrmMigrationUrl](/powershell/aadrm/vlatest/set-aadrmmigrationurl)<br /><br />[Get-AadrmMigrationUrl](/powershell/aadrm/vlatest/get-aadrmmigrationurl)|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
