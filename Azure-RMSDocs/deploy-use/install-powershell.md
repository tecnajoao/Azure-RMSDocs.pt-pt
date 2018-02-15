---
title: "Instalar o PowerShell para o Azure Rights Management – AIP"
description: "Instruções para instalar o Windows PowerShell para o serviço Azure Rights Management do Azure Information Protection. O nome deste módulo é AADRM."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5946ab7315b646abf119cb32cd66ac62535253c9
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2018
---
# <a name="installing-windows-powershell-for-azure-rights-management"></a>Instalar o Windows PowerShell para o Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

Utilize as seguintes informações para ajudar a instalar o módulo Windows PowerShell para o serviço Azure Rights Management do Azure Information Protection.

Pode utilizar este módulo do PowerShell para administrar o serviço Azure Rights Management na linha de comandos, em qualquer computador que tenha uma ligação à Internet e que cumpra os pré-requisitos indicados na secção seguinte. O Windows PowerShell para o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] suporta o scripting para a automatização ou poderá ser necessário para cenários de configuração avançada. Para obter mais informações sobre as tarefas de administração e as configurações que o módulo suporta, consulte [Administrar o Azure Rights Management utilizando o Windows PowerShell](administer-powershell.md).

## <a name="prerequisites"></a>Pré-requisitos
Esta tabela lista os pré-requisitos para instalar e utilizar o Windows PowerShell para o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

|Requisito|Mais informações|
|---------------|--------------------|
|Uma versão do Windows que suporte o módulo de administração do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]|Verifique a lista de sistemas operativos suportados na secção **Requisitos de Sistema** da [página de transferência da Ferramenta de Administração do Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Versão mínima do Windows PowerShell: 3.0|Pode confirmar a versão do Windows PowerShell que está a executar, escrevendo `$PSVersionTable` numa sessão do PowerShell. <br /><br /> Se precisar de instalar uma versão posterior do Windows PowerShell, consulte [atualizar existentes do Windows PowerShell](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell).|
|Versão mínima do Microsoft .NET Framework: 4.5<br /><br />Nota: esta versão do Microsoft .NET Framework está incluída em sistemas operativos posteriores, pelo que apenas deve instalá-la manualmente se o sistema operativo cliente for inferior ao Windows 8.0 ou o sistema operativo do servidor for inferior ao Windows Server 2012.|Se a versão mínima do Microsoft .NET Framework não estiver já instalada, pode transferir o [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Esta versão mínima do Microsoft .NET Framework é necessária para algumas das classes que o módulo de administração do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] utiliza.|

> [!NOTE]
> A partir da versão 2.5.0.0 do módulo de administração do Rights Management, o Assistente de Início de Sessão do Microsoft Online Services já não é necessário.
> 
> Se tiver uma versão anterior do módulo de administração do Rights Management instalada, utilize **Programas e Funcionalidades** para desinstalar a **Administração do Microsoft Azure AD Rights Management** antes de instalar a versão mais recente.


## <a name="how-to-install-the-rights-management-administration-module"></a>Como instalar o módulo de administração do Rights Management

1. Vá para a Microsoft Download Center e localize o [ferramenta de administração do Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721), que contém o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] módulo de administração para o Windows PowerShell.

2. Transfira e guarde o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] ficheiro instalador, **WindowsAzureADRightsManagementAdministration_x64**. Em seguida, faça duplo clique este ficheiro para iniciar o Azure AD Rights Management administração Assistente de configuração.

3.  Conclua o assistente.

O Windows PowerShell para o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] está agora instalado.

## <a name="next-steps"></a>Próximos passos
Inicie uma sessão do Windows PowerShell e confirme a versão do módulo instalado. Esta verificação é particularmente importante se tiver atualizado de uma versão mais antiga:

```
(Get-Module AADRM –ListAvailable).Version
```

Nota: se este comando falhar, execute primeiro **Import-Module AADRM**.

Para ver os cmdlets disponíveis, escreva o seguinte:

```
Get-Command -Module AADRM
```

Utilize o comando `Get-Help <cmdlet_name>` para ver a Ajuda de um cmdlet específico e utilize o parâmetro **-online** para ver a ajuda mais recente no site de documentação da Microsoft. Por exemplo:

```
Get-Help Connect-AadrmService -online
```


Para obter mais informações:

-   Lista completa de cmdlets disponíveis: [Módulo AADRM](/powershell/aadrm/vlatest/rightsmanagement)

-   Lista dos principais cenários de configuração que suportam o PowerShell: [Administrar o Azure Rights Management ao Utilizar o Windows PowerShell](administer-powershell.md)

Antes de poder executar quaisquer comandos para configurar o serviço [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], tem de ligar ao serviço através do cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice). 

Quando terminar de executar os comandos de configuração, como melhor prática, encerre o serviço através do cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice). Se não desligar, a ligação é automaticamente desligada após um período de inatividade. Devido ao comportamento de desativação automático, pode ter de voltar a ligar ocasionalmente numa sessão do PowerShell. 

> [!NOTE]
> Se ainda não ativou o serviço Azure Rights Management, pode fazê-lo depois de ligar ao serviço, através do cmdlet [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]