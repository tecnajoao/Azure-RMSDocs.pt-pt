---
title: Instalação do SDK de proteção de informações da Microsoft (MIP) e configuração
description: Fornece os pré-requisitos de instalação e configuração, para poder utilizar aplicações criadas com o SDK do Microsoft Information Protection.
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 2790c64095a6fca4a33f70aeada68fa0c6668020
ms.sourcegitcommit: bdce88088f7a575938db3848dce33e7ae24fdc26
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52386734"
---
# <a name="microsoft-information-protection-mip-sdk-setup-and-configuration"></a>Instalação do SDK de proteção de informações da Microsoft (MIP) e configuração 

O guia de introdução e tutoriais são centradas em torno da criação de aplicativos que usam as APIs e bibliotecas MIP SDK. Este artigo mostra-lhe como configurar e configurar a sua subscrição do Office 365 e a estação de trabalho do cliente, em preparação para utilizar o SDK.

O SDK de MIP é suportado nas seguintes plataformas:  

[!INCLUDE [MIP SDK platform support](../include/mip-sdk-platform-support.md)]

## <a name="prerequisites"></a>Pré-requisitos

Certifique-se de que consulte os tópicos seguintes antes de começar:

- [O que é o Centro de conformidade e de segurança do Office 365?](https://docs.microsoft.com/office365/securitycompliance/security-and-compliance)
- [O que é o Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection)
- [Como funciona a proteção no Azure Information Protection?](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

> [!IMPORTANT]
> **Para respeitar a privacidade dos utilizadores, tem de pedir ao utilizador para dar consentimento antes de ativar o registo automático.** O exemplo seguinte é uma mensagem padrão, a Microsoft utiliza para notificações de registos:
>
> *Ao ativar os Registos de Desempenho e de Erros, está a concordar em enviar Dados de Desempenho e de Erros para a Microsoft. A Microsoft irá recolher dados de desempenho e de erros através da Internet ("Dados"). A Microsoft utiliza estes Dados para fornecer e melhorar a qualidade, segurança e integridade dos produtos e serviços da Microsoft. Por exemplo, analisamos o desempenho e a fiabilidade, como as funcionalidades que utiliza, o tempo de resposta das funcionalidades, o desempenho do dispositivo, as interações de interface de utilizador e os problemas que possa ter com o produto. Os Dados também incluirão informações acerca da configuração do seu software, como o software que está a utilizar atualmente e o endereço IP.*

## <a name="sign-up-for-an-office-365-subscription"></a>Inscreva-se uma subscrição do Office 365

Muitas das amostras do SDK exigem acesso a uma subscrição do Office 365. Se ainda não o fez, certifique-se de que inscreva-se um dos seguintes tipos de subscrição:

| Nome | Inscreva-se |
|------|---------|
| Office 365 Enterprise E3 avaliação (avaliação gratuita de 30 dias) | https://go.microsoft.com/fwlink/p/?LinkID=403802 |
| Office 365 Enterprise E3 ou E5 | https://products.office.com/business/office-365-enterprise-e3-business-software |
| Enterprise Mobility e Security E3 ou E5 | https://www.microsoft.com/cloud-platform/enterprise-mobility-security |
| Azure Information Protection Premium P1 ou P2 | https://azure.microsoft.com/pricing/details/information-protection/ |
| O Microsoft 365 E3, E5 ou em F1 | https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans | 

## <a name="configure-sensitivity-labels"></a>Configurar etiquetas de sensibilidade

Se utilizar atualmente o Azure Information Protection, tem de migrar as etiquetas para segurança do Office 365 e do Centro de conformidade. Para obter mais informações sobre o processo, consulte [como migrar as etiquetas do Azure Information Protection para o Centro de conformidade e segurança do Office 365](/azure/information-protection/configure-policy-migrate-labels). 

## <a name="configure-your-client-workstation"></a>Configurar a sua estação de trabalho do cliente

Em seguida, conclua os seguintes passos para garantir que seu computador cliente foi definido e configurado corretamente.

1. Se estiver a utilizar uma estação de trabalho do Windows 10:

   - Utilizar o Windows Update, atualize o seu computador para o Windows 10 Fall Creators Update (versão 1709) ou posterior. Para verificar a sua versão atual:
     - Clique no ícone do Windows no canto inferior esquerdo.
     - Escreva "Sobre seu PC" e prima a tecla "Enter".
     - Desloque para baixo até **especificações de Windows** e procure **versão**.

   - Certifique-se de que o "Modo de programador" está ativado na sua estação de trabalho:
     - Clique no ícone do Windows no canto inferior esquerdo.
     - Escreva "Utilizar funcionalidades de programador" e prima a tecla "Enter", quando vir o **utilizar funcionalidades de programador** show de item.
     - Sobre o **definições** caixa de diálogo, **para desenvolvedores** separador, em "Utilizar funcionalidades de programador", selecione o **modo de programador** opção.
     - Fechar o **definições** caixa de diálogo.

2. Instale [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/), com as seguintes cargas de trabalho e os componentes opcionais:
   - **Desenvolvimento de plataforma Windows universal** carga de trabalho do Windows, bem como os seguintes componentes opcionais:
     - **Ferramentas da plataforma Windows Universal do C++**
     - **SDK do Windows 10 SDK 10.0.16299.0** ou posteriormente, se não incluídas por predefinição
   - **Desenvolvimento com C++** carga de trabalho do Windows, bem como os seguintes componentes opcionais:
     - **SDK do Windows 10 SDK 10.0.16299.0** ou posteriormente, se não incluídas por predefinição 

     [![Instalação do Visual Studio](media/setup-mip-client/visual-studio-install.png)](media/setup-mip-client/visual-studio-install.png#lightbox)

3. Instalar o [módulo do PowerShell ADAL.PS](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2). 

   - Porque os direitos de administrador são necessários para instalar os módulos, primeiro precisa:

     - Inicie sessão no seu computador com uma conta que tenha direitos de administrador.
     - Execute a sessão do Windows PowerShell com direitos elevados (executar como administrador).

   - Em seguida, execute o `install-module -name adal.ps` cmdlet:

     ```powershell
     PS C:\WINDOWS\system32> install-module -name adal.ps

     Untrusted repository
     You are installing the modules from an untrusted repository. If you trust this repository, change its
     InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
     'PSGallery'?
     [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): A

     PS C:\WINDOWS\system32>
     ```

4. Baixe amostras SDK a partir do GitHub 

   - Se ainda não tiver uma, crie primeiro um [perfil do GitHub](https://github.com/join).
   - Em seguida, instale a versão mais recente do [ferramentas de cliente do Git da Software Freedom Conservancy (Git Bash)](https://git-scm.com/download/)
   - Com o Git Bash, transfira o sample(s) de interesse:
     - Utilize a seguinte consulta para ver os repositórios: https://github.com/Azure-Samples?utf8=%E2%9C%93&q=MipSdk. 
     - Com o Git Bash, utilize `git clone https://github.com/azure-samples/<repo-name>` para transferir cada repositório de exemplo.

5. Transferir os ficheiros binários e de cabeçalho do SDK

   Um ficheiro. zip que contém os binários do SDK e cabeçalhos para todas as plataformas podem ser encontradas em https://aka.ms/mipsdkbinaries. O zip contém vários arquivos. zip adicionais, um para cada plataforma e API. Os ficheiros são nomeados da seguinte forma, onde \<API\> = `file`, `protection`, ou `upe`, e \<SO\> = a plataforma: `mip_sdk_<API>_<OS>_1.0.0.0.zip (or .tar.gz)`.

   Por exemplo, seria o. zip para binários de API de proteção e os cabeçalhos no Debian: `mip_sdk_protection_debian9_1.0.0.0.tar.gz`.

   Cada. zip ou tarball contém outros três diretórios:

   - **Contentores:** os binários compilados para cada arquitetura de plataforma, quando aplicável.
   - **Incluem:** os arquivos de cabeçalho do SDK do Microsoft Information Protection
   - **Exemplos:** da origem de código para aplicativos de exemplo

   Se estiver fazendo o desenvolvimento do Visual Studio, o SDK pode ser instalado também através da consola do Gestor de pacotes NuGet:

    ```console
    Install-Package Microsoft.InformationProtection.File
    Install-Package Microsoft.InformationProtection.Policy
    Install-Package Microsoft.InformationProtection.Protection
    ```  
    
6. Adicione os caminhos dos binários do SDK (bibliotecas de vínculo dinâmico (. dll)), a variável de ambiente PATH. A variável de caminho permite que as DLLs dependentes ser encontrados em tempo de execução, por aplicações cliente:
   - Clique no ícone do Windows no canto inferior esquerdo.
   - Escreva "Caminho" e prima a tecla "Enter", quando vir o **editar as variáveis de ambiente de sistema** show de item.
   - Sobre o **propriedades do sistema** caixa de diálogo, clique em **variáveis de ambiente**.
   - No **variáveis de ambiente** caixa de diálogo, clique no **caminho** variável linha sob **variáveis de utilizador para \<utilizador\>**, em seguida, clique em **Editar...** .
   - Sobre o **variável de ambiente de edição** caixa de diálogo, clique em **New**, que cria uma nova linha editável. Usando o caminho completo para cada um a `file\bins\debug\amd64`, `protection\bins\debug\amd64`, e `upe\bins\debug\amd64` subdiretórios, adicionar uma nova linha para cada um. Os diretórios SDK são armazenados num `<API>\bins\<target>\<platform>` formato, em que:
     - \<API\> = `file`, `protection`, `upe`
     - \<destino\> = `debug`, `release`
     - \<plataforma\>  =  `amd64` (também conhecido como: x64), `x86`, etc.
   
   - Quando a atualização foi concluída a **caminho** variável, clique **OK**. Em seguida, clique em **OK** quando devolvido para o **variáveis de ambiente** caixa de diálogo.

## <a name="register-a-client-application-with-azure-active-directory"></a>Registar uma aplicação de cliente com o Azure Active Directory

Como parte da subscrição do Office 365, processo, um Azure associado de aprovisionamento é criado o inquilino do AD. O inquilino do Azure AD fornece gestão de identidades e acessos para o Office 365 *contas de utilizador* e *contas de aplicação*. Aplicativos que exigem acesso a APIs seguros (como APIs de MIP), requerem uma conta de aplicativos.

Para autenticação e autorização em tempo de execução, as contas são representadas por um *entidade de segurança*, que é derivado de informações de identidade da conta. Entidades de segurança que representam uma conta de aplicativos são conhecidas como um [ *principal de serviço*](/azure/active-directory/develop/developer-glossary#service-principal-object). 

Para registar uma conta de aplicação no Azure AD para utilização com os exemplos de inícios rápidos e MIP SDK:

  > [!IMPORTANT] 
  > Para aceder à gestão de inquilino do Azure AD para a criação de conta, terá de iniciar sessão no portal do Azure com uma conta de utilizador que seja um membro a [função de "Proprietário" na subscrição](/azure/billing/billing-add-change-azure-subscription-administrator). Dependendo da configuração do seu inquilino, também poderá ter de ser um membro da função de diretório "Palavra Global" para [registar uma aplicação](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps).
  > Recomendamos que teste com uma conta restrita. Certifique-se de que a conta tem apenas direitos de acesso os pontos de extremidade de SCC necessários. Palavras-passe de texto simples transmitidas por meio da linha de comandos podem ser recolhidas por sistemas de Registro em log.

1. Siga os passos em [integrar aplicações com o Azure Active Directory, adicione uma seção do aplicativo](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#adding-an-application). Para fins de teste, utilize os seguintes valores para as propriedades de determinada à medida que revê os passos do guia: 
    - **Tipo de aplicação** -selecione "Nativo", como as aplicações demonstradas pelo SDK aplicativos de console instalados nativamente. Aplicativos nativos são considerados "public" clientes por OAuth2, pois estão não é possível para armazenamento/utilizar credenciais de aplicação de forma segura. Ao contrário de um aplicativo "Confidencial" baseado em servidor, como um aplicativo web, que está registado com suas próprias credenciais. 
    - **URI de redirecionamento** - uma vez que o SDK utiliza aplicações de cliente de console simples, utilize um URI no formato `<app-name>://authorize`.

2. Quando terminar, será encaminhado de volta para o **aplicação registada** page de seu novo registo de aplicação. Copie e guarde o GUID no **ID da aplicação** campo, pois irá precisar dele para os inícios rápidos. 

3. Em seguida, clique em **definições** para adicionar as APIs e as permissões para o qual o cliente precisará de acesso. Sobre o **definições** página, clique em **permissões obrigatórias**.

4. Agora adicionará as APIs de MIP e as permissões que o aplicativo exigirá em tempo de execução:
   - Sobre o **permissões obrigatórias** página, clique em **Add**. 
   - Sobre o **adicionar acesso à API** página, clique em **selecionar uma API**.
   - Sobre o **selecionar uma API** página, clique no "**Microsoft Rights Management Services**" API e clique em **selecionar**.
   - Na **ativar o acesso ao** para permissões de disponíveis da API, clique em "**criar e aceder a conteúdo protegido para utilizadores**" e clique em **selecione**, em seguida,  **Feito**.

5. Repita o passo 4 de #, mas desta vez, quando vai para o **selecionar uma API** página, será necessário para a API de pesquisa.
   - Sobre o **selecionar uma API** página, no tipo de caixa de pesquisa "**serviço de sincronização do Microsoft Information Protection**", em seguida, clique a API e clique em **selecionar**.
   - No **ativar o acesso ao** para permissões de disponíveis da API, clique em "**unificadas todas as políticas de leitura um utilizador tem acesso a**" e clique em **selecione**, em seguida,  **Concluído**

6. Quando estiver novamente o **permissões obrigatórias** página, clique em **conceder permissões**, em seguida, **Sim**. Este passo dá consentimento prévia para a aplicação com esse registro, para aceder às APIs do sob as permissões especificadas. Se tiver iniciado sessão como administrador global, o consentimento é registrado para todos os utilizadores no inquilino que executam o aplicativo; caso contrário, ele só se aplica a sua conta de utilizador. 

Quando terminar, registo de aplicação e permissões de API devem ter um aspeto semelhantes ao seguinte exemplo:

   [![Registo de aplicação do Azure AD](media/setup-mip-client/aad-app-registration.png)](media/setup-mip-client/aad-app-registration.png#lightbox)


Para obter mais informações sobre como adicionar APIs e as permissões para um registo, consulte [atualização de aplicativos, configurar uma aplicação de cliente para acessar a seção APIs web](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#updating-an-application). Aqui encontrará informações sobre como adicionar as APIs e as permissões necessárias por uma aplicação cliente.  

## <a name="request-an-information-protection-integration-agreement-ipia"></a>Pedir um Contrato de Integração do Information Protection (IPIA)

Para poder disponibilizar uma aplicação desenvolvida com MIP, tem de aplicar para e celebrar um contrato formal com a Microsoft.

1. Obtenha o seu IPIA ao enviar um e-mail para [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Requesting%20IPIA%20for%20<company-name>) com as seguintes informações:

   **Assunto:** pedido de IPIA para *Nome da Empresa*

   No corpo do e-mail, inclua:
   - Nome da aplicação e do produto
   - Nome próprio e apelido do autor do pedido
   - Endereço de e-mail do autor do pedido

2. Após a receção do seu pedido de IPIA, ser-lhe-á enviado um formulário (como um documento do Word). Analise os termos e condições do IPIA e devolva o formulário para o e-mail [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=IPIA%20Response%20for%20<company-name>) com as seguintes informações:

   - Denominação legal da Empresa
   - Estado/Distrito (E.U.A./Canadá) ou País de Registo
   - URL da empresa
   - Endereço de e-mail do contacto
   - Endereços adicionais da empresa (opcional)
   - Nome da Aplicação da Empresa
   - Breve Descrição da Aplicação
   - *ID do Inquilino do Azure*
   - *ID da Aplicação*
   - Contactos, e-mail e telefone da empresa para Correspondência em Situações Críticas

3. Quando recebermos o seu formulário, ser-lhe-á enviada a ligação final do IPIA para assinar digitalmente. Depois de assinar, o contrato será assinado pelo devido representante da Microsoft, dando-se por concluída a celebração do contrato.

### <a name="already-have-a-signed-ipia"></a>Já tem um IPIA assinado?

Se já tiver um IPIA assinado e quiser adicionar um novo *ID da Aplicação* a uma aplicação que irá disponibilizar, envie um e-mail para [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Updating%20IPIA%20for%20<company-name>) e forneça-nos as seguintes informações:

- Nome da Aplicação da Empresa
- Breve Descrição da Aplicação
- ID do Inquilino do Azure (mesmo que seja igual ao anterior)
- ID da Aplicação
- Contactos, e-mail e telefone da empresa para Correspondência em Situações Críticas

Depois de nos enviar o e-mail, aguarde até 72 horas para receber um aviso de receção.

## <a name="next-steps"></a>Passos Seguintes

- Antes de iniciar a secção de guias de introdução, não deixe de ler sobre [observadores no SDK do MIP](concept-async-observers.md), como o SDK de MIP foi concebido para ser quase que totalmente assíncrono.
- Se estiver pronto para obter experiência prática com o SDK, começar com [início rápido: inicialização de aplicações de cliente (C++)](quick-app-initialization-cpp.md).


