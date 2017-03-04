---
title: "FAQs do Azure RMS – AIP"
description: "Algumas perguntas mais frequentes sobre o serviço de proteção de dados, o Azure Rights Management (Azure RMS), do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/22/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: f2413580bf76f0b9b6fa52d8be381c44f9c985fe
ms.lasthandoff: 02/24/2017


---

# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Perguntas mais frequentes sobre a proteção de dados no Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Tem uma pergunta sobre o serviço de proteção de dados, o Azure Rights Management, do Azure Information Protection? Verifique se a resposta está aqui. 

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Os ficheiros têm de estar na cloud para serem protegidos pelo Azure Rights Management?
Não, este é um equívoco comum. O serviço Azure Rights Management (e a Microsoft) não vê nem armazena os seus dados como parte do processo de proteção das informações. As informações que protege nunca são enviadas para ou armazenadas no Azure, a menos que as armazene explicitamente no Azure ou utilize outro serviço cloud que as armazene no Azure. 

Para obter mais informações, consulte [How does Azure RMS work? Under the hood (Como funciona o Azure RMS? Nos bastidores)](../understand-explore/how-does-it-work.md) para compreender como uma fórmula de cola secreta criada e armazenada no local é protegida pelo serviço Azure Rights Management, mas permanece no local.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Qual é a diferença entre a encriptação do Azure Rights Management e a encriptação noutros serviços cloud da Microsoft?

A Microsoft fornece múltiplas tecnologias de encriptação que lhe permitem proteger os seus dados para cenários diferentes e muitas vezes complementares. Por exemplo, enquanto o Office 365 oferece encriptação para dados inativos armazenados no Office 365, o serviço Azure Rights Management do Azure Information Protection encripta os seus dados independentemente para que estes estejam protegidos, qualquer que seja o local ou a forma de transmissão.

Estas tecnologias de encriptação são complementares e para as utilizar tem de as ativar e configurar independentemente. Quando o fizer, poderá ter a opção de utilizar a sua própria chave para a encriptação, um cenário também conhecido como "BYOK". Ativar o BYOK para uma destas tecnologias não afeta as outras tecnologias existentes. Por exemplo, pode utilizar o BYOK para o Azure Information Protection e não o utilizar para outras tecnologias de encriptação e vice-versa. As chaves utilizadas por estas diferentes tecnologias podem ser as mesmas ou diferentes, dependendo da forma como configurou as opções de encriptação para cada serviço.

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>Qual é a diferença entre BYOK e HYOK e quando devo utilizá-los?

**Bring Your Own Key – Traga a Sua Própria Chave** (BYOK), no contexto do Azure Information Protection, é quando cria a sua própria chave no local para a proteção do Azure Rights Management. Em seguida, transfere essa chave para um módulo de segurança de hardware (HSM) no Azure Key Vault, onde continua a ser o proprietário e a gerir a sua chave. Se não o fizer, a proteção do Azure Rights Management utilizará uma chave criada e gerida automaticamente no Azure. Esta configuração predefinida é referida como "gerida pela Microsoft" em vez de "gerida pelo cliente" (opção BYOK).

Para obter mais informações sobre o BYOK e se deve escolher esta topologia de chaves para a sua organização, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md). 

**Hold Your Own Key – Tenha a Sua Própria Chave** (HYOK), no contexto do Azure Information Protection, destina-se a um pequeno número de organizações com um subconjunto de documentos ou e-mails que não podem ser protegidos por uma chave armazenada na cloud. Para estas organizações, esta restrição aplica-se mesmo que tenham criado e gerido a chave através de BYOK. A restrição pode dever-se muitas vezes a motivos de regulamentação e conformidade e a configuração HYOK só deve ser aplicada a informações "Confidenciais", que nunca serão partilhadas fora da organização, que serão consumidas apenas na rede interna e que não precisam de ser acedidas a partir de dispositivos móveis. 

