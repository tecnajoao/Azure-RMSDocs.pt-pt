---
title: Implementar o conector Rights Management – AIP
description: Instruções para implementar o conector do RMS, que fornece o serviço de proteção de dados para as implementações no local existentes que utilizam o Exchange Server, o SharePoint Server ou o Windows Server e a Infraestrutura de Classificação de Ficheiros (FCI).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90e7e33f-9ecc-497b-89c5-09205ffc5066
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 664ff595a5bfd5f4695f9c3cad06fc1fb454839c
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491362"
---
# <a name="deploying-the-azure-rights-management-connector"></a>Implementar o conetor Azure Rights Management

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilize estas informações para saber mais sobre o conector Azure Rights Management e, em seguida, saiba como implementá-lo com êxito na sua organização. Este conector proporciona proteção de dados para as implementações no local existentes que utilizam o **Microsoft Exchange Server**, o **SharePoint Server** ou servidores de ficheiros que executam o Windows Server e a **Infraestrutura de Classificação de Ficheiros** (FCI).


## <a name="overview-of-the-microsoft-rights-management-connector"></a>Descrição geral do conector Microsoft Rights Management
O conector Microsoft Rights Management (RMS) permite-lhe ativar rapidamente servidores no local existentes para utilizar a respetiva funcionalidade de Gestão de Direitos de Informação (IRM) com o serviço Microsoft Rights Management (Azure RMS) baseado na cloud. Com esta funcionalidade, o departamento de TI e os utilizadores podem proteger facilmente documentos e imagens dentro e fora da organização, sem terem de instalar outras infraestruturas ou estabelecer relações de fidedignidade com outras organizações. 

O conector RMS é um serviço que consome poucos recursos e que se instala no local, em servidores que executem o Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2. Além de executar o conector em computadores físicos, também pode executá-lo em máquinas virtuais, incluindo VMs IaaS do Azure. Após implementar o conector, este funciona como uma interface comunicações (um reencaminhamento) entre os servidores no local e o serviço na cloud, conforme apresentado na imagem seguinte. As setas indicam a direção em que são iniciadas as ligações de rede.

![Descrição geral da arquitetura do conector RMS](./media/RMS_connector.png)


### <a name="on-premises-servers-supported"></a>Servidores no local suportados

O conector RMS suporta os seguintes servidores no local: Exchange Server, SharePoint Server e servidores de ficheiros que executam o Windows Server e utilizam a Infraestrutura de Classificação de Ficheiros para classificar e aplicar políticas a documentos do Office numa pasta. 

> [!NOTE]
> Se quiser proteger vários tipos de ficheiro (e não apenas os documentos do Office) ao utilizar a Infraestrutura de Classificação de Ficheiros, não utilize o conector RMS, mas sim os [cmdlets AzureInformationProtection](/powershell/azureinformationprotection/vlatest/aip).

Para as versões destes servidores no local que são suportadas pelo conector RMS, consulte [Servidores no local que suportam o Azure RMS](requirements-servers.md).


### <a name="support-for-hybrid-scenarios"></a>Suporte para cenários híbridos

Pode utilizar o conector RMS num cenário híbrido, mesmo que alguns dos seus utilizadores estabeleçam ligação a serviços online. Por exemplo, as caixas de correio de alguns utilizadores utilizam o Exchange Online e as caixas de correio de alguns utilizadores utilizam o Exchange Server. Depois de instalar o conector RMS, todos os utilizadores podem proteger e consumir mensagens de e-mail e anexos ao utilizar o Azure RMS, sendo que a proteção de informações funciona na perfeição entre as duas configurações de implementação.

### <a name="support-for-customer-managed-keys-byok"></a>Suporte para chaves geridas pelo cliente (BYOK)

Se gerir a sua própria chave de inquilino do Azure RMS (o cenário traga a sua própria chave ou BYOK), o conector RMS e os servidores no local que a utilizam não acedem ao módulo de hardware de segurança (HSM) que contém a chave de inquilino. Isto acontece porque todas as operações de criptografia que utilizam a chave de inquilino são executadas no Azure RMS e não no local.

