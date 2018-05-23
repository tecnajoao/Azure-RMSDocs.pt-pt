---
title: Gerir os dados pessoais para o Azure Information Protection
description: Informações sobre os dados pessoais que são utilizadas pelo Azure Information Protection e a forma como pode ver, exporte e eliminá-lo.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 99a51862-83e9-4a1e-873a-a84ae1465f07
ms.reviewer: aashishr
ms.suite: ems
ms.openlocfilehash: f0fc9b01b042c3210abf69804d552607d92c5928
ms.sourcegitcommit: aae04d78ff301921a4e29ac23bd932fb24a83dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/22/2018
---
# <a name="manage-personal-data-for-azure-information-protection"></a>Gerir os dados pessoais para o Azure Information Protection

Quando configurar e utilizar o Azure Information Protection, os endereços de e-mail e os endereços IP são armazenados e utilizados pelo serviço do Azure Information Protection. Estes dados pessoais podem encontrar os seguintes itens:

- A política do Azure Information Protection

- Modelos de proteção para o serviço Azure Rights Management

- Superutilizadores e os administradores delegados para o serviço Azure Rights Management 

- Registos de administração para o serviço Azure Rights Management

- Registos de utilização para o serviço Azure Rights Management

- Os registos de controlo de documentos

- Registos de utilização para o cliente Azure Information Protection e o cliente do RMS 


[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]


## <a name="viewing-personal-data-that-azure-information-protection-uses"></a>Visualizar dados pessoais que utiliza o Azure Information Protection

No portal do Azure, um administrador pode especificar endereços de correio eletrónico para políticas de âmbito e para as definições de proteção dentro de uma configuração de etiqueta. Para obter mais informações, consulte [como configurar a política do Azure Information Protection para utilizadores específicos através da utilização de políticas de âmbito](../deploy-use/configure-policy-scope.md) e [como configurar uma etiqueta para a proteção Rights Management](configure-policy-protection.md). 

Para etiquetas que estão configuradas para aplicar a proteção do serviço Azure Rights Management, as endereço de e-mail também pode ser encontrado em modelos de proteção, utilizando cmdlets do PowerShell do [módulo AADRM](/powershell/module/aadrm). Este módulo do PowerShell também permite que um administrador especificar utilizadores por endereço de e-mail para ser um [Superutilizador](../deploy-use/configure-super-users.md), ou um administrador para o serviço Azure Rights Management. 

Quando o Azure Information Protection é utilizado para classificar e proteger os documentos e e-mails, endereços de e-mail e dos utilizadores poderão estar guardados nos ficheiros de registo.


### <a name="protection-templates"></a>Modelos de proteção

Execute o [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) cmdlet para obter uma lista de modelos de proteção. Pode utilizar o ID de modelo para obter detalhes de um modelo específico. O `RightsDefinitions` objeto apresenta os dados pessoais, se aplicável. 

Exemplo:
```
PS C:\Users> Get-AadrmTemplate -TemplateId fcdbbc36-1f48-48ca-887f-265ee1268f51 | select *


TemplateId              : fcdbbc36-1f48-48ca-887f-265ee1268f51
Names                   : {1033 -> Confidential}
Descriptions            : {1033 -> This data includes sensitive business information. Exposing this data to
                          unauthorized users may cause damage to the business. Examples for Confidential information
                          are employee information, individual customer projects or contracts and sales account data.}
Status                  : Archived
RightsDefinitions       : {admin@aip500.onmicrosoft.com -> VIEW, VIEWRIGHTSDATA, EDIT, DOCEDIT, PRINT, EXTRACT,
                          REPLY, REPLYALL, FORWARD, EXPORT, EDITRIGHTSDATA, OBJMODEL, OWNER,
                          AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@aip500.onmicrosoft.com -> VIEW,
                          VIEWRIGHTSDATA, EDIT, DOCEDIT, PRINT, EXTRACT, REPLY, REPLYALL, FORWARD, EXPORT,
                          EDITRIGHTSDATA, OBJMODEL, OWNER, admin2@aip500.onmicrosoft.com -> VIEW, VIEWRIGHTSDATA, EDIT,
                          DOCEDIT, PRINT, EXTRACT, REPLY, REPLYALL, FORWARD, EXPORT, EDITRIGHTSDATA, OBJMODEL, OWNER}
ContentExpirationDate   : 1/1/0001 12:00:00 AM
ContentValidityDuration : 0
ContentExpirationOption : Never
LicenseValidityDuration : 7
ReadOnly                : False
LastModifiedTimeStamp   : 1/26/2018 6:17:00 PM
ScopedIdentities        : {}
EnableInLegacyApps      : False
LabelId                 :
```

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Superutilizadores e os administradores delegados para o serviço Azure Rights Management

