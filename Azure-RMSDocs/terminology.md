---
title: Terminologia do Azure Information Protection
description: Está confuso com uma palavra, expressão ou acrónimo relacionado com o Microsoft Azure Information Protection? Encontre aqui a definição de termos e de abreviaturas específicos do Azure Information Protection ou que tenham um significado específico quando utilizados no contexto deste serviço.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/01/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 742877bf-26f5-40e3-b1f7-8475e7c3ce11
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 388abeb75a5b80a575990923f37f2bb19a9e5e7f
ms.sourcegitcommit: 8558af7116f62414054feffa346aba197a1250d9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2019
ms.locfileid: "55559704"
---
# <a name="terminology-for-azure-information-protection"></a>Terminologia do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Está confuso com uma palavra, expressão ou acrónimo relacionado com o Microsoft Azure Information Protection? Encontre aqui a definição de termos e de abreviaturas específicos do Azure Information Protection ou que tenham um significado específico quando utilizados no contexto deste serviço.

|Termo|Definição|
|--------|--------------|
|AADRM|O nome do módulo do PowerShell para o serviço Azure Rights Management, derivado da abreviatura não oficial do Azure Rights Management quando, anteriormente denominado (Windows) Azure Active Directory Rights Management.|
|ativar|Para ativar o serviço Azure Rights Management para que uma organização possa proteger os respetivos documentos e e-mails. Esta ação também permite que as funcionalidades da IRM no Exchange Online e SharePoint Online.|
|Serviços de Gestão de Direitos do Active Directory|Frequentemente abreviado para *AD RMS*.<br /><br />Uma função do Windows Server que fornece proteção de gestão de direitos através da utilização de encriptação e políticas para ajudar a proteger documentos, ficheiros e e-mails.|
|AD RMS|Consulte *Serviços de Gestão de Direitos do Active Directory*.|
AzureInformationProtection|O nome do módulo do PowerShell para o cliente do Azure Information Protection.
|Azure Information Protection|Um serviço baseado na nuvem que utiliza as etiquetas para classificar e proteger documentos e e-mails. O Azure Rights Management fornece a proteção utilizando as políticas de encriptação, de identidade e de autorização.|
Cliente do Azure Information Protection|Lado do cliente do Azure Information Protection, que permite que os utilizadores, administradores e os serviços utilizam as etiquetas e as definições de política do Azure Information Protection.|
|Etiqueta do Azure Information Protection|Um item que aplica-se uma classificação a documentos e e-mails de valor e, opcionalmente, pode protegê-los.|
|Política do Azure Information Protection|Configuração para clientes e serviços que utilizam o Azure Information Protection etiquetas e as definições de política definida pelo administrador.|
|Scanner do Azure Information Protection|Um serviço que é executado no Windows Server e permite-lhe detetar, classificar e proteger os documentos em pastas locais, compartilhamentos de rede e sites do SharePoint Server e bibliotecas.|
|Visualizador do Azure Information Protection|Uma aplicação que é executado em computadores Windows e dispositivos móveis, para apresentar ficheiros protegidos.|
|Azure Rights Management|Frequentemente abreviado para *do Azure RMS*.<br /><br />Um serviço do Azure utilizado pelo Azure Information Protection que utiliza encriptação e políticas para o ajudar a proteger documentos, ficheiros e e-mails.  Também conhecido como *serviço Azure Rights Management*. Os nomes anteriores incluem:<br /><br />- *Gestão de direitos do Windows do Azure Active Directory*: Frequentemente abreviado para Windows Azure AD Rights Management Service.<br /><br />- *RMS Online*: O nome originalmente proposto, que por vezes, poderá ver em mensagens de erro e as entradas de ficheiros de registo.|
|Azure RMS|Ver *do Azure Rights Management*.|
|modelo predefinido|Um modelo de proteção que é criado automaticamente para quando obtém uma subscrição do Azure Information Protection, para que pode começar a proteger os documentos e e-mails que contêm informações confidenciais.|
|BYOK|Consulte *traga a sua própria chave*.|
|traga a sua própria chave|Frequentemente abreviado para *BYOK*.<br /><br />Uma opção de configuração e topologia escolhida por uma organização que pretenda gerar e gerir as próprias chaves de inquilino do Azure Information Protection.|
|chave de conteúdo|Uma chave exclusiva que é criada por aplicações otimizadas por RMS para cada documento ou e-mail que é protegido com o Rights Management e que ajuda a limitar o risco de divulgação de informações.|
|consumir|Para abrir um documento ou e-mail para ler ou utilizá-lo quando esse conteúdo tenha sido protegido pelo Rights Management. Para um documento, consumindo inclui edição e a adição de novos conteúdos para um documento protegido. Para uma mensagem de e-mail, consumindo inclui responder a uma mensagem protegida.|
|desativar|Desativar o serviço Rights Management para que a organização deixe de poder utilizar o Azure Information Protection.|
|modelo departamental|Um modelo de proteção que cria e que está configurado para ser visível para utilizadores selecionados, em vez de todos os utilizadores na sua organização. Também conhecido como um *modelo com âmbito*.|
|aplicações otimizadas|Aplicações que suportam nativamente o Rights Management, que inclui aplicações do Office, como o Word e o Excel. Fornecedores independentes de software (ISVs) e os desenvolvedores também podem escrever as aplicações que suportam nativamente o Rights Management.|
|gestão de direitos de empresa|Um termo genérico comum da indústria, utilizado frequentemente para descrever produtos e soluções que ajudam as organizações a proteger as informações confidenciais ou valiosas ao utilizar uma combinação de ferramentas de encriptação e de autorização de políticas. O Azure Information Protection é um exemplo de uma solução de gestão de direitos de empresa (ERM).|
|ERM|Consulte *gestão de direitos de empresa*.|
|proteção genérica|Um nível de proteção que encripta qualquer tipo de ficheiro e evita que os utilizadores não autorizados abram o ficheiro. Depois do arquivo é aberto, o ficheiro fica desencriptado e utilizável numa aplicação que não suporta nativamente o Rights Management.|
|HYOK|Veja *tenha a sua própria chave*.|
|tenha a sua própria chave|Frequentemente abreviado para *HYOK*.<br /><br />Uma opção de configuração e topologia de uma organização que pretende gerar e armazenar as suas próprias chaves no local, normalmente por motivos de regulamentação ou conformidade.|
|objeto de chave|No contexto de chaves de inquilino, uma entidade que contém metadados exigidos pelo serviço Azure Rights Management para operações criptográficas.|
|label|Ver *etiqueta do Azure Information Protection*.|
|proteção de informações|Por vezes, abreviado para *IP*.<br /><br />Um termo genérico comum na indústria que se refere à proteção de dados e ficheiros contra acesso não autorizado, mesmo depois de os dados e os ficheiros saírem dos limites organizacionais através de e-mail ou da partilha de documentos. Microsoft Azure Information Protection é um exemplo de uma solução de proteção (IP) de informações.|
|Gestão de Direitos de Informação|Frequentemente abreviado para *IRM*.<br /><br />Um termo utilizado em conjunto com os serviços do Office, como o Exchange Server, o Word e o SharePoint Online, para descrever a capacidade para suportar os serviços Microsoft Rights Management.|
|IRM|Consulte *Gestão de Direitos de Informação*.|
|Encriptação de mensagens do Office|Frequentemente abreviado para *LGUMAS*.<br /><br />As novas capacidades de encriptação de mensagens do Office 365 tem integração nativa com o serviço Azure Rights Management para fornecer a mesma proteção de e-mail para utilizadores internos e externos, automática de atualização de modelos e oferecer suporte para a traga a sua própria chave (BYOK) cenário. A implementação de LGUMAS anterior foi projetada para apenas os destinatários externos, necessária uma regra de fluxo de correio e não oferecia suporte BYOK.|
|MSDRM|Por vezes apresentado como referência para o cliente RMS 1.0, que é substituído pelo cliente mais recente, MSIPC. Este cliente antigo suporta as aplicações que são desenvolvidas com o SDK RMS 1.0 e suporta o Office 2010 e o Office 2007, o Exchange 2010 e o Exchange 2013 e o SharePoint 2010 e o SharePoint 2007.|
|MSIPC|Por vezes apresentado como referência para o cliente do RMS 2.0, que substituiu o cliente RMS mais antigo, MSDRM. Este cliente mais recente suporta as aplicações que são desenvolvidas com o SDK RMS 2.0 e suporta o Office 365 ProPlus, Office 2019, Office 2016, Office 2013, SharePoint 2013 e o cliente do Azure Information Protection.|
|proteção nativa|Um nível de proteção disponível em todas as aplicações otimizadas que impede que pessoas não autorizadas abram um ficheiro e que também possam aplicar políticas mais restritas, tais como só de leitura e que não são impressas. Além disso, esta proteção permanece com o ficheiro, mesmo quando o ficheiro é reencaminhado para outras pessoas ou guardado numa localização pública à qual outras pessoas possam aceder.|
|.pfile|A extensão de nome de ficheiro que é acrescentada a todos os ficheiros que o serviço de gestão de direitos protege genericamente.|
|nível de permissões|Um agrupamento de direitos de utilização lógico que faz com que seja mais fácil para os utilizadores finais e os administradores escolherem opções de configuração baseadas em funções. Por exemplo, Revisor e Coautor.|
|proteger|Aplicar controlos de gestão de direitos a ficheiros ou mensagens de e-mail através de políticas de controlo de acesso, encriptação e identidade para ajudar a proteger os seus dados.|
|modelo de proteção|Também conhecido como um *modelo de política de direitos*, *modelo do Rights Management*, e *modelo RMS*.<br /><br />Um grupo de definições de proteção que são geridos por um administrador e que incluem os direitos de utilização definidos para os utilizadores autorizados e acessar os controles de expiração e acesso offline. |
|publicar|Proteger um ficheiro de modo a salvaguardá-lo contra o acesso e a utilização não autorizados. Também utilizado como um termo em conjunto com modelos de proteção e a política do Azure Information Protection, para que estes itens disponíveis para utilização por clientes e serviços.|
|Conector Rights Management|Um reencaminhamento de proxy de saída que pode implementar para serviços no local, como o Exchange Server e SharePoint, para proteger os dados com o serviço Azure Rights Management.|
|Emissor do Rights Management|A conta que protegeu um documento ou e-mail.|
|Proprietário do Rights Management|A conta que mantém o controlo total de um documento protegido ou e-mail pelo facto de ser automaticamente concedido o direito de utilização controlo total do Rights Management e está isento de qualquer data de expiração ou a definição offline.|
|Serviços de Gestão de Direitos|O termo genérico que aplica-se para a versão de nuvem do Rights Management (Azure Rights Management) e a versão no local do Rights Management (AD RMS).|
|Aplicação de partilha Rights Management|Agora substituída pelo cliente do Azure Information Protection.|
|RMS|Consulte *Serviços de Gestão de Direitos*.|
|Conector RMS|Consulte *Conector Rights Management*.|
|RMS para indivíduos|Uma subscrição gratuita para um utilizador utilizar o Rights Management quando a sua organização não tiver uma subscrição do Office 365 ou Azure Active Directory.|
|Aplicação de partilha RMS|Consulte *Aplicação de partilha Rights Management*.|
|Modelo de RMS|Ver *modelo de proteção*.|
|modo apenas de proteção|Um modo operacional para o cliente do Azure Information Protection quando não existe qualquer política do Azure Information Protection para aplicar etiquetas. Neste modo, não são apresentadas etiquetas de classificação, mas os utilizadores ainda podem aplicar a proteção do Rights Management.|
|scanner|Ver *scanner do Azure Information Protection*.|
|superutilizador|Um grupo de administradores altamente fidedignos que pode desencriptar e aceder a ficheiros que a organização protegeu através de um serviço de gestão de direitos. Normalmente, este nível de acesso é necessário para a Deteção de Dados Eletrónicos jurídicos e as equipas de auditoria.|
|chave de inquilino|Também conhecida como a chave do certificado de licenciante para servidor (SLC).<br /><br />A chave que é exclusiva de uma organização e, por fim, protege todas as funções criptográficas do Rights Management que se encadeiam nesta chave de inquilino.|
|desproteger|Remover controlos de proteção de ficheiros ou mensagens de e-mail, que utilizaram a encriptação, identidade, direitos de utilização, e aceder a políticas de controlo para ajudar a proteger seus dados.|
|licença de utilização|Um certificado por documento que é concedido a um utilizador que abre um ficheiro ou e-mail que tenha sido protegido por um serviço de gestão de direitos. Este certificado contém direitos desse utilizador para o ficheiro ou a mensagem de e-mail e a chave de encriptação que foi utilizada para encriptar o conteúdo, bem como restrições de acesso adicionais definidas na política do documento.|

