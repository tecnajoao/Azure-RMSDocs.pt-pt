---
title: Configurar a IRM do Exchange Online para o serviço Azure Rights Management do Azure Information Protection
description: Informações e instruções para os administradores configurar o Exchange Online para o serviço Azure Rights Management quando o inquilino do Office 365 não suporta as novas funcionalidades da encriptação de mensagens do Office 365.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/22/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ''
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 022eb960ef58e69c0a4c2d8a76962ed792a9ed38
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="exchange-online-irm-configuration-when-you-have-imported-a-trusted-publishing-domain"></a>Configuração de IRM do Exchange Online quando importou um domínio de publicação fidedigno

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize estas instruções apenas se tiver configurado anteriormente Exchange Online para IRM ao importar o domínio de publicação fidedigno (TPD) e tem de conseguir desencriptar mensagens de correio eletrónico que anteriormente foram encriptadas.

Se nenhuma destas condições se aplicar ao utilizador, não utilize estas instruções e, em vez disso, utilize instruções do [configurar novas capacidades de encriptação de mensagens do Office 365 desenvolvidas Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e).

## <a name="exchange-online-irm-configuration-if-you-have-an-imported-tpd"></a>Configuração de IRM do Exchange Online, se tiver um TPD importado

Para configurar o Exchange Online para suportar o serviço Azure Rights Management, tem de configurar o serviço de gestão de direitos de informação (IRM) para o Exchange Online. Para isso, tem de utilizar o Windows PowerShell (não é necessário instalar um módulo separado) e executar os [comandos do PowerShell para o Exchange Online](https://technet.microsoft.com/library/jj200677.aspx).

> [!NOTE]
> Até que a Microsoft efetua a migração de inquilino do Office 365, não é possível configurar o Exchange Online para suportar o serviço Azure Rights Management, se estiver a utilizar uma chave de inquilino gerida pelo cliente (BYOK) para o Azure Information Protection, em vez da configuração predefinida de uma Chave de inquilino gerida pela Microsoft.
>
> Se tentar configurar o Exchange Online quando o serviço Azure Rights Management está a utilizar o BYOK, o comando para importar a chave (passo 5 no procedimento seguinte) falhará com a mensagem de erro **[FailureCategory=Cmdlet-FailedToGetTrustedPublishingDomainFromRmsOnlineException]**.

Os passos seguintes fornecem um conjunto típico de comandos que executaria para ativar o Exchange Online utilizar o serviço Azure Rights Management para este cenário:

1.  Se esta é a primeira vez que utiliza o Windows PowerShell para o Exchange Online no seu computador, tem de configurar o Windows PowerShell para executar scripts assinados. Inicie sessão do Windows PowerShell através da opção **Executar como administrador** e, em seguida, escreva:

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

2.  Na sessão do Windows PowerShell, inicie sessão no Exchange Online com uma conta ativada para acesso remoto à Shell. Por predefinição, todas as contas criadas no Exchange Online têm o acesso remoto à Shell ativado, embora possa desativar (e ativar) esta funcionalidade através do comando [Set-User &lt;UserIdentity&gt; -RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx).

    Para iniciar sessão, escreva:

    ```
    $UserCredential = Get-Credential
    ```
    Na caixa de diálogo **Pedido de Credencial do Windows PowerShell**, forneça o seu nome de utilizador e palavra-passe do Office 365.

3.  Execute os dois comandos seguintes para ligar ao serviço Exchange Online:

    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    ```
    Import-PSSession $Session
    ```

4.  Especifique a localização da chave de inquilino do Azure Information Protection, em conformidade com a localização onde foi criado o inquilino da sua organização:

    Para a América do Norte

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Para a Europa:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Para a Ásia:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Para a América do Sul:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Para o Office 365 Administração Pública (Government Community Cloud):

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc"
    ```

5.  Importe dados de configuração do serviço Azure Rights Management para o Exchange Online sob a forma de um domínio de publicação fidedigno (TPD). Isto inclui a chave de inquilino do Azure Information Protection e modelos do Azure Rights Management:

    ```
    Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"
    ```
    Neste comando, utilizámos o nome **RMS Online** como nome base do TPD para o Azure Rights Management no Exchange Online. Após a importação do TPD, terá o nome **RMS Online – 1** no Exchange Online.

6.  Ative a funcionalidade do Azure Rights Management para que as funcionalidades da IRM estejam disponíveis no Exchange Online:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $true
    ```
    Após executar este comando, o Rights Management é automaticamente ativado para o cliente do Outlook, o Outlook Web App e o Exchange Active Sync.

7.  Opcionalmente, pode testar se esta configuração tem êxito através do seguinte comando:

    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Por exemplo: **Test-IRMConfiguration -Sender  adams@contoso.com**

    Este comando executa um conjunto de verificações que inclui a verificação da conectividade ao serviço, a obtenção da configuração, a obtenção de URIs, licenças e modelos. Na sessão do Windows PowerShell, verá os resultados de cada verificação e, no final, se nenhuma delas encontrar problemas, verá a mensagem: **RESULTADO GERAL: APROVADO**

8.  Desligue a sua sessão remota do PowerShell:

    ```
    Remove-PSSession $Session
    ```

Agora, os utilizadores podem proteger as suas mensagens de e-mail através do serviço Azure Rights Management. Por exemplo, no Outlook Web App, selecione **definir permissões** no menu expandido (**...** ) e, em seguida, escolha **não reencaminhar** ou um dos modelos disponíveis para aplicar a proteção da informação à mensagem de e-mail e quaisquer anexos. Contudo, como o Outlook Web App coloca a IU em cache durante um dia, espere que este período de tempo termine antes de tentar aplicar a proteção da informação às mensagens de e-mail e depois de executar estes comandos de configuração. Antes da atualização da IU para refletir a nova configuração, não verá nenhuma opção no menu **Definir permissões**.

> [!IMPORTANT]
> Se criar novos [modelos personalizados](configure-custom-templates.md) para o Azure Rights Management ou atualizar os modelos, de cada vez que o fizer, terá de executar o seguinte comando do Exchange Online PowerShell (se for necessário, execute primeiro os passos 2 e 3) para sincronizar estas alterações com o Exchange Online: `Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline`

Como administrador do Exchange, já pode configurar funcionalidades que apliquem automaticamente a proteção da informação, como, por exemplo, [regras de transporte](https://technet.microsoft.com/library/dd302432.aspx), [políticas de prevenção de perda de dados (DLP)](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) e [voice mail protegido](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (Unified Messaging).


### <a name="office-365-message-encryption"></a>Encriptação de Mensagens do Office 365
Execute os mesmos passos conforme documentado na secção anterior, mas se não quiser modelos sejam apresentados, antes do passo 6, execute o seguinte comando para impedir que os modelos IRM estejam disponíveis no Outlook Web App e do cliente do Outlook: `Set-IRMConfiguration -ClientAccessServerEnabled $false`

Em seguida, estará pronto para configurar [regras de transporte](https://technet.microsoft.com/library/dd302432.aspx), para modificar automaticamente a segurança da mensagem quando os destinatários estão fora da organização, e selecionar a opção **Aplicar a Encriptação de Mensagens do Office 365**.

Para obter mais informações sobre a encriptação de mensagens, veja [Encryption in Office 365 (Encriptação no Office 365 – em inglês)](https://technet.microsoft.com/library/dn569286.aspx) na biblioteca do Exchange.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
