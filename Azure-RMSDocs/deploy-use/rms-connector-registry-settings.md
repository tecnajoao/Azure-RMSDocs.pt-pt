---
title: Definições de registo para o conetor Rights Management – AIP
description: Informações sobre as definições de registo em servidores que utilizam o conector RMS. O método recomendado para configurar estas definições é utilizar a ferramenta de configuração do servidor do conetor Microsoft RMS.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/01/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed3e9a3d-0f7c-4abc-9d0b-aa3b18403d39
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: bc0cb2a7349bf19ee19a42bdb283cd86297748bc
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="registry-setting-for-the-rights-management-connector"></a>Definição de registo para o conetor Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Utilize as tabelas nas secções seguintes apenas se pretender adicionar manualmente ou verifique as definições de registo nos servidores que executam o Exchange, SharePoint ou Windows Server. Estas definições de registo configuram servidores para utilizar o [conector RMS](deploy-rms-connector.md). O método recomendado para configurar estes servidores é utilizar a ferramenta de configuração do servidor do conetor Microsoft RMS.

Instruções ao utilizar estas definições:

-   *\<Urldeinquilino >* é o URL do serviço Azure Rights Management para o seu inquilino do Azure Information Protection. Para localizar este valor:

    1.  Execute o [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) cmdlet para o serviço Azure Rights Management. Se já ainda não instalou o módulo Windows PowerShell para o Azure RMS, consulte [instalar o módulo do AADRM PowerShell](install-powershell.md).

    2.  A partir da saída, identifique o valor **LicensingIntranetDistributionPointUrl**.

        Por exemplo: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  No valor, remova **/_wmcs/licensing** desta cadeia. A cadeia restante é o URL do serviço Azure Rights Management. No nosso exemplo, o URL do serviço Azure Rights Management seria o seguinte valor:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**
        
        Pode verificar que tem o valor correto, executando o seguinte comando do PowerShell:
        
            (Get-AadrmConfiguration).LicensingIntranetDistributionPointUrl -match "https:\/\/[0-9A-Za-z\.-]*" | Out-Null; $matches[0]

-   *\<ConnectorFQDN >* é o nome de balanceamento de carga que definiu no DNS para o conector. Por exemplo, **rmsconnector.contoso.com**.

-   Utilize o prefixo HTTPS para o URL do conetor se configurou o conetor para utilizar o HTTPS para comunicar com os servidores no local. Para obter mais informações, veja a secção [Configurar o conetor RMS para utilizar HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https) das instruções principais. O URL do serviço Azure Rights Management utiliza sempre HTTPS.


## <a name="exchange-2016-or-exchange-2013-registry-settings"></a>Definições de registo do Exchange 2016 ou Exchange 2013

**Caminho do registo:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Tipo:** Reg_SZ

**Valor:** predefinido

**Dados:** https://*\<Urldeinquilino >*  /wmcs/certification

---

**Caminho do registo:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Tipo:** Reg_SZ

**Valor:** predefinido

**Dados:** https://*\<Urldeinquilino >*/_wmcs/Licensing

---

**Caminho do registo:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection

**Tipo:** Reg_SZ

**Valor:** https://*\<Urldeinquilino >*


**Dados:** um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange server para o conetor RMS:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*

---

**Caminho do registo:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Value:** https://*<\YourTenantURL>*


**Dados:** um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange server para o conetor RMS:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*


## <a name="exchange-2010-registry-settings"></a>Definições de registo do Exchange 2010

**Caminho do registo:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Tipo:** Reg_SZ

**Valor:** predefinido

**Data:** https://*<\YourTenantURL>*/_wmcs/certification

---

**Caminho do registo:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Tipo:** Reg_SZ

**Valor:** predefinido

**Dados:** https://*< \YourTenantURL >*/_wmcs/Licensing

---

**Caminho do registo:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection

**Tipo:** Reg_SZ

**Value:** https://*<\YourTenantURL>*

**Dados:** um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange server para o conetor RMS:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*

---

**Caminho do registo:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Tipo:** Reg_SZ

**Value:** https://*<\YourTenantURL>*

**Dados:** um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no Exchange server para o conetor RMS:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*


## <a name="sharepoint-2016-or-sharepoint-2013-registry-settings"></a>Definições de registo do SharePoint 2016 ou SharePoint 2013

**Caminho do registo:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection

**Tipo:** Reg_SZ

**Valor:** https://*< \YourTenantURL >*/_wmcs/Licensing


**Dados:** um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no SharePoint server para o conetor RMS:

- http://*<\ConnectorFQDN>*/_wmcs/licensing

- https://*<\ConnectorFQDN>*/_wmcs/licensing

---

**Caminho do registo:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification

**Tipo:** Reg_SZ

**Valor:** predefinido

**Dados:** um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no SharePoint server para o conetor RMS:

- http://*<\ConnectorFQDN>*/_wmcs/certification

- https://*<\ConnectorFQDN>*/_wmcs/certification

---

**Caminho do registo:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing

**Tipo:** Reg_SZ

**Valor:** predefinido


**Dados:** um dos seguintes, dependendo se está a utilizar HTTP ou HTTPS no SharePoint server para o conetor RMS:

- http://*<\ConnectorFQDN>*/_wmcs/licensing

- https://*<\ConnectorFQDN>*/_wmcs/licensing




## <a name="file-server-and-file-classification-infrastructure-registry-settings"></a>Servidor de ficheiros e definições de registo de Infraestrutura de Classificação de Ficheiros

**Caminho do registo:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Tipo:** Reg_SZ

**Valor:** predefinido

**Dados:** http://*< \ConnectorFQDN >*/_wmcs/Licensing

---

**Caminho do registo:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

**Tipo:** Reg_SZ

**Valor:** predefinido

**Data:** http://*<\ConnectorFQDN>*/_wmcs/certification


Voltar a [Implementar o conetor Azure Rights Management](deploy-rms-connector.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]