---
title: FAQs sobre o Azure Information Protection
description: "Algumas perguntas mais frequentes sobre o Azure Information Protection e o respetivo serviço de proteção de dados, o Azure Rights Management (Azure RMS)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 28b0e73fe8761cac230392479b664c000d9eba79
ms.sourcegitcommit: 85250f5ea80c2ee22197058ff2f65a79503b0f0c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="frequently-asked-questions-for-azure-information-protection"></a>Perguntas mais frequentes sobre o Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Tem uma pergunta sobre o Azure Information Protection ou o serviço Azure Rights Management (Azure RMS)? Verifique se a resposta está aqui.

Estas páginas de FAQ são atualizadas regularmente, com novas adições indicadas nos anúncios de atualização de documentação mensal no [blogue Enterprise Mobility and Security](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services&content-type=updates).

## <a name="whats-the-difference-between-azure-information-protection-and-azure-rights-management"></a>Qual é a diferença entre o Azure Information Protection e o Azure Rights Management?

O Azure Information Protection fornece classificação, etiquetagem e proteção para os documentos e e-mails de uma organização. A tecnologia de proteção utiliza o serviço Azure Rights Management, que agora faz parte do Azure Information Protection.

## <a name="what-is-the-role-of-identity-management-for-azure-information-protection"></a>O que é a função de gestão de identidade do Azure Information Protection?

