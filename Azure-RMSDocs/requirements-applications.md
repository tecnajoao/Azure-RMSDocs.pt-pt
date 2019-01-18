---
title: Suporte da aplicação para a proteção de dados RMS – AIP
description: Identifique as aplicações que utilizam APIs de RMS para suportar nativamente o serviço Azure Rights Management do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/17/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0f83401b8cac96820f2628a501ca2f731d678126
ms.sourcegitcommit: 2daa75cda8475028a3dac83d70505fcfccef42a1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361805"
---
# <a name="applications-that-support-azure-rights-management-data-protection"></a>Aplicações que suportam a proteção de dados do Azure Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Utilize as tabelas seguintes para identificar as aplicações e as soluções que suportam nativamente o serviço Azure Rights Management (Azure RMS), que proporciona proteção de dados para o Azure Information Protection.

Para estas aplicações e soluções, o suporte do Rights Management está totalmente integrado através das APIs de Rights Management para suportar restrições de utilização. Estas aplicações e soluções também são conhecidas como "otimizadas por RMS".

Salvo indicação em contrário, as capacidades suportadas aplicam-se ao Azure RMS e ao AD RMS. Além disso, o suporte de AD RMS em iOS, Android, macOS e Windows Phone 8.1 necessita [extensão de dispositivo de móveis de serviços do Rights Management Active Directory](https://technet.microsoft.com/library/dn673574.aspx).

## <a name="rms-enlightened-applications"></a>Aplicações otimizadas por RMS

A tabela seguinte apresenta as aplicações de cliente otimizadas por RMS da Microsoft e de fornecedores de software. 

Para obter informações sobre a visualização de documentos PDF protegidos, consulte [leitores de PDF protegido para o Microsoft Information Protection](./rms-client/protected-pdf-readers.md).

Informações acerca das colunas da tabela:

-   **Email:** Os clientes de e-mail listados podem proteger a própria mensagem de e-mail, que protege automaticamente quaisquer ficheiros do Office anexados que já não estão protegidos. Neste cenário, a funcionalidade de pré-visualização do cliente pode apresentar o conteúdo protegido (mensagem e anexos) aos destinatários autorizados. No entanto, se uma mensagem de e-mail em si não estiver protegida mas o anexo estiver protegido, a funcionalidade de pré-visualização do cliente não conseguirá apresentar o anexo protegido aos destinatários autorizados. 
    
    Sugestão: E-mail de clientes que não suportam proteger mensagens de e-mail, considere a utilização [regras de fluxo de correio Exchange Online para aplicar esta proteção](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8).

-   **Outros tipos de ficheiro**: Ficheiros de texto e imagem incluem ficheiros que tenham uma extensão de nome de arquivo como. txt,. XML,. jpg e. JPEG. A extensão de nome destes ficheiros é alterada após estes serem nativamente protegidos pelo Rights Management e os mesmos passam a ser só de leitura. Os ficheiros que não podem ser protegidos nativamente têm uma extensão de nome de ficheiro .pfile após serem protegidos genericamente pelo Rights Management. Para obter mais informações, veja os [Tipos de ficheiros suportados](./rms-client/client-admin-guide-file-types.md) no guia do administrador do cliente do Azure Information Protection.


|**Sistema operativo do dispositivo**|Word, Excel, PowerPoint|Email|Outros tipos de ficheiro|
|---------------------------|-----------------------|-----------------|---------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />O Office Online (exibindo documentos protegidos) [[1]](#footnote-1)<br /><br />Navegador da Web [[2]](#footnote-2)|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Navegador da Web [[3]](#footnote-3)<br /><br />Windows Mail [[4]](#footnote-4) |Cliente de proteção de informações do Azure para Windows: Texto, imagens, pfile<br /><br />Aplicação para Windows de partilha do RMS: Texto, imagens, pfile<br /><br />Plug-in do SealPath RMS para AutoCAD:. dwg|
|**iOS**|GigaTrust<br /><br /> Office Mobile (visualização e edição de documentos protegidos)<br /><br />Office Online [[1]](#footnote-1)<br /><br />TITUS Docs<br /><br />Navegador da Web [[2]](#footnote-2)|Aplicação do Azure Information Protection (exibindo o e-mail protegido)<br /><br />Trabalho blackBerry<br /><br />Citrix WorxMail <br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Outlook para iPad e iPhone [[4]](#footnote-4)<br /><br />TITUS Mail <br /><br />Navegador da Web [[3]](#footnote-3)|Aplicação do Azure Information Protection (proteção de texto e imagens de visualização)<br /><br />TITUS Docs: Pfile|
|**Android**|GigaTrust App for Android<br /><br />Office Online [[1]](#footnote-1)<br /><br />Office Mobile <br /><br />Navegador da Web [[2]](#footnote-2)|9Folders [[4]](#footnote-4)<br /><br />Aplicação do Azure Information Protection (ver e-mails protegidos)<br /><br />Trabalho blackBerry <br /><br />GigaTrust App for Android [[4]](#footnote-4)<br /><br />Citrix WorxMail <br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Outlook para Android [[4]](#footnote-4)<br /><br />Samsung Email (S3 e posterior) [[4]](#footnote-4)<br /><br />TITUS Classification for Mobile <br /><br />Navegador da Web [[3]](#footnote-3)|Aplicação do Azure Information Protection (visualização de imagens e texto protegido)|
|**macOS**|Office 2016 para Mac<br /><br />Office Online [[1]](#footnote-1)<br /><br />Navegador da Web [[2]](#footnote-2)|Outlook 2016 para Mac<br /><br />Navegador da Web [[3]](#footnote-3)|(Texto de exibição protegido, imagens, ficheiros protegidos genericamente) de aplicação de partilha RMS|
|**Windows 10 Mobile**|Aplicações móveis do Office (exibindo documentos protegidos com o Azure RMS) <br /><br />Navegador da Web [[2]](#footnote-2)|Citrix WorxMail <br /><br />Correio do Outlook (ver e-mails protegidos) <br /><br />Navegador da Web [[3]](#footnote-3)|Não suportado|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[1]](#footnote-1)<br /><br />Navegador da Web [[2]](#footnote-2)|Outlook 2013 RT<br /><br />Aplicação Correio para Windows<br /><br />Navegador da Web [[3]](#footnote-3)<br /><br />Windows Mail [[4]](#footnote-4)|Siemens JT2Go: Ficheiros JT|
|**Windows Phone 8.1**|Office Mobile (apenas para AD RMS)<br /><br />Navegador da Web [[2]](#footnote-2)|Outlook Mobile [[4]](#footnote-4) <br /><br />Navegador da Web [[3]](#footnote-3)|(Texto de exibição protegido, imagens, ficheiros protegidos genericamente) de aplicação de partilha RMS|
|**Blackberry 10**|Navegador da Web [[2]](#footnote-2)|E-mail Blackberry [[4]](#footnote-4) <br /><br />Navegador da Web [[3]](#footnote-3)|Não suportado|

###### <a name="footnote-1"></a>Nota de rodapé 1
Suportado apenas com o SharePoint Online e OneDrive para empresas e os documentos são desprotegidos antes que eles são carregados para uma biblioteca protegida.

###### <a name="footnote-2"></a>Nota de rodapé 2
Para [anexos do Office](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) que estão protegidos pelo [encriptação de mensagens do Office 365 com os novos recursos](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

###### <a name="footnote-3"></a>Nota de rodapé 3
Se o remetente e o destinatário fazem parte da mesma organização. Ou qualquer uma das seguintes condições:

- O remetente ou o destinatário estiver a utilizar Exchange Online.

- O remetente está a utilizar Exchange no local numa configuração híbrida. 

###### <a name="footnote-4"></a>Nota de rodapé 4
Utiliza a IRM do Exchange ActiveSync, que tem de ser ativada pelo administrador do Exchange. Os utilizadores podem ver, responder e responder a que todas as mensagens de e-mail protegidas, mas os utilizadores não podem proteger novas mensagens de e-mail.
 
Se a aplicação de e-mail não é possível processar a mensagem porque o IRM do Exchange ActiveSync não está ativado, o destinatário pode ver a mensagem de e-mail num navegador da web quando o remetente utiliza o Exchange Online ou Exchange no local numa configuração híbrida. 



### <a name="more-information-about-azure-rms-support-for-office"></a>Mais informações sobre o suporte do Azure RMS para o Office

O Azure RMS está totalmente integrado nas aplicações Word, Excel, PowerPoint e Outlook, sendo esta funcionalidade frequentemente denominada Gestão de Direitos de Informação (IRM). 

Consulte também: [Descrição de serviço de aplicações do Office](https://technet.microsoft.com/library/office-applications-service-description.aspx)

#### <a name="windows-computers-for-information-rights-management-irm"></a>Computadores do Windows para gestão de direitos de informação (IRM)

Os seguintes conjuntos de cliente do Office suportam a proteção de ficheiros e e-mails nos computadores Windows com o serviço Azure Rights Management:

- Office 365 com aplicações do Office 2016 (versão mínima 1805, build 9330.2078) quando o utilizador tem atribuída uma licença do Azure Rights Management (também conhecido como Azure Information Protection para o Office 365)

- Office 365 ProPlus: Office 2016 e Office 2013
    
    Estas edições do Office são incluídas com a maioria dos mas nem todas as subscrições do Office 365 que incluem a proteção de dados do Azure Information Protection. Verifique as informações de subscrição para ver se do Office 365 ProPlus está incluído. Também irá encontrar estas informações no [folha de dados do Azure Information Protection](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010 com Service Pack 2

Todas as edições do Office (à exceção do Office 2007) suportam o consumo de conteúdo protegido.

Quando utiliza o serviço Azure Rights Management com o Office Professional Plus 2010 e o Service Pack 2 ou o Office Professional 2010 com Service Pack 2:

- Exige que o cliente do Azure Information Protection para Windows ou a aplicação de partilha Rights Management para Windows.

- Não é suportado no Windows 10.

- Não suporta autenticação baseada em formulários para contas de utilizador federado. Estas contas devem utilizar Autenticação Integrada do Windows.

- Não suporta a proteção de modelo substituir com permissões personalizadas que um utilizador seleciona com o cliente do Azure Information Protection. Neste cenário, a proteção original pela primeira vez deve ser removida antes de permissões personalizadas podem ser aplicadas.

#### <a name="mac-computers-for-information-rights-management-irm"></a>Computadores MAC para a gestão de direitos de informação (IRM)

Os seguintes conjuntos de aplicações de cliente do Office suportam a proteção de ficheiros e e-mails no macOS com o Azure RMS:

- Office 365 ProPlus: Office 2016

- Office Standard 2016 para Mac

Todas as edições do Office para Mac 2016 suportam o consumo de conteúdo protegido.

Sugestão: Para começar a proteger documentos com o Office para Mac, poderá considerar as seguintes FAQ úteis: [Como posso configurar um computador Mac para proteger e controlar documentos?](faqs-rms.md#how-do-i-configure-a-mac-computer-to-protect-and-track-documents)

### <a name="more-information-about-the-azure-information-protection-app-for-ios-and-android"></a>Mais informações sobre a aplicação Azure Information Protection para iOS e Android

A aplicação Azure Information Protection para iOS e Android fornece um visualizador para mensagens de e-mail protegido por direitos (ficheiros. rpmsg) quando estes dispositivos móveis não tiverem uma aplicação de e-mail que pode abrir e-mails protegidos. Esta aplicação também pode abrir ficheiros PDF protegido por direitos, imagens e arquivos de texto que estão protegido por direitos.

Se os dispositivos iOS e Android inscritos pelo Microsoft Intune, os utilizadores podem instalar a aplicação do Portal da empresa e pode gerir a aplicação através da utilização do Intune [políticas de proteção de aplicações](/intune/app-protection-policies).

Para obter mais informações sobre como utilizar a aplicação, consulte a [FAQ da aplicação do Microsoft Azure Information Protection para iOS e Android](./rms-client/mobile-app-faq.md).


### <a name="more-information-about-the-azure-information-protection-client-for-windows"></a>Mais informações sobre o cliente do Azure Information Protection para Windows

Este cliente substitui agora a aplicação de partilha Rights Management para Windows.

Para mais informações, consulte os seguintes recursos:

- [Guia do administrador de clientes do Azure Information Protection](./rms-client/client-admin-guide.md)

- [Guia do utilizador do cliente do Azure Information Protection](./rms-client/client-user-guide.md)

- [FAQs sobre a aplicação Azure Information Protection para iOS e Android](./rms-client/mobile-app-faq.md)

Transferir a aplicação relevante ao utilizar as ligações na [página Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970).

### <a name="more-information-about-the-rights-management-sharing-application"></a>Mais informações sobre a aplicação de partilha Rights Management

Esta aplicação está a ser substituída pelo cliente do Azure Information Protection. Ele ainda é necessário para dispositivos móveis do Windows Phone ver ficheiros protegidos. 

Para computadores Mac, oferece um visualizador para ficheiros PDF protegidos (. ppdf), protegidos imagens de texto e ficheiros protegidos genericamente. Aplicação de partilha para Mac RMS também pode proteger ficheiros de imagem, mas não a outros ficheiros. Para proteger ficheiros do Office, utilize o Office para Mac. 

Para mais informações, consulte os seguintes recursos:

-   [Guia do administrador da aplicação de partilha Rights Management](./rms-client/sharing-app-admin-guide.md)

-   [Guia do utilizador da aplicação de partilha Rights Management](./rms-client/sharing-app-user-guide.md)

-   [FAQ acerca da Aplicação de Partilha Microsoft Rights Management para Plataformas Móveis](https://technet.microsoft.com/dn451248)

Transferir o Visualizador para computadores Mac e para o Windows Phone ao utilizar as ligações na [página do Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970).


### <a name="more-information-about-other-applications-that-support-azure-information-protection"></a>Mais informações sobre outras aplicações que suportem o Azure Information Protection

Para além das aplicações na tabela, qualquer aplicação que suporte as APIs para o serviço Azure Rights Management pode ser integrada com o Azure Information Protection, que inclui:

- Aplicações de linha de negócio que são escritas internamente através de SDKs RMS

- Aplicações de fornecedores de software que são escritas através de SDKs RMS.

Para obter mais informações, veja o [Guia para Programadores do Azure Information Protection](./develop/developers-guide.md).

### <a name="applications-that-are-not-supported-by-azure-rms"></a>Aplicações que não são suportadas pelo Azure RMS

As aplicações seguintes não são atualmente suportadas pelo Azure RMS incluem o seguinte:

-   Microsoft OneDrive para empresas para o SharePoint Server 2013

-   Visualizador XPS

Além disso, a aplicação de partilha RMS e o cliente do Azure Information Protection têm as seguintes restrições:

-   Para computadores Windows: Requer a versão mínima do Windows 7 Service Pack 1

## <a name="rms-enlightened-solutions"></a>Soluções otimizadas por RMS

A tabela seguinte apresenta as aplicações otimizadas por RMS de fornecedores de software.

Se for um fornecedor de software e tiver uma solução para esta tabela que não esteja listada, registe a sua aplicação no Azure AD. Para obter mais informações, veja [Como registar-se e ativar o RMS na aplicação com o Azure AD](./develop/authentication-integration.md).


|Produto|Fornecedor|Descrição|
|-------------------------------|---------------------------|-----------------|
|Absoluto|Absoluto|Prevenção de perda de dados (DLP) para proteger conteúdo.|
|Content Locker|VMware|Armazena, consome e cria conteúdo protegido.|
|Controle|TakeControle|Deteção de dados eletrónicos através da etiquetagem e da proteção.|
|Forcepoint|Forcepoint DLP|Solução ponto final dados perda prevenção (DLP) para aplicar políticas de segurança de dados de uma organização.|
|Halocore|Secude|Protege os ficheiros que são exportados a partir de ambientes SAP.|
|MaaS 360|IBM|Integração para consumir e proteger documentos.|
|Mobiliya|Mobiliya|Protege os documentos dos repositórios Documentum do EMC.
|Ramessys|Ramessys|Integração para Chemcart e Documentum.
|Sealpath|Sealpath Technologies|Integração com ferramentas de design CAD, como AutoCAD e Siemens Jt2GO.
|SecRMM|Sqaudra Technologies |Proteção de documentos para suporte de dados amovível.
|Security Sheriff|CryptZone |Acede à gestão no SharePoint e protege documentos, consoante as permissões de acesso e de classificação.
|Symantec DLP|Symantec |Deteção e monitorização de ficheiros protegidos.

## <a name="next-steps"></a>Passos Seguintes
Para verificar outros requisitos, consulte [Requisitos do Azure Information Protection](requirements.md).

Para obter mais informações sobre como as aplicações utilizadas com mais frequência suportam o Azure RMS, consulte [Como as aplicações suportam o serviço Azure Rights Management](./applications-support.md).

Para obter informações sobre como configurar as aplicações utilizadas com mais frequência para o Azure RMS, consulte [Configurar aplicações para o Azure Rights Management](configure-applications.md).

