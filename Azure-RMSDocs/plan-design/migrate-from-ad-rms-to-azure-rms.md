---
title: Migrar do AD RMS para o Azure Information Protection
description: "Instruções para migrar a implementação dos Serviços de Gestão de Direitos do Active Directory (AD RMS) para o Azure Information Protection. Após a migração, os utilizadores continuam a ter acesso a documentos e mensagens de e-mail que a sua organização protegeu com o AD RMS, sendo que os conteúdos recentemente protegidos utilizarão o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a65e1178594e14c7d8f4faaedee96d827a9412e5
ms.sourcegitcommit: 9b975e66b12a3836003c6c4de139ded4bbf370bf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2017
---
# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>Migrar do AD RMS para o Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*

Utilize o seguinte conjunto de instruções para migrar a implementação dos Serviços de Gestão de Direitos do Active Directory (AD RMS) para o Azure Information Protection. 

Após a migração, os servidores do AD RMS já não estão em utilização mas os utilizadores ainda têm acesso aos documentos e às mensagens de e-mail que a sua organização protegeu com o AD RMS. Os conteúdos protegidos recentemente irão utilizar o serviço Azure Rights Management (Azure RMS) do Azure Information Protection.

Não tem a certeza se esta migração do AD RMS é adequada para a sua organização?

- Para obter uma introdução ao Azure Information Protection, veja [O que é o Azure Information Protection?](../understand-explore/what-is-information-protection.md)

- Para obter uma comparação entre o Azure Information Protection e o AD RMS, veja [Comparar o Azure Information Protection e o AD RMS](../understand-explore/compare-azure-rms-ad-rms.md).

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Leitura recomendada antes de migrar para o Azure Information Protection

Ainda que não seja obrigatório, poderá considerar útil a leitura da seguinte documentação antes de iniciar a migração. Estes conhecimentos fornecem uma melhor compreensão da forma como a tecnologia funciona quando é relevante para o passo de migração.

- [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md): compreenda as opções de gestão de chaves que tem para o seu inquilino do Azure Information Protection em que o equivalente da sua chave SLC na cloud é gerido pela Microsoft (predefinição) ou gerido por si (a configuração "traga a sua própria chave" ou BYOK (Bring Your Own Key)). 

