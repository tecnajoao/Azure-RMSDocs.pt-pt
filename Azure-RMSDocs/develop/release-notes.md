---
title: "Novidades e notas de versão"
description: "Descreve as funcionalidades e alterações importantes nesta versão nova do SDK RMS."
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2017
ms.topic: article
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: df78d1f1740128c79c944a6b5d33353141933d78
ms.sourcegitcommit: faaab68064f365c977dfd1890f7c8b05a144a95c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2017
---
# <a name="whats-new-and-release-notes"></a>Novidades e Notas de versão

## <a name="whats-new"></a>Novidades

Este tópico descreve as funcionalidades nesta versão nova do v4.x RMS SDK e alterações importantes.

-   [Novidades para Julho de 2017](#new-for-july-2017)
-   [Atualização de Outubro de 2016](#October-2016-update)
-   [Atualização de Junho de 2016](#new-for-June-2016)
-   [Atualização de Dezembro de 2015](#december-2015-update)
-   [Atualização de Julho de 2015 – adiciona suporte para Linux / desenvolvimento do C++](#july-2015-update-adds-support-for-linux-c-developm)
-   [Maio de atualização de 2015 – adiciona o controlo de registo](#may-2015-update-adds-logging-control)
-   [Atualizar Fevereiro de 2015 - suporte para aplicações da loja do Windows adiciona](#february-2015-update-adds-windows-store-application-support)
-   [Atualização de Janeiro de 2015 – adiciona o suporte da plataforma WinPhone](#january-2015-update-adds-winphone-platform-support)
-   [Atualização de Outubro de 2014 – atualizar para o SDK do Microsoft RMS 4.1](#october-2014-update-upgrade-to-microsoft-rms-sdk-4-1)
-   [Notas de versão](#release-notes)
-   [Perguntas mais frequentes](#frequently-asked-questions)

### <a name="new-for-july-2017"></a>Novidades para Julho de 2017

A atualização para a nossa versão de Julho incluídos incrementando a revisão do SDK, 4.2.5 agora.

- Android SDK: A aplicação pode agora **definir o registo ao nível no-a-momento** com o SDK Android. Para obter mais informações, consulte [Como: ativar registo de erros e de desempenho](https://docs.microsoft.com/en-us/information-protection/develop/enabling-logging)
- O SDK iOS não suporta o nível de registo. 
- O SDK agora devolve um erro para obter um token de acesso nula.

### <a name="october-2016-update"></a>Atualização de Outubro de 2016

- Implemente algumas correções de erros de back-end.
- Ative bitcode para o Apple iOS/OSX SDK.

### <a name="june-2016-update"></a>Atualização de Junho de 2016

- **Suporte para a autenticação moderna** -coloca baseada no Active Directory Authentication Library ADAL início de sessão para o RMS otimizada por aplicações. Permite início de sessão funcionalidades como o multi-factor Authentication (MFA), fornecedores de identidade de terceiros baseados em SAML com aplicações de cliente de RMS, smart card e a autenticação baseada em certificado e remove a necessidade de aplicações a utilizar o básico protocolo de autenticação.
- **Suporte ao Controlo de Documentos** - os programadores agora podem ativar o controlo de documentos ao proteger um documento nas suas aplicações
- Melhoramentos de desempenho
- Correções

### <a name="december-2015-update"></a>Atualização de dezembro de 2015

Com esta versão, o SDK RMS para dispositivos está agora na versão 4.2 e adiciona:

-   O controlo de documentos e o RMS apenas online para sistemas operativos Android e iOS/OS X.

    Para obter detalhes e instruções de utilização no iOS/OS X, consulte o [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx) classe, que fornece informações de controlo e o documento adicional método de registo de controlo no [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx). Existem adições semelhantes para o Android em [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx) e [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx).

    Para obter uma descrição detalhada da funcionalidade de controlo de documentos, consulte [Como: utilizar o controlo de documentos](how-to-use-document-tracking.md).

-   Um conjunto de métodos síncronos paralelos às versões assíncronas para a API do Android:

    [Método síncrono CustomProtectedInputStream.create](https://msdn.microsoft.com/library/mt631362.aspx)

    [Método síncrono CustomProtectedOutputStream.create](https://msdn.microsoft.com/library/mt631363.aspx)

    [Método síncrono ProtectedFileInputStream.create](https://msdn.microsoft.com/library/mt631375.aspx)

    [Método síncrono ProtectedFileOutputStream.create](https://msdn.microsoft.com/library/mt631376.aspx)

    [Método síncrono TemplateDescriptor.getTemplates](https://msdn.microsoft.com/library/mt631380.aspx)

    [Método síncrono UserPolicy.acquire](https://msdn.microsoft.com/library/mt631384.aspx)

    [Método síncrono UserPolicy.create (PolicyDescriptor…)**](https://msdn.microsoft.com/library/mt631385.aspx)

    [Método síncrono UserPolicy.create (TemplateDescriptor…)](https://msdn.microsoft.com/library/mt631386.aspx)

-   Foi adicionada uma nova classe [ProtectedBuffer](https://msdn.microsoft.com/library/mt631369.aspx) à API do Android.
-   Atualizações para melhorar a experiência de resolução de problemas e de mensagens de erro.
-   Melhorias de desempenho significativas para operações de criptografia.

### <a name="july-2015-update---adds-support-for-linux--c-development"></a>Atualização de julho de 2015 – adiciona suporte para a programação em Linux/C++

Esta versão adiciona as seguintes atualizações:

-   SDK RMS 4.1 para plataformas Linux

    Para obter mais informações, consulte [Introdução](get-started.md).

### <a name="may-2015-update---adds-logging-control"></a>Atualização de maio de 2015 – adiciona o controlo de registo

Esta versão adiciona suporte para as seguintes atualizações:

-   iOS

    A encriptação e a desencriptação de aplicações podem funcionar independentemente e em paralelo.

    Para mais informações, consulte [MSProtector](https://msdn.microsoft.com/library/mt210993.aspx).

    Definições de controlo do nível de registo ativadas.

    Para obter mais informações, consulte [Como: ativar registo de erros e de desempenho](enabling-logging.md)

    Suporte de limpeza da cache adicionado.

    Para mais informações, consulte [MSProtection:resetStateWithCompletionBlock](https://msdn.microsoft.com/library/mt210991.aspx).

### <a name="february-2015-update---adds-windows-store-application-support"></a>Atualização de fevereiro de 2015 – adiciona o suporte para aplicações da Loja Windows

Esta versão adiciona suporte para aplicações da loja Windows e fornece paridade funcional com o Windows Phone, Android e versão do iOS/OS X do SDK RMS 4.1.

### <a name="january-2015-update---adds-winphone-platform-support"></a>Atualização de janeiro de 2015 – adiciona o suporte da plataforma WinPhone

Esta versão adiciona o suporte para o sistema operativo Windows Phone e fornece paridade funcional com o lançamento para Android e iOS/OS X do SDK RMS 4.1.

### <a name="october-2014-update---upgrade-to-microsoft-rms-sdk-41"></a>Atualização de outubro de 2014 – atualizar para o SDK Microsoft RMS 4.1

O lançamento da versão 4.1 do SDK RMS adiciona as seguintes funcionalidades novas para o Google Android e Apple iOS/OS X.

-   Extensões da API do SDK iOS/OS X para o processamento do *consentimento do utilizador*, permitindo a confirmação do utilizador de comportamentos do SDK. Atualmente, o controlo de documentos e o acesso a URLs desconhecidos do serviço AD RMS são os tipos de consentimento suportados.

    Para mais informações, consulte, como exemplo, a versão da API do Android da [interface ConsentCallback](https://msdn.microsoft.com/library/dn833503.aspx).

-   O iOS 8 e o OS X 10.10 (Yosemite) já são suportados. De igual modo, houve algumas alterações de nomes de propriedades obrigatórias pelo Xcode 6.

    Exemplo: alterou-se MSUserPolicy.name para [MSUserPolicy.policyName](https://msdn.microsoft.com/library/dn790799.aspx).

## <a name="release-notes"></a>Notas de versão

Esta secção apresenta as informações sobre as versões atuais e anteriores das APIs SDK Microsoft Rights Management 4. x que o programador deve ter em consideração.

**SDK AD RMS 4.1 – Lançamento de Disponibilidade Global para as plataformas iOS / OS X e Android**

-   **Suporte do AD RMS** – os administradores de TI podem utilizar aplicações com suporte RMS em dispositivos móveis com as novas extensões para dispositivos móveis do servidor AD RMS.
-   **Consumo offline** -os utilizadores finais podem aceder a dados protegidos do RMS offline.
-   **Autorização Separada** – os programadores podem utilizar a sua própria biblioteca de autenticação para o Azure RMS e AD RMS (ou utilizar a [Azure AD Authentication Library (ADAL)](https://MSDN.Microsoft.Com/library/jj573266.aspx) recomendada).
-   **IU Separada** – os programadores podem criar a sua interface de utilizador para proteger e consumir documentos protegidos por RMS.
-   **Reestruturado API** -os programadores podem agora desfrutar uma simples e transparente encriptação e desencriptação API, que fornece a experiência de utilizador e comportamentos de RMS consistentes, com esforços mínimos.

**Comum a todas as plataformas**

-   As APIs do SDK RMS 4.x não são *seguras para os threads*.

**Android**

-   Quando utilizar uma aplicação de exemplo num dispositivo Amazon® Kindle para ver anexos .ptxt, tem primeiro de transferir o ficheiro antes de o visualizar.

    **Solução** -um problema conhecido que será resolvido mais tarde.

-   Uma aplicação que utilize o SDK pode falhar se forem permitidas várias instâncias.

    **Solução** – certifique-se de que a aplicação não permite chamadas de várias instâncias para a API do Android.

-   Quando utilizar o [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx). Write (byte\[ \] array, int offset, int comprimento) método com um comprimento diferente do *Array* valor, não consigo para consuma o conteúdo posteriormente utilizando o SDK.

    **Solução** – isto é um problema conhecido. Para resolver o problema, transmita sempre uma matriz de *bytes \[\]* com o mesmo valor de comprimento que o parâmetro de comprimento ou utilize o método [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write(byte\[\] array).

**iOS e OS X**

-   Existem dois dialetos de português que os nossos SDKs para iOS e OS X suportam. Infelizmente, devido a um erro, estamos atualmente não suportam a primeira localização completamente. Devido a este erro, o português não é totalmente suportado. A maior parte do texto é traduzido, mas não a IU.

    1. Português

    2. Português (Portugal)

**Apenas iOS**

-   O SDK RMS 4.x não mostra o indicador da atividade de rede.

    Este é um comportamento opcional conhecido do iOS, de acordo com as diretrizes Interface humana da Apple.

**Apenas OS X**

-   O SDK RMS 4.x não mostra o indicador da atividade de rede.

    Este é um comportamento opcional conhecido dos X, de acordo com as diretrizes Interface humana da Apple.

-   **Solução** – para criar uma aplicação de interface MDI (multiple document interface) através do nosso SDK para OS X, utilize as seguintes orientações.

    Os seguintes métodos não podem ser executados em simultâneo. Para monitorizar a conclusão da execução, utilize a abordagem de bloco de conclusão, conforme indicado.

    - [MSProtectedData.protectedDataWithProtectedFile](https://msdn.microsoft.com/library/dn758351.aspx)
    - [MSCustomProtectedData.customProtectedDataWithPolicy](https://msdn.microsoft.com/library/dn758315.aspx)



**Nota:** as aplicações MDI não são suportadas pela nossa API do iOS.

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

**Todas as plataformas**

**P**: não consigo ver uma IU de seleção de **Permissões Personalizadas** no fluxo de trabalho da proteção. Por que motivo?

**R** – isto é um problema conhecido e será resolvido mais tarde.

**P**: de que forma obtenho novos inquilinos organizacionais para experimentar o SDK e as aplicações de exemplo?

**A**: para pedir credenciais para as organizações de teste do Azure AD RMS, enviar correio eletrónico para < rmcstbeta@microsoft.com >.

**P**: não vejo qualquer debate sobre a hierarquia de testes aqui na documentação. Por que motivo?

**R**: não existe qualquer conceito de hierarquia de testes com os novos SDKs AD RMS. Irá sempre trabalhar com a hierarquia de produção.

**Q**: era necessário na versão 2.1 do SDK RMS, um manifesto gerado para cada aplicação que implementasse a proteção de informações. Este é ainda true para as versões 4.0 e posteriores do SDK?

**R**: não, os manifestos já não são necessários para as versões 3.0 e posteriores do SDK Rights Management.

**Android**

**P**: com que ambientes de desenvolvimento foi o SDK testado?

**R**: Eclipse Juno através da API do Google 15 e superior.

**P**: posso chamar um método de cancelamento cancel() a partir do thread da IU?
**R**: deve chamar cancel() a partir de um thread não IU, pois pode abortar uma ligação de rede.

**iOS**

**P**: que plataformas foram verificadas para o desenvolvimento de SDK?

**R**: Xcode 5.0 com iOS 7 e posterior.

**P**: chamei um método cancel() numa operação; no entanto, ainda obtive uma notificação sobre a conclusão da operação. Por que motivo?

**Um**: nem todas as operações podem ser canceladas, pelo que uma operação de cancelamento é executada da melhor forma possível.

**OS X**

**Q**: estrutura de aplicação de exemplo é adaptada para o Xcode 5, pode trabalhar com o Xcode 4.6?

**R**: o SDK OS X apenas funciona com o Xcode 4.6 e versões posteriores, bem como o OS X 10.8 e versões posteriores.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]