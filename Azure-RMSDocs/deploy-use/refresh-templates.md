---
title: "Atualizar os modelos do Azure RMS – AIP"
description: "Quando utiliza o serviço Azure Rights Management, os modelos são automaticamente transferidos para computadores cliente para os utilizadores poderem selecioná-los a partir das suas aplicações. No entanto, poderá ter de efetuar passos adicionais se fizer alterações aos modelos."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6f02bffa99719d5cd987bc0fa9c84baabe191ec5
ms.sourcegitcommit: 2358f76f9a039daff7d70ea68967a45362d3da35
translationtype: HT
---
# <a name="refreshing-templates-for-users"></a>Atualizar modelos para os utilizadores

>*Aplica-se a: Azure Information Protection, Office 365*

Quando utiliza o serviço Azure Rights Management do Azure Information Protection, os modelos são automaticamente transferidos para computadores cliente para os utilizadores poderem selecioná-los a partir das suas aplicações. No entanto, poderá ter de efetuar passos adicionais se fizer alterações aos modelos:

|Aplicação ou serviço|Como os modelos são atualizados depois das alterações|
|--------------------------|---------------------------------------------|
|Exchange Online<br /><br />Aplicável a regras de transporte, regras de DLP e ao Outlook Web App|Configuração manual necessária para atualizar os modelos.<br /><br />Para obter os passos de configuração, consulte a secção [Apenas para o Exchange Online: como configurar o Exchange para transferir modelos personalizados modificados](#exchange-online-only-how-to-configure-exchange-to-download-changed-custom-templates).|
|Cliente do Azure Information Protection|Atualizado automaticamente sempre que a política do Azure Information Protection é atualizada no cliente:<br /><br /> - Quando abre uma aplicação do Office que suporta a barra do Azure Information Protection. <br /><br /> - Quando clica com o botão direito do rato para classificar e proteger um ficheiro ou uma pasta. <br /><br /> - Quando executa os cmdlets do PowerShell para etiquetagem e proteção (Get-AIPFileStatus e Set-AIPFileLabel).<br /><br /> - A cada 24 horas.<br /><br /> Além disso, uma vez que o cliente do Azure Information Protection está totalmente integrado no Office, todos os modelos atualizados do Office 2016 ou do Office 2013 também serão atualizados no cliente do Azure Information Protection.|
|Office 2016 e Office 2013<br /><br />Aplicação de partilha RMS para Windows|Atualizados automaticamente – com base numa agenda:<br /><br />- Para estas versões posteriores do Office: o intervalo de atualização predefinido é de sete dias.<br /><br />- Para a aplicação de partilha RMS para Windows: a partir da versão 1.0.1784.0, o intervalo de atualização predefinido é de um dia. As versões anteriores têm um intervalo de atualização predefinido de 7 dias.<br /><br />Para forçar uma atualização mais cedo do que a agendada, veja a secção [Office 2016, Office 2013 e aplicação de partilha RMS para Windows: como forçar uma atualização de um modelo personalizado modificado](#office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template).|
|Office 2010|Atualizado automaticamente quando os utilizadores terminam sessão no Windows, iniciam sessão novamente e esperam até uma hora.|
|Exchange no local com o conector Rights Management<br /><br />Aplicável a regras de transporte e ao Outlook Web App|Atualizados automaticamente – não existem passos adicionais necessários. No entanto, o Outlook Web App coloca a IU em cache durante um dia.|
|Office 2016 para Mac|Atualizados automaticamente – não existem passos adicionais necessários.|
|Aplicação de partilha RMS para computadores Mac|Atualizados automaticamente – não existem passos adicionais necessários.|


## <a name="exchange-online-only-how-to-configure-exchange-to-download-changed-custom-templates"></a>Apenas para Exchange Online: como configurar o Exchange para transferir modelos personalizados modificados
Se já tiver configurado a Gestão de Direitos de Informação (IRM) para o Exchange Online, os utilizadores não poderão transferir os modelos personalizados até fazer as seguintes alterações com o Windows PowerShell no Exchange Online.

> [!NOTE]
> Para mais informações sobre como utilizar o Windows PowerShell no Exchange Online, consulte [Utilizar o PowerShell com o Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

Tem de efetuar este procedimento sempre que alterar um modelo.

### <a name="to-update-templates-for-exchange-online"></a>Para atualizar modelos para o Exchange Online

1.  Com o Windows PowerShell no Exchange Online, ligue-se ao serviço:

    1.  Forneça o nome de utilizador e a palavra-passe do Office 365:

        ```
        $UserCredential = Get-Credential
        ```

    2.  Execute os dois comandos seguintes para ligar ao serviço Exchange Online:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Utilize o cmdlet [Import-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) para voltar a importar o domínio de publicação fidedigno (TPD) do Azure RMS:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Por exemplo, se o nome TPD for **RMS Online – 1** (nome típico para muitas organizações), introduza: **Import-RMSTrustedPublishingDomain -Name "RMS Online – 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > Para verificar o seu nome TPD, pode utilizar o cmdlet [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx).

3.  Para confirmar que os modelos foram importados com êxito, aguarde alguns minutos e, em seguida, execute o cmdlet [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) e defina o Tipo para Todos. Por exemplo:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > É útil guardar uma cópia do ficheiro de saída para poder copiar facilmente os nomes dos modelos ou os GUIDs se arquivar um modelo posteriormente.

4.  Para cada modelo importado que pretenda disponibilizar no Outlook Web App, tem de utilizar o cmdlet [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) e definir o Tipo para Distribuído:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Como o Outlook Web Access coloca a IU em cache durante 24 horas, os utilizadores não poderão ver o novo modelo até ao dia seguinte.

Além disso, se arquivar um modelo (personalizado ou predefinido) e utilizar o Exchange Online com o Office 365, os utilizadores irão continuar a ver os modelos arquivados se utilizarem o Outlook Web App ou os dispositivos móveis que utilizam o Protocolo do Exchange ActiveSync.

Para os utilizadores deixarem de ver estes modelos, ligue-se ao serviço com o Windows PowerShell no Exchange Online e, em seguida, utilize o cmdlet [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) ao executar o seguinte comando:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

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

    **Caminho do registo:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\<*MicrosoftRMS_FQDN*>\Template

    **Tipo:** REG_SZ

    **Valor:** LastUpdatedTime

    > [!TIP]
        > No caminho do registo, *MicrosoftRMS_FQDN*> refere-se ao seu FQDN do serviço Microsoft RMS. Se quiser verificar este valor:

    > 1.  Execute o cmdlet [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) para o Azure RMS. Se ainda não instalou o módulo do Windows PowerShell para o Azure RMS, consulte [Instalar o Windows PowerShell para o Azure Rights Management](install-powershell.md).
    > 2.  A partir da saída, identifique o valor **LicensingIntranetDistributionPointUrl**.
    > 
    >     Por exemplo: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  No valor, remova **https://** e **/_wmcs/licensing** desta cadeia. O valor restante é o seu FQDN do serviço Microsoft RMS. No nosso exemplo, o FQDN do serviço Microsoft RMS teria o seguinte valor:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Elimine a seguinte pasta e todos os ficheiros nela contidos: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Reinicie as suas aplicações do Office e instâncias do Explorador de Ficheiros.


## <a name="see-also"></a>Consulte Também
[Configurar modelos personalizados para o Azure Rights Management](configure-custom-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]