---
title: Implementar o scanner do Azure Information Protection (pré-visualização)
description: Instruções para instalar, configurar e executar a versão de pré-visualização atual do scanner do Azure Information Protection para detetar, classificar e proteger ficheiros em arquivos de dados.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 3856454d630dd0f287d8156a615946530e7c693e
ms.sourcegitcommit: 0bb53739867b3d07e44563cfae83f5c5f3d429e7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56302290"
---
# <a name="deploying-the-preview-version-of-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Implantar a versão de pré-visualização do scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2*

> [!NOTE]
> Este artigo é para a versão de pré-visualização atual do scanner do Azure Information Protection. Versões em pré-visualização estão sujeitos a alterações.
> 
> Para obter instruções de implementação para a versão de disponibilidade geral do scanner, consulte [Implantando o scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](deploy-aip-scanner.md).
> 
> Se estiver a atualizar de uma versão de disponibilidade geral do scanner de para a versão de pré-visualização, veja [atualizar o scanner do Azure Information Protection](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).

Utilize estas informações para saber mais sobre as versões de pré-visualização do scanner do Azure Information Protection e, em seguida, como instalar, configurar e executá-lo com êxito. 

Este scanner é executado como um serviço no Windows Server e permite-lhe Deteta, classifica e proteger ficheiros em arquivos de dados seguintes:

- Pastas locais no computador Windows Server que executa a deteção de impressão.

- Caminhos UNC para partilhas de rede que utilizam o protocolo de bloco de mensagem de servidor (SMB).

- Os sites e bibliotecas para o SharePoint Server 2016 e o SharePoint Server 2013. SharePoint 2010 também é suportada para os clientes que tenham [suporte para esta versão do SharePoint estendido](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).

