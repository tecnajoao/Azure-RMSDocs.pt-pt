---
title: Descrição geral da proteção do Azure Rights Management do Azure Information Protection – AIP
description: Informações sobre o Azure Rights Management (Azure RMS), a tecnologia de proteção utilizada pelo Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: aeeebcd7-6646-4405-addf-ee1cc74df5df
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ba44c23b56c2832268f0ed6df122a347c9a8fdf3
ms.sourcegitcommit: 2a1c0882d2b0400f4da6370dbc1830df09867e3d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53218464"
---
# <a name="what-is-azure-rights-management"></a>O que é o Azure Rights Management?

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


O Azure Rights Management (frequentemente abreviado para o Azure RMS) é a tecnologia de proteção utilizada pelo [do Azure Information Protection](what-is-information-protection.md).

Este serviço de proteção baseada na cloud utiliza políticas de encriptação, identidade e autorização para ajudar a proteger os ficheiros e e-mail e funciona em vários dispositivos — telemóveis, tablets e PCs. As informações podem ser protegidas dentro e fora da organização, porque essa proteção permanece com os dados, mesmo quando sai dos limites da organização.

Por exemplo, os funcionários podem enviar por e-mail um documento a uma empresa parceira ou guardar um documento na respetiva unidade na cloud. A proteção persistente que o Azure RMS fornece não só ajuda a proteger os dados da sua empresa, mas pode também ser legalmente estabelecida para conformidade, requisitos, ou simplesmente para práticas de gestão de boas informações.

Mas muito importante, as pessoas autorizadas e serviços (por exemplo, pesquisa e indexação) podem continuar a ler e inspecionar os dados protegidos. Esta capacidade não é facilmente realizada com outras soluções de proteção de informações que utilizam encriptação ponto a ponto-a-ponto. Esse recurso conhecido como "raciocínio através de dados" deve ter ouvido falar e é um elemento fundamental na manutenção do controlo dos dados da sua organização.

A imagem seguinte mostra como este serviço oferece uma solução de proteção para o Office 365, bem como para servidores no local e serviços. Também verá que a proteção é suportada pelos dispositivos de utilizador final populares que executam o Windows, Mac OS, iOS, Android e Windows Phone.


![Como funciona o Azure RMS](./media/AzRMS_elements.png)

Pode utilizar esta proteção com subscrições do Office 365, bem como com subscrições do Azure Information Protection. Pode encontrar mais informações sobre as subscrições disponíveis e que funcionalidades que suportam no [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) site.

## <a name="business-problems-solved-by-azure-rights-management"></a>Problemas de negócios resolvidos pelo Azure Rights Management

Utilize a tabela seguinte para identificar os requisitos de negócios ou os problemas que sua organização pode ter ao proteger documentos e e-mails e como a tecnologia Azure Rights Management pode resolver.


