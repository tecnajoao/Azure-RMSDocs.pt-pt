---
title: "Suporte da aplicação para a proteção de dados RMS – AIP"
description: "Identifique as aplicações que utilizam APIs de RMS para suportar nativamente o serviço Azure Rights Management do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 2c80ff43c07eab80527a3cb764ff3030f2459657
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/30/2017
---
<a id="applications-that-support-azure-rights-management-data-protection" class="xliff"></a>

# Aplicações que suportam a proteção de dados do Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*


Utilize as tabelas seguintes para identificar as aplicações e as soluções que suportam nativamente o serviço Azure Rights Management (Azure RMS), que proporciona proteção de dados para o Azure Information Protection. 

Para estas aplicações e soluções, o suporte do Rights Management está totalmente integrado através das APIs de Rights Management para suportar restrições de utilização. Estas aplicações e soluções também são conhecidas como “otimizadas por RMS”.

Salvo indicação em contrário, as capacidades suportadas aplicam-se ao Azure RMS e ao AD RMS. Além disso, o suporte do AD RMS em iOS, Android, macOS e Windows Phone 8.1 necessita da [Extensão de Dispositivos Móveis dos Serviços de Gestão de Direitos do Active Directory](https://technet.microsoft.com/library/dn673574.aspx).

<a id="rms-enlightened-applications" class="xliff"></a>

## Aplicações otimizadas por RMS

A tabela seguinte apresenta as aplicações de cliente otimizadas por RMS da Microsoft e de fornecedores de software.

Informações acerca das colunas da tabela:

-   **PDF protegido**: estes ficheiros podem ter uma extensão de nome de ficheiro .pdf ou .ppdf.

-   **E-mail:** os clientes de e-mail listados podem proteger a própria mensagem de e-mail, que protegerá automaticamente quaisquer ficheiros do Office anexados que já não estejam protegidos. Neste cenário, a funcionalidade de pré-visualização do cliente pode apresentar o conteúdo protegido (mensagem e anexos) aos destinatários autorizados. No entanto, se uma mensagem de e-mail em si não estiver protegida mas o anexo estiver protegido, a funcionalidade de pré-visualização do cliente não conseguirá apresentar o anexo protegido aos destinatários autorizados.

-   **Outros tipos de ficheiro**: os ficheiros de texto e imagem incluem ficheiros que tenham uma extensão de nome de ficheiro .txt, .xml, .jpg e .jpeg. A extensão de nome destes ficheiros é alterada após estes serem nativamente protegidos pelo Rights Management e os mesmos passam a ser só de leitura. Os ficheiros que não podem ser protegidos nativamente têm uma extensão de nome de ficheiro .pfile após serem protegidos genericamente pelo Rights Management. Para obter mais informações, veja os [Tipos de ficheiros suportados](../rms-client/client-admin-guide-file-types.md) no guia do administrador do cliente do Azure Information Protection.


|**Sistema operativo do dispositivo**|Word, Excel, PowerPoint|PDF protegido|E-mail|Outros tipos de ficheiro|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Aplicações do Office Mobile (apenas para Azure RMS) [[1]](#footnote-1)<br /><br />Office Online [[2]](#footnote-2)|Cliente do Azure Information Protection para Windows <br /><br />Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />Aplicação de partilha RMS|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Outlook Web App (OWA) [[3]](#footnote-3)<br /><br />Windows Mail [[4]](#footnote-4)|Cliente do Azure Information Protection para Windows: texto, imagens, pfile<br /><br />Aplicação de partilha RMS para Windows: texto, imagens, pfile<br /><br />Plug-in do SealPath RMS para AutoCAD [[8]](#footnote-8): .dwg<br />|
|**iOS**|Office para iPad e iPhone [[5]](#footnote-5)<br /><br />Office Online [[2]](#footnote-2)<br /><br />TITUS Docs|Aplicação Azure Information Protection [[1]](#footnote-1)<br /><br /> Foxit Reader<br /><br />TITUS Docs|Aplicação Azure Information Protection [[1]](#footnote-1)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Outlook para iPad e iPhone [[4]](#footnote-4)<br /><br />OWA para iOS [[3]](#footnote-3)<br /><br />TITUS Mail|Aplicação Azure Information Protection [[1]](#footnote-1): texto, imagens<br /><br />TITUS Docs: Pfile|
|**Android**|GigaTrust App for Android<br /><br />Office Online [[2]](#footnote-2)<br /><br />Office Mobile [[1]](#footnote-1)|Aplicação Azure Information Protection [[1]](#footnote-1)<br /><br />GigaTrust App for Android<br /><br />Foxit Reader<br /><br />Aplicação de partilha RMS [[1]](#footnote-1)|9Folders [[4]](#footnote-4)<br /><br />Aplicação Azure Information Protection [[1]](#footnote-1)<br /><br />GigaTrust App for Android [[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Outlook para Android [[4]](#footnote-4)<br /><br />OWA para Android [[3]](#footnote-3) e [[7]](#footnote-7)<br /><br />Samsung Email (S3 e posterior) [[7]](#footnote-7)<br /><br />TITUS Classification for Mobile|Aplicação Azure Information Protection [[1]](#footnote-1): texto, imagens|
|**macOS**|Office 2011 (apenas para AD RMS)<br /><br />Office 2016 para Mac<br /><br />Office Online [[2]](#footnote-2)|Foxit Reader<br /><br />Aplicação de partilha RMS [[1]](#footnote-1)|Outlook 2011 (apenas para AD RMS)<br /><br />Outlook 2016 para Mac<br /><br />Outlook para Mac|Aplicação de partilha RMS [[1]](#footnote-1): texto, imagens, pfile|
|**Windows 10 Mobile**|Aplicações do Office Mobile (apenas para Azure RMS) [[1]](#footnote-1)|Não suportado|Citrix WorxMail [[6]](#footnote-6)<br /><br />Correio do Outlook|Não suportado|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[2]](#footnote-2)|Não suportado|Outlook 2013 RT<br /><br />Aplicação Correio para Windows<br /><br />Windows Mail [[4]](#footnote-4)|Siemens JT2Go: ficheiros JT|
|**Windows Phone 8.1**|Office Mobile (apenas para AD RMS)|Aplicação de partilha RMS [[1]](#footnote-1)|Outlook Mobile [[4]](#footnote-4)|Aplicação de partilha RMS [[1]](#footnote-1): texto, imagens, pfile|
|**Blackberry 10**|Não suportado|Não suportado|E-mail Blackberry [[4]](#footnote-4)|Não suportado|


<a id="footnote-1" class="xliff"></a>

###### Nota de rodapé 1
Suporta a visualização de conteúdo protegido.

<a id="footnote-2" class="xliff"></a>

###### Nota de rodapé 2 
Suporta a visualização de documentos protegidos quando um documento desprotegido é carregado para uma biblioteca protegida no SharePoint Online e no OneDrive para Empresas. 

<a id="footnote-3" class="xliff"></a>

###### Nota de rodapé 3
Se um destinatário receber um e-mail protegido e não estiver a utilizar o Exchange como servidor de correio ou se o remetente pertencer a outra organização, este conteúdo só pode ser aberto num cliente de e-mail avançado, como o Outlook. Não é possível abrir este conteúdo no Outlook Web Access.

<a id="footnote-4" class="xliff"></a>

###### Nota de rodapé 4
Utiliza a IRM do Exchange ActiveSync, que tem de ser ativada pelo administrador do Exchange. Os utilizadores podem ver, responder e responder a todos em mensagens de e-mail protegidas, mas não podem proteger novas mensagens de e-mail.

Se um destinatário receber um e-mail protegido e não estiver a utilizar o Exchange como servidor de correio ou se o remetente pertencer a outra organização, este conteúdo só pode ser aberto num cliente de e-mail avançado, como o Outlook. Não é possível abrir este conteúdo a partir do Outlook Web Access ou a partir de clientes de correio num dispositivo que utiliza a IRM do Exchange Active Sync.

<a id="footnote-5" class="xliff"></a>

###### Nota de rodapé 5
Suporta a visualização e a edição de documentos protegidos para iOS. Para obter mais informações, consulte a seguinte publicação no blogue do Office: [Suporte do Azure Rights Management chega ao Office para iPad e iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

<a id="footnote-6" class="xliff"></a>

###### Nota de rodapé 6
Para obter mais informações, consulte a [documentação do produto Citrix para WorxMail](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html).

<a id="footnote-7" class="xliff"></a>

###### Nota de rodapé 7
Para obter mais informações, consulte a seguinte publicação no blogue do Office: [OWA para Android, agora disponível em determinados dispositivos](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

<a id="footnote-8" class="xliff"></a>

###### Nota de rodapé 8
Para obter mais informações, veja a seguinte mensagem no Enterprise and Mobility Blog: [SealPath brings RMS protection to AutoCAD (SealPath proporciona proteção RMS para AutoCAD)](https://blogs.technet.microsoft.com/enterprisemobility/2015/09/08/sealpath-brings-rms-protection-to-autocad/)


<a id="more-information-about-azure-rms-support-for-office" class="xliff"></a>

### Mais informações sobre o suporte do Azure RMS para o Office

O Azure RMS está totalmente integrado nas aplicações Word, Excel, PowerPoint e Outlook, sendo esta funcionalidade frequentemente denominada Gestão de Direitos de Informação (IRM). As seguintes edições de cliente do Office suportam a proteção de ficheiros e e-mails com o Azure RMS:

- Office 365 ProPlus: Office 2016 e Office 2013

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Todas as edições do Office (à exceção do Office 2007) suportam o consumo de conteúdo protegido.

O Azure RMS com Office Professional Plus 2010 ou Office Professional 2010:

- Precisa do cliente do Azure Information Protection para Windows ou da aplicação de partilha Rights Management para Windows

- Não suportado no Windows 10

- Não suporta autenticação baseada em formulários para contas de utilizador federado. Estas contas devem utilizar Autenticação Integrada do Windows.

<a id="more-information-about-the-azure-information-protection-app-for-ios-and-android" class="xliff"></a>

### Mais informações sobre a aplicação Azure Information Protection para iOS e Android

A aplicação Azure Information Protection para iOS e Android substitui a aplicação de partilha RMS para estes dispositivos. Fornece a mesma funcionalidade e, além disso, suporta mensagens de e-mail e ficheiros PDF protegidos por direitos no SharePoint Online.

Se os dispositivos iOS e Android tiverem sido inscritos pelo Microsoft Intune, pode implementar e gerir esta aplicação com uma aplicação gerida por política. Para obter mais informações, consulte [Configurar e implementar políticas de gestão de aplicações móveis na consola do Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) na documentação do Intune. Para o Passo 2 desta documentação do Intune, utilize as instruções para publicar uma aplicação gerida por política.

Para obter mais informações, consulte [FAQ da aplicação Microsoft Azure Information Protection para iOS e Android](../rms-client/mobile-app-faq.md).


<a id="more-information-about-the-azure-information-protection-client-for-windows" class="xliff"></a>

### Mais informações sobre o cliente do Azure Information Protection para Windows

Este cliente substitui agora a aplicação de partilha Rights Management para Windows. 

Para mais informações, consulte os seguintes recursos:

- [Guia do administrador de clientes do Azure Information Protection](../rms-client/client-admin-guide.md)

- [Guia do utilizador do cliente do Azure Information Protection](../rms-client/client-user-guide.md)

- [FAQs sobre a aplicação Azure Information Protection para iOS e Android](../rms-client/mobile-app-faq.md)

Transferir a aplicação relevante ao utilizar as ligações na [página Microsoft Azure Information Protection](http://go.microsoft.com/fwlink/?LinkId=303970).

<a id="more-information-about-the-rights-management-sharing-application" class="xliff"></a>

### Mais informações sobre a aplicação de partilha Rights Management

Esta aplicação está a ser substituída pelo cliente do Azure Information Protection. Continua a ser obrigatória para computadores Mac e dispositivos móveis Windows Phone. 

Para mais informações, consulte os seguintes recursos:

-   [Guia do administrador da aplicação de partilha Rights Management](../rms-client/sharing-app-admin-guide.md)

-   [Guia do utilizador da aplicação de partilha Rights Management](../rms-client/sharing-app-user-guide.md)

-   [FAQ acerca da Aplicação de Partilha Microsoft Rights Management para Plataformas Móveis](https://technet.microsoft.com/dn451248)

Transfira a aplicação para computadores Mac e para o Windows Phone ao utilizar as ligações na [página Microsoft Azure Information Protection](http://go.microsoft.com/fwlink/?LinkId=303970).


<a id="more-information-about-other-applications-that-support-azure-information-protection" class="xliff"></a>

### Mais informações sobre outras aplicações que suportem o Azure Information Protection

Para além das aplicações na tabela, qualquer aplicação que suporte as APIs para o serviço Azure Rights Management pode ser integrada com o Azure Information Protection, que inclui:

- Aplicações de linha de negócio que são escritas internamente através de SDKs RMS

- Aplicações de fornecedores de software que são escritas através de SDKs RMS.

Para obter mais informações, veja o [Guia para Programadores do Azure Information Protection](../develop/developers-guide.md).

<a id="applications-that-are-not-supported-by-azure-rms" class="xliff"></a>

### Aplicações que não são suportadas pelo Azure RMS

As aplicações seguintes não são atualmente suportadas pelo Azure RMS incluem o seguinte:

-   Microsoft Office para Mac 2011

-   Microsoft OneDrive para Empresas para o SharePoint Server 2013

-   Visualizador XPS
 
Além disso, a aplicação de partilha RMS e o cliente do Azure Information Protection tem as seguintes restrições:

-   Para computadores com o Windows: necessita de uma versão mínima do Windows 7 Service Pack 1

<a id="rms-enlightened-solutions" class="xliff"></a>

## Soluções otimizadas por RMS

A tabela seguinte apresenta as aplicações otimizadas por RMS de fornecedores de software.

Se for um fornecedor de software e tiver uma solução para esta tabela que não esteja listada, registe a sua aplicação no Azure AD. Para obter mais informações, veja [Como registar-se e ativar o RMS na aplicação com o Azure AD](../develop/authentication-integration.md).


|Produto|Fornecedor|Descrição|
|-------------------------------|---------------------------|-----------------|
|Absoluto|Absoluto|Prevenção de perda de dados (DLP) para proteger conteúdo.|
|Content Locker|VMware|Armazena, consome e cria conteúdo protegido.|
|Controle|TakeControle|Deteção de dados eletrónicos através da etiquetagem e da proteção.|
|Halocore|Secude|Protege os ficheiros que são exportados a partir de ambientes SAP.|
|MaaS 360|IBM|Integração para consumir e proteger documentos.|
|Mobiliya|Mobiliya|Protege os documentos dos repositórios Documentum do EMC.
|Ramessys|Ramessys|Integração para Chemcart e Documentum.
|Sealpath|Sealpath Technologies|Integração com ferramentas de design CAD, como AutoCAD e Siemens Jt2GO.
|SecRMM|Sqaudra Technologies |Proteção de documentos para suporte de dados amovível.
|Security Sheriff|CryptZone |Acede à gestão no SharePoint e protege documentos, consoante as permissões de acesso e de classificação.
|Symantec DLP|Symantec |Deteção e monitorização de ficheiros protegidos.

<a id="next-steps" class="xliff"></a>

## Próximos passos
Para verificar outros requisitos, consulte [Requisitos do Azure Information Protection](requirements-azure-rms.md).

Para obter mais informações sobre como as aplicações utilizadas com mais frequência suportam o Azure RMS, consulte [Como as aplicações suportam o serviço Azure Rights Management](../understand-explore/applications-support.md).

Para obter informações sobre como configurar as aplicações utilizadas com mais frequência para o Azure RMS, consulte [Configurar aplicações para o Azure Rights Management](../deploy-use/configure-applications.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]