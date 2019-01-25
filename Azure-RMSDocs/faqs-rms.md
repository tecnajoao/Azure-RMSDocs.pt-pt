---
title: FAQs do Azure RMS – AIP
description: Algumas perguntas mais frequentes sobre o serviço de proteção de dados, o Azure Rights Management (Azure RMS), do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: information-protection
ms.custom: askipteam
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ac079a7046b6166b89c828054ed5f94e756fa99f
ms.sourcegitcommit: 8bda26b8b84cb8b66ae8f927906710d60c4b6a80
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397985"
---
# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Perguntas mais frequentes sobre a proteção de dados no Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Tem uma pergunta sobre o serviço de proteção de dados, o Azure Rights Management, do Azure Information Protection? Verifique se a resposta está aqui.

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Os ficheiros têm de estar na cloud para serem protegidos pelo Azure Rights Management?
Não, este é um equívoco comum. O serviço Azure Rights Management (e a Microsoft) não vê nem armazena os seus dados como parte do processo de proteção das informações. As informações que protege nunca são enviadas para ou armazenadas no Azure, a menos que as armazene explicitamente no Azure ou utilize outro serviço cloud que as armazene no Azure.

Para obter mais informações, veja [Como funciona o Azure RMS Under the hood (Como funciona o Azure RMS? Nos bastidores)](./how-does-it-work.md) para compreender como uma fórmula de cola secreta criada e armazenada no local é protegida pelo serviço Azure Rights Management, mas permanece no local.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Qual é a diferença entre a encriptação do Azure Rights Management e a encriptação noutros serviços cloud da Microsoft?

A Microsoft fornece múltiplas tecnologias de encriptação que lhe permitem proteger os seus dados para cenários diferentes e muitas vezes complementares. Por exemplo, enquanto o Office 365 oferece encriptação para dados inativos armazenados no Office 365, o serviço Azure Rights Management do Azure Information Protection encripta os seus dados independentemente para que estes estejam protegidos, qualquer que seja o local ou a forma de transmissão.

Estas tecnologias de encriptação são complementares e para as utilizar tem de as ativar e configurar independentemente. Quando o fizer, poderá ter a opção de utilizar a sua própria chave para a encriptação, um cenário também conhecido como "BYOK". Ativar o BYOK para uma destas tecnologias não afeta as outras tecnologias existentes. Por exemplo, pode utilizar o BYOK para o Azure Information Protection e não o utilizar para outras tecnologias de encriptação e vice-versa. As chaves utilizadas por estas diferentes tecnologias podem ser as mesmas ou diferentes, dependendo da forma como configurou as opções de encriptação para cada serviço.

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>Qual é a diferença entre BYOK e HYOK e quando devo utilizá-los?

**Bring Your Own Key – Traga a Sua Própria Chave** (BYOK), no contexto do Azure Information Protection, é quando cria a sua própria chave no local para a proteção do Azure Rights Management. Em seguida, transfere essa chave para um módulo de segurança de hardware (HSM) no Azure Key Vault, onde continua a ser o proprietário e a gerir a sua chave. Se não o fizer, a proteção do Azure Rights Management utilizará uma chave criada e gerida automaticamente no Azure. Esta configuração predefinida é referida como "gerida pela Microsoft" em vez de "gerida pelo cliente" (opção BYOK).

