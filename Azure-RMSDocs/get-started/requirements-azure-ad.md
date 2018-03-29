---
title: Requisitos do Azure Active Directory para o AIP
description: Conheça os requisitos do Azure AD para utilizar o Azure Information Protection, para que os utilizadores possam ser autenticados com êxito.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/19/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 82e2fcb1cdbce0476e95b35b0faef7ada7637795
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Requisitos do Azure Active Directory para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Para utilizar o Azure Information Protection, é necessário ter um diretório do Azure AD. Utilizar a sua conta de organização para este diretório para iniciar sessão no portal do Azure, onde, por exemplo, pode configurar e gerir modelos de Rights Management.

Se ainda não tiver uma subscrição do Azure para a sua organização, pode obter uma inscrevendo-se numa versão de avaliação gratuita. Aceda à página [Introdução ao Azure](https://account.windowsazure.com/organization) e siga as instruções.

Para obter mais informações, consulte os recursos seguintes na documentação do Azure Active Directory:

-   [O que é o Azure AD Directory?](/active-directory/active-directory-whatis)

-   [Como é que as subscrições do Azure são associadas ao Azure Active Directory](/active-directory/active-directory-how-subscriptions-associated-directory)

Se pretender integrar o seu diretório do Azure AD com as suas florestas do AD no local, veja [Integrar as identidades no local com o Azure Active Directory](/active-directory/active-directory-aadconnect).

### <a name="scenarios-that-have-specific-requirements"></a>Cenários com requisitos específicos 

Computadores a executar o Office 2010: 

- Os computadores necessitam do [cliente Azure Information Protection](../rms-client/aip-client.md) (recomendado) ou da [aplicação de partilha Rights Management para Windows](../rms-client/sharing-app-windows.md) para se autenticarem no Azure Information Protection e no respetivo serviço de proteção de dados, o Azure Rights Management.

- Se as suas contas de utilizador forem federadas (por exemplo, se utilizar o AD FS), terá de utilizar a Autenticação Integrada do Windows. Neste cenário, a autenticação baseada em formulários não consegue autenticar os utilizadores do Azure Information Protection.

Suporte para a autenticação baseada em certificados (CBA):

- As aplicações do Azure Information Protection para iOS e Android suportam a autenticação baseada em certificado. Para obter instruções sobre como configurar a autenticação baseada em certificados, veja [Começar a utilizar a autenticação baseada em certificados no Azure Active Directory](/azure/active-directory/active-directory-certificate-based-authentication-get-started).

O valor UPN dos utilizadores não corresponde ao endereço de e-mail deles:

- Esta configuração não é recomendada. Se não conseguir alterar o valor UPN, configure um ID de início de sessão alternativo para os utilizadores e diga-lhes como iniciar sessão no Office com esse início de sessão alternativo. Para obter mais informações, veja [Configurar o ID de Início de Sessão Alternativo](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) e [As aplicações do Office pedem periodicamente credenciais para o SharePoint Online, o OneDrive e o Lync Online](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online).
    
    Quando o nome de domínio no valor UPN é um domínio validado para o seu inquilino, adicione o valor UPN do utilizador como outro endereço de e-mail ao atributo proxyAddresses do Azure AD. Esta ação permitirá que seja concedida autorização ao utilizador do Azure Rights Management se o seu valor UPN for especificado durante a concessão dos direitos de utilização. Para obter mais informações sobre isto e sobre como é concedida autorização às contas de utilizador, veja [Preparar utilizadores e grupos para o Azure Information Protection](../plan-design/prepare.md).

Os dispositivos móveis ou computadores Mac que autenticam no local com o AD FS ou um fornecedor de autenticação equivalente:

- É necessário utilizar o AD FS na versão mínima de servidor do **Windows Server 2012 R2** ou num fornecedor de autenticação alternativo que suporte o protocolo OAuth 2.0.

## <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>A autenticação multifator (MFA) e o Azure Information Protection
A utilização da autenticação multifator (MFA) com o Azure Information Protection requer pelo menos um dos seguintes:

-   Office 2013 (versão mínima):

    -   Se tiver o Office 2013, poderá ter de instalar uma atualização adicional para suportar o Azure Active Directory Authentication Library (ADAL). Por exemplo [a atualização de 9 de junho de 2015 para o Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853). Para obter mais informações acerca desta atualização e de como a autenticação moderna proporciona ao Office 2013 o início de sessão baseado na Active Directory Authentication Library (ADAL), veja [Pré-visualização pública da autenticação moderna do Office 2013 comunicada](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) no blogue do Office.

- Cliente do Azure Information Protection:

    - O [cliente do Azure Information Protection](../rms-client/aip-client.md) para Windows, iOS e Android sempre suportou a MFA; não é preciso uma versão mínima. 

-   Aplicação de partilha Rights Management para Windows:

    - Tem de ter instalada a versão mínima 1.0.1908.0, que pode confirmar ao aceder ao Painel de Controlo > Programas e Funcionalidades. Note que a aplicação de Partilha Rights Management está a ser substituída pelo cliente do Azure Information Protection. Para obter mais informações acerca da aplicação de partilha, veja [Aplicação de partilha Rights Management para Windows](../rms-client/sharing-app-windows.md).

-   Aplicação de partilha Rights Management para dispositivos móveis e computadores Mac:

    -   Certifique-se de que tem a versão mais recente instalada. O suporte à MFA foi introduzido na versão de setembro de 2015 da aplicação de partilha RMS.

Em seguida, configure a sua solução de MFA:

-   Para inquilinos geridos pela Microsoft (que possuem o Azure Active Directory ou Office 365):

    - Configure a Azure MFA para impor a MFA aos utilizadores. Para obter instruções, veja [Introdução à Multi-Factor Authentication do Azure na cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) na documentação da Multi-factor Authentication.

        Para obter mais informações acerca da Azure MFA, veja [O que é a Multi-Factor Authentication do Azure?](/multi-factor-authentication/multi-factor-authentication)

- Para inquilinos federados (que operam servidores de federação no local):

    - Configure os servidores de federação para o Azure Active Directory ou Office 365. Por exemplo, se estiver a utilizar o AD FS, veja [Configurar Métodos de Autenticação Adicionais para o AD FS](https://technet.microsoft.com/library/dn758113.aspx) na TechNet.

        Para obter mais informações acerca deste cenário, veja [Trabalhos no Office 365 – o programa de identidade está mais simples](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) no blogue do Office.

O conector Rights Management e a análise do Azure Information Protection não suportam MFA. Se implementar o conector ou scanner, as seguintes contas não devem necessitar de MFA:

- A conta que instala e configura o conector.

- A conta do principal de serviço no Azure AD, **Aadrm_S-1-7-0**, que cria o conector.
 
- A conta de serviço que executa o verificador.

## <a name="next-steps"></a>Próximos passos
Para verificar outros requisitos, veja [Requisitos do Azure Information Protection](requirements-azure-rms.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
