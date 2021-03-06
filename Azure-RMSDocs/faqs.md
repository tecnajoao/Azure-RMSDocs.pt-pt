---
title: FAQs sobre o Azure Information Protection
description: Algumas perguntas mais frequentes sobre o Azure Information Protection e o respetivo serviço de proteção de dados, o Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/02/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 17e46002486aaca8d09a5a4767a6f976d9acbb82
ms.sourcegitcommit: 729b12e1219c6dbf1bb2a6cfa7239f24d1d13cc5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59364560"
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Perguntas mais frequentes sobre o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Tem uma pergunta sobre o Azure Information Protection ou o serviço Azure Rights Management (Azure RMS)? Verifique se a resposta está aqui.

Essas páginas de FAQ são atualizadas regularmente, com novas adições indicadas nos anúncios de atualização de documentação mensal no [blog técnico do Azure Information Protection](https://aka.ms/AIPblog).

## <a name="whats-the-difference-between-azure-information-protection-and-microsoft-information-protection"></a>O que é a diferença entre o Azure Information Protection e Microsoft Information Protection?

Ao contrário do Azure Information Protection, proteção de informações da Microsoft, não é uma subscrição ou produto que pode comprar. Em vez disso, é uma estrutura para produtos e as capacidades integradas que ajudam a proteger informações confidenciais da sua organização:

- Produtos individuais nessa estrutura incluem o Azure Information Protection, o Office 365 Information Protection (por exemplo, DLP do Office 365), o Windows Information Protection e o Microsoft Cloud App Security. 

- As capacidades integradas nessa estrutura incluem o gerenciamento de etiqueta unificada, experiências de utilizador final etiquetagem incorporadas nas aplicações do Office, a capacidade para Windows compreender as etiquetas unificadas e aplicar a proteção a dados, o SDK do Microsoft Information Protection, e a nova funcionalidade no Adobe Acrobat Reader para ver o nome e protegidas de PDFs.

Para obter mais informações, consulte [anúncio da disponibilidade das funcionalidades de proteção de informações para ajudar a proteger os seus dados confidenciais](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

## <a name="whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365"></a>O que é a diferença entre as etiquetas no Azure Information Protection e as etiquetas no Office 365?

Originalmente, o Office 365 tinha apenas [etiquetas de retenção](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30) que permitem-lhe classificar documentos e e-mails para auditoria e de retenção, quando esse conteúdo está em serviços do Office 365. Em comparação, o Azure Information Protection etiquetas permitem-lhe aplicar uma política de classificação e proteção consistente para documentos e e-mails, quer estejam no local ou na cloud.

Anunciado na Microsoft Ignite 2018 em Orlando, tem agora uma opção para criar e configurar [etiquetas de sensibilidade](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) além das etiquetas de retenção de uma do administrador centra-se: A segurança do Office 365 e Centro de conformidade, o Centro de segurança do Microsoft 365 ou o Centro de conformidade do Microsoft 365. Atualmente em pré-visualização, é possível migrar seu existente do Azure Information Protection etiquetas de etiquetagem unificada novo armazenam, a ser utilizado como rótulos de sensibilidade com o Office 365. 

Para obter mais informações sobre o unified a etiquetagem de gestão e como estas etiquetas sejam suportadas, consulte a postagem no blog [anúncio da disponibilidade das funcionalidades de proteção de informações para ajudar a proteger os seus dados confidenciais](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).

Para obter mais informações sobre como migrar as suas etiquetas existentes, consulte [como migrar as etiquetas do Azure Information Protection para Office 365](configure-policy-migrate-labels.md).

## <a name="when-is-the-right-time-to-migrate-my-labels-to-office-365"></a>Quando é o momento certo para migrar os meus rótulos para Office 365?

Etiquetas de sensibilidade nos centros de administração (segurança do Office 365 e Centro de conformidade, o Centro de segurança do Microsoft 365 e Centro de conformidade do Microsoft 365) estão disponíveis em geral, mas a opção para migrar as suas etiquetas do Azure Information Protection está ainda em pré-visualização. Quando as etiquetas são migradas para a loja de etiquetagem unificada, podem ser publicados e, em seguida, utilizados pelo [os clientes e serviços que suportam a etiquetagem unificada](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling). Hoje em dia, nem todos os clientes suportam etiquetas unificadas ou estão disponíveis em geral.

Recomendamos que teste primeiro a funcionalidade de pré-visualização com um inquilino de teste e, em seguida, migre o seu inquilino de produção. Adicionalmente:

- **Se estiver familiarizado com o Azure Information Protection:** 
    
    Como o Azure Information Protection tem etiquetas predefinidas para acelerar a implementação, recomendamos que primeiro migrar esses etiquetas predefinidas e, em seguida, geri-los a partir de um dos centros de administração.

- **Se não é novidade para o Azure Information Protection, mas no meio de definir e configurar as etiquetas que pretende utilizar:**
    
    Recomendamos que conclua a configuração de etiqueta no portal do Azure e, em seguida, migre as etiquetas. Esta estratégia evita a duplicação de etiquetas durante o processo de migração, que, em seguida, vai ter de ser editado em um dos centros de administração.

Antes de migrar as etiquetas, certifique-se de que compreende os [considerações e configurações de rótulo que não são suportadas pelos centros de administração](configure-policy-migrate-labels.md#considerations-for-unified-labels).

Consulte também [o cliente de pré-visualização instalo nova funcionalidade de teste?](faqs-infoprotect.md#which-preview-client-do-i-install-for-testing-new-functionality)

## <a name="after-ive-migrated-my-labels-which-management-portal-do-i-use"></a>Depois que tiver migrado meus rótulos, do portal de gestão que utilizo?

Depois de ter migrado as etiquetas no portal do Azure:

- Se tiver [unified etiquetagem clientes e serviços](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling), aceda a um dos centros de administração (segurança do Office 365 e Centro de conformidade, o Centro de segurança do Microsoft 365 ou centro de conformidade do Microsoft 365) para publicar estas etiquetas e para Configure as definições de política. Para alterações de etiqueta abaixem reencaminhar, utilize um nestes centros de administração. Os clientes de etiquetas unificados transferem as etiquetas e as definições de política nestes centros de administração.

- Se tiver [os clientes do Azure Information Protection](./rms-client/aip-client.md), continuar a utilizar o portal do Azure para editar os rótulos e as definições de política. Clientes do Azure Information Protection continuam a transferir as etiquetas e as definições de política do Azure.

- Se tiver ambos [unified clientes etiquetas](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling) e [clientes do Azure Information Protection](./rms-client/aip-client.md), pode utilizar os centros de administração ou o portal do Azure para fazer alterações de etiqueta. No entanto, para clientes do Azure Information Protection recolher as alterações de etiqueta que fizer nos centros de administração, tem de devolver ao portal do Azure: Utilize o **Publish** opção da **unificada do Azure Information Protection – etiquetagem** painel no portal do Azure. 

Continuar a utilizar o portal do Azure para [central reporting](reports-aip.md) e o [scanner](deploy-aip-scanner-preview.md).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Qual é a diferença entre o Azure Information Protection e o Azure Rights Management?

O Azure Information Protection fornece classificação, etiquetagem e proteção para os documentos e e-mails de uma organização. A tecnologia de proteção utiliza o serviço Azure Rights Management, que agora faz parte do Azure Information Protection.

## <a name="what-is-the-role-of-identity-management-for-azure-information-protection"></a>O que é a função de gestão de identidade do Azure Information Protection?

Um utilizador deve ter um nome de utilizador válido e uma palavra-passe para aceder a conteúdo protegido pelo Azure Information Protection. Para ler mais sobre como o Azure Information Protection o ajuda a proteger os seus dados, veja [A função do Azure Information Protection na proteção de dados](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>De que subscrição preciso para o Azure Information Protection e que funcionalidades estão incluídas?

Ver a lista de informações e recursos de subscrição no [preços do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection) página.

Se tiver uma subscrição do Office 365 que inclui proteção de dados do Azure Rights Management, transfira o [folha de dados de licenciamento do Azure Information Protection](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Ainda tem dúvidas sobre o licenciamento? Veja se eles são respondidos no [perguntas mais frequentes sobre licenciamento](https://azure.microsoft.com/pricing/details/information-protection#faq) secção.

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>O cliente do Azure Information Protection destina-se apenas a subscrições que incluem classificação e etiquetagem?

Não. Embora a maioria das apresentações e demonstrações que viu do cliente do Azure Information Protection mostrem como suporta a classificação e a etiquetagem, também podem ser utilizadas com as subscrições que incluem apenas o serviço Azure Rights Management para proteger dados.

Quando o cliente do Azure Information Protection para o Windows estiver instalado e não tiver uma política do Azure Information Protection, o cliente funciona automaticamente no [modo apenas de proteção](./rms-client/client-protection-only-mode.md). Neste modo, os utilizadores podem facilmente aplicar modelos e permissões personalizadas do Rights Management. Se posteriormente comprar uma subscrição que inclui classificação e etiquetagem, o cliente mudará automaticamente para o modo padrão quando transfere a política do Azure Information Protection.

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Precisa de ser um administrador global para configurar o Azure Information Protection, ou posso delegar noutros administradores?

Os administradores globais de um inquilino do Office 365 ou inquilino do Azure AD podem obviamente executar todas as tarefas administrativas do Azure Information Protection. No entanto, se pretender atribuir permissões administrativas a outros utilizadores, tem as seguintes opções:

- **Administrador do Information Protection**: Esta função de administrador do Azure Active Directory permite que um administrador configurar todos os aspetos do Azure Information Protection, mas não a outros serviços. Um administrador com esta função pode ativar e desativar o serviço de proteção do Azure Rights Management, configurar as definições de proteção e as etiquetas e configurar a política do Azure Information Protection. Além disso, um administrador com esta função pode executar todos os cmdlets do PowerShell para o [cliente Azure Information Protection](./rms-client/client-admin-guide-powershell.md) e para o [módulo AADRM](administer-powershell.md). 
    
    > [!NOTE]
    > Depois de [migrar o seu inquilino para a loja de etiquetagem unificada](configure-policy-migrate-labels.md), esta função já não é suportada para o portal do Azure.
    
    Para atribuir um utilizador a esta função administrativa, veja [atribuir um utilizador a funções de administrador no Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

- **Administrador de conformidade**: Este Azure Active Directory função de administrador permite que um administrador configurar todos os aspetos do Azure Information Protection, que inclui ativar e desativar o serviço de proteção do Azure Rights Management, configure as definições de proteção e etiquetas, e Configure a política do Azure Information Protection. Além disso, um administrador com esta função pode executar todos os cmdlets do PowerShell para o [cliente Azure Information Protection](./rms-client/client-admin-guide-powershell.md) e para o [módulo AADRM](administer-powershell.md)....
    
    Para atribuir um utilizador a esta função administrativa, veja [atribuir um utilizador a funções de administrador no Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Para ver quais outras permissões que um utilizador com esta função tem, consulte a [funções disponíveis](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) secção da documentação do Azure Active Directory.

- **Leitor de segurança**: Para [analytics do Azure Information Protection](reports-aip.md) apenas. Este Azure Active Directory função de administrador permite que um administrador ver como as etiquetas estão sendo usadas, monitorizar o acesso dos utilizadores a etiquetados de documentos e e-mails e quaisquer alterações à respetiva classificação e pode identificar documentos que contenham informações confidenciais que devem ser protegidas. Uma vez que esse recurso usa o Log Analytics do Azure, também tem de ter um tipo de suporte [função RBAC](reports-aip.md#permissions-required-for-azure-information-protection-analytics).

- **Administrador de segurança**: Esta função de administrador do Azure Active Directory permite que um administrador configurar todos os aspetos do Azure Information Protection no portal do Azure, além de configurar alguns aspetos dos outros serviços do Azure. Um administrador com esta função não é possível executar qualquer um da [cmdlets do PowerShell do módulo do AADRM](administer-powershell.md).
    
    Para atribuir um utilizador a esta função administrativa, veja [atribuir um utilizador a funções de administrador no Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Para ver quais outras permissões que um utilizador com esta função tem, consulte a [funções disponíveis](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) secção da documentação do Azure Active Directory.

- Azure Rights Management **Administrador Global** e **administrador do conector**: Para estas funções de administrador do Azure Rights Management, a primeira concede aos usuários permissões para executar todos [cmdlets do PowerShell do módulo do AADRM](administer-powershell.md) sem o tornar um administrador global para outros serviços em nuvem e a segunda função concede permissões para executar apenas o conector do Rights Management (RMS). Nenhuma destas funções administrativas concedem permissões para consolas de gestão ou para utilizar o modo de administrador no site de controlo de documentos.

    Para atribuir qualquer uma destas funções administrativas, utilize o cmdlet do PowerShell do AADRM [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator).

Factos a ter em conta:

- Se tiver configurado [controlos de inclusão](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), esta configuração não afeta a capacidade para administrar o Azure Information Protection, exceto o conector RMS. Por exemplo, se tiver configurado controlos de inclusão de para restringir a capacidade de proteger conteúdo ao grupo "Departamento de TI", a conta utilizada para instalar e configurar o conector do RMS tem de ser um membro desse grupo. 

- Os utilizadores que são atribuídos uma função administrativa automaticamente não é possível remover a proteção de documentos ou e-mails que foram protegidos pelo Azure Information Protection. Os utilizadores que estão atribuídos superutilizadores podem fazê-lo, e somente quando a funcionalidade de Superutilizador é ativada. No entanto, qualquer utilizador que atribuir permissões administrativas para o Azure Information Protection pode atribuir utilizadores como superutilizadores, incluindo a sua própria conta. Também pode ativar a funcionalidade de superutilizador. Estas ações são registadas no registo de um administrador. Para obter mais informações, veja a secção de melhores práticas em [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](configure-super-users.md). 

- Se estiver a migrar suas etiquetas do Azure Information Protection para o Office 365, certifique-se de que leem a seção a seguir a documentação de migração de etiqueta: [Informações importantes sobre as funções administrativas](configure-policy-migrate-labels.md#important-information-about-administrative-roles).

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>O Azure Information Protection suporta cenários no local e híbridos?

Sim. Embora o Azure Information Protection seja uma solução baseada na cloud, o mesmo consegue classificar, etiquetar e proteger documentos e e-mails armazenados tanto no local como na cloud.

Se tiver o Exchange Server, SharePoint Server e servidores de ficheiros do Windows, pode implementar o [conector Rights Management](deploy-rms-connector.md) para que estes servidores no local possam utilizar o serviço Azure Rights Management para proteger suas mensagens de e-mail e documentos. Também pode sincronizar e federar os seus controladores de domínio do Active Directory com o Azure AD para uma experiência de autenticação mais integrada para os utilizadores, por exemplo, ao utilizar [do Azure AD Connect](/azure/active-directory/hybrid/whatis-azure-ad-connect).

O serviço Azure Rights Management gera e gere o dos certificados XrML conforme necessário, pelo que não utiliza um PKI no local automaticamente. Para obter mais informações sobre como o Azure Rights Management utiliza certificados, consulte o [instruções sobre como funciona o Azure RMS: Primeira utilização, proteção de conteúdos, consumo de conteúdos](./how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) secção do [como o Azure RMS funciona?](./how-does-it-work.md) artigo.

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Que tipos de dados pode do Azure Information Protection classificar e proteger?

O Azure Information Protection pode classificar e proteger mensagens de e-mail e documentos, quer estejam localizado no local ou na cloud. Estes documentos incluem Word documentos, Excel folhas de cálculo, PowerPoint apresentações, PDF documentos, arquivos baseados em texto e arquivos de imagem. Para obter uma lista dos tipos de documentos suportadas, consulte a lista de [tipos de ficheiro suportados](./rms-client/client-admin-guide-file-types.md) no Guia do administrador.

O Azure Information Protection não é possível classificar e proteger os dados estruturados, como ficheiros de base de dados, itens de calendário, relatórios do Power BI, Yammer mensagens, os conteúdos de Sway e blocos de notas do OneNote.

## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Posso ver o Azure Information Protection está indicado como uma aplicação de cloud disponível para o acesso condicional, como faz esse trabalho?

Sim, como uma pré-visualização da oferta, pode agora configurar o acesso condicional do Azure AD para o Azure Information Protection.

Quando um utilizador abre um documento protegido pelo Azure Information Protection, os administradores agora podem bloquear ou conceder acesso aos utilizadores no seu inquilino, com base nos controlos padrão de acesso condicional. Exigir autenticação multifator (MFA) é uma das condições mais pedidas. Outro uma é que dispositivos têm de ser [em conformidade com as políticas do Intune](/intune/conditional-access-intune-common-ways-use) para que, por exemplo, dispositivos móveis cumprem os requisitos de palavra-passe e uma versão mínima do sistema operativo e computadores têm de ser associado a um domínio.

Para obter mais informações e alguns exemplos passo a passo, consulte a seguinte mensagem de blogue: [Políticas de acesso condicional do Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/).

Informações adicionais:

- Para computadores Windows: Para a versão de pré-visualização atual, as políticas de acesso condicional do Azure Information Protection são avaliadas quando o [ambiente do utilizador é inicializado](./how-does-it-work.md#initializing-the-user-environment) (este processo também é conhecido como arranque do sistema) e, em seguida, a cada 30 dias.

- Pode querer ajustar a frequência de suas políticas de acesso condicional obterem avaliação. Pode fazê-lo ao configurar a duração do token. Para obter mais informações, consulte [durações de token configuráveis no Azure Active Directory](/azure/active-directory/active-directory-configurable-token-lifetimes).

- Recomendamos que não adiciona as contas de administrador para as políticas de acesso condicional porque estas contas não será capazes de aceder ao painel do Azure Information Protection no portal do Azure.

- Se utilizar a MFA no seu políticas de acesso condicional para colaborar com outras organizações (B2B), tem de utilizar [colaboração B2B do Azure AD](/azure/active-directory/b2b/what-is-b2b) e crie contas de convidado para os utilizadores que pretende partilhar com a da outra organização.

- Com o Azure AD de Dezembro de 2018 versão de pré-visualização, pode agora pedir aos utilizadores que aceitem os termos de utilização antes de abrir um documento protegido pela primeira vez. Para obter mais informações, consulte o seguinte anúncio de mensagem de blogue: [Atualizações à funcionalidade de AD termos de utilização do Azure dentro de acesso condicional](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Updates-to-Azure-AD-Terms-of-Use-functionality-within/ba-p/294822)

- Se usar muitas aplicações de cloud para o acesso condicional, não poderá ver **Microsoft Azure Information Protection** apresentados na lista para selecionar. Neste caso, utilize a caixa de pesquisa na parte superior da lista. Comece a escrever "Microsoft Azure Information Protection" para filtrar as aplicações disponíveis. Desde que tiver uma subscrição de suporte, em seguida, irá ver **Microsoft Azure Information Protection** para selecionar. 

## <a name="i-see-azure-information-protection-is-listed-as-a-security-provider-for-microsoft-graph-securityhow-does-this-work-and-what-alerts-will-i-receive"></a>Posso ver o Azure Information Protection está listado como um fornecedor de segurança para o Microsoft Graph Security — como este funciona e que alertas recebo?

Sim, como uma oferta de pré-visualização pública, podem agora receber um alerta para **acesso a dados anómalas do Azure Information Protection**. Este alerta é acionado quando existem invulgares tentativas de acesso a dados protegidos pelo Azure Information Protection. Por exemplo, aceder a um volume anormalmente elevado de dados, numa hora invulgar do dia ou aceder a partir de uma localização desconhecida.

Esses alertas podem ajudar a detetar ataques relacionados com dados avançados e ameaças internas no seu ambiente. Estes alertas utilizam o machine learning para criar um perfil do comportamento dos utilizadores que acedem aos seus dados protegidos. 

Os alertas do Azure Information Protection podem ser acedidos por [com a API de segurança do Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/security-api-overview), ou pode [transmitir alertas](https://developer.microsoft.com/graph/docs/concepts/security_siemintegration) para soluções SIEM, como Splunk e o IBM Qradar, com o Azure Monitor.

Para obter mais informações sobre a API de segurança do Microsoft Graph, consulte [descrição geral da API de segurança do Microsoft Graph](https://developer.microsoft.com/graph/docs/concepts/security-concept-overview).

## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>O que é a diferença entre a FCI do Windows Server e o scanner do Azure Information Protection?

Infraestrutura de classificação de ficheiros do Windows Server tem sido historicamente uma opção para classificar documentos e, em seguida, protegê-los utilizando o [conector Rights Management](deploy-rms-connector.md) (Office documenta apenas) ou um [PowerShell script](./rms-client/configure-fci.md) (todos os tipos de ficheiros). 

Agora, recomendamos que utilize o [scanner do Azure Information Protection](deploy-aip-scanner.md). O scanner utiliza o cliente do Azure Information Protection e a sua política do Azure Information Protection para documentos de etiqueta (todos os tipos de ficheiro), para que esses documentos são, em seguida, classificados e, opcionalmente, protegidos.

As principais diferenças entre essas duas soluções:

|Windows Server FCI|Scanner do Azure Information Protection|
|--------------------------------|-------------------------------------|
|Arquivos de dados suportados: <br /><br />-Pastas locais no Windows Server|Arquivos de dados suportados: <br /><br />-Pastas locais no Windows Server<br /><br />-Windows ficheiro partilhas e armazenamento ligado à rede<br /><br />-O SharePoint Server 2016 e o SharePoint Server 2013. SharePoint Server 2010 também é suportada para os clientes que tenham [suporte para esta versão do SharePoint estendido](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).|
|Modo operacional: <br /><br />-Em Tempo Real|Modo operacional: <br /><br />-Sistematicamente rastreia os arquivos de dados e esse ciclo pode executar uma vez ou repetidamente|
|Suporte para tipos de ficheiro: <br /><br />-Todos os tipos de ficheiros estão protegidos por predefinição <br /><br />-Tipos de ficheiro específicos podem ser excluídos da proteção ao editar o registo|Suporte para tipos de ficheiro: <br /><br />-Tipos de ficheiro office e documentos PDF protegidos por padrão <br /><br />-Tipos de ficheiro adicionais podem ser incluídos para proteção ao editar o registo|

Atualmente, existe uma diferença na definição do [proprietário do Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) para ficheiros que estão protegidos num compartilhamento de rede ou pasta local. Por predefinição, para ambas as soluções, o proprietário do Rights Management é definido para a conta que protege o ficheiro, mas pode substituir esta definição:

- Para o Windows Server FCI: Pode definir o proprietário do Rights Management para ser uma única conta para todos os ficheiros ou definir dinamicamente o proprietário do Rights Management para cada ficheiro. Para definir dinamicamente o proprietário do Rights Management, utilize o **- OwnerMail [Source File Owner Email]** parâmetro e valor. Esta configuração obtém o endereço de e-mail do utilizador do Active Directory utilizando o nome da conta de utilizador na propriedade proprietário do ficheiro.

- Para o scanner do Azure Information Protection: Para ficheiros protegidos recentemente, pode definir o proprietário do Rights Management para ser uma única conta para todos os ficheiros num arquivo de dados especificada, mas não é possível definir dinamicamente o proprietário do Rights Management para cada ficheiro. O proprietário do Rights Management não é alterado para ficheiros protegidos anteriormente. Para definir a conta para ficheiros protegidos recentemente, especifique a **-predefinição proprietário** definição no perfil de scanner. 

Quando a deteção de impressão pode proteger ficheiros em sites do SharePoint e bibliotecas, o proprietário do Rights Management é definido dinamicamente para cada ficheiro ao utilizar o valor de Editor do SharePoint.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Já ouvi falar que uma nova versão irá estar disponível em breve para o Azure Information Protection. Quando será lançada?

A documentação técnica não contém informações sobre os lançamentos futuros. Para este tipo de informações e anúncios de lançamento, verifique os [blogue Enterprise Mobility + Security](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity?product=azure-information-protection,azure-rights-management-services).

Se uma versão do Office que está interessado em, certifique-se de que também consulta os [blogue do Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/bg-p/Office365Blog) e [blogue de aplicações do Office](https://techcommunity.microsoft.com/t5/Office-Apps-Blog/bg-p/OfficeAppsBlog).

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Azure Information Protection é adequado para o meu país?

Países diferentes têm requisitos diferentes e regulamentos. Para ajudar a responder a essa pergunta para a sua organização, consulte [adequação para diferentes países](./compliance.md#suitability-for-different-countries).

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>Como o Azure Information Protection pode ajudar com o GDPR?

Para ver como o Azure Information Protection o pode ajudar-o a cumprir o Regulamento de proteção de dados (GDPR) em geral, consulte o seguinte anúncio de mensagem do blogue, com vídeo: [Microsoft 365 fornece uma estratégia de proteção de informações para ajudar com o GDPR](https://blogs.office.com/2018/02/22/microsoft-365-provides-an-information-protection-strategy-to-help-with-the-gdpr).

## <a name="where-can-i-find-supporting-information-for-azureinformation-protectionsuch-as-legal-compliance-and-slas"></a>Onde posso encontrar informações de suporte do Azure Information Protection – como legais, conformidade e SLAs?
Veja [Informações de suporte e conformidade do Azure Information Protection](./compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Como posso comunicar um problema ou enviar feedback do Azure Information Protection?

Em alternativa, utilize os canais de suporte padrão ou [contacte o Suporte da Microsoft](information-support.md#to-contact-microsoft-support).

É também convidado a interagir com a nossa equipa de engenharia, no [site Yammer do Azure Information Protection](https://www.yammer.com/askipteam/). 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>O que posso fazer se a minha pergunta não constar aqui?

Em primeiro lugar, reveja as seguintes perguntas mais frequentes sobre que são específicas para classificação e etiquetagem ou específicas para proteção de dados. O serviço Azure Rights Management (Azure RMS) fornece a tecnologia de proteção de dados do Azure Information Protection. O Azure RMS pode ser utilizado com classificação e etiquetagem ou por si só. 

- [FAQs sobre a classificação e etiquetagem](faqs-infoprotect.md)

- [FAQs sobre a proteção de dados](faqs-rms.md)

Se não encontrar respostas às suas perguntas, utilize as ligações e os recursos indicados em [Informações e suporte do Azure Information Protection](information-support.md).

Além disso, existem FAQ criadas para os utilizadores finais:

- [FAQ sobre a aplicação Azure Information Protection para iOS e Android](./rms-client/mobile-app-faq.md)

- [FAQ da aplicação para computadores Mac de partilha RMS](https://technet.microsoft.com/dn451248)

