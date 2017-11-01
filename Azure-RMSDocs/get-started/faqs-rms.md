---
title: "FAQs do Azure RMS – AIP"
description: "Algumas perguntas mais frequentes sobre o serviço de proteção de dados, o Azure Rights Management (Azure RMS), do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 190ad05c5f505f2c0247c04bf271c8c12cac2ea9
ms.sourcegitcommit: 832d3ef5f9c41d6adb18a8cf5304f6048cc7252e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/24/2017
---
# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Perguntas mais frequentes sobre a proteção de dados no Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Tem uma pergunta sobre o serviço de proteção de dados, o Azure Rights Management, do Azure Information Protection? Verifique se a resposta está aqui. 

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Os ficheiros têm de estar na cloud para serem protegidos pelo Azure Rights Management?
Não, este é um equívoco comum. O serviço Azure Rights Management (e a Microsoft) não vê nem armazena os seus dados como parte do processo de proteção das informações. As informações que protege nunca são enviadas para ou armazenadas no Azure, a menos que as armazene explicitamente no Azure ou utilize outro serviço cloud que as armazene no Azure. 

Para obter mais informações, veja [Como funciona o Azure RMS Under the hood (Como funciona o Azure RMS? Nos bastidores)](../understand-explore/how-does-it-work.md) para compreender como uma fórmula de cola secreta criada e armazenada no local é protegida pelo serviço Azure Rights Management, mas permanece no local.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Qual é a diferença entre a encriptação do Azure Rights Management e a encriptação noutros serviços cloud da Microsoft?

A Microsoft fornece múltiplas tecnologias de encriptação que lhe permitem proteger os seus dados para cenários diferentes e muitas vezes complementares. Por exemplo, enquanto o Office 365 oferece encriptação para dados inativos armazenados no Office 365, o serviço Azure Rights Management do Azure Information Protection encripta os seus dados independentemente para que estes estejam protegidos, qualquer que seja o local ou a forma de transmissão.

Estas tecnologias de encriptação são complementares e para as utilizar tem de as ativar e configurar independentemente. Quando o fizer, poderá ter a opção de utilizar a sua própria chave para a encriptação, um cenário também conhecido como "BYOK". Ativar o BYOK para uma destas tecnologias não afeta as outras tecnologias existentes. Por exemplo, pode utilizar o BYOK para o Azure Information Protection e não o utilizar para outras tecnologias de encriptação e vice-versa. As chaves utilizadas por estas diferentes tecnologias podem ser as mesmas ou diferentes, dependendo da forma como configurou as opções de encriptação para cada serviço.

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>Qual é a diferença entre BYOK e HYOK e quando devo utilizá-los?

**Bring Your Own Key – Traga a Sua Própria Chave** (BYOK), no contexto do Azure Information Protection, é quando cria a sua própria chave no local para a proteção do Azure Rights Management. Em seguida, transfere essa chave para um módulo de segurança de hardware (HSM) no Azure Key Vault, onde continua a ser o proprietário e a gerir a sua chave. Se não o fizer, a proteção do Azure Rights Management utilizará uma chave criada e gerida automaticamente no Azure. Esta configuração predefinida é referida como "gerida pela Microsoft" em vez de "gerida pelo cliente" (opção BYOK).

Para obter mais informações sobre o BYOK e se deve escolher esta topologia de chaves para a sua organização, veja [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md). 

**Hold your own key – tenha a sua própria chave** (HYOK), no contexto do Azure Information Protection, destina-se a poucas organizações com um subconjunto de documentos ou e-mails que não podem ser protegidos por uma chave armazenada na cloud. Para estas organizações, esta restrição aplica-se mesmo que tenham criado e gerido a chave através de BYOK. A restrição pode dever-se muitas vezes a motivos de regulamentação e conformidade e a configuração HYOK só deve ser aplicada a informações "Confidenciais", que nunca serão partilhadas fora da organização, que serão consumidas apenas na rede interna e que não precisam de ser acedidas a partir de dispositivos móveis. 

Para estas exceções (normalmente, menos de 10% de todos os conteúdos que têm de ser protegidos), as organizações podem utilizar uma solução no local, os Serviços de Gestão de Direitos do Active Directory, para criar a chave que permanece no local. Com esta solução, os computadores obtêm a política do Azure Information Protection a partir da cloud, mas estes conteúdos identificados podem ser protegidos com a chave no local.