|Requisito ou problema|Resolvido pelo Azure RMS|
|--------------------------|-----------------------|
|Proteger vários tipos de ficheiro|√ Na implementação anterior do Rights Management, só era possível proteger ficheiros, do Office através da proteção do Rights Management nativa. Agora, a **proteção genérica** que foi primeiro oferecida pela aplicação de partilha Rights Management e agora pelo cliente do Azure Information Protection significa que mais [tipos de ficheiro](./rms-client/client-admin-guide-file-types.md) são suportados.|
|Proteger ficheiros em qualquer lugar|√ Quando um ficheiro está [protegidos](./rms-client/client-classify-protect.md), a proteção mantém-se com o ficheiro, mesmo que seja guardado ou copiado para o armazenamento que não esteja sob o controlo de TI, tal como um serviço de armazenamento na cloud.|
|Partilhar informações de forma segura|√ Quando um ficheiro está [protegidos](./rms-client/client-classify-protect.md), é seguro partilhar com outras pessoas. Por exemplo, um anexo de um e-mail ou uma ligação para um site do SharePoint. Se as informações confidenciais estiverem numa mensagem de e-mail, pode proteger o e-mail ou simplesmente utilizar a opção Não Reencaminhar no Outlook. <br /><br />A vantagem de anexar um ficheiro protegido, em vez de proteger toda a mensagem de e-mail completa, é que o texto do e-mail não é encriptado, pelo que pode incluir as instruções para a primeira utilização se o e-mail estiver a ser enviado fora da sua organização. Qualquer pessoa pode ler as instruções. No entanto, dado que o documento anexado está protegido, apenas os utilizadores autorizados poderão abri-lo, mesmo que o e-mail ou o documento seja reencaminhado para outras pessoas.|
|Auditoria e monitorização|√ Pode [auditar e monitorizar a utilização](log-analyze-usage.md) dos seus ficheiros protegidos, mesmo depois destes ficheiros saírem dos limites da organização.<br /><br />Por exemplo, trabalha para a Contoso, Ltd. Está a trabalhar num projeto conjunto com três pessoas da Fabrikam, Inc. Envia a estas três pessoas um documento por e-mail que protege e restringe para só de leitura. A auditoria do Azure Rights Management, pode fornecer as seguintes informações:<br /><br />- Se as pessoas que especificou na Fabrikam abriram o documento e quando.<br /><br />- Se outras pessoas que não especificou tentaram (e não conseguiram) abrir o documento, talvez porque foi reencaminhado ou guardado numa localização partilhada à qual outros utilizadores podiam aceder.<br /><br />- Se qualquer uma das pessoas especificadas tentou (e não conseguiu) imprimir ou alterar o documento.<br /><br />Além disso, o [site de controlo de documentos](./rms-client/client-track-revoke.md) permite aos utilizadores e administradores controlar e, se necessário, revogar o acesso a documentos protegidos.|
|Suporte para os dispositivos utilizados mais frequentemente, não apenas computadores Windows|√ [dispositivos suportados](./requirements-client-devices.md) incluem:<br /><br />- Computadores e telemóveis Windows<br /><br />- Computadores Mac<br /><br />- Telemóveis e tablets iOS<br /><br />- Telemóveis e tablets Android|
|Suporte para colaboração empresa-empresa|√ uma vez que o Azure Rights Management é um serviço cloud, não é necessário configurar explicitamente fidedignidades com outras organizações para poder partilhar conteúdo protegido com eles. Se estas já possuírem um Office 365 ou um diretório do Azure AD, a colaboração entre organizações automaticamente é suportada. Caso contrário, os utilizadores podem inscrever-se gratuitamente [RMS para indivíduos](rms-for-individuals.md) subscrição ou utilize um Microsoft conta [aplicações que suportam esta autenticação do Azure Information Protection](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents).|
|Suporte para serviços no local, bem como o Office 365|√ Para além de trabalhar [forma totalmente integrada com o Office 365](office-apps-services-support.md), pode também utilizar do Azure Rights Management com os seguintes serviços no local quando implementar a [conector do RMS](deploy-rms-connector.md):<br /><br />- Exchange Server<br /><br />- SharePoint Server<br /><br />-Windows Server a executar a infraestrutura de classificação de ficheiros|
|Ativação fácil|√ Para novas subscrições, a ativação é automática. Para as assinaturas existentes, [ativar o serviço de Rights Management](activate-service.md) requer apenas alguns cliques no portal de gestão. Em alternativa, se preferir o controlo da linha de comandos, apenas dois comandos do PowerShell.|
|Capacidade de dimensionamento na sua organização, conforme necessário|√ uma vez que o Azure Rights Management é executado como um serviço em nuvem com a elasticidade do Azure para aumentar verticalmente e horizontalmente, não tem de aprovisionar ou implementar mais servidores no local.|
|Capacidade para criar políticas simples e flexíveis|√ [proteção modelos personalizados](configure-policy-templates.md) fornecem uma solução rápida e fácil para os administradores aplicarem políticas e para os utilizadores aplicarem o nível correto de proteção para cada documento e restringir o acesso a pessoas dentro de sua organização.<br /><br />Por exemplo, para um documento estratégico à escala da empresa ser partilhado com todos os funcionários, pode aplicar uma política só de leitura a todos os empregados internos. Em seguida, para um documento mais confidencial, tal como um relatório financeiro, pode restringir o acesso a apenas executivos.|
|Suporte abrangente de aplicações|√ Azure Rights Management tem uma integração total com os serviços e aplicativos do Microsoft Office e expande o suporte para outras aplicações utilizando o [cliente Azure Information Protection](./rms-client/aip-client.md ).<br /><br />√ o [SDKs do Azure Information Protection](./develop/developers-guide.md) fornecem aos programadores internos e os fornecedores de software APIs para que escrevam aplicações personalizadas que suportam o Azure Information Protection.<br /><br />Para obter mais informações, veja [Outras aplicações que suportam as APIs do Rights Management](api-support.md).|
|O departamento de TI tem de manter o controlo dos dados|√ as organizações podem optar por gerir as próprias chaves de inquilino e utilizar a "[traga a sua própria chave](plan-implement-tenant-key.md)" solução de (BYOK) e armazenar as chaves de inquilino nos módulos de segurança de Hardware (HSMs).<br /><br />√ Suporte para auditoria e [registo de utilização](log-analyze-usage.md) para que pode analisar informações empresariais, monitorizar abusos e (se tiver uma fuga de informação) efetuar análises forenses.<br /><br />√ o acesso de delegado ao utilizar o [funcionalidade de Superutilizador](configure-super-users.md) garante que o departamento de TI pode sempre aceder a conteúdo protegido, mesmo que um documento foi protegido por um funcionário que, em seguida, saia da organização. Em comparação, as soluções de encriptação ponto a ponto arriscam a perda de acesso aos dados da empresa.<br /><br />√ Sincronize [apenas os atributos de diretório do Azure RMS necessita](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized#azure-rms) para suportar uma identidade comum para as suas contas do Active Directory no local, utilizando [uma solução de identidade híbrida](/azure/active-directory/hybrid/), como o Azure AD Ligue-se.<br /><br />√ Ative o início de sessão único sem replicar as palavras-passe para a cloud, através da utilização do AD FS.<br /><br />√ as organizações têm sempre a opção de deixar de utilizar o serviço Azure Rights Management sem perderem o acesso a conteúdo que foi anteriormente protegido pelo Azure Rights Management. Para mais informações acerca das opções de desativação, consulte [Encerrar e desativar o Azure Rights Management](decommission-deactivate.md). Além disso, as organizações que implantaram o Active Directory Rights Management Services (AD RMS) podem [migrar para o serviço Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) sem perderem o acesso aos dados que foram anteriormente protegido pelo AD RMS.|
> [!TIP]
> Se está familiarizado com a versão no local do Rights Management e dos Serviços de Gestão de Direitos do Active Directory (AD RMS), a tabela de comparação apresentada em [Comparar o Azure Rights Management e o AD RMS](compare-on-premise.md) poderá interessar-lhe.

## <a name="security-compliance-and-regulatory-requirements"></a>Requisitos de segurança, conformidade e regulamentação
O Azure Rights Management suporta os seguintes de segurança, conformidade e os requisitos de regulamentação:

√ Utilização de criptografia de norma da indústria e suporte da certificação FIPS 140-2. Para obter mais informações, consulte o [controlos criptográficos utilizados pelo Azure RMS: Algoritmos e comprimentos de chave](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths) informações.

√ centros de suporte para módulos de segurança da Thales Hardware (HSMs) para armazenar a chave de inquilino nos dados do Microsoft Azure. O Azure Rights Management utiliza universos de segurança separados de seus centros de dados na América do Norte, EMEA (Europa, Médio Oriente e África) e Ásia, para que as suas chaves possam ser utilizadas apenas na sua região.

√ possui o seguinte:

-   ISO/IEC 27001:2013 (. / inclui [ISO/IEC 27018](https://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))

-   Certificados SOC 2 SSAE 16/ISAE 3402

-   BAA HIPAA

-   Cláusula Modelo da UE

-   FedRAMP como parte do Azure Active Directory na certificação do Office 365, emitido autoridade de agência FedRAMP emitida pelos HHS

-   PCI DSS de Nível 1

Para obter mais informações acerca destas certificações externas, consulte o [Centro de Fidedignidade do Azure](https://azure.microsoft.com/support/trust-center/compliance/).

## <a name="next-steps"></a>Passos Seguintes

Para obter mais informações técnicas sobre o funcionamento do serviço Azure Rights Management, veja [Como funciona o Azure RMS?](how-does-it-work.md)

