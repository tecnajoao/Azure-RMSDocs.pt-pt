---
title: Guia do administrador do cliente do Azure Information Protection
description: "Instruções e informações para administradores numa rede empresarial responsáveis por implementar o cliente do Azure Information Protection para o Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 33a5982f-7125-4031-92c2-05daf760ced1
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 9359d83ec2ee85edeef6a3d2680f95633d22546e
ms.sourcegitcommit: 7bec3dfe3ce61793a33d53691046c5b2bdba3fb9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
---
# <a name="azure-information-protection-client-administrator-guide"></a>Guia do administrador do cliente do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilize as informações deste guia se for responsável pelo cliente do Azure Information Protection numa rede empresarial ou se pretender mais informações técnicas além das que estão no [Guia do utilizador do cliente do Azure Information Protection](client-user-guide.md). 

Por exemplo:

- Entender os diferentes componentes do cliente e se o deve instalar

- Como instalar o cliente para utilizadores, com informações sobre pré-requisitos, opções de instalação e parâmetros e verificações

- Como inserir configurações personalizadas que muitas vezes exigem a edição do registo

- Encontre os ficheiros de cliente e registos de utilização

- Identifique os tipos de ficheiro suportados pelo cliente

- Configure e utilize o site de controlo de documentos para os utilizadores

- Utilize o cliente com o PowerShell para controlo de linha de comandos

