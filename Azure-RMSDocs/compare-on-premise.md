---
title: Comparar o Azure Information Protection e o AD RMS
description: Se conhecer ou se tiver implementado anteriormente os Serviços de Gestão de Direitos do Active Directory (AD RMS), é possível que se pergunte como o Azure Information Protection se compara em termos de funcionalidade e requisitos.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a5bf7bd4a4d82c40346694d243403ea2684174d9
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39489302"
---
# <a name="comparing-azure-information-protection-and-ad-rms"></a>Comparar o Azure Information Protection e o AD RMS

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Se conhecer ou se tiver implementado anteriormente os Serviços de Gestão de Direitos do Active Directory (AD RMS), é possível que se pergunte como o Azure Information Protection se compara em termos de funcionalidade e requisitos como uma solução de proteção de informações.

Algumas das diferenças principais do Azure Information Protection:

- **É necessária nenhuma infraestrutura servidor**: Azure Information Protection não necessita dos servidores adicionais e certificados PKI que o AD RMS necessita, porque o Microsoft Azure trata-se um deles para. Isto torna a solução na cloud mais rápida de implementar e mais fácil de manter.

- **Autenticação baseada na cloud**: o Azure Information Protection utiliza o Azure AD para autenticação – tanto para utilizadores internos como para utilizadores de outras organizações. Isto significa que os utilizadores móveis podem ser autenticados mesmo quando não estiverem ligados à sua rede interna e que é mais fácil partilhar conteúdo protegido com utilizadores de outras organizações. Muitas organizações já possuem contas de utilizador no Azure AD porque executam serviços do Azure ou possuem o Office 365. Mas se não, o RMS para indivíduos permite aos utilizadores criar uma conta gratuita ou uma conta Microsoft pode ser utilizada para [aplicações que suportam esta autenticação do Azure Information Protection](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents). A partilha de conteúdo protegido pelo AD RMS com outra organização exige que configure fidedignidades explícitas com cada organização.

- **Suporte incorporado para dispositivos móveis**: não são necessárias alterações de implementação para que o Azure RMS suporte dispositivos móveis e computadores Mac. Para suportar estes dispositivos com o AD RMS, tem de instalar a extensão de dispositivo móvel, configurar o AD FS para federação e criar registos adicionais para o seu serviço DNS público.

- **Modelos predefinidos**: Azure Information Protection cria dois modelos predefinidos assim que o serviço de proteção é ativado, o que torna mais fácil começar a proteger dados importantes imediatamente. Não existem modelos predefinidos para o AD RMS.

- **Modelos departamentais**: o Azure Information Protection suporta modelos departamentais como uma definição de configuração para modelos adicionais que crie. Esta configuração permite-lhe especificar um subconjunto de utilizadores para ver modelos específicos nas respetivas aplicações cliente. Limitar o número de modelos que os utilizadores veem torna mais fácil para selecionar a política correta que definir para diferentes grupos de utilizadores. O AD RMS não suporta modelos departamentais.

- **Controlo e revogação de documentos**: o Azure Information Protection suporta estas funcionalidades com o cliente do Azure Information Protection, ao passo que o AD RMS não.

- **Classificação e etiquetagem**: o Azure Information Protection suporta estas funcionalidades com o cliente do Azure Information Protection que está integrado nas aplicações do Office e no Explorador de Ficheiros, ao passo que o AD RMS não.


Além disso, uma vez que o Azure Information Protection é um serviço na cloud, pode disponibilizar novas funcionalidades e correções mais rapidamente do que uma solução baseada num servidor no local. Não existem quaisquer funcionalidades novas planeadas para o AD RMS no Windows Server 2016.

