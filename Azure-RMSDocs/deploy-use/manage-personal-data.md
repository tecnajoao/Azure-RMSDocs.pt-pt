---
title: Gerir dados pessoais para o Azure Information Protection
description: Informações sobre os dados pessoais que são utilizados pelo Azure Information Protection e como pode exibir, exportar e eliminá-lo.
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
ms.openlocfilehash: f42e1318e8be0d805216cffd402a9b87a1259e1e
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39473853"
---
# <a name="manage-personal-data-for-azure-information-protection"></a>Gerir dados pessoais para o Azure Information Protection

Ao configurar e utilizar o Azure Information Protection, endereços de e-mail e endereços IP são utilizados e armazenados pelo serviço do Azure Information Protection. Estes dados pessoais podem ser encontrados nos seguintes itens:

- A política do Azure Information Protection

- Modelos de proteção para o serviço Azure Rights Management

- Superutilizadores e os administradores delegados para o serviço Azure Rights Management 

- Registos de administração para o serviço Azure Rights Management

- Registos de utilização para o serviço Azure Rights Management

- Registos de controlo de documentos

- Registos de utilização para o cliente Azure Information Protection e o cliente de RMS 


[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]


## <a name="viewing-personal-data-that-azure-information-protection-uses"></a>Ver os dados pessoais que utiliza o Azure Information Protection

Utilizar o portal do Azure, um administrador pode especificar endereços de e-mail para políticas de âmbito e para as definições de proteção dentro de uma configuração de etiqueta. Para obter mais informações, consulte [como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito](../deploy-use/configure-policy-scope.md) e [como configurar uma etiqueta para proteção do Rights Management](configure-policy-protection.md). 

Para etiquetas que estão configuradas para aplicar a proteção contra o serviço Azure Rights Management, endereço de e-mail também é possível encontrar nos modelos de proteção, utilizando cmdlets do PowerShell do [módulo AADRM](/powershell/module/aadrm). Este módulo do PowerShell também permite que um administrador especificar utilizadores por endereço de e-mail para ser um [Superutilizador](../deploy-use/configure-super-users.md), ou um administrador do serviço Azure Rights Management. 

Quando o Azure Information Protection é utilizado para classificar e proteger documentos e e-mails, endereços de e-mail e dos utilizadores pode ser guardado em ficheiros de registo.


### <a name="protection-templates"></a>Modelos de proteção

Executar o [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) cmdlet para obter uma lista de modelos de proteção. Pode utilizar o ID do modelo para obter detalhes de um modelo específico. O `RightsDefinitions` objeto apresenta os dados pessoais, se aplicável. 

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

Executar o [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser) cmdlet e [Get-AadrmRoleBasedAdministrator](/powershell/module/aadrm/get-aadrmrolebasedadministrator) cmdlet para ver quais os utilizadores que foram atribuídos a função de utilizador super ou a função de administrador global para o Azure Rights Management serviço. Para os utilizadores que tenham sido atribuídos a qualquer uma destas funções, os respetivos endereços de e-mail são apresentados.


### <a name="administration-logs-for-the-azure-rights-management-service"></a>Registos de administração para o serviço Azure Rights Management

Executar o [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) cmdlet para obter um registo de ações de administração para o serviço Azure Rights Management, que protege os dados do Azure Information Protection. Este registo inclui os dados pessoais na forma de endereços de e-mail e endereços IP. O registo está em texto não criptografado e depois de ser transferido, os detalhes de um administrador específico podem ser pesquisados offline.

Por exemplo:
```
PS C:\Users> Get-AadrmAdminLog -Path '.\Desktop\admin.log' -FromTime 4/1/2018 -ToTime 4/30/2018 -Verbose
The Rights Management administration log was successfully generated and can be found at .\Desktop\admin.log.
```

### <a name="usage-logs-for-the-azure-rights-management-service"></a>Registos de utilização para o serviço Azure Rights Management
Executar o [Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog) cmdlet para obter um log de ações de utilizador final que utilizam o serviço Azure Rights Management. Este serviço protege os dados do Azure Information Protection. O registo pode incluir dados pessoais na forma de endereços de e-mail e endereços IP. O registo está em texto não criptografado e depois de ser transferido, os detalhes de um administrador específico podem ser pesquisados offline.

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

