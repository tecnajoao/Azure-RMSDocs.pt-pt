---
title: Instalar o PowerShell para o AADRM – AIP
description: Instruções para instalar o Windows PowerShell para o serviço Azure Rights Management do Azure Information Protection. O nome deste módulo é AADRM.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 8809524c197321840016e2db4347b0c37154e352
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305357"
---
# <a name="installing-the-aadrm-powershell-module"></a>Instalar o módulo do PowerShell do AADRM

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize as seguintes informações para ajudar a instalar o módulo do Windows PowerShell para o serviço Azure Rights Management do Azure Information Protection. O nome deste módulo é AADRM.

Pode utilizar este módulo do PowerShell para administrar o serviço Azure Rights Management na linha de comandos, em qualquer computador que tenha uma ligação à Internet e que cumpra os pré-requisitos indicados na secção seguinte. Windows PowerShell para o Azure Rights Management suporta a criação de scripts para a automatização ou poderá ser necessário para cenários de configuração avançada. Para obter mais informações sobre as tarefas de administração e as configurações que o módulo suporta, consulte [Administrar o Azure Rights Management utilizando o Windows PowerShell](administer-powershell.md).

## <a name="prerequisites"></a>Pré-requisitos
Esta tabela lista os pré-requisitos para instalar e utilizar o módulo do PowerShell do AADRM para o serviço Azure Rights Management do Azure Information Protection.

|Requisito|Mais informações|
|---------------|--------------------|
|Versão mínima do Windows PowerShell: 3.0|Pode confirmar a versão do Windows PowerShell que está a executar, escrevendo `$PSVersionTable` numa sessão do PowerShell. <br /><br /> Se precisar de instalar uma versão posterior do Windows PowerShell, consulte [existentes do Windows PowerShell a atualizar](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell).|
|Versão mínima do Microsoft .NET Framework: 4.5<br /><br />Nota: Esta versão do Microsoft .NET Framework está incluída em sistemas de operativos posteriores, pelo que deve tem de instalá-la manualmente apenas se o sistema operativo cliente for inferior ao Windows 8.0 ou seu sistema operativo do servidor é menor que o Windows Server 2012.|Se a versão mínima do Microsoft .NET Framework não estiver já instalada, pode transferir o [Microsoft .NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Esta versão mínima do Microsoft .NET Framework é necessário para algumas das classes que utiliza o módulo do AADRM.|

A partir da versão 2.5.0.0 do módulo do AADRM, o assistente Microsoft Online Services início de sessão já não é necessário.

> [!NOTE]
> 
> Se instalou uma versão do módulo do AADRM com a ferramenta de administração do Azure Rights Management, utilize **programas e funcionalidades** desinstalar **administração de gestão de direitos do Windows Azure AD** antes de Instale a versão mais recente do módulo do AADRM da galeria do PowerShell.


## <a name="how-to-install-the-aadrm-module"></a>Como instalar o módulo do AADRM

O módulo do AADRM foi movido para o [galeria do PowerShell](/powershell/gallery/readme) e já não está disponível no Microsoft Download Center. 

### <a name="to-install-the-aadrm-module-from-the-powershell-gallery"></a>Para instalar o módulo do AADRM a partir da galeria do PowerShell

Se estiver familiarizado com a galeria do PowerShell, veja [começar com a galeria do PowerShell](/powershell/gallery/psgallery/psgallery_gettingstarted). Siga as instruções para os requisitos de galeria, que incluem a instalar o módulo PowerShellGet e o fornecedor de NuGet.

Para ver detalhes sobre o módulo do AADRM na galeria do PowerShell, visite o [página do AADRM](https://www.powershellgallery.com/packages/AADRM).

Para instalar o módulo do AADRM, iniciar uma sessão do PowerShell com o **executar como administrador** opção e escreva:

    Install-Module -Name AADRM

Se é avisado sobre a instalação a partir de um repositório não confiável, pode pressionar Y para confirmar. Ou, prima N e configure a galeria do PowerShell como um repositório fidedigno, utilizando o comando `Set-PSRepository -Name PSGallery -InstallationPolicy Trusted` e, em seguida, volte a executar o comando para instalar o módulo do AADRM.  

Se tiver uma versão anterior do módulo do AADRM instalado a partir da galeria, a atualização para a versão mais recente ao escrever:

    Update-Module -Name AADRM


## <a name="next-steps"></a>Passos Seguintes
Numa sessão do Windows PowerShell, certifique-se a versão do módulo instalado. Esta verificação é particularmente importante se tiver atualizado de uma versão mais antiga:

```
(Get-Module AADRM –ListAvailable).Version
```

Nota: Se este comando falhar, execute primeiro **Import-Module AADRM**.

Para ver os cmdlets disponíveis, escreva o seguinte:

```
Get-Command -Module AADRM
```

Utilize o comando `Get-Help <cmdlet_name>` para ver a Ajuda de um cmdlet específico e utilize o parâmetro **-online** para ver a ajuda mais recente no site de documentação da Microsoft. Por exemplo:

```
Get-Help Connect-AadrmService -online
```

Para obter mais informações:

-   Lista completa dos cmdlets disponíveis: [Módulo AADRM](/powershell/aadrm/vlatest/rightsmanagement)

-   Lista de principais cenários de configuração que suportam o PowerShell: [Administrar o Azure Rights Management ao Utilizar o Windows PowerShell](administer-powershell.md)

Antes de poder executar quaisquer comandos para configurar o serviço Azure Rights Management, tem de ligar ao serviço, utilizando o [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) cmdlet. Quando terminar de executar os comandos de configuração, como melhor prática, encerre o serviço através do cmdlet [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice). Se não desligar, a ligação é automaticamente desligada após um período de inatividade. Devido ao comportamento de desativação automático, pode ter de voltar a ligar ocasionalmente numa sessão do PowerShell. 

> [!NOTE]
> Se ainda não ativou o serviço Azure Rights Management, pode fazê-lo depois de ligar ao serviço, através do cmdlet [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm).

