---
title: Notas de versão
description: Atualizações do SDK, revisão e outras informações do desenvolvedor.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 10/18/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: CE379738-4E1D-42AD-83F4-F89B70456EBB
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 6e962a2e9727048a60e74e811e964e6a0a9bc82d
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57332162"
---
# <a name="release-notes"></a>Notas de versão

Este artigo contém informações importantes sobre isto e versões anteriores do SDK RMS 2.1.

## <a name="october-2017---update"></a>Atualização de Outubro de 2017-

- Adição de duas novas APIs para o ambiente inintialization e desinicialização. Para obter informações, consulte [IpcInitializeEnvironment](https://msdn.microsoft.com/library/hh535289.aspx) e [IpcUninitializeEnvironment](https://msdn.microsoft.com/library/hh535289.aspx).
- Tipos de ficheiro do Visio são agora suportados. Para obter mais informações, veja [Configuração da API de Ficheiros](file-api-configuration.md).

## <a name="february-2016---sdk-documentation-update"></a>Atualização da documentação do SDK de fevereiro de 2016

>[!Note]
> As atualizações da documentação da funcionalidade nesta secção aplicam-se à transferência do SDK com a data de 11/12/2015.

- **Fluxo de autenticação melhorado** -através da autenticação baseada em tokens do OAuth2 através do [do Azure Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/). Para obter mais informações sobre este processo e as extensões da API para o mesmo, veja [Autenticação ADAL para a aplicação com permissão para RMS](how-to-use-adal-authentication.md).

- **Atualizar para a ADAL** – ao atualizar a sua aplicação para utilizar a autenticação ADAL em vez do Assistente de Início de Sessão Online da Microsoft, o utilizador e os seus clientes poderão:

  - Utilizar a autenticação multifator
  - Instalar o cliente RMS 2.1 sem necessidade de privilégios administrativos no computador
  - Certificar a aplicação para o Windows 10

- **O suporte para o Assistente de Início de Sessão Online da Microsoft (SIA) com o SDK RMS está a ser removido.** Vamos continuar a suportar a utilização do SIA durante seis meses após o qual irá parar de suporte.


## <a name="december-2015-update"></a>Atualização de dezembro de 2015

- As melhorias de desempenho têm sido implementadas em várias áreas, incluindo:
    - A publicação a partir do servidor de licenciamento principal quando utilizar servidores só de licenciamento.
    - O SDK RMS 2.1 falha mais rapidamente quando não existe qualquer ligação de rede.

- Muitas atualizações para melhorar a experiência de resolução de problemas e de mensagens de erro.
- Note também que a lista das [Plataformas suportadas](supported-platforms.md) também está atualizada.
- A necessidade de ambiente de pré-produção e a utilização de um manifesto de aplicativo foi removida do SDK RMS 2.1. Estas secções deste conjunto de documentação para programadores foram removidas e a documentação geral simplificada e reorganizada.

## <a name="may-2015-update"></a>Atualização de maio de 2015

-   **Serviço de aplicações e baseado na nuvem RMS** - [IPC\_CREDENTIAL\_SYMMETRIC\_chave](https://msdn.microsoft.com/library/dn133062.aspx) precisa de três partes de informações; a chave simétrica,  **AppPrincipalId**, e **TenantBposId**. O artigo para que isso foi atualizado para fornecer orientações sobre o processamento destas informações. Para esta atualização, veja a versão revista de [Permitir que a aplicação do serviço funcione com o RMS baseado na cloud](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="april-2015-update"></a>Atualização de abril de 2015

-   O **controlo de documentos** é agora possível através de um conjunto de APIs novas. Para obter mais informações, veja [Controlar Conteúdo](tracking-content.md).
-   **Tipo de encriptação** – agora suportamos o controlo de nível da API para a seleção do pacote de encriptação. Para obter mais informações, veja [Trabalhar com a encriptação](working-with-encryption.md).

    **Tenha em atenção**  já não irá expor o **IPC\_LI\_PRETERIDO\_encriptação\_algoritmos** sinalizador na nossa API. Isto significa que as aplicações futuras vão deixar de compilar se fizerem referência a este sinalizador, mas as aplicações já criadas vão continuar a funcionar, uma vez que respeitamos o sinalizador em privado no código da API. Para aproveitar ainda as vantagens do sinalizador de algoritmos de encriptação preterido antigo, basta alterar um sinalizador. Para obter mais informações, veja [Trabalhar com a encriptação](working-with-encryption.md).

-   As **Aplicações de Modo de Servidor** que utilizarem um [Valor de modo de API](https://msdn.microsoft.com/library/hh535236.aspx) de **IPC\_API\_MODE\_SERVER** já não necessitam de um manifesto da aplicação. Pode testar a aplicação relativamente a um servidor RMS de produção e não é necessário obter uma licença de produção quando mudar para um ambiente de produção. Para obter mais informações sobre as aplicações do modo de servidor, veja [Tipos de aplicação](application-types.md).
-   O **registo** é agora implementado através dos métodos Rastreio de Eventos e ficheiros do Windows.
-   Se estiver a utilizar um **computador Windows 7 SP1 ou Windows Server 2008 R2**, veja a nota em “Notas importantes do programador” a seguir.

## <a name="january-2015-update"></a>Atualização de janeiro de 2015

-   **Aumento do tamanho do ficheiro protegido (pfile)** – agora suporta tamanhos de pfile maiores do que um gigabyte (1 GB). Para obter mais informações sobre pfiles, veja [Formatos de Ficheiro Suportados](supported-file-formats.md).
-   **Registo melhorado para um melhor diagnóstico** –os níveis de registo apresentarão um **ERRO** ou **AVISO** nas mensagens que devem ser revistas. Todas as outras mensagens, incluindo as exceções, que ainda são apresentadas, serão registadas como **informações**.

    Escolhemos esta abordagem para nenhum detalhe seja perdido. Agora, apenas as mensagens importantes são apresentadas com o nível de AVISO.

-   **Adquirir modelos da Empresa** – correções substanciais no código de aquisição de modelos, com base em relatórios de cliente e feedback.
-   Consistência de localização melhorada

## <a name="october-2014-update"></a>Atualização de outubro de 2014

-   Foram atualizados os comportamentos predefinidos do componente da API de Ficheiros do SDK. Para obter mais informações, veja [Configuração da API de Ficheiros](file-api-configuration.md).
-   Notificação por e-mail, uma nova funcionalidade, é descrita no artigo de notas do programador, [permitir notificação por e-mail](how-to-enable-email-notification.md).

## <a name="july-2014-update"></a>Atualização de julho de 2014

O componente da API de ficheiros do SDK foram expandido e oferece as seguintes funcionalidades:

-   Identifica o protetor a utilizar.
-   Fornece a proteção do RMS ao nível de granularidade de um ficheiro.

    Funções adicionadas a esta versão:

    **Tenha em atenção** - dados de suporte tipos e estruturas, não listadas aqui, foram adicionadas para as extensões de API de ficheiros. Todos os artigos que foram atualizados nesta versão estão marcados como **preliminares e estão sujeitas a alterações**.

    -   [IpcfOpenFileOnHandle](https://msdn.microsoft.com/library/dn771751.aspx)
    -   [IpcfOpenFileOnILockBytes](https://msdn.microsoft.com/library/dn771752.aspx)
    -   [IpcfGetFileProperty](https://msdn.microsoft.com/library/dn771749.aspx)
    -   [IpcfLogicalFileRangeToRawFileRange](https://msdn.microsoft.com/library/dn771750.aspx)
    -   [IpcfReadFile](https://msdn.microsoft.com/library/dn771753.aspx)
    -   [IpcfSetEndOfFile](https://msdn.microsoft.com/library/dn771754.aspx)
    -   [IpcfWriteFile](https://msdn.microsoft.com/library/dn771756.aspx)

## <a name="april-2014-update"></a>Atualização de abril de 2014

-   A **utilização da memória da API de Ficheiros**, especialmente para PFiles grandes, foi significativamente melhorada.
-   O **ID de conteúdo** agora é gravável através da propriedade **IPC\_LI\_CONTENT\_ID**. Para obter mais informações, veja [Tipos de propriedade de licença](https://msdn.microsoft.com/library/hh535287.aspx).
-   **Requisito de manifesto de produção** – quando o serviço/aplicação com suporte RMS está a ser executado no modo de servidor, deixará de ser necessário um manifesto. Para obter mais informações, veja [Tipos de aplicações](application-types.md).
-   **Atualizações da documentação**

    **Testar a melhor prática** – orientações adicionadas para a utilização do servidor no local antes de testar com o Azure RMS. Para obter mais informações, veja [Permitir que a aplicação do serviço funcione com o RMS baseado na cloud](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="important-developer-notes"></a>Notas importantes do programador

-   **Suporte nativo para todos os tipos de ficheiro**

    É possível adicionar suporte nativo para qualquer tipo de ficheiro (extensão) com esta versão do SDK do Rights Management Services 2.1. Por exemplo, para qualquer extensão &lt;ext&gt; (não Office e pdf), \*.p&lt;ext&gt; será utilizado se a configuração de administração para essa extensão for “NATIVO”.

    Para obter mais informações sobre tipos de ficheiro suportados, veja [Configuração da API de Ficheiros](file-api-configuration.md).

-   **Máquinas do Windows 7 SP1 e Windows Server 2008 R2 SP1** sem a atualização [KB2533623](https://support.microsoft.com/kb/2533623), pode ter o seguinte erro de proteger um ficheiro do office "o parâmetro está incorreto. Código de erro 0x80070057”. Se vir isto, instale a atualização e tente novamente. Se os problemas persistirem, contacte o alias de comentários do RMS SDK Beta <rmcstbeta@microsoft.com>.

    **Tenha em atenção**  no momento do lançamento de Abril de 2015, uma verificação foi adicionada para o processo de instalação para este KB.

     

-   **Integração da API de Ficheiros**

    O Active Directory Rights Management API dos serviços do arquivo, com a adição da API de ficheiros, fornece as seguintes vantagens e capacidades.

      - Pode proteger dados confidenciais de uma forma automática sem necessitar de saber os detalhes sobre a implementação da Gestão de Direitos de Informação (IRM) utilizada por vários formatos de ficheiro.

      - É possível proteger ficheiros do Microsoft Office, Portable Document Format (PDF) e outros tipos de ficheiros selecionados através da proteção nativa. Para obter uma lista completa dos tipos de ficheiro que podem ser protegidos com a proteção nativa, veja [Configuração da API de Ficheiros](file-api-configuration.md).

      - Todos os ficheiros, exceto ficheiros do sistema e ficheiros do Office, podem ser protegidos através do formato de Ficheiro Protegido (PFile) do RMS.

    A API de ficheiros é implementada por meio das seguintes quatro novas funções: [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx), [IpcfEncryptFile](https://msdn.microsoft.com/library/dn133059.aspx), [IpcfGetSerializedLicenseFromFile](https://msdn.microsoft.com/library/dn133060.aspx), and [IpcfIsFileEncrypted](https://msdn.microsoft.com/library/dn133061.aspx).

    A API de Ficheiro necessita que o Rights Management Service Client 2.1 seja instalado no computador cliente e que o computador tenha conectividade com um servidor RMS. Para obter mais informações sobre o servidor RMS, o cliente RMS e a respetiva funcionalidade, veja o conteúdo do TechNet relativo à [Documentação do RMS para Profissionais de TI](https://technet.microsoft.com/library/cc771234(v=ws.10).aspx).

-   **Problema**: Quando criar uma licença do zero, direitos de propriedade tem de ser concedidos explicitamente.

    **Solução**: A aplicação deve adicionar explicitamente **proprietário** direitos para o proprietário da licença ao criar uma licença do zero através de [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx). Para obter mais informações, veja [Adicionar direitos de proprietário explícitos](add-explicit-owner-rights.md).

-   **Problema**: Se uma aplicação chamar [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx) ou [IpcUnprotectWindow](https://msdn.microsoft.com/library/hh535272.aspx) duas vezes para a mesma janela utilizando o respetivo identificador, SDK RMS 2.1 devolve uma falha no **HRESULT**.

    **Solução**: Para obter instruções específicas sobre isto, consulte a secção observações em [IpcProtectWindow](https://msdn.microsoft.com/library/hh535268.aspx) e [IpcUnprotectWindow](https://msdn.microsoft.com/library/hh535272.aspx).

-   **Problema**: Ao criar para várias arquiteturas, tem de utilizar esta orientação.

    **Solução**: Se pretender utilizar o Ipcsecproc\*ISV. dll para uma arquitetura diferente (por exemplo, tiver instalado o SDK de 64 bits num computador de 64 bits, mas agora pretende implementar num computador de 32 bits que requer o Ipcsecproc\*ISV. dll), tem de instalar o SDK de 32 bits num computador diferente e copiar o Ipcsecproc\*ficheiros de ISV. dll para lá do "% PROGRAMFILES %\\Microsoft Information Protection e o controle" pasta (a localização predefinida ou onde quer que tenha optado por instalar o SDK).

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

**Q**: Como funciona o comportamento de idioma predefinido com as funções que assumem um parâmetro LCID?

**A**: Utilize 0 para a região predefinida. Neste caso, o cliente de AD RMS 2.1 procura nomes e descrições na seguinte sequência e obtém o primeiro um disponível:

    1 - User preferred LCID.
    2 - System locale LCID.
    3 - The first available language specified in the Rights Management Server (RMS) template.

Se não for possível obter um nome e uma descrição, é devolvido um erro. Apenas pode existir um nome e descrição para um LCID específico.
