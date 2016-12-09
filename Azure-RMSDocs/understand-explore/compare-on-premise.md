---
title: Comparar o Azure Information Protection e o AD RMS | Azure Information Protection
description: "Se conhecer ou se tiver implementado anteriormente os Serviços de Gestão de Direitos do Active Directory (AD RMS), é possível que se pergunte como o Azure Information Protection se compara em termos de funcionalidade e requisitos."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/04/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cf9dba0e6e194e4613f715496f79aa9fdb2fe597
ms.openlocfilehash: c649534dc43742d46de4d9044495c85ce734aa80


---

# <a name="comparing-azure-information-protection-and-ad-rms"></a>Comparar o Azure Information Protection e o AD RMS

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Office 365*

Se conhecer ou se tiver implementado anteriormente os Serviços de Gestão de Direitos do Active Directory (AD RMS), é possível que se pergunte como o Azure Information Protection se compara em termos de funcionalidade e requisitos como uma solução de proteção de informações.

Algumas das diferenças principais do Azure Information Protection:

- **Não é necessária nenhuma infraestrutura de servidor**: o Azure Information Protection não necessita dos servidores adicionais e dos certificados PKI de que o AD RMS necessita, porque o Microsoft Azure trata disso por si. Isto torna a solução em nuvem mais rápida de implementar e mais fácil de manter.

- **Autenticação baseada na nuvem**: o Azure Information Protection utiliza o Azure AD para autenticação – tanto para utilizadores internos como para utilizadores de outras organizações. Isto significa que os utilizadores móveis podem ser autenticados mesmo quando não estiverem ligados à sua rede interna e que é mais fácil partilhar conteúdo protegido com utilizadores de outras organizações. Muitas organizações já possuem contas de utilizador no Azure AD porque executam serviços do Azure ou possuem o Office 365. Caso contrário, o RMS para indivíduos permite que os utilizadores criem uma conta gratuita. A partilha de conteúdo protegido pelo AD RMS com outra organização exige que configure fidedignidades explícitas com cada organização.

- **Suporte incorporado para dispositivos móveis**: não são necessárias alterações de implementação para que o Azure RMS suporte dispositivos móveis e computadores Mac. Para suportar estes dispositivos com o AD RMS, tem de instalar a extensão de dispositivo móvel, configurar o AD FS para federação e criar registos adicionais para o seu serviço DNS público.

- **Modelos predefinidos**: o Azure Information Protection cria dois modelos predefinidos assim que o serviço de proteção é ativado, o que faz com que seja muito fácil começar a proteger dados importantes imediatamente. Não existem modelos predefinidos para o AD RMS.

- **Modelos departamentais**: o Azure Information Protection suporta modelos departamentais como uma definição de configuração para modelos adicionais que crie. Esta definição permite-lhe especificar os utilizadores que veem o modelo nas respetivas aplicações cliente (por exemplo, aplicações do Office), facilitando-lhes a seleção da política correta que definir para diferentes grupos de utilizadores. O AD RMS não suporta modelos departamentais.

- **Controlo de documentos, revogação e notificação por e-mail**: o Azure Information Protection suporta estas funcionalidades com a aplicação de partilha RMS, ao passo que o AD RMS não.

- **Classificação e etiquetagem**: o Azure Information Protection suporta estas funcionalidades com a barra do Azure Information Protection que está integrada nas aplicações do Office, ao passo que o AD RMS não.


Além disso, uma vez que o Azure Information Protection é um serviço em nuvem, pode disponibilizar novas funcionalidades e correções mais rapidamente do que uma solução baseada num servidor no local. Não existem quaisquer funcionalidades novas planeadas para o AD RMS no Windows Server 2016.

