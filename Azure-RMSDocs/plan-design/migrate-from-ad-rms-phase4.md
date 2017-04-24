---
title: "Migrar do AD RMS para o Azure Information Protection – fase 4"
description: "Fase 4 da migração do AD RMS para o Azure Information Protection, que abrange os passos 8 a 9 de Migrar do AD RMS para o Azure Information Protection"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 51a689248834f2578655d62752c19b7a387068a5
ms.sourcegitcommit: 237ce3a0cc4921da5a08ed5753e6491403298194
translationtype: HT
---
# <a name="migration-phase-4---supporting-services-configuration"></a>Fase 4 da migração – configuração de serviços de suporte

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*


Utilize as seguintes informações para a Fase 4 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem os passos 8 a 9 do tópico [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).



## <a name="step-8-configure-irm-integration-for-exchange-online"></a>Passo 8: configurar a integração de IRM para o Exchange Online

Se tiver importado anteriormente o TDP do AD RMS para o Exchange Online, tem de remover este TDP para evitar modelos e políticas em conflito após a migração para o Azure Information Protection. Para tal, utilize o cmdlet [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) do Exchange Online.

Se optou por uma topologia de chave de inquilino do Azure Information Protection **gerida pela Microsoft**:

1. Utilize as instruções na secção [Exchange Online: configuração de IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration) no artigo [Office 365: Configuração para clientes e serviços online](../deploy-use/configure-office365.md). Esta secção inclui comandos típicos a executar que ligam ao serviço do Exchange Online, importam a chave de inquilino do Azure Information Protection e ativam a funcionalidade IRM para o Exchange Online. Após concluir estes passos, terá acesso às funcionalidades completas de proteção do Azure Rights Management com o Exchange Online.

2. Para além da configuração padrão para ativar a IRM para o Exchange Online, execute os seguintes comandos do PowerShell para garantir que os utilizadores conseguirão ler e-mails que foram enviados ao utilizar a proteção do AD RMS.

    Substitua o nome de domínio da organização para *\<asuaempresa.dominio>*.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation
        $list += "https://adrms.<yourcompany.domain>/_wmcs/licensing"
        Set-IRMConfiguration -LicensingLocation $list
        Set-IRMConfiguration -internallicensingenabled $false
        Set-IRMConfiguration -internallicensingenabled $true


Se optou por uma topologia de chave de inquilino do Azure Information Protection **gerida pelo cliente (BYOK)**:

-   Terá funcionalidades reduzidas de proteção do Rights Management com o Exchange Online, conforme descrito no artigo [Preços e restrições do BYOK](byok-price-restrictions.md).


## <a name="step-9-configure-irm-integration-for-exchange-server-and-sharepoint-server"></a>Passo 9: configurar a integração de IRM para o Exchange Server e SharePoint Server

Se tiver utilizado a funcionalidade de Gestão de Direitos de Informação (IRM) do Exchange Server ou SharePoint Server com o AD RMS, terá de implementar o conector Azure Rights Management (RMS), que atua como uma interface de comunicações (um reencaminhamento) entre os seus servidores no local e o serviço de proteção do Azure Information Protection.

Estes passos indicam como instalar e configurar o conector, desativar a IRM para o Exchange e SharePoint e configurar estes servidores para utilizar o conector. Por fim, se tiver importado ficheiros de configuração de dados do AD RMS (.xml) para o Azure Information Protection que foram utilizados para proteger mensagens de e-mail, terá de editar manualmente o registo nos computadores do Exchange Server para redirecionar todos os URLs de domínio de publicação fidedigno para o conector RMS.

> [!NOTE]
> Antes de começar, verifique as versões dos servidores no local que o serviço Azure Rights Management suporta em [Servidores no local que suportam o Azure RMS](../get-started/requirements-servers.md).

### <a name="install-and-configure-the-rms-connector"></a>Instalar e configurar o conector RMS

Utilize as instruções no artigo [Implementar o conector Azure Rights Management](../deploy-use/deploy-rms-connector.md) e efetue os passos 1 a 4. Ainda não inicie o passo 5 das instruções de conector. 

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Desativar a IRM nos Servidores do Exchange e remover a configuração do AD RMS

1.  Em cada servidor Exchange, localize a pasta seguinte e elimine todas as entradas nessa pasta: **\ProgramData\Microsoft\DRM\Server\S-1-5-18**

2. Num dos servidores Exchange, execute os seguintes comandos do PowerShell para garantir que os utilizadores poderão ler e-mails que estão protegidos ao utilizar o Azure Rights Management.

    Antes de executar estes comandos, substitua o URL do serviço Azure Rights Management para *\<URL de Inquilino>*.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation 
        $list + "<Your Tenant URL>/_wmcs/licensing"
        Set-IRMConfiguration -LicensingLocation $list

