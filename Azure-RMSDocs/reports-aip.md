---
title: Central de relatórios do Azure Information Protection
description: Como utilizar a centralização de relatórios para monitorizar a adoção das suas etiquetas do Azure Information Protection e identificar ficheiros que contêm informações confidenciais
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/08/2019
ms.topic: article
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.reviewer: lilukov
ms.suite: ems
ms.openlocfilehash: 735e7253701c3cbed8af7974d27cf241fb515c90
ms.sourcegitcommit: ce2078712d111f102a72b3a8697121f1390bdf07
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59289422"
---
# <a name="central-reporting-for-azure-information-protection"></a>Central de relatórios do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Esta funcionalidade está atualmente em pré-visualização e estão sujeitas a alterações.

Utilize a análise do Azure Information Protection para criação de relatórios central para o ajudar a controlar a adoção das suas etiquetas do Azure Information Protection. Adicionalmente:

- O nome de monitor e proteger documentos e e-mails em sua organização

- Identificar documentos que contenham informações confidenciais da sua organização

- Acesso de utilizador do monitor para etiquetados de documentos e e-mails e registar alterações de classificação do documento.

- Identifica documentos que contenham informações confidenciais que podem ser colocando sua organização em risco se eles não estão protegidos e mitigar o risco ao seguintes recomendações.

Os dados que vê são agregados a partir de seus clientes do Azure Information Protection e verificadores de computadores Windows com o Azure Information Protection [Windows Defender proteção avançada contra ameaças (Windows Defender ATP)](/windows/security/threat-protection/windows-defender-atp/overview), e a partir [clientes que suportam a etiquetagem unificada](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling).

Por exemplo, será capaz de ver o seguinte:

- Partir do **relatório de utilização**, onde pode selecionar um período de tempo:
    
    - As etiquetas estão a ser aplicadas
    
    - Número de documentos e e-mails que estão a ser identificados
    
    - Número de documentos e e-mails que estão a ser protegidos
    
    - O número de utilizadores e o número de dispositivos é Etiquetar documentos e e-mails
    
    - As aplicações que estão a ser utilizadas para etiquetagem

- Partir do **registos de atividades**, onde pode selecionar um período de tempo:
    
    - Que ações de etiquetas foram executadas por um utilizador específico
    
    - Que ações de etiquetas foram executadas de um dispositivo específico
    
    - Os utilizadores que acederam a um documento com nome específico
    
    - Que ações de etiquetas foram efetuadas para um caminho de ficheiro específico
    
    - Que ações de etiquetas foram executadas por uma aplicação específica, tal Explorador de ficheiros e botão direito do mouse ou o módulo AzureInformationProtection do PowerShell
    
    - Desagregar para ficheiros comunicados para exibir **detalhes de atividade** para obter informações adicionais

