---
title: Requisitos para o Azure Information Protection
description: "Identifique os pré-requisitos para implementar o Azure Information Protection para a sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/18/2018
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9286be6e9feb6be87494db0be8e625bdbbf30ddd
ms.sourcegitcommit: ad628bcc2eea26ed69511870b36924e58e4c2fc8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/19/2018
---
# <a name="requirements-for-azure-information-protection"></a>Requisitos para o Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Antes de implementar o Azure Information Protection na sua organização, certifique-se de que cumpre os seguintes pré-requisitos. 

## <a name="subscription-for-azure-information-protection"></a>Subscrição do Azure Information Protection

Para classificação, etiquetagem e proteção, tem de ter um [plano do Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing). 

Para obter apenas proteção, deve ter um [plano do Office 365 que inclui o Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Para se certificar de que a subscrição da sua organização inclui as funcionalidades do Azure Information Protection que pretende utilizar, veja as [informações de subscrição](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) e a [lista de funcionalidades](https://www.microsoft.com/cloud-platform/azure-information-protection-features) no site do Azure Information Protection.

> [!NOTE]
> Se tiver dúvidas sobre subscrições ou licenciamento, não as publique nesta página. em alternativa, entre em contacto com o seu Gestor de Conta Microsoft ou com o [Suporte da Microsoft](information-support.md#to-contact-microsoft-support).

## <a name="azure-active-directory"></a>Azure Active Directory

A sua organização tem de ter um Azure Active Directory (Azure AD) para suportar a autorização e autenticação de utilizador para o Azure Information Protection. Além disso, se pretender utilizar as contas de utilizador do seu diretório no local (AD DS), tem também de configurar a integração de diretórios.

A autenticação multifator (MFA) é suportada com o Azure Information Protection quando tem o software de cliente necessário e a infraestrutura de suporte de MFA corretamente configurada.

Acesso condicional é suportado na pré-visualização para documentos protegidos pelo Azure Information Protection. Para obter mais informações, consulte as FAQ seguintes: [vejo Azure Information Protection está indicado como uma aplicação de nuvem disponíveis para o acesso condicional — como funciona este trabalho?](faqs.md#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

Para obter mais informações sobre os requisitos de autenticação, veja [Requisitos do Azure Active Directory para o Azure Information Protection](requirements-azure-ad.md). 

Para obter mais informações sobre os requisitos para as contas de utilizador e de grupo a autorizar, veja [Preparar utilizadores e grupos para o Azure Information Protection](../plan-design/prepare.md).

## <a name="client-devices"></a>Dispositivos cliente

Os utilizadores têm de ter dispositivos cliente (computador ou dispositivo móvel) com um sistema operativo que suporte o Azure Information Protection.

Os seguintes dispositivos suportam o cliente do Azure Information Protection, o qual permite aos utilizadores classificar e etiquetar os documentos e e-mails:

- Windows 10 (x86, x64)

- Windows 8.1 (x86, x64)

- Windows 8 (x86, x64)

- Windows 7 Service Pack 1 (x86, x64)

- Windows Server 2016 

- Windows Server 2012 R2 e Windows Server 2012

- Windows Server 2008 R2 

Nas versões de servidor listadas, o cliente do Azure Information Protection é suportado para os Serviços de Ambiente de Trabalho Remoto. Se eliminar perfis de utilizador ao utilizar o cliente do Azure Information Protection com os Serviços de Ambiente de Trabalho Remoto, não elimine a pasta **%Appdata%\Microsoft\Protect**.

Quando o cliente do Azure Information Protection protege os dados através do serviço Azure Rights Management, estes podem ser consumidos pelos [mesmos dispositivos](requirements-client-devices.md) que suportam o serviço Azure Rights Management.

## <a name="applications"></a>Aplicações

O cliente do Azure Information Protection pode etiquetar e proteger documentos e e-mails ao utilizar as aplicações **Word**, **Excel**, **PowerPoint** e **Outlook** a partir de qualquer uma das seguintes edições do Office:

- Office 365 ProPlus com aplicações da versão de 2016 ou 2013 (instalação com tecnologia Clique-e-Use ou baseada no Windows Installer)

- Office Professional Plus 2016

- Office Professional Plus 2013 com Service Pack 1

- Office Professional Plus 2010 com Service Pack 2

Outras edições do Office não podem proteger documentos e e-mails com um serviço Rights Management. Nestas edições, o Azure Information Protection é suportado apenas para classificação. As etiquetas que aplicam a proteção não são apresentadas na barra do Azure Information Protection. 

Para obter informações sobre as aplicações do Office que suportam o serviço de proteção de dados, consulte [Aplicações que suportam a proteção de dados do Azure Rights Management](requirements-applications.md).

## <a name="firewalls-and-network-infrastructure"></a>Firewalls e infraestrutura de rede

Se tiver uma firewall ou um dispositivo de rede interveniente semelhante configurado para permitir ligações específicas, veja as informações do **Azure Rights Management (RMS)** na secção [Portal e serviços partilhados do Office 365](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US#bkmk_portal-identity) do seguinte artigo do Office: [Intervalos de URLs e endereços IP do Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Utilize as instruções neste artigo do Office para se manter atualizado em relação às alterações a estas informações ao subscrever um feed RSS.

Além das informações no artigo do Office, específico para o Azure Information Protection:

- Permitir tráfego HTTPS em TCP 443 para **api.informationprotection.azure.com**.

- Se utilizar um proxy Web que requer autenticação, tem de o configurar para utilizar a autenticação integrada do Windows com as credenciais de início de sessão do utilizador do Active Directory.

- Não termine a ligação cliente para serviço TLS (por exemplo, para fazer uma inspeção ao nível do pacote). Se o fizer, interrompe o certificado que os clientes de RMS utilizam com as ACs gerida pela Microsoft para ajudar a proteger as comunicações com o serviço Azure Rights Management de afixação.
    
    - Sugestão: Devido a forma como o Chrome apresenta ligações seguras na barra de endereço, pode utilizar este browser para rapidamente verificar se a ligação de cliente é terminada antes de atingir o serviço Azure Rights Management. Introduza o seguinte URL na barra de endereço do browser:`https://admin.na.aadrm.com/admin/admin.svc` 
    
        Não se preocupe que apresenta a janela do browser. Clique em vez disso, o cadeado na barra de endereço para ver as informações do site. As informações do site permite-lhe ver a autoridade de certificação (AC) emissora. Se o certificado não é emitido por uma CA Microsoft, é muito provável que a ligação de serviço de cliente segura está a ser terminada e tem de reconfiguração na sua firewall. A imagem seguinte mostra um exemplo de um Microsoft AC emissora. Se vir que uma AC interna emitiu o certificado, esta configuração não é compatível com o Azure Information Protection.
        
        ![A verificar o certificado emitido para ligações do Azure Information Protection](../media/certificate-checking.png)

### <a name="on-premises-servers"></a>Servidores no local

Se quiser utilizar o serviço Azure Rights Management a partir do Azure Information Protection com servidores no local, são suportados os seguintes produtos:

- Exchange Server

- SharePoint Server

- Servidores de ficheiros do Windows Server que suportam a Infraestrutura de Classificação de Ficheiros

Para obter informações sobre os requisitos adicionais para este cenário, consulte [Servidores no local que suportam a proteção de dados do Azure Rights Management](requirements-servers.md).

### <a name="coexistence-of-ad-rms-with-azure-rms"></a>Coexistência do AD RMS com o Azure RMS

O seguinte cenário de implementação não é suportado, exceto se estiver a utilizar a proteção do AD RMS com o Azure Information Protection (configuração "tenha a sua própria chave" ou HYOK):

- Executar o AD RMS e o Azure RMS lado a lado na mesma organização, exceto durante a migração, conforme descrito em [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

Existe um caminho de migração suportado [do AD RMS para o Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) e do [Azure Information Protection para o AD RMS](/powershell/module/aadrm/Set-AadrmMigrationUrl). Se implementar o Azure Information Protection e, em seguida, decidir que já não quer utilizar este serviço na cloud, consulte [Encerrar e desativar o Azure Information Protection](../deploy-use/decommission-deactivate.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