Execute o [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser) cmdlet e [Get-AadrmRoleBasedAdministrator](/powershell/module/aadrm/get-aadrmrolebasedadministrator) cmdlet para ver quais os utilizadores que tenham sido atribuídos a função de utilizador super ou a função de administrador global para o Azure Rights Management serviço. Para os utilizadores que tenham sido atribuídos a qualquer uma destas funções, são apresentados os respetivos endereços de e-mail.


### <a name="administration-logs-for-the-azure-rights-management-service"></a>Registos de administração para o serviço Azure Rights Management

Execute o [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) cmdlet para obter um registo das ações de administração para o serviço Azure Rights Management, que protege os dados para o Azure Information Protection. Este registo inclui dados pessoais sob a forma de endereços de e-mail e os endereços IP. O registo está em texto não encriptado e após a transferência, os detalhes de num administrador específico podem ser pesquisados offline.

Por exemplo:
```
PS C:\Users> Get-AadrmAdminLog -Path '.\Desktop\admin.log' -FromTime 4/1/2018 -ToTime 4/30/2018 -Verbose
The Rights Management administration log was successfully generated and can be found at .\Desktop\admin.log.
```

### <a name="usage-logs-for-the-azure-rights-management-service"></a>Registos de utilização para o serviço Azure Rights Management
Execute o [Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog) cmdlet para obter um registo das ações do utilizador final que utilizam o serviço Azure Rights Management. Este serviço protege os dados do Azure Information Protection. O registo pode incluir dados pessoais sob a forma de endereços de e-mail e os endereços IP. O registo está em texto não encriptado e após a transferência, os detalhes de num administrador específico podem ser pesquisados offline.

Por exemplo:
```
PS C:\Users> Get-AadrmUserLog -Path '.\Desktop\' -FromDate 4/1/2018 -ToDate 4/30/2018 -NumberOfThreads 10
Acquiring access to your user log…
Downloading the log for 2018-04-01.
Downloading the log for 2018-04-03.
Downloading the log for 2018-04-06.
Downloading the log for 2018-04-09.
Downloading the log for 2018-04-10.
Downloaded the log for 2018-04-01. The log is available at .\Desktop\rmslog-2018-04-01.log.
Downloaded the log for 2018-04-03. The log is available at .\Desktop\rmslog-2018-04-03.log.
Downloaded the log for 2018-04-06. The log is available at .\Desktop\rmslog-2018-04-06.log.
Downloaded the log for 2018-04-09. The log is available at .\Desktop\rmslog-2018-04-09.log.
Downloaded the log for 2018-04-10. The log is available at .\Desktop\rmslog-2018-04-10.log.
Downloading the log for 2018-04-12.
Downloading the log for 2018-04-13.
Downloading the log for 2018-04-14.
Downloading the log for 2018-04-16.
Downloading the log for 2018-04-18.
Downloaded the log for 2018-04-12. The log is available at .\Desktop\rmslog-2018-04-12.log.
Downloaded the log for 2018-04-13. The log is available at .\Desktop\rmslog-2018-04-13.log.
Downloaded the log for 2018-04-14. The log is available at .\Desktop\rmslog-2018-04-14.log.
Downloaded the log for 2018-04-16. The log is available at .\Desktop\rmslog-2018-04-16.log.
Downloaded the log for 2018-04-18. The log is available at .\Desktop\rmslog-2018-04-18.log.
Downloading the log for 2018-04-24.
Downloaded the log for 2018-04-24. The log is available at .\Desktop\rmslog-2018-04-24.log.
```   

### <a name="document-tracking-logs"></a>Os registos de controlo de documentos

Execute o [Get-AadrmDocumentLog](/powershell/module/aadrm/get-aadrmdocumentlog) cmdlet para obter as informações do site sobre um utilizador específico de controlo de documentos. Para obter as informações associadas com os registos de documento de controlo, utilize o [Get-AadrmTrackingLog](/powershell/module/aadrm/get-aadrmtrackinglog?view=azureipps) cmdlet.

