---
title: Migrar do AD RMS para o Azure Information Protection – fase 5
description: Fase 5 da migração do AD RMS para o Azure Information Protection, que abrange os passos 10 a 12 de Migrar do AD RMS para o Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9cb5f30f5af9031829b1d416b34da45170cd8db4
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491376"
---
# <a name="migration-phase-5---post-migration-tasks"></a>Fase 5 da migração – tarefas de pós-migração

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Utilize as seguintes informações para a Fase 5 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem os passos 10 a 12 de [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-10-deprovision-ad-rms"></a>Passo 10: Desaprovisionar o AD RMS

Remova o Ponto de Ligação de Serviço (SCP) do Active Directory para impedir que os computadores detetem a sua infraestrutura da Gestão de Direitos no local. Isto é opcional para os clientes existentes que migraram devido ao redirecionamento que foi configurado no registo (por exemplo, ao executar o script de migração). No entanto, remover o SCP impede que novos clientes e ferramentas e serviços potencialmente relacionados com o RMS localizem o SCP quando a migração estiver concluída. Neste momento, todas as ligações de computador devem ir para o serviço Azure Rights Management. 

Para remover o SCP, garanta que tem sessão iniciada como administrador da empresa do domínio e, em seguida, utilize o seguinte procedimento:

1. Na consola Serviços de Gestão de Direitos do Active Directory, clique com o botão direito do rato no cluster do AD RMS e, em seguida, clique em **Propriedades**.

2. Clique no separador **SCP**.

3. Selecione a caixa de verificação **Alterar SCP**.

4. Selecione **Remover SCP atual** e, em seguida, clique em **OK**.

Agora monitorize servidores do AD RMS para a atividade. Por exemplo, confira o [pedidos no relatório do Estado de funcionamento do sistema](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), o [tabela ServiceRequest](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) ou [auditar o acesso de utilizador a conteúdo protegido](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). 

Quando tiver confirmado que os clientes RMS já não estão a comunicar com estes servidores e que os clientes estão a utilizar o Azure Information Protection com êxito, pode remover a função de servidor do AD RMS destes servidores. Se estiver a utilizar servidores dedicados, poderá preferir o passo cautelar de começar por encerrar os servidores durante um período de tempo. Este lhe dará tempo para se certificar de que não existem não existem problemas comunicados que exijam reiniciar estes servidores para continuidade do serviço enquanto estiver a investigar por que os clientes não estiver a utilizar do Azure Information Protection.

Depois de ter desaprovisionado os servidores do AD RMS, pode querer aproveitar a oportunidade para rever os seus modelos no portal do Azure. Por exemplo, convertê-los em etiquetas, consolidá-los para que os utilizadores tenham menos por onde escolher entre ou reconfigurá-los. É também uma boa altura para publicar os modelos predefinidos. Para obter mais informações, consulte [configurando e gerenciando modelos do Azure Information Protection](./configure-policy-templates.md).

>[!IMPORTANT]
> No final desta migração, o seu cluster do AD RMS não pode ser utilizado com o Azure Information Protection e a opção "tenha a sua própria chave" (HYOK). Se optar por utilizar o HYOK para uma etiqueta do Azure Information Protection, por causa dos redirecionamentos que estão em vigor, o cluster do AD RMS que utilizar tem de ter URLs de licenciamento diferentes do que tem nos clusters que migrou.

## <a name="step-11-complete-client-migration-tasks"></a>Passo 11: Tarefas de migração de cliente concluída

Para clientes de dispositivos móveis e computadores Mac: remover os registos SRV de DNS que criou quando implementou o [extensão de dispositivo móvel do AD RMS](http://technet.microsoft.com/library/dn673574.aspx).

Quando estas alterações DNS tem propogated, estes clientes irão detetar automaticamente e começar a utilizar o serviço Azure Rights Management. No entanto, computadores Mac que executem Office Mac colocar em cache as informações do AD RMS. Para estes computadores, este processo pode demorar até 30 dias. 

Para forçar computadores de Mac a executar o processo de deteção imediatamente, na keychain, procure "adal" e elimine todas as entradas da ADAL. Em seguida, execute os seguintes comandos nestes computadores:

````

rm -r ~/Library/Cache/MSRightsManagement

rm -r ~/Library/Caches/com.microsoft.RMS-XPCService

rm -r ~/Library/Caches/Microsoft\ Rights\ Management\ Services

rm -r ~/Library/Containers/com.microsoft.RMS-XPCService

rm -r ~/Library/Containers/com.microsoft.RMSTestApp

rm ~/Library/Group\ Containers/UBF8T346G9.Office/DRM.plist

killall cfprefsd

````

Quando todos os seus computadores Windows existentes tem migrado para o Azure Information Protection, não há motivo para continuar a utilizar controlos de inclusão e manter o **AIPMigrated** grupo que criou para o processo de migração. 

Remova os controlos de inclusão primeiro e, em seguida, pode eliminar a **AIPMigrated** grupo e qualquer método de implementação de software que criou para implementar os scripts de migração.

Para remover os controlos de inclusão:

1. Numa sessão do PowerShell, ligue ao serviço Azure Rights Management e quando lhe for pedido, especifique as credenciais de administrador global:

        Connect-Aadrmservice

2. Execute o seguinte comando e introduza **Y** para confirmar:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False
    
    Tenha em atenção que este comando remove quaisquer imposição de licença para o serviço de proteção do Azure Rights Management, para que todos os computadores possam proteger documentos e e-mails.

3. Confirme que os controlos de inclusão já não estão definidos:

        Get-AadrmOnboardingControlPolicy

    No resultado, a opção **License** deve apresentar **False** e não é apresentado um GUID para **SecurityGroupOjbectId**

Por fim, se estiver a utilizar o Office 2010 e tiver ativado o **gestão de modelos de política de direitos de RMS do AD (automatizada)** de tarefas na biblioteca do agendador de tarefas do Windows, desative esta tarefa porque não está a ser utilizado pelas informações do Azure Cliente de proteção. Esta tarefa normalmente é ativada pela política de grupo e suporta uma implementação do AD RMS. Pode encontrar esta tarefa na seguinte localização: **Microsoft** > **Windows** > **Active Directory Rights Management Services Client**

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>Passo 12: Recodificar a chave de inquilino do Azure Information Protection

Este passo é recomendado quando a migração estiver concluída se a sua implementação do AD RMS estava a utilizar o RMS modo criptográfico 1. Recodificação resultados na proteção que utiliza o RMS modo criptográfico 2. 

Mesmo que sua implementação do AD RMS estava a utilizar o modo criptográfico 2, recomendamos ainda que efetuar este passo porque uma nova chave ajuda a proteger o seu inquilino de potenciais falhas de segurança para a chave do AD RMS.

Quando recodificar a chave de inquilino do Azure Information Protection (também conhecido como "implementar a chave"), a chave ativa no momento é arquivada e Azure Information Protection começa a utilizar uma chave diferente que especificar. Esta chave diferente pode ser uma nova chave que criar no Azure Key Vault ou a chave predefinida que foi criada automaticamente para o seu inquilino.

Mover de uma chave para outra não ocorre imediatamente mas ao longo de algumas semanas. Porque não é imediata, não espere até suspeitar que uma violação de chave original mas este passo, assim como a migração estiver concluída.

Para recodificar a chave de inquilino do Azure Information Protection:

- **Se a sua chave de inquilino for gerida pela Microsoft**: execute o cmdlet do PowerShell [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) e especifique o identificador de chave da chave que foi criado automaticamente para o seu inquilino. Pode identificar o valor a especificar ao executar o [Get-AadrmKeys](/powershell/module/aadrm/get-aadrmkeys) cmdlet. A chave que foi criada automaticamente para o seu inquilino tem a data de criação mais antiga, para que possa identificá-lo utilizando o seguinte comando:
    
        (Get-AadrmKeys) | Sort-Object CreationTime | Select-Object -First 1

- **Se a sua chave de inquilino for gerida por si (BYOK)**: no Azure Key Vault, repita o processo de criação da chave para o seu inquilino do Azure Information Protection e, em seguida, execute o [Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey) cmdlet novamente para especificar o URI de Esta nova chave. 

Para obter mais informações sobre como gerir a sua chave de inquilino do Azure Information Protection, consulte [operações para a chave de inquilino do Azure Information Protection](./operations-tenant-key.md).


## <a name="next-steps"></a>Passos Seguintes

Agora que concluiu a migração, veja o [plano de implementação](deployment-roadmap.md) para identificar quaisquer outras tarefas de implementação que tenha de efetuar.

