---
title: Registar e analisar a utilização do serviço Azure RMS – AIP
description: Informações e instruções sobre como utilizar os registos de utilização com o Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9e17e13eeb86b161444e222cde658905177dd285
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259920"
---
# <a name="logging-and-analyzing-usage-of-the-azure-rights-management-service"></a>Registar e analisar a utilização do serviço Azure Rights Management

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize estas informações para ajudar a compreender como pode utilizar o registo de utilização do serviço do Azure Rights Management do Azure Information Protection. Este serviço fornece a proteção de dados de documentos da sua organização e mensagens de correio eletrónico e pode registar cada solicitação a ele. Estes pedidos incluem quando os utilizadores protegerem documentos e e-mail e a consumam este conteúdo, ações efetuadas pelos seus administradores para este serviço e ações realizadas por operadores da Microsoft para suportar a implementação do Azure Information Protection. 

Em seguida, pode utilizar estes registos do serviço Azure Rights Management para suportar os seguintes cenários empresariais:

-   **Analisar informações empresariais**

    Os registos gerados pelo serviço Azure Rights Management podem ser importados para um repositório à sua escolha (tal como uma base de dados, um sistema OLAP (Online Analytical Processing) ou um sistema MapReduce) para analisar as informações e criar relatórios. Por exemplo, poderia identificar quem está a aceder aos seus dados protegidos. Pode determinar o tipo de dados protegidos a que as pessoas estão a aceder, bem como os dispositivos e o local a partir dos quais estão a aceder. Pode descobrir se as pessoas conseguem ler conteúdos protegidos com êxito. Também pode identificar as pessoas que leram um documento importante que estava protegido.

-   **Monitorizar abusos**

    Informações de registo de Rights Management do Azure são-lhe disponibilizadas quase em tempo real, para que possa monitorizar continuamente a utilização da sua empresa do serviço Rights Management. 99,9% dos registos estão disponíveis dentro de 15 minutos após uma ação iniciada para o serviço.

    Por exemplo, poderá querer ser alertado caso ocorra um aumento súbito de pessoas que estão a ler dados protegidos fora do horário de trabalho normal, o que pode significar que um utilizador mal-intencionado está a recolher informações para vender à concorrência. Em alternativa, poderá querer ser alertado se o mesmo utilizador parecer aceder a dados a partir de dois endereços IP diferentes num curto período de tempo, o que pode significar que uma conta de utilizador foi comprometida.

-   **Efetuar análises forenses**

    Se ocorrer uma fuga de informações, é provável que lhe seja pedido para indicar quem acedeu recentemente a documentos específicos e a que tipo de informações uma pessoa suspeita acedeu recentemente. Pode responder a esses tipos de perguntas quando utiliza este registo porque as pessoas que utilizam conteúdos protegidos têm sempre de obter uma licença de Rights Management para abrir documentos e imagens protegidos pelo serviço Azure Rights Management, mesmo que esses arquivos são movidos por e-mail ou copiados para unidades USB ou outros dispositivos de armazenamento. Isso significa que pode utilizar estes registos como fonte definitiva de informações para análise forense quando proteger os seus dados com o serviço Azure Rights Management.

Além deste registo de utilização, também tem as seguintes opções de registo:

|Opção de registo|Descrição|
|----------------|---------------|
|Registo de administrador|Regista tarefas administrativas para o serviço Azure Rights Management. Por exemplo, se o serviço estiver desativado, quando a funcionalidade de Superutilizador é ativada e quando os utilizadores estiverem permissões de administrador delegado para o serviço. <br /><br />Para obter mais informações, consulte o cmdlet do PowerShell [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog).|
|Controlo de documentos|Permite aos utilizadores controlar e revogar os documentos que eles têm controlado com o cliente do Azure Information Protection. Os administradores globais também podem controlar esses documentos em nome dos utilizadores. <br /><br />Para obter mais informações, consulte [configurando e usando o controlo de documentos do Azure Information Protection](./rms-client/client-admin-guide-document-tracking.md).|
|Registos de eventos de cliente|Atividade de utilização para o cliente do Azure Information Protection, iniciou sessão do Windows local **aplicativos e serviços** registo de eventos **do Azure Information Protection**. <br /><br />Para obter mais informações, consulte [registo de utilização para o cliente do Azure Information Protection](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client).|
|Ficheiros de registo de cliente|Registos de resolução de problemas para o cliente do Azure Information Protection, localizado em **%localappdata%\Microsoft\MSIP**. <br /><br />Estes ficheiros estão concebidos para Support da Microsoft.|

