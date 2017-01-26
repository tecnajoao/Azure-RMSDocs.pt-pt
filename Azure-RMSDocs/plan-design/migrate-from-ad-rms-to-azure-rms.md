---
title: Migrar do AD RMS para o Azure Information Protection | Azure Information Protection
description: "Instruções para migrar a implementação dos Serviços de Gestão de Direitos do Active Directory (AD RMS) para o Azure Information Protection. Após a migração, os utilizadores continuam a ter acesso a documentos e mensagens de e-mail que a sua organização protegeu com o AD RMS, sendo que os conteúdos recentemente protegidos utilizarão o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/27/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 30a154d67db81441cd48c56681ddb6552fc4cd18


---

# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>Migrar do AD RMS para o Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*

Utilize o seguinte conjunto de instruções para migrar a implementação dos Serviços de Gestão de Direitos do Active Directory (AD RMS) para o Azure Information Protection. Após a migração, os utilizadores continuam a ter acesso a documentos e mensagens de e-mail que a sua organização protegeu com o AD RMS, sendo que os conteúdos recentemente protegidos utilizarão o serviço Azure Rights Management do Azure Information Protection.

Não tem a certeza se esta migração do AD RMS é adequada para a sua organização?

-   Para obter uma introdução ao Azure Information Protection, consulte [O que é o Azure Information Protection?](../understand-explore/what-is-information-protection.md)

-   Para obter uma comparação entre o Azure Information Protection e o AD RMS, consulte [Comparar o Azure Information Protection e o AD RMS](../understand-explore/compare-azure-rms-ad-rms.md).

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Leitura recomendada antes de migrar para o Azure Information Protection

Apesar de não ser obrigatório, poderá considerar útil ler o seguinte antes de iniciar a migração para que possa compreender melhor como funciona a tecnologia quando é relevante para o seu passo de migração:

- [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md): compreenda as opções de gestão de chaves que tem para o seu inquilino do Azure Information Protection em que o equivalente da sua chave SLC na nuvem é gerido pela Microsoft (predefinição) ou gerido por si (a configuração "traga a sua própria chave" ou BYOK (Bring Your Own Key)). 

