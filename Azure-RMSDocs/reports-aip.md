---
title: Central de relatórios do Azure Information Protection
description: Como utilizar a centralização de relatórios para monitorizar a adoção das suas etiquetas do Azure Information Protection e identificar ficheiros que contêm informações confidenciais
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/27/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.reviewer: lilukov
ms.suite: ems
ms.openlocfilehash: 98403232311731b137719c613b2ce061a236b706
ms.sourcegitcommit: ff77e4da1f7c7cf2262c208f8e58b85cfdb54903
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52421016"
---
# <a name="central-reporting-for-azure-information-protection"></a>Central de relatórios do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Esta funcionalidade está atualmente em pré-visualização e estão sujeitas a alterações. Quaisquer dados recolhidos durante esta pré-visualização podem não ser suportados quando o recurso for movido para disponibilidade geral.


Utilize a análise do Azure Information Protection para criação de relatórios central para controlar a adoção das suas etiquetas do Azure Information Protection, bem como monitorizar o acesso dos utilizadores a etiquetados de documentos e e-mails e quaisquer alterações à respetiva classificação. Também pode identificar documentos que contenham informações confidenciais que devem ser protegidas.

Atualmente, os dados que vê são agregados a partir de seus clientes do Azure Information Protection e scanners de Azure Information Protection.

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

    - Os ficheiros que estão em seus repositórios de dados digitalizados
    
    - Quais arquivos são etiquetados e protegidos e a localização dos ficheiros por etiquetas
    
    - Os ficheiros que contêm informações confidenciais relativas a categorias conhecidas, como dados financeiros e informações pessoais e a localização dos ficheiros por estas categorias
    
Utilizam os relatórios [do Azure Log Analytics](/azure/log-analytics/log-analytics-overview) para armazenar os dados numa área de trabalho que sua organização é proprietária. Se estiver familiarizado com a linguagem de consulta, pode modificar as consultas e criar novos relatórios e dashboards do Power BI. Poderá considerar o seguinte tutorial útil compreender a linguagem de consulta: [introdução ao Portal do Analytics](https://docs.loganalytics.io/docs/Learn/Getting-Started/Getting-started-with-the-Analytics-portal). 

Para obter mais informações, leia a mensagem de blogue: [deteção de dados, relatórios e análises para todos os seus dados com o Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854).

### <a name="information-collected-and-sent-to-microsoft"></a>Informações recolhidas e enviadas à Microsoft

Para gerar esses relatórios, os pontos finais de enviar os seguintes tipos de informações à Microsoft:

- A ação de etiqueta. Por exemplo, definir uma etiqueta, alterar uma etiqueta, adicionar ou remover a proteção automáticas e recomendadas de etiquetas.

- O nome de etiqueta antes e depois da ação de etiqueta.

- ID do inquilino. da sua organização

- O ID de utilizador (endereço de e-mail ou UPN).

- O nome do dispositivo do utilizador.

- Para documentos: caminho de ficheiro e nome de ficheiro de documentos que estão identificadas.

- Para e-mails: O assunto do e-mail, do remetente de e-mail e destinatários de e-mail para os e-mails que estão identificadas. 

- Os tipos de informações confidenciais ([predefinidos](https://docs.microsoft.com/office365/securitycompliance/what-the-sensitive-information-types-look-for) e personalizada) que foram detetadas no conteúdo.

- A versão de cliente do Azure Information Protection.

- A versão de sistema operativo do cliente.

Essas informações são armazenadas numa área de trabalho do Log Analytics do Azure que é proprietário e pode ser visualizada por utilizadores que têm direitos de acesso a esta área de trabalho da sua organização. Para obter informações sobre como configurar o acesso à área de trabalho, consulte a [gerir contas e utilizadores](/azure/log-analytics/log-analytics-manage-access?toc=/azure/azure-monitor#manage-accounts-and-users) seção na documentação do Azure.

## <a name="prerequisites-for-azure-information-protection-analytics"></a>Pré-requisitos para a análise do Azure Information Protection
Para ver os relatórios do Azure Information Protection e criar os seus próprios, certifique-se de que os seguintes requisitos são cumpridos.

|Requisito|Mais informações|
|---------------|--------------------|
|Uma subscrição do Azure, que inclui o Log Analytics|Consulte a [preços do Azure Log Analytics](https://azure.microsoft.com/pricing/details/log-analytics) página.<br /><br />Se não tiver uma subscrição do Azure ou não utilizar atualmente o Azure Log Analytics, a página de preços inclui uma ligação para uma avaliação gratuita.|
|A versão atual em disponibilidade geral do cliente do Azure Information Protection.|Se ainda não instalou esta versão do cliente, pode transferir e instalá-lo a partir da [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).|
|Para o **e o risco de deteção** relatório: <br /><br />-Implementar pelo menos uma instância do scanner do Azure Information Protection (versão de pré-visualização atual)|Para obter instruções de instalação, consulte [Implantando o scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](deploy-aip-scanner.md). <br /><br />Se estiver a atualizar a partir de uma versão anterior do scanner, veja [atualizar o scanner do Azure Information Protection](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).|


## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Configurar uma área de trabalho do Log Analytics para os relatórios

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.
    
2. Localize a **Manage** opções de menu e selecione **configurar análises (pré-visualização)**.

3. Sobre o **o log analytics do Azure Information Protection** painel, verá uma lista de quaisquer áreas de trabalho do Log Analytics que pertencem ao seu inquilino. Efetue uma das seguintes ações:
    
    - Para criar uma nova área de trabalho do Log Analytics: selecione **criar nova área de trabalho**e, no **área de trabalho do Log analytics** painel, forneça as informações pedidas.
    
    - Para utilizar uma área de trabalho do Log Analytics existente: selecione a área de trabalho da lista.

Se precisar de obter ajuda na criação da área de trabalho do Log Analytics, consulte [criar uma área de trabalho do Log Analytics no portal do Azure](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace).

Quando a área de trabalho é configurada, está pronto para ver os relatórios.

## <a name="how-to-view-the-reports"></a>Como ver os relatórios

No painel do Azure Information Protection, localize a **Dashboards** opções de menu e selecione uma das seguintes opções:

- **Relatório de utilização (pré-visualização)**: Utilize este relatório para ver como as etiquetas estão sendo usadas. 

- **Registos de Atividades (pré-visualização)**: Utilize este relatório para ver a etiquetagem de ações de usuários e em dispositivos e caminhos de ficheiro.
    
    Este relatório está atualmente a implementar aos inquilinos, portanto, se não o vir, tente novamente dentro de alguns dias. 
    
    Este relatório tem um **colunas** opção, o que lhe permite exibir mais informações de atividade do que a apresentação predefinida. Uma das colunas destina **risco do dispositivo**, que irá apresentar dados do Windows Defender quando esse aplicativo é integrado com o Azure Information Protection.

- **Deteção de dados (pré-visualização)**: Utilize este relatório para ver informações sobre ficheiros que os scanners encontrados.

## <a name="how-to-modify-the-reports"></a>Como modificar os relatórios

Selecione o ícone de consulta no dashboard para abrir um **pesquisa de registos** painel: 

![Ícone de análise de registo para personalizar os relatórios do Azure Information Protection](./media/log-analytics-icon.png)


Os dados com sessão iniciada para o Azure Information Protection são armazenados na tabela seguinte: **InformationProtectionLogs_CL**

## <a name="next-steps"></a>Passos Seguintes
Depois de rever as informações nos relatórios, pode optar por efetuar alterações à sua política do Azure Information Protection. Para obter instruções, consulte [configurar a política do Azure Information Protection](configure-policy.md).