---
title: "Administrar o serviço Azure Rights Management através do Windows PowerShell | Azure Information Protection"
description: "Saiba como pode utilizar o módulo do PowerShell do serviço Azure Rights Management (AADRM) para o Azure Information Protection para administrar este serviço na sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 16d6a8a00db28c23fd650a1b8beba00333ba6ea4
ms.openlocfilehash: f9aa0d5910ba4868878ae54c446793bfc031d3c2


---

# <a name="administering-the-azure-rights-management-service-by-using-windows-powershell"></a>Administrar o serviço Azure Rights Management através do Windows PowerShell

>*Aplica-se a: Azure Information Protection, Office 365*

Precisa de utilizar o PowerShell para administrar o serviço Azure Rights Management para o Azure Information Protection? Poderá não ter de o fazer se for um administrador global e a única configuração necessária para este serviço for a sua ativação (ou desativação) e a configuração dos modelos do Rights Management.

No entanto, terá de utilizar o PowerShell para configurações mais avançadas e se também não for um administrador global, mas tiver permissões para administrar o serviço por um administrador global. Também poderá preferir utilizar o PowerShell para o controlo da linha de comandos e processamento de scripts mais eficiente.

A tabela na secção seguinte inclui alguns dos cenários de configuração avançada que utilizam o PowerShell. Quando a configuração também puder ser concluída sem utilizar o PowerShell, esta informação também é incluída na tabela.

Para obter uma lista completa dos cmdlets disponíveis com mais informações acerca de cada um deles, consulte [Cmdlets do Azure Rights Management](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> Para instalar este módulo do PowerShell, veja [Instalar o Windows PowerShell para o Azure Rights Management](install-powershell.md).

Para além deste módulo do PowerShell do lado do serviço, o cliente do Azure Information Protection instala o módulo do PowerShell suplementar **AzureInformationProtection**. Este módulo cliente suporta a classificação e a proteção de vários ficheiros de modo a, por exemplo, poder proteger em massa todos os ficheiros numa pasta. Para obter mais informações, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](../rms-client/client-admin-guide-powershell.md) no guia do administrador.

## <a name="cmdlets-grouped-by-administration-task"></a>Cmdlets agrupados por tarefa de administração

|Se precisar de...|...utilize os seguintes cmdlets|
|-------------------|------------------------------|
|Migrar do Rights Management no local (AD RMS ou Windows RMS) para o Azure Information Protection.|[Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Ligar ou desligar o serviço do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] para a sua organização.|[Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Gerar e gerir sua própria chave de inquilino – o cenário traga a sua própria chave (BYOK).|[Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Ativar ou desativar o serviço [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] para a sua organização.<br /><br />Também pode realizar estas ações a partir dos portais de gestão. Para obter mais informações, veja [Ativar o serviço Azure Rights Management](activate-service.md).|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Desativar ou ativar o site de controlo de documentos do Azure Information Protection.|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Configurar os controlos de inclusão de uma implementação faseada do serviço Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Criar e gerir modelos do Rights Management para a sua organização.<br /><br />Também pode fazer a maioria destas ações a partir do portal clássico do Azure, embora o PowerShell ofereça um controlo mais detalhado. Para mais informações, consulte [Configurar modelos personalizados para o serviço Azure Rights Management](configure-custom-templates.md).|[Add-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Export-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Import-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[New-AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Configurar o número máximo de dias durante os quais é possível aceder ao conteúdo protegido pela sua organização sem uma ligação à Internet (o período de validade da licença de utilização).|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Gerir a funcionalidade de superutilizador do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] para a sua organização.|[Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Add-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Remove-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629405.aspx)<br /><br />[Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx)<br /><br />[Get-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653942.aspx)<br /><br />[Clear-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653944.aspx)|
|Gerir utilizadores e grupos que estão autorizados a administrar o serviço do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] da sua organização.|[Add-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Remove-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Obter um registo das tarefas administrativas do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] da sua organização.|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Registe e analise o registo de utilização do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|[Get-AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx)|
|Apresentar a configuração atual do serviço do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] da sua organização.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Migrar a sua organização do Azure Information Protection para uma implementação do AD RMS no local.|[Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]





<!--HONumber=Feb17_HO2-->


