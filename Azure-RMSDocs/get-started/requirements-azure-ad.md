---
title: Requisitos do Azure Active Directory para o AIP
description: "Conheça os requisitos do Azure AD para utilizar o Azure Information Protection, para que os utilizadores possam ser autenticados com êxito."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 1422db06905f342f930bce5cd63eb4e08fc8076a
ms.lasthandoff: 02/24/2017


---

# <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Requisitos do Azure Active Directory para o Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Para utilizar o Azure Information Protection, é necessário ter um diretório do Azure AD. A conta da sua organização é utilizada para este diretório de modo a iniciar sessão no portal clássico do Azure onde, por exemplo, pode configurar e gerir modelos de Rights Management.

Se ainda não tiver uma subscrição do Azure para a sua organização, pode obter uma inscrevendo-se numa versão de avaliação gratuita. Aceda à página [Introdução ao Azure](https://account.windowsazure.com/organization) e siga as instruções.

Para obter mais informações, consulte os recursos seguintes na documentação do Azure Active Directory:

-   [O que é o Azure AD Directory?](/active-directory/active-directory-whatis)

-   [Como é que as subscrições do Azure são associadas ao Azure Active Directory](/active-directory/active-directory-how-subscriptions-associated-directory)

Se pretender integrar o seu diretório do Azure AD com as suas florestas do AD no local, consulte [Integrar as identidades no local com o Azure Active Directory](/active-directory/active-directory-aadconnect).

### <a name="scenarios-that-have-specific-requirements"></a>Cenários com requisitos específicos 

Computadores a executar o Office 2010: 

- Se as suas contas de utilizador forem federadas (por exemplo, se utilizar o AD FS), terá de utilizar a Autenticação Integrada do Windows. Neste cenário, a autenticação baseada em formulários não conseguirá autenticar os utilizadores do Azure Information Protection.

Os dispositivos móveis ou computadores Mac que autenticam no local com o AD FS ou um fornecedor de autenticação equivalente:

- É necessário utilizar o AD FS na versão mínima de servidor do **Windows Server 2012 R2** ou num fornecedor de autenticação alternativo que suporte o protocolo OAuth 2.0.

## <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>A autenticação multifator (MFA) e o Azure Information Protection
A utilização da autenticação multifator (MFA) com o Azure Information Protection requer pelo menos um dos seguintes:

-   Office 2013 (versão mínima):

    -   Se tiver o Office 2013, também tem de instalar a [Atualização do Office 2013 de 9 de junho de 2015 (KB3054853)](https://support.microsoft.com/kb/3054853). Para obter mais informações acerca desta atualização e de como a autenticação moderna proporciona ao Office 2013 o início de sessão baseado na Active Directory Authentication Library (ADAL), consulte [Pré-visualização pública da autenticação moderna do Office 2013 comunicada](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) no blogue do Office.

- Cliente do Azure Information Protection:

    - O [cliente do Azure Information Protection](../rms-client/aip-client.md) para Windows, iOS e Android sempre suportou a MFA; não é preciso uma versão mínima. 

-   Aplicação de partilha Rights Management para Windows:

    -   Tem de ter instalada a versão mínima 1.0.1908.0, que pode ser confirmada ao aceder ao Painel de Controlo, Programas e Funcionalidades. Note que a aplicação de Partilha Rights Management está a ser substituída pelo cliente do Azure Information Protection. Para obter mais informações acerca da aplicação de partilha, consulte [Aplicação de partilha Rights Management para Windows](../rms-client/sharing-app-windows.md).

-   Aplicação de partilha Rights Management para dispositivos móveis e computadores Mac:

    -   Certifique-se de que tem a versão mais recente instalada. O suporte à MFA foi introduzido na versão de setembro de 2015 da aplicação de partilha RMS.

Em seguida, configure a sua solução de MFA:

-   Para inquilinos geridos pela Microsoft (que possuem o Azure Active Directory ou Office 365):

    -   Configure a Azure MFA para impor a MFA aos utilizadores. Para obter instruções, consulte [Introdução à Multi-Factor Authentication do Azure na cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) na documentação da Multi-factor Authentication.

        Para obter mais informações acerca da Azure MFA, consulte [O que é a Multi-Factor Authentication do Azure?](/multi-factor-authentication/multi-factor-authentication)

-   Para inquilinos federados (que operam servidores de federação no local):

    -   Configure os servidores de federação para o Azure Active Directory ou Office 365. Por exemplo, se estiver a utilizar o AD FS, consulte [Configurar Métodos de Autenticação Adicionais para o AD FS](https://technet.microsoft.com/library/dn758113.aspx) na TechNet.

        Para obter mais informações acerca deste cenário, consulte [Trabalhos no Office 365 – o programa de identidade está mais simples](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) no blogue do Office.

## <a name="next-steps"></a>Passos seguintes
Para verificar outros requisitos, consulte [Requisitos do Azure Information Protection](requirements-azure-rms.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