**Tem uma pergunta que não foi respondida nesta documentação?** Visite o nosso [site Yammer do Azure Information Protection](https://www.yammer.com/AskIPTeam). 

## <a name="technical-overview-of-the-azure-information-protection-client"></a>Descrição geral técnica sobre o cliente do Azure Information Protection

O cliente do Azure Information Protection inclui o seguinte:

- Um suplemento do Office, que instala a barra do Azure Information Protection para os utilizadores selecionarem etiquetas de classificação e um botão **Proteger** no friso para opções adicionais.

- Opções de clique com o botão direito do rato do Explorador de Ficheiros do Windows para os utilizadores aplicarem etiquetas de classificação e proteção a ficheiros.

- Um visualizador para apresentar ficheiros protegidos quando uma aplicação nativa não consegue abri-los.

- Um módulo do PowerShell para aplicar e remover etiquetas de classificação e proteção de ficheiros.

- O cliente do Rights Management que comunica com o Azure Rights Management (Azure RMS) ou os Serviços de Gestão de Direitos do Active Directory (AD RMS).

O cliente do Azure Information Protection é mais adequado para funcionar com os respetivos serviços do Azure; o Azure Information Protection e o respetivo serviço de proteção de dados, o Azure Rights Management. No entanto, com algumas limitações, o cliente do Azure Information Protection também funciona com a versão no local do Rights Management, o AD RMS. Para ver uma comparação detalhada das funcionalidades suportadas pelo Azure Information Protection e pelo AD RMS, veja [Comparar o Azure Information Protection e o AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). 

Se tiver o AD RMS e quiser migrar para o Azure Information Protection, veja [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Deve implementar o cliente do Azure Information Protection?

Implemente o cliente do Azure Information Protection no caso de se aplicar alguma das seguintes condições:

- Quer classificar (e, opcionalmente, proteger) documentos e e-mails ao selecionar etiquetas a partir das suas aplicações do Office (Word, Excel, PowerPoint, Outlook).

- Quer classificar (e, opcionalmente, proteger) documentos e e-mails através do Explorador de Ficheiros, que suporta outros tipos de ficheiro, a seleção múltipla e as pastas.

- Quer executar scripts que classificam (e, opcionalmente, protegem) documentos ao utilizar comandos do PowerShell.

- Quer ver documentos protegidos quando uma aplicação nativa para apresentar o ficheiro não está instalada ou não consegue abrir estes documentos.

- Quer apenas proteger os ficheiros através do Explorador de Ficheiros ou através de comandos do PowerShell.

- Quer que os utilizadores e os administradores possam monitorizar e revogar documentos protegidos.

- Quer remover a encriptação dos ficheiros e contentores (desproteger) em massa para fins de recuperação de dados.

- Utiliza o Office 2010 e quer proteger documentos e e-mails através do serviço Azure Rights Management.

Exemplo que mostra o suplemento do cliente do Azure Information Protection numa aplicação do Office a apresentar as etiquetas de classificação da sua organização e o novo botão **Proteger** no friso:

![Barra do Azure Information Protection com a política predefinida](../media/word2016-calloutsv2.png)

## <a name="how-to-install-the-azure-information-protection-client-for-users"></a>Como instalar o cliente do Azure Information Protection para os utilizadores

Antes de instalar o cliente, verifique se os computadores têm as versões de sistema operativo e as aplicações necessárias para o Azure Information Protection: [Requisitos do Azure Information Protection](../get-started/requirements-azure-rms.md). 

Em seguida, verifique os pré-requisitos adicionais que o cliente do Azure Information Protection possa precisar.

### <a name="additional-prerequisites-for-the-azure-information-protection-client"></a>Pré-requisitos adicionais para o cliente do Azure Information Protection

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

- Não desative o suplemento **Microsoft Azure Information Protection** para as aplicações do Office
    
    Se configurou a definição de política de grupo **Lista de suplementos geridos**, adicione o suplemento Microsoft Azure Information Protection às aplicações do Office ao especificar os seguintes identificadores programáticos (ProgID) para o Azure Information Protection e definir a opção para **1: o suplemento está sempre ativado**.
    
    - Para o Outlook: `MSIP.OutlookAddin`
    
    - Para o Word: `MSIP.WordAddin`
    
    - Para o Excel: `MSIP.ExcelAddin`
    
    - Para o PowerPoint: `MSIP.PowerPointAddin`
    
    Mesmo que ainda não tenha configurado esta definição de política de grupo **Lista de suplementos geridos**, poderá ter de a configurar se receber relatórios a informar que o suplemento Microsoft Azure Information Protection será desativado. Quando este suplemento é desativado, os utilizadores não veem a barra Azure Information Protection na aplicação do Office.
    
    Para obter mais informações sobre esta definição de política de grupo, veja [No Add-ins loaded due to group policy settings for Office 2013 and Office 2016 programs](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off) (Os suplementos não são carregados devido às definições de política de grupo dos programas do Office 2013 e do Office 2016).

> [!IMPORTANT]
> A instalação do cliente do Azure Information Protection requer permissões administrativas locais.


### <a name="options-to-install-the-azure-information-protection-client-for-users"></a>Opções para instalar o cliente do Azure Information Protection para os utilizadores

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
 
    Se ainda não tiver instalado o módulo do PowerShell para o serviço Azure Rights Management, veja [Instalar o Windows PowerShell para o Azure Rights Management](../deploy-use/install-powershell.md).

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
    |Office 2013|Todas as versões suportadas|[KB 3054941](https://www.microsoft.com/en-us/download/details.aspx?id=49337)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instalar|
    |Office 2010|Todas as versões suportadas|[Assistente de Início de Sessão do Microsoft Online Services](https://www.microsoft.com/en-us/download/details.aspx?id=28177)<br /><br /> Versão: 2.1|Instalar|
    |Office 2010|Windows 8.1 e Windows Server 2012 R2|[KB 2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instale se KB 2843630 ou KB 2919355 não estiver instalado|
    |Office 2010|Windows 8 e Windows Server 2012|[KB 2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instalar|
    |Office 2010|Windows 7|[KB 2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41709)<br /><br /> Número da versão incluído no nome de ficheiro: v3|Instale se KB 3125574 não estiver instalado|
    |Não aplicável|Windows 7|KB 2627273 <br /><br /> Número da versão incluído no nome de ficheiro: v4|Desinstalar|

3. Para uma instalação predefinida, execute o .msi com **/quiet**, por exemplo, `AzInfoProtection.msi /quiet`. No entanto, irá precisar de especificar parâmetros adicionais de instalação que estão documentados nas [instruções de instalação executáveis](#to-install-the-azure-information-protection-client-by-using-the-executable-installer).  

## <a name="additional-checks-and-troubleshooting"></a>Verificações adicionais e resolução de problemas

Utilize a opção **Ajuda e Feedback** para abrir a caixa de diálogo **Microsoft Azure Information Protection**:

- A partir de uma aplicação do Office: no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, selecione **Ajuda e Feedback**.

- No Explorador de Ficheiros: selecione com o botão direito do rato um ficheiro, ficheiros ou pasta, selecione **Classificar e proteger** e, em seguida, selecione **Ajuda e Feedback**. 

### <a name="help-and-feedback-section"></a>Secção **Ajuda e Feedback**

A **ligação Mais informações** direciona-o, por predefinição, para o site do [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection), mas pode configurá-la para um URL personalizado, de acordo com uma das [definições da política](../deploy-use/configure-policy-settings.md) da política do Azure Information Protection.

Utilize a ligação **Enviar Comentários** para enviar pedidos ou sugestões para a equipa do Information Protection. Não utilize esta opção para o suporte técnico e, em vez disso, veja [Opções de suporte e recursos da comunidade](../get-started/information-support.md#support-options-and-community-resources). 

**Exportar Registos** recolhe e anexa automaticamente ficheiros de registo para o cliente de Azure Information Protection se lhe tiver sido pedido para os enviar ao Suporte da Microsoft. Esta opção também serve para os utilizadores finais enviarem estes ficheiros de registo ao suporte técnico.

Para ver as informações de diagnóstico e para repor o cliente, selecione **Executar diagnósticos**. Quando os testes de diagnóstico forem concluídos, clique em **Copiar Resultados** para colar as informações num e-mail que pode enviar ao Suporte da Microsoft ou os utilizadores podem enviar ao seu suporte técnico. Quando os testes forem concluídos, também pode repor o cliente.

> [!NOTE]
> Na versão de pré-visualização do cliente, a função **Executar diagnósticos** foi removida e substituída por **Repor Definições**. Além disso, o comportamento desta opção foi [alterado](#more-information-about-the-reset-option-for-the-current-preview-version-of-the-azure-information-protection-client).

#### <a name="more-information-about-the-reset-option-for-the-general-availability-ga-version-of-the-azure-information-protection-client"></a>Obter mais informações sobre a opção de reposição da versão de disponibilidade geral (DG) do cliente do Azure Information Protection

- Não precisa de ser um administrador local para utilizar esta opção e esta ação não é registada no Visualizador de Eventos. 

- A menos que os ficheiros estejam bloqueados, esta ação elimina todos os ficheiros existentes em **%LocalAppData%\Microsoft\MSIPC**, que é o local onde os certificados de cliente e os modelos do Rights Management estão armazenados. Não elimina a política do Azure Information Protection ou os ficheiros de registo de clientes nem termina a sessão do utilizador.

- A chave de registo e definições seguintes são eliminadas: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Se tiver configurado as definições para esta chave do registo, terá de reconfigurar as definições do registo após repor o cliente. Por exemplo, configurou as definições de forma a redirecionar para o seu inquilino do Azure Information Protection porque está a migrar a partir do AD RMS e ainda tem um Ponto de Ligação de Serviço na sua rede.

- Depois da reposição do cliente, tem de reinicializar o ambiente do utilizador, o que irá transferir para o cliente certificados e os modelos mais recentes. Para o fazer, feche todas as instâncias do Office e, em seguida, reinicie uma aplicação do Office. Esta ação também verifica se transferiu a política do Azure Information Protection mais recente. Não execute novamente os testes de diagnóstico até ter efetuado esta ação.

#### <a name="more-information-about-the-reset-option-for-the-current-preview-version-of-the-azure-information-protection-client"></a>Obter mais informações sobre a opção de reposição da versão de pré-visualização atual do cliente do Azure Information Protection

- Não precisa de ser um administrador local para utilizar esta opção e esta ação não é registada no Visualizador de Eventos. 

- A menos que os ficheiros estejam bloqueados, esta ação elimina todos os ficheiros nas seguintes localizações. Estes ficheiros incluem certificados de cliente, modelos do Rights Management, a política do Azure Information Protection e as credenciais de utilizador em cache. Não são eliminados os ficheiros de registo de cliente.
    
    - %LocalAppData%\Microsoft\DRM
    
    - %LocalAppData%\Microsoft\MSIPC
    
    - %LocalAppData%\Microsoft\MSIP\Policy.msip
    
    - %LocalAppData%\Microsoft\MSIP\TokenCache

- As seguintes chaves do registo e definições são eliminadas. Se tiver configurado definições para alguma destas chaves do registo, terá de as reconfigurar após efetuar a reposição do cliente. Por exemplo, configurou as definições de forma a redirecionar para o seu inquilino do Azure Information Protection porque está a migrar a partir do AD RMS e ainda tem um Ponto de Ligação de Serviço na sua rede:
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\16.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Classes\Local Settings\Software\Microsoft\MSIPC    

- É terminada a sessão do utilizador com sessão iniciada atualmente.

### <a name="client-status-section"></a>Secção **Estado de cliente**

Utilize o valor **Ligado como** para confirmar que o nome de utilizador apresentado identifica a conta a ser utilizada para autenticação do Azure Information Protection. Este nome de utilizador tem de corresponder a uma conta utilizada no Office 365 ou no Azure Active Directory. A conta também tem de pertencer a um inquilino configurado para o Azure Information Protection.

Se precisar de iniciar sessão como um utilizador diferente do apresentado, veja a personalização [Iniciar sessão como um utilizador diferente](client-admin-guide-customizations.md#sign-in-as-a-different-user).

A **Última ligação** mostra quando o cliente esteve ligado pela última vez ao serviço Azure Information Protection da organização. Pode utilizar esta informação com a data e hora apresentada em **A política do Information Protection foi instalada a** para confirmar quando foi a última vez em que a política do Azure Information Protection foi instalada ou atualizada. Quando o cliente se liga ao serviço, será transferida automaticamente a política mais recente se forem detetadas alterações em relação à política atual e, também, a cada 24 horas. Se tiver efetuado alterações de política após a hora apresentada, feche e reabra a aplicação do Office.

Se vir **O cliente não está licenciado para o Office Professional Plus**: significa que o cliente do Azure Information Protection detetou que a edição instalada do Office não suporta a aplicação da proteção Rights Management. Quando esta deteção é feita, as etiquetas que aplicam a proteção não são apresentadas na barra do Azure Information Protection.

Utilize as informações da **Versão** para confirmar que versão do cliente está instalada. Pode verificar se esta é a versão mais recente, bem como as correções correspondentes e as novas funcionalidades, ao clicar na ligação **Novidades**, para ler o [Histórico do Lançamento de Versões](client-version-release-history.md) do cliente.

## <a name="support-for-multiple-languages"></a>Suporte para múltiplos idiomas

O cliente do Azure Information Protection suporta todos os idiomas de cliente suportados pelo Office. Por exemplo, as opções de menu, caixas de diálogo e mensagens são apresentadas no idioma do utilizador. Existe um único instalador para detetar o idioma, pelo que não é necessária qualquer configuração adicional para instalar o cliente de idiomas diferentes. 

No entanto, os nomes de etiquetas que os utilizadores veem não são traduzidos automaticamente para a [política predefinida](../deploy-use/configure-policy-default.md) ou para os nomes de etiquetas que especificar. Para os utilizadores verem as etiquetas em idiomas diferentes, tem de fornecer as suas próprias traduções e configurar a política do Azure Information Protection para as utilizar. Para obter mais informações, veja [Como configurar etiquetas para diferentes idiomas no Azure Information Protection](../deploy-use/configure-policy-languages.md).

## <a name="to-uninstall-the-azure-information-protection-client"></a>Para instalar o cliente do Azure Information Protection

Pode utilizar uma das seguintes opções:

- Utilize o Painel de Controlo para desinstalar um programa: clique em **Microsoft Azure Information Protection** > **Desinstalar**

- Volte a executar o ficheiro executável (por exemplo, **AzInfoProtection.exe**) e, na página **Modificar Configuração**, clique em **Desinstalar**. 

- Execute o ficheiro executável com **/uninstall**. Por exemplo: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Próximos passos
Agora que instalou o cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
