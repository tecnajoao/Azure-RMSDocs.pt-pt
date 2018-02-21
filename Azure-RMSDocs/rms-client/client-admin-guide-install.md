---
title: Instalar o cliente Azure Information Protection para os utilizadores
description: "As instruções e informações para os administradores implementar o cliente Azure Information Protection para o Windows em redes de empresa."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ea3ec965-3720-4614-8564-3ecfe60bc175
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: a62c8c1c27855b25e5de69bd162d524bf1851890
ms.sourcegitcommit: 31c79d948ec3089a4dc65639f1842c07c7aecba6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2018
---
# <a name="admin-guide-install-the-azure-information-protection-client-for-users"></a>Guia do administrador: Instalar o cliente Azure Information Protection para os utilizadores

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Antes de instalar o cliente Azure Information Protection na sua rede empresarial, verifique se os computadores têm as aplicações do Azure Information Protection e as versões do sistema operativo necessário: [requisitos para obter informações do Azure Proteção](../get-started/requirements-azure-rms.md). 

Em seguida, verifique os pré-requisitos adicionais que podem ser necessários para o cliente Azure Information Protection, conforme documentado na secção seguinte. Nem todos os pré-requisitos são verificados pelo programa de instalação.

## <a name="additional-prerequisites-for-the-azure-information-protection-client"></a>Pré-requisitos adicionais para o cliente do Azure Information Protection

