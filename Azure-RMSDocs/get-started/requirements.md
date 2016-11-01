---
title: Requisitos do Azure Information Protection | Azure Information Protection
description: "Identifique os pré-requisitos para implementar o Azure Information Protection para a sua organização."
author: cabailey
manager: mbaldwin
ms.date: 10/19/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: efbb95e5f34a45c8a5f17eb61ebb09dfe5c8f65f
ms.openlocfilehash: 1b69be775b3cd270e4b6ea42a306eb51c15424cb


---

# Requisitos para o Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*


Antes de implementar o Azure Information Protection na sua organização, certifique-se de que cumpre os seguintes pré-requisitos. 

|Requisito|Mais informações|
|---------------|--------------------|
|Uma subscrição do Azure Information Protection|Consulte as [informações de subscrição](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) e a [lista de funcionalidades](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) no site do Azure Information Protection para certificar-se de que a subscrição da sua organização inclui as funcionalidades do Azure Information Protection que pretende utilizar.|
|Azure Active Directory|A sua organização tem de ter um Azure Active Directory (Azure AD) para suportar a autenticação de utilizador para Azure Information Protection. Além disso, se pretender utilizar as contas de utilizador do seu diretório no local (AD DS), tem também de configurar a integração de diretórios.<br /><br />Se as suas contas forem federadas (por exemplo, se utilizar o AD FS), tem de utilizar a Autenticação Integrada do Windows. A autenticação baseada em formulários não é suportada para Azure Information Protection.<br /><br />A autenticação multifator (MFA) é suportada com o Azure Information Protection quando tem o software de cliente necessário e a infraestrutura de suporte de MFA corretamente configurada.<br /><br />Para mais informações, consulte [Requisitos do Azure Active Directory para o Azure Information Protection](requirements-azure-ad.md).|
|Dispositivos cliente|Os utilizadores têm de ter dispositivos cliente (computador ou dispositivo móvel) com um sistema operativo que suporte o Azure Information Protection.<br /><br />Os seguintes dispositivos suportam o cliente do Azure Information Protection, o qual permite aos utilizadores classificar e etiquetar os documentos e e-mails do Office:<br /><br />- Windows 10 (x86, x64)<br /><br />- Windows 8.1 (x86, x64)<br /><br />- Windows 8 (x86, x64)<br /><br />- Windows 7 Service Pack 1 (x86, x64)<br /><br />Quando este cliente protege os dados através do serviço Azure Rights Management, estes podem ser consumidos pelos mesmos dispositivos (Windows, Mac, iOS, Android) que suportam o serviço Azure Rights Management. <br /><br />Para obter detalhes sobre os dispositivos que suportam o serviço Azure Rights Management, consulte [Dispositivos cliente que suportam a proteção de dados do Azure Rights Management](../get-started/requirements-client-devices.md).|
|Aplicações|O cliente do Azure Information Protection suporta a etiquetagem e a proteção de ficheiros e e-mails criados pelas seguintes aplicações do Office: **Word**, **Excel**, **PowerPoint** e **Outlook** a partir dos seguintes conjuntos de aplicações do Office:<br /><br />- Office Professional Plus 2016<br /><br />- Office Professional Plus 2013 com o Service Pack 1<br /><br />- Office Professional Plus 2010<br /><br />Para obter informações sobre as aplicações que suportam o serviço Azure Rights Management, consulte [Aplicações que suportam a proteção de dados do Azure Rights Management](requirements-applications.md).|
|Infraestrutura que suporta a conetividade à Internet e a serviços em nuvem dependentes|Se tiver uma firewall ou um dispositivo interveniente semelhante que deve ser configurado para permitir ligações específicas, veja as informações do **Azure Rights Management (RMS)** na secção [Portal do Office 365 e partilhado](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) do seguinte artigo do Office: [URLs do Office 365 e intervalos de endereços IP](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Utilize as instruções neste artigo do Office para se manter atualizado em relação às alterações a estas informações ao subscrever um feed RSS.<br /><br />Além das informações no artigo do Office, específico para o Azure Information Protection:<br /><br />- Permitir tráfego HTTPS em TCP 443 para **api.informationprotection.azure.com**.<br /><br />- Não termine a ligação cliente para serviço TLS (por exemplo, para fazer uma inspeção ao nível do pacote). Se o fizer, quebrará a afixação de certificado que os clientes de RMS utilizam com as AC geridas pela Microsoft para ajudar a proteger as comunicações com o Azure RMS.<br /><br />- Se utilizar um proxy Web que requer autenticação, tem de o configurar para utilizar a autenticação integrada do Windows com as credenciais de início de sessão do utilizador do Active Directory.|

Se quiser utilizar o serviço Azure Rights Management a partir do Azure Information Protection com servidores no local, são suportados os seguintes produtos:

-   Exchange Server

-   SharePoint Server

-   Servidores de ficheiros do Windows Server que suportam a Infraestrutura de Classificação de Ficheiros

Para obter informações sobre os requisitos adicionais para este cenário, consulte [Servidores no local que suportam a proteção de dados do Azure Rights Management](requirements-servers.md).

> [!IMPORTANT]
> O seguinte cenário de implementação não é suportado, exceto se estiver a utilizar a proteção do AD RMS com o Azure Information Protection (configuração "tenha a sua própria chave" ou HYOK):
> 
> -   Executar o AD RMS e o Azure RMS lado a lado na mesma organização, exceto durante a migração, conforme descrito em [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).
> 
> Existe um caminho de migração suportado [do AD RMS para o Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) e do [Azure Information Protection para o AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Se implementar o Azure Information Protection e, em seguida, decidir que já não quer utilizar este serviço em nuvem, consulte [Encerrar e desativar o Azure Information Protection](../deploy-use/decommission-deactivate.md).






<!--HONumber=Oct16_HO3-->


