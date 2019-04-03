---
title: Novidades e notas de versão
description: Descreve as alterações importantes e de recursos desta e de versões anteriores.
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 12/11/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: d9fda9c7477c408e8003f48c85e6d35fec6a1884
ms.sourcegitcommit: 8da0aa8f9bb9f91375580a703682d23a81a441bf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58809816"
---
# <a name="whats-new-and-release-notes"></a>Novidades e Notas de versão

## <a name="whats-new"></a>Novidades

Este tópico descreve as funcionalidades nesta versão nova do v4.x RMS SDK e alterações importantes.

-   [Novo em Julho de 2017](#new-for-july-2017)
-   [Atualização de Outubro de 2016](#october-2016-update)
-   [Atualização de Junho de 2016](#june-2016-update)
-   [Atualização de Dezembro de 2015](#december-2015-update)
-   [Atualização de Julho de 2015 – adiciona suporte para Linux / desenvolvimento em C++](#july-2015-update---adds-support-for-linux--c-development)
-   [Talvez a atualização de 2015 – adiciona o controlo de registo](#may-2015-update---adds-logging-control)
-   [Atualização de Fevereiro de 2015 - suporte técnico da aplicação adiciona o Windows Store](#february-2015-update---adds-windows-store-application-support)
-   [Atualização de Janeiro de 2015 – adiciona o suporte da plataforma WinPhone](#january-2015-update---adds-winphone-platform-support)
-   [Atualização de Outubro de 2014 – atualizar para o SDK do Microsoft RMS 4.1](#october-2014-update---upgrade-to-microsoft-rms-sdk-41)
-   [Notas de versão](#release-notes)
-   [Perguntas mais frequentes](#frequently-asked-questions)

### <a name="new-for-july-2017"></a>Novo em Julho de 2017

A atualização para a nossa versão de Julho incluído deixa de aumentar a revisão do SDK, 4.2.5 agora.

- Android SDK: Agora a sua aplicação pode **definir o registo ao nível no momento** com o SDK do Android. Para obter mais informações, consulte [como: Ativar o registo de desempenho e de erro](https://docs.microsoft.com/information-protection/develop/enabling-logging)
- O SDK do iOS não suporta o nível de registo. 
- O SDK agora retorna um erro para um token de acesso NULL.

### <a name="october-2016-update"></a>Atualização de Outubro de 2016

- Implemente algumas correções de erros de back-end.
- Ative bitcode para a Apple iOS/OSX SDK.

### <a name="june-2016-update"></a>Atualização de Junho de 2016

- **Suporte para autenticação moderna** -traz baseada no Active Directory Authentication Library ADAL início de sessão para o RMS, as aplicações. Ele permite o início de sessão funcionalidades, como o multi-factor Authentication (MFA), fornecedores de identidade de terceiros baseadas em SAML com aplicações de cliente do RMS, cartão inteligente e a autenticação baseada em certificado e remove a necessidade de RMS as aplicações para utilizar o básico protocolo de autenticação.
- **Suporte ao Controlo de Documentos** - os programadores agora podem ativar o controlo de documentos ao proteger um documento nas suas aplicações
- Melhoramentos de desempenho
- Correções de erros

### <a name="december-2015-update"></a>Atualização de dezembro de 2015

Com esta versão, o SDK RMS para dispositivos está agora na versão 4.2 e adiciona:

-   O controlo de documentos e o RMS apenas online para sistemas operativos Android e iOS/OS X.

    Para obter detalhes e instruções de utilização no iOS/OS X, consulte a [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx) classe, que fornece informações de controlo e o método de registo de controlo no adicional de documentos [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx). Existem adições semelhantes para o Android em [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx) e [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx).

    Para obter uma descrição detalhada da funcionalidade de controlo de documentos, consulte [como: Utilizar o controlo de documentos](how-to-use-document-tracking.md).

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

    Para obter mais informações, consulte [como: Ativar o registo de desempenho e de erro](enabling-logging.md)

    Suporte de limpeza da cache adicionado.

    Para mais informações, consulte [MSProtection:resetStateWithCompletionBlock](https://msdn.microsoft.com/library/mt210991.aspx).

### <a name="february-2015-update---adds-windows-store-application-support"></a>Atualização de fevereiro de 2015 – adiciona o suporte para aplicações da Loja Windows

Esta versão adiciona suporte para aplicativos da Windows Store e fornece paridade funcional com o Windows Phone, Android e versão do iOS/OS X do SDK RMS 4.1.

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
-   **Consumo offline** -os utilizadores finais podem aceder a dados protegidos por RMS offline.
-   **Autorização Separada** – os programadores podem utilizar a sua própria biblioteca de autenticação para o Azure RMS e AD RMS (ou utilizar a [Azure AD Authentication Library (ADAL)](https://MSDN.Microsoft.Com/library/jj573266.aspx) recomendada).
-   **IU Separada** – os programadores podem criar a sua interface de utilizador para proteger e consumir documentos protegidos por RMS.
-   **Reprojetados API** -os desenvolvedores agora podem ter um simples e transparente de encriptação e desencriptação API, que fornece a experiência de utilizador e comportamentos de RMS consistentes, com esforço mínimo.

**Comum a todas as plataformas**

-   As APIs do SDK RMS 4.x não são *seguras para os threads*.

**Android**

-   Quando utilizar uma aplicação de exemplo num dispositivo Amazon® Kindle para ver anexos .ptxt, tem primeiro de transferir o ficheiro antes de o visualizar.

    **Solução** -um problema conhecido que será resolvido mais tarde.

-   Uma aplicação que utilize o SDK pode falhar se forem permitidas várias instâncias.

    **Solução** – certifique-se de que a aplicação não permite chamadas de várias instâncias para a API do Android.

-   Quando utilizo o [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx). Write (byte\[ \] array, int offset, int comprimento) método com um comprimento diferente da *length* valor, não sou capaz de consuma o conteúdo posteriormente utilizando o SDK.

    **Solução** – isto é um problema conhecido. Para resolver o problema, transmita sempre uma matriz de *bytes \[\]* com o mesmo valor de comprimento que o parâmetro de comprimento ou utilize o método [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx).write(byte\[\] array).

**iOS e OS X**

-   Existem dois dialetos de português que os nossos SDKs para iOS e OS X suportam. Infelizmente, devido a um erro, nós não suportam atualmente a primeira localização completamente. Devido a este erro, o português não é totalmente suportado. A maior parte do texto é traduzido, mas não a IU.

    1. Português

    2. Português (Portugal)

**Apenas iOS**

-   O SDK RMS 4.x não mostra o indicador da atividade de rede.

    Este é um comportamento opcional conhecido para iOS, de acordo com as diretrizes de Interface humana da Apple.

**Apenas OS X**

-   O SDK RMS 4.x não mostra o indicador da atividade de rede.

    Este é um comportamento opcional conhecido para OS X, de acordo com as diretrizes de Interface humana da Apple.

-   **Solução** – para criar uma aplicação de interface MDI (multiple document interface) através do nosso SDK para OS X, utilize as seguintes orientações.

    Os seguintes métodos não podem ser executados em simultâneo. Para monitorizar a conclusão da execução, use a abordagem de bloco de conclusão, conforme indicado.

    - [MSProtectedData.protectedDataWithProtectedFile](https://msdn.microsoft.com/library/dn758351.aspx)
    - [MSCustomProtectedData.customProtectedDataWithPolicy](https://msdn.microsoft.com/library/dn758315.aspx)



**Tenha em atenção**  as aplicações MDI não são suportadas pela nossa API do iOS.

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

**Todas as plataformas**

**Q**: Não vejo uma **permissões personalizadas** seleção da interface do Usuário do fluxo de trabalho de proteção. Por que motivo?

**A**: Este é um problema conhecido e será resolvido mais tarde.

**Q**: Como obtenho novos inquilinos organizacionais para experimentar o SDK e aplicações de exemplo?

**A**: Para pedir credenciais para organizações de teste do Azure AD RMS, envie um e-mail para <rmcstbeta@microsoft.com>.

**Q**: Não vejo qualquer discussão aqui da hierarquia de teste na documentação. Por que motivo?

**A**: Não há nenhum conceito de hierarquia de teste com os novos SDKs AD RMS. Irá sempre trabalhar com a hierarquia de produção.

**Q**: Na versão do RMS SDK 2.1, um manifesto gerado foi necessário para cada aplicação que implementasse a proteção de informações. Isso é ainda verdade para as versões 4.0 e posteriores do SDK?

**A**: Não, os manifestos já não são necessários para as versões 3.0 e versões posteriores do SDK do Rights Management.

**Android**

**Q**: Que ambientes de desenvolvimento tem o SDK testado?

**A**: Eclipse Juno através da API do Google 15 e superior.

**Q**: Posso chamar Cancel () um método de cancelamento do thread da interface do Usuário?
**A**: Deve chamar Cancel () a partir de um thread não IU, pois pode abortar uma ligação de rede.

**iOS**

**Q**: Que plataformas foram verificadas para o desenvolvimento de SDK?

**A**: Xcode 5.0 com iOS 7 e posterior.

**Q**: Chamei um método Cancel () numa operação, no entanto, eu ainda Obtive uma notificação concluir a operação. Por que motivo?

**A**: Nem todas as operações podem ser canceladas, pelo que uma operação de cancelamento é executada da melhor forma possível.

**OS X**

**Q**: Estrutura de aplicação de exemplo é adaptada para o Xcode 5, posso trabalhar com o Xcode 4.6?

**R**: o SDK OS X apenas funciona com o Xcode 4.6 e versões posteriores, bem como o OS X 10.8 e versões posteriores.