### <a name="document-tracking-logs"></a>Registos de controlo de documentos

Executar o [Get-AadrmDocumentLog](/powershell/module/aadrm/get-aadrmdocumentlog) cmdlet para obter informações a partir do site sobre um utilizador específico de controlo de documentos. Para obter informações associadas com os registos de documento de controlo, utilize o [Get-AadrmTrackingLog](/powershell/module/aadrm/get-aadrmtrackinglog?view=azureipps) cmdlet.

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

Não há nenhuma pesquisa por ObjectID. No entanto, não está limitado pelo `-UserEmail` parâmetro e o endereço de e-mail indicado não precisa de ser parte do seu inquilino. Se o endereço de e-mail fornecido é armazenado em qualquer lugar nos registos de controlo de documentos, entrada de controlo de documentos é devolvido no resultado do cmdlet.

### <a name="usage-logs-for-the-azure-information-protection-client-and-rms-client"></a>Registos de utilização para o cliente Azure Information Protection e o cliente de RMS

Quando as etiquetas e proteção são aplicadas a documentos e e-mails, endereços de e-mail e endereços IP podem ser armazenados nos ficheiros de registo no computador de um usuário nas seguintes localizações:

- Para o cliente do Azure Information Protection: %localappdata%\Microsoft\MSIP\Logs

- Para o cliente do RMS: %localappdata%\Microsoft\MSIPC\msip\Logs

Além disso, o cliente do Azure Information Protection regista a estes dados pessoais para o registo de eventos do Windows local **Applications and Services Logs** > **do Azure Information Protection**.

