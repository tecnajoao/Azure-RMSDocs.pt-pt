---
title: FAQs sobre o Azure Information Protection
description: Algumas perguntas mais frequentes sobre o Azure Information Protection e o respetivo serviço de proteção de dados, o Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/09/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5e78630e39c63f69037dd7288f764c435ff5c81e
ms.sourcegitcommit: ef70dab87478084fca853f389dab2408b95d1df1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304064"
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Perguntas mais frequentes sobre o Azure Information Protection

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Tem uma pergunta sobre o Azure Information Protection ou o serviço Azure Rights Management (Azure RMS)? Verifique se a resposta está aqui.

Essas páginas de FAQ são atualizadas regularmente, com novas adições indicadas nos anúncios de atualização de documentação mensal no [blog técnico do Azure Information Protection](https://aka.ms/AIPblog).

## <a name="whats-the-difference-between-azure-information-protection-and-microsoft-information-protection"></a>O que é a diferença entre o Azure Information Protection e Microsoft Information Protection?

Ao contrário do Azure Information Protection, proteção de informações da Microsoft, não é uma subscrição ou produto que pode comprar. Em vez disso, é uma estrutura para produtos e as capacidades integradas que ajudam a proteger informações confidenciais da sua organização:

- Produtos individuais nessa estrutura incluem o Azure Information Protection, o Office 365 Information Protection (por exemplo, DLP do Office 365), o Windows Information Protection e o Microsoft Cloud App Security. 

- As capacidades integradas nessa estrutura incluem o gerenciamento de etiqueta unificada, experiências de utilizador final etiquetagem incorporadas nas aplicações do Office, a capacidade para Windows compreender as etiquetas unificadas e aplicar a proteção a dados, o SDK do Microsoft Information Protection, e a nova funcionalidade no Adobe Acrobat Reader para ver o nome e protegidas de PDFs.

Para obter mais informações, consulte [anúncio da disponibilidade das funcionalidades de proteção de informações para ajudar a proteger os seus dados confidenciais](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Qual é a diferença entre o Azure Information Protection e o Azure Rights Management?

O Azure Information Protection fornece classificação, etiquetagem e proteção para os documentos e e-mails de uma organização. A tecnologia de proteção utiliza o serviço Azure Rights Management, que agora faz parte do Azure Information Protection.

## <a name="what-is-the-role-of-identity-management-for-azure-information-protection"></a>O que é a função de gestão de identidade do Azure Information Protection?

Um utilizador deve ter um nome de utilizador válido e uma palavra-passe para aceder a conteúdo protegido pelo Azure Information Protection. Para ler mais sobre como o Azure Information Protection o ajuda a proteger os seus dados, veja [A função do Azure Information Protection na proteção de dados](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>De que subscrição preciso para o Azure Information Protection e que funcionalidades estão incluídas?
Ver a lista de informações e recursos de subscrição no [preços do Azure Information Protection](https://azure.microsoft.com/en-us/pricing/details/information-protection) página. 

Se tiver uma subscrição do Office 365 que inclui proteção de dados do Azure Rights Management, transfira o [folha de dados de licenciamento do Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf), que inclui também algumas perguntas mais frequentes sobre o licenciamento.

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>O cliente do Azure Information Protection destina-se apenas a subscrições que incluem classificação e etiquetagem?

Não. Embora a maioria das apresentações e demonstrações que viu do cliente do Azure Information Protection mostrem como suporta a classificação e a etiquetagem, também podem ser utilizadas com as subscrições que incluem apenas o serviço Azure Rights Management para proteger dados.

Quando o cliente do Azure Information Protection para o Windows estiver instalado e não tiver uma política do Azure Information Protection, o cliente funciona automaticamente no [modo apenas de proteção](./rms-client/client-protection-only-mode.md). Neste modo, os utilizadores podem facilmente aplicar modelos e permissões personalizadas do Rights Management. Se posteriormente comprar uma subscrição que inclui classificação e etiquetagem, o cliente mudará automaticamente para o modo padrão quando transfere a política do Azure Information Protection.

Se utilizar atualmente o aplicativo para Windows de partilha Rights Management, recomendamos que substitua esta aplicação com o cliente do Azure Information Protection. Suporte para a aplicação de partilha vai terminar a 31 de Janeiro de 2019. Para ajudar com a transição, veja [Tarefas que costumava realizar com a aplicação de partilha RMS](./rms-client/upgrade-client-app.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Precisa de ser um administrador global para configurar o Azure Information Protection, ou posso delegar noutros administradores?

Os administradores globais de um inquilino do Office 365 ou inquilino do Azure AD podem obviamente executar todas as tarefas administrativas do Azure Information Protection. No entanto, se pretender atribuir permissões administrativas a outros utilizadores, tem as seguintes opções:

- **Administrador do Information Protection**: função de administrador neste Azure Active Directory permite que um administrador configurar todos os aspetos do Azure Information Protection, mas não a outros serviços. Um administrador com esta função pode ativar e desativar o serviço de proteção do Azure Rights Management, configurar as definições de proteção e as etiquetas e configurar a política do Azure Information Protection. Além disso, um administrador com esta função pode executar todos os cmdlets do PowerShell para o [cliente Azure Information Protection](./rms-client/client-admin-guide-powershell.md) e para o [módulo AADRM](administer-powershell.md). 
    
    Para atribuir um utilizador a esta função administrativa, veja [atribuir um utilizador a funções de administrador no Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

- **Administrador de segurança**: função de administrador neste Azure Active Directory permite que um administrador configurar todos os aspetos do Azure Information Protection no portal do Azure, além de configurar alguns aspetos dos outros serviços do Azure. Um administrador com esta função não é possível executar qualquer um da [cmdlets do PowerShell do módulo do AADRM](administer-powershell.md).
    
    Para atribuir um utilizador a esta função administrativa, veja [atribuir um utilizador a funções de administrador no Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Para ver quais outras permissões que um utilizador com esta função tem, consulte a [funções disponíveis](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) secção da documentação do Azure Active Directory.

- O Azure Rights Management **Administrador Global** e **administrador do conector**: para estas funções de administrador do Azure Rights Management, a primeira concede aos usuários permissões para executar todos [ Cmdlets do PowerShell do módulo do AADRM](administer-powershell.md) sem o tornar um administrador global para outros serviços em nuvem e a segunda função concede permissões para executar apenas o conector do Rights Management (RMS). Nenhuma destas funções administrativas concedem permissões para consolas de gestão ou para utilizar o modo de administrador no site de controlo de documentos.

    Para atribuir qualquer uma destas funções administrativas, utilize o cmdlet do PowerShell do AADRM [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator).

Factos a ter em conta:

- Se tiver configurado [controlos de inclusão](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), esta configuração não afeta a capacidade para administrar o Azure Information Protection, exceto o conector RMS. Por exemplo, se tiver configurado controlos de inclusão de para restringir a capacidade de proteger conteúdo ao grupo "Departamento de TI", a conta utilizada para instalar e configurar o conector do RMS tem de ser um membro desse grupo. 

- Os utilizadores que são atribuídos uma função administrativa automaticamente não é possível remover a proteção de documentos ou e-mails que foram protegidos pelo Azure Information Protection. Os utilizadores que estão atribuídos superutilizadores podem fazê-lo, e somente quando a funcionalidade de Superutilizador é ativada. No entanto, qualquer utilizador que atribuir permissões administrativas para o Azure Information Protection pode atribuir utilizadores como superutilizadores, incluindo a sua própria conta. Também pode ativar a funcionalidade de superutilizador. Estas ações são registadas no registo de um administrador. Para obter mais informações, veja a secção de melhores práticas em [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](configure-super-users.md). 

- Se estiver a migrar suas etiquetas do Azure Information Protection para Office 365, certifique-se de que leia a seguinte seção na documentação de migração do rótulo: [informações importantes sobre as funções administrativas](configure-policy-migrate-labels.md#important-information-about-administrative-roles).

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>O Azure Information Protection suporta cenários no local e híbridos?

Sim. Embora o Azure Information Protection seja uma solução baseada na cloud, o mesmo consegue classificar, etiquetar e proteger documentos e e-mails armazenados tanto no local como na cloud.

Se tiver o Exchange Server, SharePoint Server e servidores de ficheiros do Windows, pode implementar o [conector Rights Management](deploy-rms-connector.md) para que estes servidores no local possam utilizar o serviço Azure Rights Management para proteger suas mensagens de e-mail e documentos. Também pode sincronizar e federar os seus controladores de domínio do Active Directory com o Azure AD para uma experiência de autenticação mais integrada para os utilizadores, por exemplo, ao utilizar [do Azure AD Connect](/azure/active-directory/hybrid/whatis-hybrid-identity#what-is-azure-ad-connect).

O serviço Azure Rights Management gera e gere o dos certificados XrML conforme necessário, pelo que não utiliza um PKI no local automaticamente. Para obter mais informações sobre como o Azure Rights Management utiliza certificados, consulte a [instruções sobre como funciona o Azure RMS: primeira utilização, proteção de conteúdos, consumo de conteúdos](./how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) secção a [como o Azure RMS funciona?](./how-does-it-work.md) artigo.

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Que tipos de dados pode do Azure Information Protection classificar e proteger?

O Azure Information Protection pode classificar e proteger mensagens de e-mail e documentos, quer estejam localizado no local ou na cloud. Estes documentos incluem Word documentos, Excel folhas de cálculo, PowerPoint apresentações, PDF documentos, arquivos baseados em texto e arquivos de imagem. Para obter uma lista dos tipos de documentos suportadas, consulte a lista de [tipos de ficheiro suportados](./rms-client/client-admin-guide-file-types.md) no Guia do administrador.

O Azure Information Protection não é possível classificar e proteger os dados estruturados, como ficheiros de base de dados, itens de calendário, relatórios do Power BI, Yammer mensagens, os conteúdos de Sway e blocos de notas do OneNote.

## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Posso ver o Azure Information Protection está indicado como uma aplicação de cloud disponível para o acesso condicional, como faz esse trabalho?

Sim, como pré-visualização pública da oferta, pode agora configurar o acesso condicional do Azure AD para o Azure Information Protection.

Quando um utilizador abre um documento protegido pelo Azure Information Protection, os administradores agora podem bloquear ou conceder acesso aos utilizadores no seu inquilino, com base nos controlos padrão de acesso condicional. Exigir autenticação multifator (MFA) é uma das condições mais pedidas. Outro uma é que dispositivos têm de ser [em conformidade com as políticas do Intune](/intune/conditional-access-intune-common-ways-use) para que, por exemplo, dispositivos móveis cumprem os requisitos de palavra-passe e uma versão mínima do sistema operativo e computadores têm de ser associado a um domínio.

Para obter mais informações e alguns exemplos passo a passo, consulte a seguinte mensagem de blogue: [políticas de acesso condicional do Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/).

Informações adicionais:

- Para computadores Windows: para a versão de pré-visualização atual, as políticas de acesso condicional do Azure Information Protection são avaliadas quando o [ambiente do utilizador é inicializado](./how-does-it-work.md#initializing-the-user-environment) (este processo também é conhecido como arranque do sistema), e em seguida, cada 30 dias.

- Pode querer ajustar a frequência de suas políticas de acesso condicional obterem avaliação. Pode fazê-lo ao configurar a duração do token. Para obter mais informações, consulte [durações de token configuráveis no Azure Active Directory](/azure/active-directory/active-directory-configurable-token-lifetimes).

- Recomendamos que não adiciona as contas de administrador para as políticas de acesso condicional porque estas contas não será capazes de aceder ao painel do Azure Information Protection no portal do Azure.

- Se utilizar a MFA no seu políticas de acesso condicional para colaborar com outras organizações (B2B), tem de utilizar [colaboração B2B do Azure AD](/active-directory/b2b/what-is-b2b) e crie contas de convidado para os utilizadores que pretende partilhar com a da outra organização.

- Se usar muitas aplicações de cloud para o acesso condicional, não poderá ver **Microsoft Azure Information Protection** apresentados na lista para selecionar. Neste caso, utilize a caixa de pesquisa na parte superior da lista. Comece a escrever "Microsoft Azure Information Protection" para filtrar as aplicações disponíveis. Desde que tiver uma subscrição de suporte, em seguida, irá ver **Microsoft Azure Information Protection** para selecionar. 

## <a name="i-see-azure-information-protection-is-listed-as-a-security-provider-for-microsoft-graph-securityhow-does-this-work-and-what-alerts-will-i-receive"></a>Posso ver o Azure Information Protection está listado como um fornecedor de segurança para o Microsoft Graph Security — como este funciona e que alertas recebo?

Sim, como uma oferta de pré-visualização pública, podem agora receber um alerta para **acesso a dados anómalas do Azure Information Protection**. Este alerta é acionado quando existem invulgares tentativas de acesso a dados protegidos pelo Azure Information Protection. Por exemplo, aceder a um volume anormalmente elevado de dados, numa hora invulgar do dia ou aceder a partir de uma localização desconhecida.

Esses alertas podem ajudar a detetar ataques relacionados com dados avançados e ameaças internas no seu ambiente. Estes alertas utilizam o machine learning para criar um perfil do comportamento dos utilizadores que acedem aos seus dados protegidos. 

Os alertas do Azure Information Protection podem ser acedidos por [com a API de segurança do Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/security-api-overview), ou pode [transmitir alertas](https://developer.microsoft.com/en-us/graph/docs/concepts/security_siemintegration) para soluções SIEM, como Splunk e o IBM Qradar, com o Azure Monitor.

Para obter mais informações sobre a API de segurança do Microsoft Graph, consulte [descrição geral da API de segurança do Microsoft Graph](https://developer.microsoft.com/graph/docs/concepts/security-concept-overview).

## <a name="whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365"></a>O que é a diferença entre as etiquetas no Azure Information Protection e as etiquetas no Office 365?

Até recentemente, o Office 365 tinha apenas [etiquetas de retenção](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30) que permitem-lhe classificar documentos e e-mails para auditoria e de retenção, quando esse conteúdo está em serviços do Office 365. Em comparação, o Azure Information Protection etiquetas permitem-lhe aplicar uma política de classificação e proteção consistente para documentos e e-mails, quer estejam no local ou na cloud.

Anunciado na Microsoft Ignite 2018, começará agora ver uma opção para criar e configurar [etiquetas de sensibilidade](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) além das etiquetas de retenção no Centro de conformidade e a segurança do Office 365. Além disso, agora em pré-visualização, pode migrar as etiquetas existentes do Azure Information Protection para o novo arquivo de etiquetagem unificado. 

Para obter mais informações sobre o unified a etiquetagem de gestão e como estas etiquetas sejam suportadas, consulte a postagem no blog [anúncio da disponibilidade das funcionalidades de proteção de informações para ajudar a proteger os seus dados confidenciais](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

Para obter mais informações sobre como migrar as suas etiquetas existentes, consulte [como migrar as etiquetas do Azure Information Protection para o Centro de conformidade e segurança do Office 365](configure-policy-migrate-labels.md).

## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>O que é a diferença entre a FCI do Windows Server e o scanner do Azure Information Protection?

Infraestrutura de classificação de ficheiros do Windows Server tem sido historicamente uma opção para classificar documentos e, em seguida, protegê-los utilizando o [conector Rights Management](deploy-rms-connector.md) (Office documenta apenas) ou um [PowerShell script](./rms-client/configure-fci.md) (todos os tipos de ficheiros). 

Agora, recomendamos que utilize o [scanner do Azure Information Protection](deploy-aip-scanner.md). O scanner utiliza o cliente do Azure Information Protection e a sua política do Azure Information Protection para documentos de etiqueta (todos os tipos de ficheiro), para que esses documentos são, em seguida, classificados e, opcionalmente, protegidos.

As principais diferenças entre essas duas soluções:

|Windows Server FCI|Scanner do Azure Information Protection|
|--------------------------------|-------------------------------------|
|Arquivos de dados suportados: <br /><br />-Pastas locais no Windows Server|Arquivos de dados suportados: <br /><br />-Pastas locais no Windows Server<br /><br />-Windows ficheiro partilhas e armazenamento ligado à rede<br /><br />-O SharePoint Server 2016 e o SharePoint Server 2013. SharePoint Server 2010 também é suportada para os clientes que tenham [suporte para esta versão do SharePoint estendido](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).|
|Modo operacional: <br /><br />-Em Tempo Real|Modo operacional: <br /><br />-Sistematicamente rastreia os arquivos de dados e esse ciclo pode executar uma vez ou repetidamente|
|Suporte para tipos de ficheiro: <br /><br />-Todos os tipos de ficheiros estão protegidos por predefinição <br /><br />-Tipos de ficheiro específicos podem ser excluídos da proteção ao editar o registo|Suporte para tipos de ficheiro: <br /><br />-Tipos de ficheiro office estão protegidos por predefinição <br /><br />-Tipos de ficheiro específicos podem ser incluídos para proteção ao editar o registo|

Atualmente, existe uma diferença na definição do [proprietário do Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) para ficheiros que estão protegidos num compartilhamento de rede ou pasta local. Por predefinição, para ambas as soluções, o proprietário do Rights Management é definido para a conta que protege o ficheiro, mas pode substituir esta definição:

- Para o Windows Server FCI: Pode definir o proprietário do Rights Management para ser uma única conta para todos os ficheiros ou definir dinamicamente o proprietário do Rights Management para cada ficheiro. Para definir dinamicamente o proprietário do Rights Management, utilize o **- OwnerMail [Source File Owner Email]** parâmetro e valor. Esta configuração obtém o endereço de e-mail do utilizador do Active Directory utilizando o nome da conta de utilizador na propriedade proprietário do ficheiro.

- Para o scanner do Azure Information Protection: pode definir o proprietário do Rights Management para ser uma única conta para todos os ficheiros num arquivo de dados especificada, mas não é possível definir dinamicamente o proprietário do Rights Management para cada ficheiro. Para definir a conta, especifique a **- DefaultOwner** parâmetro para o [perfil de repositório de dados](/powershell/module/azureinformationprotection/Set-AIPScannerRepository?view=azureipps#optional-parameters).

Quando a deteção de impressão pode proteger ficheiros em sites do SharePoint e bibliotecas, o proprietário do Rights Management é definido dinamicamente para cada ficheiro ao utilizar o valor de autor do SharePoint.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Já ouvi falar que uma nova versão irá estar disponível em breve para o Azure Information Protection. Quando será lançada?

A documentação técnica não contém informações sobre os lançamentos futuros. Para este tipo de informações e anúncios de lançamento, verifique os [blogue Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity?product=azure-information-protection,azure-rights-management-services) e obter as atualizações mais recentes do [Microsoft Mobility@MSFTMobility ](https://twitter.com/MSFTMobility) no Twitter. Se uma versão do Office que está interessado em, certifique-se de que também consulta os [blogue do Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/bg-p/Office365Blog) e [blogue de aplicações do Office](https://techcommunity.microsoft.com/t5/Office-Apps-Blog/bg-p/OfficeAppsBlog).

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Azure Information Protection é adequado para o meu país?

Países diferentes têm requisitos diferentes e regulamentos. Para ajudar a responder a essa pergunta para a sua organização, consulte [adequação para diferentes países](./compliance.md#suitability-for-different-countries).

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>Como o Azure Information Protection pode ajudar com o GDPR?

Para ver como o Azure Information Protection o pode ajudar-o a cumprir o Regulamento de proteção de dados (GDPR) em geral, consulte o seguinte anúncio de mensagem do blogue, com vídeo: [do Microsoft 365 fornece uma estratégia de proteção de informações para ajudar com o GDPR](https://blogs.office.com/2018/02/22/microsoft-365-provides-an-information-protection-strategy-to-help-with-the-gdpr).

## <a name="where-can-i-find-supporting-information-for-azureinformation-protectionsuch-as-legal-compliance-and-slas"></a>Onde posso encontrar informações de suporte do Azure Information Protection – como legais, conformidade e SLAs?
Veja [Informações de suporte e conformidade do Azure Information Protection](./compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Como posso comunicar um problema ou enviar feedback do Azure Information Protection?

Em alternativa, utilize os canais de suporte padrão ou [contacte o Suporte da Microsoft](information-support.md#to-contact-microsoft-support).

Para enviar feedback, como sugestões de melhorias ou novas funcionalidades: na aplicação do Office, no separador **Base** no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e Feedback**. Na caixa de diálogo **Microsoft Azure Information Protection**, clique em **Envie-nos Os Seus Comentários**. Esta opção abre-se uma mensagem de e-mail para ser enviado à equipa do Information Protection.

É também convidado a interagir com a nossa equipa de engenharia, no [site Yammer do Azure Information Protection](https://www.yammer.com/askipteam/). 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>O que posso fazer se a minha pergunta não constar aqui?

Em primeiro lugar, reveja as seguintes perguntas mais frequentes sobre que são específicas para classificação e etiquetagem ou específicas para proteção de dados. O serviço Azure Rights Management (Azure RMS) fornece a tecnologia de proteção de dados do Azure Information Protection. O Azure RMS pode ser utilizado com classificação e etiquetagem ou por si só. 

- [FAQs sobre a classificação e etiquetagem](faqs-infoprotect.md)

- [FAQs sobre a proteção de dados](faqs-rms.md)

Se não encontrar respostas às suas perguntas, utilize as ligações e os recursos indicados em [Informações e suporte do Azure Information Protection](information-support.md).

Além disso, existem FAQ criadas para os utilizadores finais:

- [FAQ sobre a aplicação Azure Information Protection para iOS e Android](./rms-client/mobile-app-faq.md)

- [FAQ sobre a aplicação de partilha RMS para computadores Mac e Windows Phone](https://technet.microsoft.com/dn451248)

- [FAQ sobre a Aplicação de Partilha Rights Management para Windows](https://technet.microsoft.com/dn467883)



