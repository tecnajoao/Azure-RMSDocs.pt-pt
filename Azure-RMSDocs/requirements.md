---
title: Requisitos para o Azure Information Protection
description: Identifique os pré-requisitos para implementar o Azure Information Protection para a sua organização.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 92b7ca3feceb70bc9b8b085b58c26231d2ae70ce
ms.sourcegitcommit: 8a4bab8dc6ee4c322a54d79091af04ec9449e5c2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51020059"
---
# <a name="requirements-for-azure-information-protection"></a>Requisitos para o Azure Information Protection

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Antes de implementar o Azure Information Protection na sua organização, certifique-se de que cumpre os seguintes pré-requisitos. 

## <a name="subscription-for-azure-information-protection"></a>Subscrição do Azure Information Protection

**Para classificação, etiquetagem e proteção**: tem de ter uma [plano do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/). 

**Para apenas de proteção**: tem de ter uma [plano do Office 365 que inclui o Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Para certificar-se de que a subscrição da sua organização inclui as funcionalidades do Azure Information Protection que pretende utilizar, reveja a lista de recursos a partir da [preços do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection) página.

> [!TIP]
> Procurando saber se planear do Office 365 ou autónomo Exchange Online plano suporta o [novas capacidades de encriptação de mensagens do Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801), para enviar e-mails protegidos para endereços de e-mail pessoais? Por exemplo, Gmail, Yahoo e Microsoft. Consulte os seguintes recursos:
>
> [Descrição de serviço Online do Exchange](https://technet.microsoft.com/library/exchange-online-service-description.aspx)
>
> [Office 365 educação](https://technet.microsoft.com/library/mt844095.aspx)
>
> [Office 365 administração pública dos EUA](https://technet.microsoft.com/library/mt774581.aspx)

Se tiver dúvidas sobre subscrições ou licenciamento, não as publique nesta página. em alternativa, entre em contacto com o seu Gestor de Conta Microsoft ou com o [Suporte da Microsoft](information-support.md#to-contact-microsoft-support).

## <a name="azure-active-directory"></a>Azure Active Directory

A sua organização tem de ter um Azure Active Directory (Azure AD) para suportar a autorização e autenticação de utilizador para o Azure Information Protection. Além disso, se pretender utilizar as contas de utilizador do diretório no local (AD DS), também tem de configurar integração de diretórios.

Início de sessão único (SSO) é suportada para o Azure Information Protection, para que os utilizadores não são um pedido repetidamente as credenciais. Se utilizar outra solução de fornecedor de Federação, consulte esse fornecedor como configurá-lo para o Azure AD. WS-Trust é um requisito comum para estas soluções suportar o início de sessão único. 

A autenticação multifator (MFA) é suportada com o Azure Information Protection quando tem o software de cliente necessário e a infraestrutura de suporte de MFA corretamente configurada.

Acesso condicional é suportado em pré-visualização para documentos protegidos pelo Azure Information Protection. Para obter mais informações, consulte as FAQ seguintes: [vejo do Azure Information Protection está indicado como uma aplicação de cloud disponível para o acesso condicional, como faz esse trabalho?](faqs.md#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

Para obter mais informações sobre os requisitos de autenticação, veja [Requisitos do Azure Active Directory para o Azure Information Protection](requirements-azure-ad.md). 

Para obter mais informações sobre os requisitos para as contas de utilizador e de grupo a autorizar, veja [Preparar utilizadores e grupos para o Azure Information Protection](prepare.md).

## <a name="client-devices"></a>Dispositivos cliente

Os utilizadores têm de ter dispositivos cliente (computador ou dispositivo móvel) com um sistema operativo que suporte o Azure Information Protection.

Os seguintes dispositivos suportam o cliente do Azure Information Protection, o qual permite aos utilizadores classificar e etiquetar os documentos e e-mails:

- Windows 10 (x86, x64)
    
    - Não há suporte para manuscrito na compilação do Windows 10 RS4 Insiders. 

- Windows 8.1 (x86, x64)

- Windows 8 (x86, x64)

- Windows 7 Service Pack 1 (x86, x64)

- Windows Server 2016 

- Windows Server 2012 R2 e Windows Server 2012

- Windows Server 2008 R2 

Para além de instalar o cliente do Azure Information Protection em computadores físicos, também pode instalá-lo em máquinas virtuais. Verifique se o fornecedor do software para a solução de área de trabalho virtual tem de configuração adicionais que pode ser necessárias para executar o cliente do Azure Information Protection. Por exemplo, para as soluções Citrix, talvez seja preciso [desativar Application Programming Interface (API) da Citrix ganchos](https://support.citrix.com/article/CTX107825) for Office (winword.exe, excel.exe, outlook.exe, powerpoint.exe) e o (de cliente do Azure Information Protection msip.App.exe, msip.viewer.exe).

Nas versões de servidor listadas, o cliente do Azure Information Protection é suportado para os Serviços de Ambiente de Trabalho Remoto. Se eliminar perfis de utilizador ao utilizar o cliente do Azure Information Protection com os Serviços de Ambiente de Trabalho Remoto, não elimine a pasta **%Appdata%\Microsoft\Protect**.

Quando o cliente do Azure Information Protection protege os dados através do serviço Azure Rights Management, estes podem ser consumidos pelos [mesmos dispositivos](requirements-client-devices.md) que suportam o serviço Azure Rights Management.

Tem do cliente do Azure Information Protection [pré-requisitos adicionais](./rms-client/client-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-client) que estão listadas na guia do administrador.

## <a name="applications"></a>Aplicações

O cliente do Azure Information Protection pode etiquetar e proteger documentos e e-mails ao utilizar as aplicações **Word**, **Excel**, **PowerPoint** e **Outlook** a partir de qualquer uma das seguintes edições do Office:

- Office 365 com aplicações do Office 2016 (versão mínima 1805, build 9330.2078) quando o utilizador tem atribuída uma licença do Azure Rights Management (também conhecido como Azure Information Protection para o Office 365)

- Office 365 ProPlus com aplicações da versão de 2016 ou 2013 (instalação com tecnologia Clique-e-Use ou baseada no Windows Installer)

- Office Professional Plus 2016

- Office Professional Plus 2013 com Service Pack 1

- Office Professional Plus 2010 com Service Pack 2

Outras edições do Office não podem proteger documentos e e-mails com um serviço Rights Management. Nestas edições, o Azure Information Protection é suportado apenas para classificação. Conseqüentemente, as etiquetas que aplicam a proteção não são apresentadas aos utilizadores no Azure Information Protection barra ou a partir da **Protect** botão da faixa de opções do Office. 

O cliente do Azure Information Protection não suporta várias versões do Office no mesmo computador. Este cliente também não suporta contas de utilizador mudar no Office.

Para obter informações sobre o Office que as edições suportam o serviço de proteção, consulte [aplicações que suportam a proteção de dados do Azure Rights Management](requirements-applications.md).

## <a name="firewalls-and-network-infrastructure"></a>Firewalls e infraestrutura de rede

Se tiver uma firewall ou interveniente semelhante que estão configurados para permitir ligações específicas, os requisitos de conectividade de rede estão incluídos no artigo do Office, [intervalos de endereços IP e URLs do Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2). Consulte a **comuns do Microsoft 365 e o Office Online** secção.

Além das informações no artigo do Office, específico para o Azure Information Protection:

- Se utilizar um proxy Web que requer autenticação, tem de o configurar para utilizar a autenticação integrada do Windows com as credenciais de início de sessão do utilizador do Active Directory.

- Não termine a ligação de cliente para serviço TLS (por exemplo, para fazer inspeção ao nível do pacote) para o **aadrm.com** URL. Se o fizer, quebra a afixação de que os clientes de RMS utilizam com as AC geridas pela Microsoft para ajudar a proteger as comunicações com o serviço Azure Rights Management de certificado.
    
    - Sugestão: Devido à forma como Chrome apresenta ligações seguras na barra de endereço, pode utilizar este browser para verificar rapidamente se a ligação de cliente é encerrada antes de atingir o serviço Azure Rights Management. Introduza o seguinte URL na barra de endereço do browser: `https://admin.na.aadrm.com/admin/admin.svc` 
    
        Não se preocupe no que apresenta a janela do browser. Clique em vez disso, o cadeado na barra de endereço para ver as informações do site. As informações do site permite-lhe ver a autoridade de certificação (AC) emissora. Se o certificado não é emitido por uma CA Microsoft, é muito provável que a ligação segura do serviço de cliente está a ser terminada e tem de reconfiguração na sua firewall. A imagem seguinte mostra um exemplo de um Microsoft AC emissora. Se vir que uma AC interna emitiu o certificado, esta configuração não é compatível com o Azure Information Protection.
        
        ![A verificar o certificado emitido para ligações de Azure Information Protection](./media/certificate-checking.png)

### <a name="on-premises-servers"></a>Servidores no local

Se quiser utilizar o serviço Azure Rights Management a partir do Azure Information Protection com servidores no local, são suportados os seguintes produtos:

- Exchange Server

- SharePoint Server

- Servidores de ficheiros do Windows Server que suportam a Infraestrutura de Classificação de Ficheiros

Para obter informações sobre os requisitos adicionais para este cenário, consulte [Servidores no local que suportam a proteção de dados do Azure Rights Management](requirements-servers.md).

### <a name="coexistence-of-ad-rms-with-azure-rms"></a>Coexistência do AD RMS com o Azure RMS

O cenário de implementação seguinte não é suportado, exceto se estiver a utilizar o AD RMS para [proteção do HYOK](configure-adrms-restrictions.md) com o Azure Information Protection (a configuração "tenha a sua própria chave"):

- Executar o AD RMS e Azure RMS lado a lado na mesma organização, exceto durante a migração, conforme descrito em [migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

Existe um caminho de migração suportados [do AD RMS para o Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx)e a partir [do Azure Information Protection para o AD RMS](/powershell/module/aadrm/Set-AadrmMigrationUrl). Se implementar o Azure Information Protection e, em seguida, decidir que já não quer utilizar este serviço na cloud, consulte [Encerrar e desativar o Azure Information Protection](decommission-deactivate.md).




