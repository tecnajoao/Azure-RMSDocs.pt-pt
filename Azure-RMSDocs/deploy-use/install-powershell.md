---
title: Instale o PowerShell para AADRM - AIP
description: Instruções para instalar o Windows PowerShell para o serviço Azure Rights Management do Azure Information Protection. O nome deste módulo é AADRM.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e69714fdb983d7235c7fca940bebc37a14892397
ms.sourcegitcommit: 5892db302bdf96538ecb3af8e3c2f678f5d1ebe2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31817149"
---
# <a name="installing-the-aadrm-powershell-module"></a>Instalar o módulo do AADRM PowerShell

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize as seguintes informações para ajudar a instalar o módulo Windows PowerShell para o serviço Azure Rights Management do Azure Information Protection. O nome deste módulo é AADRM.

Pode utilizar este módulo do PowerShell para administrar o serviço Azure Rights Management na linha de comandos, em qualquer computador que tenha uma ligação à Internet e que cumpra os pré-requisitos indicados na secção seguinte. O Windows PowerShell para o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] suporta o scripting para a automatização ou poderá ser necessário para cenários de configuração avançada. Para obter mais informações sobre as tarefas de administração e as configurações que o módulo suporta, consulte [Administrar o Azure Rights Management utilizando o Windows PowerShell](administer-powershell.md).

## <a name="prerequisites"></a>Pré-requisitos
Esta tabela lista os pré-requisitos para instalar e utilizar o módulo do AADRM PowerShell para o serviço Azure Rights Management do Azure Information Protection.

|Requisito|Mais informações|
|---------------|--------------------|
|Versão mínima do Windows PowerShell: 3.0|Pode confirmar a versão do Windows PowerShell que está a executar, escrevendo `$PSVersionTable` numa sessão do PowerShell. <br /><br /> Se precisar de instalar uma versão posterior do Windows PowerShell, consulte [atualizar existentes do Windows PowerShell](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell).|
|Versão mínima do Microsoft .NET Framework: 4.5<br /><br />Nota: esta versão do Microsoft .NET Framework está incluída em sistemas operativos posteriores, pelo que apenas deve instalá-la manualmente se o sistema operativo cliente for inferior ao Windows 8.0 ou o sistema operativo do servidor for inferior ao Windows Server 2012.|Se a versão mínima do Microsoft .NET Framework não estiver já instalada, pode transferir o [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Esta versão mínima do Microsoft .NET Framework é necessário para algumas das classes que utiliza o módulo AADRM.|

A partir da versão 2.5.0.0 do módulo AADRM, o assistente Microsoft Online Services início de sessão já não é necessário.

> [!NOTE]
> 
> Se tiver instalado uma versão do módulo AADRM com a ferramenta de administração do Azure Rights Management, utilize **programas e funcionalidades** desinstalar **administração de gestão do Windows Azure AD Rights** antes Instale a versão mais recente do módulo AADRM da galeria do PowerShell.


## <a name="how-to-install-the-aadrm-module"></a>Como instalar o módulo AADRM

O módulo AADRM foi movido para o [galeria do PowerShell](/powershell/gallery/readme) e já não está disponível a Microsoft Download Center. 

### <a name="to-install-the-aadrm-module-from-the-powershell-gallery"></a>Para instalar o módulo AADRM da galeria do PowerShell

Se estiver familiarizado com a galeria do PowerShell, consulte o artigo [introdução à galeria do PowerShell](/powershell/gallery/psgallery/psgallery_gettingstarted). Siga as instruções para os requisitos de galeria, que incluem a instalar o módulo de PowerShellGet e o fornecedor do NuGet.

Para ver detalhes sobre o módulo AADRM na galeria do PowerShell, visite o [página AADRM](https://www.powershellgallery.com/packages/AADRM).

Para instalar o módulo AADRM, inicie uma sessão do PowerShell com o **executar como administrador** opção e escreva:

    Install-Module -Name AADRM

Se estiver avisado sobre a instalação de um repositório não fidedigno, pode premir Y para confirmar. Em alternativa, prima N e configurar a galeria do PowerShell como um repositório fidedigno, utilizando o comando `Set-PSRepository -Name PSGallery -InstallationPolicy Trusted` e, em seguida, volte a executar o comando para instalar o módulo AADRM.  

Se tiver uma versão anterior do módulo AADRM instalado a partir da galeria, a atualização para a versão mais recente, escrevendo:

    Update-Module -Name AADRM


## <a name="next-steps"></a>Próximos passos
Numa sessão do Windows PowerShell, confirme a versão do módulo instalado. Esta verificação é particularmente importante se tiver atualizado de uma versão mais antiga:

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

Antes de poder executar quaisquer comandos para configurar o serviço [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], tem de ligar ao serviço através do cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice). Quando terminar de executar os comandos de configuração, como melhor prática, encerre o serviço através do cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice). Se não desligar, a ligação é automaticamente desligada após um período de inatividade. Devido ao comportamento de desativação automático, pode ter de voltar a ligar ocasionalmente numa sessão do PowerShell. 

> [!NOTE]
> Se ainda não ativou o serviço Azure Rights Management, pode fazê-lo depois de ligar ao serviço, através do cmdlet [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]