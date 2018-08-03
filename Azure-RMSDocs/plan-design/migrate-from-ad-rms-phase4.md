---
title: Migrar do AD RMS para o Azure Information Protection – fase 4
description: Fase 4 da migração do AD RMS para o Azure Information Protection, que abrange os passos 8 a 9 de Migrar do AD RMS para o Azure Information Protection
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/01/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d34c9069d7486c4a7cab78ccffe49b608e8a2825
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39473462"
---
# <a name="migration-phase-4---supporting-services-configuration"></a>Fase 4 da migração – configuração de serviços de suporte

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Utilize as seguintes informações para a Fase 4 da migração do AD RMS para o Azure Information Protection. Estes procedimentos incluem os passos 8 a 9 do tópico [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).



## <a name="step-8-configure-irm-integration-for-exchange-online"></a>Passo 8: configurar a integração de IRM para o Exchange Online

> [!IMPORTANT]
> Porque não é possível controlar quais destinatários migrados os utilizadores podem selecionar para e-mails protegidos, certifique-se de que todos os utilizadores e grupos habilitados para email na sua organização tiverem uma conta no Azure AD que pode ser utilizado com o Azure Information Protection. [Mais informações](prepare.md)

Independentemente do inquilino do Azure Information Protection, topologia de chaves que escolheu, faça o seguinte:

1. Para o Exchange Online ser capaz de descriptografar e-mails protegidos pelo AD RMS, ele precisa saber que o URL de AD RMS para o seu cluster corresponde à chave que está disponível no seu inquilino. Isso é feito com o registo SRV de DNS para o cluster de AD RMS, que também é utilizado para reconfigurar os clientes do Office para utilizar o Azure Information Protection. Se não tiver criado o registo SRV de DNS para reconfiguração de cliente no passo 7, crie este registo agora para suportar o Exchange Online. [Instruções](migrate-from-ad-rms-phase3.md#client-reconfiguration-by-using-dns-redirection)
    
    Quando este registo DNS está implementado, os utilizadores através do Outlook na web e clientes de e-mail do dispositivo móvel vão conseguir ver o AD RMS protegidos essas aplicações de mensagens de e-mail e Exchange poderá utilizar a chave que tiver sido importado de AD RMS para desencriptar, índice , diário e proteger conteúdo que foi protegido pelo AD RMS.  

2. Executar o Exchange Online [Get-IRMConfiguration] (https://technet.microsoft.com/library/dd776120(v=exchg.160\).aspx) comando. Se precisar de executar este comando de ajuda, veja as instruções passo a passo em [Exchange Online: configuração de IRM](/..deploy-use/configure-office365.md#exchange-online-irm-configuration).
    
    A partir da saída, verifique se **AzureRMSLicensingEnabled** está definida como **verdadeiro**:
    
    - Se AzureRMSLicensingEnabled estiver definido como **True**, nenhuma configuração adicional é necessária para este passo. 
    
    - Se estiver definido AzureRMSLicensingEnabled **False**, execute `Set-IRMConfiguration -AzureRMSLicensingEnabled $true` e, em seguida, utilize os passos de verificação da [configurar novas capacidades de encriptação de mensagens do Office 365 criadas com base no Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)para confirmar que Exchange Online está agora pronto para utilizar o serviço Azure Rights Management. 

## <a name="step-9-configure-irm-integration-for-exchange-server-and-sharepoint-server"></a>Passo 9: configurar a integração de IRM para o Exchange Server e SharePoint Server

Se tiver utilizado a funcionalidade de Gestão de Direitos de Informação (IRM) do Exchange Server ou SharePoint Server com o AD RMS, terá de implementar o conector Azure Rights Management (RMS), que atua como uma interface de comunicações (um reencaminhamento) entre os seus servidores no local e o serviço de proteção do Azure Information Protection.

Este passo indica como instalar e configurar o conector, desativar a IRM para o Exchange e SharePoint e configurar estes servidores para utilizar o conector. Por fim, se tiver importado ficheiros de configuração de dados do AD RMS (.xml) para o Azure Information Protection que foram utilizados para proteger mensagens de e-mail, terá de editar manualmente o registo nos computadores do Exchange Server para redirecionar todos os URLs de domínio de publicação fidedigno para o conector RMS.

> [!NOTE]
> Antes de começar, verifique as versões dos servidores no local que o serviço Azure Rights Management suporta em [Servidores no local que suportam o Azure RMS](../requirements-servers.md).

### <a name="install-and-configure-the-rms-connector"></a>Instalar e configurar o conetor RMS

Utilize as instruções no artigo [Implementar o conector Azure Rights Management](../deploy-use/deploy-rms-connector.md) e efetue os passos 1 a 4. Ainda não inicie o passo 5 das instruções de conector. 

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Desativar a IRM nos Servidores do Exchange e remover a configuração do AD RMS

1.  Em cada servidor Exchange, localize a pasta seguinte e elimine todas as entradas nessa pasta: **\ProgramData\Microsoft\DRM\Server\S-1-5-18**

2. Num dos servidores Exchange, execute os seguintes comandos do PowerShell para garantir que os utilizadores poderão ler e-mails que estão protegidos ao utilizar o Azure Rights Management.

    Antes de executar estes comandos, substitua o URL do serviço Azure Rights Management para *\<URL de Inquilino>*.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation 
        $list += "<Your Tenant URL>/_wmcs/licensing"
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

    -   Utilize o prefixo HTTP ou HTTPS para o URL do conetor, dependendo se configurou o conetor para utilizar HTTP ou HTTPS para comunicar com os servidores no local.

#### <a name="registry-edits-for-exchange"></a>Edições de registo do Exchange

Para todos os servidores do Exchange, adicione os seguintes valores de registo para LicenseServerRedirection, dependendo de suas versões do Exchange:

---

Para o Exchange 2013 e o Exchange 2016 – edição de registo 1:


**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Valor:** https://\<URL de Licenciamento na Intranet do AD RMS\>/_wmcs/licensing

**Dados:**

Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange Server para o conetor RMS:

- http://\<conector FQDN\>/_wmcs/licensing

- https://\<conector FQDN\>/_wmcs/licensing


---

Exchange 2013 – edição de registo 2:

**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection 

**Tipo:** Reg_SZ

**Valor:** https://\<URL de Licenciamento na Extranet do AD RMS\>/_wmcs/licensing

**Dados:**

Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange Server para o conetor RMS:

- http://\<conector FQDN\>/_wmcs/licensing

- https://\<conector FQDN\>/_wmcs/licensing

---

Para o Exchange 2010 – edição de registo 1:


**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Valor:** https://\<URL de Licenciamento na Intranet do AD RMS\>/_wmcs/licensing

**Dados:**

Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange Server para o conetor RMS:

- http://\<conector FQDN\>/_wmcs/licensing

- https://\<Nome do conector\>/_wmcs/licensing


---

Para o Exchange 2010 – edição de registo 2:


**Caminho do registo:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Valor:** https://\<URL de Licenciamento na Extranet do AD RMS\>/_wmcs/licensing

**Dados:**

Um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange Server para o conetor RMS:

- http://\<conector FQDN\>/_wmcs/licensing

- https://\<conector FQDN\>/_wmcs/licensing

---


## <a name="next-steps"></a>Passos Seguintes
Para continuar a migração, aceda a [fase 5 – tarefas de pós-migração](migrate-from-ad-rms-phase5.md).