Além disso, as informações dos registos de utilização do cliente do Azure Information Protection e o scanner do Azure Information Protection são recolhidas e agregadas para criar relatórios no portal do Azure. Para obter mais informações, consulte [de relatórios do Azure Information Protection](reports-aip.md).

Utilize as secções seguintes para obter mais informações sobre o registo de utilização para o serviço Azure Rights Management. 

## <a name="how-to-enable-azure-rightsmanagement-usage-logging"></a>Como ativar o registo de utilização do Azure Rights Management
A partir de Fevereiro de 2016, registo de utilização do Azure Rights Management está ativado por predefinição para todos os clientes. Isto aplica-se aos clientes que ativaram o serviço Azure Rights Management antes e após fevereiro de 2016. 

> [!NOTE]
> Não existem custos adicionais associados ao armazenamento dos registos nem à funcionalidade do registo.
> 
> Se utilizava o registo de utilização para o Azure Rights Management antes de fevereiro de 2016, precisava de uma subscrição do Azure e de espaço de armazenamento suficiente no Azure, o que já não é o caso.

## <a name="how-to-access-and-use-your-azure-rights-management-usage-logs"></a>Como aceder e utilizar os seus registos de utilização do Azure Rights Management
O serviço Azure Rights Management escreve registos na sua conta de armazenamento do Azure como uma série de blobs. Cada blob contém um ou mais registos num formato de registo expandido W3C. Os nomes dos blobs são números, pela ordem em que foram criados. A secção [Como interpretar os seus registos de utilização do Azure Rights Management](#how-to-interpret-your-azure-rights-management-usage-logs), que se encontra mais adiante neste documento, contém mais informações sobre os conteúdos dos registos e a criação dos mesmos.

Após uma ação do Azure Rights Management, os registos poderão demorar algum tempo a serem apresentados na sua conta de armazenamento. A maioria dos registos é apresentada no espaço de 15 minutos. Recomendamos que transfira os registos para o armazenamento local, por exemplo para uma pasta local, uma base de dados ou um repositório MapReduce.

Para transferir os seus registos de utilização, deverá utilizar o módulo de administração do Azure Rights Management para o Windows PowerShell. Para obter instruções de instalação, consulte [instalar o módulo do PowerShell do AADRM](install-powershell.md). Caso já tenha transferido este módulo do Windows PowerShell, execute o seguinte comando para verificar se o seu número de versão é **2.4.0.0** ou posterior: `(Get-Module aadrm -ListAvailable).Version` 

### <a name="to-download-your-usage-logs-by-using-powershell"></a>Para transferir os seus registos de utilização através do PowerShell

1.  Inicie o Windows PowerShell com a opção **Executar como administrador** e utilize o cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) para efetuar uma ligação ao serviço Azure Rights Management:

    ```
    Connect-AadrmService
    ```
    