Para obter mais informações sobre o BYOK e se deve escolher esta topologia de chaves para a sua organização, veja [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

**Hold your own key – tenha a sua própria chave** (HYOK), no contexto do Azure Information Protection, destina-se a poucas organizações com um subconjunto de documentos ou e-mails que não podem ser protegidos por uma chave armazenada na cloud. Para estas organizações, esta restrição aplica-se mesmo que tenham criado e gerido a chave através de BYOK. A restrição pode dever-se muitas vezes a motivos de regulamentação e conformidade e a configuração HYOK só deve ser aplicada a informações "Confidenciais", que nunca serão partilhadas fora da organização, que serão consumidas apenas na rede interna e que não precisam de ser acedidas a partir de dispositivos móveis.

Para estas exceções (normalmente, menos de 10% de todos os conteúdos que têm de ser protegidos), as organizações podem utilizar uma solução no local, os Serviços de Gestão de Direitos do Active Directory, para criar a chave que permanece no local. Com esta solução, os computadores obtêm a política do Azure Information Protection a partir da cloud, mas estes conteúdos identificados podem ser protegidos com a chave no local.

Para obter mais informações sobre o HYOK, certificar-se de que compreende as suas limitações e restrições e obter orientações para quando o utilizar, veja [Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS](configure-adrms-restrictions.md).

## <a name="can-i-now-use-byok-with-exchange-online"></a>Agora posso utilizar BYOK com o Exchange Online?

Sim, pode agora utilizar o BYOK com o Exchange Online quando seguir as instruções em [configurar novas capacidades de encriptação de mensagens do Office 365 criadas com base no Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Estas instruções ativar os novos recursos no Exchange Online, que suportam a utilização de BYOK para o Azure Information Protection, bem como a nova encriptação de mensagens do Office 365.

Para obter mais informações sobre esta alteração, consulte o anúncio do blogue: [Encriptação de mensagens do Office 365 com os novos recursos](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801)

## <a name="where-can-i-find-information-about-third-party-solutions-that-integrate-with-azure-rms"></a>Onde posso encontrar informações sobre soluções de terceiros que se integram com o Azure RMS?

Muitos fornecedores de software já têm soluções ou estão a implementar soluções que se integram no Azure Rights Management e a lista está a crescer rapidamente. Poderá considerar útil ler o [soluções otimizadas pelo RMS](requirements-applications.md#rms-enlightened-solutions) listar e obter as atualizações mais recentes do [Microsoft Mobility@MSFTMobility ](https://twitter.com/MSFTMobility) no Twitter. Verifique também a [Guia do programador](./develop/developers-guide.md) e publique as suas questões de integração específicos no Azure Information Protection [site do Yammer](https://www.yammer.com/AskIPTeam).

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Existe um pacote de gestão ou o mecanismo de monitorização semelhante para o conector RMS?

Embora o conector do Rights Management registe mensagens de erro, aviso e informações no registo de eventos, não existe um pacote de gestão que inclua a monitorização destes eventos. No entanto, a lista de eventos e as suas descrições, com mais informações para ajudá-lo a aplicar as medidas corretivas está documentada em [Monitorizar o conector do Azure Rights Management](monitor-rms-connector.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Tenho de ser um administrador global para configurar o Azure RMS ou posso delegar noutros administradores?

Com a função de administrador do Information Protection introduzidas recentemente, este perguntas (e respostas) agora foi movido para a página de FAQ principal: [Precisa de ser um administrador global para configurar o Azure Information Protection, ou posso delegar noutros administradores?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

## <a name="how-do-i-create-a-new-custom-template-in-the-azure-portal"></a>Como posso criar um novo modelo personalizado no portal do Azure?

Modelos personalizados foram movidas para o portal do Azure, onde pode continuar a geri-los como modelos ou convertê-los em etiquetas. Para criar um novo modelo, crie uma nova etiqueta e configure as configurações de proteção de dados do Azure RMS. Nos bastidores, esta ação cria um novo modelo que pode ser acedido por serviços e aplicações que se integram nos modelos do Rights Management.

Para obter mais informações sobre os modelos no portal do Azure, consulte [configurando e gerenciando modelos do Azure Information Protection](configure-policy-templates.md).

## <a name="ive-protected-a-document-and-now-want-to-change-the-usage-rights-or-add-usersdo-i-need-to-reprotect-the-document"></a>Eu protegeu um documento e agora Quero alterar os direitos de utilização ou adicionar utilizadores, é necessário voltar a proteger o documento?

Se o documento tiver sido protegido com uma etiqueta ou um modelo, não é necessário para voltar a proteger o documento. Modificar o modelo ou etiqueta fazendo as alterações para os direitos de utilização ou adicionar novos grupos (ou utilizadores) e, em seguida, guardar estas alterações:

- Quando um utilizador não tenha acedido o documento antes de efetuadas as alterações, as alterações entrem em vigor assim que o usuário abre o documento.

- Quando um utilizador acedeu já o documento, essas alterações entrem em vigor quando seus [utilizar a licença](configure-usage-rights.md#rights-management-use-license) expira. Voltar a proteger o documento apenas se está ansioso para a licença de utilização a expirar. Proteger novamente efetivamente cria uma nova versão do documento e, portanto, uma nova licença de utilização para o utilizador.

Em alternativa, se já tiver configurado um grupo para as permissões necessárias, pode alterar a associação a grupos para incluir ou excluir utilizadores e não é necessário para alterar a etiqueta ou modelo. Poderá haver um pequeno atraso antes das alterações entrem em vigor, porque a associação a grupos é [em cache](prepare.md#group-membership-caching-by-azure-information-protection) pelo serviço Azure Rights Management.

Se o ficheiro foi protegido ao utilizar permissões personalizadas, não é possível alterar as permissões para o documento existente. Tem de proteger o documento novamente e especifique todos os utilizadores e todos os direitos de utilização que são necessários para esta nova versão do documento. Para voltar a proteger um documento protegido, tem de ter o direito de utilização controlo total.

Sugestão: Para verificar se um documento foi protegido por um modelo ou ao utilizar a permissão personalizada, utilize o [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) cmdlet do PowerShell. Sempre a ver uma descrição do modelo de **acesso restrito** permissões personalizadas, com um ID de modelo exclusivo que não são apresentadas quando executa [Get-RMSTemplate](/powershell/module/azureinformationprotection/get-rmstemplate).

## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Tenho uma implementação híbrida do Exchange com alguns utilizadores no Exchange Online e outros no Exchange Server. Isto é suportado pelo Azure RMS?
Com certeza e o lado bom é, os utilizadores são capazes de forma totalmente integrada protegerem e consumirem e-mails e anexos protegidos nas duas implementações do Exchange. Para esta configuração, [ativar o Azure RMS](activate-service.md) e [ativar a IRM para o Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), em seguida, [implementar e configurar o conector RMS](deploy-rms-connector.md) para o Exchange Server.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azurerms"></a>Se utilizar esta proteção meu ambiente de produção, é minha empresa fica presa a solução ou o risco de perder o acesso aos conteúdos que protegemos com o Azure RMS?
Não, sempre permanece no controlo dos seus dados e pode continuar a aceder aos mesmos, mesmo se optar por deixar de utilizar o serviço Azure Rights Management. Para obter mais informações, veja [Desativar o Azure Rights Management](decommission-deactivate.md).

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Posso controlar que utilizadores podem aceder ao Azure RMS para proteger o conteúdo?
Sim, o serviço Azure Rights Management tem controlos de integração do utilizador para este cenário. Para obter mais informações, veja a secção [Configurar os controlos de inclusão para uma implementação faseada](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) no artigo [Ativar o Azure Rights Management](activate-service.md).

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Posso impedir que os utilizadores partilhem documentos protegidos com organizações específicas?
Um dos maiores benefícios de utilização do serviço Azure Rights Management para proteção de dados é que suporta a colaboração empresa-empresa sem ter de configurar confianças explícitas para cada organização parceira, porque trata do Azure AD a autenticação por si.

Não existe uma opção de administração para impedir que os utilizadores partilhem documentos de forma segura com organizações específicas. Por exemplo, imagine que pretende bloquear uma organização na qual não confia ou que tem uma empresa concorrente. Não faria sentido impedir o serviço Azure Rights Management de enviar documentos protegidos aos utilizadores nessas organizações, porque os seus utilizadores iriam partilhar os seus documentos desprotegidos, que é provavelmente a última coisa que quer que aconteça neste cenário. Por exemplo, não poderia identificar quem está a partilhar documentos confidenciais da empresa com os utilizadores nessas organizações, o que pode fazer quando o documento (ou e-mail) é protegido pelo serviço Azure Rights Management.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>Quando partilho um documento protegido com alguém fora da minha empresa, como é que esse utilizador é autenticado?

Por predefinição, o serviço Azure Rights Management utiliza uma conta do Azure Active Directory e um endereço de e-mail associado para a autenticação de utilizador, o que torna a colaboração empresa-empresa integrada para os administradores. Se a outra organização utilizar serviços do Azure, os utilizadores já terão contas no Azure Active Directory, mesmo que estas contas tenham sido criadas e geridas no local e, em seguida, sincronizadas com o Azure. Se a organização tiver o Office 365, nos bastidores, este serviço também utiliza o Azure Active Directory para as contas de utilizador. Se a organização do utilizador não tiver contas geridas no Azure, os utilizadores podem inscrever-se no [RMS para utilizadores individuais](./rms-for-individuals.md), que cria um diretório e um inquilino do Azure não gerido para a organização com uma conta para o utilizador, para que este utilizador (e utilizadores subsequentes) possa ser autenticado para o serviço Azure Rights Management.

O método de autenticação para estas contas pode variar, dependendo da forma como o administrador na outra organização configurou as contas do Azure Active Directory. Por exemplo, eles podem utilizar palavras-passe que foram criadas para estas contas, Federação ou palavras-passe que foram criadas nos serviços de domínio do Active Directory e, em seguida, sincronizadas com o Azure Active Directory.

Outros métodos de autenticação:

- Se proteger um e-mail com um anexo de documento do Office para um utilizador que não tem uma conta no Azure AD, altera o método de autenticação. O serviço Azure Rights Management está Federado com alguns fornecedores de identidade de redes sociais populares, como o Gmail. Se o fornecedor de e-mail do utilizador for suportado, o utilizador pode iniciar sessão para esse serviço e o respetivo fornecedor de e-mail é responsável por autenticá-los. Se o fornecedor de e-mail do utilizador não é suportado, ou uma preferência, o utilizador pode aplicar-se para um código de acesso único que autentica-los e exibe a mensagem de e-mail com o documento protegido num navegador da web.

- O Azure Information Protection pode utilizar contas Microsoft para aplicativos compatíveis. Atualmente, nem todos os aplicativos podem abrir conteúdo protegido, quando uma conta Microsoft é utilizada para autenticação. [Mais informações](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Posso adicionar utilizadores externos (pessoas que não pertencem à minha empresa) a modelos personalizados?

Sim. O [definições de proteção](configure-policy-protection.md) que pode configurar no portal do Azure lhe permite adicionar permissões a utilizadores e grupos externos à sua organização e até todos os utilizadores noutra organização. Poderá considerar útil para fazer referência ao exemplo passo a passo, [proteger colaboração de documentos utilizando o Azure Information Protection](secure-collaboration-documents.md). 

Tenha em atenção que se tiver etiquetas do Azure Information Protection, tem primeiro de converter seu modelo personalizado para um rótulo antes de poder configurar estas definições de proteção no portal do Azure. Para obter mais informações, consulte [configurando e gerenciando modelos do Azure Information Protection](configure-policy-templates.md).

Em alternativa, pode adicionar utilizadores externos para modelos personalizados (e rótulos) com o PowerShell. Esta configuração requer a utilização de um objeto de definição de direitos que utiliza para atualizar o modelo:

1. Especifique os endereços de e-mail externos e os seus direitos num objeto de definição de direitos, utilizando o [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) cmdlet para criar uma variável.

2. Fornecer esta variável ao parâmetro RightsDefinition com o [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) cmdlet.

    Adicionar utilizadores a um modelo existente, tem de definir os objetos de definição de direitos para os utilizadores existentes nos modelos, além dos novos utilizadores. Para este cenário, pode achar útil **exemplo 3: Adicionar novos utilizadores e os direitos para um modelo personalizado** partir de [exemplos](/powershell/module/aadrm/set-aadrmtemplateproperty#examples) secção para o cmdlet.

## <a name="what-type-of-groups-can-i-use-with-azure-rms"></a>Que tipo de grupos pode utilizar com o Azure RMS?
Na maioria dos cenários, pode usar qualquer tipo de grupo no Azure AD que tenha um endereço de e-mail. Esta regra geral aplica-se sempre ao atribuir direitos de utilização, mas existem algumas exceções para administrar o serviço Azure Rights Management. Para obter mais informações, consulte [requisitos do Azure Information Protection para contas de grupo](prepare.md#azure-information-protection-requirements-for-group-accounts).

## <a name="how-do-i-send-a-protected-email-to-a-gmail-or-hotmail-account"></a>Como envio um e-mail protegido a uma conta do Gmail ou do Hotmail?

Quando utiliza o Exchange Online e o serviço Azure Rights Management, apenas envia o e-mail para o usuário como uma mensagem protegida. Por exemplo, pode selecionar o novo **Protect** botão na barra de comando do Outlook na Web, utilize o Outlook **não reencaminhar** a opção de botão ou menu. Em alternativa, pode selecionar uma etiqueta do Azure Information Protection que aplica-se não reencaminhar para automaticamente e classifica o e-mail.

O destinatário verá uma opção para iniciar sessão na sua conta Gmail, Yahoo ou Microsoft e, em seguida, podem ler a mensagem de e-mail protegida. Em alternativa, podem escolher a opção para um código de acesso único ler o e-mail num browser.

Para suportar este cenário, Exchange Online tem de estar ativada para o serviço Azure Rights Management e os novos recursos na encriptação de mensagens do Office 365. Para obter mais informações sobre esta configuração, consulte [Exchange Online: Configuração de IRM](configure-office365.md#exchangeonline-irm-configuration).

Para obter mais informações sobre os novos recursos que incluem o suporte a todas as contas de e-mail em todos os dispositivos, consulte a seguinte mensagem de blogue: [Apresentamos novas funcionalidades disponíveis na encriptação de mensagens do Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Que dispositivos e que tipos de ficheiro são suportados pelo Azure RMS?
Para obter uma lista dos dispositivos que suportam o serviço Azure Rights Management, veja [Dispositivos cliente que suportam a proteção de dados do Azure Rights Management](./requirements-client-devices.md). Uma vez que nem todos os dispositivos suportados conseguem atualmente suportar todas as funcionalidades de Rights Management, verifique também a tabela [Aplicações otimizadas pelo RMS](./requirements-applications.md#rms-enlightened-applications).

O serviço Azure Rights Management pode suportar todos os tipos de ficheiro. Para texto, imagem, ficheiros do Microsoft Office (Word, Excel, PowerPoint), ficheiros .pdf e outros tipos de ficheiro de aplicação, o Azure Rights Management fornece proteção nativa que inclui encriptação e imposição dos direitos (permissões). Para todas as outras aplicações e tipos de ficheiro, a proteção genérica fornece autenticação e encapsulamento de ficheiro para verificar se um utilizador tem autorização para abrir o ficheiro.

Para obter uma lista de extensões de nome de ficheiro que são suportadas nativamente pelo Azure Rights Management, veja [Ficheiros suportados pelo cliente do Azure Information Protection](./rms-client/client-admin-guide-file-types.md). As extensões de nome de ficheiro que não estiverem indicadas são suportadas através do cliente do Azure Information Protection que aplica automaticamente a proteção genérica a estes ficheiros.

## <a name="how-do-i-configure-a-mac-computer-to-protect-and-track-documents"></a>Como configurar um computador Mac para proteger e controlar documentos?

Primeiro, certifique-se de que tem instalado Office para Mac, utilizando a ligação de instalação de software de https://portal.office.com. Para obter instruções completas, veja [Transferir e instalar ou reinstalar o Office 365 ou o Office 2016 num PC ou Mac](https://support.office.com/en-us/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658).

Abra o Outlook e crie um perfil com a conta escolar ou profissional do Office 365. Em seguida, crie uma nova mensagem e faça o seguinte procedimento para configurar o Office, para que possa proteger documentos e e-mails com o serviço Azure Rights Management:

1. Na nova mensagem, no separador **Opções**, clique em **Permissões** e, em seguida, clique em **Verificar Credenciais**.

2. Quando solicitado, especifique os detalhes da conta escolar ou profissional do Office 365 novamente e selecione **Iniciar sessão**.

    Esta ação irá transferir os modelos do Azure Rights Management e **Verificar Credenciais** foi agora substituído por opções que incluem **Sem Restrições**, **Não Encaminhar** e quaisquer modelos do Azure Rights Management que estejam publicados para o seu inquilino. Já pode cancelar esta nova mensagem.

Para proteger uma mensagem de e-mail ou um documento: Sobre o **opções** separador, clique em **permissões** e escolha uma opção ou um modelo que protege o seu e-mail ou documento.

Para controlar um documento depois de o proteger: Num computador Windows que tenha o cliente do Azure Information Protection instalado, registe o documento com o site de controlo utilizando um aplicativo do Office ou o Explorador de ficheiros de documentos. Para obter instruções, veja [Controlar e revogar os documentos](./rms-client/client-track-revoke.md). No seu computador Mac, agora pode utilizar o browser para ir para o site de controlo de documentos (https://track.azurerms.com) para controlar e revogar este documento.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>Quando abro um documento do Office protegido por RMS, o ficheiro temporário associado também fica protegido por RMS?
Não. Neste cenário, o ficheiro temporário associado não contém dados do documento original, mas apenas o que o utilizador introduz enquanto o ficheiro está aberto. Ao contrário do ficheiro original, o ficheiro temporário não foi concebido para partilha e permaneceria no dispositivo, protegido por controlos de segurança locais, como o BitLocker e o EFS.

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>A funcionalidade que procuro não funciona com bibliotecas protegidas do SharePoint. Planeiam oferecer suporte para a minha funcionalidade?
Atualmente, o SharePoint suporta protegidos pelo RMS documentos ao utilizar IRM protegidos bibliotecas, o que não suportam modelos do Rights Management, controlo de documentos e outras funcionalidades. Para obter mais informações veja a secção [SharePoint Online e SharePoint Server](./office-apps-services-support.md#sharepoint-online-and-sharepoint-server) no artigo [Aplicações e serviços do Office ](./office-apps-services-support.md).

Se estiver interessado numa funcionalidade específica que ainda não é suportada, fique atento aos anúncios no [Blogue Enterprise Mobility and Security (em inglês)](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-rights-management-services).

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Como posso configurar o OneDrive para Empresas no SharePoint Online, para que os utilizadores possam partilhar os seus ficheiros de forma segura com pessoas dentro e fora da empresa?
Por predefinição, enquanto administrador do Office 365, não lhe cabe a si configurar isto, mas sim aos utilizadores.

Tal como um administrador do site do SharePoint ativa e configura a IRM para uma biblioteca do SharePoint que possui, o OneDrive para Empresas é concebido para os utilizadores ativarem e configurarem a IRM para as suas próprias bibliotecas do OneDrive para Empresas. No entanto, com o PowerShell, pode fazê-lo pelos utilizadores. Para obter instruções, consulte o [SharePoint Online e OneDrive para empresas: Configuração de IRM](configure-office365.md#sharepointonline-and-onedrive-for-business-irm-configuration) secção o [do Office 365: Configuração para clientes e serviços online](configure-office365.md) artigo.

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Tem sugestões ou truques para uma implementação com êxito?

Após supervisionar várias implementações e ouvir os nossos clientes, parceiros, consultores e engenheiros de suporte – uma das maiores sugestões que podemos transmitir da experiência: **Crie e implemente políticas simples**.

Como o Azure Information Protection suporta a partilha segura com todas as pessoas, pode ser ambicioso com o alcance da proteção de dados. Mas, seja conservador quando configurar restrições de utilização de direitos. Para muitas organizações, o maior impacto comercial provém de impedir a fuga de dados ao restringir o acesso a pessoas na sua organização. Claro que, se for necessário, pode ser muito mais granular e impedir que as pessoas imprimam, editem, etc. Mas manter as restrições mais granulares, como a exceção para documentos que precisam de segurança de alto nível e não implementam estes direitos de utilização mais restritivos no primeiro dia, mas planeie uma abordagem mais faseada.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Como recuperamos o acesso a ficheiros que foram protegidos por um funcionário que saiu da organização?
Utilize o [funcionalidade de Superutilizador](configure-super-users.md), que concede a utilização de controlo total de direitos aos utilizadores autorizados para todos os documentos e e-mails que estão protegidos pelo seu inquilino. Superutilizadores podem sempre ler este conteúdo protegido e se for necessário, remover a proteção ou volte a protegê-lo para diferentes usuários. Esta mesma funcionalidade permite que os serviços autorizados indexem e inspecionem ficheiros, conforme necessário.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Quando testo a revogação no site de controlo do documento, vejo uma mensagem a indicar que as pessoas ainda podem aceder ao documento durante até 30 dias. Este período de tempo é configurável?

Sim. Esta mensagem reflete a [utilizar a licença](configure-usage-rights.md#rights-management-use-license) para esse ficheiro específico.

Se revogar um ficheiro, essa ação só poderá ser aplicada quando o utilizador autenticar para o serviço Azure Rights Management. Por isso, se um ficheiro tiver um período de validade de licença de utilização de 30 dias e o utilizador já tiver aberto o documento, esse utilizador continuará a ter acesso ao documento enquanto a licença de utilização durar. Quando a licença de utilização expirar, o utilizador terá de ser novamente autenticado. Nessa altura, será rejeitado o acesso ao utilizador porque o documento já estará revogado.

O utilizador que protegeu o documento, o [emissor do Rights Management](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) está isento desta revogação e terá sempre acesso aos respetivos documentos.

O valor predefinido para o período de validade de licença de utilização de um inquilino é de 30 dias e esta definição pode ser substituída por uma definição mais restritiva numa etiqueta ou modelo. Para obter mais informações sobre a licença de utilização e como configurá-lo, consulte a [utilizar a gestão de direitos de licença](configure-usage-rights.md#rights-management-use-license) documentação.

## <a name="can-rights-management-prevent-screen-captures"></a>O Rights Management pode impedir capturas de ecrã?
Ao não conceder direitos de **utilização** [de Cópia](configure-usage-rights.md), o Rights Management pode impedir capturas de ecrãs de muitas das ferramentas de captura de ecrã utilizadas normalmente em plataformas com Windows (Windows 7, Windows 8.1, Windows 10, Windows Phone) e Android. No entanto, os dispositivos iOS e Mac não permitem que as aplicações impeçam capturas de ecrã e os browsers (por exemplo, quando são utilizados com o Outlook Web App e o Office Online) também não podem impedir capturas de ecrã.

Impedir capturas de ecrã pode ajudar a evitar a divulgação por acidente ou por negligência de informações confidenciais. No entanto, existem várias formas de um utilizador partilhar os dados apresentados num ecrã e tirar uma captura de ecrã é apenas um dos métodos possíveis. Por exemplo, um utilizador que esteja determinado em partilhar as informações apresentadas pode tirar uma fotografia com a câmara do telemóvel, reescrever os dados ou simplesmente dizê-las a alguém.

Conforme estes exemplos demonstram, mesmo que todas as plataformas e todos os softwares suportassem as APIs do Rights Management para bloquear as capturas de ecrã, a tecnologia por si só nem sempre pode impedir os utilizadores de partilharem dados que não deviam. O Rights Management pode ajudar a salvaguardar os seus dados importantes com políticas de utilização e autorização, mas esta solução de gestão de direitos de empresa deve ser utilizada em conjunto com outros controlos. Por exemplo, implementar segurança física, monitorizar cuidadosamente as pessoas que têm acesso autorizado aos dados da sua organização e investir na educação dos utilizadores para que estes compreendam que os dados não devem ser partilhados.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Qual a diferença entre um utilizador que protege um e-mail com Não Reencaminhar e um modelo que não inclui o direito de Reencaminhar?

Apesar do nome e do aspeto, **Não Reencaminhar** não é o oposto do direito de Reencaminhar ou um modelo. Na realidade, é um conjunto de direitos que incluem restringir a cópia, impressão e gravação de anexos, para além de restringir o reencaminhamento de e-mails. Os direitos são aplicados dinamicamente aos utilizadores através de destinatários escolhidos e não estaticamente atribuídos pelo administrador. Para obter mais informações, veja a secção [Opção Não Reencaminhar para e-mails](configure-usage-rights.md#do-not-forward-option-for-emails) em [Configurar os direitos de utilização do Azure Rights Management](configure-usage-rights.md).

