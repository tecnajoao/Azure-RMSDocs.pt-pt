---
title: Central de relatórios do Azure Information Protection
description: Como utilizar a centralização de relatórios para monitorizar a adoção das suas etiquetas do Azure Information Protection e identificar ficheiros que contêm informações confidenciais
author: cabailey
ms.author: cabailey
ms.date: 03/22/2019
manager: barbkess
ms.topic: article
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.reviewer: lilukov
ms.suite: ems
ms.openlocfilehash: c7f862a7a16579b6d414c79015c42664e4066c29
ms.sourcegitcommit: cf06c3854e6ee8645c3b71a0257bdb6a1b569843
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2019
ms.locfileid: "58343048"
---
# <a name="central-reporting-for-azure-information-protection"></a>Central de relatórios do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Esta funcionalidade está atualmente em pré-visualização e estão sujeitas a alterações.

Utilize a análise do Azure Information Protection para criação de relatórios central para controlar a adoção das suas etiquetas do Azure Information Protection. Além disso:

- Monitorizar o acesso dos utilizadores a etiquetados de documentos e e-mails e quaisquer alterações à respetiva classificação. 

- Identifica documentos que contenham informações confidenciais que podem ser colocando sua organização em risco se eles não estão protegidos e mitigar o risco ao seguintes recomendações.

Atualmente, os dados que vê são agregados a partir de seus clientes do Azure Information Protection e scanners de Azure Information Protection e de computadores Windows com o [Windows Defender proteção avançada contra ameaças (Windows Defender ATP)](/windows/security/threat-protection/windows-defender-atp/overview).

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

- Partir do **deteção de dados** relatório:

    - Que arquivos estão no seu repositório de dados digitalizados ou computadores Windows 10
    
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

Para gerar esses relatórios, os pontos finais de enviar os seguintes tipos de informações à Microsoft:

- A ação de etiqueta. Por exemplo, definir uma etiqueta, alterar uma etiqueta, adicionar ou remover a proteção automáticas e recomendadas de etiquetas.

- O nome de etiqueta antes e depois da ação de etiqueta.

- ID do inquilino. da sua organização

- O ID de utilizador (endereço de e-mail ou UPN).

- O nome do dispositivo do utilizador.

- Para documentos: O caminho do ficheiro e o nome de ficheiro de documentos que estão identificadas.

- Para mensagens de e-mail: O assunto do e-mail, o remetente de e-mail e destinatários de e-mail para os e-mails que estão identificadas. 

- Os tipos de informações confidenciais ([predefinidos](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) e personalizada) que foram detetadas no conteúdo.

- A versão de cliente do Azure Information Protection.

- A versão de sistema operativo do cliente.