Se quiser saber mais sobre este cenário onde gere a sua chave, consulte de inquilino [planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

## <a name="prerequisites-for-the-rms-connector"></a>Pré-requisitos do conector RMS
Antes de instalar o conector RMS, certifique-se de que os seguintes requisitos são cumpridos.

|Requisito|Mais informações|
|---------------|--------------------|
|O serviço Rights Management (RMS) está ativado|[Ativar o Azure Rights Management](activate-service.md)|
|Sincronização de diretórios entre as suas florestas do Active Directory no local e o Azure Active Directory|Depois de o RMS estar ativado, tem de configurar o Azure Active Directory para funcionar com os utilizadores e os grupos na sua base de dados do Active Directory.<br /><br />**Importante**: é necessário efetuar este passo de sincronização de diretórios para que o conector RMS funcione, inclusivamente para uma rede de teste. Apesar de poder utilizar o Office 365 e o Azure Active Directory através de contas que cria manualmente no Azure Active Directory, este conector requer que as contas no Azure Active Directory estejam sincronizadas com os Serviços de Domínio do Active Directory. A sincronização manual de palavra-passe não é suficiente.<br /><br />Para mais informações, consulte os seguintes recursos:<br /><br />[Integrar as suas identidades no local com o Azure Active Directory](/active-directory/active-directory-aadconnect)<br /><br />[Comparação de ferramentas de integração de diretórios de Identidade Híbrida](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison)|
|Um mínimo de dois computadores membros em que pretende instalar o conector RMS:<br /><br />– Um computador físico ou virtual de 64 bits com um dos seguintes sistemas operativos: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2.<br /><br />– Um mínimo de 1 GB de RAM.<br /><br />– Um mínimo de 64 GB de espaço em disco.<br /><br />– Pelo menos uma interface de rede.<br /><br />– Acesso à Internet através de uma firewall (ou proxy Web) que não exija autenticação.<br /><br />– Tem de estar numa floresta ou domínio que confie noutras florestas na organização que contêm instalações de servidores do Exchange ou do SharePoint que pretenda utilizar com o conector RMS.|Para conseguir tolerância a falhas e elevada disponibilidade, tem de instalar o conector RMS, no mínimo, em dois computadores.<br /><br />**Sugestão**: se estiver a utilizar o Outlook Web Access ou dispositivos móveis que utilizem o Exchange ActiveSync IRM e se for fundamental manter o acesso a e-mails e anexos que estão protegidos pelo Azure RMS, recomendamos que implemente um grupo com balanceamento de carga de servidores de conector para assegurar a elevada disponibilidade.<br /><br />Não necessita de servidores dedicados para executar o conector, mas tem de instalá-lo num computador separado dos servidores que irão utilizar o conector.<br /><br />**Importante**: não instale o conector num computador que executa o Exchange Server, o SharePoint Server ou um servidor de ficheiros que esteja configurado para a infraestrutura de classificação de ficheiros se pretender utilizar a funcionalidade a partir destes serviços com o Azure RMS. Além disso, não instale este conector num controlador de domínio.<br /><br />Se tiver cargas de trabalho do servidor que pretende utilizar com o conector RMS, mas os servidores estiverem em domínios que não são considerado fidedigno pelo domínio do qual pretende executar o conector, pode instalar servidores adicionais do conector de RMS nestes domínios não fidedignos ou outro domínios na sua floresta. <br /><br />Não há limite para o número de servidores do conector que pode executar para a sua organização e todos os servidores do conector instalado numa partilha de organização, a mesma configuração. No entanto, para configurar o conector para autorizar servidores, tem de ser capaz de navegar para as contas de servidor ou serviço que pretende autorizar, que significa que tem de executar a ferramenta de administração do RMS numa floresta do qual pode procurar essas contas.|


## <a name="steps-to-deploy-the-rms-connector"></a>Passos para implementar o conector RMS

O conector não verifica automaticamente todos os [pré-requisitos](deploy-rms-connector.md#prerequisites-for-the-rms-connector) que necessita para uma implementação bem-sucedida, por isso, certifique-se de que estes foram cumpridos antes de começar. A implementação necessita que instale o conector, configure o conector e, em seguida, configure os servidores que quer que utilizem o conector. 

-   **Passo 1:**  [instalar o conector RMS](install-configure-rms-connector.md#installing-the-rms-connector)

-   **Passo 2:**  [introduzir credenciais](install-configure-rms-connector.md#entering-credentials)

-   **Passo 3:**  [autorizar os servidores a utilizar o conector RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector)

-   **Passo 4:**  [configurar o balanceamento de carga e a elevada disponibilidade](install-configure-rms-connector.md#configuring-load-balancing-and-high-availability)

-   Opcional: [configurar o conector RMS para utilizar HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https)

-   Opcional: [configurar o conector RMS para um servidor proxy Web](install-configure-rms-connector.md#configuring-the-rms-connector-for-a-web-proxy-server)

-   Opcional: [instalar a ferramenta de administração do conector RMS em computadores administrativos](install-configure-rms-connector.md#installing-the-rms-connector-administration-tool-on-administrative-computers)

-   **Passo 5:**  [configurar servidores para utilizar o conector RMS](configure-servers-rms-connector.md)

    -   [Configurar um servidor Exchange para utilizar o conector](configure-servers-rms-connector.md#configuring-an-exchange-server-to-use-the-connector)

    -   [Configurar um servidor SharePoint para utilizar o conector](configure-servers-rms-connector.md#configuring-a-sharepoint-server-to-use-the-connector)

    -   [Configurar um servidor de ficheiros para a Infraestrutura de Classificação de Ficheiros para utilizar o conector](configure-servers-rms-connector.md#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)


## <a name="next-steps"></a>Passos Seguintes

Aceda ao Passo 1: [instalar e configurar o conector Azure Rights Management](install-configure-rms-connector.md).