Para estas exceções (normalmente, menos de 10% de todos os conteúdos que têm de ser protegidos), as organizações podem utilizar uma solução no local, os Serviços de Gestão de Direitos do Active Directory, para criar a chave que permanece no local. Com esta solução, os computadores obtêm a política do Azure Information Protection a partir da cloud, mas estes conteúdos identificados podem ser protegidos com a chave no local.

Para obter mais informações sobre o HYOK, certificar-se de que compreende as suas limitações e restrições e obter orientações para quando o utilizar, veja [Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS](../deploy-use/configure-adrms-restrictions.md).


## <a name="can-i-integrate-the-azure-rights-management-service-with-my-on-premises-servers"></a>Posso integrar o serviço Azure Rights Management nos meus servidores no local?
Sim. O Azure Rights Management pode ser integrado nos seus servidores no local, como o Exchange Server, o SharePoint e os servidores de ficheiros do Windows. Para tal, utilize o [conetor Rights Management](../deploy-use/deploy-rms-connector.md). Em alternativa, se estiver interessado em apenas utilizar a Infraestrutura de Classificação de Ficheiros (FCI) com o Windows Server, pode utilizar os [Cmdlets da Proteção RMS](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). Também pode sincronizar e federar os seus controladores de domínio do Active Directory com o Azure AD para uma experiência de autenticação mais integrada para os utilizadores, por exemplo, ao utilizar o [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

O Azure Rights Management gera e faz a gestão dos certificados XrML automaticamente conforme necessário, pelo que não utiliza um PKI no local. Para obter mais informações sobre como o Azure Rights Management utiliza certificados, consulte a secção [Explicação passo a passo sobre como funciona o Azure RMS: primeira utilização, proteção de conteúdos, consumo de conteúdos](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) no artigo [Como funciona o Azure RMS?](../understand-explore/how-does-it-work.md).

## <a name="where-can-i-find-information-about-3rd-party-solutions-that-integrate-with-azure-rms"></a>Onde posso encontrar informações sobre soluções de terceiros que se integram com o Azure RMS?

Muitos fornecedores de software já têm soluções ou estão a implementar soluções que se integram no Azure Rights Management, e a lista está a crescer muito rapidamente. Poderá considerar útil ler o [Blogue Enterprise Mobility and Security (em inglês)](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) e obter as atualizações mais recentes através de [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy) no Twitter. No entanto, se tiver uma pergunta específica, envie uma mensagem de e-mail à equipa do Information Protection: askipteam@microsoft.com.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Existe um pacote de gestão ou o mecanismo de monitorização semelhante para o conector RMS?

Embora o conector do Rights Management registe mensagens de erro, aviso e informações no registo de eventos, não existe um pacote de gestão que inclua a monitorização destes eventos. No entanto, a lista de eventos e as suas descrições, com mais informações para ajudá-lo a aplicar as medidas corretivas está documentada em [Monitorizar o conector do Azure Rights Management](../deploy-use/monitor-rms-connector.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Tenho de ser um administrador global para configurar o Azure RMS ou posso delegar noutros administradores?

Os administradores globais de um inquilino do Office 365 ou inquilino do Azure AD podem obviamente executar todas as tarefas administrativas do serviço Azure Rights Management. No entanto, se quiser atribuir permissões administrativas a outros utilizadores, pode fazê-lo utilizando o cmdlet do PowerShell do Azure RMS, [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/dn629417.aspx). Pode atribuir esta função administrativa por conta de utilizador ou por grupo. Existem duas funções disponíveis: **Administrador Global** e **Administrador do Conector**. 

Como estes nomes de função sugerem, a primeira função atribui permissões para executar todas as tarefas administrativas do Azure Rights Management (sem torná-los administrador global para outros serviços cloud) e a segunda função concede permissões para executar apenas o conector do Rights Management (RMS).

Factos a ter em conta:

- Apenas os administradores globais do Office 365 e os administradores globais do Azure AD podem utilizar os portais de gestão (centro de administração do Office 365 ou portal clássico do Azure) para configurarem o Azure RMS. Os utilizadores aos quais atribui a função de administrador global para o Azure RMS têm de utilizar os comandos do PowerShell do Azure RMS para configurarem o Azure RMS. Para ajudar a encontrar os cmdlets certos para tarefas específicas, consulte [Administrar o Azure Rights Management Utilizando o Windows PowerShell](../deploy-use/administer-powershell.md).

- Se tiver configurado [controlos de inclusão](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), isto não afeta a capacidade para administrar o Azure RMS, com exceção do conector RMS. Por exemplo, se tiver configurado controlos de inclusão de para restringir a capacidade de proteger conteúdo ao grupo "Departamento de TI", a conta utilizada para instalar e configurar o conector do RMS tem de ser um membro desse grupo. 

- Nenhum administrador do Azure RMS (o administrador global do inquilino ou um administrador global do Azure RMS) pode remover automaticamente a proteção de documentos ou e-mails protegidos pelo Azure RMS. Apenas os utilizadores aos quais estão atribuídos superutilizadores para o Azure RMS podem fazê-lo, desde que a funcionalidade de superutilizador esteja ativada. No entanto, o administrador global do inquilino e qualquer administrador global do Azure RMS pode atribuir utilizadores como superutilizadores, incluindo a sua própria conta. Também pode ativar a funcionalidade de superutilizador. Estas ações são registadas no registo de administrador do Azure RMS. Para obter mais informações, consulte a secção de melhores práticas em [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md). 


## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Tenho uma implementação híbrida do Exchange com alguns utilizadores no Exchange Online e outros no Exchange Server. Isto é suportado pelo Azure RMS?
Absolutamente. Além disso, a vantagem é que os utilizadores poderão proteger e consumir de forma totalmente integrada e-mails e anexos protegidos nas duas implementações do Exchange. Para esta configuração, [ative o Azure RMS](../deploy-use/activate-service.md) e [ative a IRM para o Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx) e, em seguida, [implemente e configure o conetor RMS](../deploy-use/deploy-rms-connector.md) para o Exchange Server.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>Se utilizar esta proteção para o meu ambiente de produção, a minha empresa fica presa a essa solução ou arrisca-se a perder o acesso aos conteúdos que protegemos com o Azure RMS?
Não, permanece sempre no controlo dos seus dados e pode continuar a aceder aos mesmos, mesmo se optar por deixar de utilizar o serviço Azure Rights Management. Para obter mais informações, consulte [Desativar o Azure Rights Management](../deploy-use/decommission-deactivate.md).

No entanto, antes de desativar a implementação do Azure RMS, gostaríamos de ouvir o seu feedback e compreender por que motivo tomou esta decisão. Se a proteção do Azure Rights Management não satisfizer os seus requisitos empresariais, contacte-nos no caso de estarmos a planear novas funcionalidades para um futuro próximo ou no caso de existirem alternativas. Envie uma mensagem de e-mail para [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) e teremos todo o gosto em falar sobre os seus requisitos técnicos e empresariais.

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Posso controlar que utilizadores podem aceder ao Azure RMS para proteger o conteúdo?
Sim, o serviço Azure Rights Management tem controlos de integração do utilizador para este cenário. Para obter mais informações, consulte a secção [Configuring onboarding controls for a phased deployment (Configurar os controlos de inclusão para uma implementação faseada – em inglês)](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) no artigo [Activating Azure Rights Management (Ativar o Azure Rights Management – em inglês)](../deploy-use/activate-service.md).

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Posso impedir que os utilizadores partilhem documentos protegidos com organizações específicas?
Uma das grandes vantagens da utilização do serviço Azure Rights Management na proteção de dados é que suporta a colaboração entre empresas sem ter de configurar confianças explícitas para cada organização parceira, porque o Azure AD processa a autenticação automaticamente.

Não existe uma opção de administração para impedir que os utilizadores partilhem documentos de forma segura com organizações específicas. Por exemplo, imagine que pretende bloquear uma organização na qual não confia ou que tem uma empresa concorrente. Não faria sentido impedir o serviço Azure Rights Management de enviar documentos protegidos aos utilizadores nessas organizações, porque os seus utilizadores iriam partilhar os seus documentos desprotegidos, que é provavelmente a última coisa que quer que aconteça neste cenário! Por exemplo, não poderia identificar quem está a partilhar documentos confidenciais da empresa com os utilizadores nessas organizações, o que pode fazer quando o documento (ou e-mail) é protegido pelo serviço Azure Rights Management.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>Quando partilho um documento protegido com alguém fora da minha empresa, como é que esse utilizador é autenticado?
O serviço Azure Rights Management utiliza sempre uma conta do Azure Active Directory e um endereço de e-mail associado para a autenticação do utilizador, o que torna a colaboração entre empresas totalmente integrada para os administradores. Se a outra organização utilizar serviços do Azure, os utilizadores já terão contas no Azure Active Directory, mesmo que estas contas tenham sido criadas e geridas no local e, em seguida, sincronizadas com o Azure. Se a organização tiver o Office 365, nos bastidores, este serviço também utiliza o Azure Active Directory para as contas de utilizador. Se a organização do utilizador não tiver contas geridas no Azure, os utilizadores podem inscrever-se no [RMS para utilizadores individuais](../understand-explore/rms-for-individuals.md), que cria um diretório e um inquilino do Azure não gerido para a organização com uma conta para o utilizador, para que este utilizador (e utilizadores subsequentes) possa ser autenticado para o serviço Azure Rights Management.

O método de autenticação para estas contas pode variar, dependendo da forma como o administrador na outra organização configurou as contas do Azure Active Directory. Por exemplo, podem utilizar palavras-passe que foram criadas para estas contas, autenticação multifator (MFA), federação ou palavras-passe que foram criadas nos Active Directory Domain Services e, em seguida, sincronizadas com o Azure Active Directory.

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Posso adicionar utilizadores externos (pessoas que não pertencem à minha empresa) a modelos personalizados?
Sim. Criar modelos personalizados que os utilizadores finais (e os administradores) podem selecionar a partir de aplicações torna mais rápido e fácil aplicar a proteção de informações, com políticas predefinidas especificadas por si. Uma das definições no modelo é quem pode aceder aos conteúdos. Pode especificar os utilizadores e os grupos da sua organização e os utilizadores e os grupos externos à sua organização. 

Para especificar os utilizadores a partir de fora da sua organização, adicioná-los como contactos a um grupo que selecionou no portal clássico do Azure quando configurar os seus modelos. Para especificar grupos externos à sua organização, tem de utilizar o [módulo do Windows PowerShell para o Azure Rights Management](../deploy-use/install-powershell.md), que também pode utilizar para especificar utilizadores externos individuais e até todos os utilizadores de outra organização:

-   **Utilize um objeto de definição de direitos para criar ou atualizar um modelo**.    Especifique os endereços de e-mail externos e os seus direitos num objeto de definição de direitos, que utilizará para criar ou atualizar um modelo. Especifique o objeto de definição de direitos com o cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) para criar uma variável e, em seguida, fornecer esta variável ao parâmetro -RightsDefinition com o cmdlet [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) (para um novo modelo) ou o cmdlet [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) (se estiver a modificar um modelo existente). No entanto, se estiver a adicionar estes utilizadores a um modelo existente, terá de definir os objetos de definição de direitos para os grupos existentes nos modelos e não apenas os utilizadores externos.

Para obter mais informações sobre os modelos personalizados, consulte [Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md).

## <a name="does-azure-rms-work-with-dynamic-groups-in-azure-ad"></a>O Azure RMS funciona com grupos dinâmicos no Azure AD?
Uma funcionalidade do Azure AD Premium permite-lhe configurar a associação dinâmica para grupos ao especificar [regras baseadas em atributos](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/). Quando cria um grupo de segurança no Azure AD, este tipo de grupo suporta a associação dinâmica mas não suporta um endereço de e-mail e por isso não pode ser utilizado com o serviço Azure Rights Management. No entanto, agora pode criar um novo tipo de grupo no Azure AD que suporte a associação dinâmica e tenha capacidade de correio. Quando adiciona um novo grupo no portal clássico do Azure, pode escolher o **TIPO DE GRUPO** do **Office 365 "Preview"**. Como este grupo tem capacidade de correio, pode utilizá-lo com a proteção do Azure Rights Management.

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Que dispositivos e que tipos de ficheiro são suportados pelo Azure RMS?
Para obter uma lista dos dispositivos que suportam o serviço Azure Rights Management, consulte [Dispositivos cliente que suportam a proteção de dados do Azure Rights Management](../get-started/requirements-client-devices.md). Uma vez que nem todos os dispositivos suportados conseguem atualmente suportar todas as capacidades de Rights Management, certifique-se de que também consulta a tabela em [Aplicações que suportam a proteção de dados do Azure Rights Management](../get-started/requirements-applications.md).

O serviço Azure Rights Management pode suportar todos os tipos de ficheiro. Para texto, imagem, ficheiros do Microsoft Office (Word, Excel, PowerPoint), ficheiros .pdf e outros tipos de ficheiro de aplicação, o Azure Rights Management fornece proteção nativa que inclui encriptação e imposição dos direitos (permissões). Para todas as outras aplicações e tipos de ficheiro, a proteção genérica fornece autenticação e encapsulamento de ficheiro para verificar se um utilizador tem autorização para abrir o ficheiro.

Para obter uma lista de extensões de nome de ficheiro que são suportadas nativamente pelo Azure Rights Management, veja [Ficheiros suportados pelo cliente do Azure Information Protection](../rms-client/client-admin-guide-file-types.md). As extensões de nome de ficheiro que não estiverem indicadas são suportadas através do cliente do Azure Information Protection que aplica automaticamente a proteção genérica a estes ficheiros.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>Quando abro um documento do Office protegido por RMS, o ficheiro temporário associado também fica protegido por RMS?

Não. Neste cenário, o ficheiro temporário associado não contém dados do documento original, mas apenas o que o utilizador introduz enquanto o ficheiro está aberto. Ao contrário do ficheiro original, o ficheiro temporário não foi concebido para partilha e permaneceria no dispositivo, protegido por controlos de segurança locais, como o BitLocker e o EFS.

## <a name="we-really-want-to-use-byok-with-azure-information-protection-but-learned-that-this-isnt-compatible-with-exchange-onlinewhats-your-advice"></a>Queremos utilizar o BYOK com o Azure Information Protection, mas descobrimos que não é compatível com o Exchange Online. O que aconselham?
Não permita que esta limitação atual atrase a utilização do serviço Azure Rights Management do Azure Information Protection. Se tiver o Exchange Online e quiser utilizar o BYOK (Bring Your Own Key – Traga a Sua Própria Chave), recomendamos que implemente agora o Azure Information Protection no modo de gestão de chaves predefinido, em que a Microsoft gera e faz a gestão da sua chave. Dessa forma, obtém todas as vantagens de proteger os seus ficheiros e e-mails importantes, com a opção de mudar para o BYOK mais tarde (por exemplo, quando o Exchange Online suporta o BYOK). Quando mudar para o BYOK, os seus documentos e e-mails anteriormente protegidos continuarão acessíveis através de uma chave arquivada.

No entanto, se as políticas da sua empresa exigirem que utilize um módulo de hardware de segurança (HSM) e isto bloquear a sua implementação do Azure Information Protection, outra opção é implementar o Azure Information Protection com o BYOK agora, com funcionalidade de proteção do Rights Management reduzida para o Exchange. Para obter mais informações, consulte [Preços e restrições do BYOK](../plan-design/byok-price-restrictions.md) em [Planear e implementar a sua chave de inquilino do Azure Rights Management](../plan-design/plan-implement-tenant-key.md).

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>A funcionalidade que procuro não funciona com bibliotecas protegidas do SharePoint. Planeiam oferecer suporte para a minha funcionalidade?
Atualmente, o SharePoint suporta documentos protegidos pelo Rights Management com bibliotecas protegidas da IRM, que não suportam modelos personalizados, controlo de documentos e outras funcionalidades. Para obter mais informações consulte a secção [SharePoint Online e SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) no artigo [Aplicações e serviços do Office ](../understand-explore/office-apps-services-support.md).

Se estiver interessado numa funcionalidade específica que ainda não é suportada, fique atento aos anúncios no [Blogue Enterprise Mobility and Security (em inglês)](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services).

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Como posso configurar o OneDrive para Empresas no SharePoint Online, para que os utilizadores possam partilhar os seus ficheiros de forma segura com pessoas dentro e fora da empresa?
Por predefinição, enquanto administrador do Office 365, não lhe cabe a si configurar isto, mas sim aos utilizadores.

Tal como um administrador do site do SharePoint ativa e configura a IRM para uma biblioteca do SharePoint que possui, o OneDrive para Empresas é concebido para os utilizadores ativarem e configurarem a IRM para as suas próprias bibliotecas do OneDrive para Empresas.  No entanto, com o PowerShell, pode fazê-lo pelos utilizadores. Para obter instruções, consulte a secção [SharePoint Online and OneDrive for Business: IRM Configuration (SharePoint Online e OneDrive para Empresas: configuração de IRM – em inglês)](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) no artigo [Office 365: Configuration for clients and online services (Office 365: configuração para clientes e serviços online – em inglês)](../deploy-use/configure-office365.md).

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Tem sugestões ou truques para uma implementação com êxito?
Após supervisionar várias implementações e ouvir os nossos clientes, parceiros, consultores e engenheiros de suporte – uma das maiores sugestões que podemos transmitir da nossa experiência: **Crie e implemente políticas de direitos simples**.

Como o Azure Information Protection suporta a partilha segura com todas as pessoas, pode ser ambicioso com o alcance da proteção de dados. No entanto, seja conservador com as suas políticas de direitos. Para muitas organizações, o maior impacto comercial provém de impedir a fuga de dados ao aplicar o modelo de política de direitos predefinido que restringe o acesso a pessoas na sua organização. Claro que, se for necessário, pode ser muito mais granular e impedir que as pessoas imprimam, editem, etc. No entanto, as restrições mais granulares devem ser a exceção, para documentos que precisam de um alto nível de segurança. Não implemente estas políticas mais restritas no primeiro dia, mas planeie uma abordagem mais faseada.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Como recuperamos o acesso a ficheiros que foram protegidos por um funcionário que saiu da organização?
Utilize a funcionalidade de superutilizador do Azure RMS, que permite que os utilizadores autorizados tenham direitos de proprietário totais para todas as licenças de utilização que foram concedidas pelo inquilino do RMS da sua organização. Esta mesma funcionalidade permite que os serviços autorizados indexem e inspecionem ficheiros, conforme necessário.

Para obter mais informações, consulte [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md).

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Quando testo a revogação no site de controlo do documento, vejo uma mensagem a indicar que as pessoas ainda podem aceder ao documento durante até 30 dias. Este período de tempo é configurável?

Sim. Esta mensagem reflete a licença de utilização desse ficheiro específico. Uma licença de utilização é um certificado por documento que é concedido a um utilizador que abre um ficheiro ou uma mensagem de e-mail protegido. Este certificado contém direitos desse utilizador para o ficheiro ou a mensagem de e-mail e a chave de encriptação que foi utilizada para encriptar os conteúdos, bem como restrições de acesso adicionais definidas na política do documento. Quando o período de validade da licença de utilização expirar e o utilizador tentar abrir o ficheiro ou a mensagem de e-mail, as respetivas credenciais de utilizador têm de voltar a ser submetidas para o serviço Azure Rights Management. 

Se revogar um ficheiro, essa ação só poderá ser aplicada quando o utilizador autenticar para o serviço Azure Rights Management. Por isso, se um ficheiro tiver um período de validade de licença de utilização de 30 dias e o utilizador já tiver aberto o documento, esse utilizador continuará a ter acesso ao documento enquanto a licença de utilização durar. Quando a licença de utilização expirar, o utilizador terá de ser novamente autenticado. Nessa altura, será rejeitado acesso ao utilizador porque o documento já estará revogado.

O valor predefinido do período de validade da licença de utilização para um inquilino é de 30 dias e pode configurar este valor através do cmdlet do PowerShell [Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx). Esta definição pode ser substituída por uma definição mais restritiva num modelo personalizado. 

Para obter mais informações e exemplos de como a licença funciona, consulte a descrição detalhada de [Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx).

## <a name="can-rights-management-prevent-screen-captures"></a>O Rights Management pode impedir capturas de ecrã?
Ao não conceder direitos de **cópia**[utilização](../deploy-use/configure-usage-rights.md), o Rights Management pode impedir capturas de ecrãs de muitas das ferramentas de captura de ecrã utilizadas normalmente em plataformas com Windows (Windows 7, Windows 8.1, Windows 10, Windows Phone) e Android. No entanto, os dispositivos iOS e Mac não permitem que as aplicações impeçam capturas de ecrã e os browsers (por exemplo, quando são utilizados com o Outlook Web App e o Office Online) também não podem impedir capturas de ecrã.

Impedir capturas de ecrã pode ajudar a evitar a divulgação por acidente ou por negligência de informações confidenciais. No entanto, existem várias formas de um utilizador partilhar os dados apresentados num ecrã e tirar uma captura de ecrã é apenas um dos métodos possíveis. Por exemplo, um utilizador que esteja determinado em partilhar as informações apresentadas pode tirar uma fotografia com a câmara do telemóvel, reescrever os dados ou simplesmente dizê-las a alguém.

Conforme estes exemplos demonstram, mesmo que todas as plataformas e todos os softwares suportassem as APIs do Rights Management para bloquear as capturas de ecrã, a tecnologia por si só nem sempre pode impedir os utilizadores de partilharem dados que não deviam. O Rights Management pode ajudar a salvaguardar os seus dados importantes com políticas de utilização e autorização, mas esta solução de gestão de direitos de empresa deve ser utilizada em conjunto com outros controlos. Por exemplo, implementar segurança física, monitorizar cuidadosamente as pessoas que têm acesso autorizado aos dados da sua organização e investir na educação do utilizadores para que estes compreendam que os dados não devem ser partilhados.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Qual a diferença entre um utilizador que protege um e-mail com Não Reencaminhar e um modelo que não inclui o direito de Reencaminhar?

Apesar do nome e do aspeto, **Não Reencaminhar** não é o oposto do direito de Reencaminhar nem um modelo. Na realidade, é um conjunto de direitos que incluem restringir a cópia, impressão e gravação de anexos, para além de restringir o reencaminhamento de e-mails. Os direitos são aplicados dinamicamente aos utilizadores através de destinatários escolhidos e não estaticamente atribuídos pelo administrador. Para obter mais informações, consulte a secção [Opção Não Reencaminhar para e-mails](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) em [Configurar os direitos de utilização do Azure Rights Management](../deploy-use/configure-usage-rights.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