Para obter mais detalhes e outras diferenças, utilize a seguinte tabela para ver uma comparação lado a lado das funcionalidades e vantagens do Azure Information Protection e do AD RMS. Se tiver dúvidas de comparação específicas em relação à segurança, consulte a secção [Controlos criptográficos para assinatura e encriptação](#cryptographic-controls-for-signing-and-encryption) neste artigo.

> [!NOTE]
> Para facilitar esta comparação, algumas destas informações são repetidas com base nos [Requisitos do Azure Information Protection](../get-started/requirements-azure-rms.md). Utilize essa origem para obter informações mais específicas sobre o suporte e as versões do [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Suporta as capacidades de Gestão de Direitos de Informação (IRM) nos serviços do Microsoft Online, como o Exchange Online e o SharePoint Online, bem como o Office 365.<br /><br />Também suporta produtos de servidor da Microsoft no local, como o Exchange Server, o SharePoint Server e servidores de ficheiros que utilizam o Windows Server e a Infraestrutura de Classificação de Ficheiros (FCI).|Suporta produtos de servidor da Microsoft no local, como o Exchange Server, o SharePoint Server e servidores de ficheiros que utilizam o Windows Server e a Infraestrutura de Classificação de Ficheiros (FCI).|
|Permite a fidedignidade implícita entre as organizações e os utilizadores em qualquer organização. Isto significa que o conteúdo protegido pode ser partilhado entre os utilizadores dentro da mesma organização ou entre organizações quando os utilizadores têm o [!INCLUDE[o365_1](../includes/o365_1_md.md)] ou o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], ou quando os utilizadores se inscrevem no RMS para indivíduos.|As fidedignidades têm de ser explicitamente definidas numa relação direta de ponto a ponto entre duas organizações ao utilizar domínios de utilizadores fidedignos (TUDs) ou fidedignidades federadas que cria ao utilizar Serviços de Federação do Active Directory (AD FS).|
|Fornece dois modelos de política de direitos predefinidos que restringem o acesso do conteúdo à sua própria organização. Um modelo que proporciona a visualização só de leitura de conteúdo protegido e outro que proporciona permissões de escrita ou modificação no conteúdo protegido.<br /><br />Também pode criar os seus modelos personalizados, que incluem modelos departamentais que estão visíveis apenas para um subconjunto de utilizadores. Para mais informações, consulte [Configurar modelos personalizados para o serviço Azure Rights Management](../deploy-use/configure-custom-templates.md).<br /><br />Além disso, os utilizadores podem definir o seu próprio conjunto de permissões se os modelos não forem suficientes.|Não existem modelos de política de direitos predefinidos. Tem de criá-los e, em seguida, distribuí-los. Para mais informações, consulte [Considerações sobre os Modelos de Política do AD RMS](http://go.microsoft.com/fwlink/?LinkId=154765).<br /><br />Além disso, os utilizadores podem definir o seu próprio conjunto de permissões se os modelos não forem suficientes.|
|A versão mínima suportada do Microsoft Office é o Office 2010, que requer a [aplicação de partilha RMS](../rms-client/sharing-app-windows.md).<br /><br />Microsoft Office para Mac:<br /><br />- Microsoft Office para Mac 2016: suportado<br /><br />- Microsoft Office para Mac 2011: não suportado|A versão mínima suportada do Microsoft Office é o Office 2007.<br /><br />Microsoft Office para Mac:<br /><br />- Microsoft Office para Mac 2016: suportado<br /><br />- Microsoft Office para Mac 2011: suportado|
|Suporta a [aplicação de partilha RMS](../rms-client/sharing-app-windows.md) para Windows, computadores Mac e dispositivos móveis.<br /><br />Além disso, a aplicação de partilha RMS suporta o seguinte:<br /><br />- A partilha com pessoas noutra organização.<br /><br />- A notificação por e-mail, que informa o remetente quando alguém tenta abrir um anexo protegido.<br /><br />- Um site de controlo de documentos para utilizadores, que inclui a capacidade para revogar um documento.|Suporta a [aplicação de partilha RMS](../rms-client/sharing-app-windows.md) para Windows, computadores Mac e dispositivos móveis. No entanto, a partilha não suporta a partilha com pessoas noutra organização, a notificação por e-mail ou o site de controlo de documentos, nem a capacidade para os utilizadores revogarem documentos.|
|Todos os tipos de ficheiro podem ser protegidos com [proteção nativa ou genérica](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection--native-and-generic) quando utiliza a aplicação de partilha RMS.<br /><br />Para outras aplicações, consulte a tabela em [Aplicações que suportam a proteção de dados do Azure Rights Management](../get-started/requirements-applications.md).|Todos os tipos de ficheiro podem ser protegidos com [proteção nativa ou genérica](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection--native-and-generic) quando utiliza a aplicação de partilha RMS.<br /><br />Para outras aplicações, consulte a tabela em [Aplicações que suportam a proteção de dados do Azure Rights Management](../get-started/requirements-applications.md).|
|A versão mínima suportada do cliente Windows é o Windows 7.|A versão mínima suportada do cliente Windows é o Windows Vista Service Pack 2.|
|O suporte de dispositivos móveis inclui Windows Phone, Android, iOS e Windows RT.<br /><br />O suporte de e-mail através da IRM do Exchange ActiveSynct também é suportado em todas as plataformas de dispositivos móveis que suportem este protocolo.|O suporte de dispositivos móveis inclui Windows Phone, Android, iOS e Windows RT, e necessita da [Extensão de Dispositivos Móveis dos Serviços de Gestão de Direitos do Active Directory](http://technet.microsoft.com/library/dn673574.aspx).<br /><br />O suporte de e-mail através da IRM do Exchange ActiveSync é suportado em todas as plataformas de dispositivos móveis que suportem este protocolo.|
|Suporta autenticação multifator (MFA) para computadores e dispositivos móveis.<br /><br />Para mais informações, consulte [A autenticação multifator (MFA) e o Azure Information Protection](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-information-protection).|Suporta a autenticação de smart cards se o IIS estiver configurado para solicitar certificados.|
|Suporta o Modo Criptográfico 2 sem configuração adicional, que proporciona uma segurança reforçada para comprimentos de chaves e algoritmos de encriptação.<br /><br />Para mais informações, consulte a secção [Controlos criptográficos para assinatura e encriptação](#cryptographic-controls-for-signing-and-encryption) neste artigo e [Modos Criptográficos do AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|Suporta o Modo Criptográfico 1 por predefinição e requer configuração adicional para suportar o Modo Criptográfico 2 para reforçar a segurança.<br /><br />Para mais informações, consulte a secção [Controlos criptográficos para assinatura e encriptação](#cryptographic-controls-for-signing-and-encryption) neste artigo e [Modos Criptográficos do AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|
|Suporta a migração do AD RMS e, se necessário, para o AD RMS:<br /><br />- [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Desativar o Azure Information Protection](../deploy-use/decommission-deactivate.md)|Suporta a migração de e para o Azure Information Protection:<br /><br />- [Desativar o Azure Rights Management](../deploy-use/decommission-deactivate.md)<br /><br />- [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)|
|Necessita de uma licença do Azure Information Protection para proteger conteúdo. Não é necessária nenhuma licença do Azure Information Protection para consumir conteúdos que tenham sido protegidos pelo Azure Information Protection (inclui utilizadores de outra organização).<br /><br />Para mais informações, consulte a [lista de funcionalidades](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) no site do Azure Information Protection.|Necessita de uma licença RMS para proteger conteúdo e consumir conteúdo que tenha sido protegido pelo AD RMS.<br /><br />Para obter mais informações sobre o licenciamento do AD RMS, consulte [Licenças de Acesso de Cliente e Licenças de Gestão](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx) para obter informações gerais, mas contacte o seu parceiro da Microsoft ou o representante da Microsoft para obter informações específicas.|

## <a name="cryptographic-controls-for-signing-and-encryption"></a>Controlos criptográficos para assinatura e encriptação
O Azure Information Protection utiliza sempre RSA 2048 para a criptografia de todas as chaves públicas e SHA 256 para as operações de assinatura. Em comparação, o AD RMS suporta RSA 1024 e RSA 2048 e SHA 1 ou SHA 256 para operações de assinatura.

O Azure Information Protection e o AD RMS utilizam AES 128 para a encriptação simétrica.

O Azure Information Protection está em conformidade com FIPS 140-2 se a sua chave de inquilino for criada e gerida pela Microsoft (predefinição) ou se gerir a sua própria chave de inquilino (a solução BYOK). Para mais informações sobre a gestão da chave de inquilino, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md).

## <a name="next-steps"></a>Passos seguintes
Se quer migrar do AD RMS para o Azure Information Protection, consulte [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)





<!--HONumber=Nov16_HO1-->

