---
title: "Requisitos para o Azure Information Protection – artigo completo"
description: "Identifique os pré-requisitos para implementar o Azure Information Protection para a sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 10cf9371-a61b-495f-9d42-898448806994
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 94259046ed2eb78bce9d7ce49a4dc3b9c99d55c3
ms.lasthandoff: 02/24/2017


---


# <a name="requirements-for-azure-information-protection"></a>Requisitos para o Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*


Antes de implementar o Azure Information Protection na sua organização, certifique-se de que cumpre os seguintes pré-requisitos. 

|Requisito|Mais informações|
|---------------|--------------------|
|Uma subscrição do Azure Information Protection|Consulte as [informações de subscrição](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) e a [lista de funcionalidades](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) no site do Azure Information Protection para certificar-se de que a subscrição da sua organização inclui as funcionalidades do Azure Information Protection que pretende utilizar.|
|Azure Active Directory|A sua organização tem de ter um Azure Active Directory (Azure AD) para suportar a autenticação de utilizador para Azure Information Protection. Além disso, se pretender utilizar as contas de utilizador do seu diretório no local (AD DS), tem também de configurar a integração de diretórios.<br /><br />Se as suas contas forem federadas (por exemplo, se utilizar o AD FS), tem de utilizar a Autenticação Integrada do Windows. A autenticação baseada em formulários não é suportada para Azure Information Protection.<br /><br />A autenticação multifator (MFA) é suportada com o Azure Information Protection quando tem o software de cliente necessário e a infraestrutura de suporte de MFA corretamente configurada.<br /><br />Para mais informações, consulte [Requisitos do Azure Active Directory para o Azure Information Protection](requirements-azure-ad.md).|
|Dispositivos cliente|Os utilizadores têm de ter dispositivos cliente (computador ou dispositivo móvel) com um sistema operativo que suporte o Azure Information Protection.<br /><br />Os seguintes dispositivos suportam o cliente do Azure Information Protection, o qual permite aos utilizadores classificar e etiquetar os documentos e e-mails do Office:<br /><br />– Windows 10 (x86, x64)<br /><br />– Windows 8.1 (x86, x64)<br /><br />– Windows 8 (x86, x64)<br /><br />– Windows 7 Service Pack 1 (x86, x64)<br /><br />Quando este cliente protege os dados através do serviço Azure Rights Management, estes podem ser consumidos pelos mesmos dispositivos (Windows, Mac, iOS, Android) que suportam o serviço Azure Rights Management. <br /><br />Para obter detalhes sobre os dispositivos que suportam o serviço Azure Rights Management, consulte [Dispositivos cliente que suportam a proteção de dados do Azure Rights Management](../get-started/requirements-client-devices.md).|
|Aplicações|O cliente do Azure Information Protection suporta a etiquetagem e a proteção de ficheiros e e-mails criados pelas seguintes aplicações do Office: **Word**, **Excel**, **PowerPoint** e **Outlook** a partir dos seguintes conjuntos de aplicações do Office:<br /><br />– Office Professional Plus 2016<br /><br />– Office Professional Plus 2013 com o Service Pack 1<br /><br />– Office Professional Plus 2010<br /><br />Para obter informações sobre as aplicações que suportam o serviço Azure Rights Management, consulte [Aplicações que suportam a proteção de dados do Azure Rights Management](requirements-applications.md).|
|Infraestrutura que suporta a conetividade à Internet e a serviços cloud dependentes|Se tiver uma firewall ou um dispositivo interveniente semelhante que deve ser configurado para permitir ligações específicas, veja as informações do **Azure Rights Management (RMS)** na secção [Portal do Office 365 e partilhado](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) do seguinte artigo do Office: [URLs do Office 365 e intervalos de endereços IP](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Utilize as instruções neste artigo do Office para se manter atualizado em relação às alterações a estas informações ao subscrever um feed RSS.<br /><br />Além das informações no artigo do Office, específico para o Azure Information Protection:<br /><br />– Permitir tráfego HTTPS em TCP 443 para **api.informationprotection.azure.com**.<br /><br />– Não termine a ligação cliente para serviço TLS (por exemplo, para fazer uma inspeção ao nível do pacote). Se o fizer, quebrará a afixação de certificado que os clientes de RMS utilizam com as AC geridas pela Microsoft para ajudar a proteger as comunicações com o Azure RMS.<br /><br />– Se utilizar um proxy Web que necessite de autenticação, tem de o configurar para utilizar a autenticação integrada do Windows com as credenciais do utilizador para início de sessão no Active Directory.|

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
> Existe um caminho de migração suportado [do AD RMS para o Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) e do [Azure Information Protection para o AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Se implementar o Azure Information Protection e, em seguida, decidir que já não quer utilizar este serviço na cloud, consulte [Encerrar e desativar o Azure Information Protection](../deploy-use/decommission-deactivate.md).

## <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Requisitos do Azure Active Directory para o Azure Information Protection

Para utilizar o Azure Information Protection, é necessário ter um diretório do Azure AD. A conta da sua organização é utilizada para este diretório de modo a iniciar sessão no portal clássico do Azure onde, por exemplo, pode configurar e gerir modelos de Rights Management.

Se ainda não tiver uma subscrição do Azure para a sua organização, pode obter uma ao inscrever-se para uma versão de avaliação gratuita. Aceda à página [Introdução ao Azure](https://account.windowsazure.com/organization) e siga as instruções.

Para obter mais informações, consulte os recursos seguintes na documentação do Azure Active Directory:

-   [O que é o Azure AD Directory?](/active-directory/active-directory-whatis)

-   [Como é que as subscrições do Azure são associadas ao Azure Active Directory](/active-directory/active-directory-how-subscriptions-associated-directory)

Se pretender integrar o seu diretório do Azure AD com as suas florestas do AD no local, consulte [Integrar as identidades no local com o Azure Active Directory](/active-directory/active-directory-aadconnect).

> [!NOTE]
> Se tiver dispositivos móveis ou computadores Mac que autenticam no local ao utilizar o AD FS ou um fornecedor de autenticação equivalente:
> 
> -   É necessário utilizar o AD FS na versão mínima de servidor do **Windows Server 2012 R2** ou num fornecedor de autenticação alternativo que suporte o protocolo OAuth 2.0.

### <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>A autenticação multifator (MFA) e o Azure Information Protection
A utilização da autenticação multifator (MFA) com o Azure Information Protection requer pelo menos um dos seguintes:

-   Office 2013 (versão mínima):

    -   Se tiver o Office 2013, também tem de instalar a [Atualização do Office 2013 de 9 de junho de 2015 (KB3054853)](https://support.microsoft.com/kb/3054853). Para obter mais informações acerca desta atualização e de como a autenticação moderna proporciona ao Office 2013 o início de sessão baseado na Active Directory Authentication Library (ADAL), consulte [Pré-visualização pública da autenticação moderna do Office 2013 comunicada](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) no blogue do Office.

-   Aplicação de partilha Rights Management para Windows:

    -   Tem de ter instalada a versão mínima 1.0.1908.0, que pode ser confirmada ao aceder ao Painel de Controlo, Programas e Funcionalidades. Para obter mais informações acerca da aplicação de partilha, consulte [Aplicação de partilha Rights Management para Windows](../rms-client/sharing-app-windows.md).

-   Aplicação de partilha Rights Management para dispositivos móveis e computadores Mac:

    -   Certifique-se de que tem a versão mais recente instalada. O suporte à MFA foi introduzido na versão de setembro de 2015 da aplicação de partilha RMS.

Em seguida, configure a sua solução de MFA:

-   Para inquilinos geridos pela Microsoft (que possuem o Azure Active Directory ou Office 365):

    -   Configure a Azure MFA para impor a MFA aos utilizadores. Para obter instruções, consulte [Introdução à Multi-Factor Authentication do Azure na cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) na documentação da Multi-factor Authentication.

        Para obter mais informações acerca da Azure MFA, consulte [O que é a Multi-Factor Authentication do Azure?](/multi-factor-authentication/multi-factor-authentication)

-   Para inquilinos federados (que operam servidores de federação no local):

    -   Configure os servidores de federação para o Azure Active Directory ou Office 365. Por exemplo, se estiver a utilizar o AD FS, consulte [Configurar Métodos de Autenticação Adicionais para o AD FS](https://technet.microsoft.com/library/dn758113.aspx) na TechNet.

        Para mais informações acerca deste cenário, consulte [The Works with Office 365 � Identity program now streamlined (Programa Funciona com o Office 365 – Identidade, agora simplificado – em inglês)](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) no blogue do Office.

## <a name="client-devices-that-support-azure-rights-management-data-protection"></a>Dispositivos cliente que suportam a proteção de dados do Azure Rights Management

Utilize as secções seguintes para identificar os dispositivos que suportam o serviço Azure Rights Management, que fornece proteção de dados para o Azure Information Protection.

### <a name="computers"></a>Computadores
Os seguintes sistemas operativos de computador suportam o serviço Azure Rights Management:

-   **Windows 7** (x86, x64)

-   **Windows 8** (x86, x64)

-   **Windows 8.1** (x86, x64)

-   **Windows 10** (x86, x64)

-   **Mac OS X**: versão mínima do Mac OS X 10.8 (Mountain Lion)

### <a name="mobile-devices"></a>Dispositivos móveis
Os seguintes sistemas operativos de dispositivo móvel suportam o serviço Azure Rights Management:

-   **Windows Phone**: Windows Phone 8.1

-   **Telemóveis e tablets Android**: versão mínima do Android 4.0.3

-   **iPhone e iPad**: versão mínima do iOS 7.0

-   **Tablets Windows**: Windows 10 Mobile e Windows 8.1 RT

## <a name="applications-that-support-azure-rights-management-data-protection"></a>Aplicações que suportam a proteção de dados do Azure Rights Management

Utilize a seguinte tabela para identificar as aplicações que suportam nativamente o serviço Azure Rights Management (Azure RMS), que fornece proteção de dados para o Azure Information Protection. 

Para estas aplicações, o suporte do Rights Management está totalmente integrado através das APIs de Rights Management para suportar restrições de utilização. Estas aplicações também são conhecidas como otimizadas por RMS.

Salvo indicação em contrário, as capacidades suportadas aplicam-se ao Azure RMS e ao AD RMS. Além disso, o suporte do AD RMS em iOS, Android, OS X e Windows Phone 8.1 necessita da [Extensão de Dispositivos Móveis dos Serviços de Gestão de Direitos do Active Directory](https://technet.microsoft.com/library/dn673574.aspx).

Informações acerca das colunas da tabela:

-   **PDF protegido**: ficheiros que têm uma extensão de nome de ficheiro .ppdf e que são criados automaticamente quando utiliza a aplicação de partilha RMS para partilhar ficheiros do Office e ficheiros PDF por e-mail. A aplicação de partilha RMS e a aplicação Azure Information Protection para iOS e Android incluem um leitor para ficheiros PDF protegidos. Se anteriormente tiver criado ficheiros PDF que protegeu ao utilizar o Azure RMS ou o AD RMS, pode continuar a ler estes ficheiros em dispositivos com Windows, iOS e Android através do Foxit Reader e do Nitro Pro.

-   **E-mail:** os clientes de e-mail listados podem proteger a própria mensagem de e-mail, que protegerá automaticamente quaisquer ficheiros anexados. Neste cenário, a funcionalidade de pré-visualização do cliente pode apresentar os conteúdos protegidos (mensagem e anexos) aos destinatários autorizados. No entanto, se uma mensagem de e-mail em si não estiver protegida mas o anexo estiver protegido, a funcionalidade de pré-visualização do cliente não conseguirá apresentar o anexo protegido aos destinatários autorizados.

-   **Outros tipos de ficheiro**: os ficheiros de texto e imagem incluem ficheiros que tenham uma extensão de nome de ficheiro .txt, .xml, .jpg e .jpeg. A extensão de nome destes ficheiros é alterada após estes serem nativamente protegidos pelo Rights Management e os mesmos passam a ser só de leitura. Os ficheiros que não podem ser protegidos nativamente têm uma extensão de nome de ficheiro .pfile após serem protegidos genericamente pelo Rights Management. Para obter mais informações, consulte o [Guia do administrador da aplicação de partilha Rights Management](../rms-client/sharing-app-admin-guide.md).


|**Sistema operativo do dispositivo**|Word, Excel, PowerPoint|PDF protegido|E-mail|Outros tipos de ficheiro|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Aplicações do Office Mobile (apenas para Azure RMS) [[1]](#footnote-1)<br /><br />Office Online [[2]](#footnote-2)|Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />Aplicação de partilha RMS|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Outlook Web App (OWA) [[3]](#footnote-3)<br /><br />Windows Mail [[4]](#footnote-4)|Aplicação de partilha RMS para Windows: texto, imagens, pfile<br /><br />Siemens JT2Go: ficheiros JT (apenas para Windows 10)|
|**iOS**|Office para iPad e iPhone [[5]](#footnote-5)<br /><br />Office Online [[2]](#footnote-2)<br /><br />TITUS Docs|Aplicação Azure Information Protection [[1]](#footnote-1)<br /><br /> Foxit Reader<br /><br />TITUS Docs|Aplicação Azure Information Protection [[1]](#footnote-1)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Outlook para iPad e iPhone [[4]](#footnote-4)<br /><br />OWA para iOS [[3]](#footnote-3)<br /><br />TITUS Mail|Aplicação Azure Information Protection [[1]](#footnote-1): texto, imagens<br /><br />TITUS Docs: Pfile|
|**Android**|GigaTrust App for Android<br /><br />Office Online [[2]](#footnote-2)<br /><br />Office Mobile (apenas Azure RMS) [[1]](#footnote-1)|Aplicação Azure Information Protection [[1]](#footnote-1)<br /><br />GigaTrust App for Android<br /><br />Foxit Reader<br /><br />Aplicação de partilha RMS [[1]](#footnote-1)|9Folders [[4]](#footnote-4)<br /><br />Aplicação Azure Information Protection [[1]](#footnote-1)<br /><br />GigaTrust App for Android [[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Outlook para Android [[4]](#footnote-4)<br /><br />OWA para Android [[3]](#footnote-3) e [[7]](#footnote-7)<br /><br />Samsung Email (S3 e posterior) [[7]](#footnote-7)<br /><br />TITUS Classification for Mobile|Aplicação Azure Information Protection [[1]](#footnote-1): texto, imagens|
|**OS X**|Office 2011 (apenas para AD RMS)<br /><br />Office 2016 para Mac<br /><br />Office Online [[2]](#footnote-2)|Foxit Reader<br /><br />Aplicação de partilha RMS [[1]](#footnote-1)|Outlook 2011 (apenas para AD RMS)<br /><br />Outlook 2016 para Mac<br /><br />Outlook para Mac|Aplicação de partilha RMS [[1]](#footnote-1): texto, imagens, pfile|
|**Windows 10 Mobile**|Aplicações do Office Mobile (apenas para Azure RMS)[[1]](#footnote-1)|Não suportado|Citrix WorxMail [[6]](#footnote-6)<br /><br />Correio do Outlook|Não suportado|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[2]](#footnote-2)|Não suportado|Outlook 2013 RT<br /><br />Aplicação Correio para Windows<br /><br />Windows Mail [[4]](#footnote-4)|Siemens JT2Go: ficheiros JT|
|**Windows Phone 8.1**|Office Mobile (apenas para AD RMS)|Aplicação de partilha RMS [[1]](#footnote-1)|Outlook Mobile [[4]](#footnote-4)|Aplicação de partilha RMS [[1]](#footnote-1): texto, imagens, pfile|
|**Blackberry 10**|Não suportado|Não suportado|E-mail Blackberry [[4]](#footnote-4)|Não suportado|


##### <a name="footnote-1"></a>Nota de rodapé 1
Suporta a visualização de conteúdo protegido.

##### <a name="footnote-2"></a>Nota de rodapé 2 
Suporta a visualização de documentos protegidos quando um documento desprotegido é carregado para uma biblioteca protegida no SharePoint Online e no OneDrive para Empresas. 

##### <a name="footnote-3"></a>Nota de rodapé 3
Se um destinatário receber um e-mail protegido e não estiver a utilizar o Exchange como servidor de correio ou se o remetente pertencer a outra organização, este conteúdo só pode ser aberto num cliente de e-mail avançado, como o Outlook. Não é possível abrir este conteúdo no Outlook Web Access.

##### <a name="footnote-4"></a>Nota de rodapé 4
Utiliza a IRM do Exchange ActiveSync, que tem de ser ativada pelo administrador do Exchange. Os utilizadores podem ver, responder e responder a todos em mensagens de e-mail protegidas, mas não podem proteger novas mensagens de e-mail.

Se um destinatário receber um e-mail protegido e não estiver a utilizar o Exchange como servidor de correio ou se o remetente pertencer a outra organização, este conteúdo só pode ser aberto num cliente de e-mail avançado, como o Outlook. Não é possível abrir este conteúdo a partir do Outlook Web Access ou a partir de clientes de correio num dispositivo que utiliza a IRM do Exchange Active Sync.

##### <a name="footnote-5"></a>Nota de rodapé 5
Suporta a visualização e a edição de documentos protegidos. Para obter mais informações, consulte a seguinte publicação no blogue do Office: [Suporte do Azure Rights Management chega ao Office para iPad e iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

##### <a name="footnote-6"></a>Nota de rodapé 6
Para obter mais informações, consulte a [documentação do produto Citrix para WorxMail](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html).

##### <a name="footnote-7"></a>Nota de rodapé 7
Para obter mais informações, consulte a seguinte publicação no blogue do Office: [OWA para Android, agora disponível em determinados dispositivos](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

## <a name="more-information-about-azure-rms-support-for-office"></a>Mais informações sobre o suporte do Azure RMS para o Office

O Azure RMS está totalmente integrado nas aplicações Word, Excel, PowerPoint e Outlook, sendo esta funcionalidade frequentemente denominada Gestão de Direitos de Informação (IRM). As seguintes edições de cliente do Office suportam a proteção de ficheiros e e-mails com o Azure RMS:

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Todas as edições do Office (à exceção do Office 2007) suportam o consumo de conteúdo protegido.

O Azure RMS com Office Professional Plus 2010 ou Office Professional 2010:

- Necessita da aplicação de partilha Rights Management para Windows

- Não suportado no Windows 10

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>Mais informações sobre a aplicação Azure Information Protection para iOS e Android

A aplicação Azure Information Protection para iOS e Android substitui a aplicação de partilha RMS para estes dispositivos. Fornece a mesma funcionalidade e, além disso, suporta mensagens de e-mail e ficheiros PDF protegidos por direitos no SharePoint Online.

Se os dispositivos iOS e Android tiverem sido inscritos pelo Microsoft Intune, pode implementar e gerir esta aplicação com uma aplicação gerida por política. Para obter mais informações, consulte [Configurar e implementar políticas de gestão de aplicações móveis na consola do Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) na documentação do Intune. Para o Passo 2 desta documentação do Intune, utilize as instruções para publicar uma aplicação gerida por política.

Para obter mais informações, consulte [FAQ da aplicação Microsoft Azure Information Protection para iOS e Android](../rms-client/mobile-app-faq.md).


### <a name="more-information-about-the-rights-management-sharing-application"></a>Mais informações sobre a aplicação de partilha Rights Management

Para obter mais informações acerca da aplicação de partilha Rights Management para Windows, consulte os seguintes recursos:

-   [Guia do administrador da aplicação de partilha Rights Management](../rms-client/sharing-app-admin-guide.md)

-   [Guia do utilizador da aplicação de partilha Rights Management](../rms-client/sharing-app-user-guide.md)

Para obter mais informações acerca da aplicação de partilha Rights Management para plataformas móveis, consulte os seguintes recursos:

-   Transferir a aplicação relevante utilizando as ligações na [página Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)

-   [FAQ acerca da Aplicação de Partilha Microsoft Rights Management para Plataformas Móveis](https://technet.microsoft.com/dn451248)

> [!NOTE]
> A aplicação de partilha RMS para iOS e Android foi substituída pela aplicação Azure Information Protection.

### <a name="more-information-about-other-applications-that-support-azure-rms"></a>Mais informações sobre outras aplicações que suportem o Azure RMS

Para além das aplicações na tabela, qualquer aplicação que suporte essas APIs do RMS pode ser integrada com o Azure RMS, que inclui:

- Aplicações de linha de negócio que são escritas internamente através do SDK RMS

- Aplicações de fornecedores de software que são escritas através do SDK RMS.

Para obter mais informações acerca do SDK, consulte o [SDK Microsoft Rights Management](../develop/developers-guide.md).

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Aplicações que não são suportadas pelo Azure RMS

As aplicações seguintes não são atualmente suportadas pelo Azure RMS incluem o seguinte:

-   Microsoft Office para Mac 2011

-   Microsoft OneDrive para Empresas para o SharePoint Server 2013

-   Visualizador XPS
 
Além disso, a aplicação de partilha RMS tem as seguintes restrições:

-   Para computadores com o Windows: necessita de uma versão mínima do Windows 7 Service Pack 1

## <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Servidores no local que suportam a proteção de dados do Azure Rights Management

Os seguintes produtos de servidor no local são suportados com o Azure Information Protection quando utiliza o conector do Azure Rights Management. Este conector funciona como uma interface de comunicação (um reencaminhador) entre os servidores no local e o serviço Azure Rights Management que é utilizado pelo Azure Information Protection para proteger e-mails e documentos do Office. 

Para utilizar este conector, tem de configurar a sincronização de diretórios entre as suas florestas do Active Directory e o Azure Active Directory.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Servidores de ficheiros que executam o Windows Server e utilizam a Infraestrutura de Classificação de Ficheiros (FCI)**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Uma vez que os servidores de ficheiros que executam o Windows Server 2008 R2 não têm uma ação de tarefa de gestão de ficheiros incorporados para aplicar a proteção do Rights Management, não pode utilizar o conector Rights Management para este cenário. No entanto, pode utilizar a Infraestrutura de Classificação de Ficheiros e o Azure RMS nestes sistemas operativos se configurar uma tarefa de gestão de ficheiros personalizada para executar um executável ou um script que possa proteger ficheiros ao utilizar o Azure RMS. Por exemplo, um script do Windows PowerShell que utiliza os [Cmdlets de Proteção RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > Também pode utilizar estes cmdlets com servidores a executar versões posteriores do Windows Server, com a vantagem de estes cmdlets poderem proteger todos os tipos de ficheiro. O conector RMS protege apenas os ficheiros do Office. Para obter instruções sobre como utilizar, consulte [Proteção RMS com Infraestrutura de Classificação de Ficheiros do Windows Server &#40;FCI&#41;](../rms-client/configure-fci.md).

O conector Rights Management é suportado no Windows Server 2012 R2, Windows Server 2012 e Windows Server 2008 R2.

Para mais informações sobre como configurar o conector Rights Management para estes servidores no local, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

