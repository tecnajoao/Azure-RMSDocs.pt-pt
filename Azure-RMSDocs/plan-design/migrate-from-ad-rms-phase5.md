---
title: "Migrar do AD RMS para o Azure Information Protection – fase 5"
description: "Fase 5 da migração do AD RMS para o Azure Information Protection, que abrange os passos 10 a 12 de Migrar do AD RMS para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: aeffd9780001f4c91ea8600f11d8fc3b36abce73
ms.sourcegitcommit: 238657f9450f18213c2b9fb453174df0ce1f1aef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2017
---
# <a name="migration-phase-5---post-migration-tasks"></a>Fase 5 da migração – tarefas de pós-migração

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*


Utilize as seguintes informações para a Fase 5 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem os passos 10 a 12 de [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-10-deprovision-ad-rms"></a>Passo 10: Retirar o aprovisionamento do AD RMS

Remova o Ponto de Ligação de Serviço (SCP) do Active Directory para impedir que os computadores detetem a sua infraestrutura da Gestão de Direitos no local. Isto é opcional para os clientes existentes que migraram devido ao redirecionamento que foi configurado no registo (por exemplo, ao executar o script de migração). No entanto, remover o SCP impede que novos clientes e serviços potencialmente relacionados com o RMS e as ferramentas de localizar o SCP quando a migração estar concluída. Neste momento, todas as ligações do computador devem passar para o serviço Azure Rights Management. 

Para remover o SCP, garanta que tem sessão iniciada como administrador da empresa do domínio e, em seguida, utilize o seguinte procedimento:

1. Na consola Serviços de Gestão de Direitos do Active Directory, clique com o botão direito do rato no cluster do AD RMS e, em seguida, clique em **Propriedades**.

2. Clique no separador **SCP**.

3. Selecione a caixa de verificação **Alterar SCP**.

4. Selecione **Remover SCP atual** e, em seguida, clique em **OK**.

Agora a monitorizar os servidores do AD RMS para a atividade. Por exemplo, verificar o [pedidos no relatório do Estado de funcionamento do sistema](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), a [tabela ServiceRequest](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) ou [auditar o acesso de utilizador a conteúdo protegido](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). 

Quando tiver confirmado que os clientes RMS já não estão a comunicar com estes servidores e que os clientes estão a utilizar o Azure Information Protection com êxito, pode remover a função de servidor do AD RMS destes servidores. Se estiver a utilizar servidores dedicados, poderá preferir o passo cautelar de começar por encerrar os servidores durante um período de tempo. Este fornecem tempo para se certificar de que existem não existem problemas comunicados que exijam reiniciar estes servidores para a continuidade do serviço enquanto estiver a investigar por que razão os clientes não estiver a utilizar o Azure Information Protection.

Depois de ter desaprovisionada seus servidores AD RMS, pode querer aproveitar a oportunidade para rever os modelos no portal do Azure. Por exemplo, convertê-las em etiquetas, consolidá-los para que os utilizadores tenham menos escolher entre ou reconfigurá-las. É também uma boa altura para publicar os modelos predefinidos. Para obter mais informações, consulte [configurar e gerir modelos do Azure Information Protection](../deploy-use/configure-policy-templates.md).

>[!IMPORTANT]
> No final desta migração, o seu cluster do AD RMS não pode ser utilizado com o Azure Information Protection e a opção "tenha a sua própria chave" (HYOK). Se optar por utilizar o HYOK para uma etiqueta do Azure Information Protection, por causa dos redirecionamentos que estão em vigor, o cluster do AD RMS que utilizar tem de ter URLs de licenciamento diferentes do que tem nos clusters que migrou.

## <a name="step-11-remove-onboarding-controls"></a>Passo 11: remover os controlos de inclusão

Quando todos os clientes existentes tiverem migrado para o Azure Information Protection, não precisa de continuar a utilizar controlos de inclusão e manter o grupo **AIPMigrated** que criou para o processo de migração. 

Remova primeiro os controlos de inclusão e, em seguida, pode eliminar o **AIPMigrated** grupo e as tarefas de implementação de software que criou para implementar os redirecionamentos.

Para remover os controlos de inclusão:

1. Numa sessão do PowerShell, ligue ao serviço Azure Rights Management e quando lhe for pedido, especifique as credenciais de administrador global:

        Connect-Aadrmservice

2. Execute o seguinte comando e introduza **Y** para confirmar:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False

3. Confirme que os controlos de inclusão já não estão definidos:

        Get-AadrmOnboardingControlPolicy

    No resultado, a opção **License** deve apresentar **False** e não é apresentado um GUID para **SecurityGroupOjbectId**

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>Passo 12: recodificar a chave de inquilino do Azure Information Protection
Este passo é necessário quando a migração estiver concluída se a sua implementação do AD RMS estava a utilizar o RMS modo criptográfico 1. Rekeying cria uma nova chave de inquilino que utiliza o RMS modo criptográfico 2. Modo criptográfico 1 é suportada para o Azure Information Protection apenas durante o processo de migração.

Também rekeying quando a migração estiver concluída ajuda a proteger a chave de inquilino do Azure Information Protection contra potenciais falhas de segurança para a sua chave de AD RMS.

Quando a recodificar a chave de inquilino do Azure Information Protection (também conhecido como "implementar a chave"), é criada uma nova chave e a chave original é arquivada. No entanto, a mover de uma chave para outra não ocorre imediatamente mas ao longo de algumas semanas. Porque não é imediata, não espere até suspeitar uma violação na chave original e recodificar a chave de inquilino do Azure Information Protection, assim que a migração estar concluída.

Para recodificar a chave de inquilino do Azure Information Protection:

- Se a sua chave de inquilino for gerida pela Microsoft: contacte o [Suporte da Microsoft](../get-started/information-support.md#to-contact-microsoft-support) e abra um **caso de suporte do Azure Information Protection com um pedido de recodificação da sua chave do Azure Information Protection após a migração a partir do AD RMS**. Tem de provar que é um administrador do inquilino do Azure Information Protection e compreender que este processo demorará vários dias a ser confirmado. São aplicáveis encargos de suporte padrão; a recodificação da chave de inquilino não é um serviço de suporte gratuito.

- Se a sua chave de inquilino for gerida por si (BYOK): no Azure Key Vault, recodifique a chave que estiver a utilizar para o inquilino do Azure Information Protection e, em seguida, execute o cmdlet [Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey) novamente para especificar o novo URL da chave. 

Para obter mais informações sobre a gestão da chave de inquilino do Azure Information Protection, veja [Operações para a chave de inquilino do Azure Rights Management](../deploy-use/operations-tenant-key.md).

## <a name="next-steps"></a>Passos seguintes

Agora que concluiu a migração, veja o [plano de implementação](deployment-roadmap.md) para identificar quaisquer outras tarefas de implementação que tenha de efetuar.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