- Partir do **deteção de dados** relatório:

    - Que arquivos estão no seu repositório de dados digitalizados, Windows 10 computadores ou computadores que executam a versão de pré-visualização do cliente do Azure Information Protection ou [os clientes que suportam a etiquetagem unificada](configure-policy-migrate-labels.md#clients-and-services-that-support-unified-labeling)
    
    - Quais arquivos são etiquetados e protegidos e a localização dos ficheiros por etiquetas
    
    - Os ficheiros que contêm informações confidenciais relativas a categorias conhecidas, como dados financeiros e informações pessoais e a localização dos ficheiros por estas categorias

- Partir do **recomendações** relatório:
    
    - Identificar ficheiros desprotegidos, que contêm um tipo de informações confidenciais conhecidos. Uma recomendação permite que configure imediatamente a condição correspondente para uma das suas etiquetas para aplicar automática ou recomendada de etiquetagem.
        
        Se seguir a recomendação: Da próxima vez que os arquivos são abertos por um utilizador ou analisados pelo scanner do Azure Information Protection, os ficheiros podem ser automaticamente classificados e protegidos.
    
    - Os repositórios de dados tem ficheiros com informações confidenciais identificados, mas não estão a ser analisados pelo Azure Information Protection. Uma recomendação permite-lhe adicionar imediatamente o arquivo de dados identificado como um dos perfis do scanner.
        
        Se seguir a recomendação: No próximo ciclo de scanner, os ficheiros podem ser automaticamente classificados e protegidos.

Utilizam os relatórios [do Azure Monitor](/azure/log-analytics/log-analytics-overview) para armazenar os dados numa área de trabalho do Log Analytics que sua organização é proprietária. Se estiver familiarizado com a linguagem de consulta, pode modificar as consultas e criar novos relatórios e dashboards do Power BI. Poderá considerar o seguinte tutorial útil compreender a linguagem de consulta: [Introdução às consultas de registo do Azure Monitor](/azure/azure-monitor/log-query/get-started-queries).

Para obter mais informações, leia as seguintes mensagens de blogue: 
- [Deteção de dados, relatórios e análises para todos os seus dados com o Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854)

- [Detetar e proteger os dados confidenciais através do Azure Information Protection e o Windows Defender ATP](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discover-and-protect-sensitive-data-through-Azure-Information/ba-p/297292)

### <a name="information-collected-and-sent-to-microsoft"></a>Informações recolhidas e enviadas à Microsoft

Para gerar esses relatórios, pontos finais de enviar os seguintes tipos de informações à Microsoft:

- A ação de etiqueta. Por exemplo, definir uma etiqueta, alterar uma etiqueta, adicionar ou remover a proteção automáticas e recomendadas de etiquetas.

- O nome de etiqueta antes e depois da ação de etiqueta.

- ID do inquilino. da sua organização

- O ID de utilizador (endereço de e-mail ou UPN).

- O nome do dispositivo do utilizador.

- Para documentos: O caminho do ficheiro e o nome de ficheiro de documentos que estão identificadas.

- Para mensagens de e-mail: O assunto do e-mail e o remetente de e-mail para os e-mails que estão identificadas. 

- Os tipos de informações confidenciais ([predefinidos](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) e personalizada) que foram detetadas no conteúdo.

- A versão de cliente do Azure Information Protection.

- A versão de sistema operativo do cliente.

Essas informações são armazenadas numa área de trabalho do Log Analytics do Azure que pode ser visualizada independentemente do Azure Information Protection, os utilizadores que têm direitos de acesso a esta área de trabalho e é o proprietário de sua organização. Para obter detalhes, consulte a [as permissões necessárias para análise do Azure Information Protection](#permissions-required-for-azure-information-protection-analytics) secção. Para obter informações sobre a gestão de acesso à área de trabalho, consulte a [gerir o acesso ao Log Analytics área de trabalho com permissões do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#manage-access-to-log-analytics-workspace-using-azure-permissions) seção na documentação do Azure.

Para impedir que os clientes do Azure Information Protection enviar estes dados, defina o [definição de política](configure-policy-settings.md) dos **enviar dados de auditoria para o Azure Information Protection do log analytics** para **desligado**:

- Para a maioria dos usuários ao enviar esta não é possível enviar os dados e um subconjunto de utilizadores a auditoria de dados: 
    - Definir **enviar dados de auditoria para o Azure Information Protection do log analytics** ao **desativar** numa política de âmbito para o subconjunto de utilizadores. Esta configuração é típica para cenários de produção.

- Para apenas um subconjunto de utilizadores para enviar dados de auditoria: 
    - Definir **enviar dados de auditoria para o Azure Information Protection do log analytics** ao **desativar** na política global, e **no** numa política de âmbito para o subconjunto de utilizadores. Esta configuração é típica para cenários de teste.

#### <a name="content-matches-for-deeper-analysis"></a>Correspondências de conteúdo para uma análise mais aprofundada 

A área de trabalho do Log Analytics do Azure para o Azure Information Protection inclui uma caixa de verificação também recolher e armazenar os dados que esteja identificados pelos tipos de informações confidenciais ou de suas condições personalizadas. Por exemplo, isto pode incluir números de cartão de crédito que forem encontrados, bem como números de previdência social, números de passaporte e números de contas bancárias. Se não pretender enviar estes dados adicionais, não selecione esta caixa de verificação. Se pretender que a maioria dos usuários para enviar esses dados adicionais e um subconjunto de utilizadores não pode enviá-lo, selecione a caixa de verificação e configure uma [definição de cliente avançado](./rms-client/client-admin-guide-customizations.md#disable-sending-information-type-matches-for-a-subset-of-users) numa política de âmbito para o subconjunto de utilizadores.

Depois de recolher o conteúdo corresponde, são apresentados nos relatórios quando desagregar para ficheiros a partir de registos de atividade, para exibir **detalhes de atividade**. Estas informações também podem ser visualizadas e obtidas com consultas.

## <a name="prerequisites"></a>Pré-requisitos
Para ver os relatórios do Azure Information Protection e criar os seus próprios, certifique-se de que os seguintes requisitos são cumpridos.

|Requisito|Mais informações|
|---------------|--------------------|
|Uma subscrição do Azure, que inclui o Log Analytics e que destina-se ao mesmo inquilino do Azure Information Protection|Consulte a [preços do Azure Monitor](https://azure.microsoft.com/pricing/details/log-analytics) página.<br /><br />Se não tiver uma subscrição do Azure para o mesmo inquilino ou não utilizar atualmente o Azure Log Analytics, a página de preços inclui uma ligação para uma avaliação gratuita.|
|O cliente do Azure Information Protection (versão atual da disponibilidade geral ou versão de pré-visualização) ou a versão de pré-visualização do Azure Information Protection unified cliente etiquetagem|Se ainda não estiver instalado um destas versões do cliente, pode transferir e instalá-los a partir do Microsoft Download Center:<br /> - [Cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) <br /> - [O Azure Information Protection unified cliente etiquetagem](https://www.microsoft.com/en-us/download/details.aspx?id=57440)|
|Para o **e o risco de deteção** relatório: <br /><br />-Para apresentar dados de arquivos de dados no local, implementar, pelo menos, uma instância do scanner do Azure Information Protection (versão atual do geral disponibilidade ou de pré-visualização) <br /><br />-Para apresentar dados de computadores Windows 10, tem de ser uma compilação mínimo do 1809, que está a utilizar o Windows Defender proteção avançada contra ameaças (Windows Defender ATP) e tiver ativado a funcionalidade de integração do Azure Information Protection do Windows Defender Centro de segurança|Para obter instruções de instalação para a deteção de impressão, consulte [Implantando o scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](deploy-aip-scanner.md). <br /><br />Para obter informações sobre como configurar e utilizar a funcionalidade de integração do Azure Information Protection a partir do Centro de segurança do Windows Defender, consulte [proteção de informações na visão geral do Windows](/windows/security/threat-protection/windows-defender-atp/information-protection-in-windows-overview).|
|Para o **recomendações** relatório: <br /><br />-Para adicionar um novo repositório de dados a partir do portal do Azure como uma ação recomendada, tem de utilizar a versão de pré-visualização atual do scanner do Azure Information Protection |Para implementar a versão de pré-visualização do scanner, veja [implantar a versão de pré-visualização do scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](deploy-aip-scanner-preview.md).|


### <a name="permissions-required-for-azure-information-protection-analytics"></a>Permissões necessárias para análise do Azure Information Protection

Especificamente para análise do Azure Information Protection, depois de ter configurado a sua área de trabalho do Log Analytics do Azure, pode utilizar a função de administrador do Azure AD de leitor de segurança como uma alternativa para as outras funções do Azure AD que suporta a gestão de informações do Azure Proteção no portal do Azure.

Uma vez que esse recurso usa a monitorização do Azure, o controlo de acesso baseado em funções (RBAC) para o Azure também controla o acesso à área de trabalho. Precisa, portanto, uma função do Azure, bem como uma função de administrador do Azure AD para gerir a análise do Azure Information Protection. Se estiver familiarizado com as funções do Azure, poderá considerar útil ler [diferenças entre funções RBAC do Azure e funções de administrador do Azure AD](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles#differences-between-azure-rbac-roles-and-azure-ad-administrator-roles).

Detalhes:

1. Um dos seguintes [funções de administrador do Azure AD](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) para aceder ao painel de análise do Azure Information Protection:
    
    - Para criar a sua área de trabalho do Log Analytics ou para criar consultas personalizadas:
    
        - **Administrador do Information Protection**
        - **Administrador de segurança**
        - **Administrador de conformidade**
        - **Administrador global**
    
    - Depois da área de trabalho tiver sido criada, em seguida, pode utilizar a seguinte função com menos permissões para ver os dados recolhidos:
    
        - **Leitor de segurança**
    
    > [!NOTE] 
    > Se o seu inquilino tiver sido migrado para a loja de etiquetagem unificada, não é possível utilizar a função de administrador do Information Protection. [Mais informações](configure-policy-migrate-labels.md#important-information-about-administrative-roles)

2. Além disso, precisa de um dos seguintes procedimentos [funções do Azure Log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#managing-access-to-log-analytics-using-azure-permissions) ou padrão [funções do Azure](https://docs.microsoft.com/azure/role-based-access-control/overview#role-assignments) para acessar sua área de trabalho do Log Analytics do Azure:
    
    - Para criar a área de trabalho ou para criar consultas personalizadas, um dos seguintes:
    
        - **Contribuidor do log Analytics**
        - **Contribuinte**
        - **Proprietário**
    
    - Depois da área de trabalho tiver sido criada, pode, em seguida, utilizar uma das seguintes funções com menos permissões para ver os dados recolhidos:
    
        - **Leitor do log Analytics**
        - **Reader**

#### <a name="minimum-roles-to-view-the-reports"></a>Funções mínimo para visualizar os relatórios

Depois de ter configurado a sua área de trabalho para análise do Azure Information Protection, as funções mínimas necessárias para ver os relatórios de análise do Azure Information Protection são os seguintes elementos:

- Função de administrador do Azure AD: **Leitor de segurança**
- Função do Azure: **Leitor do log Analytics**

No entanto, uma atribuição de função típico para muitas organizações é a função de Azure AD **leitor de segurança** e a função do Azure das **leitor**.

## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Configurar uma área de trabalho do Log Analytics para os relatórios

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](https://portal.azure.com) com uma conta que tenha o [as permissões necessárias para análise do Azure Information Protection](#permissions-required-for-azure-information-protection-analytics). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.
    
2. Localize a **Manage** opções de menu e selecione **configurar análises (pré-visualização)**.

3. Sobre o **o log analytics do Azure Information Protection** painel, verá uma lista de quaisquer áreas de trabalho do Log Analytics que pertencem ao seu inquilino. Efetue uma das seguintes opções:
    
    - Para criar uma nova área de trabalho do Log Analytics: Selecione **criar nova área de trabalho**e, no **área de trabalho do Log analytics** painel, forneça as informações pedidas.
    
    - Para utilizar uma área de trabalho do Log Analytics existente: Selecione a área de trabalho da lista.

Se precisar de ajuda com a criação da área de trabalho do Log Analytics, consulte [criar uma área de trabalho do Log Analytics no portal do Azure](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace).

Quando a área de trabalho é configurada, está pronto para ver os relatórios.

## <a name="how-to-view-the-reports"></a>Como ver os relatórios

No painel do Azure Information Protection, localize a **Dashboards** opções de menu e selecione uma das seguintes opções:

- **Relatório de utilização (pré-visualização)**: Utilize este relatório para ver como as etiquetas estão sendo usadas.

- **Registos de Atividades (pré-visualização)**: Utilize este relatório para ver a etiquetagem de ações de usuários e em dispositivos e caminhos de ficheiros.
    
    Este relatório tem um **colunas** opção que lhe permite exibir mais informações de atividade do que a apresentação predefinida. Também pode ver mais detalhes sobre um ficheiro ao selecioná-lo a apresentar **detalhes de atividade**.

- **Deteção de dados (pré-visualização)**: Utilize este relatório para ver informações sobre ficheiros etiquetados encontrado por scanners e pontos de extremidades suportados.
    
    Nota: Deteção para o ponto final é implementar gradualmente aos inquilinos. Começar a ver dados a partir de pontos finais suportados neste relatório, quando esta funcionalidade foi implementada com o seu inquilino.
    
    Pode configurar uma [definição de cliente avançado](./rms-client/client-admin-guide-customizations.md#enable-azure-information-protection-analytics-to-discover-sensitive-information-in-documents) para a versão de pré-visualização do cliente do Azure Information Protection para os ficheiros de relatório que contêm informações confidenciais.
    
    Sugestão: As informações recolhidas, poderá considerar os utilizadores que acedem a ficheiros que contêm informações confidenciais da localização que não tem conhecimento ou não são atualmente análise:
    
    - Se as localizações no local, considere adicionar as localizações como repositórios de dados adicionais para o scanner do Azure Information Protection.
    - Se as localizações encontram-se na cloud, considere utilizar o Microsoft Cloud App Security para geri-los. 
    
- **Recomendações (pré-visualização)**: Utilize este relatório para identificar ficheiros que tenham informações confidenciais e mitigar o risco ao seguir as recomendações.
    
    Quando seleciona um item, o **ver dados** opção apresenta as atividades de auditoria que disparou a recomendação.

> [!NOTE]
> Está a ocorrer um problema conhecido ao visualizar pontos de interrogação (**?**) em caminhos e nomes de arquivos em vez de não-ASCII quando a Localidade do sistema de operativo envio está em inglês.

## <a name="how-to-modify-the-reports-and-create-custom-queries"></a>Como modificar os relatórios e criar consultas personalizadas

Selecione o ícone de consulta no dashboard para abrir um **pesquisa de registos** painel: 

![Ícone de análise de registo para personalizar os relatórios do Azure Information Protection](./media/log-analytics-icon.png)


Os dados com sessão iniciada para o Azure Information Protection são armazenados na tabela a seguir: **InformationProtectionLogs_CL**

Ao criar suas próprias consultas, utilize os nomes de esquema amigável que foi implementados como **InformationProtectionEvents** funções. Estas funções são derivadas de atributos que são suportados para consultas personalizadas (alguns atributos são apenas para utilização interna) e os respetivos nomes, não serão alterado ao longo do tempo, mesmo que os atributos subjacentes alterar para novas funcionalidades e melhorias.

### <a name="friendly-schema-reference-for-event-functions"></a>Referência de esquema amigável para as funções de eventos

Utilize a tabela seguinte para identificar o nome amigável de funções de eventos que podem ser utilizados para consultas personalizadas com a análise do Azure Information Protection.

| Nome da coluna | Descrição | |---_---|---| | Tempo | Hora do evento: UTC no formato AAAA-MM-ddTHH | | Utilizador | Utilizador: Formato UPN ou domínio \ utilizador | | O caminho de item | Item completo caminho ou assunto de e-mail | | ItemName | Assunto de e-mail ou nome de ficheiro | | Método | Etiqueta atribuída método: Manual, automático, recomendado, predefinidas ou obrigatório | | Atividade | Atividade de auditoria: DowngradeLabel, UpgradeLabel, RemoveLabel, NewLabel, detetar, acesso, RemoveCustomProtection, ChangeCustomProtection ou NewCustomProtection | | LabelName | Nome de etiqueta (não localizado) | | LabelNameBefore | Nome de etiqueta antes da alteração (não localizada) | | ProtectionType | Tipo de proteção [JSON] <br />{ <br />"Type": ["Template", "Custom", "DoNotForward"], <br />  "TemplateID": "GUID" <br /> } <br />| | ProtectionBefore | Tipo de proteção antes de alteração [JSON] | | InformationTypesMatches | Matriz JSON de [SensitiveInformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) encontrado nos dados em que uma matriz vazia significa que não existem tipos de informações significa encontrada e null não existem informações disponíveis | | MachineName | FQDN quando disponível; caso contrário, nome de anfitrião | | DeviceRisk | Pontuação de risco do dispositivo de WDATP quando estiverem disponíveis | | Plataforma | Plataforma de dispositivo (Win, OSX, Android, iOS) | | ApplicationName | Nome amigável de aplicação | | AIPVersion | Versão do cliente do Azure Information Protection que efetuou a ação de auditoria | | TenantId | ID de inquilino do Azure AD | | AzureApplicationId | O Azure AD registado aplicação ID (GUID) | | ProcessName | Processo que hospeda MIP SDK | | LabelId | Etiqueta GUID ou null | | IsProtected | Se protegido: Sim/não | | ProtectionOwner | Proprietário de gestão de direitos no formato UPN | | LabelIdBefore | GUID ou null antes da alteração da etiqueta | | InformationTypesAbove55 | Matriz JSON de [SensitiveInformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) encontrados nos dados com o nível de confiança 55 ou acima | | InformationTypesAbove65 | Matriz JSON de [SensitiveInformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) encontrados nos dados com o nível de confiança de 65 ou acima | | InformationTypesAbove75 | Matriz JSON de [SensitiveInformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) encontrados nos dados com o nível de confiança de 75 ou acima | | InformationTypesAbove85 | Matriz JSON de [SensitiveInformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) encontrados nos dados com o nível de confiança 85 ou superior | | InformationTypesAbove95 | Matriz JSON de [SensitiveInformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) encontrados nos dados com o nível de confiança 95 ou acima | | DiscoveredInformationTypes | Matriz JSON de [SensitiveInformation](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) encontrado nos dados e seu conteúdo correspondente (se ativada), onde uma matriz vazia significa que não existem tipos de informações encontrados e nulos significa que não existem informações disponíveis | | ProtectedBefore | Se o conteúdo foi protegido antes de alteração: Sim/não | | ProtectionOwnerBefore | Proprietário do Rights Management antes da alteração | | UserJustification | Justificação quando fazer downgrade ou remover etiqueta | | LastModifiedBy | Utilizador no formato do UPN que modificou pela última vez o ficheiro. Disponível para o Office e SharePoint Online apenas | | LastModifiedDate | UTC no formato AAAA-MM-ddTHH: Disponível para o Office e SharePoint Online apenas |


#### <a name="examples-using-informationprotectionevents"></a>Exemplos que utilizam o InformationProtectionEvents

Utilize os exemplos seguintes para ver como pode usar o esquema amigável para criar consultas personalizadas.

##### <a name="example-1-return-all-users-who-sent-audit-data-in-the-last-31-days"></a>Exemplo 1: Devolver todos os utilizadores que enviaram dados de auditoria nos últimos 31 dias 

```
InformationProtectionEvents 
| where Time > ago(31d) 
| distinct User 
```

 
##### <a name="example-2-return-the-number-of-labels-that-were-downgraded-per-day-in-the-last-31-days"></a>Exemplo 2: Devolver o número de etiquetas que foram desatualizada por dia nos últimos 31 dias 


```
InformationProtectionEvents 
| where Time > ago(31d) 
| where Activity == "DowngradeLabel"  
| summarize Label_Downgrades_per_Day = count(Activity) by bin(Time, 1d) 
 
```
 
##### <a name="example-3-return-the-number-of-labels-that-were-downgraded-from-confidential-by-user-in-the-last-31-days"></a>Exemplo 3: Devolver o número de etiquetas que foram mudado de confidencial por utilizador, nos últimos 31 dias 

```

InformationProtectionEvents 
| where Time > ago(31d) 
| where Activity == "DowngradeLabel"  
| where LabelNameBefore contains "Confidential" and LabelName !contains "Confidential"  
| summarize Label_Downgrades_by_User = count(Activity) by User | sort by Label_Downgrades_by_User desc 

```

Neste exemplo, uma etiqueta desatualizada é contabilizada apenas se o nome de etiqueta antes da ação contido o nome **confidencial** e o nome de rótulo depois da ação não continha o nome do **confidencial**. 


## <a name="next-steps"></a>Passos Seguintes
Depois de rever as informações nos relatórios, pode optar por efetuar alterações à sua política do Azure Information Protection. Para obter instruções, consulte [configurar a política do Azure Information Protection](configure-policy.md).

Se tiver uma subscrição do Microsoft 365, também pode ver a utilização de etiqueta no Centro de conformidade do Microsoft 365 e do Centro de segurança do Microsoft 365. Para obter mais informações, consulte [ver a utilização de etiqueta com a análise de etiqueta](/Office365/SecurityCompliance/label-analytics).