Por exemplo:
```
PS C:\Users> Get-AadrmDocumentLog -UserEmail "admin@aip500.onmicrosoft.com"


ContentId             : 6326fcb2-c465-4c24-a7f6-1cace7a9cb6f
Issuer                : admin@aip500.onmicrosoft.com
Owner                 : admin@aip500.onmicrosoft.com
ContentName           :
CreatedTime           : 3/6/2018 10:24:00 PM
Recipients            : {
                        PrimaryEmail: johndoe@contoso.com
                        DisplayName: JOHNDOE@CONTOSO.COM
                        UserType: External,
                        PrimaryEmail: alice@contoso0110.onmicrosoft.com
                        DisplayName: ALICE@CONTOSO0110.ONMICROSOFT.COM
                        UserType: External
                        }
TemplateId            :
PolicyExpires         :
EULDuration           :
SendRegistrationEmail : True
NotificationInfo      : Enabled: False
                        DeniedOnly: False
                        Culture:
                        TimeZoneId:
                        TimeZoneOffset: 0
                        TimeZoneDaylightName:
                        TimeZoneStandardName:

RevocationInfo        : Revoked: False
                        RevokedTime:
                        RevokedBy:


PS C:\Users> Get-AadrmTrackingLog -UserEmail "admin@aip500.onmicrosoft.com"

ContentId            : 6326fcb2-c465-4c24-a7f6-1cace7a9cb6f
Issuer               : admin@aip500.onmicrosoft.com
RequestTime          : 3/6/2018 10:45:57 PM
RequesterType        : External
RequesterEmail       : johndoe@contoso.com
RequesterDisplayName : johndoe@contoso.com
RequesterLocation    : IP: 167.220.1.54
                       Country: US
                       City: redmond
                       Position: 47.6812453974602,-122.120736471666

Rights               : {VIEW,OBJMODEL}
Successful           : False
IsHiddenInfo         : False
```

Não há nenhum pesquisa por ObjectID. No entanto, não estão restringidas pelo `-UserEmail` parâmetro e o endereço de e-mail que fornecer não necessita de fazer parte do seu inquilino. Se o endereço de correio eletrónico fornecido é armazenado em qualquer lugar em registos de controlo de documentos, é devolvido entrada de controlo de documentos no resultado do cmdlet.

### <a name="usage-logs-for-the-azure-information-protection-client-and-rms-client"></a>Registos de utilização para o cliente Azure Information Protection e o cliente do RMS

Quando as etiquetas e proteção são aplicadas a documentos e e-mails, endereços de e-mail e os endereços IP podem ser armazenados nos ficheiros de registo no computador de um utilizador nas seguintes localizações:

- Para o cliente Azure Information Protection: %localappdata%\Microsoft\MSIP\Logs

- Para o cliente do RMS: %localappdata%\Microsoft\MSIPC\msip\Logs

Além disso, o cliente Azure Information Protection os registos de dados pessoais para o registo de eventos do Windows local **registos de serviços e aplicações** > **Azure Information Protection**.