Essas informações são armazenadas numa área de trabalho do Log Analytics do Azure que pode ser visualizada independentemente do Azure Information Protection, os utilizadores que têm direitos de acesso a esta área de trabalho e é o proprietário de sua organização. Para obter detalhes, consulte a [as permissões necessárias para análise do Azure Information Protection](#permissions-required-for-azure-information-protection-analytics) secção. Para obter informações sobre a gestão de acesso à área de trabalho, consulte a [gerir o acesso ao Log Analytics área de trabalho com permissões do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#manage-access-to-log-analytics-workspace-using-azure-permissions) seção na documentação do Azure.

> [!NOTE]
> A área de trabalho do Log Analytics do Azure para o Azure Information Protection inclui uma caixa de verificação para correspondências de conteúdo do documento. Ao selecionar esta caixa de verificação, os dados reais que esteja identificados pelos tipos de informações confidenciais ou de suas condições personalizadas também são recolhidos. Por exemplo, isto pode incluir números de cartão de crédito que forem encontrados, bem como números de previdência social, números de passaporte e números de contas bancárias. Se não pretender recolher estes dados, não selecione esta caixa de verificação.
>
> Atualmente, esta informação não é apresentada nos relatórios, mas pode ser visualizada e obtida com consultas.

## <a name="prerequisites-for-azure-information-protection-analytics"></a>Pré-requisitos para a análise do Azure Information Protection
Para ver os relatórios do Azure Information Protection e criar os seus próprios, certifique-se de que os seguintes requisitos são cumpridos.

|Requisito|Mais informações|
|---------------|--------------------|
|Uma subscrição do Azure, que inclui o Log Analytics|Consulte a [preços do Azure Monitor](https://azure.microsoft.com/pricing/details/log-analytics) página.<br /><br />Se não tiver uma subscrição do Azure ou não utilizar atualmente o Azure Log Analytics, a página de preços inclui uma ligação para uma avaliação gratuita.|
|O cliente do Azure Information Protection (versão atual da disponibilidade geral ou versão de pré-visualização) ou a versão de pré-visualização do Azure Information Protection unified cliente etiquetagem|Se ainda não estiver instalado um destas versões do cliente, pode transferir e instalá-los a partir do Microsoft Download Center:<br /> - [Cliente do Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) <br /> - [O Azure Information Protection unified cliente etiquetagem](https://www.microsoft.com/en-us/download/details.aspx?id=57440)|
|Para o **e o risco de deteção** relatório: <br /><br />-Para apresentar dados de arquivos de dados no local, implementar, pelo menos, uma instância do scanner do Azure Information Protection (versão atual do geral disponibilidade ou de pré-visualização) <br /><br />-Para apresentar dados de computadores Windows 10, tem de ser uma compilação mínimo do 1809, que está a utilizar o Windows Defender proteção avançada contra ameaças (Windows Defender ATP) e tiver ativado a funcionalidade de integração do Azure Information Protection do Windows Defender Centro de segurança|Para obter instruções de instalação para a deteção de impressão, consulte [Implantando o scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](deploy-aip-scanner.md). <br /><br />Para obter informações sobre como configurar e utilizar a funcionalidade de integração do Azure Information Protection a partir do Centro de segurança do Windows Defender, consulte [proteção de informações na visão geral do Windows](/windows/security/threat-protection/windows-defender-atp/information-protection-in-windows-overview).|
|Para o **recomendações** relatório: <br /><br />-Para adicionar um novo repositório de dados a partir do portal do Azure como uma ação recomendada, tem de utilizar a versão de pré-visualização atual do scanner do Azure Information Protection |Para implementar a versão de pré-visualização do scanner, veja [implantar a versão de pré-visualização do scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](deploy-aip-scanner-preview.md).|

### <a name="permissions-required-for-azure-information-protection-analytics"></a>Permissões necessárias para análise do Azure Information Protection

Especificamente para análise do Azure Information Protection, depois de ter configurado a sua área de trabalho do Log Analytics do Azure, pode utilizar a função de administrador do Azure AD de leitor de segurança como uma alternativa para as outras funções do Azure AD que suporta a gestão de informações do Azure Proteção no portal do Azure.

Uma vez que esse recurso usa a monitorização do Azure, o controlo de acesso baseado em funções (RBAC) para o Azure também controla o acesso à área de trabalho. Precisa, portanto, uma função do Azure, bem como uma função de administrador do Azure AD para gerir a análise do Azure Information Protection. Se estiver familiarizado com as funções do Azure, poderá considerar útil ler [diferenças entre funções RBAC do Azure e funções de administrador do Azure AD](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles#differences-between-azure-rbac-roles-and-azure-ad-administrator-roles).

Detalhes:

1. Para aceder ao painel de análise do Azure Information Protection no portal do Azure, tem de ter um dos seguintes [funções de administrador do Azure AD](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
    - Para criar a sua área de trabalho do Log Analytics ou para criar consultas personalizadas, um dos seguintes:
    
        - **Administrador do Information Protection**
        - **Administrador de segurança**
        - **Administrador Global**
    
    - Para ver os dados após o Log Analytics área de trabalho tiver sido criado, um dos seguintes:
    
        - **Leitor de segurança**
        - **Administrador do Information Protection**
        - **Administrador de segurança**
        - **Administrador Global**
    
    > [!NOTE] 
    > Se o seu inquilino tiver sido migrado para a loja de etiquetagem unificada, sua conta tem de ser um administrador global ou um do listadas funções e permissões para acessar o Centro de conformidade e segurança do Office 365. [Mais informações](configure-policy-migrate-labels.md#important-information-about-administrative-roles)

2. Para acessar sua área de trabalho do Log Analytics do Azure, tem de ter um dos seguintes procedimentos [funções do Azure Log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access#manage-access-to-log-analytics-workspace-using-azure-permissions) ou padrão [funções do Azure](https://docs.microsoft.com/azure/role-based-access-control/overview#role-assignments):
    
    - Para criar uma área de trabalho do Log Analytics ou para criar consultas personalizadas, um dos seguintes:
    
        - **Contribuidor do log Analytics**
        - Função do Azure: **Proprietário** ou **contribuinte**
    
    - Para ver os dados numa área de trabalho do Log Analytics depois da área de trabalho ter sido criada, um dos seguintes:
    
        - **Leitor do log Analytics**
        - Função do Azure: **Reader**

#### <a name="minimum-roles-to-view-the-reports"></a>Funções mínimo para visualizar os relatórios

Depois de ter configurado a sua área de trabalho para análise do Azure Information Protection, as funções mínimas necessárias para ver os relatórios são os seguintes elementos:

- Função de administrador do Azure AD: **Leitor de segurança**
- Função do Azure: **Leitor do log Analytics**

## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Configurar uma área de trabalho do Log Analytics para os relatórios

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](https://portal.azure.com) com uma conta que tenha o [as permissões necessárias para análise do Azure Information Protection](#permissions-required-for-azure-information-protection-analytics). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.
    
2. Localize a **Manage** opções de menu e selecione **configurar análises (pré-visualização)**.

3. Sobre o **o log analytics do Azure Information Protection** painel, verá uma lista de quaisquer áreas de trabalho do Log Analytics que pertencem ao seu inquilino. Efetue uma das seguintes ações:
    
    - Para criar uma nova área de trabalho do Log Analytics: Selecione **criar nova área de trabalho**e, no **área de trabalho do Log analytics** painel, forneça as informações pedidas.
    
    - Para utilizar uma área de trabalho do Log Analytics existente: Selecione a área de trabalho da lista.

Se precisar de ajuda com a criação da área de trabalho do Log Analytics, consulte [criar uma área de trabalho do Log Analytics no portal do Azure](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace).

Quando a área de trabalho é configurada, está pronto para ver os relatórios.

## <a name="how-to-view-the-reports"></a>Como ver os relatórios

No painel do Azure Information Protection, localize a **Dashboards** opções de menu e selecione uma das seguintes opções:

- **Relatório de utilização (pré-visualização)**: Utilize este relatório para ver como as etiquetas estão sendo usadas. 

- **Registos de Atividades (pré-visualização)**: Utilize este relatório para ver a etiquetagem de ações de usuários e em dispositivos e caminhos de ficheiros.
    
    Este relatório tem um **colunas** opção, o que lhe permite exibir mais informações de atividade do que a apresentação predefinida.

- **Deteção de dados (pré-visualização)**: Utilize este relatório para ver informações sobre arquivos encontrados por scanners ou do Windows Defender ATP.

- **Recomendações (pré-visualização)**: Utilize este relatório para identificar ficheiros que tenham informações confidenciais e mitigar o risco ao seguir as recomendações.
    
    Este relatório está atualmente a implementar aos inquilinos, portanto, se não o vir, tente novamente dentro de alguns dias.
    
    Quando seleciona um item, o **ver dados** opção apresenta as atividades de auditoria que disparou a recomendação.

> [!NOTE]
> Está a ocorrer um problema conhecido ao visualizar pontos de interrogação (**?**) em caminhos e nomes de arquivos em vez de não-ASCII quando a Localidade do sistema de operativo envio está em inglês.

## <a name="how-to-modify-the-reports"></a>Como modificar os relatórios

Selecione o ícone de consulta no dashboard para abrir um **pesquisa de registos** painel: 

![Ícone de análise de registo para personalizar os relatórios do Azure Information Protection](./media/log-analytics-icon.png)


Os dados com sessão iniciada para o Azure Information Protection são armazenados na tabela a seguir: **InformationProtectionLogs_CL**

## <a name="next-steps"></a>Passos Seguintes
Depois de rever as informações nos relatórios, pode optar por efetuar alterações à sua política do Azure Information Protection. Para obter instruções, consulte [configurar a política do Azure Information Protection](configure-policy.md).