Um utilizador deve ter um nome de utilizador válido e uma palavra-passe para aceder a conteúdo protegido pelo Azure Information Protection. Para ler mais sobre como o Azure Information Protection o ajuda a proteger os seus dados, veja [A função do Azure Information Protection na proteção de dados](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

## <a name="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included"></a>De que subscrição preciso para o Azure Information Protection e que funcionalidades estão incluídas?
Veja as [informações da subscrição](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) e a [lista de funcionalidades](https://www.microsoft.com/cloud-platform/azure-information-protection-features) no site do Azure Information Protection. 

Se tiver uma subscrição do Office 365 que inclui o Rights Management, transfira a [folha de dados de licenciamento do Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) a partir da página **Funcionalidades**.

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>O cliente do Azure Information Protection destina-se apenas a subscrições que incluem classificação e etiquetagem?

Não. Embora a maioria das apresentações e demonstrações que viu do cliente do Azure Information Protection mostrem como suporta a classificação e a etiquetagem, também podem ser utilizadas com as subscrições que incluem apenas o serviço Azure Rights Management para proteger dados.

Quando o cliente do Azure Information Protection para o Windows estiver instalado e não tiver uma política do Azure Information Protection, o cliente funciona automaticamente no [modo apenas de proteção](../rms-client/client-protection-only-mode.md). Neste modo, os utilizadores podem facilmente aplicar modelos e permissões personalizadas do Rights Management. Se posteriormente comprar uma subscrição que inclui classificação e etiquetagem, o cliente mudará automaticamente para o modo padrão quando transfere a política do Azure Information Protection.

Se utilizar atualmente a aplicação para Windows de partilha Rights Management, recomendamos que substituem esta aplicação com o cliente Azure Information Protection. Suporte para a aplicação de partilha vai terminar 31 de Janeiro de 2019. Para ajudar com a transição, veja [Tarefas que costumava realizar com a aplicação de partilha RMS](../rms-client/upgrade-client-app.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators"></a>Tem de ser um administrador global para configurar o Azure Information Protection ou posso delegar noutros administradores?

Os administradores globais para um inquilino do Office 365 ou inquilino do Azure AD podem obviamente executar todas as tarefas administrativas do Azure Information Protection. No entanto, se pretender atribuir permissões administrativas a outros utilizadores, tem as seguintes opções:

- **Administrador de proteção de informações** (atualmente em pré-visualização): função de administrador este Azure Active Directory permite ao administrador configurar todos os aspetos do Azure Information Protection, mas não a outros serviços. Um administrador com esta função pode ativar e desativar o serviço de proteção do Azure Rights Management, configurar as definições de proteção e as etiquetas e configurar a política do Azure Information Protection. Além disso, um administrador com esta função pode ser executados todos os [cmdlets do PowerShell do módulo AADRM](../deploy-use/administer-powershell.md). 
    
    Para atribuir um utilizador a esta função administrativa, consulte [atribuir um utilizador a funções de administrador no Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal).

- **Administrador de segurança**: função de administrador este Azure Active Directory permite ao administrador configurar todos os aspetos do Azure Information Protection no portal do Azure, para além de configurar alguns aspetos dos outros serviços do Azure. Um administrador com esta função não é possível executar qualquer uma do [cmdlets do PowerShell do módulo AADRM](../deploy-use/administer-powershell.md).
    
    Para atribuir um utilizador a esta função administrativa, consulte [atribuir um utilizador a funções de administrador no Azure Active Directory](/azure/active-directory/active-directory-users-assign-role-azure-portal). Para ver que outras permissões que um utilizador com esta função, consulte o [funções disponíveis](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#available-roles) secção de documentação do Azure Active Directory.

- O Azure Rights Management **Administrador Global** e **administrador do conector**: para estas funções de administrador do Azure Rights Management, o primeiro concede permissões de utilizadores para executar todos [ Cmdlets do PowerShell do módulo AADRM](../deploy-use/administer-powershell.md) sem o tornar um administrador global para outros serviços em nuvem e a segunda função concede permissões para executar apenas o conector do Rights Management (RMS). Nenhuma destas funções administrativas conceder permissões às consolas de gestão.

    Para atribuir qualquer uma destas funções administrativas, utilize o cmdlet AADRM PowerShell, [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator).

Factos a ter em conta:

- Se tiver configurado [controlos de inclusão](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), esta configuração não afeta a capacidade para administrar o Azure Information Protection, exceto o conector RMS. Por exemplo, se tiver configurado controlos de inclusão de para restringir a capacidade de proteger conteúdo ao grupo "Departamento de TI", a conta utilizada para instalar e configurar o conector do RMS tem de ser um membro desse grupo. 

- Os utilizadores que são atribuídos uma função administrativa automaticamente não é possível remover a proteção de documentos ou e-mails que foram protegidos pelo Azure Information Protection. Apenas os utilizadores que estão atribuídos superutilizadores podem fazer isto, e quando a funcionalidade de Superutilizador é ativada. No entanto, qualquer utilizador que atribua permissões administrativas para o Azure Information Protection pode atribuir utilizadores como superutilizadores, incluindo a sua própria conta. Também pode ativar a funcionalidade de superutilizador. Estas ações são registadas no registo de um administrador. Para obter mais informações, veja a secção de melhores práticas em [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md). 


## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>O Azure Information Protection suporta cenários no local e híbridos?

Sim. Embora o Azure Information Protection seja uma solução baseada na cloud, o mesmo consegue classificar, etiquetar e proteger documentos e e-mails armazenados tanto no local como na cloud.

Se tiver servidores de ficheiros do Exchange Server, do SharePoint Server e do Windows, pode implementar o [conector do Rights Management](../deploy-use/deploy-rms-connector.md) para que estes servidores no local possam utilizar o serviço Azure Rights Management para proteger os seus e-mails e documentos. Também pode sincronizar e federar os seus controladores de domínio do Active Directory com o Azure AD para uma experiência de autenticação mais integrada para os utilizadores, por exemplo, ao utilizar o [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

O serviço Azure Rights Management gera e faz a gestão automática de certificados XrML conforme necessário, para não ter de utilizar um PKI no local. Para obter mais informações sobre como o Azure Rights Management utiliza certificados, veja a secção [Explicação passo a passo sobre como funciona o Azure RMS: primeira utilização, proteção de conteúdos, consumo de conteúdos](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) no artigo [Como funciona o Azure RMS?](../understand-explore/how-does-it-work.md).

## <a name="what-types-of-data-can-azure-information-protection-classify-and-protect"></a>Que tipos de dados pode Azure Information Protection classificar e proteger?

O Azure Information Protection pode classificar e proteger mensagens de e-mail e documentos, quer sejam no local ou na nuvem. Estes documentos incluem Word documentos, Excel folhas de cálculo, PowerPoint apresentações, PDF documentos, ficheiros baseados em texto e ficheiros de imagem. Para obter uma lista dos tipos de documentos suportados, consulte a lista de [suportados de tipos de ficheiros](../rms-client/client-admin-guide-file-types.md) no Guia do administrador.

O Azure Information Protection não é possível classificar e proteger os dados estruturados, como ficheiros de base de dados, itens de calendário, relatórios do Power BI, Yammer publicações, Sway conteúdo e blocos de notas OneNote.

## <a name="i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work"></a>Posso ver o Azure Information Protection está indicado como uma aplicação de nuvem disponíveis para o acesso condicional — como funciona este trabalho?

Sim, como uma pré-visualização pública oferta, agora pode configurar o acesso condicional do Azure AD para o Azure Information Protection.

Quando um utilizador abre um documento protegido pelo Azure Information Protection, os administradores agora podem bloquear ou conceder acesso aos utilizadores no seu inquilino, com base nos controlos padrão de acesso condicional. Que exigem que a autenticação multifator (MFA) é uma das condições mais pedidas. Outro um é que dispositivos tem de ser [em conformidade com as políticas do Intune](/intune/conditional-access-intune-common-ways-use) para que, por exemplo, dispositivos móveis cumprem os requisitos de palavra-passe e uma versão mínima do sistema operativo e computadores têm de estar associados a um domínio.

Para obter mais informações e alguns exemplos de instruções, consulte a seguinte mensagem de blogue: [políticas de acesso condicional para o Azure Information Protection](https://cloudblogs.microsoft.com/enterprisemobility/2017/10/17/conditional-access-policies-for-azure-information-protection/).

Informações adicionais:

- Para computadores Windows: para a versão de pré-visualização atual, são avaliadas as políticas de acesso condicional para o Azure Information Protection quando o [ambiente do utilizador é inicializado](../understand-explore/how-does-it-work.md#initializing-the-user-environment) (este processo também é conhecido como bootstrapping), e em seguida, cada 30 dias.

- Pode querer ajustar a frequência obterem avaliadas as políticas de acesso condicional. Pode fazê-lo ao configurar a duração do token. Para obter mais informações, consulte [configuráveis durações token no Azure Active Directory](/azure/active-directory/active-directory-configurable-token-lifetimes).

- Recomendamos que não o adicione contas de administrador para as políticas de acesso condicional porque estas contas não conseguirá aceder ao painel do Azure Information Protection no portal do Azure.

- Se utilizar muitas aplicações em nuvem para o acesso condicional, não poderá ver **Microsoft Azure Information Protection** apresentado na lista de selecção. Neste caso, utilize a caixa de pesquisa na parte superior da lista. Comece a escrever "Microsoft Azure Information Protection" para filtrar as aplicações disponíveis. Desde que tiver uma subscrição suportada, em seguida, verá **Microsoft Azure Information Protection** para selecionar. 

## <a name="whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365"></a>O que é a diferença entre as etiquetas no Azure Information Protection e as etiquetas no Office 365?

As etiquetas no Azure Information Protection permitem-lhe aplicar uma política de classificação e a proteção consistente para documentos e e-mails, quer sejam no local ou na nuvem. Esta classificação e a proteção é independente de onde o conteúdo está armazenado ou como é movido. [Etiquetas no Office 365 segurança & conformidade](https://support.office.com/article/af398293-c69d-465e-a249-d74561552d30) permitem-lhe classificar documentos e e-mails de auditoria e retenção de quando esse conteúdo está em serviços do Office 365. 

Hoje em dia, aplicam-se e gerir estes etiquetas em separado, mas a Microsoft está a trabalhar para uma estratégia de etiquetas abrangente e unificada para vários serviços que incluem o Azure Information Protection, o Office 365, o Microsoft Cloud App Security e o Windows Proteção de informações. Este mesmo esquema de etiquetas e arquivo também estará disponíveis para fornecedores de software. Para obter mais informações, consulte a sessão do Microsoft Ignite 2017, [ciclo de vida de dados completo Protecting utilizando as capacidades de proteção de informações do Microsoft](https://myignite.microsoft.com/videos/55397).

## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>O que é a diferença entre a FCI do Windows Server e a análise do Azure Information Protection?

De tempo, tiver sido capazes de utilizar a infraestrutura de classificação de ficheiros do Windows Server para classificar documentos e, em seguida, protegê-los utilizando o [conector Rights Management](../deploy-use/deploy-rms-connector.md) (Office documentos apenas) ou um [PowerShell script](../rms-client/configure-fci.md) (todos os tipos de ficheiros). 

Agora, pode utilizar o [scanner do Azure Information Protection](../deploy-use/deploy-aip-scanner.md). O scanner utiliza o cliente Azure Information Protection e a política do Azure Information Protection para documentos de etiqueta (todos os tipos de ficheiro) para que estes documentos sejam classificados, em seguida e, opcionalmente, protegidos.

As principais diferenças entre estas duas soluções:

|Windows Server FCI|Análise do Azure Information Protection|
|--------------------------------|-------------------------------------|
|Arquivos de dados suportados: <br /><br />-Pastas locais no Windows Server|Arquivos de dados suportados: <br /><br />-Pastas locais no Windows Server<br /><br />-Windows ficheiro partilhas e armazenamento ligados à rede<br /><br />-SharePoint Server 2016 e o SharePoint Server 2013|
|Modo operacional: <br /><br />-Em Tempo Real|Modo operacional: <br /><br />-Pesquisa sistematicamente arquivos de dados e este ciclo pode executar uma vez ou repetidamente|

Atualmente, não há uma diferença na definição de [proprietário de Rights Management](../deploy-use/configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) para ficheiros que estão protegidos numa partilha de rede ou de pasta local. Por predefinição, para ambas as soluções, o proprietário de Rights Management é definido para a conta que protege o ficheiro, mas pode substituir esta definição:

- Para o Windows Server FCI: Pode definir o proprietário de Rights Management seja uma conta única para todos os ficheiros ou dinamicamente definir o proprietário de Rights Management para cada ficheiro. Para definir dinamicamente o proprietário de Rights Management, utilize o **- OwnerMail [Source File Owner Email]** parâmetro e valor. Esta configuração obtém o endereço de correio eletrónico do utilizador do Active Directory utilizando o nome da conta de utilizador na propriedade proprietário do ficheiro.

- Para a análise do Azure Information Protection: pode definir o proprietário de Rights Management seja uma conta única para todos os ficheiros no arquivo de dados especificado, mas dinamicamente não é possível definir o proprietário de Rights Management para cada ficheiro. Para configurar a conta, especifique o **- DefaultOwner** parâmetro para o [perfil do repositório de dados](/powershell/module/azureinformationprotection/Set-AIPScannerRepository?view=azureipps#optional-parameters).

Quando o verificador protege os ficheiros em sites do SharePoint e bibliotecas, o proprietário de Rights Management dinamicamente definido para cada ficheiro ao utilizar o valor de autor do SharePoint.

## <a name="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released"></a>Já ouvi falar que uma nova versão irá estar disponível em breve para o Azure Information Protection. Quando será lançada?

A documentação técnica não contém informações sobre os lançamentos futuros. Para este tipo de informações e anúncios de lançamento, verifique o [blogue Enterprise Mobility and Security](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services) e obter as atualizações mais recentes do [Microsoft Mobility@MSFTMobility ](https://twitter.com/MSFTMobility) no Twitter. Se estiver interessado numa versão do Office, certifique-se de que vê também o [blogue do Office](https://blogs.office.com/).

## <a name="is-azure-information-protection-suitable-for-my-country"></a>Azure Information Protection é adequado para a minha país?

Países/regiões diferentes têm requisitos diferentes e regulamentos. Para ajudar a responder a esta questão para a sua organização, consulte [adequabilidade diferentes países](../understand-explore/compliance.md#suitability-for-different-countries).

## <a name="how-can-azure-information-protection-help-with-gdpr"></a>Como o Azure Information Protection pode ajudar com GDPR?

Para ver como o Azure Information Protection o podem ajudar a satisfazer as regulamento de proteção de dados (GDPR) em geral, veja o anúncio de mensagem de blogue seguinte, com as vídeo: [Microsoft 365 fornece uma estratégia de proteção de informações para ajudar a GDPR](https://blogs.office.com/2018/02/22/microsoft-365-provides-an-information-protection-strategy-to-help-with-the-gdpr).

## <a name="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas"></a>Onde posso encontrar informações de suporte para o Azure Information Protection, como informações legais, sobre conformidade e SLAs?
Veja [Informações de suporte e conformidade do Azure Information Protection](../understand-explore/compliance.md).

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Como posso comunicar um problema ou enviar feedback do Azure Information Protection?

Em alternativa, utilize os canais de suporte padrão ou [contacte o Suporte da Microsoft](information-support.md#to-contact-microsoft-support).

Para enviar feedback, como sugestões de melhorias ou novas funcionalidades: na aplicação do Office, no separador **Base** no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e Feedback**. Na caixa de diálogo **Microsoft Azure Information Protection**, clique em **Envie-nos Os Seus Comentários**. Esta opção abre uma mensagem de e-mail para serem enviadas a equipa do Information Protection.

É também convidado a interagir com a nossa equipa de engenharia, no [site Yammer do Azure Information Protection](https://www.yammer.com/askipteam/). 

## <a name="what-do-i-do-if-my-question-isnt-here"></a>O que posso fazer se a minha pergunta não constar aqui?

Em primeiro lugar, reveja as seguintes perguntas mais frequentes sobre que são específicas para classificação e etiquetagem ou específicas para proteção de dados. O serviço Azure Rights Management (Azure RMS) fornece a tecnologia de proteção de dados do Azure Information Protection. O Azure RMS pode ser utilizado com a classificação e etiquetagem ou por si só. 

- [FAQs sobre a classificação e etiquetagem](faqs-infoprotect.md)

- [FAQs sobre a proteção de dados](faqs-rms.md)

Se não encontrar respostas às suas perguntas, utilize as ligações e os recursos indicados em [Informações e suporte do Azure Information Protection](information-support.md).

Além disso, existem FAQs criadas para os utilizadores finais:

- [FAQ sobre a aplicação Azure Information Protection para iOS e Android](../rms-client/mobile-app-faq.md)

- [FAQ sobre a aplicação de partilha RMS para computadores Mac e Windows Phone](https://technet.microsoft.com/dn451248)

- [FAQ sobre a Aplicação de Partilha Rights Management para Windows](https://technet.microsoft.com/dn467883)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]

