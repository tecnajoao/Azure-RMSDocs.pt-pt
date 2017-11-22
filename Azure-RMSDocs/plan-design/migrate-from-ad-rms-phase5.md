---
title: "Migrar do AD RMS para o Azure Information Protection – fase 5"
description: "Fase 5 da migração do AD RMS para o Azure Information Protection, que abrange os passos 10 a 12 de Migrar do AD RMS para o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 2cf486a5319d6addcd150351054d44db62c250b0
ms.sourcegitcommit: 9b975e66b12a3836003c6c4de139ded4bbf370bf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/21/2017
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

## <a name="step-11-complete-client-migration-tasks"></a>Passo 11: Tarefas de migração de cliente completa

Para clientes de dispositivos móveis e computadores Mac: remover os registos SRV de DNS que criou quando implementou o [extensão de dispositivo móvel do AD RMS](http://technet.microsoft.com/library/dn673574.aspx).

Quando estas alterações DNS tem propogated, estes clientes irão detetar automaticamente e começar a utilizar o serviço Azure Rights Management. No entanto, os computadores Mac que executem Office Mac cache as informações do AD RMS. Para estes computadores, este processo pode demorar até 30 dias. 

Para forçar computadores Mac para executar o processo de deteção imediatamente, na keychain, procure "adal" e elimine todas as entradas ADAL. Em seguida, execute os seguintes comandos nestes computadores:

````

rm -r ~/Library/Cache/MSRightsManagement

rm -r ~/Library/Caches/com.microsoft.RMS-XPCService

rm -r ~/Library/Caches/Microsoft\ Rights\ Management\ Services

rm -r ~/Library/Containers/com.microsoft.RMS-XPCService

rm -r ~/Library/Containers/com.microsoft.RMSTestApp

rm ~/Library/Group\ Containers/UBF8T346G9.Office/DRM.plist

killall cfprefsd

````

Quando todos os seus computadores Windows existentes tem migrado para o Azure Information Protection, não há nenhuma razão para continuar a utilizar controlos de inclusão e manter o **AIPMigrated** grupo que criou para o processo de migração. 

Remova primeiro os controlos de inclusão e, em seguida, pode eliminar o **AIPMigrated** grupo e qualquer método de implementação de software que criou para implementar os scripts de migração.

Para remover os controlos de inclusão:

1. Numa sessão do PowerShell, ligue ao serviço Azure Rights Management e quando lhe for pedido, especifique as credenciais de administrador global:

        Connect-Aadrmservice

2. Execute o seguinte comando e introduza **Y** para confirmar:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False
    
    Tenha em atenção que este comando remove quaisquer imposição de licença para o serviço de proteção do Azure Rights Management, para que todos os computadores possam proteger documentos e e-mails.

3. Confirme que os controlos de inclusão já não estão definidos:

        Get-AadrmOnboardingControlPolicy

    No resultado, a opção **License** deve apresentar **False** e não é apresentado um GUID para **SecurityGroupOjbectId**

Por fim, se estiver a utilizar o Office 2010 e tiver ativado o **gestão de modelos de política de direitos de RMS do AD (automatizada)** tarefas na biblioteca do Programador de tarefas do Windows, desative esta tarefa porque não está a ser utilizado pelas informações do Azure Cliente de proteção. Esta tarefa estiver ativada, normalmente, utilizando a política de grupo e suporta uma implementação de AD RMS. Pode encontrar esta tarefa na seguinte localização: **Microsoft** > **Windows** > **cliente do Active Directory Rights Management Services**

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>Passo 12: recodificar a chave de inquilino do Azure Information Protection

Este passo é recomendado quando a migração estiver concluída se a sua implementação do AD RMS estava a utilizar o RMS modo criptográfico 1. Rekeying resulta na proteção que utiliza o RMS modo criptográfico 2. 

Mesmo que a implementação do AD RMS estava a utilizar o modo criptográfico 2, recomendamos que execute este passo porque uma nova chave ajuda a proteger o seu inquilino contra potenciais falhas de segurança para a sua chave de AD RMS.

No entanto, não recodificar se foram a utilizar o Exchange Online com o AD RMS. Exchange Online não suporta a alteração modos criptográficos. 

Quando a recodificar a chave de inquilino do Azure Information Protection (também conhecido como "implementar a chave"), a chave atualmente ativa é arquivada e Azure Information Protection começa a utilizar uma chave diferente que especificar. Esta chave diferente pode ser uma nova chave que criar no Cofre de chaves do Azure ou a chave predefinida que foi criada automaticamente para o seu inquilino.

Mover de uma chave para outra não ocorre imediatamente mas ao longo de algumas semanas. Porque não é imediata, não espere até suspeitar uma violação na chave original, mas efetue este passo, assim que a migração estar concluída.

Para recodificar a chave de inquilino do Azure Information Protection:

- **Se a chave de inquilino é gerida pela Microsoft**: executar o cmdlet do PowerShell [conjunto AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) e especificar o identificador da chave para a chave que foi criado automaticamente para o seu inquilino. Pode identificar o valor para especificar executando o [Get-AadrmKeys](/powershell/module/aadrm/get-aadrmkeys) cmdlet. A chave que foi criada automaticamente para o seu inquilino tem a data de criação mais antiga, para que possa identificá-lo utilizando o seguinte comando:
    
        (Get-AadrmKeys) | Sort-Object CreationTime | Select-Object -First 1

- **Se a sua chave de inquilino é gerida por si (BYOK)**: no Cofre de chaves do Azure, repita o processo de criação de chaves para o seu inquilino do Azure Information Protection e, em seguida, execute o [utilize AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey) cmdlet novamente para especificar o URI para esta chave de novo. 

Para obter mais informações sobre a gestão da chave de inquilino do Azure Information Protection, veja [Operações para a chave de inquilino do Azure Rights Management](../deploy-use/operations-tenant-key.md).


## <a name="next-steps"></a>Passos seguintes

Agora que concluiu a migração, veja o [plano de implementação](deployment-roadmap.md) para identificar quaisquer outras tarefas de implementação que tenha de efetuar.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
