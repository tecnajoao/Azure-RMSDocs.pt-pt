---
title: Terminologia do Azure Information Protection
description: "Está confuso com uma palavra, expressão ou acrónimo relacionado com o Microsoft Azure Information Protection? Encontre aqui a definição de termos e de abreviaturas específicos do Azure Information Protection ou que tenham um significado específico quando utilizados no contexto deste serviço."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 742877bf-26f5-40e3-b1f7-8475e7c3ce11
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: a5cfa773d440e92fe9d3e88e242dfb25f7174400


---

# <a name="terminology-for-azure-information-protection"></a>Terminologia do Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Está confuso com uma palavra, expressão ou acrónimo relacionado com o Microsoft Azure Information Protection? Encontre aqui a definição de termos e de abreviaturas específicos do Azure Information Protection ou que tenham um significado específico quando utilizados no contexto deste serviço.

|Termo|Definição|
|--------|--------------|
|AADRM|O nome do módulo do Windows PowerShell para o serviço Azure Rights Management, derivado da abreviatura não oficial do [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], anteriormente denominado (Windows) Azure Active Directory Rights Management.|
|ativar|Ativar o serviço [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] para que uma organização possa proteger os respetivos documentos e e-mails. Esta ação também ativa as funcionalidades do Rights Management no Exchange Online e no SharePoint Online.|
|Serviços de Gestão de Direitos do Active Directory|Frequentemente abreviado para *AD RMS*.<br /><br />Uma função do Windows Server que fornece proteção de gestão de direitos através de encriptação e políticas para o ajudar a proteger documentos, ficheiros e e-mails.|
|AD RMS|Consulte *Serviços de Gestão de Direitos do Active Directory*.|
|Azure Information Protection|Um serviço baseado na nuvem que utiliza classificação, etiquetagem e proteção para o ajudar a proteger documentos e e-mails. O Azure Rights Management fornece a proteção utilizando as políticas de encriptação, de identidade e de autorização.|
|Azure Rights Management|Frequentemente abreviado para *Azure RMS*.<br /><br />Um serviço do Azure utilizado pelo Azure Information Protection que utiliza encriptação e políticas para o ajudar a proteger documentos, ficheiros e e-mails.  Também conhecido como *serviço Azure Rights Management*. Os nomes anteriores incluem:<br /><br />- *Windows Azure Active Directory Rights Management*: abreviado frequentemente para Windows Azure AD Rights Management Service.<br /><br />- *RMS Online*: o nome originalmente proposto, que por vezes poderá ver em mensagens de erro e em entradas de ficheiros de registo.|
|Azure RMS|Consulte *Azure Rights Management*.|
|BYOK|Consulte *traga a sua própria chave*.|
|traga a sua própria chave|Frequentemente abreviado para *BYOK*.<br /><br />Uma opção de configuração e topologia escolhida por uma organização que pretenda gerar e gerir as próprias chaves de inquilino do Azure Information Protection.|
|chave de conteúdo|Uma chave exclusiva que é criada por aplicações otimizadas por RMS para cada documento ou e-mail que é protegido através da utilização do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] e que ajuda a limitar o risco de divulgação de informações.|
|consumir|Desbloquear um ficheiro para leitura ou utilização quando esse ficheiro foi protegido pelo [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|
|desativar|Desativar o serviço Rights Management para que a organização deixe de poder utilizar o Azure Information Protection.|
|modelo departamental|Um modelo de política de direitos que o utilizador cria (um modelo personalizado) e que está configurado para ser visível para utilizadores selecionados, em vez de todos os utilizadores na sua organização.|
|aplicações otimizadas|Aplicações que suportam nativamente o Rights Management, que inclui aplicações do Office, como o Word e o Excel. Os fabricantes independentes de software (ISV) e os programadores também podem escrever aplicações que suportem nativamente o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|
|gestão de direitos de empresa|Um termo genérico comum da indústria, utilizado frequentemente para descrever produtos e soluções que ajudam as organizações a proteger as informações confidenciais ou valiosas ao utilizar uma combinação de ferramentas de encriptação e de autorização de políticas. O Azure Information Protection é um exemplo de uma solução de gestão de direitos de empresa (ERM).|
|ERM|Consulte *gestão de direitos de empresa*.|
|proteção genérica|Um nível de proteção que encripta qualquer tipo de ficheiro e evita que os utilizadores não autorizados abram o ficheiro. Ao abrir o ficheiro, o ficheiro fica desencriptado e utilizável numa aplicação que não suporta nativamente o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|
|HYOK|Veja *tenha a sua própria chave*.|
|tenha a sua própria chave|Frequentemente abreviado para *HYOK*.<br /><br />Uma opção de configuração e topologia de uma organização que pretende gerar e armazenar as suas próprias chaves no local, normalmente por motivos de regulamentação ou conformidade.|
|proteção de informações|Por vezes, abreviado para *IP*.<br /><br />Um termo genérico comum na indústria que se refere à proteção de dados e ficheiros contra acesso não autorizado, mesmo depois de os dados e os ficheiros saírem dos limites organizacionais através de e-mail ou da partilha de documentos. O Microsoft Azure Information Protection é um exemplo de uma solução de proteção de informações (IP).|
|Gestão de Direitos de Informação|Frequentemente abreviado para *IRM*.<br /><br />Um termo utilizado em conjunto com os serviços do Office, como o Exchange Server, o Word e o SharePoint Online, para descrever a capacidade de suportar o serviço Microsoft Rights Management.|
|IRM|Consulte *Gestão de Direitos de Informação*.|
|MSDRM|Por vezes apresentado como referência para o cliente RMS 1.0, que é substituído pelo cliente mais recente, MSIPC. Este cliente antigo suporta as aplicações que são desenvolvidas com o SDK RMS 1.0 e suporta o Office 2010 e o Office 2007, o Exchange 2010 e o Exchange 2013, bem como o SharePoint 2010 e o SharePoint 2007.|
|MSIPC|Por vezes apresentado como referência para o cliente RMS 2.0, que substituiu o cliente RMS mais antigo, MSDRM. Este cliente mais recente suporta as aplicações que são desenvolvidas com o SDK RMS 2.0 e suporta o Office 2016 e o Office 2013, o SharePoint 2013, a aplicação de partilha RMS e o cliente do Azure Information Protection.|
|proteção nativa|Um nível de proteção disponível em todas as aplicações otimizadas que impede que pessoas não autorizadas abram um ficheiro e que também possam aplicar políticas mais restritas, tais como só de leitura e que não são impressas. Além disso, esta proteção permanece com o ficheiro, mesmo quando o ficheiro é reencaminhado para outras pessoas ou guardado numa localização pública à qual outras pessoas possam aceder.|
|.pfile|A extensão de nome de ficheiro que é acrescentada a todos os ficheiros que o serviço de gestão de direitos protege genericamente.|
|.ppdf|A extensão de nome de ficheiro que o serviço de gestão de direitos cria quando este cria automaticamente uma cópia em PDF de um ficheiro (Word, Excel, PowerPoint ou PDF) que partilha por e-mail, para que o ficheiro possa ser lido (mas não editado) em todos os dispositivos.|
|nível de permissões|Um agrupamento de direitos de utilização lógico que faz com que seja mais fácil para os utilizadores finais e os administradores escolherem opções de configuração baseadas em funções. Por exemplo, Revisor e Coautor.|
|proteger|Aplicar controlos de gestão de direitos a ficheiros ou mensagens de e-mail através de políticas de controlo de acesso, encriptação e identidade para ajudar a proteger os seus dados.|
|publicar|Proteger um ficheiro de modo a salvaguardá-lo contra o acesso e a utilização não autorizados.|
|Conector Rights Management|Um reencaminhamento de proxy de saída que pode implementar para serviços no local, como o Exchange Server e o SharePoint, para proteger dados através do serviço Azure Rights Management.|
|Serviços de Gestão de Direitos|O termo genérico que se aplica tanto à versão na nuvem do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] ([!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]) como à versão no local do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] (AD RMS).|
|Aplicação de partilha Rights Management|Foi agora substituída pelo cliente do Azure Information Protection, uma aplicação opcional para o Windows e para os dispositivos móveis mais populares, que suporta a partilha segura de ficheiros no local e por e-mail.|
|RMS|Consulte *Serviços de Gestão de Direitos*.|
|Conector RMS|Consulte *Conector Rights Management*.|
|RMS para indivíduos|Uma subscrição gratuita para um utilizador utilizar o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] quando a sua organização não tiver uma subscrição do Office 365 ou do Azure Active Directory.|
|Aplicação de partilha RMS|Consulte *Aplicação de partilha Rights Management*.|
|superutilizador|Um grupo de administradores altamente fidedignos que pode desencriptar e aceder a ficheiros que a organização protegeu através de um serviço de gestão de direitos. Normalmente, este nível de acesso é necessário para a Deteção de Dados Eletrónicos jurídicos e as equipas de auditoria.|
|chave de inquilino|Também conhecida como a chave do certificado de licenciante para servidor (SLC).<br /><br />A chave que é exclusiva de uma organização e, em última análise, protege todas as funções criptográficas do [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] que se encadeiam nesta chave de inquilino.|
|desproteger|Remover controlos de gestão de direitos de ficheiros ou mensagens de e-mail, que utilizaram políticas de controlo de acesso, encriptação e identidade para ajudar a proteger os seus dados.|
|licença de utilização|Um certificado por documento que é concedido a um utilizador que abre um ficheiro ou e-mail que tenha sido protegido por um serviço de gestão de direitos. Este certificado contém direitos desse utilizador para o ficheiro ou a mensagem de e-mail e a chave de encriptação que foi utilizada para encriptar o conteúdo, bem como restrições de acesso adicionais definidas na política do documento.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Feb17_HO4-->


