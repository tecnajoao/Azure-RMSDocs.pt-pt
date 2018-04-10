---
title: Migrar do AD RMS para o Azure Information Protection – fase 3
description: Fase 3 da migração do AD RMS para o Azure Information Protection, que abrange o passo 7 de Migrar do AD RMS para o Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e5e1f0fa043a0a15ef34c9e4d5690e974cf6bddd
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="migration-phase-3---client-side-configuration"></a>Fase 3 da migração – configuração do lado do cliente

>*Aplica-se a: serviços de gestão de direitos do Active Directory [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize as seguintes informações para a Fase 3 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem o passo 7 de [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>Passo 7: Reconfigure os computadores com o Windows para utilizar o Azure Information Protection

Para computadores com Windows que utilizam aplicações de ambiente de trabalho do Office 2016 clique para execução:

- Pode reconfigurar a estes clientes para utilizarem o Azure Information Protection utilizando o redirecionamento de DNS. Este é o método preferencial de migração de cliente, porque é o mais simples. No entanto, este método está restrito a aplicações de ambiente de trabalho clique para execução do Office 2016 (ou posterior) para computadores Windows.
    
    Este método requer a criação de um novo SRV registar e conjunto um NTFS neguem a permissão para os utilizadores no ponto final publicação AD RMS.

- Para computadores com Windows que não utilizam o Office 2016 clique para execução:
    
    Não é possível utilizar o redirecionamento de DNS e, em vez disso, tem de utilizar as edições de registo. Se tiver uma mistura de Office 2016 e outras versões do Office, pode utilizar este método único para todos os computadores Windows ou uma combinação de redirecionamento de DNS e editar o registo. 
    
    As alterações de registo que são efetuadas mais fácil para si, editar e implementação de scripts que pode transferir. 

Consulte as secções seguintes para obter mais informações sobre como reconfigurar clientes do Windows.

## <a name="client-reconfiguration-by-using-dns-redirection"></a>Reconfiguração de cliente através da utilização de redirecionamento de DNS

Este método é adequado apenas para clientes do Windows que executem aplicações de ambiente de trabalho do Office 2016 (ou posterior) clique para execução. 

1. Crie um registo SRV de DNS com o seguinte formato:
    
    `_rmsredir._http._tcp.<AD RMS cluster>. <TTL> IN SRV <priority> <weight> <port> <your tenant URL>.`
    
    Para  *\<cluster AD RMS >*, especifique o FQDN do cluster do AD RMS. Por exemplo, **rmscluster.contoso.com**.
    
    Em alternativa, se tiver apenas um cluster de AD RMS no domínio, pode especificar apenas o nome de domínio do cluster do AD RMS. No nosso exemplo, que seria **contoso.com**. Quando especificar o nome de domínio neste registo, o redirecionamento é aplicada a todos os clusters de AD RMS nesse domínio.
    
    O  *\<porta >* número será ignorado.
    
    Para  *\<o seu URL de inquilino\>*, especificar a sua própria [URL do serviço Azure Rights Management para o seu inquilino](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).
    
    Se utilizar a função de servidor DNS no Windows Server, pode utilizar a tabela seguinte como exemplo como especificar as propriedades de registo SRV na consola do Gestor de DNS.
    
    |Campo|Valor|  
    |-----------|-----------|  
    |**Domínio**|_tcp.rmscluster.contoso.com|  
    |**Serviço**|_rmsredir|  
    |**Protocol**|_http|  
    |**prioridade**|0|  
    |**Weight**|0|  
    |**Número de porta**|80|  
    |**Anfitrião que oferece este serviço**|5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com|  

2. Defina uma permissão recusar para os utilizadores do Office 2016 no ponto final publicação AD RMS:

    a. Dos seus servidores do AD RMS no cluster, inicie a consola do Gestor de serviços de informação Internet (IIS).

    b. Navegue para **Web Site predefinido** > **wmcs** > **licenciamento** > **publish.asmx**

    c. Clique com botão direito **publish.asmx** > **propriedades** > **editar**

    d. No **permissões para publish.asmx** caixa de diálogo, selecione **utilizadores** se pretende definir o redirecionamento para todos os utilizadores ou clique em **adicionar** e, em seguida, especifique um grupo que contenha os utilizadores que pretende redirecionar.
    
    Mesmo se todos os seus utilizadores estão a utilizar o Office 2016, poderá preferir inicialmente especificar um subconjunto de utilizadores para uma migração faseada.
    
    e. Para o grupo selecionado, selecione **negar** para o **leitura & executar** e **leitura** permissão e, em seguida, clique em **OK** duas vezes.

    f. Para confirmar que esta configuração está a funcionar conforme esperado, tente estabelecer ligação com o ficheiro publish.asmx diretamente a partir de um browser. Deverá ver a seguinte mensagem de erro, o que aciona o cliente com o Office 2016 para procurar o registo SRV:
    
    **Mensagem de erro 401.3: não tem permissões para visualizar este diretório ou página com as credenciais fornecidas (acesso negado devido a listas de controlo de acesso).**


## <a name="client-reconfiguration-by-using-registry-edits"></a>Reconfiguração de clientes com edições de registo

Este método é adequado para todos os clientes Windows e deve ser utilizado se não executar o Office 2016, mas uma versão anterior. Este método utiliza dois scripts de migração para reconfigurar clientes de AD RMS:

- Migrate-Client.cmd

- Migrate-User.cmd

O script de configuração de cliente (migrar Client.cmd) configura as definições de nível de computador no registo, o que significa que tem de ser executada no contexto de segurança que pode efetuar essas alterações. Isto significa habitualmente um dos seguintes métodos:

- Utilize a política de grupo para executar o script como um script de arranque do computador.

- Utilize a instalação de software de política de grupo para atribuir o script para o computador.

- Utilize uma solução de implementação de software para implementar o script para os computadores. Por exemplo, utilizar o System Center Configuration Manager [pacotes e programas](/sccm/apps/deploy-use/packages-and-programs). Nas propriedades do pacote e programa, em **modo de execução**, especifique que o script é executado com permissões administrativas no dispositivo. 

- Utilize um script de início de sessão se o utilizador possui privilégios de administrador local.

O script de configuração de utilizador (migrar User.cmd) configura as definições de nível de utilizador e limpa o arquivo de licença de cliente. Isto significa que este script tem de executar no contexto do utilizador real. Por exemplo:

- Utilize um script de início de sessão.

- Utilize a instalação de software de política de grupo para publicar o script para o utilizador executar.

- Utilize uma solução de implementação de software para implementar o script para os utilizadores. Por exemplo, utilizar o System Center Configuration Manager [pacotes e programas](/sccm/apps/deploy-use/packages-and-programs). Nas propriedades do pacote e programa, em **modo de execução**, especifique que o script é executado com as permissões do utilizador. 

- Pedir ao utilizador para executar o script quando iniciar a sessão aos respetivos computadores.

Os dois scripts incluem um número de versão e não volte a executar até que este número de versão é alterado. Isto significa que pode deixar os scripts em vigor até que a migração estar concluída. No entanto, se efetuar alterações para os scripts de que pretende que sejam computadores e utilizadores a voltar a executar nos respetivos computadores Windows, atualize a seguinte linha em ambos os scripts para um valor superior:

    SET Version=20170427

O script de configuração do utilizador foi concebido para ser executada após o script de configuração de cliente e utiliza o número de versão nesta verificação. Interrompe se não tiver executado o script de configuração de cliente com a mesma versão. Esta verificação garante que os dois scripts executadas na sequência correta. 

Quando não é possível migrar todos os seus clientes do Windows de uma só vez, execute os seguintes procedimentos para lotes de clientes. Para cada utilizador com um computador Windows que pretende migrar no seu lote, adicione o utilizador ao grupo **AIPMigrated** que criou anteriormente.

### <a name="modifying-the-scripts-for-registry-edits"></a>Modificar os scripts para edições de registo

1. Regressar para os scripts de migração, **migrar Client.cmd** e **migrar User.cmd**, que anteriormente extraiu quando tiver transferido estes scripts no [fase de preparação](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration).

2.  Siga as instruções em **migrar Client.cmd** para modificar o script para que este contém o URL do serviço do seu inquilino do Azure Rights Management e também os nomes de servidor para o AD RMS cluster URL de licenciamento de extranet e da intranet URL de licenciamento. Em seguida, aumentar a versão do script, que foi explicada anteriormente. É uma boa prática para controlar as versões de script para utilizar a data de hoje no seguinte formato: AAAAMMDD
    
    > [!IMPORTANT]
    > Tal como anteriormente, tenha cuidado para não introduzir espaços adicionais antes ou depois dos seus endereços.
    > 
    > Além disso, se os seus servidores do AD RMS utilizarem certificados de servidor SSL/TLS, verifique se os valores de URL de licenciamento incluem o número de porta **443** na cadeia. Por exemplo: https:// rms.treyresearch.net:443/_wmcs/licensing. Pode encontrar estas informações na consola de serviços de gestão de direitos do Active Directory quando clicar no nome do cluster e ver o **os detalhes do Cluster** informações. Se vir o número de porta 443 incluído no URL, inclua este valor quando modificar o script. Por exemplo, https://rms.treyresearch.net:**443**. 
    
    Se precisar de obter o URL do serviço Azure Rights Management para *&lt;YourTenantURL&gt;*, veja novamente [Para identificar o URL do serviço Azure Rights Management](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3. Utilizar as instruções no início deste passo, a configurar os métodos de implementação de script para executar **migrar Client.cmd** e **migrar User.cmd** nos computadores de cliente do Windows que são utilizados pelo membros do grupo AIPMigrated. 

## <a name="next-steps"></a>Próximos passos
Para continuar a migração, veja a [fase 4 – configuração de serviços de suporte](migrate-from-ad-rms-phase4.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]