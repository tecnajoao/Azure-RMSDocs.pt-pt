---
title: "Migrar do AD RMS para o Azure Information Protection – fase 3"
description: "Fase 3 da migração do AD RMS para o Azure Information Protection, que abrange o passo 7 de Migrar do AD RMS para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5de30d095e1c279babb8f8be74a5a9b9d54db204
ms.sourcegitcommit: 45c23b3b353ad0e438292cb1cd8d1b13061620e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/12/2017
---
# <a name="migration-phase-3---client-side-configuration"></a>Fase 3 da migração – configuração do lado do cliente

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*

Utilize as seguintes informações para a Fase 3 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem o passo 7 de [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-7-reconfigure-windows-computers-to-use-azure-information-protection"></a>Passo 7: Reconfigure os computadores com o Windows para utilizar o Azure Information Protection

Para computadores Windows, utilize dois scripts de migração para reconfigurar clientes de AD RMS:

- Client.cmd migrar

- User.cmd migrar

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

O script de configuração do utilizador foi concebido para ser executada após o script de configuração de cliente e utiliza o número de versão nesta verificação. Irá parar se não tiver executado o script de configuração de cliente com a mesma versão. Esta verificação garante que os dois scripts são executados na sequência correta. 

Quando não é possível migrar todos os seus clientes do Windows de uma só vez, execute os seguintes procedimentos para lotes de clientes. Para cada utilizador com um computador Windows que pretende migrar no seu lote, adicione o utilizador ao grupo **AIPMigrated** que criou anteriormente.

### <a name="windows-client-reconfiguration-by-using-registry-edits"></a>Reconfiguração de cliente do Windows, utilizando as edições de registo

1. Regressar para os scripts de migração, **migrar Client.cmd** e **migrar User.cmd**, que anteriormente extraiu quando tiver transferido estes scripts no [fase de preparação](migrate-from-ad-rms-phase1.md#step-2-prepare-for-client-migration).

2.  Siga as instruções em **migrar Client.cmd** para modificar o script para que este contém o URL do serviço do seu inquilino do Azure Rights Management e também os nomes de servidor para o AD RMS cluster URL de licenciamento de extranet e da intranet URL de licenciamento. Em seguida, aumentar a versão do script, que foi explicada anteriormente. É uma boa prática para controlar as versões de script para utilizar a data de hoje no seguinte formato: AAAAMMDD

    > [!IMPORTANT]
    > Tal como anteriormente, tenha cuidado para não introduzir espaços adicionais antes ou depois dos seus endereços.
    > 
    > Além disso, se os seus servidores do AD RMS utilizarem certificados de servidor SSL/TLS, verifique se os valores de URL de licenciamento incluem o número de porta **443** na cadeia. Por exemplo: https:// rms.treyresearch.net:443/_wmcs/licensing. Estas informações encontram-se na consola dos Serviços de Gestão de Direitos do Active Directory quando clica no nome do cluster e vê as informações de **Detalhes do Cluster**. Se vir o número de porta 443 incluído no URL, inclua este valor quando modificar o script. Por exemplo, https://rms.treyresearch.net:**443**. 

    Se precisar de obter o URL do serviço Azure Rights Management para *&lt;YourTenantURL&gt;*, veja novamente [Para identificar o URL do serviço Azure Rights Management](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3. Utilizar as instruções no início deste passo, a configurar os métodos de implementação de script para executar **migrar Client.cmd** e **migrar User.cmd** nos computadores de cliente do Windows que são utilizados pelo membros do grupo AIPMigrated. 

## <a name="next-steps"></a>Próximos passos
Para continuar a migração, veja a [fase 4 – configuração de serviços de suporte](migrate-from-ad-rms-phase3.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]