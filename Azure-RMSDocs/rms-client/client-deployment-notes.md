---
title: Notas de implementação do cliente do RMS – AIP
description: Informações sobre instalação, sistemas operativos suportados, definições de registo e deteção de serviços da versão 2 do cliente de Rights Management Service (cliente do RMS), também conhecida como cliente MSIPC.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e1c8e79fefd94d4c0fb5ca2997726d1864f0019e
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151848"
---
# <a name="rms-client-deployment-notes"></a>Notas de implementação do cliente do RMS

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 7 com SP1, Windows 8, Windows 8.1, Windows 10, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2, Windows Server 2016*

A versão 2 do cliente de Rights Management Service (cliente do RMS) é também conhecida como cliente MSIPC. É o software para computadores com o Windows que comunica com os serviços do Microsoft Rights Management no local ou na cloud, para ajudar a proteger o acesso e a utilização de informações que fluem através de aplicações e dispositivos, dentro dos limites da sua organização ou fora desses limites geridos. 

Além de ser enviado com o [cliente do Azure Information Protection para Windows](aip-client.md), o cliente do RMS está disponível [como uma transferência opcional](http://www.microsoft.com/download/details.aspx?id=38396) que pode, com a confirmação e a aceitação do contrato de licença, ser livremente distribuída com software de terceiros para que os clientes possam proteger e consumir conteúdos protegidos por serviços de Gestão de Direitos.


## <a name="redistributing-the-rms-client"></a>Redistribuir o cliente do RMS
O cliente do RMS pode ser livremente redistribuído e incluído com outras aplicações e soluções de TI. Se for programador de aplicações ou fornecedor de soluções e quiser redistribuir o cliente do RMS, tem duas opções:

- Recomendado: incorporar o instalador do cliente do RMS na instalação da aplicação e executá-lo no modo silencioso (o parâmetro **/quiet**, detalhado na secção seguinte).

- Tornar o cliente do RMS um pré-requisito da sua aplicação. Com esta opção, poderá ser necessário fornecer aos utilizadores instruções adicionais para que obtenham, instalem e atualizem os seus computadores com o cliente, para poderem utilizar a aplicação.

## <a name="installing-the-rms-client"></a>Instalar o cliente do RMS
O cliente do RMS está contido num ficheiro executável instalador denominado **setup_msipc*\<arch\>*.exe**, onde  *\<arch >* está **x86** (para computadores de cliente de 32 bits) ou **x64** (para computadores de cliente de 64 bits). O pacote do instalador de 64 bits (x64) instala um executável de 32 bits, para compatibilidade com aplicações de 32 bits executadas numa instalação de sistema operativo de 64 bits, e um executável de 64 bits, para suportar aplicações de 64 bits nativas. O instalador de 32 bits (x86) não é executado numa instalação do Windows de 64 bits.

> [!NOTE]
> Tem de ter privilégios elevados para instalar o cliente do RMS, por exemplo enquanto membro do grupo Administradores no computador local.

Pode instalar o cliente do RMS através de um dos seguintes métodos de instalação:

- **Modo silencioso.** Ao utilizar o parâmetro **/quiet** como parte das opções da linha de comandos, pode instalar silenciosamente o cliente do RMS nos computadores. O exemplo seguinte mostra uma instalação do cliente do RMS no modo silencioso, num computador cliente de 64 bits:

    ```
    setup_msipc_x64.exe /quiet
    ```

- **Modo interativo.** Em alternativa, pode instalar o cliente do RMS com o programa de instalação baseada em GUI fornecida pelo Assistente de instalação de cliente do RMS. Para instalar interativamente, faça duplo clique o pacote de instalador do cliente de RMS (**setup_msipc*\<arch\>*.exe**) na pasta à qual foi copiado ou transferido no local computador.

## <a name="questions-and-answers-about-the-rms-client"></a>Perguntas e respostas sobre o cliente do RMS
A secção seguinte contém as perguntas mais frequentes sobre o cliente do RMS e as respostas às mesmas.

### <a name="which-operating-systems-support-the-rms-client"></a>Que sistemas operativos suportam o cliente do RMS?
O cliente do RMS é suportado nos seguintes sistemas operativos:

|Sistema Operativo Windows Server|Sistema Operativo Windows Client|
|-----------------------------------|-----------------------------------|
|Windows Server 2016|Windows 10|
|Windows Server 2012 R2|Windows 8.1|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7 com, pelo menos, o SP1|


### <a name="which-processors-or-platforms-support-the--rms-client"></a>Que processadores ou plataformas suportam o cliente do RMS?
O cliente do RMS é suportado nas plataformas de processamento x86 e x64.

### <a name="where-is-the--rms-client-installed"></a>Onde está instalado o cliente do RMS?
Por predefinição, o cliente do RMS é instalado em %ProgramFiles%\Active Directory Rights Management Services Client 2. \<menor número de versão >.

### <a name="what-files--are-associated-with-the-rms-client-software"></a>Que ficheiros estão associados ao software do cliente do RMS?
Os seguintes ficheiros são instalados como parte do software do cliente do RMS:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Além destes ficheiros, o cliente do RMS também instala ficheiros de suporte da interface de utilizador multilingues (MUI) em 44 idiomas. Para verificar os idiomas suportados, execute a instalação do cliente do RMS e, quando a instalação for concluída, veja os conteúdos das pastas de suporte multilingue no caminho predefinido.

### <a name="is-the-rms-client-included-by-default-when-i-install-a-supported-operating-system"></a>O cliente do RMS está incluído por predefinição quando instalo um sistema operativo suportado?
Não. Esta versão do cliente do RMS é fornecida como uma transferência opcional que pode ser instalada separadamente em computadores com versões suportadas do sistema operativo Microsoft Windows.

### <a name="is-the-rms-client-automatically-updated-by-microsoft-update"></a>O cliente do RMS é automaticamente atualizado pelo Microsoft Update?
Se instalou o cliente do RMS através da opção de instalação silenciosa, o cliente do RMS herda as suas definições atuais do Microsoft Update. Se instalou o cliente do RMS com o programa de configuração baseado na GUI, o assistente de instalação do cliente do RMS pede para ativar o Microsoft Update.

## <a name="rms-client-settings"></a>Definições do cliente do RMS
A secção seguinte contém informações sobre as definições do cliente do RMS. Estas informações poderão ser úteis se tiver problemas com aplicações ou serviços que utilizam o cliente do RMS.

> [!NOTE]
> Algumas definições só estarão disponíveis se a aplicação otimizada para o RMS for executada como uma aplicação de modo de cliente (tal como o Microsoft Word e o Outlook ou o cliente do Azure Information Protection com o Explorador de Ficheiros do Windows) ou uma aplicação de modo de servidor (tal como o SharePoint e o Exchange). Nas tabelas seguintes, estas definições são identificadas como **Modo de Cliente** e **Modo de Servidor**, respetivamente.

### <a name="where-the-rms-client-stores-licenses-on-client-computers"></a>Local onde o cliente do RMS armazena licenças nos computadores cliente
O cliente do RMS armazena licenças no disco local e também coloca em cache algumas informações no registo do Windows.

|Descrição|Caminhos do Modo de Cliente|Caminhos do Modo de Servidor|
|---------------|---------------------|---------------------|
|Localização do arquivo das licenças|%localappdata%\Microsoft\MSIPC|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\\*\<SID\>*|
|Localização do arquivo dos modelos|%localappdata%\Microsoft\MSIPC\Templates|%ALLUSERSPROFILE%\Microsoft\MSIPC\Server\\*\<SID\>*|
|Localização do Registo|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> \Local Settings<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \\*\<SID*\>|

> [!NOTE]
> *\<SID*> é o identificador de segurança (SID) da conta sob a qual a aplicação de servidor está em execução. Por exemplo, se a aplicação está em execução na conta de serviço de rede incorporada, substitua *\<SID\>* com o valor do SID já conhecido dessa conta (S-1-5 e 20).

### <a name="windows-registry-settings-for-the-rms-client"></a>Definições do registo do Windows para o cliente do RMS
Pode utilizar as chaves do registo do Windows para definir ou modificar algumas configurações do cliente do RMS. Por exemplo, enquanto administrador de aplicações otimizadas para o RMS que comunicam com servidores do AD RMS, poderá querer atualizar a localização de serviço da empresa (substituir o servidor do AD RMS atualmente selecionado para publicação), dependendo da localização atual do computador cliente na topologia do Active Directory. Em alternativa, poderá querer ativar o controlo de RMS no computador cliente, para ajudar a resolver um problema com uma aplicação otimizada para o RMS. Utilize a seguinte tabela para identificar as definições do registo que podem ser alteradas para o cliente do RMS.

|Tarefa|Definições|
|--------|------------|
|Se a versão do cliente for 1.03102.0221 ou posterior:<br /><br />**Para controlar a recolha de dados da aplicação**|**Importante**: para respeitar a privacidade dos utilizadores, enquanto administrador deverá pedir autorização aos mesmos antes de ativar a recolha de dados.<br /><br />Se ativar a recolha de dados, está a aceitar o envio de dados para a Microsoft através da Internet. A Microsoft utiliza estes dados para fornecer e melhorar a qualidade, segurança e integridade dos produtos e serviços Microsoft. Por exemplo, a Microsoft analisa o desempenho e fiabilidade, como as funcionalidades utilizar, como rapidamente os recursos de respondem, desempenho do dispositivo, as interações de interface de utilizador e quaisquer problemas com o produto. Dados também incluem informações sobre a configuração de software, como o software que está a executar atualmente e o endereço IP.<br /><br />Para a versão 1.0.3356 ou posterior: <br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft\MSIPC<br />REG_DWORD: DiagnosticAvailability<br /><br />Para versões anteriores 1.0.3356: <br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft\MSIPC<br />REG_DWORD: DiagnosticState<br /><br />**Valor:** 0 para a Aplicação definida (predefinição) através da propriedade de ambiente [IPC_EI_DATA_COLLECTION_ENABLED](https://msdn.microsoft.com/library/hh535247(v=vs.85).aspx), 1 para Desativado, 2 para Ativado<br /><br />**Tenha em atenção**: se a aplicação baseada em MSIPC de 32 bits está em execução numa versão de 64 bits do Windows, a localização será HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC.|
|Apenas AD RMS:<br /><br />**Para atualizar a localização do serviço da empresa para um computador cliente**|Atualize as seguintes chaves do registo:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />REG_SZ: default<br /><br />**Valor:**\<http ou https>://*RMS_Cluster_Name*/_wmcs/Certification<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />REG_SZ: default<br /><br />**Valor:** \<http ou https>://*RMS_Cluster_Name*/_wmcs/Licensing|
|**Para ativar e desativar o rastreio**|Atualize a seguinte chave do registo:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />REG_DWORD: Trace<br /><br />**Valor:** 1 para ativar o rastreio, 0 para desativar o rastreio (predefinição)|
|**Para alterar a frequência de atualização dos modelos em dias**|Os seguintes valores de registo especificam a frequência com que modelos de atualização no computador do usuário se o valor de TemplateUpdateFrequencyInSeconds não estiver definido.  Se nenhum destes valores estiver definido, o intervalo de atualização predefinido para que as aplicações com o cliente do RMS (versão 1.0.1784.0) transfiram modelos é de 1 dia. As versões anteriores têm um valor predefinido de 7 dias.<br /><br />**Modo de Cliente:**<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Valor:** um valor inteiro que especifica o número de dias (mínimo de 1) entre transferências.<br /><br />**Modo de Servidor:**<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\\<SID\><br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Valor:** um valor inteiro que especifica o número de dias (mínimo de 1) entre transferências.|
|**Para alterar a frequência de atualização dos modelos em segundos**<br /><br />Importante: Se esta definição for especificada, o valor para a atualização dos modelos em dias é ignorado. Especifique uma das definições, não ambas.|Os seguintes valores de registo especificam a frequência com que modelos de atualização no computador do usuário. Se este valor ou o valor para alterar a frequência em dias (TemplateUpdateFrequency) não for definido, o intervalo de atualização predefinido para que as aplicações com o cliente do RMS (versão 1.0.1784.0) transfiram modelos é de 1 dia. As versões anteriores têm um valor predefinido de 7 dias.<br /><br />**Modo de Cliente:**<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Valor:** um valor inteiro que especifica o número de segundos (mínimo de 1) entre transferências.<br /><br />**Modo de Servidor:**<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\\<*SID*><br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Valor:** um valor inteiro que especifica o número de segundos (mínimo de 1) entre transferências.|
|Apenas AD RMS:<br /><br />**Para transferir modelos de forma imediata no pedido de publicação seguinte**|No decorrer de testes e avaliações, poderá querer que o cliente do RMS transfira modelos logo que seja possível. Para esta configuração, remova a seguinte chave de registo e o cliente do RMS, em seguida, downloads modelos imediatamente no próxima de publicação do pedido em vez de aguardar que a hora especificada pela definição do registo TemplateUpdateFrequency:<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\\<*Nome do Servidor*>\Template <br /><br />**Nota**: o valor \<*Nome do Servidor*> pode ter URLs externos (corprights.contoso.com) e internos (corprights) e, por conseguinte, duas entradas diferentes.|
|Apenas AD RMS:<br /><br />**Para ativar o suporte para a autenticação federada**|Se o computador do cliente do RMS estiver ligado a um cluster do AD RMS, através de uma fidedignidade federada, é necessário configurar o realm inicial da federação.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_SZ: FederationHomeRealm<br /><br />**Valor:** o valor desta entrada de registo é o uniform resource identifier (URI) para o serviço de Federação (por exemplo, "http://TreyADFS.trey.net/adfs/services/trust").<br /><br /> **Nota**: é importante que especifique http e não https para este valor. Além disso, se a sua aplicação baseada em MSIPC de 32 bits está em execução numa versão de 64 bits do Windows, a localização é HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Federation. Para uma configuração de exemplo, veja [Implementar os Serviços de Gestão de Direitos do Active Directory com os Serviços de Federação do Active Directory](https://technet.microsoft.com/library/dn758110.aspx).|
|Apenas AD RMS:<br /><br />**Para suportar servidores de federação parceiros que requerem a autenticação baseada em formulários para a introdução de dados pelo utilizador**|Por predefinição, o cliente do RMS funciona em modo silencioso e não é necessária a introdução de dados pelo utilizador. No entanto, os servidores de federação parceiros poderão ser configurados para exigir a introdução de dados pelo utilizador, através, por exemplo, da autenticação baseada em formulários. Neste caso, é necessário configurar o cliente do RMS para ignorar o modo silencioso, para que o formulário de autenticação federada seja apresentado numa janela do browser e seja pedida autenticação ao utilizador.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_DWORD: EnableBrowser<br /><br />**Nota**: se o servidor de federação estiver configurado para utilizar a autenticação baseada em formulários, esta chave é necessária. Se o servidor de Federação estiver configurado para utilizar a autenticação integrada do Windows, esta chave não é necessária.|
|Apenas AD RMS:<br /><br />**Para bloquear o consumo do serviço ILS**|Por predefinição, o cliente do RMS ativa o consumo de conteúdos protegidos pelo serviço ILS, mas é possível configurar o cliente para bloquear este serviço ao definir a seguinte chave do registo. Se esta chave de registo está definida para bloquear o serviço ILS, todas as tentativas para abrir e consumir conteúdo protegido pelo serviço ILS devolve o erro seguinte:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: **DisablePassportCertification**<br /><br />**Valor:** 1 para bloquear o consumo de ILS, 0 para permitir o consumo de ILS (predefinição)|

### <a name="managing-template-distribution-for-the-rms-client"></a>Gerir a distribuição de modelos para o cliente do RMS
Modelos tornam mais fácil para os utilizadores e administradores aplicarem rapidamente a proteção do Rights Management e o cliente do RMS transfira automaticamente modelos dos seus servidores ou serviço RMS. Se colocar os modelos na seguinte localização de pasta, o cliente do RMS não transferir nenhum modelo a partir da localização predefinida e, em vez disso, transfira os modelos colocados nesta pasta. O cliente do RMS poderá continuar a transferir modelos a partir de outros servidores de RMS disponíveis.

**Modo de Cliente:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Modo de Servidor**: %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\\*\<SID\>*

Ao utilizar esta pasta, não é necessária qualquer convenção de nomenclatura especial, embora os modelos devam ser emitidos pelo servidor ou serviço RMS e tenham de ter a extensão de nome de ficheiro .xml. Por exemplo, Contoso–Confidencial.xml ou Contoso–ApenasLeitura.xml são nomes válidos.

## <a name="ad-rms-only-limiting-the-rms-client-to-use-trusted-ad-rms-servers"></a>Apenas AD RMS: limitar o cliente do RMS para utilizar servidores do AD RMS fidedignos
É possível limitar o cliente do RMS apenas à utilização de servidores do AD RMS fidedignos específicos, ao fazer as seguintes alterações no registo do Windows, nos computadores locais.

**Para ativar a limitação do cliente do RMS para utilizar apenas servidores do AD RMS fidedignos**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
   
    REG_DWORD:AllowTrustedServersOnly
    
    **Valor:** se for especificado um valor diferente de zero, o cliente do RMS confia apenas os servidores especificados que estejam configurados na lista TrustedServers e o serviço Azure Rights Management.

**Para adicionar membros à lista de servidores do AD RMS fidedignos**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    
    REG_SZ:*\<URL_or_HostName>*
    
    **Valor:** os valores de cadeia de caracteres nesta localização da chave de registo podem ser um formato de nome de domínio DNS (por exemplo, **adrms.contoso.com**) ou URLs completos para servidores AD RMS fidedignos (por exemplo, **https://adrms.contoso.com**). Se um URL especificado começar com **https://**, o cliente de RMS utiliza SSL ou TLS para contactar o servidor de AD RMS especificado.

## <a name="rms-service-discovery"></a>Deteção do serviço RMS
A deteção do serviço RMS permite que o cliente do RMS verifique com que servidor ou serviço RMS irá comunicar antes de proteger os conteúdos. Deteção do serviço também poderá ocorrer quando o cliente do RMS consumir conteúdos protegidos, mas esse tipo de deteção é pouco provável, uma vez que a política associada aos conteúdos inclui o servidor RMS ou o serviço preferencial. Apenas se as origens são sem êxito é o cliente, em seguida, executado a deteção do serviço.

Para efetuar a deteção do serviço, o cliente do RMS verifica o seguinte:

1. **O registo do Windows no computador local**: se as definições de deteção do serviço estiverem configuradas no registo, estas definições são experimentadas em primeiro lugar. 

    Por predefinição, estas definições não são configuradas no registo, mas um administrador pode configurá-las para o AD RMS, tal como documentado numa das [secções seguintes](#enabling-client-side-service-discovery-by-using-the-windows-registry). Normalmente um administrador configura essas definições para o serviço Azure Rights Management durante o [processo de migração](../migrate-from-ad-rms-phase2.md) a partir do AD RMS para o Azure Information Protection.

2. **Active Directory Domain Services**: um computador associado a um domínio consulta o Active Directory para procurar um ponto de ligação de serviço (SCP). 

    Se estiver registado um SCP, como é documentado na [secção seguinte](#ad-rms-only-enabling-server-side-service-discovery-by-using-active-directory), é devolvido o URL do servidor de AD RMS para o cliente do RMS utilizar.

3. **O serviço de deteção do Azure Rights Management**: O cliente de RMS liga-se ao **https://discover.aadrm.com**, que pede ao utilizador para autenticar.

    Quando a autenticação tiver sido concluída com êxito, o nome de utilizador (e o domínio) da autenticação é utilizado para identificar o inquilino do Azure Information Protection a utilizar. O URL do Azure Information Protection a utilizar para essa conta de utilizador é devolvido ao cliente de RMS. O URL é o seguinte formato: **https://**\<YourTenantURL\>**wmcs/licensing** 

    Por exemplo: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing

    O *\<URLdeInquilino\>* tem o seguinte formato: **{GUID}.rms.[Região].aadrm.com**. Pode encontrar este valor ao identificar o valor **RightsManagementServiceId** quando executar o cmdlet [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) do Azure RMS.

> [!NOTE]
> Existem quatro exceções importantes para este fluxo de deteção do serviço:
> 
> - Dispositivos móveis são mais adequados para utilizar um serviço em nuvem, portanto, por predefinição, utilizam a deteção do serviço para o serviço Azure Rights Management (https://discover.aadrm.com). Para substituir esta predefinição, para que os dispositivos móveis utilizam o AD RMS em vez do serviço Azure Rights Management, especificar registos SRV no DNS e instalar a extensão do dispositivo móvel, conforme documentado no [Directory Rights Management serviços Mobile dispositivos ativos Extensão](https://technet.microsoft.com/library/dn673574\(v=ws.11\).aspx). 
>
> - Quando o serviço Rights Management é invocado por uma etiqueta do Azure Information Protection, a deteção de serviço não é realizada. Em alternativa, o URL é especificado diretamente na definição da etiqueta que é configurada na política do Azure Information Protection. 
>  
> - Quando um utilizador inicia sessão a partir de uma aplicação do Office, o nome de utilizador (e o domínio) da autenticação é utilizado para identificar qual o inquilino do Azure Information Protection a utilizar. Neste caso, as definições de registo não são necessárias e o SCP não é verificado.
> 
> - Quando tiver configurado [redirecionamento de DNS](../migrate-from-ad-rms-phase3.md#client-reconfiguration-by-using-dns-redirection) para aplicações de ambiente de trabalho de clique-e-Use do Office 2016, o cliente do RMS localiza o serviço Azure Rights Management, que está a ser negado o acesso ao cluster do AD RMS que localizou anteriormente. Negar os acionadores de ação do cliente para procurar o registo SRV, que redireciona o cliente para o serviço Azure Rights Management para o seu inquilino. Este registo SRV também permite Exchange Online desencriptar e-mails que foram protegidos pelo cluster do AD RMS. 

### <a name="ad-rms-only-enabling-server-side-service-discovery-by-using-active-directory"></a>Apenas AD RMS: ativar a deteção do serviço do lado do servidor através do Active Directory
Se a sua conta tem privilégios suficientes (administradores da empresa e administrador local para o servidor AD RMS), pode registar automaticamente um ponto de ligação de serviço (SCP) quando instala o servidor de cluster de raiz do AD RMS. Se já existir um SCP na floresta, tem de eliminar primeiro o SCP existente para poder registar um novo.

Pode registar e eliminar um SCP após a instalação do AD RMS, através do seguinte procedimento. Antes de começar, certifique-se de que a sua conta tem os privilégios necessários (Administradores da Empresa e administrador local para o servidor do AD RMS).

#### <a name="to-enable-ad-rms-service-discovery-by-registering-an-scp-in-active-directory"></a>Para ativar a deteção do serviço AD RMS ao registar um SCP no Active Directory

1.  Abra a consola dos Serviços de Gestão do Active Directory no servidor do AD RMS:
    
    - Para o Windows Server 2012 R2 ou Windows Server 2012, no Gestor de servidor, selecione **ferramentas** > **serviços de gestão de direitos do Active Directory**.

    - Para o Windows Server 2008 R2, selecione **começar** > **ferramentas administrativas** > **serviços de gestão de direitos do Active Directory**.

2.  Na consola do AD RMS, faça duplo clique no cluster do AD RMS e, em seguida, clique em **propriedades**.

3.  Clique no separador **SCP**.

4.  Selecione a caixa de verificação **Alterar SCP**.

5.  Selecione a opção **Definir SCP para o cluster de certificação atual** e clique em **OK**.

### <a name="enabling-client-side-service-discovery-by-using-the-windows-registry"></a>Ativar a deteção do serviço do lado do cliente através do registo do Windows
Como alternativa à utilização de um SCP, ou caso não exista um SCP, pode configurar o registo do computador cliente para que o cliente do RMS possa localizar o respetivo servidor do AD RMS.

#### <a name="to-enable-client-side-ad-rms-service-discovery-by-using-the-windows-registry"></a>Para ativar a deteção do serviço AD RMS do lado do cliente através do registo do Windows

1. Abra o editor de registo do Windows, Regedit.exe:
    
    - No computador cliente, na janela Executar, escreva **regedit** e prima Enter para abrir o Editor de Registo.

2. No Editor de Registo, navegue até **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!NOTE]
    > Se estiver a executar uma aplicação de 32 bits num computador de 64 bits, navegue para **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3. Para criar a subchave ServiceLocation, clique com o botão direito do rato em **MSIPC**, aponte para **Novo**, clique em **Chave** e escreva **ServiceLocation**.

4. Para criar a subchave EnterpriseCertification, clique com o botão direito do rato em **ServiceLocation**, aponte para **Novo**, clique em **Chave** e escreva **EnterpriseCertification**.

5. Para definir o URL de certificação da empresa, faça duplo clique o **(predefinição)** valor no **EnterpriseCertification** subchave. Quando o **Editar cadeia de caracteres** é apresentada a caixa de diálogo, para **dados do valor**, tipo `<http or https>://<AD RMS_cluster_name>/_wmcs/Certification`e, em seguida, clique em **OK**.

6. Para criar a subchave EnterprisePublishing, clique com botão direito **ServiceLocation**, aponte para **New**, clique em **chave**e, em seguida, escreva `EnterprisePublishing`.

7. Para definir o URL de publicação da empresa, faça duplo clique **(predefinição)** sob a **EnterprisePublishing** subchave. Quando o **Editar cadeia de caracteres** é apresentada a caixa de diálogo, para **dados do valor**, tipo `<http or https>://<AD RMS_cluster_name>/_wmcs/Licensing`e, em seguida, clique em **OK**.

8.  Feche o Editor de Registo.

Se o cliente do RMS não é possível encontrar um SCP através da consulta do Active Directory e não for especificado no Registro, chamadas de deteção do serviço do AD RMS falhará.

### <a name="redirecting-licensing-server-traffic"></a>Redirecionar o tráfego do servidor de licenciamento
Em alguns casos, poderá ser necessário redirecionar o tráfego durante a deteção do serviço quando, por exemplo, duas organizações são fundidas e o servidor de licenciamento antigo numa organização é extinto, fazendo com que os clientes tenham de ser redirecionados para um novo servidor de licenciamento. Em alternativa, pode efetuar a migração do AD RMS para o Azure RMS. Para ativar o redirecionamento do licenciamento, utilize o seguinte procedimento.

#### <a name="to-enable-rms-licensing-redirection-by-using-the-windows-registry"></a>Para ativar o redirecionamento do licenciamento do RMS através do registo do Windows

1.  Abra o editor de registo do Windows, Regedit.exe.

2.  No Editor de Registo, navegue até um dos seguintes caminhos:

    -   Para a versão de 64 bits do Office numa plataforma x64: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   Para a versão de 32 bits do Office numa plataforma x64: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Para criar uma subchave LicensingRedirection, clique com o botão direito do rato em **Servicelocation**, aponte para **Novo**, clique em **Chave** e escreva **LicensingRedirection**.

4.  Para definir o redirecionamento do licenciamento, clique com o botão direito do rato na subchave **LicensingRedirection**, selecione **Novo** e selecione **Valor de cadeia**.  Para **Nome**, especifique o URL de licenciamento do servidor anterior e, para **Valor**, especifique o URL de licenciamento do servidor novo.

    Por exemplo, para redirecionar o licenciamento de um servidor em Contoso.com para outro em Fabrikam.com, poderá introduzir os seguintes valores:

    **Nome:** `https://contoso.com/_wmcs/licensing`

    **Valor:** `https://fabrikam.com/_wmcs/licensing`
    
    > [!NOTE]
    > Se o servidor de licenciamento antigo tiver URLs da intranet e extranet especificados, um novo nome e o mapeamento do valor tem de ser definidos para ambos os URLs na **LicensingRedirection** chave.

5.  Repita o passo anterior para todos os servidores que precisem de ser redirecionados.

6.  Feche o Editor de Registo.

