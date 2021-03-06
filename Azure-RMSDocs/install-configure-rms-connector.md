---
title: Instalar e configurar o conector Rights Management – AIP
description: Informações para o ajudar a instalar e configurar o conector Azure Rights Management (RMS). Estes procedimentos incluem os passos 1 a 4 da secção Implementar o conector do Azure Rights Management.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/12/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4fed9d4f-e420-4a7f-9667-569690e0d733
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b89bab8cd4ae7aecb8484f729001038b922360c8
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259436"
---
# <a name="installing-and-configuring-the-azure-rights-management-connector"></a>Instalar e configurar o conector Azure Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilize as seguintes informações para o ajudar a instalar e configurar o conector Azure Rights Management (RMS). Estes procedimentos abrangem os passos de 1 a 4 para [Implementar o conector do Azure Rights Management](deploy-rms-connector.md).

Antes de começar, certifique-se de que consultou e verificou os [pré-requisitos](deploy-rms-connector.md#prerequisites-for-the-rms-connector) para esta implementação.


## <a name="installing-the-rms-connector"></a>Instalar o conector RMS

1.  Identificar os computadores (mínimo de dois) dessa migrarmos
2.  l executa o conector do RMS. Os computadores têm de cumprir as especificações mínimas descritas nos pré-requisitos.

    > [!NOTE]
    > Instale um único conector RMS (composto por múltiplos servidores para elevada disponibilidade) por inquilino (inquilino do Office 365 ou do Azure AD). Ao contrário do Active Directory RMS, não precisa de instalar um conector RMS em cada floresta.

2.  Transfira os ficheiros de origem do conector RMS a partir do [Centro de Transferências da Microsoft](https://go.microsoft.com/fwlink/?LinkId=314106).

    Para instalar o conector RMS, transfira o ficheiro RMSConnectorSetup.exe.

    Além disso:

    -   Se posteriormente quiser configurar o conector de um computador de 32 bits, transfira também o ficheiro RMSConnectorAdminToolSetup_x86.exe.

    -   Se pretender utilizar a ferramenta de configuração do servidor para o conector RMS, para automatizar a configuração das definições de registo nos seus servidores no local, transfira também GenConnectorConfig.ps1.

3.  No computador em que pretende instalar o conector RMS, execute o ficheiro **RMSConnectorSetup.exe** com privilégios de Administrador.

4.  Na página de boas-vindas de configuração de conector do Microsoft Rights Management, selecione **conector de instalar o Microsoft Rights Management no computador**e, em seguida, clique em **próxima**.

5.  Leia e aceite os termos de licença do conector RMS e, em seguida, clique em **Seguinte**.

Para continuar, introduza uma conta e palavra-passe para configurar o conector RMS.

## <a name="entering-credentials"></a>Introduzir credenciais
Antes de configurar o conector RMS, tem de introduzir as credenciais da conta que tem privilégios suficientes para configurar o conector RMS. Por exemplo, pode escrever <strong>admin@contoso.com</strong> e, em seguida, especificar a palavra-passe desta conta.

Esta conta não deve exigir a autenticação multifator (MFA) porque a ferramenta de administração do Microsoft Rights Management não suporta a MFA para esta conta. 

O conector também tem algumas restrições de carateres para esta palavra-passe. Não é possível utilizar uma palavra-passe que tenha os seguintes carateres: "E" comercial ( **&** ); esquerdo Reto ( **[** ); certo Reto ( **]** ); diretamente entre aspas ( **"** ); e apóstrofo ( **'** ). Se a sua palavra-passe tiver algum destes carateres, a autenticação do conector RMS irá falhar e receberá a mensagem de erro **Essa combinação de nome de utilizador e palavra-passe não está correta**, mesmo que já tenha conseguido iniciar sessão com esta conta e palavra-passe noutros cenários. Se este cenário aplica-se a sua palavra-passe, utilize uma conta com uma palavra-passe que não tenha nenhum destes carateres especiais ou reponha a palavra-passe para que ele não tem nenhum destes carateres especiais.

Além disso, se tiver implementado [controlos de integração](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), certifique-se de que a conta especificada tem a capacidade de proteger conteúdos. Por exemplo, se tiver restringido a capacidade de proteger conteúdos ao grupo "Departamento de TI", a conta que especificar tem de ser membro desse grupo. Caso contrário, verá a mensagem de erro: **Falha ao tentar descobrir a localização do serviço de administração e organização. Certifique-se de que o serviço Microsoft Rights Management está ativado para a sua organização.**

Pode utilizar uma conta que tenha um dos seguintes privilégios:

- **Administrador global do seu inquilino**: Uma conta que seja um administrador global para o seu inquilino do Office 365 ou inquilino do Azure AD.

- **Administrador global do Azure Rights Management**: Uma conta no Azure Active Directory que tenha sido atribuída a função de administrador global do Azure RMS.

- **Administrador do conector Rights Management do Azure**: Uma conta no Azure Active Directory com direitos para instalar e administrar o conector RMS para a sua organização.

  > [!NOTE]
  > A função de administrador global do Azure Rights Management e a função de administrador do conector do Azure Rights Management são atribuídas às contas através do cmdlet [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) do Azure RMS.
  > 
  > Para executar o conector do RMS com o mínimo de privilégios, crie uma conta dedicada para este efeito que depois atribui a função de administrador do conector do Azure RMS através do seguinte procedimento:
  > 
  > 1. Se ainda não o fez, transfira e instale o Windows PowerShell para o Rights Management. Para obter mais informações, consulte [instalar o módulo do PowerShell do AADRM](install-powershell.md).
  > 
  >    Inicie o Windows PowerShell com o comando **Executar como administrador** e estabeleça ligação ao serviço Azure RMS através do comando [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice):
  > 
  >    ```
  >    Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
  >    ```
  > 2. Em seguida, execute o comando [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) com apenas um dos seguintes parâmetros:
  > 
  >    ```
  >    Add-AadrmRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
  >    ```
  > 
  >    ```
  >    Add-AadrmRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
  >    ```
  > 
  >    ```
  >    Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
  >    ```
  >    Por exemplo, escreva: **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role "ConnectorAdministrator"**
  > 
  >    Embora estes comandos atribuam a função de administrador do conector, também pode utilizar a função GlobalAdministrator aqui.

Durante o processo de instalação do conector RMS, todos os softwares de pré-requisito são validados e instalados, os Serviços de Informação Internet (IIS) são instalados se ainda não estiverem presentes e o software do conector é instalado e configurado. Além disso, o Azure RMS é preparado para configuração ao criar o seguinte:

-   Uma tabela vazia dos servidores que têm autorização para utilizar o conector para comunicar com o Azure RMS. Adicionará os servidores a esta tabela mais tarde.

-   Um conjunto de tokens de segurança do conector, que autoriza operações no Azure RMS. Estes tokens são transferidos a partir do Azure RMS e instalados no computador local no registo. São protegidos através da interface de programação da aplicação de proteção de dados (DPAPI) e das credenciais de conta do Sistema Local.

Na página final do assistente, efetue o seguinte procedimento e, em seguida, clique em **Concluir**:

-   Se este for o primeiro conector que instala, não selecione ainda a opção **Iniciar a consola do administrador do conector para autorizar servidores**. Selecione esta opção depois de instalar o seu segundo (ou último) conector RMS. Em alternativa, execute novamente o assistente em pelo menos mais um computador. Tem de instalar um mínimo de dois conectores.

-   Se já tiver instalado o seu segundo (ou último) conector, selecione **Iniciar a consola do administrador do conector para autorizar servidores**.

> [!TIP]
> Nesta fase, existe um teste de verificação que pode realizar para testar se os serviços Web do conector RMS estão operacionais:
>
> -   Num browser, estabeleça ligação a **http://&lt;endereçodoconector&gt;/_wmcs/certification/servercertification.asmx** e substitua *&lt;endereçodoconector&gt;* pelo nome ou endereço do servidor que tem o conector RMS instalado. Uma ligação com êxito apresenta a página **ServerCertificationWebService**.

Se precisar de desinstalar o conector RMS, execute novamente o assistente e selecione a opção Desinstalar.

Se tiver problemas durante a instalação, verifique o registo de instalação: **%LocalAppData%\Temp\Microsoft Rights Management connector_\<data e hora >. log** 

Por exemplo, o registo de instalação pode ter um aspeto semelhante connector_20170803110352.log C:\Users\Administrator\AppData\Local\Temp\Microsoft Rights Management

## <a name="authorizing-servers-to-use-the-rms-connector"></a>Autorizar os servidores a utilizar o conector RMS
Quando tiver instalado o conector RMS em pelo menos dois computadores, está pronto para autorizar os servidores e os serviços com os quais quer utilizar o conector RMS. Por exemplo, os servidores com o Exchange Server 2013 ou o SharePoint Server 2013.

Para definir estes servidores, execute a ferramenta de administração do conector RMS e adicione entradas à lista de servidores permitidos. Pode executar esta ferramenta quando selecionar a opção **Iniciar a consola do administrador do conector para autorizar servidores** no final do Assistente de configuração do conector Microsoft Rights Management ou pode executá-la separadamente do assistente.

Quando autorizar estes servidores, tenha em consideração o seguinte:

- Os servidores que adicionar terão privilégios especiais. Todas as contas que especificar para a função do Exchange Server na configuração do conector terão a [função de superutilizador](configure-super-users.md) no Azure RMS, que lhes concede acesso a todos os conteúdos deste inquilino RMS. Se necessário, a funcionalidade de superutilizador é ativada automaticamente nesta fase. Para evitar o risco de segurança da elevação de privilégios, tenha o cuidado de especificar apenas as contas que são utilizadas pelos servidores Exchange da sua organização. Todos os servidores configurados como servidores do SharePoint ou servidores de ficheiros que utilizem a FCI (Infraestrutura de Classificação de Ficheiros) terão privilégios de utilizador normais.

- Pode adicionar múltiplos servidores como uma única entrada, ao especificar um grupo de distribuição ou de segurança do Active Directory ou uma conta de serviço que seja utilizada por mais do que um servidor. Quando utiliza esta configuração, o grupo de servidores compartilha os mesmos certificados RMS e está a ser considerados proprietários dos conteúdos protegidos por qualquer um deles. Para minimizar as tarefas administrativas adicionais, recomendamos que utilize esta configuração de um único grupo, em vez de servidores individuais, para autorizar os servidores Exchange da sua organização ou um farm de servidores do SharePoint.

Na página **Servidores com permissão para utilizar o conector**, clique em **Adicionar**.

> [!NOTE]
> A autorização de servidores é a configuração do Azure RMS equivalente à configuração do AD RMS, que consiste em aplicar manualmente direitos NTFS ao ServerCertification.asmx para a conta de serviço ou do computador servidor e, também, em conceder manualmente direitos de superutilizador às contas do Exchange. Não é necessário aplicar direitos NTFS ao ServerCertification.asmx no conector.


### <a name="add-a-server-to-the-list-of-allowed-servers"></a>Adicionar um servidor à lista de servidores permitidos
Na página **Permitir que um servidor utilize o conector**, introduza o nome do objeto ou procure para identificar o objeto a autorizar.

É importante que autorize o objeto correto. Para um servidor utilizar o conector, a conta que executa o serviço no local (por exemplo, o Exchange ou o SharePoint) tem de estar selecionada para autorização. Por exemplo, se o serviço estiver a ser executado como conta de serviço configurada, adicione o nome dessa conta de serviço à lista. Se o serviço estiver a ser executado como Sistema Local, adicione o nome do objeto do computador (por exemplo, NOMEDOSERVIDOR$) Como melhor prática, crie um grupo composto por estas contas e especifique o grupo em vez de nomes de servidores individuais.

Mais informações sobre as diferentes funções de servidor:

-   Para servidores que executam o Exchange: Tem de especificar um grupo de segurança e pode utilizar o grupo predefinido (**servidores Exchange**) que Exchange automaticamente cria e mantém todos os servidores do Exchange na floresta.

-   Para os servidores que executam o SharePoint:

    -   Se um servidor do SharePoint 2010 estiver configurado para executar como Sistema Local (não está a utilizar uma conta de serviço), crie manualmente um grupo de segurança nos Serviços de Domínio do Active Directory e adicione o nome de objeto de computador do servidor nesta configuração ao grupo.

    -   Se um servidor do SharePoint estiver configurado para utilizar uma conta de serviço (a prática recomendada para o SharePoint 2010 e a única opção para o SharePoint 2016 e o SharePoint 2013), faça o seguinte:

        1.  Adicione a conta de serviço que executa o serviço da Administração Central do SharePoint para permitir que o SharePoint seja configurado a partir da respetiva consola do administrador.

        2.  Adicione a conta que está configurada para o Conjunto Aplicacional do SharePoint.

        > [!TIP]
        > Se estas duas contas forem diferentes, pondere criar um único grupo que contenha ambas as contas para minimizar as tarefas administrativas adicionais.

-   Para os servidores de ficheiros que utilizam a Infraestrutura de Classificação de Ficheiros, os serviços associados são executados como a conta do Sistema Local, por isso, tem de autorizar a conta do computador para os servidores de ficheiros (por exemplo, NOMEDOSERVIDOR$) ou um grupo que contenha essas contas de computador.

Quando terminar de adicionar os servidores à lista, clique em **Fechar**.

Se ainda não o tiver feito, tem de configurar agora o balanceamento de carga dos servidores que têm o conector RMS instalado e decidir se quer utilizar HTTPS nas ligações entre estes servidores e os servidores que acabou de autorizar.

## <a name="configuring-load-balancing-and-high-availability"></a>Configurar o balanceamento de carga e a elevada disponibilidade
Depois de instalar a segunda ou última instância do conector RMS, defina um nome de servidor do URL do conector e configure um sistema de balanceamento de carga.

O nome de servidor do URL do conector pode ser qualquer nome dentro do espaço de nomes controlado por si. Por exemplo, pode criar uma entrada no seu sistema DNS para **rmsconnector.contoso.com** e configurar esta entrada para utilizar um endereço IP no seu sistema de balanceamento de carga. Não existem requisitos especiais para este nome e não precisa de ser configurado nos próprios servidores do conector. A menos que os seus servidores Exchange e do SharePoint comuniquem com o conector através da Internet, este nome não precisa de resolver na Internet.

> [!IMPORTANT]
> Recomendamos que não altere este nome após ter configurado os servidores Exchange e do SharePoint para utilizar o conector, uma vez que teria de limpar as configurações de IRM destes servidores e, depois, reconfigurá-las.

Depois de criar o nome no DNS e de o configurar para um endereço IP, configure o balanceamento de carga desse endereço, que redireciona o tráfego para os servidores do conector. Pode utilizar qualquer balanceador de carga baseado em IP para este fim, que inclua a funcionalidade Balanceamento de Carga na Rede (NLB) no Windows Server. Para obter mais informações, consulte o [Load Balancing Deployment Guide ](https://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx) (Guia de Implementação do Balanceamento de Carga – em inglês).

Utilize as seguintes definições para configurar o cluster com balanceamento de carga em rede (NLB):

-   Portas: 80 (para HTTP) ou 443 (para HTTPS)

    Para obter mais informações sobre quando utilizar HTTP ou HTTPS, consulte a secção seguinte.

-   Afinidade: Nenhum

-   Método de distribuição: Equal

O nome que define para o sistema com balanceamento de carga (para os servidores a executar o serviço do conector RMS) é o nome do conector RMS da sua organização que irá utilizar mais tarde, quando configurar os servidores no local para utilizar o Azure RMS.

## <a name="configuring-the-rms-connector-to-use-https"></a>Configurar o conector RMS para utilizar HTTPS
> [!NOTE]
> Este passo da configuração é opcional, mas é recomendado para uma segurança adicional.

Embora o uso de TLS ou SSL seja opcional para o conector RMS, recomendamos que seja utilizado para todos os serviços de segurança importantes baseados em HTTP. Esta configuração autentica os servidores que estão a executar o conector nos seus servidores Exchange e do SharePoint que utilizam o conector. Além disso, todos os dados enviados a partir destes servidores para o conector são encriptados.

Para ativar o conector RMS para utilizar TLS, em cada servidor que executa o conector RMS, instale um certificado de autenticação de servidor que contenha o nome que irá utilizar para o conector. Por exemplo, se o nome do seu conector RMS que definiu no DNS for **rmsconnector.contoso.com**, implemente um certificado de autenticação de servidor que contenha **rmsconnector.contoso.com** como nome comum no requerente do certificado. Em alternativa, especifique **rmsconnector.contoso.com** como valor DNS no nome alternativo do certificado. O certificado não precisa de incluir o nome do servidor. Em seguida, nos IIS, vincule este certificado ao Web Site Predefinido.

Se utilizar a opção HTTPS, certifique-se de que todos os servidores que executam o conector têm um certificado de autenticação de servidor válido que encadeia numa AC de raiz considerada fidedigna pelos servidores Exchange e do SharePoint. Além disso, se a autoridade de certificação (AC) que emitiu o certificado para os servidores do conector publicar uma lista de revogação de certificados (CRL), os servidores Exchange e do SharePoint têm de conseguir transferir esta CRL.

> [!TIP]
> Pode utilizar os seguintes recursos e informações para o ajudar a pedir e instalar um certificado de autenticação de servidor e para vincular este certificado ao Web Site Predefinido no IIS:
>
> - Se utilizar os Serviços de Certificados do Active Directory (AD CS) e uma autoridade de certificação empresarial (AC) para implementar estes certificados de autenticação de servidor, pode duplicar e utilizar o modelo de certificado do Web Server. Este modelo de certificado utiliza a opção **Fornecido no pedido** para o nome do requerente do certificado, o que significa que pode fornecer o FQDN do nome do conector RMS para o nome do requerente do certificado ou um nome de requerente alternativo quando pedir o certificado.
> -   Se utilizar uma AC autónoma ou adquirir este certificado a partir de outra empresa, consulte [Configuring Internet Server Certificates (IIS 7) (Configurar Certificados do Servidor de Internet (IIS 7) – em inglês)](https://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx) na biblioteca de documentos referente ao [Web Server (IIS)](https://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) no TechNet.
> - Para configurar o IIS para utilizar o certificado, veja [Add a Binding to a Site (IIS 7) (Adicionar um Enlace a um Site (IIS 7))](https://technet.microsoft.com/library/cc731692.aspx) na biblioteca de documentos referente ao [Web Server (IIS)](https://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) no TechNet.

## <a name="configuring-the-rms-connector-for-a-web-proxy-server"></a>Configurar o conector RMS para um servidor proxy Web
Se os servidores do seu conector estiverem instalados numa rede que não tem conectividade Internet direta e que necessita de configuração manual de um servidor proxy Web para o acesso à Internet de saída, tem de configurar o registo nestes servidores para o conector RMS.

#### <a name="to-configure-the-rms-connector-to-use-a-web-proxy-server"></a>Para configurar o conector RMS para utilizar um servidor proxy Web

1.  Abra o editor de registo, por exemplo o Regedit, em cada servidor que executa o conector RMS.

2.  Navegue para **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**

3.  Adicione o valor de cadeia de **ProxyAddress** e, em seguida, defina os Dados deste valor como **http://&lt;OMeuDomínioDeProxyOuEndereçoIP&gt;:&lt;AMinhaPortaDeProxy&gt;**

    Por exemplo: **http://proxyserver.contoso.com:8080**

4.  Feche o editor de registo e, em seguida, reinicie o servidor ou execute o comando IISReset para reiniciar o IIS.

## <a name="installing-the-rms-connector-administration-tool-on-administrative-computers"></a>Instalar a ferramenta de administração do conector RMS em computadores administrativos
Pode executar a ferramenta de administração do conector RMS a partir de um computador que não tenha o conector RMS instalado, se esse computador cumprir os seguintes requisitos:

-   Um computador físico ou virtual com o Windows Server 2012 ou Windows Server 2012 R2 (todas as edições), o Windows Server 2008 R2 ou Windows Server 2008 R2 Service Pack 1 (todas as edições), o Windows 8.1, o Windows 8 ou o Windows 7.

-   Um mínimo de 1 GB de RAM.

-   Um mínimo de 64 GB de espaço em disco.

-   Pelo menos uma interface de rede.

-   Acesso à Internet através da firewall (ou proxy Web).

Para instalar a ferramenta de administração do conector RMS, execute os seguintes ficheiros:

-   Para um computador de 32 bits: RMSConnectorAdminToolSetup_x86.exe

-   Para um computador de 64 bits: RMSConnectorSetup.exe

Se ainda não tiver transferido estes ficheiros, pode fazê-lo no [Centro de Transferências da Microsoft](https://go.microsoft.com/fwlink/?LinkId=314106).


## <a name="next-steps"></a>Passos Seguintes
Agora que o conector RMS está instalado e configurado, está pronto para configurar os seus servidores no local para utilizá-lo. Aceda a [Configuring servers for the Azure Rights Management connector](configure-servers-rms-connector.md) (Configurar servidores para o conector Azure Rights Management – em inglês).

