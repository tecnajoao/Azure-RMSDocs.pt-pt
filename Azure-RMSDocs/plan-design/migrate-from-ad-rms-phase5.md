---
title: "Migrar do AD RMS para o Azure Information Protection – fase 5"
description: "Fase 5 da migração do AD RMS para o Azure Information Protection, que abrange os passos 10 a 12 de Migrar do AD RMS para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/17/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 85b00b8f1e6bd8612b4bd49770e2ff4a934d3177
ms.sourcegitcommit: 52ad844cd42479a56b1ae0e56ba0614f088d8a1a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/20/2017
---
# <a name="migration-phase-5---post-migration-tasks"></a>Fase 5 da migração – tarefas de pós-migração

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*


Utilize as seguintes informações para a Fase 5 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem os passos 10 a 12 de [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-10-deprovison-ad-rms"></a>Passo 10: desaprovisionar o AD RMS

Remova o Ponto de Ligação de Serviço (SCP) do Active Directory para impedir que os computadores detetem a sua infraestrutura da Gestão de Direitos no local. Isto é opcional para os clientes existentes que migraram devido ao redirecionamento que foi configurado no registo (por exemplo, ao executar o script de migração). No entanto, remover o SCP impede que novos clientes e potenciais serviços e ferramentas relacionados com o RMS localizem o SCP quando a migração estiver concluída e que todas as ligações sejam direcionadas para o serviço Azure Rights Management. 

Para remover o SCP, garanta que tem sessão iniciada como administrador da empresa do domínio e, em seguida, utilize o seguinte procedimento:

1. Na consola Serviços de Gestão de Direitos do Active Directory, clique com o botão direito do rato no cluster do AD RMS e, em seguida, clique em **Propriedades**.

2. Clique no separador **SCP**.

3. Selecione a caixa de verificação **Alterar SCP**.

4. Selecione **Remover SCP atual** e, em seguida, clique em **OK**.

Agora monitorize a atividade dos seus servidores do AD RMS, por exemplo, ao verificar os [pedidos no relatório de Estado de Funcionamento do Sistema](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), a [tabela ServiceRequest](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) ou a [auditoria de acesso de utilizador a conteúdos protegidos](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). 

Quando tiver confirmado que os clientes RMS já não estão a comunicar com estes servidores e que os clientes estão a utilizar o Azure Information Protection com êxito, pode remover a função de servidor do AD RMS destes servidores. Se estiver a utilizar servidores dedicados, poderá preferir o passo cautelar de começar por encerrar os servidores durante um período de tempo para se certificar de que não existem problemas comunicados que exijam reiniciar estes servidores para assegurar a continuidade do serviço enquanto estiver a investigar por que razão os clientes não estão a utilizar o Azure Information Protection.

Depois de ter desaprovisionado os seus servidores do AD RMS, pode aproveitar a oportunidade para rever os seus modelos no portal clássico do Azure e consolidá-los para que os utilizadores tenham menos opções por onde escolher, reconfigurá-los ou até mesmo adicionar novos modelos. É também uma boa altura para publicar os modelos predefinidos. Para obter mais informações, veja [Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md).

>[!IMPORTANT]
> No final desta migração, o seu cluster do AD RMS não pode ser utilizado com o Azure Information Protection e a opção "tenha a sua própria chave" (HYOK). Se optar por utilizar o HYOK para uma etiqueta do Azure Information Protection, por causa dos redirecionamentos que estão em vigor, o cluster do AD RMS que utilizar tem de ter URLs de licenciamento diferentes do que tem nos clusters que migrou.

## <a name="step-11-remove-onboarding-controls"></a>Passo 11: remover os controlos de inclusão

Quando todos os clientes existentes tiverem migrado para o Azure Information Protection, não precisa de continuar a utilizar controlos de inclusão e manter o grupo **AIPMigrated** que criou para o processo de migração. 

Remova os controlos de inclusão primeiro e, em seguida, pode eliminar o grupo **AIPMigrated** e qualquer tarefa de implementação de software que criou para implementar os redirecionamentos.

Para remover os controlos de inclusão:

1. Numa sessão do PowerShell, ligue ao serviço Azure Rights Management e quando lhe for pedido, especifique as credenciais de administrador global:

        Connect-Aadrmservice

2. Execute o seguinte comando e introduza **Y** para confirmar:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False

3. Confirme que os controlos de inclusão já não estão definidos:

        Get-AadrmOnboardingControlPolicy

    No resultado, a opção **License** deve apresentar **False** e não é apresentado um GUID para **SecurityGroupOjbectId**

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>Passo 12: recodificar a chave de inquilino do Azure Information Protection
Este passo é obrigatório quando a migração estiver concluída se a sua implementação do AD RMS estava a utilizar o Modo Criptográfico 1 do RMS, porque a recodificação cria uma nova chave de inquilino que utiliza o Modo Criptográfico 2 do RMS. A utilização do Azure RMS com o Modo Criptográfico 1 é suportada apenas durante o processo de migração.

Este passo é opcional, mas é recomendado quando a migração estiver concluída, mesmo que estivesse em execução no Modo Criptográfico 2 do RMS. Neste cenário, a recodificação ajuda a proteger a sua chave de inquilino do Azure Information Protection contra potenciais falhas de segurança na sua chave do AD RMS.

Quando recodificar a chave de inquilino do Azure Information Protection (também conhecido como "implementar a chave"), é criada uma nova chave e a chave original é arquivada. No entanto, uma vez que a mudança de uma chave para outra não é imediata, mas sim um processo de algumas semanas, não espere até suspeitar que existe uma falha na chave original e recodifique a chave de inquilino do Azure Information Protection assim que a migração estiver concluída.

Para recodificar a chave de inquilino do Azure Information Protection:

- Se a sua chave de inquilino for gerida pela Microsoft: contacte o [Suporte da Microsoft](../get-started/information-support.md#to-contact-microsoft-support) e abra um **caso de suporte do Azure Information Protection com um pedido de recodificação da sua chave do Azure Information Protection após a migração a partir do AD RMS**. Tem de provar que é um administrador do inquilino do Azure Information Protection e compreender que este processo demorará vários dias a ser confirmado. São aplicáveis encargos de suporte padrão; a recodificação da chave de inquilino não é um serviço de suporte gratuito.

- Se a sua chave de inquilino for gerida por si (BYOK): no Azure Key Vault, recodifique a chave que estiver a utilizar para o inquilino do Azure Information Protection e, em seguida, execute o cmdlet [Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey) novamente para especificar o novo URL da chave. 

Para obter mais informações sobre a gestão da chave de inquilino do Azure Information Protection, veja [Operações para a chave de inquilino do Azure Rights Management](../deploy-use/operations-tenant-key.md).

## <a name="next-steps"></a>Passos seguintes

Agora que concluiu a migração, veja o [plano de implementação](deployment-roadmap.md) para identificar quaisquer outras tarefas de implementação que tenha de efetuar.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
