---
title: Migrar do AD RMS para o Azure Information Protection – fase 3
description: Fase 3 da migração do AD RMS para o Azure Information Protection, que abrange o passo 7 de Migrar do AD RMS para o Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/11/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5aa86c3806dd23787d2661b4a4ac2e6850d1e907
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393895"
---
# <a name="migration-phase-3---client-side-configuration"></a>Fase 3 da migração – configuração do lado do cliente

>*Aplica-se a: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize as seguintes informações para a Fase 3 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem o passo 7 de [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>Passo 7: Reconfigure os computadores Windows para utilizar o Azure Information Protection

Para computadores Windows que utilizam aplicações de ambiente de trabalho de clique-e-Use do Office 2016:

- Pode reconfigurar a estes clientes para utilizarem o Azure Information Protection com o redirecionamento de DNS. Este é o método preferencial de migração de clientes, porque é a forma mais simples. No entanto, esse método é restrito a aplicações de ambiente de trabalho clique-e-Use do Office 2016 (ou posterior) para computadores Windows.
    
    Este método requer que crie um novo SRV registe e conjunto um NTFS neguem a permissão para os utilizadores no ponto de final de publicação de AD RMS.

- Para computadores Windows que não usam o Office 2016 click-to-run:
    
    Não é possível utilizar o redirecionamento de DNS e em vez disso, tem de utilizar edições de registo. Se tiver uma mistura de Office 2016 e outras versões do Office, pode utilizar este método único para todos os computadores Windows ou uma combinação de redirecionamento de DNS e editar o registo. 
    
    As alterações de registo são mais fácil para editando e implantação de scripts que pode baixar. 

Veja as secções seguintes para obter mais informações sobre como reconfigurar os clientes do Windows.

## <a name="client-reconfiguration-by-using-dns-redirection"></a>Reconfiguração de clientes com o redirecionamento de DNS

Este método só é adequado para clientes de Windows que executam aplicações de ambiente de trabalho de clique-e-Use do Office 2016 (ou posterior). 

1. Crie um registo SRV de DNS com o seguinte formato:
    
    `_rmsredir._http._tcp.<AD RMS cluster>. <TTL> IN SRV <priority> <weight> <port> <your tenant URL>.`
    
    Para  *\<cluster AD RMS >*, especifique o FQDN do cluster do AD RMS. Por exemplo, **rmscluster.contoso.com**.
    
    Em alternativa, se tiver apenas um cluster de AD RMS nesse domínio, pode especificar apenas o nome de domínio do cluster do AD RMS. No nosso exemplo, isso seria **contoso.com**. Quando especificar o nome de domínio neste registo, o redirecionamento aplica-se a todos os clusters do AD RMS nesse domínio.
    
    O  *\<porta >* número é ignorado.
    
    Para  *\<o URL de inquilino\>*, especificar a sua própria [URL do serviço Azure Rights Management para o seu inquilino](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).
    
    Se utilizar a função de servidor DNS no Windows Server, pode utilizar a tabela seguinte como exemplo como especificar as propriedades de registo SRV na consola do Gestor de DNS.
    
    |Campo|Valor|  
    |-----------|-----------|  
    |**Domínio**|_tcp.rmscluster.contoso.com|  
    |**Serviço**|_rmsredir|  
    |**Protocolo**|_http|  
    |**prioridade**|0|  
    |**peso**|0|  
    |**Número da porta**|80|  
    |**Anfitrião que oferece este serviço**|5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com|  

2. Defina uma permissão de negação para os utilizadores do Office 2016 no ponto de final de publicação de AD RMS:

    a. Dos servidores do AD RMS no cluster, inicie a consola do Gestor de serviços de informação Internet (IIS).

    b. Navegue para **Web Site predefinido** > **wmcs** > **licenciamento** > **licensing.asmx**

    c. Com o botão direito **licensing.asmx** > **propriedades** > **editar**

    d. Na **permissões para licensing.asmx** caixa de diálogo, selecione **utilizadores** se pretender definir o redirecionamento para todos os utilizadores ou clique em **Add** e, em seguida, especifique um grupo que contém os utilizadores que pretende redirecionar.
    
    Mesmo que todos os seus utilizadores estão a utilizar o Office 2016, poderá preferir inicialmente especificar um subconjunto de utilizadores para uma migração faseada.
    
    e. Para o seu grupo selecionado, selecione **negar** para o **leitura & Execute** e o **leitura** permissão e clique em **OK** duas vezes.

    f. Para confirmar que esta configuração está a funcionar conforme esperado, tente ligar-se para o ficheiro de licensing.asmx diretamente a partir de um browser. Deverá ver a seguinte mensagem de erro, que dispara o cliente a executar o Office 2016 para procurar o registo SRV:
    
    **Chybová zpráva 401.3: Não tem permissões para visualizar este diretório ou página com as credenciais que forneceu (acesso negado devido a listas de controlo de acesso).**


## <a name="client-reconfiguration-by-using-registry-edits"></a>Reconfiguração de clientes com edições de registo

Esse método é adequado para todos os clientes do Windows e deve ser utilizado se não executam o Office 2016, mas uma versão anterior. Este método utiliza dois scripts de migração para reconfigurar clientes de AD RMS:

- Migrate-Client.cmd

- Migrate-User.cmd

O script de configuração de cliente (Migrate-Client.cmd) configura definições ao nível do computador no Registro, o que significa que deve ser executado num contexto de segurança que pode efetuar essas alterações. Isso normalmente significa que um dos seguintes métodos:

- Utilize a política de grupo para executar o script como um script de inicialização do computador.

- Utilize a instalação de software da diretiva de grupo para atribuir o script no computador.

- Utilize uma solução de implantação de software para implementar o script nos computadores. Por exemplo, utilizar o System Center Configuration Manager [pacotes e programas](/sccm/apps/deploy-use/packages-and-programs). Nas propriedades do pacote e programa, sob **modo de execução**, especifique que o script é executado com permissões administrativas no dispositivo. 

- Utilize um script de início de sessão se o utilizador tiver privilégios de administrador local.

O script de configuração de utilizador (Migrate-User.cmd) configura as definições de nível de usuário e limpa o arquivo de licença de cliente. Isso significa que este script deve ser executado no contexto de utilizador reais. Por exemplo:

- Utilize um script de início de sessão.

- Utilize a instalação de software da diretiva de grupo para publicar o script para o utilizador executar.

- Utilize uma solução de implantação de software para implementar o script para os utilizadores. Por exemplo, utilizar o System Center Configuration Manager [pacotes e programas](/sccm/apps/deploy-use/packages-and-programs). Nas propriedades do pacote e programa, sob **modo de execução**, especifique que o script é executado com as permissões do utilizador. 

- Pedir ao utilizador para executar o script quando iniciar a sessão aos respetivos computadores.

Os dois scripts incluem um número de versão e não volte a executar até que este número de versão é alterado. Isso significa que pode deixar os scripts em vigor até que a migração estiver concluída. No entanto, se fizer alterações aos scripts de que pretende que computadores e utilizadores para voltar a executar em seus computadores Windows, atualize a seguinte linha em ambos os scripts para um valor mais alto:

    SET Version=20170427

O script de configuração do utilizador foi concebido para ser executado após o script de configuração do cliente e utiliza o número de versão nesta verificação. Ele será interrompido se não tiver executado o script de configuração de cliente com a mesma versão. Esta verificação assegura que os dois scripts executado na sequência correta. 

Quando não é possível migrar todos os seus clientes de Windows de uma só vez, execute os seguintes procedimentos em lotes de clientes. Para cada utilizador com um computador Windows que pretende migrar no seu lote, adicione o utilizador ao grupo **AIPMigrated** que criou anteriormente.

### <a name="modifying-the-scripts-for-registry-edits"></a>Modificar os scripts para edições de registo

1. Voltar para os scripts de migração **Client.cmd para migrar** e **User.cmd para migrar**, que extraiu anteriormente quando transferiu esses scripts no [fase de preparação](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration).

2. Siga as instruções em **migrar Client.cmd** para modificar o script para que ele contém o URL de serviço do Azure Rights Management do seu inquilino, e também os nomes de servidores para o AD RMS cluster URL de licenciamento na extranet e da intranet URL de licenciamento. Em seguida, incremente a versão do script, o que foi explicada anteriormente. Uma boa prática para controlo de versões de script é usar a data de hoje no seguinte formato: AAAAMMDD
    
   > [!IMPORTANT]
   > Tal como anteriormente, tenha cuidado para não introduzir espaços adicionais antes ou depois dos seus endereços.
   > 
   > Além disso, se os seus servidores do AD RMS utilizarem certificados de servidor SSL/TLS, verifique se os valores de URL de licenciamento incluem o número de porta **443** na cadeia. Por exemplo: https://rms.treyresearch.net:443/_wmcs/licensing. Pode encontrar estas informações na consola de serviços de gestão de direitos do Active Directory quando clica no nome do cluster e veja a **detalhes do Cluster** informações. Se vir o número de porta 443 incluído no URL, inclua este valor quando modificar o script. Por exemplo, https://rms.treyresearch.net:<strong>443</strong>. 
    
   Se precisar de obter o URL do serviço Azure Rights Management para *&lt;YourTenantURL&gt;*, veja novamente [Para identificar o URL do serviço Azure Rights Management](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3. Usando as instruções no início deste passo, a configurar seus métodos de implementação de script para executar **Client.cmd para migrar** e **migrar User.cmd** nos computadores cliente Windows que são utilizados pela membros do grupo AIPMigrated. 

## <a name="next-steps"></a>Passos Seguintes
Para continuar a migração, veja a [fase 4 – configuração de serviços de suporte](migrate-from-ad-rms-phase4.md).