Para obter mais detalhes e outras diferenças, utilize a seguinte tabela para ver uma comparação lado a lado das funcionalidades e vantagens do Azure Information Protection e do AD RMS. Se tiver dúvidas de comparação específicas em relação à segurança, consulte a secção [Controlos criptográficos para assinatura e encriptação](#cryptographic-controls-for-signing-and-encryption) neste artigo.

> [!NOTE]
> Para facilitar esta comparação, algumas destas informações são repetidas com base nos [Requisitos do Azure Information Protection](requirements.md). Utilize essa origem para as informações mais específicas sobre o suporte e as versões do Azure Rights Management.

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Suporta as capacidades de Gestão de Direitos de Informação (IRM) nos serviços do Microsoft Online, como o Exchange Online e o SharePoint Online, bem como o Office 365.<br /><br />Também suporta produtos de servidor da Microsoft no local, como o Exchange Server, o SharePoint Server e servidores de ficheiros que utilizam o Windows Server e a Infraestrutura de Classificação de Ficheiros (FCI).|Suporta produtos de servidor da Microsoft no local, como o Exchange Server, o SharePoint Server e servidores de ficheiros que utilizam o Windows Server e a Infraestrutura de Classificação de Ficheiros (FCI).|
|Permite a colaboração segura em documentos com qualquer organização que também utiliza o Azure AD para autenticação automaticamente. Isso significa que as organizações podem proteger documentos que partilham internamente ou com outras organizações.|Colaboração segura em documentos fora da organização necessita de relações de confiança de autenticação para ser explicitamente definidas numa relação ponto a ponto direta entre duas organizações. Tem de configurar qualquer um dos domínios de utilizadores fidedignos (TUDs) ou confianças cria ao utilizar os serviços de Federação do Active Directory (AD FS) federadas.|
|Envie um e-mail protegido (opcionalmente, com os anexos de documento do Office que são automaticamente protegidos) aos utilizadores quando não existe nenhuma relação de confiança de autenticação. Este cenário se tornou possível com o federação com fornecedores de redes sociais ou de um navegador da web e de código de acesso Monouso para visualização.|Não suporta o envio de e-mail protegido quando não existe nenhuma relação de confiança de autenticação.|
|Fornece dois modelos de política de direitos predefinidos que restringem o acesso do conteúdo à sua própria organização. Um modelo que proporciona a visualização só de leitura de conteúdo protegido e outro que proporciona permissões de escrita ou modificação no conteúdo protegido.<br /><br />Também pode criar seus próprios modelos personalizados, que incluem modelos departamentais que estão visíveis para apenas um subconjunto de utilizadores. Para obter mais informações, consulte [configurando e gerenciando modelos do Azure Information Protection](configure-policy-templates.md).<br /><br />Além disso, os utilizadores podem definir o seu próprio conjunto de permissões se os modelos não forem suficientes.|Existem não existem modelos predefinidos; tem de criar e, em seguida, distribuir seus próprios modelos. Para mais informações, consulte [Considerações sobre os Modelos de Política do AD RMS](http://go.microsoft.com/fwlink/?LinkId=154765).<br /><br />Além disso, os utilizadores podem definir o seu próprio conjunto de permissões se os modelos não forem suficientes.|
|A versão mínima suportada do Microsoft Office é o Office 2010, que requer o [cliente do Azure Information Protection](./rms-client/aip-client.md) ou a aplicação de partilha RMS.<br /><br />Microsoft Office para Mac:<br /><br />- Microsoft Office para Mac 2016: suportado<br /><br />- Microsoft Office para Mac 2011: não suportado|A versão mínima suportada do Microsoft Office é o Office 2007.<br /><br />Microsoft Office para Mac:<br /><br />- Microsoft Office para Mac 2016: suportado<br /><br />- Microsoft Office para Mac 2011: suportado|
|Suporta o [cliente do Azure Information Protection](./rms-client/aip-client.md) para Windows, iOS e Android. Computadores Mac e Windows Phone continuam a ser suportada pela aplicação de partilha RMS.<br /><br />Além disso, o cliente do Azure Information Protection suporta o seguinte:<br /><br />- A partilha com pessoas noutra organização.<br /><br />- Um site de controlo de documentos para utilizadores, que inclui a capacidade para revogar um documento.|Suporta o [cliente do Azure Information Protection](./rms-client/aip-client.md) para Windows, iOS e Android. Os computadores Mac e dispositivos Windows Phone continuam a ser suportados pela aplicação de partilha RMS. No entanto, a partilha não suporta a partilha com pessoas noutra organização ou o site de controlo de documentos, nem a capacidade para os utilizadores revogarem documentos.|
|A maioria dos [tipos de ficheiro](./rms-client/client-admin-guide-file-types.md) pode ser classificada e protegida ao utilizar o cliente do Azure Information Protection.<br /><br />Para outras aplicações, consulte a tabela em [Aplicações que suportam a proteção de dados do Azure Rights Management](./requirements-applications.md).|A maioria dos [tipos de ficheiro](./rms-client/client-admin-guide-file-types.md) pode ser protegida ao utilizar o cliente do Azure Information Protection.<br /><br />Para outras aplicações, consulte a tabela em [Aplicações que suportam a proteção de dados do Azure Rights Management](./requirements-applications.md).|
|A versão mínima suportada do cliente Windows é o Windows 7 SP1.|A versão mínima suportada do cliente Windows é o Windows 7 SP1.|
|O suporte de dispositivos móveis inclui Windows Phone, Android, iOS e Windows RT.<br /><br />O suporte de e-mail através da IRM do Exchange ActiveSynct também é suportado em todas as plataformas de dispositivos móveis que suportem este protocolo.|O suporte de dispositivos móveis inclui Windows Phone, Android, iOS e Windows RT, e necessita da [Extensão de Dispositivos Móveis dos Serviços de Gestão de Direitos do Active Directory](http://technet.microsoft.com/library/dn673574.aspx).<br /><br />O suporte de e-mail através da IRM do Exchange ActiveSync é suportado em todas as plataformas de dispositivos móveis que suportem este protocolo.|
|Suporta autenticação multifator (MFA) para computadores e dispositivos móveis.<br /><br />Para mais informações, consulte [A autenticação multifator (MFA) e o Azure Information Protection](./requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-information-protection).|Suporta a autenticação de smart cards se o IIS estiver configurado para solicitar certificados.|
|Suporta o Modo Criptográfico 2 sem configuração adicional, que proporciona uma segurança reforçada para comprimentos de chaves e algoritmos de encriptação.<br /><br />Para mais informações, consulte a secção [Controlos criptográficos para assinatura e encriptação](#cryptographic-controls-for-signing-and-encryption) neste artigo e [Modos Criptográficos do AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|Suporta o Modo Criptográfico 1 por predefinição e requer configuração adicional para suportar o Modo Criptográfico 2 para reforçar a segurança.<br /><br />Para mais informações, consulte a secção [Controlos criptográficos para assinatura e encriptação](#cryptographic-controls-for-signing-and-encryption) neste artigo e [Modos Criptográficos do AD RMS](http://go.microsoft.com/fwlink/?LinkId=266659).|
|Suporta a migração do AD RMS e, se necessário, para o AD RMS:<br /><br />- [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Desativar o Azure Information Protection](decommission-deactivate.md)|Suporta a migração de e para o Azure Information Protection:<br /><br />- [Desativar o Azure Rights Management](decommission-deactivate.md)<br /><br />- [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)|
|Precisa de uma licença do Azure Information Protection ou do Azure Rights Management com o Office 365 para proteger o conteúdo. É necessária nenhuma licença para consumir conteúdos protegidos pelo Azure Information Protection (. / inclui utilizadores de outra organização).<br /><br />Para mais informações, consulte a [lista de funcionalidades](https://www.microsoft.com/cloud-platform/azure-information-protection-features) no site do Azure Information Protection.|Necessita de uma licença RMS para proteger conteúdo e consumir conteúdo que tenha sido protegido pelo AD RMS.<br /><br />Para obter mais informações sobre o licenciamento do AD RMS, consulte [Licenças de Acesso de Cliente e Licenças de Gestão](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx) para obter informações gerais, mas contacte o seu parceiro da Microsoft ou o representante da Microsoft para obter informações específicas.|

## <a name="cryptographic-controls-for-signing-and-encryption"></a>Controlos criptográficos para assinatura e encriptação
Por predefinição, o Azure Information Protection utiliza RSA 2048 para a criptografia de todas as chaves públicas e SHA 256 para as operações de assinatura. Em comparação, o AD RMS suporta RSA 1024 e RSA 2048 e SHA 1 ou SHA 256 para operações de assinatura.

O Azure Information Protection e o AD RMS utilizam AES 128 para a encriptação simétrica.

O Azure Information Protection está em conformidade com FIPS 140-2 quando o tamanho da chave de inquilino é de 2048 bits, o que é a predefinição quando o serviço Azure Rights Management está ativado. 

Para obter mais informações sobre os controlos criptográficos, veja [Controlos criptográficos utilizados pelo Azure RMS: comprimentos de chave e algoritmos](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).


## <a name="next-steps"></a>Passos Seguintes
Se quer migrar do AD RMS para o Azure Information Protection, consulte [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)