Quando o cliente Azure Information Protection é executado scanner, são guardados os dados pessoais %localappdata%\Microsoft\MSIP\Scanner\Reports no computador do servidor do Windows que executa o verificador.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="securing-and-controlling-access-to-personal-information"></a>Proteger e controlar o acesso a informações pessoais
Dados pessoais que poderá ver e especificar no portal do Azure estão acessíveis apenas a utilizadores que tenham sido atribuídos um dos seguintes [funções de administrador do Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
- **Administrador de proteção de informações**

- **Administrador de segurança**

- **Administrador global / administrador de empresa**

Dados pessoais que poderá ver e especifica utilizando o módulo AADRM apenas esteja acessíveis aos utilizadores que tenham sido atribuídos a **administrador de proteção de informações** função ou **Administrador Global / administrador da empresa** funções do Azure Active Directory ou a função de administrador global para o serviço Azure Rights Management.  

## <a name="updating-personal-data"></a>Atualizar dados pessoais

Pode atualizar os endereços de correio eletrónico para políticas de âmbito e as definições de proteção na política do Azure Information Protection. Para obter mais informações, consulte [como configurar a política do Azure Information Protection para utilizadores específicos através da utilização de políticas de âmbito](../deploy-use/configure-policy-scope.md) e [como configurar uma etiqueta para a proteção Rights Management](configure-policy-protection.md). 

Para as definições de proteção, pode atualizar as mesmas informações utilizando cmdlets do PowerShell do [módulo AADRM](/powershell/module/aadrm).

Não é possível atualizar os endereços de correio eletrónico para os utilizadores superutilizadores e os administradores delegados. Em vez disso, remover a conta de utilizador especificada e adicione a conta de utilizador com o endereço de e-mail atualizado. 

### <a name="protection-templates"></a>Modelos de proteção

Execute o [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet para atualizar o modelo de proteção. Porque os dados pessoais estão dentro do `RightsDefinitions` propriedade, também terá de utilizar o [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) cmdlet para criar um objeto de RightsDefinitions com as informações atualizadas e utilizar o RightsDefinitions objeto com o `Set-AadrmTemplateProperty` cmdlet.

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Superutilizadores e os administradores delegados para o serviço Azure Rights Management

Quando precisar de atualizar um endereço de e-mail para um Superutilizador:

1. Utilize [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) para remover o utilizador e o endereço de correio eletrónico antigo.

2. Utilize [Add-AadrmSuperUser](/powershell/module/aadrm/Add-AadrmSuperUser) para adicionar o utilizador e o novo endereço de e-mail.

Quando precisar de atualizar um endereço de e-mail para um administrador delegado:

1. Utilize [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator) para remover o utilizador e o endereço de correio eletrónico antigo.

2. Utilize [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Add-AadrmRoleBasedAdministrator) para adicionar o utilizador e o novo endereço de e-mail.

## <a name="deleting-personal-data"></a>Eliminar dados pessoais
Pode eliminar os endereços de correio eletrónico para políticas de âmbito e as definições de proteção na política do Azure Information Protection. Para obter mais informações, consulte [como configurar a política do Azure Information Protection para utilizadores específicos através da utilização de políticas de âmbito](../deploy-use/configure-policy-scope.md) e [como configurar uma etiqueta para a proteção Rights Management](configure-policy-protection.md). 

Para as definições de proteção, pode eliminar as mesmas informações utilizando cmdlets do PowerShell do [módulo AADRM](/powershell/module/aadrm).

Para eliminar os endereços de correio eletrónico para superutilizadores e os administradores delegados, remova estes utilizadores utilizando o [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) cmdlet e [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator). 

Para eliminar os dados pessoais no registos de controlo de documentos, registos de administração ou os registos de utilização para o serviço Azure Rights Management, utilizam a secção seguinte para emitir um pedido com Support da Microsoft.

Para eliminar os dados pessoais nos ficheiros de registo de cliente e registos de análise que estão armazenados nos computadores, utilize quaisquer ferramentas padrão do Windows para eliminar os ficheiros ou dados pessoais dos ficheiros. 

### <a name="to-delete-personal-data-with-microsoft-support"></a>Para eliminar dados pessoais com Support da Microsoft

Utilize os seguintes três passos para pedir que a Microsoft elimina dados pessoais no registos, registos de administração ou os registos de utilização para o serviço Azure Rights Management de controlo de documentos. 

**Passo 1: Iniciar Eliminar pedido**
[contacte o suporte da Microsoft](../get-started/information-support.md#to-contact-microsoft-support) para abrir um incidente de suporte do Azure Information Protection com um pedido de eliminação de dados do seu inquilino. Tem de provar que é um administrador do seu inquilino do Azure Information Protection e compreender que este processo demora vários dias para confirmar. Ao submeter o pedido, terá de fornecer informações adicionais, consoante os dados que tem de ser eliminado.

- Para eliminar o registo de administração, forneça o **data de fim**. Todos os registos de admin até essa data de fim será eliminada.
- Para eliminar os registos de utilização, forneça o **data de fim**. Utilização de todos os registos de até que a data de fim será eliminada.
- Para eliminar registos de controlo de documentos, forneça o **UserEmail**. Todos os documentos controlo informações relacionadas com o UserEmail serão eliminados.

A eliminação de dados é uma ação permanente. Não há nenhum significa recuperar os dados depois de um pedido de eliminação foi processado. Recomenda-se que os administradores exportar os dados necessários antes de submeter um pedido de eliminação.

**Passo 2: Aguardar pela verificação** a Microsoft irá verificar que o seu pedido para eliminar um ou mais registos é legítimo. Este processo pode demorar até cinco dias úteis.

**Passo 3: Obter a eliminação de** Microsoft suporte ao cliente (CSS) irá enviar um e-mail de confirmação que os dados foram eliminados. 

## <a name="exporting-personal-data"></a>Exportar os dados pessoais
Quando utilizar os cmdlets do PowerShell de AADRM, os dados pessoais são disponibilizados para pesquisa e exportação como um objeto do PowerShell. O objeto do PowerShell pode ser convertido em JSON e guardado utilizando o `ConvertTo-Json` cmdlet.

## <a name="restricting-the-use-of-personal-data-for-profiling-or-marketing-without-consent"></a>Restringir a utilização dos dados pessoais para a criação de perfis ou sem o consentimento de marketing
O Azure Information Protection segue da Microsoft [termos de privacidade](https://privacy.microsoft.com/privacystatement) para criação de perfis ou marketing com base nos dados pessoais.

## <a name="auditing-and-reporting"></a>Auditoria e de relatórios
Apenas os utilizadores que tenham sido atribuídos [permissões de administrador](#securing-and-controlling-access-to-personal-information) pode utilizar o módulo AADRM para pesquisa e exportação de dados pessoais. Estas operações são registadas no registo de administração que pode ser transferido.

Para ações de eliminação, o pedido de suporte atua como a auditoria e relatórios de registo para as ações executadas pela Microsoft. Após a eliminação, os dados eliminados não estarão disponíveis para pesquisa e exportação e o administrador pode verificar isto utilizando os cmdlets Get do módulo AADRM.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
