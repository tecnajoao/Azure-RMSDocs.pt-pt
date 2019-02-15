---
title: Instalar o cliente do Azure Information Protection para utilizadores
description: Instruções e informações para administradores implementar o cliente de Azure Information Protection para Windows em redes corporativas.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 01/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ea3ec965-3720-4614-8564-3ecfe60bc175
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: f1f111b0f5e6c534f005dae5725211f9035377ec
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56257081"
---
# <a name="admin-guide-install-the-azure-information-protection-client-for-users"></a>Guia do administrador: Instalar o cliente do Azure Information Protection para utilizadores

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Antes de instalar o cliente do Azure Information Protection na sua rede empresarial, verifique que os computadores têm as versões de sistema operativo necessária e as aplicações do Azure Information Protection: [Requisitos do Azure Information Protection](../requirements.md). 

Em seguida, verifique os pré-requisitos adicionais que podem ser necessários para o cliente do Azure Information Protection, conforme documentado na próxima seção. Nem todos os pré-requisitos são verificados pelo programa de instalação.

## <a name="additional-prerequisites-for-the-azure-information-protection-client"></a>Pré-requisitos adicionais para o cliente do Azure Information Protection

- Microsoft .NET Framework 4.6.2
    
    A instalação completa do cliente do Azure Information Protection, por predefinição, requer a versão mínima do Microsoft .NET Framework 4.6.2 e se esta estiver em falta, o Assistente de configuração a partir do instalador executável tentará transferir e instalar este pré-requisito. Quando este pré-requisito é instalado como parte da instalação do cliente, o computador tem de ser reiniciado. Embora não seja recomendado, pode ignorar este pré-requisito quando utiliza o Assistente de configuração ao utilizar um [parâmetro de instalação personalizada](#more-information-about-the-downgradedotnetrequirement-installation-parameter).
    
    Este pré-requisito não é instalado automaticamente quando instala automaticamente o cliente utilizando o instalador executável, o Windows Update ou o instalador do Windows. Nestes cenários, tem de instalar este pré-requisito separadamente se for necessário, ou a instalação falha. Pode transferir o Microsoft .NET Framework 4.6.2 (Offline instalador) a partir da [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53344).

- Microsoft .NET Framework 4.5.2
    
    Se o Visualizador do Azure Information Protection está instalado em separado, isto requer a versão mínima do Microsoft .NET Framework 4.5.2 e se esta estiver em falta, o instalador executável não transferir nem instalá-lo.

- Versão do Windows PowerShell 4.0
    
    O módulo do PowerShell para o cliente requer o Windows PowerShell versão 4.0, que poderá ter de ser instalado em sistemas operativos mais antigos. Para obter mais informações, veja [Como Instalar o Windows PowerShell 4.0](https://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx). O instalador não verifica nem instala este pré-requisito automaticamente. Para verificar que versão do Windows PowerShell está a executar, escreva `$PSVersionTable` numa sessão do PowerShell.

- Resolução de ecrã superior a 800 x 600
    
    Resoluções de 800 x 600 e inferiores totalmente não é possível apresentar os **classificar e proteger – Azure Information Protection** caixa de diálogo quando faça duplo clique de um ficheiro ou pasta no Explorador de ficheiros.


- Assistente de Início de Sessão do Microsoft Online Services 7.250.4303.0
    
    Os computadores com o Office 2010 necessitam do Assistente de Início de Sessão do Microsoft Online Services versão 7.250.4303.0. Esta versão está incluída na instalação do cliente. Se tiver uma versão posterior do Assistente de Início de Sessão, desinstale-a antes de instalar o cliente do Azure Information Protection. Por exemplo, verifique a versão e desinstale o Assistente de Início de Sessão através do **Painel de Controlo** > **Programa e Funcionalidades** > **Desinstalar ou alterar um programa**.

- KB 2533623
    
    Os computadores que executem o Windows 7 Service Pack 1 requerem a KB 2533623. Para obter mais informações sobre esta atualização, consulte [aviso de segurança da Microsoft: Carregamento de bibliotecas não seguro pode permitir a execução de código remoto](https://support.microsoft.com/en-us/kb/2533623). Poderá instalar diretamente esta atualização ou ser substituída por outra atualização que a instala por si.
    
    Se esta atualização for obrigatória e não estiver instalada, a instalação do cliente avisa-o de que tem de ser instalada. Esta atualização pode ser instalada após a instalação do cliente, mas algumas ações serão bloqueadas e a mensagem é apresentada novamente.  

- Visual C++ Redistributable para Visual Studio 2015 (versão de 32 bits)
    
    Para computadores que executam o Windows 7 Service Pack 1, instale **vc_redist.x86.exe** página de transferência entre as seguintes opções: [Visual C++ Redistributable para Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145)
    
    A instalação do cliente não verifica este pré-requisito, mas é necessário para o cliente do Azure Information Protection classificar e proteger ficheiros PDF.

- Configurar a política de grupo para impedir que o suplemento para o Azure Information Protection que está a ser desativada
    
    Para o Office 2013 e versões posteriores, configure a política de grupo para garantir que o **Microsoft Azure Information Protection** suplemento para aplicativos do Office está sempre ativada. Sem esta configuração, o suplemento do Microsoft Azure Information Protection pode obter desativado e os utilizadores não poderão etiquetar os documentos e e-mails na sua aplicação do Office.
    
    - Para o Outlook: Usar a diretiva de grupo documentados em [controlo de administrador de sistema sobre suplementos](https://docs.microsoft.com/office/vba/outlook/concepts/getting-started/support-for-keeping-add-ins-enabled#system-administrator-control-over-add-ins) na documentação do Office.
    
    - Para Word, Excel e PowerPoint: Utilizar a definição de política de grupo **lista de suplementos gerenciados** documentados no artigo de suporte [Add-ins carregados devido a definições de política de grupo para programas do Office 2013 e Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off). 
        
        Especifique os seguintes identificadores programáticos (ProgID) para o Azure Information Protection e definir a opção **1: O suplemento está sempre ativado**.
        
        Para o Word: `MSIP.WordAddin`
        
        Para o Excel: `MSIP.ExcelAddin`
        
        Para o PowerPoint: `MSIP.PowerPointAddin`

> [!IMPORTANT]
> A instalação do cliente do Azure Information Protection requer permissões administrativas locais.


## <a name="options-to-install-the-azure-information-protection-client-for-users"></a>Opções para instalar o cliente do Azure Information Protection para os utilizadores

Existem duas opções para instalar o cliente para utilizadores:

**Executar a versão do executável (.exe) do cliente**: O método de instalação recomendado que pode executar interativamente ou silenciosamente. Este método tem mais flexibilidade e é recomendado porque o instalador verifica muitos dos pré-requisitos e pode instalar automaticamente pré-requisitos ausentes. [Instruções](#to-install-the-azure-information-protection-client-by-using-the-executable-installer)

**Implementar a versão do Windows installer (MSI) do cliente**: Suporte para instalações silenciosas apenas que utilizam um mecanismo de implementação central, como diretiva de grupo, o Configuration Manager e o Microsoft Intune. Este método é necessário para computadores com Windows 10 geridos pelo Intune e pela gestão de dispositivos móveis (MDM) porque para estes computadores, os ficheiros executáveis não têm suporte para instalação. No entanto, quando utilizar este método de instalação, deve verificar e instalar manualmente ou desinstalar o software dependente que o instalador do executável deve executar para cada computador. [Instruções](#to-install-the-azure-information-protection-client-by-using-the-msi-installer)

Depois do Azure Information Protection é instalado, pode atualizar este cliente, repetindo o seu método de instalação escolhido, ou utilizar o Windows Update para manter o cliente atualizado automaticamente. Para obter mais informações sobre a atualização, consulte a [Upgrading e manter o cliente do Azure Information Protection](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client) secção.

### <a name="to-install-the-azure-information-protection-client-by-using-the-executable-installer"></a>Instalar o cliente do Azure Information Protection através do instalador executável

Utilize as instruções a seguir para instalar o cliente quando não estiver a utilizar o catálogo do Microsoft Update ou implemente o .msi com um método de implementação central como o Intune.

1. Transfira a versão executável do cliente do Azure Information Protection a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 
    
    Se existir uma versão de pré-visualização disponível, mantenha esta versão apenas para teste. Não se destina a utilizadores finais num ambiente de produção. 

2. Para uma instalação predefinida, basta executar o ficheiro **AzInfoProtection.exe**, por exemplo. Porém, para ver as opções de instalação, execute primeiro o ficheiro com **/help**: `AzInfoProtection.exe /help`

    Exemplo de como instalar automaticamente o cliente: `AzInfoProtection.exe /quiet`
    
    Exemplo de como instalar automaticamente apenas os cmdlets do PowerShell: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
    
    Parâmetros adicionais que não estão listados no ecrã de ajuda:
    
    - **ServiceLocation**: Utilize este parâmetro se estiver a instalar o cliente em computadores que executam o Office 2010 e os utilizadores não sejam administradores locais em seus computadores ou não pretender que lhes seja pedido. [Mais informações](#more-information-about-the-servicelocation-installation-parameter) 
    
    - **DowngradeDotNetRequirement**: Utilize este parâmetro para contornar o requisito do Microsoft Framework .NET versão 4.6.2. [Mais informações](#more-information-about-the-downgradedotnetrequirement-installation-parameter)
    
    - **AllowTelemetry=0**: Utilize este parâmetro para desativar a opção de instalação **ajude a melhorar o Azure Information Protection ao enviar estatísticas de utilização à Microsoft**. 
    
3. Se estiver a instalar interativamente, selecione a opção para instalar uma **política de demonstração** se não puder ligar-se ao Office 365 ou ao Azure Active Directory e quiser ver e experimentar o lado do cliente do Azure Information Protection com uma política local para efeitos de demonstração. Quando o cliente se liga a um serviço Azure Information Protection, esta política de demonstração é substituída pela política do Azure Information Protection da organização.
    
4. Para concluir a instalação: 

    - Se o computador estiver a executar o Office 2010, reinicie o computador. 
        
        Se o cliente não tiver sido instalado com o parâmetro ServiceLocation, quando abre uma das aplicações do Office que utilizam a barra do Azure Information Protection (por exemplo, o Word) pela primeira vez, terá de confirmar todos os pedidos para atualizar o registo para esta primeira utilização. A [deteção do serviço](client-deployment-notes.md#rms-service-discovery) é utilizada para preencher as chaves de registo. 
    
    - Para outras versões do Office, reinicie todas as aplicações do Office e todas as instâncias do Explorador de Ficheiros. 
        
5. Pode confirmar que a instalação foi concluída com êxito ao verificar o ficheiro de registo de instalação que, por predefinição, é criado na pasta %temp%. Pode alterar esta localização com o parâmetro de instalação **/log**. 
 
    Este ficheiro tem o seguinte formato de nomes: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`
    
    Por exemplo: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    Neste ficheiro de registo, procure a seguinte cadeia: **Produto: Microsoft Azure Information Protection-- Instalação concluída com êxito.** Se a instalação falhou, este ficheiro de registo contém detalhes que o ajudam a identificar e resolver qualquer tipo de problemas.

#### <a name="more-information-about-the-servicelocation-installation-parameter"></a>Mais informações sobre o parâmetro de instalação ServiceLocation

Quando instala o cliente para utilizadores que têm o Office 2010 e não têm permissões administrativas locais, especifique o parâmetro ServiceLocation e o URL para o serviço Azure Rights Management. O parâmetro e o valor criam e definem as seguintes chaves de registo:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

Utilize o seguinte procedimento para identificar o valor a especificar para o parâmetro ServiceLocation. 

##### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>Para identificar o valor a especificar para o parâmetro ServiceLocation

1. A partir de uma sessão do PowerShell, primeiro execute [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice) e especifique as suas credenciais de administrador para ligar ao serviço Azure Rights Management. Em seguida, execute [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration). 
 
    Se ainda não instalou o módulo do PowerShell para o serviço Azure Rights Management, veja [instalar o módulo do PowerShell do AADRM](../install-powershell.md).

2. A partir da saída, identifique o valor **LicensingIntranetDistributionPointUrl**.

    Por exemplo: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. No valor, remova **/_wmcs/licensing** desta cadeia. Por exemplo: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    A cadeia restante é o valor a especificar para o parâmetro ServiceLocation.

Exemplo de como instalar automaticamente o cliente para o Office 2010 e para o Azure RMS: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


#### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>Mais informações sobre o parâmetro de instalação DowngradeDotNetRequirement

Para suportar as atualizações automáticas através do Windows Update e para integração fiável com aplicações do Office, o cliente do Azure Information Protection utiliza o Microsoft .NET Framework versão 4.6.2. Por predefinição, uma instalação interativa usando o executável procura esta versão e tenta instalá-la se ela está em falta. A instalação depois exige que o computador seja reiniciado.

Se a instalação desta versão posterior do Microsoft .NET Framework não for conveniente, poderá instalar o cliente com o parâmetro e valor **DowngradeDotNetRequirement=True**, que ignorará este requisito se o Microsoft .NET Framework 4.5.1 estiver instalado.

Por exemplo: `AzInfoProtection.exe DowngradeDotNetRequirement=True`

Recomendamos que utilize este parâmetro com cuidado e com o conhecimento de que existem problemas comunicados com aplicações do Office pendentes quando o cliente do Azure Information Protection é utilizado com esta versão mais antiga do Microsoft .NET Framework. Se surgirem problemas de aplicações pendentes, atualize para a versão recomendada antes de experimentar outras soluções para resolução de problemas. 

Lembre-se também de que, se utilizar o Windows Update para manter atualizado o cliente do Azure Information Protection, tem de ter de outro mecanismo de implementação de software para atualizar o cliente para versões posteriores.

### <a name="to-install-the-azure-information-protection-client-by-using-the-msi-installer"></a>Instalar o cliente do Azure Information Protection através do instalador .msi

Para implementação central, utilize as seguintes informações específicas da versão de instalação .msi do cliente do Azure Information Protection. 

Se utilizar o Intune enquanto método de implementação de software, utilize estas instruções em conjunto com [Adicionar aplicações com o Microsoft Intune](/intune/deploy-use/add-apps).

1. Transfira a versão .msi do cliente do Azure Information Protection a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 
    
    Se existir uma versão de pré-visualização disponível, mantenha esta versão apenas para teste. Não se destina a utilizadores finais num ambiente de produção. 

2. Para cada computador que executar o ficheiro .msi, deve garantir que as seguintes dependências de software estão em vigor. Por exemplo, envie estes com a versão .msi do cliente ou implemente apenas em computadores que cumprem estas dependências:
    
    |Versão do Office|Sistema operativo|Software|Ação|
    |--------------------|--------------|----------------|---------------------|
    |Office 2016|Todas as versões suportadas|64 bits: [KB3178666](https://www.microsoft.com/en-us/download/details.aspx?id=55007)<br /><br />32 bits: [KB3178666](https://www.microsoft.com/en-us/download/details.aspx?id=54999)<br /><br /> Versão: 1.0|Instalar|
    |Office 2013|Todas as versões suportadas|64 bits: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54992)<br /><br /> 32 bits: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54979) <br /><br />Versão: 1.0|Instalar|
    |Office 2010|Todas as versões suportadas|[Assistente de Início de Sessão do Microsoft Online Services](https://www.microsoft.com/en-us/download/details.aspx?id=28177)<br /><br /> Versão: 2.1|Instalar|
    |Office 2010|Windows 8.1 e Windows Server 2012 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instale se KB2843630 ou KB2919355 não está instalado|
    |Office 2010|Windows 8 e Windows Server 2012|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instalar|
    |Office 2010|O Windows 7 e Windows Server 2008 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41709)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instale se KB3125574 não está instalado|
    |Não aplicável|Windows 7|[vc_redist.x86.exe](https://www.microsoft.com/en-us/download/details.aspx?id=48145)|Instalar|
    |Não aplicável|Windows 7|KB2627273 <br /><br /> Número da versão incluído no nome de ficheiro: v4|Desinstalar|

3. Para uma instalação predefinida, execute o .msi com **/quiet**, por exemplo, `AzInfoProtection.msi /quiet`. No entanto, irá precisar de especificar parâmetros adicionais de instalação que estão documentados nas [instruções de instalação executáveis](#to-install-the-azure-information-protection-client-by-using-the-executable-installer).  


## <a name="how-to-install-the-azure-information-protection-scanner"></a>Como instalar o scanner do Azure Information Protection

O módulo do PowerShell que está incluído com o cliente do Azure Information Protection tem de cmdlets para instalar e configurar a deteção de impressão. No entanto, para utilizar o scanner, que tem de instalar a versão completa do cliente e não é possível instalar apenas o módulo do PowerShell.

Para instalar o cliente para a deteção de impressão, siga as mesmas instruções nas secções anteriores. Em seguida, está pronto para instalar o scanner. Para obter instruções, consulte [Implantando o scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](../deploy-aip-scanner.md).

## <a name="next-steps"></a>Passos Seguintes
Agora que instalou o cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