2.  Execute o seguinte comando para transferir os registos de uma data específica: 

    ```
    Get-AadrmUserLog -Path <location> -fordate <date>
    ```

    Por exemplo, depois de criar uma pasta denominada Registos na unidade E:
    
    * Para transferir os registos de uma data específica (como 01/02/2016), execute o seguinte comando: `Get-AadrmUserLog -Path E:\Logs -fordate 2/1/2016`
    
    * Para transferir os registos de um intervalo de datas (como de 01/02/2016 a 14/02/2016), execute o seguinte comando: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016` 

Quando especifica apenas o dia (tal como acontece nos nossos exemplos), assume-se que a hora é 00:00:00 na sua hora local, que é então convertida para UTC. Se especificar uma hora com os parâmetros -fromdate ou -todate (por exemplo, -fromdate "01/02/2016 15:00:00"), essa data e hora será convertida para UTC. Em seguida, o comando Get-AadrmUserLog obtém os registos correspondentes a esse período de tempo UTC.

Não pode especificar menos de um dia inteiro para transferir.

Por predefinição, este cmdlet utiliza três threads para transferir os registos. Se tiver largura de banda de rede suficiente e quiser diminuir o tempo necessário para transferir os registos, utilize o parâmetro -NumberOfThreads, que suporta um valor de 1 a 32. Por exemplo, se executar o seguinte comando, o cmdlet cria 10 threads para transferir os registos: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016 -numberofthreads 10`