3.  Agora, desative as funcionalidades da IRM para mensagens que são enviadas para destinatários internos:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

4. Em seguida, utilize o mesmo cmdlet para desativar a IRM no Microsoft Office Outlook Web App e no Microsoft Exchange ActiveSync:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Por fim, utilize o mesmo cmdlet para limpar todos os certificados em cache:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Em cada Exchange Server, reponha o IIS, por exemplo, ao executar uma linha de comandos como administrador e escrever **iisreset**.

### <a name="disable-irm-on-sharepoint-servers-and-remove-ad-rms-configuration"></a>Desativar a IRM em SharePoint Servers e remover a configuração do AD RMS

1.  Certifique-se de que não existem documentos com saída dada em bibliotecas protegidas por RMS. Se existirem, vão tornar-se inacessíveis no final deste procedimento.

2.  No Web site de Administração Central do SharePoint , na secção **Iniciação Rápida**, clique em **Segurança**.

3.  Na página **Segurança**, na secção **Política de Informações**, clique em **Configurar gestão de direitos de informação**.

4.  Na página **Gestão de Direitos de Informação**, na secção **Gestão de Direitos de Informação**, selecione **Não utilizar IRM neste servidor** e, em seguida, clique em **OK**.

5.  Em cada computador do SharePoint Server, elimine os conteúdos da pasta \ProgramData\Microsoft\MSIPC\Server\\\<*SID da conta que está a executar o SharePoint Server>*.

### <a name="configure-exchange-and-sharepoint-to-use-the-connector"></a>Configurar o Exchange e o SharePoint para utilizar o conector

1. Volte às instruções para implementar o conector RMS: [Passo 5: configurar servidores para utilizar o conector RMS](../deploy-use/configure-servers-rms-connector.md)

    Se apenas tiver o SharePoint Server, aceda diretamente aos [Passos seguintes](#next-steps) para continuar a migração. 

2. Em cada Exchange Server, adicione manualmente as chaves de registo na secção seguinte para cada ficheiro de dados de configuração (.xml) que tenha importado para redirecionar os URLs de domínio de publicação fidedigno para o conector RMS. Estas entradas do registo são específicas da migração e não são adicionadas pela ferramenta de configuração do servidor para o conector Microsoft RMS.

    Quando efetuar estas edições de registo, utilize as instruções seguintes:

    -   Substitua o *conector FQDN* pelo nome que definiu no DNS para o conector. Por exemplo, **rmsconnector.contoso.com**.

    -   Utilize o prefixo HTTP ou HTTPS para o URL do conector, dependendo se configurou o conector para utilizar HTTP ou HTTPS para comunicar com os servidores no local.

#### <a name="registry-edits-for-exchange"></a>Edições de registo do Exchange

Para todos os servidores Exchange, remova os valores de registo que adicionou para LicenseServerRedirection durante a fase de preparação. Estes valores foram adicionados aos seguintes caminhos:

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection


Para o Exchange 2013 e o Exchange 2016 – edição de registo 1:


**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Valor:** https://\<URL de Licenciamento na Intranet do AD RMS\>/_wmcs/licensing

**Dados:**

Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange Server para o conector RMS:

- http://\<conector FQDN\>/_wmcs/licensing

- https://\<conector FQDN\>/_wmcs/licensing


---

Para o Exchange 2013 – edição de registo 2:

**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection 

**Tipo:** Reg_SZ

**Valor:**https://\<URL de Licenciamento na Extranet do AD RMS\>/_wmcs/licensing

**Dados:**

Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange Server para o conector RMS:

- http://\<conector FQDN\>/_wmcs/licensing

- https://\<conector FQDN\>/_wmcs/licensing

---

Para o Exchange 2010 – edição de registo 1:


**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Valor:** https://\<URL de Licenciamento na Intranet do AD RMS\>/_wmcs/licensing

**Dados:**

Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange Server para o conector RMS:

- http://\<conector FQDN\>/_wmcs/licensing

- https://\<Nome do conector\>/_wmcs/licensing


---

Para o Exchange 2010 – edição de registo 2:


**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Valor:**https://\<URL de Licenciamento na Extranet do AD RMS\>/_wmcs/licensing

**Dados:**

Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange Server para o conector RMS:

- http://\<conector FQDN\>/_wmcs/licensing

- https://\<conector FQDN\>/_wmcs/licensing

---


## <a name="next-steps"></a>Passos seguintes
Para continuar a migração, aceda a [fase 5 – tarefas de pós-migração](migrate-from-ad-rms-phase5.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]