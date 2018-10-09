---
title: Central de relatórios do Azure Information Protection
description: Como utilizar a centralização de relatórios para monitorizar a adoção das suas etiquetas do Azure Information Protection e identificar ficheiros que contêm informações confidenciais
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/27/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.assetid: b2da2cdc-74fd-4bfb-b3c2-2a3a59a6bf2e
ms.reviewer: lilukov
ms.suite: ems
ms.openlocfilehash: cf951bba3cc74a82e31841986dde9e75ec34a630
ms.sourcegitcommit: e70bb1a02e96d701fd5ae2a25536fa485bbf2e87
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/08/2018
ms.locfileid: "48862129"
---
# <a name="central-reporting-for-azure-information-protection"></a>Central de relatórios do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
> Esta funcionalidade está atualmente em pré-visualização e estão sujeitas a alterações. Quaisquer dados recolhidos durante esta pré-visualização podem não ser suportados quando o recurso for movido para disponibilidade geral.


Utilize a análise do Azure Information Protection para criação de relatórios central para controlar a adoção das suas etiquetas do Azure Information Protection, bem como monitorizar o acesso dos utilizadores a etiquetados de documentos e e-mails e quaisquer alterações à respetiva classificação. Também pode identificar documentos que contenham informações confidenciais que devem ser protegidas.

Os dados que vê é agregado de seus clientes do Azure Information Protection, scanners de Azure Information Protection, e [clientes que suportam a etiquetagem unificada](configure-policy-migrate-labels.md#clients-that-support-unified-labeling).

Por exemplo, será capaz de ver o seguinte:

- Partir do **relatório de utilização**, onde pode selecionar um período de tempo:
    
    - As etiquetas estão a ser aplicadas
    
    - Número de documentos e e-mails que estão a ser identificados
    
    - Número de documentos e e-mails que estão a ser protegidos
    
    - O número de utilizadores e o número de dispositivos é Etiquetar documentos e e-mails
    
    - As aplicações que estão a ser utilizadas para etiquetagem

- Partir do **deteção de dados** relatório:

    - Os ficheiros que estão em seus repositórios de dados digitalizados
    
    - Quais arquivos são etiquetados e protegidos e a localização dos ficheiros por etiquetas
    
    - Os ficheiros que contêm informações confidenciais relativas a categorias conhecidas, como dados financeiros e informações pessoais e a localização dos ficheiros por estas categorias
    
Utilizam os relatórios [do Azure Log Analytics](/azure/log-analytics/log-analytics-overview) para armazenar os dados numa área de trabalho que é proprietário. Se estiver familiarizado com a linguagem de consulta, pode modificar as consultas e criar novos relatórios e dashboards do Power BI. Poderá considerar o seguinte tutorial útil compreender a linguagem de consulta: [introdução ao Portal do Analytics](https://docs.loganalytics.io/docs/Learn/Getting-Started/Getting-started-with-the-Analytics-portal). 

Para obter mais informações, leia a mensagem de blogue: [deteção de dados, relatórios e análises para todos os seus dados com o Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Data-discovery-reporting-and-analytics-for-all-your-data-with/ba-p/253854).

### <a name="information-collected-and-sent-to-microsoft"></a>Informações recolhidas e enviadas à Microsoft

Para gerar esses relatórios, os pontos finais de enviar os seguintes tipos de informações à Microsoft:

- A ação de etiqueta. Por exemplo, definir uma etiqueta, alterar uma etiqueta, adicionar ou remover a proteção automáticas e recomendadas de etiquetas.

- ID do inquilino. da sua organização

- O ID de utilizador (endereço de e-mail ou UPN).

- O caminho do ficheiro e o nome de ficheiro de documentos que estão identificadas.

- A versão de cliente do Azure Information Protection.

- A versão de sistema operativo do cliente.

Essas informações são armazenadas numa área de trabalho do Log Analytics do Azure que é proprietário.

## <a name="prerequisites-for-azure-information-protection-analytics"></a>Pré-requisitos para a análise do Azure Information Protection
Para ver os relatórios do Azure Information Protection e criar os seus próprios, certifique-se de que os seguintes requisitos são cumpridos.

|Requisito|Mais informações|
|---------------|--------------------|
|Uma subscrição do Azure, que inclui o Log Analytics|Consulte a [preços do Azure Log Analytics](https://azure.microsoft.com/pricing/details/log-analytics) página.<br /><br />Se não tiver uma subscrição do Azure ou não utilizar atualmente o Azure Log Analytics, a página de preços inclui uma ligação para uma avaliação gratuita.|
|A versão de pré-visualização atual do cliente do Azure Information Protection.|Se ainda não instalou a versão de pré-visualização atual do cliente, pode transferir e instalá-lo a partir da [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).|
|Para o **e o risco de deteção** relatório: <br /><br />-Implementar pelo menos uma instância do scanner do Azure Information Protection (versão de pré-visualização atual)|Para obter instruções de instalação, consulte [Implantando o scanner do Azure Information Protection para classificar e proteger ficheiros automaticamente](deploy-aip-scanner.md). <br /><br />Se estiver a atualizar a partir de uma versão anterior do scanner, veja [atualizar o scanner do Azure Information Protection](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).|


## <a name="configure-a-log-analytics-workspace-for-the-reports"></a>Configurar uma área de trabalho do Log Analytics para os relatórios

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**. 
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.
    
2. Localize a **MANAGE** opções de menu e selecione **configurar análises (pré-visualização)**.

3. Sobre o **o log analytics do Azure Information Protection** painel, verá uma lista de quaisquer áreas de trabalho do Log Analytics que pertencem ao seu inquilino. Efetue uma das seguintes ações:
    
    - Para criar uma nova área de trabalho do Log Analytics: selecione **criar nova área de trabalho**e, no **área de trabalho do Log analytics** painel, forneça as informações pedidas.
    
    - Para utilizar uma área de trabalho do Log Analytics existente: selecione a área de trabalho da lista.

Se precisar de obter ajuda na criação da área de trabalho do Log Analytics, consulte [criar uma área de trabalho do Log Analytics no portal do Azure](https://docs.microsoft.com/azure/log-analytics/log-analytics-quick-create-workspace).

Quando a área de trabalho é configurada, está pronto para ver os relatórios.

## <a name="how-to-view-the-reports"></a>Como ver os relatórios

No painel do Azure Information Protection, localize a **DASHBOARDS (pré-visualização)** opções de menu e selecione uma das seguintes opções:

- **Relatório de utilização**: Utilize este relatório para ver como as etiquetas estão sendo usadas. 

- **Deteção de dados**: Utilize este relatório para ver informações sobre ficheiros que os scanners encontrados.

## <a name="how-to-modify-the-reports"></a>Como modificar os relatórios

Selecione o ícone de consulta no dashboard para abrir um **pesquisa de registos** painel: 

![Ícone de análise de registo para personalizar os relatórios do Azure Information Protection](./media/log-analytics-icon.png)


## <a name="next-steps"></a>Passos Seguintes
Depois de rever as informações nos relatórios, pode optar por efetuar alterações à sua política do Azure Information Protection. Para obter instruções, consulte [configurar a política do Azure Information Protection](configure-policy.md).