Para analisar e ficheiros no repositório de nuvem da etiqueta, utilize [Cloud App Security](https://docs.microsoft.com/cloud-app-security/).

## <a name="overview-of-the-azure-information-protection-scanner"></a>Descrição geral do scanner do Azure Information Protection

Quando tiver configurado a sua [política do Azure Information Protection](configure-policy.md) para etiquetas que aplicam classificação automática, ficheiros que Deteta esta scanner, em seguida, podem ser rotulados. Etiquetas de aplicam a classificação e, opcionalmente, aplicarem a proteção ou removam a proteção:

![Proteção de informações scanner arquitetura descrição geral do Azure](./media/infoprotect-scanner.png)

O scanner pode inspecionar a todos os ficheiros que o Windows podem indexar, utilizando os IFilters que estão instalados no computador. Em seguida, para determinar se os arquivos precisam de etiquetagem, o scanner usa a tipos de informações de sensibilidade perda prevenção (DLP) do Office 365 dados internos e deteção de padrão ou padrões de regex do Office 365. Uma vez que o scanner utiliza o cliente do Azure Information Protection, pode classificar e proteger os mesmos [tipos de ficheiro](./rms-client/client-admin-guide-file-types.md).

Pode executar a deteção de impressão no modo de deteção apenas, em que usar os relatórios para verificar o que aconteceria se os ficheiros foram etiquetados. Em alternativa, pode executar a deteção de impressão para aplicar automaticamente as etiquetas. Também pode executar a deteção de impressão para detetar ficheiros que contenham tipos de informações confidenciais, sem configurar etiquetas para condições que se aplicam a classificação automática.

Tenha em atenção que o scanner não Deteta e etiqueta em tempo real. Sistematicamente rastreia o por meio de arquivos em arquivos de dados que especificar e pode configurar este ciclo para executar uma vez ou repetidamente.

Pode especificar que tipos de ficheiro de analisar ou excluir da análise, definindo uma lista de tipos de ficheiros como parte da configuração do scanner.


## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Pré-requisitos para o scanner do Azure Information Protection
Antes de instalar o scanner do Azure Information Protection, certifique-se de que os seguintes requisitos são cumpridos.

|Requisito|Mais informações|
|---------------|--------------------|
|Computador Windows Server para executar o serviço de scanner:<br /><br />-4 processadores de núcleo<br /><br />-8 GB de RAM<br /><br />-10 GB de espaço livre (média) para ficheiros temporários|Windows Server 2016 ou Windows Server 2012 R2. <br /><br />Nota: Para fins de teste ou avaliação num ambiente de não produção, pode usar um sistema de operativo de cliente Windows que está [suportados pelo cliente do Azure Information Protection](requirements.md#client-devices).<br /><br />Este computador pode ser um computador físico ou virtual que tenha uma ligação de rede rápida e fiável para os arquivos de dados deve ser verificado.<br /><br /> O scanner requer espaço em disco suficiente para criar ficheiros temporários para cada ficheiro que verifica a, quatro arquivos por núcleo. Permite que o espaço em disco recomendado de 10 GB para 4 processadores de núcleo de análise de 16 ficheiros que tenham, cada um tamanho de ficheiro de 625 MB. <br /><br />Se a conectividade com a Internet não é possível devido às políticas de sua organização, consulte a [Implantando o scanner com configurações alternativos](#deploying-the-scanner-with-alternative-configurations) secção. Caso contrário, certifique-se de que este computador tem conectividade de Internet que permite que os seguintes URLs:<br /> \*.aadrm.com <br /> \*.azurerms.com<br /> \*.informationprotection.azure.com <br /> informationprotection.hosting.portal.azure.net <br /> \*.aria.microsoft.com|
|SQL Server para armazenar a configuração de scanner:<br /><br />-Instância local ou remota<br /><br />-Função de administrador do sistema para instalar o scanner|SQL Server 2012 é a versão mínima para as seguintes edições:<br /><br />- SQL Server Enterprise<br /><br />-SQL Server Standard<br /><br />- SQL Server Express<br /><br />O scanner do Azure Information Protection suporta vários bancos de dados de configuração na mesma instância do SQL server quando especifica um nome de perfil personalizado para a deteção de impressão.<br /><br />Quando instala o scanner e a sua conta com a função de administrador do sistema, o processo de instalação automaticamente cria a base de dados de configuração de scanner e atribui a função db_owner necessária para a conta de serviço que executa a deteção de impressão. Se não é possível conceder a função de administrador do sistema ou as políticas de sua organização necessitam bases de dados a ser criado e configurado manualmente, consulte a [Implantando o scanner com configurações alternativos](#deploying-the-scanner-with-alternative-configurations) secção.<br /><br />O tamanho da base de dados de configuração irá variar para cada implementação, mas recomendamos que alocar o 500 MB para cada 1 000 000 ficheiros que pretende analisar. |
|Conta de serviço para executar o serviço de scanner|Além de executar o serviço de scanner, esta conta autentica para o Azure AD e transfere a política do Azure Information Protection. Esta conta tem de ser uma conta do Active Directory e sincronizado com o Azure AD. Se não é possível sincronizar esta conta devido às políticas de sua organização, consulte a [Implantando o scanner com configurações alternativos](#deploying-the-scanner-with-alternative-configurations) secção.<br /><br />Esta conta de serviço tem os seguintes requisitos:<br /><br />- **Iniciar sessão localmente** certo. Este direito é necessário para a instalação e configuração do scanner, mas não para a operação. Tem de conceder este direito para a conta de serviço, mas é possível remover este direito após a confirmação de que a deteção de impressão pode detetar, classificar e proteger ficheiros. Se conceder este direito até mesmo para um curto período de tempo não é possível devido às políticas de sua organização, consulte a [Implantando o scanner com configurações alternativos](#deploying-the-scanner-with-alternative-configurations) secção.<br /><br />- **Iniciar sessão como um serviço** certo. Este direito é concedido automaticamente para a conta de serviço durante a instalação de scanner e este direito é necessário para a instalação, configuração e operação do scanner. <br /><br />-Permissões para os repositórios de dados: Tem de conceder **leitura** e **escrever** permissões para verificar os ficheiros e, em seguida, a aplicar a classificação e proteção para os ficheiros que cumprem as condições na política do Azure Information Protection. Para executar a deteção de impressão no modo de deteção apenas **leitura** permissão é suficiente.<br /><br />-Para etiquetas que voltar a proteger ou remover a proteção: Para garantir que a deteção de impressão tem sempre acesso aos ficheiros protegidos, tornar esta conta uma [Superutilizador](configure-super-users.md) para o Azure Rights Management service e certifique-se de que a funcionalidade de Superutilizador é ativada. Para obter mais informações sobre os requisitos de conta para a aplicação de proteção, consulte [preparar utilizadores e grupos do Azure Information Protection](prepare.md). Além disso, se tiver implementado [controlos de inclusão](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) para uma implementação faseada, certifique-se de que esta conta está incluída na sua controlos de inclusão que configurou.|
|A versão de pré-visualização do cliente do Azure Information Protection está instalada no computador do servidor do Windows|Tem de instalar o cliente completo para a deteção de impressão. Não instale o cliente com apenas o módulo do PowerShell.<br /><br />Para obter instruções de instalação do cliente, consulte a [Guia do administrador](./rms-client/client-admin-guide.md). Se tiver instalado anteriormente o scanner e agora tem de atualizá-lo para uma versão posterior, veja [atualizar o scanner do Azure Information Protection](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).|
|Configurado etiquetas que aplicam a classificação automática e, opcionalmente, proteção|Para obter mais informações sobre como configurar uma etiqueta para condições de e para aplicar a proteção:<br /> - [Como configurar condições para classificação automática e recomendada](configure-policy-classification.md)<br /> - [Como configurar uma etiqueta para proteção do Rights Management](configure-policy-protection.md) <br /><br />Sugestão: Pode utilizar as instruções a partir da [tutorial](infoprotect-quick-start-tutorial.md) para testar o scanner com uma etiqueta que procura por números de cartão de crédito num documento do Word preparado. No entanto, terá de alterar a configuração de etiqueta, para que a opção **selecione a forma como esta etiqueta é aplicada** está definida como **automática**, em vez **recomendado**. Em seguida, remover a etiqueta do documento (se é aplicada) e copie o ficheiro para um repositório de dados para a deteção de impressão. Para um teste rápido, isso pode ser uma pasta local no computador do scanner.<br /><br /> Embora seja possível executar a deteção de impressão, mesmo que ainda não tiver configurado as etiquetas que aplicam classificação automática, este cenário não é abrangido com estas instruções. [Mais informações](#using-the-scanner-with-alternative-configurations)|
|Para sites do SharePoint e bibliotecas para ser analisado:<br /><br />- SharePoint 2016<br /><br />- SharePoint 2012<br /><br />- SharePoint 2010|Outras versões do SharePoint não são suportadas para a deteção de impressão.<br /><br />Para grandes farms do SharePoint, verifique se precisa de aumentar o limiar de vista de lista (por predefinição, 5.000) para o scanner aceder a todos os ficheiros. Para obter mais informações, consulte a seguinte documentação do SharePoint: [Gerir grandes listas e bibliotecas no SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server)|
|Para documentos do Office ser analisado:<br /><br />-formatos de arquivo 97-2003 e formatos XML abertos do Office para Word, Excel e PowerPoint|Para obter mais informações sobre os tipos de ficheiro que o suporta o scanner para estes formatos de ficheiros Consulte [tipos de ficheiro suportados pelo cliente do Azure Information Protection](./rms-client/client-admin-guide-file-types.md)|
|Para os caminhos longos:<br /><br />-Máximo de 260 carateres, a menos que o scanner é instalado no Windows 2016 e o computador está configurado para suportar os caminhos longos|Comprimentos de caminhos superiores a 260 carateres com o seguinte de suporte do Windows 10 e Windows Server 2016 [definição de política de grupo](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/): **Política de computador local** > **configuração do computador** > **modelos administrativos** > **todas as definições**  >  **NTFS** > **caminhos longos do Win32 ativar**<br /><br /> Para obter mais informações sobre o suporte de caminhos de ficheiro longos, consulte a [limitação de comprimento máximo do caminho](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) secção da documentação do desenvolvedor do Windows 10.

Se não é possível cumprir todos os requisitos na tabela porque eles são proibidos pelas suas diretivas da organização, consulte a secção seguinte para alternativas.

Se todos os requisitos são cumpridos, avance diretamente para [configurar a secção de scanner](#configure-the-scanner-in-the-azure-portal).

### <a name="deploying-the-scanner-with-alternative-configurations"></a>Implementar o scanner com configurações alternativos

Os pré-requisitos indicados na tabela são os requisitos de padrão para a deteção de impressão e recomendado porque eles são a configuração mais simples para a implementação do scanner. Eles devem ser adequados para teste inicial, para que pode verificar as capacidades do scanner. No entanto, num ambiente de produto, as políticas de sua organização podem proibir esses requisitos de predefinição devido a uma ou mais das seguintes restrições:

- Servidores não são permitidos a conectividade à Internet

- Não é possível conceder Sysadmin ou bases de dados tem de ser criados e configurados manualmente

- Contas de serviço não não possível conceder a **iniciar sessão localmente** certo

- Contas de serviço não podem ser sincronizadas para o Azure Active Directory, mas servidores têm conectividade com a Internet

O scanner pode acomodar essas restrições, mas que requerem configuração adicional.


#### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Restrição: O servidor de scanner não pode ter conectividade à Internet

Siga as instruções para uma [computadores desligados](./rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers). Em seguida, faça o seguinte:

1. Configure a deteção de impressão no portal do Azure, ao criar um perfil de scanner. Se precisar de ajuda com este passo, consulte [configurar a deteção de impressão no portal do Azure](#configure-the-scanner-in-the-azure-portal).

2. Exportar o seu perfil de scanner do **do Azure Information Protection – perfis (pré-visualização)** painel, utilizando o **exportar** opção.

3. Por fim, numa sessão do PowerShell, execute [Import-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration) e especifique o ficheiro que contém as definições exportadas.

Tenha em atenção que esta configuração, o scanner não é possível aplicar proteção (ou remover proteção), utilizando a chave de com base na cloud da sua organização. Em vez disso, o scanner é limitado a utilizar as etiquetas que aplicam apenas a classificação ou proteção que utiliza [HYOK](configure-adrms-restrictions.md). 

#### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Restrição: Não é possível conceder Sysadmin ou bases de dados tem de ser criados e configurados manualmente

Se pode ser concedida a função de administrador do sistema temporariamente para instalar o scanner, pode remover esta função quando a instalação de scanner estiver concluída. Quando utiliza esta configuração, a base de dados é criado automaticamente para e a conta de serviço para o scanner é concedida automaticamente as permissões necessárias. No entanto, a conta de utilizador que configura o scanner requer a função db_owner da base de dados de configuração de scanner e tem de conceder manualmente esta função para a conta de utilizador.

Se não é possível conceder a função de administrador do sistema até mesmo temporariamente, tem de criar manualmente uma base de dados antes de instalar o scanner. Quando utiliza esta configuração, atribua as seguintes funções:
    
|Conta|Função de nível de base de dados|
|--------------------------------|---------------------|
|Conta de serviço para a deteção de impressão|db_owner|
|Conta de utilizador para a instalação de scanner|db_owner|
|Conta de utilizador para configuração de scanner |db_owner|

Normalmente, irá utilizar a mesma conta de utilizador para instalar e configurar a deteção de impressão. Mas se utilizar contas diferentes, ambos requerem a função db_owner da base de dados de configuração do scanner:

- Se não especificar o nome de perfil para a deteção de impressão, a base de dados de configuração com o nome **AIPScanner_\<nome_do_computador >**. 

- Se especificar o nome do seu perfil, a base de dados de configuração com o nome **AIPScanner_\<Nome_do_perfil >**.

#### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>Restrição: A conta de serviço para a deteção de impressão não é possível conceder a **iniciar sessão localmente** certo

Se as políticas de organização proíbem o **iniciar sessão localmente** com o botão direito para contas de serviço, mas permite que o **iniciar sessão como uma tarefa do batch** certo, siga as instruções para [especificar e utilizar o Token o parâmetro de Set-AIPAuthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) no Guia do administrador.

#### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Restrição: A conta de serviço do scanner não pode ser sincronizada para o Azure Active Directory, mas o servidor tem conectividade à Internet

Pode ter uma conta para executar o serviço de scanner e utilizar outra conta para autenticar no Azure Active Directory:

- Para a conta de serviço do scanner, pode utilizar uma conta local do Windows ou uma conta do Active Directory.

- Para a conta do Azure Active Directory, siga as instruções para [especificar e utilize o parâmetro de Token para Set-AIPAuthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) no Guia do administrador.


## <a name="configure-the-scanner-in-the-azure-portal"></a>Configurar a deteção de impressão no portal do Azure

Antes de instalar o scanner, ou atualizá-lo a partir da versão de disponibilidade geral do scanner, crie um perfil para a deteção de impressão no portal do Azure. Configurar o perfil para definições de scanner e os repositórios de dados para análise.

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.
    
2. Localize a **Scanner** opções de menu e selecione **perfis (pré-visualização)**.
    
    Esta opção está ainda a implementar aos inquilinos para que se não vir listadas, é possível abrir o painel diretamente, usando a seguinte hiperligação: https://portal.azure.com/?ScannerConfiguration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade

3. Sobre o **do Azure Information Protection – perfis (pré-visualização)** painel, selecione **Add**:
    
    ![Adicionar perfil para o scanner do Azure Information Protection](./media/scanner-add-profile.png)

4. Sobre o **adicionar um novo perfil** painel, especifique um nome para a deteção de impressão que é utilizado para identificar os seus repositórios de dados e definições de configuração para analisar. Por exemplo, poderia especificar **Europa** para identificar a localização geográfica dos repositórios de dados que abrange o scanner. Quando instalar mais tarde ou Atualize o scanner, terá de especificar o mesmo nome de perfil.
    
    Opcionalmente, especifique uma descrição para fins administrativos, para ajudar a identificar o nome do perfil do leitor.

5. Para esta configuração inicial, configure as seguintes definições e, em seguida, selecione **guardar** , mas não feche o painel:
    
    - **Agenda**: Mantenha a predefinição de **Manual**
    - **Tipos de informações para que sejam detetados**: Alterar para **apenas política**
    - **Configurar repositórios**: Não configure neste momento porque o perfil tem primeiro de ser guardado.
    - **Enforce**: Selecione **desativado**
    - **Ficheiros com base no conteúdo da etiqueta**: Mantenha a predefinição de **no**
    - **Etiqueta predefinida**: Mantenha a predefinição de **predefinição da política**
    - **Relabel ficheiros**: Mantenha a predefinição de **desativado**
    - **Preservar a "Data de modificação", "Última modificação" e "Modificado por"**: Mantenha a predefinição de **no**
    - **Tipos de ficheiros a analisar**: Mantenha a predefinição de tipos de ficheiro para **excluir**
    - **Proprietário de predefinição**: Mantenha a predefinição de **conta de analista**

6. Agora que o perfil é criado e guardado, está pronto para retornar para o **configurar repositórios** opção para especificar os arquivos de dados deve ser verificado. Pode especificar pastas locais, caminhos UNC e URLs do servidor SharePoint para sites do SharePoint e bibliotecas. 
    
    SharePoint Server 2016 e o SharePoint Server 2013 são suportadas para o SharePoint. SharePoint Server 2010 também é suportado quando tiver [suporte para esta versão do SharePoint estendido](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).
    
    Para adicionar a sua primeira do arquivo de dados, ainda na **adicionar um novo perfil** painel, selecione **configurar repositórios** para abrir o **repositórios** painel:
    
    ![Configurar repositórios de dados para o scanner do Azure Information Protection](./media/scanner-repositories-bar.png)

7. Sobre o **repositórios** painel, selecione **Add**:
    
    ![Adicionar repositório de dados para o scanner do Azure Information Protection](./media/scanner-repository-add.png)

8. Sobre o **repositório** painel, especifique o caminho para o repositório de dados. 
    
    Carateres universais não são suportadas e localizações de WebDav não são suportadas.
    
    Exemplos:
    
    Para um caminho local: `C:\Folder`
    
    Para uma partilha de rede: `C:\Folder\Filename`
    
    Para um caminho UNC:`\\Server\Folder`
    
    Para uma biblioteca do SharePoint: `http://sharepoint.contoso.com/Shared%20Documents/Folder`
    
    > [!TIP]
    > Se adicionar um caminho de SharePoint para "Documentos compartilhados":
    >
     >- Especifique **documentos compartilhados** no caminho quando pretende analisar todos os documentos e todas as pastas de documentos compartilhados. Por exemplo: `http://sp2013/Shared Documents`
     >
     >- Especifique **documentos** no caminho quando pretende analisar todos os documentos e todas as pastas a partir de uma subpasta sob documentos compartilhados. Por exemplo: `http://sp2013/Documents/Sales Reports`
    
    Para as restantes definições neste painel, não alterá-los para esta configuração inicial, mas a mantê-los como **padrão de perfil**. Isso significa que o repositório de dados herda as definições do perfil de scanner. 
    
    Selecione **Guardar**.

9. Se pretender adicionar outro repositório de dados, repita os passos 7 e 8.

10. Agora, pode fechar o **adicionar um novo perfil** painel e ver o seu nome de perfil apresentado no **do Azure Information Protection – perfis (pré-visualização)** painel, juntamente com o **agenda** mostrando de coluna **Manual** e o **IMPOR** coluna está em branco.

Agora, está pronto para instalar o scanner com o perfil de scanner que acabou de criar.

## <a name="install-the-scanner"></a>Instalar o scanner

1. Inicie sessão no computador Windows Server que executará a deteção de impressão. Utilizar uma conta que tenha direitos de administrador local e que tenha permissões para escrever na base de dados mestra do SQL Server.

2. Abra uma sessão do Windows PowerShell com o **executar como administrador** opção.

3. Executar o [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) cmdlet, especificando sua instância do SQL Server em que pretende criar uma base de dados para o scanner do Azure Information Protection e o nome do perfil de scanner que especificou na secção anterior: 
    
    ```
    Install-AIPScanner -SqlServerInstance <name> -Profile <profile name>
    ```
    
    Exemplos, usando o nome de perfil do **Europa**:
    
    Para uma instância predefinida: `Install-AIPScanner -SqlServerInstance SQLSERVER1 -Profile Europe`
    
    Para uma instância nomeada: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER -Profile Europe`
    
    Para o SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS -Profile Europe`
    
    Quando lhe for pedido, forneça as credenciais para a conta de serviço do scanner (\<nome de domínio \ utilizador >) e palavra-passe.

4. Certifique-se de que o serviço está agora instalado usando **ferramentas administrativas** > **serviços**. 
    
    O serviço instalado com o nome **do Azure Information Protection Scanner** e está configurado para ser executado com a conta de serviço do scanner que criou.

Agora que instalou o scanner, terá de obter um Azure AD token para a conta de serviço do scanner autenticar, para que a deteção de impressão pode executá-lo automaticamente. 

## <a name="get-an-azure-ad-token-for-the-scanner"></a>Obter um Azure AD token para a deteção de impressão

O token do Azure AD permite que a conta de serviço do scanner autenticar para o serviço Azure Information Protection.

1. Regresse ao portal do Azure para criar duas aplicações do Azure AD que são necessários para especificar um token de acesso para a autenticação. Após um inicial interativo início de sessão, este token permite o scanner executar de forma não interativa.
    
    Para criar esses aplicativos, siga as instruções em [como Etiquetar ficheiros de forma não interativa para o Azure Information Protection](./rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) no Guia do administrador.

2. Do computador Windows Server, se a sua conta de serviço do scanner recebeu o **iniciar sessão localmente** diretamente para a instalação: Inicie sessão com esta conta e iniciar uma sessão do PowerShell. Execute [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), especificar os valores que copiou no passo anterior:
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application> -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application>
    ```
    
    Quando lhe for pedido, especifique a palavra-passe para as credenciais da conta de serviço para o Azure AD e, em seguida, clique em **Accept**.
    
    Se a sua conta de serviço do scanner não é possível conceder a **iniciar sessão localmente** diretamente para a instalação: Siga as instruções no [especificar e utilize o parâmetro de Token para Set-AIPAuthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) secção no Guia do administrador. 

O scanner agora tem um token para autenticar para o Azure AD, que é válido durante um ano, dois anos, ou nunca expira, de acordo com a configuração da a **aplicação Web/API** no Azure AD. Quando o token expira, terá de repetir os passos 1 e 2.

Agora, está pronto para executar a sua primeira análise no modo de deteção.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>Executar um ciclo de deteção e ver relatórios para a deteção de impressão

1. No portal do Azure, retornar para o Azure Information Protection para iniciar o scanner. Partir do **Scanner** opção de menu, selecione **nós**. Selecione o nó de scanner e, em seguida, o **analisar agora** opção:
    
    ![Iniciar verificação para o scanner do Azure Information Protection](./media/scanner-scan-now.png)
    
    Em alternativa, na sessão do PowerShell, execute o seguinte comando:
    
        Start-AIPScan

2. Aguarde que o scanner concluir o seu ciclo. Quando a deteção de impressão tem rastreadas por meio de todos os arquivos nos arquivos de dados que especificou, o scanner para apesar do serviço de scanner permanece em execução:
    
    - Do **do Azure Information Protection – nós** painel, o valor para o **estado** coluna é alterado de **digitalização** para **Idle**.
    
    - Com o PowerShell, pode executar `Get-AIPScannerStatus` para monitorizar a alteração de estado.
    
    - Verifique o Windows local **aplicativos e serviços** registo de eventos **do Azure Information Protection**. Este registo também relata quando o scanner concluir a verificação, com um resumo dos resultados. Procure o ID de evento informativo **911**.

3. Rever os relatórios que são armazenados em %*localappdata*% \Microsoft\MSIP\Scanner\Reports. Os ficheiros de resumo. txt incluem o tempo necessário para analisar, o número de ficheiros e o número de ficheiros tinha uma correspondência para os tipos de informações. Os ficheiros. csv tem de obter mais detalhes para cada ficheiro. Esta pasta armazena até 60 relatórios para cada ciclo de análise e todos, mas o relatório mais recente é compactado para ajudar a minimizar o espaço em disco necessário.
    
    > [!NOTE]
    > Pode alterar o nível de registo utilizando o *ReportLevel* parâmetro com [conjunto AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration), mas não é possível alterar a localização da pasta de relatório ou o nome. Considere utilizar uma junção de diretório para a pasta se pretende armazenar os relatórios num volume diferente ou partição.
    >
    > Por exemplo, utilizando o [Mklink](/windows-server/administration/windows-commands/mklink) comando: `mklink /j D:\Scanner_reports C:\Users\aipscannersvc\AppData\Local\Microsoft\MSIP\Scanner\Reports`
    
    Com nossa definição de **apenas política** para **tipos de informações para que sejam detetados**, apenas ficheiros que cumprem as condições que configurou para a classificação automática estão incluídos nos relatórios detalhados. Se não vir quaisquer etiquetas aplicadas, verifique a configuração de etiqueta incluir automática em vez de classificação recomendada.
    
    > [!TIP]
    > Scanners de enviam estas informações para o Azure Information Protection a cada cinco minutos, para que possa visualizar os resultados em tempo quase real do portal do Azure. Para obter mais informações, consulte [de relatórios do Azure Information Protection](reports-aip.md). 
        
    Se os resultados são não conforme o esperado, poderá ter de reconfigurar as condições que especificou para que as etiquetas na sua política do Azure Information Protection. Se for esse o caso, repita os passos 1 a 3 até estar pronto para alterar a configuração para aplicar a classificação e, opcionalmente, a proteção. 

Quando estiver pronto para etiquetar automaticamente os ficheiros que Deteta o scanner, avance para o procedimento seguinte. 

## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>Configurar a deteção de impressão para aplicar a classificação e proteção

Se estiver a seguir estas instruções, o scanner executa um tempo e no modo só de relatórios. Para alterar estas definições, edite o perfil de scanner:

1. Volta a **[do Azure Information Protection – perfis (pré-visualização)](https://portal.azure.com/?ScannerConfiguration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade)** painel, selecione o perfil de scanner editá-lo.

2. Sobre o \< **nome do perfil**> painel, altere as duas definições seguintes e, em seguida, selecione **guardar**:
    
   - **Agenda**: Alterar para **sempre**
   - **Enforce**: Selecione **no**
    
     Existem outras definições de configuração que talvez queira alterar. Por exemplo, se os atributos de ficheiro são alterados e se o scanner pode relabel os ficheiros. Utilize a ajuda de pop-up de informações para saber mais informações sobre cada definição de configuração.

3. Tome nota do tempo atual e iniciar o scanner novamente a partir da **do Azure Information Protection – nós** painel:
    
    ![Iniciar verificação para o scanner do Azure Information Protection](./media/scanner-scan-now.png)
    
    Em alternativa, pode executar o seguinte comando na sua sessão do PowerShell:
    
        Start-AIPScan

4. Monitorizar o registo de eventos para o tipo de informativo **911** novamente, com um tempo de carimbo posterior quando iniciou a análise no passo anterior. 
    
    Em seguida, verifique os relatórios para ver os detalhes de quais arquivos foram etiquetados, classificação de que foi aplicada a cada ficheiro e, se a proteção foi aplicada aos mesmos. Em alternativa, utilize o portal do Azure para ver mais facilmente essas informações.

Uma vez que configurámos a agenda para ser executada continuamente, quando o scanner trilhou seu caminho através de todos os ficheiros, começa automaticamente um novo ciclo, para que todos os ficheiros novos e alterados são detetados.


## <a name="how-files-are-scanned"></a>Como os ficheiros são analisados

O scanner percorre os seguintes processos quando ele analisa os ficheiros.

### <a name="1-determine-whether-files-are-included-or-excluded-for-scanning"></a>1. Determinar se os ficheiros são incluídos ou excluídos para verificação 
O scanner ignora automaticamente ficheiros que estão [excluídos da classificação e proteção](./rms-client/client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection), como arquivos executáveis e arquivos do sistema.

Pode alterar este comportamento ao definir uma lista dos tipos de ficheiro de analisar ou excluir da análise. Pode especificar esta lista para a deteção de impressão aplicar a todos os repositórios de dados, por padrão, e pode especificar uma lista de cada repositório de dados. Para especificar esta lista, utilize o **tipos para analisar os ficheiros** definição no perfil de scanner:

![Configurar tipos de ficheiros para procurar o scanner do Azure Information Protection](./media/scanner-file-types.png)

### <a name="2-inspect-and-label-files"></a>2. Inspecione e etiquetar ficheiros

O scanner, em seguida, utiliza filtros para analisar os tipos de ficheiro suportados. Estes filtros mesmo são utilizados pelo sistema operativo para o Windows Search e a indexação. Sem qualquer configuração adicional, o Windows IFilter é utilizado para analisar os tipos de ficheiro que são utilizados pelo Word, Excel, PowerPoint e para documentos PDF e arquivos de texto.

Para obter uma lista completa dos tipos de ficheiros que são suportadas por padrão e informações adicionais como para configurar os filtros existentes que incluem ficheiros. zip e ficheiros. TIFF, consulte [tipos de ficheiro suportados para inspeção](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-inspection).

Após a inspeção, estes tipos de ficheiro podem ser rotulados utilizando as condições que especificou para as etiquetas. Em alternativa, se estiver a utilizar o modo de deteção, estes ficheiros podem ser comunicados para conter as condições que especificou para as etiquetas ou todos os tipos conhecidos de informações confidenciais. 

No entanto, o scanner não é possível etiquetar os ficheiros nas seguintes circunstâncias:

- Se aplica-se a etiqueta de classificação e proteção não e o tipo de ficheiro não existir [suportará a classificação apenas](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only).

- Se aplica-se a etiqueta de classificação e proteção, mas o scanner não protege o tipo de ficheiro.
    
    Por predefinição, o scanner protege apenas os tipos de ficheiro do Office e os ficheiros PDF que estejam protegidos utilizando a norma ISO para a encriptação de PDF. Outros tipos de ficheiro podem ser protegido quando [editar o registo](#editing-the-registry-for-the-scanner) conforme descrito na seção a seguir.

Por exemplo, depois de inspecionar ficheiros que tenham uma extensão de nome de ficheiro de. txt, o scanner não é possível aplicar uma etiqueta que está configurada para classificação, mas não a proteção, porque o tipo de ficheiro. txt não suporta apenas a classificação. Se a etiqueta é configurada para classificação e proteção, e o Registro é editado para o tipo de ficheiro. txt, o scanner pode Etiquetar o ficheiro. 

> [!TIP]
> Durante este processo, se o scanner interrompe e não concluir a verificação de um grande número de ficheiros num repositório:
> 
> - Poderá ter de aumentar o número de portas dinâmicas para o sistema operativo que aloja os ficheiros. Sistema de proteção do servidor para o SharePoint pode ser um dos motivos por que o scanner excede o número de ligações de rede permitidos e, portanto, deixa.
>     
>     Para verificar se esta é a causa do scanner a parar, dê uma olhada para ver se a seguinte mensagem de erro é registada para a deteção de impressão em %*localappdata*%\Microsoft\MSIP\Logs\MSIPScanner.iplog (comprimido se existirem vários registos): **Não é possível ligar ao servidor remoto---> System.Net.Sockets.SocketException: Utilização de apenas um de cada endereço de soquete (endereço de rede/protocolo/porta) normalmente é permitida IP: porta**
>    
>     Para obter mais informações sobre como visualizar o intervalo de portas atual e aumentar o leque de mensagens em fila, consulte [as definições que podem ser modificadas para melhorar o desempenho de rede](https://docs.microsoft.com/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).
> 
> - Para grandes farms do SharePoint, poderá ter de aumentar o limiar de vista de lista (por predefinição, 5.000). Para obter mais informações, consulte a seguinte documentação do SharePoint: [Gerir grandes listas e bibliotecas no SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).

### <a name="3-label-files-that-cant-be-inspected"></a>3. Ficheiros de etiqueta que não não possível inspecioná-lo
Para os tipos de ficheiro que não não possível inspecioná-lo, o scanner aplica-se a etiqueta predefinida na política do Azure Information Protection ou a etiqueta predefinida que configurou para a deteção de impressão.

Como no passo anterior, o scanner não é possível etiquetar os ficheiros nas seguintes circunstâncias:

- Se aplica-se a etiqueta de classificação e proteção não e o tipo de ficheiro não existir [suportará a classificação apenas](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only).

- Se aplica-se a etiqueta de classificação e proteção, mas o scanner não protege o tipo de ficheiro.
    
    Por predefinição, o scanner protege apenas os tipos de ficheiro do Office e os ficheiros PDF que estejam protegidos utilizando a norma ISO para a encriptação de PDF. Outros tipos de ficheiro podem ser protegido quando [editar o registo](#editing-the-registry-for-the-scanner) conforme descrito a seguir.


### <a name="editing-the-registry-for-the-scanner"></a>Editar o registo para a deteção de impressão

Para alterar o comportamento de scanner de padrão para proteger os tipos de ficheiro diferentes arquivos do Office e de PDFs, tem de editar o registo e especificar os tipos de ficheiro adicionais que pretende proteger e o tipo de proteção (nativo ou genérico) manualmente. Para obter instruções, consulte [configuração da API de ficheiros](develop/file-api-configuration.md) de orientação para programadores. Nesta documentação para programadores, a proteção genérica é referida como "PFile". Além disso, específico para a deteção de impressão:

- O scanner tem seu próprio comportamento padrão: Apenas os formatos de arquivo do Office e os documentos PDF protegidos por padrão. Se o registo não for modificado, outros tipos de ficheiro não serão etiquetados ou protegidos pelo leitor.

- Se pretender que o mesmo comportamento de proteção de predefinição do cliente do Azure Information Protection, onde todos os ficheiros são automaticamente protegidos com a proteção nativa ou genérica: Especifique a `*` universais como uma chave de registo e `Default` como os dados do valor.

Ao editar o registro, criar manualmente a **MSIPC** chave e **FileProtection** chave se não existirem, bem como uma chave para cada extensão de nome de ficheiro.

Por exemplo, para a deteção de impressão proteger as imagens TIFF, além de ficheiros do Office e de PDFs, o registo após editou-lo, terá um aspeto semelhante à imagem seguinte. Como um ficheiro de imagem, ficheiros TIFF suportam a proteção nativa e a extensão de nome de ficheiro resultante,. ptiff.

![Editar o registo para o scanner aplicar a proteção](./media/editregistry-scanner.png)

Para obter uma lista de texto e imagens de tipos de ficheiro que da mesma forma suportam a proteção nativa, mas tem de ser especificado no registo, consulte [tipos de ficheiros suportados para classificação e proteção](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection) no Guia do administrador.

Para ficheiros que não suportam a proteção nativa, especifique a extensão de nome de ficheiro, como uma nova chave, e **PFile** para proteção genérica. A extensão de nome de ficheiro resultante para o ficheiro protegido é. pfile.


## <a name="when-files-are-rescanned"></a>Quando ficheiros estão a ser reanalisados

Para o primeiro ciclo de análise, o scanner inspeciona todos os ficheiros nos arquivos de dados configurada e, em seguida, para análises subsequentes, apenas novos ou modificados arquivos são inspecionados. 

Pode forçar a deteção de impressão para inspecionar todos os ficheiros novamente a partir da **do Azure Information Protection – nós** painel no portal do Azure. Selecione o scanner da lista e, em seguida, selecione o **reanalisar todos os ficheiros** opção:

![Iniciar a reanálise para o scanner do Azure Information Protection](./media/scanner-rescan-files.png)

Inspecionar todos os ficheiros novamente é útil quando pretende que os relatórios para incluir todos os ficheiros e esta opção de configuração é normalmente utilizada quando o scanner é executado no modo de deteção. Quando uma análise completa estiver concluída, o tipo de análise muda automaticamente para incremental, de modo que para análises subsequentes, os ficheiros novos ou modificados só são analisados.

Além disso, todos os arquivos são inspecionados quando o scanner transfere uma política do Azure Information Protection que tem condições novas ou alteradas. O scanner é atualizada a política para cada hora, e quando é iniciado o serviço e a política é mais antigo do que uma hora.  

> [!TIP]
> Se precisar de atualizar a política mais cedo do que este intervalo de uma hora, por exemplo, durante um período de teste: Elimine manualmente o ficheiro de política **msip** tanto **%LocalAppData%\Microsoft\MSIP\Policy.msip** e **%LocalAppData%\Microsoft\MSIP\Scanner**. Em seguida, reinicie o serviço de Scanner de informações do Azure.
> 
> Se tiver alterado as definições de proteção na política, aguarde também a 15 minutos de quando guardar as definições de proteção antes de reiniciar o serviço.

Se o scanner transferido uma política que não tinha nenhuma condição automática configurada, a cópia do ficheiro de política na pasta scanner não é atualizada. Neste cenário, tem de eliminar o ficheiro de política **msip** tanto **%LocalAppData%\Microsoft\MSIP\Policy.msip** e **%LocalAppData%\Microsoft\MSIP\Scanner**antes do scanner pode utilizar um ficheiro de política recentemente transferida com etiquetas corretamente imaginei condições automática.

## <a name="editing-in-bulk-for-the-data-repository-settings"></a>Editar em massa para as definições de repositório de dados

Para os repositórios de dados que já foi adicionado a um perfil de scanner, pode utilizar o **exportar** e **importação** opções para fazer rapidamente as alterações às definições. Por exemplo, para os repositórios de dados do SharePoint, que pretende adicionar um novo tipo de ficheiro a excluir da análise.

Em vez de editar cada repositório de dados no portal do Azure, utilize o **exportar** opção a partir do **repositórios** painel:

![Exportar definições de repositório de dados para a deteção de impressão](./media/export-scanner-repositories.png)

Editar manualmente o ficheiro para fazer a alteração e, em seguida, utilize o **importação** opção no painel do mesmo.

## <a name="using-the-scanner-with-alternative-configurations"></a>Utilizar o Verificador de com configurações alternativas

Existem dois cenários alternativos que o scanner do Azure Information Protection suporta onde as etiquetas não precisa de ser configurado para todas as condições: 

- Aplicam-se uma etiqueta predefinida para todos os arquivos num repositório de dados.
    
    Para esta configuração, defina o **etiqueta predefinida** ao **personalizado**e selecione a etiqueta a utilizar.
    
    O conteúdo dos ficheiros não é inspecionado e todos os ficheiros no repositório de dados são o nome, de acordo com a etiqueta predefinida que especificou para o repositório de dados ou o perfil de scanner.
    

- Identifique todas as condições personalizadas e tipos de informações confidenciais conhecidos.
    
    Para esta configuração, defina o **tipos de informações para que sejam detetados** ao **todos os**.
    
    O scanner utiliza quaisquer condições personalizadas que tenha especificado para as etiquetas na política do Azure Information Protection e a lista de tipos de informações que estão disponíveis para especificar para etiquetas na política do Azure Information Protection. Esta definição ajuda a localizar informações confidenciais que não pode ter apercebido tinha, mas às custas de análise de taxas para a deteção de impressão.
    
    Início rápido seguinte para a versão de disponibilidade geral do scanner de utiliza esta configuração: [Início rápido: Encontrar as informações confidenciais que tiver](quickstart-findsensitiveinfo.md).

## <a name="optimizing-the-performance-of-the-scanner"></a>Otimizar o desempenho do scanner

Para maximizar o desempenho de scanner:

- **Ter uma alta velocidade e a conexão de rede confiável entre o computador de scanner e o arquivo de dados digitalizados**
    
    Por exemplo, colocar o computador do scanner no mesmo LAN ou (preferencial) no mesmo segmento de rede como o arquivo de dados digitalizados.
    
    A qualidade da ligação de rede afeta o desempenho de scanner porque para inspecionar os ficheiros, o scanner transfere o conteúdo dos ficheiros para o computador que executa o serviço de scanner. Quando reduzir (ou eliminar) o número de saltos de rede que tem destes dados de viagens, também reduzir a carga na sua rede. 

- **Certifique-se de que o computador de scanner possui recursos de processador disponíveis**
    
    Inspecionar os conteúdos do ficheiro e encriptar e desencriptar ficheiros são ações de uso intenso do processador. Monitor típico de análise de ciclos para os arquivos de dados especificado para identificar se a falta de recursos do processador é afetar negativamente o desempenho do scanner.
    
- **Não verificar pastas locais no computador que executa o serviço de scanner**
    
    Se tiver pastas para verificar num servidor Windows, instale o scanner num computador diferente e configurar essas pastas como compartilhamentos para análise de rede. Separar as duas funções de que alojem ficheiros e análise de ficheiros, significa que os recursos de computação para estes serviços não estejam competindo entre si.

Se necessário, instale várias instâncias do scanner. O scanner do Azure Information Protection suporta vários bancos de dados de configuração na mesma instância do SQL server quando especifica um nome de perfil personalizado para a deteção de impressão.

Outros fatores que afetam o desempenho de scanner:

- A carga atual e os tempos de resposta de arquivos de dados que contêm os ficheiros para analisar

- Se o scanner é executado no modo de deteção ou modo de imposição
    
    Modo de deteção, normalmente tem um maior impor a taxa de verificação que o modo de imposição, como deteção requer um único arquivo ler ação, ao passo que necessita de modo de leitura e escrita de ações.

- Alterar as condições no Azure Information Protection
    
    O primeiro ciclo de análise quando o scanner deve inspecionar cada ficheiro irá demorar mais de ciclos de análise subsequentes que, por predefinição, inspecionar os ficheiros apenas novos e alterados. No entanto, se alterar as condições na política do Azure Information Protection, todos os ficheiros são analisados mais uma vez, conforme descrito no [secção anterior](#when-files-are-rescanned).

- O nível de registo escolhido
    
    Pode escolher entre **depurar**, **informações**, **erro** e **desativar** para os relatórios de scanner. **Desativar** resulta em melhor desempenho; **Depurar** consideravelmente mais lento o scanner e deve ser usado apenas para resolução de problemas. Para obter mais informações, consulte a *ReportLevel* parâmetro para o [conjunto AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) cmdlet.

- Os próprios arquivos:
    
    - Ficheiros do Office são mais rapidamente digitalizados que ficheiros PDF.
    
    - Ficheiros desprotegidos são mais rápidos de análise de ficheiros protegidos.
    
    - Ficheiros grandes, obviamente, demoram mais tempo a análise de ficheiros pequenos.

- Além disso,
    
    - Confirme que a conta de serviço que executa a deteção de impressão tem apenas os direitos documentados no [pré-requisitos do scanner](#prerequisites-for-the-azure-information-protection-scanner) secção e, em seguida, configure a [propriedade de cliente avançada](./rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) para desativar a baixa nível de integridade para a deteção de impressão.
    
    - O scanner é executado mais rapidamente ao utilizar o [configuração alternativa](#using-the-scanner-with-alternative-configurations) para aplicar uma etiqueta predefinida para todos os ficheiros porque o scanner não inspeciona o conteúdo do ficheiro.
    
    - O scanner é executado mais lentamente quando utiliza a [configuração alternativa](#using-the-scanner-with-alternative-configurations) para identificar todas as condições personalizadas e tipos de informações confidenciais conhecidos.
    

## <a name="list-of-cmdlets-for-the-scanner"></a>Lista de cmdlets para a deteção de impressão

Porque agora configurar o scanner do portal do Azure, os cmdlets de versões anteriores que configurado repositórios de dados e a lista de tipos de ficheiro digitalizados estão agora preteridos. 

Os cmdlets que permanecem incluem cmdlets que instalar e atualizar o scanner, alterar a base de dados de configuração de scanner e o perfil, alterar o nível de geração de relatórios local e importar definições de configuração para um computador desconectado. 

A lista completa de cmdlets que a versão de pré-visualização do scanner de suporte: 

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)

- [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner)


## <a name="event-log-ids-and-descriptions-for-the-scanner"></a>IDs de registo de eventos e descrições para a deteção de impressão

Utilize as secções seguintes para identificar os IDs de eventos possíveis e descrições para a deteção de impressão. Estes eventos são registados no servidor que executa o serviço de scanner, em que o Windows **aplicativos e serviços** registo de eventos **do Azure Information Protection**.

-----

Informações **910**

**Ciclo de scanner iniciado.**

Este evento é registado quando o serviço de scanner é iniciado e começa a procurar ficheiros nos repositórios de dados que especificou.

----

Informações **911**

**Ciclo de scanner foi concluída.**

Este evento é registado quando o scanner foi concluída uma análise manual ou o scanner concluir um ciclo numa base contínua.

Se o scanner foi configurado para executar manualmente em vez de forma contínua, para analisar os ficheiros mais uma vez, defina o **agenda** ao **Manual** ou **sempre** no perfil de scanner e, em seguida, Reinicie o serviço.

----

## <a name="next-steps"></a>Passos Seguintes

Interessado em como a equipe principal Services engenharia e operações no Microsoft implementado este scanner?  Leia o caso prático técnico: [Automatizar a proteção de dados com o scanner do Azure Information Protection](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

Deve estar pensando: [O que é a diferença entre a FCI do Windows Server e o scanner do Azure Information Protection?](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

Também pode utilizar o PowerShell para classificar e proteger ficheiros a partir de seu computador desktop de interativamente. Para obter mais informações sobre este e outros cenários que utilizam o PowerShell, consulte [utilizar o PowerShell com o cliente do Azure Information Protection](./rms-client/client-admin-guide-powershell.md).