- [Deteção do serviço RMS](../rms-client/client-deployment-notes.md#rms-service-discovery): esta secção das notas de implementação do cliente RMS explica que a ordem para a deteção do serviço é **registo** > **SCP** > **nuvem**. Durante o processo de migração, quando o SCP ainda está instalado, o utilizador configura clientes com as definições de registo do seu inquilino do Azure Information Protection para que estes não utilizem o cluster do AD RMS devolvido do SCP.

- [Descrição geral do conector Microsoft Rights Management](../deploy-use/deploy-rms-connector.md#overview-of-the-microsoft-rights-management-connector): esta secção da documentação do conector RMS explica a forma como os seus servidores no local se podem ligar ao serviço Azure Rights Management para proteger documentos e e-mail.

Além disso, se estiver familiarizado com o funcionamento do AD RMS, poderá achar útil ler a secção [como funciona o Azure RMS? Nos bastidores](../understand-explore/how-does-it-work.md) para o ajudar a identificar que processos de tecnologia são iguais ou diferentes na versão em nuvem.

## <a name="prerequisites-for-migrating-ad-rms-to-azure-information-protection"></a>Pré-requisitos para migrar o AD RMS para o Azure Information Protection
Antes de iniciar a migração para o Azure Information Protection, certifique-se de que os seguintes pré-requisitos são cumpridos e de que compreende todas as limitações.

- **Uma implementação RMS suportada:**
    
    - As seguintes versões do AD RMS suportam uma migração para o Azure Information Protection:
    
        - Windows Server 2008 R2 (x64)
        
        - Windows Server 2012 (x64)
        
        - Windows Server 2012 R2 (x64)
        
        - Windows Server 2016 (x64)
        
    - Modo Criptográfico 2:

        - Os clientes e os servidores do AD RMS têm de estar em execução no Modo Criptográfico 2 antes de iniciar a migração para o Azure Information Protection.
        
        Embora a chave do certificado de licenciante para servidor (SLC) atual tenha de utilizar o Modo Criptográfico 2, as chaves anteriores que foram configuradas para o Modo Criptográfico 1 são suportadas pelo Azure Information Protection como chaves arquivadas. Para obter mais informações sobre os modos criptográficos e como mudar para o Modo Criptográfico 2, consulte [Modos Criptográficos do AD RMS](https://technet.microsoft.com/library/hh867439(v=ws.10).aspx).
        
    - Todas as topologias válidas do AD RMS são suportadas:
    
        - Floresta única, cluster RMS único
        
        - Floresta única, vários clusters RMS só de licenciamento
        
        - Várias florestas, vários clusters RMS
        
    Nota: por predefinição, múltiplos clusters RMS migram para um único inquilino do Azure Information Protection. Se quiser inquilinos do Azure Information Protection separados, tem de tratá-los como migrações diferentes. Uma chave de um cluster do RMS não pode ser importada para mais do que um inquilino do Azure Information Protection.

- **Todos os requisitos para executar o Azure Information Protection, incluindo um inquilino do Azure Information Protection (não ativado):**

    Consulte [Requisitos do Azure Information Protection](../get-started/requirements-azure-rms.md).

    Embora precise de ter um inquilino do Azure Information Protection para poder migrar do AD RMS, recomendamos que não ative o serviço Rights Management antes da migração. O processo de migração inclui este passo após a exportação de chaves e modelos do AD RMS e respetiva importação para o Azure Information Protection. No entanto, se o serviço Rights Management já estiver ativado, ainda pode migrar a partir do AD RMS.


- **Preparação para o Azure Information Protection:**

    - Sincronização de diretórios entre o diretório no local e o Azure Active Directory

    - Grupos com capacidade de correio no Azure Active Directory

    Consulte [Preparação para o Azure Information Protection](prepare.md).


- **Se tiver utilizado a funcionalidade de Gestão de Direitos de Informação (IRM) do Exchange Server** (por exemplo, regras de transporte e Outlook Web Access) ou do SharePoint Server com o AD RMS:

    - A IRM não estará disponível nestes servidores durante um curto período de tempo
 
    Pode continuar a utilizar a IRM nestes servidores com o serviço Azure Rights Management após a migração. No entanto, um dos passos da migração é a desativação temporária do serviço de IRM, a instalação e configuração de um conetor, a reconfiguração dos servidores e reativação da IRM.

    Esta é a única interrupção no serviço durante o processo de migração.

- **Se quiser gerir a sua própria chave de inquilino do Azure Information Protection com uma chave protegida por HSM**:

    - Esta configuração opcional requer o Cofre de Chaves do Azure e uma subscrição do Azure que suporte o Cofre de Chaves com chaves protegidas por HSM. Para obter mais informações, veja a [página de Preços do Cofre de Chaves do Azure](https://azure.microsoft.com/en-us/pricing/details/key-vault/). 


Limitações:

-   Embora o processo de migração permita migrar a chave do certificado de licenciamento de servidor (SLC) para um módulo de segurança de hardware (HSM) para o Azure Information Protection, o Exchange Online não suporta atualmente esta configuração para o serviço Rights Management utilizado pelo Azure Information Protection. Se quiser todas as funcionalidades de IRM com o Exchange Online após a migração para o Azure Information Protection, a chave de inquilino do Azure Information Protection tem de ser [gerida pela Microsoft](../plan-design/plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok). Em alternativa, pode executar a IRM com funcionalidade reduzida no Exchange Online quando o inquilino do Azure Information Protection é gerido por si (BYOK). Para mais informações sobre a utilização do Exchange Online com o serviço Azure Rights Management, consulte o [Passo 6. Configurar a integração de IRM para o Exchange Online](migrate-from-ad-rms-phase3.md#step-6-configure-irm-integration-for-exchange-online) nestas instruções de migração.

-   Se tiver software e clientes que não são suportados pelo serviço Rights Management utilizado pelo Azure Information Protection, estes não poderão proteger ou consumir conteúdos protegidos pelo Azure Rights Management. Não se esqueça de verificar as secções de aplicações e clientes suportados no artigo [Requisitos do Azure Rights Management](../get-started/requirements-azure-rms.md).

-   Se importar a chave no local para o Azure Information Protection como arquivada (se não definir o TPD para ser o ativo durante o processo de importação) e migrar utilizadores em lotes para uma migração faseada, os conteúdos protegidos recentemente pelos utilizadores migrados não estarão acessíveis aos utilizadores que permanecerem no AD RMS. Neste cenário, sempre que possível, mantenha o tempo de migração curto e migre os utilizadores em lotes lógicos, de tal forma que se colaborarem mutuamente, sejam migrados em conjunto.

    Esta limitação não se aplica quando define o TPD para ativo durante o processo de importação, porque todos os utilizadores irão proteger o conteúdo através da mesma chave. Recomendamos esta configuração porque lhe permite migrar todos os utilizadores de forma independente e ao seu ritmo.

-   Se colaborar com parceiros externos (por exemplo, através da utilização de domínios ou federações de utilizadores fidedignos), estes também têm de migrar para o Azure Information Protection em simultâneo com a sua migração ou logo que seja possível posteriormente. Para continuarem a aceder a conteúdos que a sua organização protegeu anteriormente com o Azure Information Protection, têm de fazer alterações na configuração de clientes semelhantes às que foram feitas por si e que estão incluídas neste documento.

    Devido às possíveis variações de configuração que os seus parceiros possam ter, as instruções exatas para esta reconfiguração não estão incluídas neste documento. Para obter ajuda, [contacte o Suporte da Microsoft](../get-started/information-support.md#support-options-and-community-resources).

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>Descrição geral dos passos para migrar o AD RMS para o Azure Information Protection


Os passos de migração podem ser divididos em 4 fases que podem ser efetuadas em alturas diferentes e por administradores diferentes.

[**FASE 1: CONFIGURAÇÃO DO AD RMS DO LADO DO SERVIDOR**](migrate-from-ad-rms-phase1.md)

- **Passo 1: transferir a Ferramenta de Administração de Gestão do Azure RMS**

    O processo de migração requer a execução de um ou mais cmdlets do Windows PowerShell do módulo do Azure RMS que é instalado com a Ferramenta de Administração de Gestão do Azure RMS.

- **Passo 2: exportar dados de configuração do AD RMS e importá-los para o Azure Information Protection**

    Exporte os dados de configuração (chaves, modelos, URLs) do AD RMS para um ficheiro XML e, em seguida, carregue esse ficheiro para o serviço Azure Rights Management do Azure Information Protection através do cmdlet Import-AadrmTpd do Windows PowerShell. É possível que sejam necessários mais passos, consoante a configuração da sua chave do AD RMS:

    - **Migração de chave protegida por software para chave protegida por software**:

        Chaves geridas centralmente com base em palavras-passe no AD RMS para a chave de inquilino do Azure Information Protection gerida pela Microsoft. Este é o caminho de migração mais simples e não são necessários passos adicionais.

    - **Migração de chave protegida por HSM para chave protegida por HSM**:

        Chaves que são armazenadas por um HSM do AD RMS para a chave de inquilino do Azure Information Protection gerida pelo cliente (o cenário "traga a sua própria chave" ou BYOK). Isto requer passos adicionais para transferir a chave do seu HSM da Thales no local para o Cofre de Chaves do Azure e autorizar o serviço Azure Rights Management a utilizar esta chave. A sua chave existente protegida por HSM tem de ser protegida por módulo. As chaves protegidas por OCS não são suportadas pelos Rights Management Services.

    - **Migração de chave protegida por software para chave protegida por HSM**:

        Chaves geridas centralmente e baseadas em palavras-passe no AD RMS para a chave de inquilino do Azure Information Protection gerida pelo cliente (o cenário "traga a sua própria chave" ou BYOK). Esta é a migração que requer mais configuração porque tem primeiro de extrair a chave de software e importá-la para um HSM no local e, em seguida, efetuar os passos adicionais para transferir a chave do seu HSM da Thales no local para um HSM do Cofre de Chaves do Azure e autorizar o serviço Azure Rights Management a utilizar o cofre de chaves que armazena a chave.

- **Passo 3: ativar o inquilino do Azure Information Protection**

    Se possível, efetue este passo depois do processo de importação e não antes.

- **Passo 4: configurar modelos importados**

    Quando importar os seus modelos de política de direitos, o estado dos mesmos é arquivado. Se pretender que os utilizadores os possam ver e utilizar, tem de alterar o estado do modelo para publicado no portal clássico do Azure.


[**FASE 2: CONFIGURAÇÃO DO LADO DO CLIENTE**](migrate-from-ad-rms-phase2.md)


- **Passo 5: reconfigurar clientes para que utilizem o Azure Information Protection**

    Os computadores existentes com Windows têm de ser reconfigurados para utilizarem o serviço Azure Information Protection em vez do AD RMS. Este passo aplica-se aos computadores na sua organização e aos computadores nas organizações parceiras, caso tenha colaborado com as mesmas enquanto executou o AD RMS.

    Além disso, se tiver implementado a [extensão de dispositivo móvel](http://technet.microsoft.com/library/dn673574.aspx) para suportar dispositivos móveis, tais como iPads e telemóveis com iOS, tablets e telemóveis Android, telemóvel Windows e computadores Mac, tem de remover os registos SRV no DNS que redirecionou estes clientes para utilizarem o AD RMS


[**FASE 3: CONFIGURAÇÃO DOS SERVIÇOS DE SUPORTE**](migrate-from-ad-rms-phase3.md)


- **Passo 6: configurar a integração de IRM com o Exchange Online**

    Este passo é necessário se quiser utilizar o Exchange Online com o serviço Azure Rights Management do Azure Information Protection.


- **Passo 7: implementar o conector RMS**

    Este passo é necessário se quiser utilizar um dos seguintes serviços no local com o serviço Azure Rights Management para proteger e-mails e documentos do Office:

    - Exchange Server (por exemplo, regras de transporte e Outlook Web Access)

    - SharePoint Server

    - Windows Server que executa a Infraestrutura de Classificação de Ficheiros (FCI)


[**FASE 4: TAREFAS PÓS-MIGRAÇÃO**](migrate-from-ad-rms-phase4.md )

- **Passo 8: desativar o AD RMS**

    Quando tiver confirmado que todos os clientes estão a utilizar o Azure Information Protection e já não acedem aos servidores do AD RMS, pode desativar a implementação do AD RMS.


- **Passo 9: recodificar a chave de inquilino do Azure Information Protection**

    Este passo é opcional mas recomendado se a topologia de chave de inquilino do Azure Information Protection escolhida no passo 2 for gerida pela Microsoft. Este passo não é aplicável se a topologia de chave de inquilino do Azure Information Protection escolhida for gerida pelo cliente (BYOK).


## <a name="next-steps"></a>Passos seguintes
Para iniciar a migração, aceda a [Fase 1 – configuração do lado do servidor](migrate-from-ad-rms-phase1.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


