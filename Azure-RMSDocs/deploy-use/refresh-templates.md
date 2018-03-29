---
title: Atualizar os modelos do Azure RMS – AIP
description: Quando utiliza o serviço Azure Rights Management, os modelos são automaticamente transferidos para computadores cliente para os utilizadores poderem selecioná-los a partir das suas aplicações. No entanto, poderá ter de efetuar passos adicionais se fizer alterações aos modelos.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5bbefccbcf5d529d64b613220013a0988fa4808a
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="refreshing-templates-for-users-and-services"></a>Atualizar modelos para os utilizadores e os serviços

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Quando utiliza o serviço Azure Rights Management do Azure Information Protection, os modelos são automaticamente transferidos para computadores cliente para os utilizadores poderem selecioná-los a partir das suas aplicações. No entanto, poderá ter de efetuar passos adicionais se fizer alterações aos modelos:

|Aplicação ou serviço|Como os modelos são atualizados depois das alterações|
|--------------------------|---------------------------------------------|
|Exchange Online<br /><br />Aplicável a regras de transporte e ao Outlook Web App |Atualizados automaticamente dentro de uma hora - não existem passos adicionais necessários.<br /><br />Este é o caso, se estiver a utilizar [encriptação de mensagens do Office 365 com as novas capacidades](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Se anteriormente tiver configurado o Exchange Online utilizar o serviço Azure Rights Management ao importar o domínio de publicação fidedigno (TPD), utilize o mesmo conjunto de instruções para ativar as novas funcionalidades no Exchange Online.|
|Cliente do Azure Information Protection|Atualizado automaticamente sempre que a política do Azure Information Protection é atualizada no cliente:<br /><br /> - Quando abre uma aplicação do Office que suporta a barra do Azure Information Protection. <br /><br /> - Quando clica com o botão direito do rato para classificar e proteger um ficheiro ou uma pasta. <br /><br /> - Quando executa os cmdlets do PowerShell para etiquetagem e proteção (Get-AIPFileStatus e Set-AIPFileLabel).<br /><br /> -Quando é iniciado o serviço de análise de proteção de informações do Azure e a política local, é mais antiga do que uma hora. Além disso, o serviço de análise verifica a existência de alterações a cada hora e utiliza estas alterações para o próximo ciclo de análise.<br /><br /> - A cada 24 horas.<br /><br /> Além disso, uma vez que o cliente do Azure Information Protection está totalmente integrado no Office, todos os modelos atualizados do Office 2016 ou do Office 2013 também serão atualizados no cliente do Azure Information Protection.|
|Office 2016 e Office 2013<br /><br />Aplicação de partilha RMS para Windows|Atualizados automaticamente – com base numa agenda:<br /><br />- Para estas versões posteriores do Office: o intervalo de atualização predefinido é de sete dias.<br /><br />- Para a aplicação de partilha RMS para Windows: a partir da versão 1.0.1784.0, o intervalo de atualização predefinido é de um dia. As versões anteriores têm um intervalo de atualização predefinido de 7 dias.<br /><br />Para forçar uma atualização mais cedo do que a agendada, veja a secção [Office 2016, Office 2013 e aplicação de partilha RMS para Windows: como forçar uma atualização de um modelo personalizado modificado](#office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template).|
|Office 2010|Atualizado automaticamente quando os utilizadores terminam sessão no Windows, iniciam sessão novamente e esperam até uma hora.|
|Exchange no local com o conector Rights Management<br /><br />Aplicável a regras de transporte e ao Outlook Web App|Atualizados automaticamente – não existem passos adicionais necessários. No entanto, o Outlook Web App coloca a IU em cache durante um dia.|
|Office 2016 para Mac|Atualizados automaticamente – não existem passos adicionais necessários.|
|Aplicação de partilha RMS para computadores Mac|Atualizados automaticamente – não existem passos adicionais necessários.|

Quando as aplicações de cliente precisam de transferir modelos (inicialmente ou atualizados para alterações), esteja preparado para aguardar até 15 minutos antes de a transferência estar concluída e os modelos novos ou atualizados estarem totalmente operacionais. O tempo em questão pode variar devido a fatores como o tamanho e a complexidade da configuração do modelo e a conectividade de rede. 

## <a name="office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template"></a>Office 2016, Office 2013 e aplicação de partilha RMS para Windows: como forçar uma atualização de um modelo personalizado modificado
Ao editar o registo nos computadores ao executar o Office 2016, Office 2013 ou a aplicação de partilha Rights Management (RMS) para Windows, pode alterar o agendamento automático para os modelos modificados serem atualizados nos computadores com mais frequência do que o respetivo valor predefinido. Também pode forçar uma atualização imediata ao eliminar os dados existentes num valor de registo.

> [!WARNING]
> A utilização incorreta do Editor de Registo poderá causar problemas graves que exijam a reinstalação do sistema operativo. A Microsoft não garante que consiga resolver os problemas resultantes da utilização incorreta do Editor de Registo. A utilização do Editor de Registo é da exclusiva responsabilidade do utilizador.

### <a name="to-change-the-automatic-schedule"></a>Para alterar o agendamento automático

1.  Através de um editor de registo, crie e defina um dos seguintes valores do registo:

    - Para definir uma frequência de atualização em dias (mínimo de 1 dia): crie um novo valor de registo com o nome **TemplateUpdateFrequency** e defina um valor inteiro para os dados, que especifica a frequência em dias para transferir quaisquer alterações a um modelo transferido. Utilize as seguintes informações para localizar o caminho do registo para criar este novo valor de registo.

        **Caminho do registo:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Tipo:** REG_DWORD

        **Valor:** TemplateUpdateFrequency

    - Para definir uma frequência de atualização em segundos (mínimo de 1 segundo): crie um novo valor de registo com o nome **TemplateUpdateFrequencyInSeconds** e defina um valor inteiro para os dados, que especifica a frequência em segundos para transferir alterações para um modelo transferido. Utilize as seguintes informações para localizar o caminho do registo para criar este novo valor de registo.

        **Caminho do registo:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Tipo:** REG_DWORD

        **Valor:** TemplateUpdateFrequencyInSeconds

    Certifique-se de que cria e configura um destes valores do registo, não ambos. Se ambos estiverem presentes, o **TemplateUpdateFrequency** será ignorado.

2.  Se quiser forçar uma atualização imediata dos modelos, avance para o procedimento seguinte. Caso contrário, reinicie as suas aplicações do Office e instâncias do Explorador de Ficheiros agora.

### <a name="to-force-an-immediate-refresh"></a>Para forçar uma atualização imediata

1.  Através de um editor de registo, elimine os dados do valor **LastUpdatedTime**. Por exemplo, os dados poderão apresentar **2015-04-20T15:52**. Elimine 2015-04-20T15:52 para não serem apresentados dados. Utilize as seguintes informações para localizar o caminho do registo para eliminar os dados deste valor de registo.

    **Caminho do registo:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\\<*MicrosoftRMS_FQDN*> \Template\\ < *user_alias*>

    **Tipo:** REG_SZ

    **Valor:** LastUpdatedTime

    > [!TIP]
    > No caminho do registo, *MicrosoftRMS_FQDN*> refere-se ao seu FQDN do serviço Microsoft RMS. Se quiser verificar este valor:

    > Execute o cmdlet [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) para o Azure RMS. Se já ainda não instalou o módulo Windows PowerShell para o Azure RMS, consulte [instalar o módulo do AADRM PowerShell](install-powershell.md).
    >
    > A partir da saída, identifique o valor **LicensingIntranetDistributionPointUrl**.
    >
    > Por exemplo: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 
    > No valor, remova **https://** e **/_wmcs/licensing** desta cadeia. O valor restante é o seu FQDN do serviço Microsoft RMS. No nosso exemplo, o FQDN do serviço Microsoft RMS teria o seguinte valor:
    >
    >**5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Elimine a seguinte pasta e todos os ficheiros nela contidos: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Reinicie as suas aplicações do Office e instâncias do Explorador de Ficheiros.


## <a name="see-also"></a>Veja Também
[Configurar e gerir modelos de política do Azure Information Protection](../deploy-use/configure-policy-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