Quando o cliente do Azure Information Protection é executado o scanner, os dados pessoais é salvo em %localappdata%\Microsoft\MSIP\Scanner\Reports no computador Windows Server que executa a deteção de impressão.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="securing-and-controlling-access-to-personal-information"></a>Protegendo e controlando o acesso a informações pessoais
Os dados pessoais que ver e especifica no portal do Azure são acessíveis apenas a utilizadores que tenham sido atribuídos um dos seguintes [funções de administrador do Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
- **Administrador do Information Protection**

- **Administrador de segurança**

- **Administrador global / administrador de empresa**

Os dados pessoais que ver e especifica com o módulo do AADRM estão acessíveis apenas para os utilizadores que foram atribuídos a **administrador do Information Protection** função ou **Administrador Global / administrador da empresa** funções do Azure Active Directory ou a função de administrador global para o serviço Azure Rights Management.  

## <a name="updating-personal-data"></a>A atualizar os dados pessoais

Pode atualizar os endereços de e-mail para políticas de âmbito e as definições de proteção na política do Azure Information Protection. Para obter mais informações, consulte [como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito](../deploy-use/configure-policy-scope.md) e [como configurar uma etiqueta para proteção do Rights Management](configure-policy-protection.md). 

Para as definições de proteção, pode atualizar as mesmas informações utilizando cmdlets do PowerShell do [módulo AADRM](/powershell/module/aadrm).

Não é possível atualizar os endereços de e-mail para os superutilizadores e os administradores delegados. Em vez disso, remova a conta de utilizador especificada e adicione a conta de utilizador com o endereço de e-mail atualizado. 

### <a name="protection-templates"></a>Modelos de proteção

Executar o [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet para atualizar o modelo de proteção. Porque os dados pessoais estão dentro do `RightsDefinitions` propriedade, também terá de utilizar o [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) cmdlet para criar um objeto de RightsDefinitions com as informações atualizadas e usar o RightsDefinitions objeto com o `Set-AadrmTemplateProperty` cmdlet.

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Superutilizadores e os administradores delegados para o serviço Azure Rights Management

Quando precisa de atualizar um endereço de e-mail para um Superutilizador:

1. Uso [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) para remover o utilizador e o endereço de e-mail antigo.

2. Uso [Add-AadrmSuperUser](/powershell/module/aadrm/Add-AadrmSuperUser) para adicionar o utilizador e o novo endereço de e-mail.

Quando precisa de atualizar um endereço de e-mail para um administrador delegado:

1. Uso [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator) para remover o utilizador e o endereço de e-mail antigo.

2. Uso [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Add-AadrmRoleBasedAdministrator) para adicionar o utilizador e o novo endereço de e-mail.

## <a name="deleting-personal-data"></a>A eliminar os dados pessoais
Pode excluir endereços de e-mail para políticas de âmbito e as definições de proteção na política do Azure Information Protection. Para obter mais informações, consulte [como configurar a política do Azure Information Protection para utilizadores específicos com políticas de âmbito](../deploy-use/configure-policy-scope.md) e [como configurar uma etiqueta para proteção do Rights Management](configure-policy-protection.md). 

Para as definições de proteção, pode eliminar as mesmas informações utilizando cmdlets do PowerShell do [módulo AADRM](/powershell/module/aadrm).

Para eliminar os endereços de e-mail para superutilizadores e os administradores delegados, remova estes utilizadores utilizando o [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) cmdlet e [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator). 

Para eliminar os dados pessoais em registos de controlo de documentos, registos de administração ou registos de utilização para o serviço Azure Rights Management, utilizam a secção seguinte para emitir um pedido com Support da Microsoft.

Para eliminar os dados pessoais nos ficheiros de registo de cliente e registos de scanner, que estão armazenados nos computadores, utilize qualquer ferramentas padrão do Windows para eliminar os ficheiros ou dados pessoais dos ficheiros. 

### <a name="to-delete-personal-data-with-microsoft-support"></a>Para eliminar os dados pessoais com Support da Microsoft

Utilize os seguintes três passos para pedir que a Microsoft elimina os dados pessoais em registos, de logs de administração ou registos de utilização para o serviço Azure Rights Management de controlo de documentos. 

**Passo 1: Iniciar Eliminar pedido**
[contacte o suporte da Microsoft](../information-support.md#to-contact-microsoft-support) para abrir um incidente de suporte do Azure Information Protection com um pedido para a eliminação de dados do seu inquilino. Tem de provar que é um administrador inquilino do Azure Information Protection e compreender que este processo demorará vários dias para confirmar. Ao submeter o pedido, terá de fornecer informações adicionais, consoante os dados que precisam de eliminar.

- Para eliminar o registo de administração, forneça o **data de fim**. Todos os registos de administrador, até que a data de fim serão eliminados.
- Para eliminar os registos de utilização, forneça o **data de fim**. Todos os registos da utilização até que a data de fim será eliminada.
- Para eliminar registos de controlo de documentos, forneça o **UserEmail**. Obter informações relacionadas com o UserEmail o controlo de todos os documentos serão eliminados.

A eliminar estes dados é uma ação permanente. Não há nenhum modo de recuperar os dados após o processamento de um pedido de eliminação. Recomenda-se que os administradores exportar os dados necessários antes de submeter um pedido de eliminação.

**Passo 2: Aguardar pela verificação** a Microsoft irá verificar se o seu pedido para eliminar um ou mais registos é legítimo. Este processo pode demorar até cinco dias úteis.

**Passo 3: Obter a confirmação da eliminação** serviços de suporte ao cliente da Microsoft (CSS) enviar-lhe um e-mail de confirmação que os dados foram eliminados. 

## <a name="exporting-personal-data"></a>Exportar os dados pessoais
Ao utilizar os cmdlets do PowerShell do AADRM, os dados pessoais são disponibilizados para pesquisa e exportação como um objeto do PowerShell. O objeto do PowerShell pode ser convertido em JSON e salvos usando o `ConvertTo-Json` cmdlet.

## <a name="restricting-the-use-of-personal-data-for-profiling-or-marketing-without-consent"></a>Restringir a utilização de dados pessoais para a criação de perfis ou de marketing sem consentimento
O Azure Information Protection segue da Microsoft [termos de privacidade](https://privacy.microsoft.com/privacystatement) para criação de perfis ou de marketing com base nos dados pessoais.

## <a name="auditing-and-reporting"></a>Auditoria e relatórios
Apenas os utilizadores que foram atribuídos [permissões de administrador](#securing-and-controlling-access-to-personal-information) pode utilizar o módulo do AADRM para pesquisa e exportação de dados pessoais. Estas operações são registradas no log de administração que pode ser transferido.

Para ações de eliminação, o pedido de suporte atua como a auditoria e relatórios do registo de ações realizadas pela Microsoft. Após a eliminação, os dados eliminados não estarão disponíveis para a pesquisa e a exportação e o administrador pode verificar isto utilizando os cmdlets Get do módulo do AADRM.

