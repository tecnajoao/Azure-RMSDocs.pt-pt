---
title: "Migrar do AD RMS para o Azure Information Protection – fase 3"
description: "Fase 3 da migração do AD RMS para o Azure Information Protection, que abrange o passo 7 de Migrar do AD RMS para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 27dc3de51c72d0142ac3dbdbd97c02c0241e902d
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
# <a name="migration-phase-3---client-side-configuration"></a>Fase 3 da migração – configuração do lado do cliente

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*

Utilize as seguintes informações para a Fase 3 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem o passo 7 de [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

Quando não é possível migrar todos os clientes de uma só vez, execute estes procedimentos em lotes de clientes. Para cada utilizador com um computador Windows que pretende migrar no seu lote, adicione o utilizador ao grupo **AIPMigrated** que criou anteriormente.

## <a name="step-7-reconfigure-clients-to-use-azure-information-protection"></a>Passo 7: reconfigurar os clientes para utilizarem o Azure Information Protection

Este passo utiliza scripts de migração para reconfigurar clientes de AD RMS. Os scripts repõem a configuração em computadores Windows para utilizar o serviço Azure Rights Management em vez do AD RMS: 

**CleanUpRMS.cmd**:

- Elimina os conteúdos de todas as pastas e chaves de registo utilizadas pelo cliente de AD RMS para armazenar a configuração. Estas informações incluem a localização do cluster do AD RMS do cliente.

**MigrateClient.cmd**:

- Configura o cliente para inicializar o ambiente de utilizador (programa de arranque do sistema) para o serviço Azure Rights Management.

-  Configura o cliente para ligar ao seu serviço Azure Rights Management para obter licenças de utilização para conteúdos que estejam protegidos pelo cluster do AD RMS. 


### <a name="client-reconfiguration-by-using-registry-edits"></a>Reconfiguração de clientes com edições de registo

1. Volte aos scripts de migração, **CleanUpRMS.cmd** e **MigrateClient.cmd**, que extraiu anteriormente.

2.  Siga as instruções em **MigrateClient.cmd** para modificar o script para que contenha o URL do serviço Azure Rights Management do seu inquilino e os nomes de servidores para o URL de licenciamento na intranet e o URL de licenciamento na extranet do cluster do AD RMS.

    > [!IMPORTANT]
    > Tal como anteriormente, tenha cuidado para não introduzir espaços adicionais antes ou depois dos seus endereços.
    > 
    > Além disso, se os seus servidores do AD RMS utilizarem certificados de servidor SSL/TLS, verifique se os valores de URL de licenciamento incluem o número de porta **443** na cadeia. Por exemplo: https:// rms.treyresearch.net:443/_wmcs/licensing. Estas informações encontram-se na consola dos Serviços de Gestão de Direitos do Active Directory quando clica no nome do cluster e vê as informações de **Detalhes do Cluster**. Se vir o número de porta 443 incluído no URL, inclua este valor quando modificar o script. Por exemplo, https://rms.treyresearch.net:**443**. 

    Se precisar de obter o URL do serviço Azure Rights Management para *&lt;YourTenantURL&gt;*, veja novamente [Para identificar o URL do serviço Azure Rights Management](migrate-from-ad-rms-phase1.md#to-identify-your-azure-rights-management-service-url).

3.  Execute **CleanUpRMS.cmd** e, em seguida, **MigrateClient.cmd** nos computadores cliente utilizados pelos membros do grupo **AIPMigrated**. Por exemplo, crie um objeto de política de grupo que execute estes scripts e atribua-o a este grupo de utilizadores.


## <a name="next-steps"></a>Passos seguintes
Para continuar a migração, veja a [fase 4 – configuração de serviços de suporte](migrate-from-ad-rms-phase3.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]