- [Deteção do serviço RMS](../rms-client/client-deployment-notes.md#rms-service-discovery): esta secção das notas de implementação do cliente RMS explica que a ordem para a deteção do serviço é **registo**, **SCP** e, em seguida, **cloud**. Durante o processo de migração, quando o SCP ainda está instalado, o utilizador configura clientes com as definições de registo do seu inquilino do Azure Information Protection para que estes não utilizem o cluster do AD RMS devolvido do SCP.

- [Descrição geral do conector Microsoft Rights Management](../deploy-use/deploy-rms-connector.md#overview-of-the-microsoft-rights-management-connector): esta secção da documentação do conector RMS explica a forma como os seus servidores no local se podem ligar ao serviço Azure Rights Management para proteger documentos e e-mail.

Além disso, se estiver familiarizado com o funcionamento do AD RMS, poderá achar útil ler a secção [como funciona o Azure RMS? Nos bastidores](../understand-explore/how-does-it-work.md) para o ajudar a identificar que processos de tecnologia são iguais ou diferentes na versão na cloud.

## <a name="prerequisites-for-migrating-ad-rms-to-azure-information-protection"></a>Pré-requisitos para migrar o AD RMS para o Azure Information Protection

Antes de iniciar a migração para o Azure Information Protection, certifique-se de que os seguintes pré-requisitos são cumpridos e de que compreende todas as limitações.

- **Uma implementação RMS suportada:**
    
    - As seguintes versões do AD RMS suportam uma migração para o Azure Information Protection:
    
        - Windows Server 2008 R2 (x64)
        
        - Windows Server 2012 (x64)
        
        - Windows Server 2012 R2 (x64)
        
        - Windows Server 2016 (x64)
        
    - Todas as topologias válidas do AD RMS são suportadas:
    
        - Floresta única, cluster RMS único
        
        - Floresta única, vários clusters RMS só de licenciamento
        
        - Várias florestas, vários clusters RMS
        
    Nota: por predefinição, vários clusters do AD RMS migram para um único inquilino do Azure Information Protection. Se quiser inquilinos separados para o Azure Information Protection, tem de tratá-los como migrações diferentes. Uma chave de um cluster do RMS não pode ser importada para mais do que um inquilino.

- **Todos os requisitos para executar o Azure Information Protection, incluindo uma subscrição do Azure Information Protection (o serviço Azure Rights Management não está ativado):**

    Consulte [Requisitos do Azure Information Protection](../get-started/requirements-azure-rms.md).

    Tenha em atenção que se tiver computadores a executar o Office 2010, tem de instalar o cliente do Azure Information Protection, porque este cliente permite autenticar os utilizadores para serviços cloud. Nas versões mais recentes do Office, o cliente do Azure Information Protection é necessário para a classificação e etiquetagem e é opcional mas recomendado se quiser apenas proteger os dados. Para obter mais informações, veja o [Guia do administrador do cliente do Azure Information Protection](../rms-client/client-admin-guide.md).

    Embora precise de ter uma subscrição do Azure Information Protection para poder migrar a partir do AD RMS, recomendamos que o serviço Rights Management do seu inquilino não seja ativado antes de iniciar a migração. O processo de migração inclui este passo de ativação depois de ter exportado as chaves e modelos do AD RMS e de os ter importado para o seu inquilino do Azure Information Protection. No entanto, se o serviço Rights Management já estiver ativado, ainda pode migrar a partir do AD RMS com alguns passos adicionais.


- **Preparação para o Azure Information Protection:**

    - Sincronização de diretórios entre o diretório no local e o Azure Active Directory

    - Grupos com capacidade de correio no Azure Active Directory

    Veja [Preparar utilizadores e grupos para o Azure Information Protection](prepare.md).

- **Se tiver utilizado a funcionalidade de Gestão de Direitos de Informação (IRM) do Exchange Server** (por exemplo, regras de transporte e Outlook Web Access) ou do SharePoint Server com o AD RMS:

    - A IRM não estará disponível nestes servidores durante um curto período de tempo
 
    Pode continuar a utilizar a IRM nestes servidores após a migração. No entanto, um dos passos da migração é a desativação temporária do serviço de IRM, a instalação e configuração de um conector, a reconfiguração dos servidores e reativação da IRM.

    Esta é a única interrupção no serviço durante o processo de migração.

- **Se quiser gerir a sua própria chave de inquilino do Azure Information Protection com uma chave protegida por HSM**:

    - Esta configuração opcional requer o Azure Key Vault e uma subscrição do Azure que suporte o Key Vault com chaves protegidas por HSM. Para obter mais informações, veja a [página de Preços do Azure Key Vault](https://azure.microsoft.com/en-us/pricing/details/key-vault/). 


### <a name="cryptographic-mode-considerations"></a>Considerações sobre o modo criptográfico

Se o cluster de AD RMS está atualmente no modo criptográfico 1, não atualize o cluster para o modo criptográfico 2 antes de começar a migração. Em vez disso, migrar através do modo criptográfico 1 e pode recodificar a chave de inquilino no final da migração, como uma das tarefas de migração post.

Para confirmar o Modo Criptográfico do AD RMS:
 
- Para o Windows Server 2012 R2 e o Windows 2012: propriedades de cluster do AD RMS > separador **Geral**. 

- Para o Windows Server 2008 R2: Verifique se o [comprimento de chave RSA é aumentado para 2048 bits para o AD RMS no Windows Server 2008 R2 e no Windows Server 2008](https://support.microsoft.com/help/2627272/rsa-key-length-is-increased-to-2048-bits-for-ad-rms-in-windows-server ) correção está instalada. Se não for, o cluster do AD RMS está em execução no modo criptográfico 1.

### <a name="migration-limitations"></a>Limitações da migração

- Se tiver software e clientes que não são suportados pelo serviço Rights Management utilizado pelo Azure Information Protection, estes não poderão proteger ou consumir conteúdos protegidos pelo Azure Rights Management. Certifique-se de que verifica as secções de aplicações e clientes suportados no artigo [Requisitos para o Azure Rights Management](../get-started/requirements-azure-rms.md).

- Se a sua implementação do AD RMS estiver configurada para colaborar com parceiros externos (por exemplo, ao utilizar federações ou domínios de utilizadores fidedignos), estes também devem migrar para o Azure Information Protection em simultâneo com a sua migração ou logo que seja possível posteriormente. Para continuarem a aceder a conteúdos que a sua organização protegeu anteriormente com o Azure Information Protection, têm de fazer alterações na configuração de clientes semelhantes às que foram feitas por si e que estão incluídas neste documento.
    
    Devido às possíveis variações de configuração que os seus parceiros possam ter, as instruções exatas para esta reconfiguração não estão incluídas neste documento. No entanto, pode consultar a secção seguinte para obter orientações de planeamento e se precisar de ajuda adicional, [contacte o Suporte da Microsoft](../get-started/information-support.md#support-options-and-community-resources).

## <a name="migration-planning-if-you-collaborate-with-external-partners"></a>Planeamento da migração se colaborar com parceiros externos

Inclua os seus parceiros de AD RMS na fase de planeamento da migração porque estes também têm de migrar para o Azure Information Protection. Antes de efetuar os seguintes passos de migração, certifique-se de que os parceiros cumprem os seguintes requisitos:

- Têm um inquilino do Azure Active Directory que suporta o serviço Azure Rights Management.  
    
    Por exemplo, têm uma subscrição do Office 365 E3 ou E5, uma subscrição Enterprise Mobility + Security ou uma subscrição autónoma do Azure Information Protection.

- O serviço Azure Rights Management dos parceiros ainda não está ativado mas estes sabem o URL do serviço Azure Rights Management.

    Podem obter estas informações ao instalar a Ferramenta do Azure Rights Management, ao ligar ao serviço ([Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice)) e, em seguida, ao ver as informações do inquilino do serviço Azure Rights Management ([Get-AadrmConfiguration](/powershell/aadrm/vlatest/get-aadrmconfiguration)).

- Fornecem-lhe os URLs para o respetivo cluster do AD RMS e o URL do serviço Azure Rights Management, para que possa configurar os seus clientes migrados para redirecionar pedidos para os conteúdos protegidos do AD RMS deles para o serviço Azure Rights Management do inquilino. As instruções para configurar o redirecionamento de clientes encontram-se no passo 7.

- Importam as chaves de raiz do cluster do AD RMS (SLC) para o inquilino antes de começar a migrar os seus utilizadores. De igual modo, tem de importar as suas chaves de raiz do cluster do AD RMS antes de começarem a migrar os respetivos utilizadores. As instruções para importar a chave estão abrangidas neste processo de migração, no [Passo 4. Exportar os dados de configuração do AD RMS e importá-los para o Azure Information Protection](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection). 

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>Descrição geral dos passos para migrar o AD RMS para o Azure Information Protection

Os passos de migração podem ser divididos em cinco fases que podem ser efetuadas em alturas diferentes e por administradores diferentes.

[**FASE 1: PREPARAÇÃO DA MIGRAÇÃO**](migrate-from-ad-rms-phase1.md)

- **Passo 1: transferir a Ferramenta de Administração do Azure RMS Management e identificar o URL de inquilino**

    O processo de migração requer a execução de um ou mais cmdlets do PowerShell do módulo do Azure RMS que é instalado com a Ferramenta de Administração do Azure RMS Management. Também precisará de saber o URL do serviço Azure Rights Management do seu inquilino para concluir vários passos da migração. Pode identificar este valor através do PowerShell.

- **Passo 2: preparar a migração de clientes**

    Se não conseguir migrar todos os clientes de uma só vez e os migrar em lotes, utilize os controlos de inclusão e implemente um script de pré-migração. No entanto, se irá migrar tudo em simultâneo em vez de efetuar uma migração faseada, pode ignorar este passo.

- **Passo 3: preparar a implementação do Exchange para a migração**

    Este passo é necessário se utilizar atualmente a funcionalidade da IRM do Exchange Online ou Exchange no local para proteger e-mails. No entanto, se irá migrar tudo em simultâneo em vez de efetuar uma migração faseada, pode ignorar este passo.

[**FASE 2: CONFIGURAÇÃO DO AD RMS DO LADO DO SERVIDOR**](migrate-from-ad-rms-phase2.md)

- **Passo 4: exportar os dados de configuração do AD RMS e importá-los para o Azure Information Protection**

    Exporte os dados de configuração (chaves, modelos, URLs) do AD RMS para um ficheiro XML e, em seguida, carregue esse ficheiro para o serviço Azure Rights Management do Azure Information Protection através do cmdlet Import-AadrmTpd do PowerShell. Em seguida, identifique a chave do Certificado de Licenciante para Servidor (SLC) importada para utilizar como a chave de inquilino no serviço do Azure Rights Management. Podem ser necessários passos adicionais, dependendo da configuração da sua chave do AD RMS:

    - **Migração de chave protegida por software para chave protegida por software**:

        Chaves geridas centralmente com base em palavras-passe no AD RMS para a chave de inquilino do Azure Information Protection gerida pela Microsoft. Este é o caminho de migração mais simples e não são necessários passos adicionais.

    - **Migração de chave protegida por HSM para chave protegida por HSM**:

        Chaves que são armazenadas por um HSM do AD RMS para a chave de inquilino do Azure Information Protection gerida pelo cliente (o cenário "traga a sua própria chave" ou BYOK). Isto requer passos adicionais para transferir a chave do seu HSM da Thales no local para o Azure Key Vault e autorizar o serviço Azure Rights Management a utilizar esta chave. A sua chave existente protegida por HSM tem de ser protegida por módulo. As chaves protegidas por OCS não são suportadas pelos Rights Management Services.

    - **Migração de chave protegida por software para chave protegida por HSM**:

        Chaves geridas centralmente e baseadas em palavras-passe no AD RMS para a chave de inquilino do Azure Information Protection gerida pelo cliente (o cenário "traga a sua própria chave" ou BYOK). Esta é a migração que requer mais configuração porque tem primeiro de extrair a chave de software e importá-la para um HSM no local e, em seguida, efetuar os passos adicionais para transferir a chave do seu HSM da Thales no local para um HSM do Azure Key Vault e autorizar o serviço Azure Rights Management a utilizar o cofre de chaves que armazena a chave.

- **Passo 5: ativar o serviço Azure Rights Management**

    Se possível, efetue este passo depois do processo de importação e não antes. Será necessário realizar passos adicionais se o serviço tiver sido ativado antes da importação.

- **Passo 6: configurar modelos importados**

    Quando importar os seus modelos de política de direitos, o estado dos mesmos é arquivado. Se pretender que os utilizadores os possam ver e utilizar, tem de alterar o estado do modelo para publicado no portal clássico do Azure.


[**FASE 3: CONFIGURAÇÃO DO LADO DO CLIENTE**](migrate-from-ad-rms-phase3.md)

- **Passo 7: Reconfigurar computadores Windows para utilizar o Azure Information Protection**

    Os computadores Windows existentes têm de ser reconfigurados para utilizar o serviço Azure Rights Management em vez do AD RMS. Este passo aplica-se aos computadores na sua organização e aos computadores nas organizações parceiras, caso tenha colaborado com as mesmas enquanto executou o AD RMS.

[**FASE 4: CONFIGURAÇÃO DE SERVIÇOS DE SUPORTE**](migrate-from-ad-rms-phase4.md)

- **Passo 8: configurar a integração de IRM para o Exchange Online**

    Este passo conclui a migração do AD RMS para o Exchange Online para utilizar o serviço Azure Rights Management.

- **Passo 9: configurar a integração de IRM para o Exchange Server e SharePoint Server**

    Este passo conclui a migração do AD RMS para o Exchange ou SharePoint no local para utilizar o serviço Azure Rights Management, que necessita da implementação do conector Rights Management.


[**FASE 5: TAREFAS DE PÓS-MIGRAÇÃO**](migrate-from-ad-rms-phase5.md )

- **Passo 10: desaprovisionar o AD RMS**

    Quando tiver confirmado que todos os computadores Windows estiver a utilizar o serviço Azure Rights Management e já não acedem aos seus servidores AD RMS, pode desaprovisionar a implementação do AD RMS.

- **Passo 11: Concluir tarefas de migração de cliente**

    Se tiver implementado o [extensão do dispositivo móvel](http://technet.microsoft.com/library/dn673574.aspx) para suportar dispositivos móveis, como telemóveis de iOS e iPads, telemóveis Android e tablets, Windows phone e computadores Mac, tem de remover os registos SRV no DNS que redirecionou estes clientes Para utilizar o AD RMS. 
    
    Os controlos de inclusão que configurou durante a fase de preparação já não são necessários. No entanto, se não utilizou controlos de inclusão porque optar por migrar tudo ao mesmo tempo, em vez de efetuar uma migração faseada, pode ignorar as instruções para remover os controlos de inclusão.
    
    Se os computadores com o Windows estiver a executar o Office 2010, verifique se tem de desativar o **gestão de modelos de política de direitos de RMS do AD (automatizada)** tarefas.

- **Passo 12: Recodificar a chave de inquilino do Azure Information Protection**

    Este passo é recomendado se não estivesse a executar no modo criptográfico 2 antes da migração.


## <a name="next-steps"></a>Próximos passos
Para iniciar a migração, avance para a [Fase 1 – preparação](migrate-from-ad-rms-phase1.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
