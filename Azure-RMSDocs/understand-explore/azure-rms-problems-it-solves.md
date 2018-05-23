---
title: Problemas resolvidos pelo Azure Rights Management – AIP
description: Conheça os requisitos ou os problemas que a sua organização pode ter e saiba de que forma a tecnologia do Azure RMS os pode resolver.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b551c62d-5ac6-4359-85b3-90693e77b37f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 7d0205628502917d6bf35386d851403a40ed597a
ms.sourcegitcommit: aae04d78ff301921a4e29ac23bd932fb24a83dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/22/2018
---
# <a name="what-problems-does-azure-rms-solve"></a>Que problemas resolve o Azure RMS?

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize a seguinte tabela para identificar os requisitos ou os problemas empresariais que a sua organização pode ter ao proteger documentos e e-mails e para saber de que forma a tecnologia do Azure Rights Management (Azure RMS) os pode resolver.

O Azure RMS é a tecnologia de proteção utilizada pelo [Azure Information Protection](what-is-information-protection.md).

|Requisito ou problema|Resolvido pelo Azure RMS|
|--------------------------|-----------------------|
|Proteger vários tipos de ficheiro|√ Na implementação anterior do Rights Management, só podia proteger ficheiros do Office através da proteção do Rights Management nativa. Agora, a **proteção genérica** que foi primeiro oferecida pela aplicação de partilha Rights Management e agora pelo cliente do Azure Information Protection significa que mais [tipos de ficheiro](../rms-client/client-admin-guide-file-types.md) são suportados.|
|Proteger ficheiros em qualquer lugar|√ Quando um ficheiro está [protegido](../rms-client/client-classify-protect.md), a proteção mantém-se com o ficheiro, mesmo que seja guardado ou copiado para um armazenamento que não esteja sob o controlo do TI, tal como um serviço de armazenamento na cloud.|
|Partilhar informações de forma segura|√ Quando um ficheiro está [protegido](../rms-client/client-classify-protect.md), é seguro partilhá-lo com outras pessoas. Por exemplo, um anexo de um e-mail ou uma ligação para um site do SharePoint. Se as informações confidenciais estiverem numa mensagem de e-mail, pode proteger o e-mail ou simplesmente utilizar a opção Não Reencaminhar no Outlook. <br /><br />A vantagem de anexar um ficheiro protegido, em vez de proteger toda a mensagem de e-mail completa, é que o texto do e-mail não é encriptado, pelo que pode incluir as instruções para a primeira utilização se o e-mail estiver a ser enviado fora da sua organização. Qualquer pessoa pode ler as instruções. No entanto, dado que o documento anexado está protegido, apenas os utilizadores autorizados poderão abri-lo, mesmo que o e-mail ou o documento seja reencaminhado para outras pessoas.|
|Auditoria e monitorização|√ Pode [auditar e monitorizar a utilização](../deploy-use/log-analyze-usage.md) dos seus ficheiros protegidos, mesmo depois de estes ficheiros saírem das imediações da sua organização.<br /><br />Por exemplo, trabalha para a Contoso, Ltd. Está a trabalhar num projeto conjunto com três pessoas da Fabrikam, Inc. Envia a estas três pessoas um documento por e-mail que protege e restringe para só de leitura. A auditoria do Azure Rights Management pode facultar as seguintes informações:<br /><br />- Se as pessoas que especificou na Fabrikam abriram o documento e quando.<br /><br />- Se outras pessoas que não especificou tentaram (e não conseguiram) abrir o documento, talvez porque foi reencaminhado ou guardado numa localização partilhada à qual outros utilizadores podiam aceder.<br /><br />- Se qualquer uma das pessoas especificadas tentou (e não conseguiu) imprimir ou alterar o documento.<br /><br />Além disso, o [site de controlo de documentos](../rms-client/client-track-revoke.md) permite aos utilizadores e administradores controlar e, se necessário, revogar o acesso a documentos protegidos.|
|Suporte para os dispositivos utilizados mais frequentemente, não apenas computadores Windows|√ [Os dispositivos suportados](../get-started/requirements-client-devices.md) incluem:<br /><br />- Computadores e telemóveis Windows<br /><br />- Computadores Mac<br /><br />- Telemóveis e tablets iOS<br /><br />- Telemóveis e tablets Android|
|Suporte para colaboração empresa-empresa|√ Uma vez que o Azure Rights Management é um serviço cloud, não é preciso configurar explicitamente fidedignidades com outras organizações para poder partilhar o conteúdo protegido com elas. Se estas já possuírem um Office 365 ou um diretório do Azure AD, a colaboração entre as organizações é suportada automaticamente. Caso contrário, os utilizadores podem inscrever-se a livre [RMS para indivíduos](rms-for-individuals.md) subscrição ou utilize um Microsoft conta para [aplicações que suportam esta autenticação para o Azure Information Protection](../get-started/secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents).|
|Suporte para serviços no local e Office 365|√ Para além de trabalhar [de forma totalmente integrada com o Office 365](office-apps-services-support.md), também pode utilizar o Azure Rights Management com os seguintes serviços no local quando implementar o [conector RMS](../deploy-use/deploy-rms-connector.md):<br /><br />- Exchange Server<br /><br />- SharePoint Server<br /><br />- Windows Server a executar a Infraestrutura de Classificação de Ficheiros|
|Ativação fácil|√ Para novas subscrições, a ativação é automática. Para subscrições existentes, [ativar o serviço Rights Management](../deploy-use/activate-service.md) requer apenas alguns cliques no portal de gestão. Em alternativa, se preferir o controlo da linha de comandos, apenas dois comandos do PowerShell.|
|Capacidade de dimensionamento na sua organização, conforme necessário|√ Uma vez que o Azure Rights Management é executado como um serviço cloud com a elasticidade do Azure para aumentar verticalmente e horizontalmente, não tem de aprovisionar ou implementar mais servidores no local.|
|Capacidade para criar políticas simples e flexíveis|√ [personalizado modelos proteção](../deploy-use/configure-policy-templates.md) fornecem uma solução rápida e fácil para os administradores aplicarem políticas e para os utilizadores aplicarem o nível correto de proteção para cada documento e restringir o acesso a pessoas dentro da organização.<br /><br />Por exemplo, para um documento estratégico à escala da empresa ser partilhado com todos os funcionários, pode aplicar uma política só de leitura a todos os empregados internos. Em seguida, para um documento mais confidencial, tal como um relatório financeiro, pode restringir o acesso a apenas executivos.|
|Suporte abrangente de aplicações|√ O Azure Rights Management tem uma integração total com as aplicações e serviços do Microsoft Office e expande o suporte a outras aplicações através do [cliente do Azure Information Protection](../rms-client/aip-client.md ).<br /><br />√ Os [SDKs do Azure Information Protection](../develop/developers-guide.md) proporcionam aos programadores internos e aos fornecedores de software APIs para que escrevam aplicações personalizadas que suportam o Azure Information Protection.<br /><br />Para obter mais informações, veja [Outras aplicações que suportam as APIs do Rights Management](api-support.md).|
|O departamento de TI tem de manter o controlo dos dados|√ As organizações podem optar por gerir as suas próprias chaves de inquilino e utilizar a solução "[Traga a Sua Própria Chave](../plan-design/plan-implement-tenant-key.md)" (BYOK) e armazenar a respetiva chave de inquilino nos Módulos de Hardware de Segurança (HSMs).<br /><br />√ Suporte para auditoria e [registo de utilização](../deploy-use/log-analyze-usage.md) para poder analisar informações empresariais, monitorizar abusos e (se tiver uma fuga de informação) proceder à análise forense.<br /><br />√ O acesso delegado através da [funcionalidade de superutilizador](../deploy-use/configure-super-users.md) garante que o departamento de TI pode sempre aceder a conteúdo protegido, mesmo que um documento tenha sido protegido por um funcionário que, entretanto, saia da organização. Em comparação, as soluções de encriptação ponto a ponto arriscam a perda de acesso aos dados da empresa.<br /><br />√ Sincronize [apenas os atributos do diretório de que o Azure RMS necessita](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) para suportar uma identidade comum para as suas contas do Active Directory no local, ao utilizar uma [ferramenta de sincronização de diretórios](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison), como o Azure AD Connect.<br /><br />√ Ative o início de sessão único sem replicar as palavras-passe na cloud, utilizando o AD FS.<br /><br />√ As organizações têm sempre a opção de deixar de utilizar o serviço Azure Rights Management sem perderem o acesso a conteúdo que foi anteriormente protegido pelo Azure Rights Management. Para mais informações acerca das opções de desativação, consulte [Encerrar e desativar o Azure Rights Management](../deploy-use/decommission-deactivate.md). Além disso, as organizações que implementaram os Serviços de Gestão de Direitos do Active Directory (AD RMS) podem [migrar para o serviço Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md) sem perderem o acesso aos dados que foram anteriormente protegidos pelo AD RMS.|
> [!TIP]
> Se está familiarizado com a versão no local do Rights Management e dos Serviços de Gestão de Direitos do Active Directory (AD RMS), a tabela de comparação apresentada em [Comparar o Azure Rights Management e o AD RMS](compare-azure-rms-ad-rms.md) poderá interessar-lhe.