> [!TIP]
> Pode agregar todos os seus ficheiros de registo transferidos num ficheiro em formato CSV através do [Log Parser da Microsoft](https://www.microsoft.com/download/details.aspx?id=24659), uma ferramenta de conversão para diversos formatos de registo comuns. Também pode utilizar esta ferramenta para converter dados no formato SYSLOG ou para os importar para uma base de dados. Após instalar a ferramenta, execute o ficheiro `LogParser.exe /?` para obter ajuda e informações relativamente à utilização desta ferramenta. 
>
> Por exemplo, pode executar o seguinte comando para importar todas as informações para um ficheiro com o formato .log: `logparser –i:w3c –o:csv "SELECT * INTO AllLogs.csv FROM *.log"`

#### <a name="if-you-manually-enabled-azure-rights-management-usage-logging-before-the-logging-change-february-22-2016"></a>Se ativou manualmente o registo da utilização do Azure Rights Management antes da alteração do registo de 22 de fevereiro de 2016


Se utilizou o registo da utilização antes da alteração do registo, terá registos de utilização na sua conta de armazenamento do Azure configurada. A Microsoft não copiará estes registos da sua conta de armazenamento para a nova conta de armazenamento gerida pelo Azure Rights Management como parte desta alteração de registo. Você é responsável por gerir o ciclo de vida dos registos gerados anteriormente e pode utilizar o cmdlet [Get-AadrmUsageLog](/powershell/aadrm/vlatest/get-aadrmusagelog) para transferir os registos antigos. Por exemplo:

- Para transferir todos os registos disponíveis para a sua pasta E:\logs: `Get-AadrmUsageLog -Path "E:\Logs"`
    
- Para transferir um intervalo específico de blobs: `Get-AadrmUsageLog –Path "E:\Logs" –FromCounter 1024 –ToCounter 2047`

Tenha em atenção que não é necessário transferir registos com o cmdlet Get-AadrmUsageLog, caso se verifique uma das situações abaixo:

-  Ativou o serviço Azure Rights Management a 22 de fevereiro de 2016 ou antes desta data, mas não ativou a funcionalidade de registo da utilização.

- Ativou o serviço Azure Rights Management depois de 22 de fevereiro de 2016.

## <a name="how-to-interpret-your-azure-rights-management-usage-logs"></a>Como interpretar os seus registos de utilização do Azure Rights Management
Utilize as seguintes informações para saber como interpretar os registos de utilização do Azure Rights Management.

### <a name="the-log-sequence"></a>A sequência de registo
O serviço Azure Rights Management escreve os registos como uma série de blobs. 

Cada entrada no registo tem um carimbo de data/hora UTC. Como o serviço Azure Rights Management é executado em múltiplos servidores de múltiplos centros de dados, por vezes os registos podem parecer não estar em sequência, mesmo quando se encontram ordenados pelo respetivo carimbo de data/hora. No entanto, a diferença é pequena e, normalmente, não é superior a um minuto. Na maioria dos casos, isto não representa um problema para a análise de registos.

### <a name="the-blob-format"></a>O formato de blob
Cada blob está num formato de registo expandido W3C. Começa com estas duas linhas:

**#Software: RMS**

**#Version: 1.1**

A primeira linha indica que estes são registos do Azure Rights Management. A segunda linha indica que o resto do blob segue a especificação da versão 1.1. Recomendamos que todas as aplicações que analisem estes registos verifiquem estas duas linhas antes de continuar a analisar o resto do blob.

A terceira linha apresenta uma lista composta por nomes de campos que são separados por tabulações:

**#Fields: tempo id de linha tipo de pedido id de utilizador resultado id de correlação e-mail de proprietário de id de conteúdo emissor id do modelo-nome do ficheiro data de publicação de datas      admin-action de informações de c c-ip acting-as-user**

Cada uma das linhas subsequentes é um registo. Os valores dos campos estão na mesma ordem da linha anterior e são separados por tabulações. Utilize a seguinte tabela para interpretar os campos.


|   Nome do campo   | Tipo de dados W3C |                                                                                                                                                                          Descrição                                                                                                                                                                          |                                                            Valor de exemplo                                                            |
|----------------|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
|      date      |     Data      |                                                                                                                     Data UTC em que o pedido foi servido.<br /><br />A origem é o relógio local no servidor que serviu o pedido.                                                                                                                     |                                                             2013-06-25                                                              |
|      time      |     Hora      |                                                                                                            Hora UTC, em formato de 24 horas, em que o pedido foi servido.<br /><br />A origem é o relógio local no servidor que serviu o pedido.                                                                                                            |                                                              21:59:28                                                               |
|     row-id     |     Texto      |                                                                           GUID exclusivo deste registo. Se não existir um valor, utilize o valor correlation-id para identificar a entrada.<br /><br />Este valor é útil quando agrega registos ou copia registos para outro formato.                                                                           |                                                1c3fe7a9-d9e0-4654-97b7-14fafa72ea63                                                 |
|  request-type  |     Name      |                                                                                                                                                            Nome da API de RMS que foi pedida.                                                                                                                                                            |                                                           AcquireLicense                                                            |
|    user-id     |    Cadeia     |                                                               O utilizador que efetuou o pedido.<br /><br />O valor está entre plicas. As chamadas a partir de uma chave de inquilino gerida por si (BYOK) têm um valor de **"**, o qual também é aplicável aplica quando os tipos de pedido são anónimos.                                                                |                                                          ‘joe@contoso.com’                                                          |
|     result     |    Cadeia     |                                                                                                                  'Êxito' se o pedido tiver sido servido com êxito.<br /><br />O tipo de erro entre plicas se o pedido tiver falhado.                                                                                                                   |                                                              'Êxito'                                                              |
| correlation-id |     Texto      |                                                                                                 GUID que é comum entre o registo de cliente do RMS e o registo do servidor para um determinado pedido.<br /><br />Este valor pode ser útil para ajudar na resolução de problemas do cliente.                                                                                                 |                                                cab52088-8925-4371-be34-4b71a3112356                                                 |
|   content-id   |     Texto      |                                                                      GUID, entre chavetas, que identifica os conteúdos protegidos (por exemplo, um documento).<br /><br />Este campo só terá um valor se o request-type for AcquireLicense e estiver em branco para todos os outros tipos de pedido.                                                                       |                                               {bb4af47b-cfed-4719-831d-71b98191a4f2}                                                |
|  owner-email   |    Cadeia     |                                                                                                                       Endereço de e-mail do proprietário do documento.<br /><br /> Este campo fica em branco se o tipo de pedido for RevokeAccess.                                                                                                                        |                                                          alice@contoso.com                                                          |
|     issuer     |    Cadeia     |                                                                                                                          Endereço de e-mail do emissor do documento. <br /><br /> Este campo fica em branco se o tipo de pedido for RevokeAccess.                                                                                                                          |                       alice@contoso.com (ou) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'                       |
|  template-id   |    Cadeia     |                                                                                                                    ID do modelo utilizado para proteger o documento. <br /><br /> Este campo fica em branco se o tipo de pedido for RevokeAccess.                                                                                                                     |                                               {6d9371a6-4e2d-4e97-9a38-202233fed26e}                                                |
|   file-name    |    Cadeia     | Nome de ficheiro de um documento protegido que é controlado com o cliente do Azure Information Protection para Windows. <br /><br />Atualmente, alguns ficheiros (como documentos do Office) são apresentados como GUIDs em vez do nome de ficheiro real.<br /><br /> Este campo fica em branco se o tipo de pedido for RevokeAccess. |                                                       DocumentoConfidencial.docx                                                        |
| date-published |     Date      |                                                                                                                          Data em que o ficheiro foi protegido.<br /><br /> Este campo fica em branco se o tipo de pedido for RevokeAccess.                                                                                                                           |                                                         2015-10-15T21:37:00                                                         |
|     c-info     |    Cadeia     |                                                                                   Informações sobre a plataforma de cliente que está a efetuar o pedido.<br /><br />A cadeia específica varia em função da aplicação (por exemplo, do sistema operativo ou do browser).                                                                                   | 'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64' |
|      c-ip      |    Endereço    |                                                                                                                                                       Endereço IP do cliente que efetua o pedido.                                                                                                                                                        |                                                            64.51.202.144                                                            |
|  admin-action  |     Booleano      |                                                                                                                                    Indica se um administrador acedeu ao site de controlo de documentos no modo de Administrador.                                                                                                                                    |                                                                Verdadeiro                                                                 |
| acting-as-user |    Cadeia     |                                                                                                                               O endereço de e-mail do utilizador pelo qual o administrador está a aceder ao site de controlo de documentos.                                                                                                                                |                                                          'joe@contoso.com'                                                          |

#### <a name="exceptions-for-the-user-id-field"></a>Exceções para o campo user-id
Apesar de o campo user-id indicar geralmente o utilizador que efetuou o pedido, existem duas exceções onde o valor não é mapeado para um utilizador real:

-   O valor **"microsoftrmsonline@&lt;IDDoSeuInquilino&gt;.rms.&lt;região&gt;.aadrm.com"**.

    Isto indica que um serviço do Office 365, como o Exchange Online ou SharePoint Online, é que efetua o pedido. Na cadeia, *&lt;IDDoSeuInquilino&gt;* é o GUID para o seu inquilino e *&lt;região&gt;* é a região em que o seu inquilino está registado. Por exemplo, **na** significa North America (América do Norte), **eu** significa Europa e **ap** significa Ásia.

-   Se estiver a utilizar o conector RMS.

    Os pedidos feitos a partir deste conector são registados com o nome do principal do serviço de **Aadrm_S-1-7-0** que é gerado automaticamente quando instala o conector RMS.

#### <a name="typical-request-types"></a>Tipos de pedido comuns
Há muitos tipos de pedido para o serviço Azure Rights Management, mas a seguinte tabela apresenta alguns dos tipos de pedido mais frequentemente utilizados.

|Tipo de pedido|Descrição|
|----------------|---------------|
|AcquireLicense|Um cliente de um computador baseado em Windows está a pedir uma licença para conteúdos protegidos pelo RMS.|
|AcquirePreLicense|Um cliente está a pedir, em nome do utilizador, uma licença para conteúdos protegidos pelo RMS.|
|AcquireTemplates|Foi efetuada uma chamada para adquirir modelos com base em IDs de modelo|
|AcquireTemplateInformation|Foi efetuada uma chamada para obter as ID do modelo a partir do serviço.|
|AddTemplate|É efetuada uma chamada a partir do portal do Azure para adicionar um modelo.|
|AllDocsCsv|É feita uma chamada a partir do site de controlo de documentos para transferir o ficheiro CSV a partir da página **Todos os Documentos**.|
|BECreateEndUserLicenseV1|É efetuada uma chamada a partir de um dispositivo móvel para criar uma licença de utilizador final.|
|BEGetAllTemplatesV1|É efetuada uma chamada a partir de um dispositivo móvel (back-end) para obter todos os modelos.|
|Certify|O cliente está a certificar o utilizador para o consumo e a criação de conteúdo protegido.|
|DeleteTemplateById|Uma chamada é feita a partir do portal do Azure, para eliminar um ID de modelo pelo modelo.|
|DocumentEventsCsv|É feita uma chamada a partir do site de controlo de documentos para transferir o ficheiro .CSV para um único documento.|
|ExportTemplateById|Uma chamada é feita a partir do portal do Azure para exportar um modelo com base no ID de modelo.|
|FECreateEndUserLicenseV1|É semelhante ao pedido AcquireLicense, mas este pedido é efetuado a partir de dispositivos móveis.|
|FECreatePublishingLicenseV1|É igual à combinação dos pedidos Certify e GetClientLicensorCert, feito a partir de clientes móveis.|
|FEGetAllTemplates|É efetuada uma chamada a partir de um dispositivo móvel (front-end) para obter os modelos.|
|FindServiceLocationsForUser|É efetuada uma chamada de consulta de URL, que é utilizada para chamar o pedido Certify ou AcquireLicense.|
|GetAllDocs|É feita uma chamada a partir do site de controlo de documentos para carregar a página **todos os documentos** para um utilizador ou procurar todos os documentos para o inquilino. Utilize este valor com os campos admin-action e acting-as-admin:<br /><br />-admin-action está vazio: Um utilizador vê a **todos os documentos** página para seus próprios documentos.<br /><br />-admin-action é verdadeiro e acting-as-user está vazia: Um administrador vê todos os documentos para o respetivo inquilino.<br /><br />-admin-action é verdadeiro e acting-as-user não está vazia: Um administrador vê a **todos os documentos** para um utilizador.|
|GetAllTemplates|É efetuada uma chamada a partir do portal do Azure, para obter todos os modelos.|
|GetClientLicensorCert|O cliente está a pedir um certificado de publicação (que é posteriormente utilizado para proteger conteúdos) a partir de um computador baseado no Windows.|
|GetConfiguration|É chamado um cmdlet do PowerShell do Azure para obter a configuração do inquilino do Azure RMS.|
|GetConnectorAuthorizations|É efetuada uma chamada a partir dos conectores do RMS para obter a configuração destes a partir da cloud.|
|GetRecipients|É feita uma chamada a partir do site de controlo de documentos para navegar para a vista de lista para um único documento.|
|GetSingle|É feita uma chamada a partir do site de controlo de documentos para navegar para uma página de um **único documento**.|
|GetTenantFunctionalState|O portal do Azure está a verificar se o serviço Azure Rights Management está ativado.|
|GetTemplateById|Uma chamada é feita a partir do portal do Azure para obter um modelo ao especificar um ID de modelo.|
|KeyVaultDecryptRequest|O cliente está a tentar desencriptar os conteúdos protegidos pelo RMS. Aplicável apenas para uma chave de inquilino gerida pelo cliente (BYOK) no Azure Key Vault.|
|KeyVaultGetKeyInfoRequest|É feita uma chamada para verificar se a chave especificada para ser utilizada no Azure Key Vault para a chave de inquilino do Azure Information Protection está acessível e se ainda não está em utilização.|
|KeyVaultSignDigest|É feita uma chamada quando uma chave gerida pelo cliente (BYOK) no Azure Key Vault é utilizada para fins de assinatura. Esta opção é normalmente chamada uma vez por cada pedido AcquireLicence (ou FECreateEndUserLicenseV1), Certify e GetClientLicensorCert (ou FECreatePublishingLicenseV1).|
|KMSPDecrypt|O cliente está a tentar desencriptar os conteúdos protegidos pelo RMS. Aplicável apenas para uma chave de inquilino gerida pelo cliente (BYOK) antiga.|
|KMSPSignDigest|É feita uma chamada quando uma chave gerida pelo cliente (BYOK) antiga é utilizada para fins de assinatura. Esta opção é normalmente chamada uma vez por cada pedido AcquireLicence (ou FECreateEndUserLicenseV1), Certify e GetClientLicensorCert (ou FECreatePublishingLicenseV1).|
|LoadEventsForMap|É feita uma chamada a partir do site de controlo de documentos para navegar para a vista de mapa de um único documento.|
|LoadEventsForSummary|É feita uma chamada a partir do site de controlo de documentos para navegar para a vista de linha de tempo de um único documento.|
|LoadEventsForTimeline|É feita uma chamada a partir do site de controlo de documentos para navegar para a vista de mapa de um único documento.|
|ImportTemplate|É efetuada uma chamada a partir do portal do Azure para importar um modelo.|
|RevokeAccess|É feita uma chamada a partir do site de controlo de documentos para revogar um documento.|
|SearchUsers |É feita uma chamada a partir do site de controlo de documentos para procurar todos os utilizadores num inquilino.|
|ServerCertify|É efetuada uma chamada a partir de um cliente com RMS ativado (tal como o SharePoint) para certificar o servidor.|
|SetUsageLogFeatureState|É efetuada uma chamada para ativar o registo de utilização.|
|SetUsageLogStorageAccount|É efetuada uma chamada para especificar a localização dos registos do serviço Azure Rights Management.|
|UpdateNotificationSettings|É feita uma chamada a partir do site de controlo de documentos para alterar as definições de notificação de um único documento.|
|UpdateTemplate|É efetuada uma chamada a partir do portal do Azure para atualizar um modelo existente.|


## <a name="windows-powershell-reference"></a>Referência do Windows PowerShell
A partir de fevereiro de 2016, o único cmdlet do Windows PowerShell de que necessita para o registo de utilização do Azure Rights Management é [Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog). 

Antes desta alteração, para os registos de utilização do Azure Rights Management, eram necessários os seguintes cmdlets, que estão agora preteridos:  

-   [Disable-AadrmUsageLogFeature](/powershell/module/aadrm/disable-aadrmusagelogfeature)

-   [Enable-AadrmUsageLogFeature](/powershell/module/aadrm/enable-aadrmusagelogfeature)

-   [Get-AadrmUsageLog](/powershell/module/aadrm/get-aadrmusagelog)

-   [Get-AadrmUsageLogFeature](/powershell/module/aadrm/get-aadrmusagelogfeature)

-   [Get-AadrmUsageLogLastCounterValue](/powershell/module/aadrm/get-aadrmusageloglastcountervalue)

-   [Get-AadrmUsageLogStorageAccount](/powershell/module/aadrm/get-aadrmusagelogstorageaccount)

-   [Set-AadrmUsageLogStorageAccount](/powershell/module/aadrm/set-aadrmusagelogstorageaccount)

Se, no seu armazenamento do Azure, tiver registos criados em datas anteriores à da alteração do registo do Azure Rights Management, pode transferi-los com os cmdlets mais antigos Get-AadrmUsageLog e Get-AadrmUsageLogLastCounterValue, tal como faria anteriormente. No entanto, todos os novos registos de utilização escreverão no novo armazenamento do Azure RMS e têm de ser transferidos com o cmdlet Get-AadrmUserLog.

Para mais informações sobre como utilizar o Windows PowerShell para o serviço Azure Rights Management, veja [Administrar o serviço Azure Rights Management através do Windows PowerShell](administer-powershell.md).