Para obter mais informações sobre o HYOK, certificar-se de que compreende as suas limitações e restrições e obter orientações para quando o utilizar, veja [Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS](../deploy-use/configure-adrms-restrictions.md).

## <a name="can-i-now-use-byok-with-exchange-online"></a>Posso agora utilizar o BYOK com o Exchange Online?

Sim, pode agora utilizar o BYOK com o Exchange Online quando siga as instruções em [configurar novas capacidades de encriptação de mensagens do Office 365 desenvolvidas Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Estas instruções ativar as novas funcionalidades no Exchange Online, que suportam a utilizar uma BYOK para o Azure Information Protection, bem como a nova encriptação de mensagens do Office 365.

Para obter mais informações sobre esta alteração, consulte o anúncio de blogue: [encriptação de mensagens do Office 365 com as novas funcionalidades](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)

## <a name="where-can-i-find-information-about-third-party-solutions-that-integrate-with-azure-rms"></a>Onde posso encontrar informações sobre soluções de terceiros que se integram com o Azure RMS?

Muitos fornecedores de software já têm soluções ou estão a implementar soluções que se integram no Azure Rights Management e a lista está a crescer rapidamente. Poderá achar útil para verificar o [soluções de RMS englightened](requirements-applications.md#rms-enlightened-solutions) lista e obter as atualizações mais recentes do [Microsoft Mobility@MSFTMobility ](https://twitter.com/MSFTMobility) no Twitter. No entanto, se tiver uma pergunta específica, envie uma mensagem de e-mail à equipa do Information Protection: askipteam@microsoft.com.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Existe um pacote de gestão ou o mecanismo de monitorização semelhante para o conector RMS?

Embora o conector do Rights Management registe mensagens de erro, aviso e informações no registo de eventos, não existe um pacote de gestão que inclua a monitorização destes eventos. No entanto, a lista de eventos e as suas descrições, com mais informações para ajudá-lo a aplicar as medidas corretivas está documentada em [Monitorizar o conector do Azure Rights Management](../deploy-use/monitor-rms-connector.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Tenho de ser um administrador global para configurar o Azure RMS ou posso delegar noutros administradores?

Os administradores globais de um inquilino do Office 365 ou inquilino do Azure AD podem obviamente executar todas as tarefas administrativas do serviço Azure Rights Management. No entanto, se quiser atribuir permissões administrativas a outros utilizadores, pode fazê-lo utilizando o cmdlet do PowerShell do Azure RMS, [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator). Pode atribuir esta função administrativa por conta de utilizador ou por grupo. Existem duas funções disponíveis: **Administrador Global** e **Administrador do Conector**. 

Como estes nomes de função sugerem, a primeira função atribui permissões para executar todas as tarefas administrativas do Azure Rights Management (sem torná-los administrador global para outros serviços cloud) e a segunda função concede permissões para executar apenas o conector do Rights Management (RMS).

Factos a ter em conta:

- Apenas os administradores globais para o Office 365 e os administradores globais para o Azure AD podem utilizar o Centro de administração do Office 365 ou portal clássico do Azure para configurar o Azure RMS. Se utilizar o portal do Azure para o Azure Information Protection, também pode iniciar sessão como um administrador de segurança.

- Os utilizadores aos quais atribui a função de administrador global para o Azure RMS têm de utilizar os comandos do PowerShell do Azure RMS para configurarem o Azure RMS. Para ajudar a encontrar os cmdlets certos para tarefas específicas, veja [Administrar o Azure Rights Management Utilizando o Windows PowerShell](../deploy-use/administer-powershell.md).

- Se tiver configurado [controlos de inclusão](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), esta configuração não afeta a capacidade para administrar o Azure RMS, exceto o conector RMS. Por exemplo, se tiver configurado controlos de inclusão de para restringir a capacidade de proteger conteúdo ao grupo "Departamento de TI", a conta utilizada para instalar e configurar o conector do RMS tem de ser um membro desse grupo. 

- Nenhum administrador para o Azure RMS (por exemplo, administrador global do inquilino ou um administrador global do Azure RMS) pode remover automaticamente a proteção de documentos ou e-mails que foram protegidos pelo Azure RMS. Apenas os utilizadores aos quais estão atribuídos superutilizadores para o Azure RMS podem fazê-lo, desde que a funcionalidade de superutilizador esteja ativada. No entanto, o administrador global do inquilino e qualquer administrador global do Azure RMS pode atribuir utilizadores como superutilizadores, incluindo a sua própria conta. Também pode ativar a funcionalidade de superutilizador. Estas ações são registadas no registo de administrador do Azure RMS. Para obter mais informações, veja a secção de melhores práticas em [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md). 

>[!NOTE]
> Modelos e as novas opções de configuração da proteção do Azure Rights Management movido para o portal do Azure, que suporta a administradores de segurança para além de acesso de administrador global. 

## <a name="how-do-i-create-a-new-custom-template-in-the-azure-portal"></a>Como posso criar um novo modelo personalizado no portal do Azure?

Modelos personalizados movido para o portal do Azure onde pode continuar a geri-los como modelos ou convertê-las em etiquetas. Para criar um novo modelo, crie uma nova etiqueta e configure as configurações de proteção de dados do Azure RMS. Nos bastidores, esta ação cria um novo modelo que pode ser acedido por serviços e aplicações que se integram nos modelos do Rights Management.

Para obter mais informações sobre os modelos no portal do Azure, consulte [configurar e gerir modelos do Azure Information Protection](../deploy-use/configure-policy-templates.md).

## <a name="ive-protected-a-document-and-now-want-to-change-the-usage-rights-or-add-usersdo-i-need-to-reprotect-the-document"></a>Posso tiver protegido um documento e agora pretende alterar os direitos de utilização ou adicionar utilizadores – é necessário voltar a proteger o documento?

Se o ficheiro foi protegido utilizando um modelo ou de etiqueta, não é necessário para voltar a proteger o documento. Modificar o modelo ou uma etiqueta ao fazer as alterações para os direitos de utilização ou adicionar novos grupos (ou os utilizadores) e, em seguida, guarde e publicar estas alterações:

- Quando um utilizador não aceder ao documento antes de efetuar as alterações, as alterações entram em vigor assim que o utilizador abre o documento. 

- Quando um utilizador acedeu já o documento, estas alterações entram em vigor quando os respetivos [utilizar licença](../deploy-use/configure-usage-rights.md#rights-management-use-license) expira. Proteja o documento apenas se não puder aguardar a licença de utilização para expirar. Trocar de forma eficaz cria uma nova versão do documento e, por conseguinte, uma nova licença de utilização para o utilizador.

Em alternativa, se já tiver configurado um grupo para as permissões necessárias, pode alterar a associação de grupo para incluir ou excluir utilizadores e não é necessário para alterar a etiqueta ou modelo. Pode existir um pequeno atraso antes das alterações surtam efeito, porque é a associação ao grupo [em cache](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management) pelo serviço do Azure Rights Management.

Se o ficheiro foi protegido através da utilização de permissões personalizadas, não é possível alterar as permissões para o documento existente. Tem de proteger o documento novamente e especifique todos os utilizadores e todos os direitos de utilização que são necessários para esta nova versão do documento. Para voltar a proteger um documento protegido, tem de ter o direito de utilização de controlo total. 

## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Tenho uma implementação híbrida do Exchange com alguns utilizadores no Exchange Online e outros no Exchange Server. Isto é suportado pelo Azure RMS?
Absolutamente. Além disso, a vantagem é que os utilizadores poderão proteger e consumir de forma totalmente integrada e-mails e anexos protegidos nas duas implementações do Exchange. Para esta configuração, [ative o Azure RMS](../deploy-use/activate-service.md) e [ative a IRM para o Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx) e, em seguida, [implemente e configure o conetor RMS](../deploy-use/deploy-rms-connector.md) para o Exchange Server.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>Se utilizar esta proteção para o meu ambiente de produção, a minha empresa fica presa a essa solução ou arrisca-se a perder o acesso aos conteúdos que protegemos com o Azure RMS?
Não, permanece sempre no controlo dos seus dados e pode continuar a aceder aos mesmos, mesmo se optar por deixar de utilizar o serviço Azure Rights Management. Para obter mais informações, veja [Desativar o Azure Rights Management](../deploy-use/decommission-deactivate.md).

No entanto, antes de desativar o serviço Azure Rights Management, gostaríamos de ouvir do utilizador e compreender por que motivo tomou esta decisão. Se a proteção do Azure Rights Management não satisfizer os seus requisitos empresariais, contacte-nos no caso de estarmos a planear novas funcionalidades para um futuro próximo ou no caso de existirem alternativas. Envie uma mensagem de e-mail para [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) e teremos todo o gosto em falar sobre os seus requisitos técnicos e empresariais.

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Posso controlar que utilizadores podem aceder ao Azure RMS para proteger o conteúdo?
Sim, o serviço Azure Rights Management tem controlos de integração do utilizador para este cenário. Para obter mais informações, veja a secção [Configurar os controlos de inclusão para uma implementação faseada](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) no artigo [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Posso impedir que os utilizadores partilhem documentos protegidos com organizações específicas?
Uma das grandes vantagens da utilização do serviço Azure Rights Management na proteção de dados é que suporta a colaboração entre empresas sem ter de configurar confianças explícitas para cada organização parceira, porque o Azure AD processa a autenticação automaticamente.

Não existe uma opção de administração para impedir que os utilizadores partilhem documentos de forma segura com organizações específicas. Por exemplo, imagine que pretende bloquear uma organização na qual não confia ou que tem uma empresa concorrente. Não faria sentido impedir o serviço Azure Rights Management de enviar documentos protegidos aos utilizadores nessas organizações, porque os seus utilizadores iriam partilhar os seus documentos desprotegidos, que é provavelmente a última coisa que quer que aconteça neste cenário. Por exemplo, não poderia identificar quem está a partilhar documentos confidenciais da empresa com os utilizadores nessas organizações, o que pode fazer quando o documento (ou e-mail) é protegido pelo serviço Azure Rights Management.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>Quando partilho um documento protegido com alguém fora da minha empresa, como é que esse utilizador é autenticado?

Por predefinição, o serviço Azure Rights Management utiliza uma conta do Azure Active Directory e um endereço de e-mail associado para a autenticação de utilizador, o que torna a colaboração de empresa-empresa totalmente integrada para os administradores. Se a outra organização utilizar serviços do Azure, os utilizadores já terão contas no Azure Active Directory, mesmo que estas contas tenham sido criadas e geridas no local e, em seguida, sincronizadas com o Azure. Se a organização tiver o Office 365, nos bastidores, este serviço também utiliza o Azure Active Directory para as contas de utilizador. Se a organização do utilizador não tiver contas geridas no Azure, os utilizadores podem inscrever-se no [RMS para utilizadores individuais](../understand-explore/rms-for-individuals.md), que cria um diretório e um inquilino do Azure não gerido para a organização com uma conta para o utilizador, para que este utilizador (e utilizadores subsequentes) possa ser autenticado para o serviço Azure Rights Management.

O método de autenticação para estas contas pode variar, dependendo da forma como o administrador na outra organização configurou as contas do Azure Active Directory. Por exemplo, podem utilizar palavras-passe que foram criadas para estas contas, autenticação multifator (MFA), federação ou palavras-passe que foram criadas nos Active Directory Domain Services e, em seguida, sincronizadas com o Azure Active Directory.

Se proteger um e-mail com um anexo de documento do Office para um utilizador não tem uma conta no Azure AD, o método de autenticação é alterado. O serviço Azure Rights Management está Federado com alguns fornecedores de identidade de redes sociais populares, tais como o Gmail. Se o fornecedor de e-mail do utilizador é suportada, o utilizador pode iniciar sessão para que o serviço e os respetivos fornecedor de correio eletrónico é responsável por autenticá-los. Se o fornecedor de e-mail do utilizador não é suportado, ou uma preferência, o utilizador pode candidatar-se um código de acesso único que autentica e apresenta o e-mail com o documento protegido num web browser.

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Posso adicionar utilizadores externos (pessoas que não pertencem à minha empresa) a modelos personalizados?

Sim. Quando converter um modelo para uma etiqueta no portal do Azure, pode configurar o [as definições de proteção](../deploy-use/configure-policy-protection.md) para adicionar permissões a utilizadores e grupos a partir de fora da sua organização e até mesmo todos os utilizadores noutra organização. Em alternativa, pode efetuar esta configuração utilizando o PowerShell.

Para obter mais informações sobre a conversão de modelos personalizados para as etiquetas para que possa, em seguida, facilmente adicionar utilizadores externos, consulte [configurar e gerir modelos do Azure Information Protection](../deploy-use/configure-policy-templates.md).

## <a name="what-type-of-groups-can-i-use-with-azure-rms"></a>Tipo de grupos que pode utilizar com o Azure RMS?
Para a maioria dos cenários, pode utilizar qualquer tipo de grupo no Azure AD que tenha um endereço de e-mail. Esta regra prática aplica-se sempre ao atribuir direitos de utilização, mas existem algumas exceções para administrar o serviço Azure Rights Management. Para obter mais informações, consulte [requisitos do Azure Information Protection para contas de grupo](../plan-design/prepare.md#azure-information-protection-requirements-for-group-accounts).

## <a name="how-do-i-send-a-protected-email-to-a-gmail-or-hotmail-account"></a>Como envio um e-mail protegido a uma conta do Gmail ou do Hotmail?

Quando utiliza o Exchange Online e o serviço Azure Rights Management, apenas enviar o e-mail para o utilizador como uma mensagem protegida. Por exemplo, pode selecionar o novo **proteger** botão na barra de comando no Outlook na Web, utilize o Outlook **não reencaminhar** opção botão ou menu. Em alternativa, pode selecionar uma etiqueta de Azure Information Protection que aplica-se não reencaminhar para si e automaticamente classifica o e-mail. 

O destinatário verá uma opção para iniciar sessão na sua conta Gmail, Yahoo ou Microsoft e, em seguida, poderá ler o e-mail protegido. Em alternativa, que possam escolher a opção para um código de acesso único ler o e-mail num browser.

Para suportar este cenário, Exchange Online tem de estar ativada para o serviço Azure Rights Management e as novas funcionalidades na encriptação de mensagens do Office 365. Para obter mais informações sobre esta configuração, consulte [Exchange Online: IRM Configuration](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

Para obter mais informações sobre as novas capacidades que incluem suporte todas as contas de e-mail em todos os dispositivos, consulte a seguinte mensagem de blogue: [anunciar novas capacidades disponíveis na encriptação de mensagens do Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Que dispositivos e que tipos de ficheiro são suportados pelo Azure RMS?
Para obter uma lista dos dispositivos que suportam o serviço Azure Rights Management, veja [Dispositivos cliente que suportam a proteção de dados do Azure Rights Management](../get-started/requirements-client-devices.md). Uma vez que nem todos os dispositivos suportados conseguem atualmente suportar todas as funcionalidades de Rights Management, verifique também a tabela [Aplicações otimizadas pelo RMS](../get-started/requirements-applications.md#rms-enlightened-applications).

O serviço Azure Rights Management pode suportar todos os tipos de ficheiro. Para texto, imagem, ficheiros do Microsoft Office (Word, Excel, PowerPoint), ficheiros .pdf e outros tipos de ficheiro de aplicação, o Azure Rights Management fornece proteção nativa que inclui encriptação e imposição dos direitos (permissões). Para todas as outras aplicações e tipos de ficheiro, a proteção genérica fornece autenticação e encapsulamento de ficheiro para verificar se um utilizador tem autorização para abrir o ficheiro.

Para obter uma lista de extensões de nome de ficheiro que são suportadas nativamente pelo Azure Rights Management, veja [Ficheiros suportados pelo cliente do Azure Information Protection](../rms-client/client-admin-guide-file-types.md). As extensões de nome de ficheiro que não estiverem indicadas são suportadas através do cliente do Azure Information Protection que aplica automaticamente a proteção genérica a estes ficheiros.

## <a name="how-do-i-configure-a-mac-computer-to-protect-and-track-documents"></a>Como configurar um computador Mac para proteger e controlar documentos?

Primeiro, confirme se instalou o Office para Mac através da ligação de instalação do software em https://portal.office.com. Para obter instruções completas, veja [Transferir e instalar ou reinstalar o Office 365 ou o Office 2016 num PC ou Mac](https://support.office.com/en-us/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658).

Abra o Outlook e crie um perfil com a conta escolar ou profissional do Office 365. Em seguida, crie uma nova mensagem e faça o seguinte procedimento para configurar o Office, para que possa proteger documentos e e-mails com o serviço Azure Rights Management:

1. Na nova mensagem, no separador **Opções**, clique em **Permissões** e, em seguida, clique em **Verificar Credenciais**.

2. Quando solicitado, especifique os detalhes da conta escolar ou profissional do Office 365 novamente e selecione **Iniciar sessão**. 
    
    Esta ação irá transferir os modelos do Azure Rights Management e **Verificar Credenciais** foi agora substituído por opções que incluem **Sem Restrições**, **Não Encaminhar** e quaisquer modelos do Azure Rights Management que estejam publicados para o seu inquilino. Já pode cancelar esta nova mensagem.

Para proteger uma mensagem de e-mail ou um documento: no separador **Opções**, clique em **Permissões** e escolha uma opção ou um modelo que protege o seu e-mail ou documento.

Para controlar um documento depois de o proteger: a partir de um computador Windows que tenha o cliente do Azure Information Protection instalado, registe o documento no site de controlo de documentos ao utilizar uma aplicação do Office ou o Explorador de Ficheiros. Para obter instruções, veja [Controlar e revogar os documentos](../rms-client/client-track-revoke.md). No seu computador Mac, agora já pode utilizar o browser para aceder ao site de controlo de documentos (https://track.azurerms.com) para controlar e revogar este documento.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>Quando abro um documento do Office protegido por RMS, o ficheiro temporário associado também fica protegido por RMS?
Não. Neste cenário, o ficheiro temporário associado não contém dados do documento original, mas apenas o que o utilizador introduz enquanto o ficheiro está aberto. Ao contrário do ficheiro original, o ficheiro temporário não foi concebido para partilha e permaneceria no dispositivo, protegido por controlos de segurança locais, como o BitLocker e o EFS.

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>A funcionalidade que procuro não funciona com bibliotecas protegidas do SharePoint. Planeiam oferecer suporte para a minha funcionalidade?
Atualmente, o SharePoint suporta protegidos pelo RMS documentos ao utilizar IRM protegido bibliotecas, o que não suportam modelos de Rights Management, controlo de documentos e outras funcionalidades. Para obter mais informações veja a secção [SharePoint Online e SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) no artigo [Aplicações e serviços do Office ](../understand-explore/office-apps-services-support.md).

Se estiver interessado numa funcionalidade específica que ainda não é suportada, fique atento aos anúncios no [Blogue Enterprise Mobility and Security (em inglês)](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services).

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Como posso configurar o OneDrive para Empresas no SharePoint Online, para que os utilizadores possam partilhar os seus ficheiros de forma segura com pessoas dentro e fora da empresa?
Por predefinição, enquanto administrador do Office 365, não lhe cabe a si configurar isto, mas sim aos utilizadores.

Tal como um administrador do site do SharePoint ativa e configura a IRM para uma biblioteca do SharePoint que possui, o OneDrive para Empresas é concebido para os utilizadores ativarem e configurarem a IRM para as suas próprias bibliotecas do OneDrive para Empresas. No entanto, com o PowerShell, pode fazê-lo pelos utilizadores. Para obter instruções, veja a secção [SharePoint Online e OneDrive para Empresas: configuração de IRM](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) no artigo [Office 365: configuração para clientes e serviços online](../deploy-use/configure-office365.md).

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Tem sugestões ou truques para uma implementação com êxito?

Após supervisionar várias implementações e ouvir os nossos clientes, parceiros, consultores e engenheiros de suporte – uma das maiores sugestões que podemos transmitir da nossa experiência: **Crie e implemente políticas simples**.

Como o Azure Information Protection suporta a partilha segura com todas as pessoas, pode ser ambicioso com o alcance da proteção de dados. Mas, seja conservador quando configurar as restrições de utilização de direitos. Para muitas organizações, o maior impacto comercial provém de impedir a fuga de dados ao restringir o acesso a pessoas na sua organização. Claro que, se for necessário, pode ser muito mais granular e impedir que as pessoas imprimam, editem, etc. Mas manter as restrições mais granulares como a exceção para documentos que precisam de alto nível de segurança e não implementam estes direitos de utilização mais restritivos no primeiro dia, mas planeie uma abordagem mais faseada.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Como recuperamos o acesso a ficheiros que foram protegidos por um funcionário que saiu da organização?
Utilize o [funcionalidade de Superutilizador](../deploy-use/configure-super-users.md), que concede a utilização de controlo total de direitos aos utilizadores autorizados para todos os documentos e e-mails que são protegidos pelo seu inquilino. Superutilizadores podem sempre ler este conteúdo protegido e se for necessário, remova a proteção ou volte a protegê-lo para diferentes utilizadores. Esta mesma funcionalidade permite que os serviços autorizados indexem e inspecionem ficheiros, conforme necessário.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Quando testo a revogação no site de controlo do documento, vejo uma mensagem a indicar que as pessoas ainda podem aceder ao documento durante até 30 dias. Este período de tempo é configurável?

Sim. Esta mensagem reflete o [utilizar licença](../deploy-use/configure-usage-rights.md#rights-management-use-license) para esse ficheiro específico. 

Se revogar um ficheiro, essa ação só poderá ser aplicada quando o utilizador autenticar para o serviço Azure Rights Management. Por isso, se um ficheiro tiver um período de validade de licença de utilização de 30 dias e o utilizador já tiver aberto o documento, esse utilizador continuará a ter acesso ao documento enquanto a licença de utilização durar. Quando a licença de utilização expirar, o utilizador terá de ser novamente autenticado. Nessa altura, será rejeitado o acesso ao utilizador porque o documento já estará revogado.

O utilizador que protegeu o documento, o [emissor do Rights Management](../deploy-use/configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) está isento desta revogação e terá sempre acesso aos respetivos documentos. 

O valor predefinido para o período de validade da licença de utilização para um inquilino é 30 dias e esta definição pode ser substituída por uma definição mais restritiva num etiqueta ou modelo. Para obter mais informações sobre a licença de utilização e como configurá-lo, consulte o [utilizar a gestão de direitos de licença](../deploy-use/configure-usage-rights.md#rights-management-use-license) documentação.

## <a name="can-rights-management-prevent-screen-captures"></a>O Rights Management pode impedir capturas de ecrã?
Ao não conceder direitos de **utilização** [de Cópia](../deploy-use/configure-usage-rights.md), o Rights Management pode impedir capturas de ecrãs de muitas das ferramentas de captura de ecrã utilizadas normalmente em plataformas com Windows (Windows 7, Windows 8.1, Windows 10, Windows Phone) e Android. No entanto, os dispositivos iOS e Mac não permitem que as aplicações impeçam capturas de ecrã e os browsers (por exemplo, quando são utilizados com o Outlook Web App e o Office Online) também não podem impedir capturas de ecrã.

Impedir capturas de ecrã pode ajudar a evitar a divulgação por acidente ou por negligência de informações confidenciais. No entanto, existem várias formas de um utilizador partilhar os dados apresentados num ecrã e tirar uma captura de ecrã é apenas um dos métodos possíveis. Por exemplo, um utilizador que esteja determinado em partilhar as informações apresentadas pode tirar uma fotografia com a câmara do telemóvel, reescrever os dados ou simplesmente dizê-las a alguém.

Conforme estes exemplos demonstram, mesmo que todas as plataformas e todos os softwares suportassem as APIs do Rights Management para bloquear as capturas de ecrã, a tecnologia por si só nem sempre pode impedir os utilizadores de partilharem dados que não deviam. O Rights Management pode ajudar a salvaguardar os seus dados importantes com políticas de utilização e autorização, mas esta solução de gestão de direitos de empresa deve ser utilizada em conjunto com outros controlos. Por exemplo, implementar segurança física, monitorizar cuidadosamente as pessoas que têm acesso autorizado aos dados da sua organização e investir na educação dos utilizadores para que estes compreendam que os dados não devem ser partilhados.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Qual a diferença entre um utilizador que protege um e-mail com Não Reencaminhar e um modelo que não inclui o direito de Reencaminhar?

Apesar do nome e do aspeto, **Não Reencaminhar** não é o oposto do direito de Reencaminhar ou um modelo. Na realidade, é um conjunto de direitos que incluem restringir a cópia, impressão e gravação de anexos, para além de restringir o reencaminhamento de e-mails. Os direitos são aplicados dinamicamente aos utilizadores através de destinatários escolhidos e não estaticamente atribuídos pelo administrador. Para obter mais informações, veja a secção [Opção Não Reencaminhar para e-mails](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) em [Configurar os direitos de utilização do Azure Rights Management](../deploy-use/configure-usage-rights.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