## <a name="security-compliance-and-regulatory-requirements"></a>Requisitos de segurança, conformidade e regulamentação
O Azure Rights Management suporta os seguintes requisitos de segurança, conformidade e regulamentação:

√ Utilização de criptografia de norma da indústria e suporte da certificação FIPS 140-2. Para obter mais informações, consulte [Controlos criptográficos utilizados pelo Azure RMS: comprimentos de chave e algoritmos](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

√ Suporte de Módulos de Hardware de Segurança (HSMs) da Thales para armazenar a sua chave de inquilino nos centros de dados do Microsoft Azure. O Azure Rights Management utiliza universos de segurança separados nos seus centros de dados na América do Norte, EMEA (Europa, Médio Oriente e África) e Ásia, para que as suas chaves possam ser utilizadas apenas na sua região.

√ Possui as seguintes certificações:

-   Norma ISO/IEC 27001:2013 (inclui a norma [ISO/IEC 27018](http://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))

-   Certificados SOC 2 SSAE 16/ISAE 3402

-   BAA HIPAA

-   Cláusula Modelo da UE

-   FedRAMP como parte da certificação do Azure Active Directory no Office 365, Autoridade Operativa da Agência FedRAMP emitida pelos HHS

-   PCI DSS de Nível 1

Para obter mais informações acerca destas certificações externas, consulte o [Centro de Fidedignidade do Azure](http://azure.microsoft.com/support/trust-center/compliance/).

## <a name="next-steps"></a>Próximos passos

Para obter mais informações técnicas sobre o funcionamento do serviço Azure Rights Management, veja [Como funciona o Azure RMS?](how-does-it-work.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]