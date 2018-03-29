---
title: Configurar superutilizadores para o Azure Rights Management – AIP
description: Conheça e implemente a funcionalidade de superutilizador do serviço Azure Rights Management do Azure Information Protection para que as pessoas e os serviços autorizados possam sempre ler e inspecionar os dados que o Azure Rights Management protege na sua organização. Esta capacidade é por vezes referida como "raciocínio através de dados" e é um elemento fundamental na manutenção do controlo dos dados da organização.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5d35f7faed0e02a253e5ba48cbdb2bca0aa76419
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="configuring-super-users-for-azure-rights-management-and-discovery-services-or-data-recovery"></a>Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

A funcionalidade de superutilizador do serviço Azure Rights Management do Azure Information Protection assegura que as pessoas e os serviços autorizados possam sempre ler e inspecionar os dados que o Azure Rights Management protege na sua organização. E, se for necessário, remove a proteção ou altera a proteção que estava anteriormente aplicada. 

Um superutilizador tem sempre o [direito de utilização](configure-usage-rights.md) Controlo Total do Rights Management para documentos e e-mails que foram protegidos pelo inquilino do Azure Information Protection da sua organização. Esta capacidade é por vezes referida como "raciocínio através de dados" e é um elemento fundamental na manutenção do controlo de dados da sua organização. Por exemplo, utilizaria esta funcionalidade para qualquer um dos seguintes cenários:

- Um funcionário sai da organização e precisa de ler os ficheiros que ele protegeu.

- Um administrador de TI tem de remover a política de proteção atual que foi configurada para OS ficheiros e aplicar uma nova política de proteção.

- O Exchange Server necessita de indexar caixas de correio para operações de pesquisa.

- Possui serviços de TI existentes para soluções de prevenção de perda de dados (DLP), gateways de encriptação de conteúdo (CEG) e produtos de antimalware que necessitam de inspecionar ficheiros que já estão protegidos.

- É necessário desencriptar em volume ficheiros por motivos de auditoria, jurídicos ou outros motivos de conformidade.

## <a name="configuration-for-the-super-user-feature"></a>Configuração para a funcionalidade de Superutilizador

Por predefinição, a funcionalidade de superutilizador não está ativada. Esta função não é atribuída a nenhum utilizador. É automaticamente ativado para si se configurar o conector Rights Management para Exchange e não é necessário para serviços padrão que executem o Exchange Online, o SharePoint Online ou o SharePoint Server.

Se precisar de ativar manualmente a funcionalidade de superutilizador, utilize o cmdlet do PowerShell [Enable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/enable-aadrmsuperuserfeature) e, em seguida, atribua utilizadores (ou contas de serviço), conforme necessário, ao utilizar o cmdlet [Add-AadrmSuperUser](/powershell/aadrm/vlatest/add-aadrmsuperuser) cmdlet ou o cmdlet [Set-AadrmSuperUserGroup](/powershell/aadrm/vlatest/set-aadrmsuperusergroup) e adicione utilizadores (ou outros grupos) a este grupo, conforme necessário. 

Embora utilizar um grupo para os seus superutilizadores seja mais fácil de gerir, tenha em atenção que, por motivos de desempenho, o Azure Rights Management [coloca a associação do grupo em cache](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). Por isso, se precisa de atribuir um novo utilizador como superutilizador para desencriptar conteúdos imediatamente, adicione esse utilizador através do cmdlet Add-AadrmSuperUser em vez de o adicionar a um grupo existente que configurou ao utilizar o cmdlet Set-AadrmSuperUserGroup.

> [!NOTE]
> Se que ainda não instalou o módulo do Windows PowerShell para [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], consulte [instalar o módulo do AADRM PowerShell](install-powershell.md).

É irrelevante quando ativa a funcionalidade de Superutilizador ou ao adicionar os utilizadores como superutilizadores. Por exemplo, se ativar a funcionalidade no Quinta-feira e, em seguida, adicionar um utilizador no sexta-feira, esse utilizador pode abrir imediatamente conteúdo que foi protegido no muito início da semana.