- Microsoft .NET Framework 4.6.2
    
    A instalação completa do cliente do Azure Information Protection requer, por predefinição, a versão mínima do Microsoft .NET Framework 4.6.2 e, se estiver em falta, o instalador tentará transferir e instalar este pré-requisito. Quando este pré-requisito é instalado como parte da instalação do cliente, o computador tem de ser reiniciado. Embora não seja recomendado, pode ignorar este pré-requisito com um [parâmetro de instalação personalizada](#more-information-about-the-downgradedotnetrequirement-installation-parameter).

- Microsoft .NET Framework 4.5.2
    
    Se o Visualizador do Azure Information Protection for instalado à parte, precisará da versão mínima do Microsoft .NET Framework 4.5.2 e, se esta estiver em falta, o instalador não a transfere nem a instala.

- Versão do Windows PowerShell 4.0
    
    O módulo do PowerShell para o cliente requer o Windows PowerShell versão 4.0, que poderá ter de ser instalado em sistemas operativos mais antigos. Para obter mais informações, veja [Como Instalar o Windows PowerShell 4.0](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx). O instalador não verifica nem instala este pré-requisito automaticamente. Para verificar que versão do Windows PowerShell está a executar, escreva `$PSVersionTable` numa sessão do PowerShell.

- Assistente de Início de Sessão do Microsoft Online Services 7.250.4303.0
    
    Os computadores com o Office 2010 necessitam do Assistente de Início de Sessão do Microsoft Online Services versão 7.250.4303.0. Esta versão está incluída na instalação do cliente. Se tiver uma versão posterior do Assistente de Início de Sessão, desinstale-a antes de instalar o cliente do Azure Information Protection. Por exemplo, verifique a versão e desinstale o Assistente de Início de Sessão através do **Painel de Controlo** > **Programa e Funcionalidades** > **Desinstalar ou alterar um programa**.

- KB 2533623
    
    Os computadores que executem o Windows 7 Service Pack 1 requerem a KB 2533623. Para obter mais informações sobre esta atualização, veja [Aviso de Segurança da Microsoft: o carregamento de bibliotecas não seguro pode permitir a execução remota de códigos](https://support.microsoft.com/en-us/kb/2533623). Poderá instalar diretamente esta atualização ou ser substituída por outra atualização que a instala por si.
    
    Se esta atualização for obrigatória e não estiver instalada, a instalação do cliente avisa-o de que tem de ser instalada. Esta atualização pode ser instalada após a instalação do cliente, mas algumas ações serão bloqueadas e a mensagem é apresentada novamente.  

- Visual C++ Redistributable for Visual Studio 2015 (versão de 32 bits)
    
    Em computadores com Windows 7 Service Pack 1, instalar **vc_redist.x86.exe** seguintes página de transferência: [Visual C++ Redistributable for Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145)
    
    A instalação do cliente não verifica este pré-requisito, mas é necessário para o cliente Azure Information Protection classificar e proteger os ficheiros PDF.

- Não desative o suplemento **Microsoft Azure Information Protection** para as aplicações do Office
    
    Se configurou a definição de política de grupo **Lista de suplementos geridos**, adicione o suplemento Microsoft Azure Information Protection às aplicações do Office ao especificar os seguintes identificadores programáticos (ProgID) para o Azure Information Protection e definir a opção para **1: o suplemento está sempre ativado**.
    
    - Para o Outlook: `MSIP.OutlookAddin`
    
    - Para o Word: `MSIP.WordAddin`
    
    - Para o Excel: `MSIP.ExcelAddin`
    
    - Para o PowerPoint: `MSIP.PowerPointAddin`
    
    Mesmo que ainda não tenha configurado esta definição de política de grupo **Lista de suplementos geridos**, poderá ter de a configurar se receber relatórios a informar que o suplemento Microsoft Azure Information Protection será desativado. Quando este suplemento é desativado, os utilizadores não veem a barra Azure Information Protection na aplicação do Office.
    
    Para obter mais informações sobre esta definição de política de grupo, veja [No Add-ins loaded due to group policy settings for Office 2013 and Office 2016 programs](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off) (Os suplementos não são carregados devido às definições de política de grupo dos programas do Office 2013 e do Office 2016).

- Para versões do Office 16.0.8628.2010 e posterior (clique para execução): Ativar o suporte legacy monitores
    
    Nota: Esta pré-requisito não é necessária para a versão de pré-visualização atual do cliente Azure Information Protection. 
    
    Para impedir a apresentação de barra de Azure Information Protection fora de aplicações do Office para estas versões do Office, poderá ter de ativar o suporte legacy para monitores. Quando a barra de não ser apresentados corretamente neste cenário, poderá ver que apresentado como **AdxTaskPane**. 
    
    Para configurar as aplicações do Office para este requisito: **ficheiro** > **opções** > **geral**  >   **As opções de Interface de utilizador**:
    
    - Se vir a opção **quando utilizar apresenta várias** está definido como **otimizar para melhor aspeto**, selecione **otimizar para compatibilidade (é necessário um reinício aplicação)** em vez disso. 
        
    - Se vir que a opção **utilizar das melhores definições para os meus apresentação** é selecionado, remover esta seleção.
    
    - Se vir nenhuma destas opções, é necessária nenhuma configuração adicional.

> [!IMPORTANT]
> A instalação do cliente do Azure Information Protection requer permissões administrativas locais.


## <a name="options-to-install-the-azure-information-protection-client-for-users"></a>Opções para instalar o cliente do Azure Information Protection para os utilizadores

Existem três opções para instalar o cliente para os utilizadores:

**Windows Update**: o cliente Azure Information Protection está incluído no catálogo Microsoft Update, pelo que pode instalar e atualizar este cliente através de qualquer serviço de atualização de software que utilize o catálogo.

**Execute a versão do executável (.exe) do cliente**: o método de instalação recomendado que pode executar interativamente ou silenciosamente. Este método tem mais flexibilidade e é recomendado porque o instalador verifica muitos dos pré-requisitos e pode instalar automaticamente pré-requisitos ausentes. [Instruções](#to-install-the-azure-information-protection-client-by-using-the-executable-installer)

**Implementar a versão do instalador do Windows (.msi) do cliente**: suportado apenas para instalações silenciosas que utilizam um mecanismo de implementação central, como uma política de grupo, o Configuration Manager e o Microsoft Intune. Este método é necessário para computadores com Windows 10 geridos pelo Intune e pela gestão de dispositivos móveis (MDM) porque para estes computadores, os ficheiros executáveis não têm suporte para instalação. No entanto, quando utilizar este método de instalação, deve verificar e instalar manualmente ou desinstalar o software dependente que o instalador do executável deve executar para cada computador. [Instruções](#to-install-the-azure-information-protection-client-by-using-the-msi-installer)

### <a name="to-install-the-azure-information-protection-client-by-using-the-executable-installer"></a>Instalar o cliente do Azure Information Protection através do instalador executável

Utilize as instruções a seguir para instalar o cliente quando não estiver a utilizar o catálogo do Microsoft Update ou implemente o .msi com um método de implementação central como o Intune.

1. Transfira a versão executável do cliente do Azure Information Protection a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 
    
    Se existir uma versão de pré-visualização disponível, mantenha esta versão apenas para teste. Não se destina a utilizadores finais num ambiente de produção. 

2. Para uma instalação predefinida, basta executar o ficheiro **AzInfoProtection.exe**, por exemplo. Porém, para ver as opções de instalação, execute primeiro o ficheiro com **/help**: `AzInfoProtection.exe /help`

    Exemplo de como instalar automaticamente o cliente: `AzInfoProtection.exe /quiet`
    
    Exemplo de como instalar automaticamente apenas os cmdlets do PowerShell: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
    
    Parâmetros adicionais que não estão listados no ecrã de ajuda:
    
    - **ServiceLocation**: utilize este parâmetro se estiver a instalar o cliente em computadores com o Office 2010 e se os utilizadores não forem administradores locais nos computadores deles ou se não quiser que lhes seja pedido. [Mais informações](#more-information-about-the-servicelocation-installation-parameter) 
    
    - **DowngradeDotNetRequirement**: utilize este parâmetro para ignorar o requisito para o Microsoft Framework .NET versão 4.6.2. [Mais informações](#more-information-about-the-downgradedotnetrequirement-installation-parameter)
    
    - **AllowTelemetry=0**: utilize este parâmetro para desativar a opção de instalação **Ajude a melhorar o Azure Information Protection ao enviar estatísticas de utilização para a Microsoft**. 
    
3. Se estiver a instalar interativamente, selecione a opção para instalar uma **política de demonstração** se não puder ligar-se ao Office 365 ou ao Azure Active Directory e quiser ver e experimentar o lado do cliente do Azure Information Protection com uma política local para efeitos de demonstração. Quando o cliente se liga a um serviço Azure Information Protection, esta política de demonstração é substituída pela política do Azure Information Protection da organização.
    
4. Para concluir a instalação: 

    - Se o computador estiver a executar o Office 2010, reinicie o computador. 
        
        Se o cliente não tiver sido instalado com o parâmetro ServiceLocation, quando abre uma das aplicações do Office que utilizam a barra do Azure Information Protection (por exemplo, o Word) pela primeira vez, terá de confirmar todos os pedidos para atualizar o registo para esta primeira utilização. A [deteção do serviço](../rms-client/client-deployment-notes.md#rms-service-discovery) é utilizada para preencher as chaves de registo. 
    
    - Para outras versões do Office, reinicie todas as aplicações do Office e todas as instâncias do Explorador de Ficheiros. 
        
5. Pode confirmar que a instalação foi concluída com êxito ao verificar o ficheiro de registo de instalação que, por predefinição, é criado na pasta %temp%. Pode alterar esta localização com o parâmetro de instalação **/log**. 
 
    Este ficheiro tem o seguinte formato de nomes: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`
    
    Por exemplo: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    Procure a seguinte cadeia neste ficheiro de registo: **Product: Microsoft Azure Information Protection -- Installation completed successfully.** Se a instalação falhou, este ficheiro de registo contém detalhes que o ajudam a identificar e resolver qualquer tipo de problemas.

#### <a name="more-information-about-the-servicelocation-installation-parameter"></a>Mais informações sobre o parâmetro de instalação ServiceLocation

Quando instala o cliente para utilizadores que têm o Office 2010 e não têm permissões administrativas locais, especifique o parâmetro ServiceLocation e o URL para o serviço Azure Rights Management. O parâmetro e o valor criam e definem as seguintes chaves de registo:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

Utilize o seguinte procedimento para identificar o valor a especificar para o parâmetro ServiceLocation. 

##### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>Para identificar o valor a especificar para o parâmetro ServiceLocation

1. A partir de uma sessão do PowerShell, primeiro execute [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice) e especifique as suas credenciais de administrador para ligar ao serviço Azure Rights Management. Em seguida, execute [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration). 
 
    Se ainda não instalou o módulo do PowerShell para o serviço Azure Rights Management, consulte [instalar o módulo do AADRM PowerShell](../deploy-use/install-powershell.md).

2. A partir da saída, identifique o valor **LicensingIntranetDistributionPointUrl**.

    Por exemplo: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. No valor, remova **/_wmcs/licensing** desta cadeia. Por exemplo: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    A cadeia restante é o valor a especificar para o parâmetro ServiceLocation.

Exemplo de como instalar automaticamente o cliente para o Office 2010 e para o Azure RMS: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


#### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>Mais informações sobre o parâmetro de instalação DowngradeDotNetRequirement

Para suportar as atualizações automáticas através do Windows Update e para integração fiável com aplicações do Office, o cliente do Azure Information Protection utiliza o Microsoft .NET Framework versão 4.6.2. Por predefinição, a instalação procura esta versão e tenta instalá-la se estiver em falta. A instalação depois exige que o computador seja reiniciado.

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
    |Office 2013|Todas as versões suportadas|64-bit: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54992)<br /><br /> 32-bit: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54979) <br /><br />Versão: 1.0|Instalar|
    |Office 2010|Todas as versões suportadas|[Assistente de Início de Sessão do Microsoft Online Services](https://www.microsoft.com/en-us/download/details.aspx?id=28177)<br /><br /> Versão: 2.1|Instalar|
    |Office 2010|Windows 8.1 e Windows Server 2012 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instalar se KB2843630 ou KB2919355 não está instalado|
    |Office 2010|Windows 8 e Windows Server 2012|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instalar|
    |Office 2010|Windows 7 e Windows Server 2008 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41709)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instalar se KB3125574 não está instalado|
    |Não aplicável|Windows 7|[vc_redist.x86.exe](https://www.microsoft.com/en-us/download/details.aspx?id=48145)|Instalar|
    |Não aplicável|Windows 7|KB2627273 <br /><br /> Número da versão incluído no nome de ficheiro: v4|Desinstalar|

3. Para uma instalação predefinida, execute o .msi com **/quiet**, por exemplo, `AzInfoProtection.msi /quiet`. No entanto, irá precisar de especificar parâmetros adicionais de instalação que estão documentados nas [instruções de instalação executáveis](#to-install-the-azure-information-protection-client-by-using-the-executable-installer).  


## <a name="how-to-install-the-azure-information-protection-scanner"></a>Como instalar o scanner do Azure Information Protection

Atualmente, a versão de disponibilidade geral (DG) do scanner Azure Information Protection é uma transferência individual com o nome **AzInfoProtectionScanner.exe** no [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Em versões posteriores do scanner serão incluídas no cliente do Azure Information Protection.

A versão de pré-visualização atual do cliente Azure Information Protection também inclui o scanner do Azure Information Protection. 

O módulo do PowerShell incluído com o scanner e o cliente de pré-visualização tem de cmdlets para instalar e Configurar scanner.

Para instalar o cliente para scanner, siga as mesmas instruções nas secções anteriores. Tenha em atenção que, se não precisarem de todos os componentes do cliente, como o suplemento do Office e Visualizador, pode instalar apenas o módulo do PowerShell. Por exemplo, pode executar o executável com `PowerShellOnly=true /quiet`.

Depois de instalar o cliente, em seguida, está pronto para instalar scanner. Para obter instruções, consulte [implementar a análise do Azure Information Protection para classificar e proteger ficheiros automaticamente](../deploy-use/deploy-aip-scanner.md).


## <a name="next-steps"></a>Próximos passos
Agora que instalou o cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
