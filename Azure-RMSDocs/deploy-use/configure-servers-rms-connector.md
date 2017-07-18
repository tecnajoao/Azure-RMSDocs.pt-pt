---
title: "Configurar servidores para o conector Rights Management – AIP"
description: "Informações para o ajudar a configurar os servidores no local que irão utilizar o conector Azure Rights Management (RMS). Estes procedimentos inclui o passo 5 do artigo Implementar o conector Azure Rights Management."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75846ee1-2370-4360-81ad-e2b6afe3ebc9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 8837b6187aee8bc041df7185527470297e913f49
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="configuring-servers-for-the-azure-rights-management-connector"></a>Configurar servidores para o conector Azure Rights Management

>*Aplica-se a: Azure Information Protection, Windows Server 2012, Windows Server 2012 R2*


Utilize as seguintes informações para ajudar a configurar os servidores no local que irão utilizar o conector Azure Rights Management (RMS). Estes procedimentos inclui o passo 5 do artigo [Implementar o conector Azure Rights Management](deploy-rms-connector.md).

Antes de começar, certifique-se de que instalou e configurou o conetor RMS e de que verificou todos os [pré-requisitos](deploy-rms-connector.md#prerequisites-for-the-rms-connector) aplicáveis aos servidores que irão utilizar o conector.


## <a name="configuring-servers-to-use-the-rms-connector"></a>Configurar servidores para utilizar o conector RMS
Após instalar e configurar o conector RMS, estará pronto para configurar os servidores no local que irão ligar ao serviço Azure Rights Management e utilizar esta tecnologia de proteção através do conector. Isto implica configurar os seguintes servidores:

-   **Para o Exchange 2016 e Exchange 2013**: servidores de acesso de cliente e servidores de caixa de correio

-   **Para o Exchange 2010**: servidores de acesso de cliente e servidores de transporte de concentrador

-   **Para o SharePoint**: servidores Web front-end do SharePoint, incluindo os que alojam o servidor de Administração Central

-   **Para a Infraestrutura de Classificação de Ficheiros**: computadores com o Windows Server e com o Gestor de Recursos de Ficheiros instalado

Esta configuração requer definições de registo. Para tal, tem duas opções: automaticamente, com a ferramenta de configuração do servidor para o conector Microsoft RMS, ou manualmente, ao editar o registo.

---

**Automaticamente, com a ferramenta de configuração do servidor para o conector Microsoft RMS:**

- Vantagens:

    - Não envolve a edição direta do registo. É um processo automatizado, em que é utilizado um script.

    - Não é necessário executar um cmdlet do Windows PowerShell para obter o seu URL do Microsoft RMS.

    - Os pré-requisitos são verificados automaticamente (mas não são remediados de forma automática) se a executar localmente.

Desvantagens:

- Quando executar a ferramenta, tem de estabelecer uma ligação a um servidor que já tenha o conector RMS em execução.

---

**Manualmente, ao editar o registo:**

- Vantagens:

    - Não é necessária conectividade a um servidor que tenha o conector RMS em execução.

- Desvantagens:

    - Mais tarefas administrativas adicionais, que são propensas a erros.

    - Tem de obter o seu URL do Microsoft RMS, o que requer a execução de um comando do Windows PowerShell.

    - Tem de verificar sempre todos os pré-requisitos pessoalmente.


---

> [!IMPORTANT]
> Em ambos os casos, tem de instalar todos os pré-requisitos manualmente e configurar o Exchange, o SharePoint e a Infraestrutura de Classificação de Ficheiros para utilizarem o Rights Management.

Na maioria das organizações, a configuração automática com a ferramenta de configuração do servidor para o conector Microsoft RMS será a melhor opção, uma vez que oferece maior eficácia e fiabilidade do que a configuração manual.

Depois de fazer as alterações de configuração nestes servidores, terá de os reiniciar se executarem o Exchange ou o SharePoint e se tiverem sido configurados anteriormente para utilizarem o AD RMS. Não é necessário reiniciar estes servidores se estiver a configurá-los para o Rights Management pela primeira vez. Após fazer estas alterações de configuração, tem sempre de reiniciar o servidor de ficheiros que está configurado para utilizar a Infraestrutura de Classificação de Ficheiros.

### <a name="how-to-use-the-server-configuration-tool-for-microsoft-rms-connector"></a>Como utilizar a ferramenta de configuração do servidor para o conector Microsoft RMS

1.  Se ainda não tiver transferido o script da ferramenta de configuração do servidor para o conector Microsoft RMS (GenConnectorConfig.ps1), transfira-o a partir do [ Centro de Transferências da Microsoft](http://go.microsoft.com/fwlink/?LinkId=314106).

2.  Guarde o ficheiro GenConnectorConfig.ps1 no computador onde irá executar a ferramenta. Se quiser executar a ferramenta localmente, este tem de ser o servidor que pretende configurar para comunicar com o conector RMS. Caso contrário, pode guardá-lo em qualquer computador.

3.  Decida como quer executar a ferramenta:

    -   **Localmente**: pode executar a ferramenta de forma interativa, a partir do servidor a configurar para comunicar com o conector RMS. Trata-se de uma opção útil para uma configuração pontual, tal como um ambiente de teste.

    -   **Implementação de software**: pode executar a ferramenta para produzir ficheiros de registo que, em seguida, irá implementar num ou mais servidores relevantes, através de uma aplicação de gestão de sistemas que suporte a implementação de software, tal como o System Center Configuration Manager.

    -   **Política de Grupo**: pode executar a ferramenta para produzir um script que irá fornecer a um administrador apto a criar objetos de Política de Grupo para os servidores a configurar. Este script cria um objeto de Política de Grupo para cada tipo de servidor a configurar, objeto este que o administrador poderá depois atribuir aos servidores relevantes.

    > [!NOTE]
    > Esta ferramenta configura os servidores que irão comunicar com o conector RMS e que estão listados no início desta secção. Não execute esta ferramenta nos servidores que executam o conector RMS.

4.  Inicie o Windows PowerShell com a opção **Executar como administrador** e utilize o comando Get-help para ler as instruções sobre como utilizar a ferramenta para o método de configuração qua escolheu:

    ```
    Get-help .\GenConnectorConfig.ps1 -detailed
    ```

Para executar o script, tem de introduzir o URL do conector RMS da sua organização. Introduza o prefixo do protocolo (HTTP:// ou HTTPS://) e o nome do conector que foram definidos no DNS para o endereço com balanceamento de carga do seu conector. Por exemplo, https://connector.contoso.com. Em seguida, a ferramenta utiliza esse URL para contactar os servidores que executam o conector RMS e obter outros parâmetros utilizados para criar as configurações necessárias.

> [!IMPORTANT]
> Quando executar esta ferramenta, certifique-se de que especifica o nome do conector RMS com balanceamento de carga para a sua organização e não o nome de um único servidor que executa o serviço do conector RMS.

Utilize as secções que se seguem para obter informações específicas para cada tipo de serviço:

-   [Configurar um servidor Exchange para utilizar o conector](#configuring-an-exchange-server-to-use-the-connector)

-   [Configurar um servidor SharePoint para utilizar o conector](#configuring-a-sharepoint-server-to-use-the-connector)

-   [Configurar um servidor de ficheiros para a Infraestrutura de Classificação de Ficheiros para utilizar o conector](#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)

> [!NOTE]
> É possível que, depois de estes servidores serem configurados para utilizarem o conector, as aplicações cliente instaladas localmente não funcionem com o RMS. Quando isto acontece, é porque as aplicações tentam utilizar o conector em vez de utilizarem o RMS diretamente, o que não é suportado.
>
> Além disso, se o Office 2010 estiver instalado localmente num servidor Exchange, as funcionalidades de IRM da aplicação cliente poderão funcionar a partir desse computador depois de o servidor ser configurado para utilizar o conector, mas isto não é suportado.
>
> Em ambos os cenários, tem de instalar as aplicações cliente em computadores separados que não estejam configurados para utilizar o conector. Desse modo, utilizarão o RMS diretamente, como é suposto.

## <a name="configuring-an-exchange-server-to-use-the-connector"></a>Configurar um servidor Exchange para utilizar o conector
As seguintes funções do Exchange comunicam com o conector RMS:

-   Para o Exchange 2016 e Exchange 2013: servidor de acesso de cliente e servidor de caixa de correio

-   Para o Exchange 2010: servidor de acesso de cliente e servidor de transporte de concentrador

Para utilizarem o conector RMS, estes servidores com o Exchange têm de ter uma das seguintes versões de software em execução:

-   Exchange Server 2016

-   Exchange Server 2013 com a Atualização Cumulativa 3 do Exchange 2013

-   Exchange Server 2010 com o Exchange 2010 Service Pack 3 Rollup Update 6

Nestes servidores, terá igualmente de ter a versão 1 do cliente RMS (também conhecido como MSDRM) que inclui suporte para o Modo Criptográfico 2 do RMS. Todos os sistemas operativos Windows incluem o cliente MSDRM, mas as versões anteriores do cliente não suportam o Modo Criptográfico 2. Se os seus servidores do Exchange estiverem a executar, pelo menos, o Windows Server 2012, não é necessária nenhuma ação adicional, porque o cliente RMS instalado nestes sistemas operativos suporta o Modo Criptográfico 2. 

Se os seus servidores do Exchange estiverem a executar uma versão anterior do sistema operativo, confirme que a versão instalada do cliente RMS suporta o Modo Criptográfico 2. Para tal, compare a versão do ficheiro instalado do Windows\System32\Msdrm.dll com os números de versão listados nos seguintes artigos da base de dados de conhecimento. Se o número da versão instalada corresponder ao número da versão listada ou for superior, não é necessária nenhuma ação adicional. Se o número da versão instalada for inferior, transfira e instale a correção a partir do artigo.

- Windows Server 2008: [https://support.microsoft.com/kb/2627272](https://support.microsoft.com/kb/2627272) 

- Windows Server 2008 R2: [https://support.microsoft.com/kb/2627273](https://support.microsoft.com/kb/2627273)

> [!IMPORTANT]
> Se estas versões ou versões posteriores do Exchange e do cliente MSDRM não estiverem instaladas, não conseguirá configurar o Exchange para utilizar o conector. Confirme que estas versões estão instaladas antes de continuar.

### <a name="to-configure-exchange-servers-to-use-the-connector"></a>Para configurar servidores Exchange para utilizarem o conector

1. Utilize a ferramenta de administração do conector RMS e as informações da secção [Autorizar os servidores a utilizar o conector RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) para se certificar de que os servidores Exchange estão autorizados a utilizar o conector RMS. Esta configuração é necessária para que o Exchange possa utilizar o conector RMS.

2.  Nas funções do servidor Exchange que comunicam com o conector RMS, efetue um dos seguintes procedimentos:

    -   Execute a ferramenta de configuração do servidor para o conector Microsoft RMS. Para mais informações, consulte [Como utilizar a ferramenta de configuração do servidor para o conector Microsoft RMS](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) neste artigo.

        Por exemplo, para executar a ferramenta localmente para configurar um servidor com o Exchange 2016 ou o Exchange 2013:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetExchange2013
        ```

    -   Faça edições de registo manuais com as informações disponíveis no artigo [Registry settings for the RMS connector (Definições de registo para o conector RMS – em inglês)](rms-connector-registry-settings.md) para adicionar as definições de registo manualmente nos servidores. 

3.  Ative a funcionalidade IRM no Exchange. Para mais informações, consulte o artigo [Information Rights Management Procedures (Procedimentos da Gestão de Direitos de Informação – em inglês)](https://technet.microsoft.com/library/dd351212%28v=exchg.150%29.aspx) na biblioteca do Exchange.

    > [!NOTE]
    > Por predefinição, depois de executar **Set-IRMConfiguration -InternalLicensingEnabled $true**, a IRM é ativada automaticamente para o Outlook Web App e para dispositivos móveis, para além de ativar a IRM para caixas de correio. No entanto, os administradores podem desativar a IRM em níveis diferentes, por exemplo, para um Servidor de Acesso de Cliente, para o diretório virtual do Outlook Web App ou a política de caixa de correio do Outlook Web App e para uma política de caixa de correio de dispositivos móveis. Se os utilizadores não conseguirem ver modelos do Azure RMS no Outlook Web App (depois de aguardarem um dia) ou nos dispositivos móveis, mas conseguirem vê-los no cliente do Outlook, verifique as definições relevantes para se certificar de que a IRM não está desativada. Para mais informações, consulte o artigo [Enable or Disable Information Rights Management on Client Access Servers (Ativar ou Desativar a Gestão de Direitos de Informação nos Servidores de Acesso de Cliente – em inglês)](https://technet.microsoft.com/library/dd876938(v=exchg.150).aspx) na documentação do Exchange. 


## <a name="configuring-a-sharepoint-server-to-use-the-connector"></a>Configurar um servidor SharePoint para utilizar o conector
As seguintes funções do SharePoint comunicam com o conector RMS:

-   Servidores Web front-end do SharePoint, incluindo os que alojam o servidor de Administração Central

Para utilizarem o conector RMS, estes servidores com o SharePoint têm de ter uma das seguintes versões de software em execução:

-   SharePoint Server 2016

-   SharePoint Server 2013

-   SharePoint Server 2010

Um servidor com o SharePoint 2016 ou SharePoint 2013 também tem de ter em execução uma versão do cliente MSIPC 2.1 que seja suportada com o conector RMS. Para se certificar de que tem uma versão suportada, transfira o cliente mais recente a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/download/details.aspx?id=38396).

> [!WARNING]
> Existem várias versões do cliente MSIPC 2.1, por isso certifique-se de que tem a versão 1.0.2004.0 ou posterior.
>
> Pode verificar a versão do cliente ao consultar o número de versão do ficheiro MSIPC.dll, que se encontra em **\Programas\Active Directory Rights Management Services Client 2.1**. A caixa de diálogo das propriedades mostra o número de versão do cliente MSIPC 2.1.

Os servidores com o SharePoint 2010 têm de ter instalada uma versão do cliente MSDRM que inclua suporte para o Modo Criptográfico 2 do RMS. A versão mínima suportada no Windows Server 2008 está incluída na correção que pode transferir a partir da página [RSA key length is increased to 2048 bits for AD RMS in Windows Server 2008 R2 and in Windows Server 2008 (O comprimento de chave RSA é aumentado para 2048 bits para o AD RMS no Windows Server 2008 R2 e no Windows Server 2008 – em inglês)](http://support.microsoft.com/kb/2627272) e a versão mínima do Windows Server 2008 R2 pode ser transferida a partir da página [RSA key length is increased to 2048 bits for AD RMS in Windows 7 or in Windows Server 2008 R2 (O comprimento de chave RSA é aumentado para 2048 bits para o AD RMS no Windows 7 ou no Windows Server 2008 R2 – em inglês)](http://support.microsoft.com/kb/2627273). O Windows Server 2012 e o Windows Server 2012 R2 suportam nativamente o Modo Criptográfico 2.

### <a name="to-configure-sharepoint-servers-to-use-the-connector"></a>Para configurar servidores SharePoint para utilizarem o conector

1. Utilize a ferramenta de administração do conector RMS e as informações da secção [Autorizar os servidores a utilizar o conector RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) para se certificar de que os servidores SharePoint estão autorizados a utilizar o conector RMS. Esta configuração é necessária para que o Exchange possa utilizar o conector RMS.

2.  Nos servidores SharePoint que comunicam com o conector RMS, efetue um dos seguintes procedimentos:

    -   Execute a ferramenta de configuração do servidor para o conector Microsoft RMS. Para mais informações, consulte [Como utilizar a ferramenta de configuração do servidor para o conector Microsoft RMS](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) neste artigo.

        Por exemplo, para executar a ferramenta localmente para configurar um servidor com o SharePoint 2016 ou o SharePoint 2013:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetSharePoint2013
        ```

    -   Se estiver a utilizar o SharePoint 2016 ou o SharePoint 2013, faça edições de registo manuais com as informações disponíveis no artigo [Definições de registo para o conector RMS](rms-connector-registry-settings.md) para adicionar as definições de registo manualmente nos servidores. 

3.  Ative a IRM no SharePoint. Para mais informações, consulte o artigo [Configure Information Rights Management (SharePoint Server 2010) (Configurar a Gestão de Direitos de Informação (SharePoint Server 2010) – em inglês)](https://technet.microsoft.com/library/hh545607%28v=office.14%29.aspx) na biblioteca do SharePoint.

    Quando seguir estas instruções, tem de configurar o SharePoint para utilizar o conector ao especificar a opção **Utilizar este servidor RMS** e, em seguida, introduzir o URL do conector com balanceamento de carga que configurou. Introduza o prefixo do protocolo (HTTP:// ou HTTPS://) e o nome do conector que foram definidos no DNS para o endereço com balanceamento de carga do seu conector. Por exemplo, se o nome do seu conector for https://connector.contoso.com, a sua configuração terá um aspeto semelhante ao da seguinte imagem:

    ![Configurar o SharePoint Server para o conector RMS](../media/AzRMS_SharePointConnector.png)

    Depois de a IRM estar ativada num farm do SharePoint, pode ativar a IRM em bibliotecas individuais através da opção **Gestão de Direitos de Informação** na página **Definições da Biblioteca** de cada uma das bibliotecas.


## <a name="configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector"></a>Configurar um servidor de ficheiros para a Infraestrutura de Classificação de Ficheiros para utilizar o conector
Para utilizar o conector RMS e a Infraestrutura de Classificação de Ficheiros para proteger documentos do Office, o servidor de ficheiros tem de ter um dos seguintes sistemas operativos em execução:

-   Windows Server 2012 R2

-   Windows Server 2012

### <a name="to-configure-file-servers-to-use-the-connector"></a>Para configurar servidores de ficheiros para utilizarem o conector

1.  Utilize a ferramenta de administração do conector RMS e as informações da secção [Autorizar os servidores a utilizar o conector RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) para se certificar de que os servidores de ficheiros estão autorizados a utilizar o conector RMS. Esta configuração é necessária para que o Exchange possa utilizar o conector RMS.

2.  Nos servidores de ficheiros configurados para a Infraestrutura de Classificação de Ficheiros e que irão comunicar com o conector RMS, efetue um dos seguintes procedimentos:

    -   Execute a ferramenta de configuração do servidor para o conector Microsoft RMS. Para mais informações, consulte [Como utilizar a ferramenta de configuração do servidor para o conector Microsoft RMS](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) neste artigo.

        Por exemplo, para executar a ferramenta localmente de modo a configurar um servidor de ficheiros com FCI:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetFCI2012
        ```

    - Faça edições de registo manuais com as informações disponíveis no artigo [Registry settings for the RMS connector (Definições de registo para o conector RMS – em inglês)](rms-connector-registry-settings.md) para adicionar as definições de registo manualmente nos servidores. 

3.  Crie regras de classificação e tarefas de gestão de ficheiros para proteger os documentos com Encriptação RMS e, em seguida, especifique um modelo de RMS para aplicar automaticamente as políticas de RMS. Para mais informações, consulte o artigo [Descrição Geral do Gestor de Recursos do Servidor de Ficheiros](http://technet.microsoft.com/library/hh831701.aspx) na biblioteca de documentação do Windows Server.

## <a name="next-steps"></a>Passos seguintes
Agora que o conector RMS está instalado e configurado, estando os servidores configurados para o utilizar, os administradores de TI e os utilizadores podem proteger e tirar partido das mensagens de e-mail e documentos com o serviço Azure Rights Management. Para facilitar o trabalho aos utilizadores, implemente o cliente do Azure Information Protection, que instala um suplemento para o Office e adiciona novas opções de contexto ao Explorador de Ficheiros. Para obter mais informações, veja o [Guia do administrador do Azure Information Protection](../rms-client/client-admin-guide.md).

Tenha em atenção que, se configurar modelos departamentais que pretende utilizar com as regras de transporte do Exchange ou com o Windows Server FCI, a configuração do âmbito tem de incluir a opção de compatibilidade de aplicações e a caixa de verificação **Mostrar este modelo a todos os utilizadores quando as aplicações não suportam a identidade de utilizador** tem de estar selecionada.

Pode utilizar o [Plano de implementação do Azure Information Protection](../plan-design/deployment-roadmap.md) para verificar se existem outros passos de configuração que seja necessário efetuar antes de implementar o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] para os utilizadores e administradores.

Para monitorizar o conector RMS, consulte o artigo [Monitorizar o conector do Azure Rights Management](monitor-rms-connector.md). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]