## <a name="security-best-practices-for-the-super-user-feature"></a>Melhores práticas de segurança para a funcionalidade de Superutilizador

- Restrinja e monitorize os administradores a quem é atribuída a função de administrador global para o seu inquilino do Office 365 ou do Azure Information Protection ou a quem é atribuída a função GlobalAdministrator através do cmdlet [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator). Estes utilizadores podem ativar a funcionalidade de superutilizador e atribuir utilizadores (e os próprios) como superutilizadores, bem como desencriptar potencialmente todos os ficheiros que a sua organização protege.

- Para ver quais os utilizadores e as contas de serviço que são atribuídos individualmente como superutilizadores, utilize o cmdlet [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser). Para ver se um grupo de superutilizadores está configurado, utilize o cmdlet [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperusergroup) e as suas ferramentas padrão de gestão de utilizadores para verificar quais os utilizadores que são membros deste grupo. Como todas as ações de administração, ativar ou desativar a funcionalidade super e adicionar ou remover superutilizadores, são registadas e podem ser auditadas ao utilizar o comando [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog). Consulte a secção seguinte para obter um exemplo. Quando os superutilizadores desencriptam ficheiros, esta ação é registada e pode ser auditada com o [registo de utilização](log-analyze-usage.md).

- Se não necessitar da funcionalidade de superutilizador para os serviços diários, ative a funcionalidade apenas quando precisar dela e desative-a novamente ao utilizar o cmdlet [Disable-AadrmSuperUserFeature](/powershell/module/aadrm/disable-aadrmsuperuserfeature).

### <a name="example-auditing-for-the-super-user-feature"></a>Exemplo de auditoria para a funcionalidade de Superutilizador

O seguinte extrato de registo mostra algumas entradas de exemplo da utilização de [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) cmdlet. 

Neste exemplo, o administrador da Contoso Ltd confirma que a funcionalidade de superutilizador está desativada, adiciona Guilherme Sarmento como um superutilizador, verifica se o Guilherme é o único superutilizador configurado para o serviço Azure Rights Management e, em seguida, ativa a funcionalidade de superutilizador para que o Guilherme possa desencriptar alguns ficheiros que foram protegidos por um empregado que entretanto saiu da empresa.

`2015-08-01T18:58:20    admin@contoso.com   GetSuperUserFeatureState    Passed  Disabled`

`2015-08-01T18:59:44    admin@contoso.com   AddSuperUser -id rsimone@contoso.com    Passed  True`

`2015-08-01T19:00:51    admin@contoso.com   GetSuperUser    Passed  rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com   SetSuperUserFeatureState -state Enabled Passed  True`

## <a name="scripting-options-for-super-users"></a>Opções de scripting para superutilizadores
É frequente que uma pessoa a quem seja atribuído um superutilizador para o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] venha a ter de remover a proteção de vários ficheiros, em várias localizações. Embora seja possível fazê-lo manualmente, é mais eficaz (e, muitas vezes, mais fiável) efetuar um script disto. Em seguida, pode utilizar o cmdlet [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) e o cmdlet [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile), conforme necessário. 

Se estiver a utilizar a classificação e a proteção, também poderá utilizar o [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) para aplicar uma nova etiqueta que não aplique proteção ou remover a etiqueta que aplicou a proteção. 

Para obter mais informações sobre estes cmdlets, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](../rms-client/client-admin-guide-powershell.md) no guia do administrador do cliente do Azure Information Protection.

> [!NOTE]
> O módulo AzureInformationProtection substitui o módulo do PowerShell de Proteção RMS que foi instalado com a Ferramenta de Proteção RMS. Ambos estes módulos são diferentes do e complementa o [módulo do PowerShell do Azure Rights Management](administer-powershell.md). O módulo AzureInformationProtection suporta o Azure Information Protection, o serviço Azure Rights Management (Azure RMS) para o Azure Information Protection e os Serviços de Gestão de Direitos do Active Directory (AD RMS).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

