---
title: Proteção de HYOK para o Azure Information Protection
description: Descrição geral da proteção de HYOK (AD RMS) com o Azure Information Protection, os cenários suportados, limitações, pré-requisitos e recomendações.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/01/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: 5ded2edb2ea3fe05cc09750c4cdb53bc03d5fbae
ms.sourcegitcommit: 87d73477b7ae9134b5956d648c390d2027a82010
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32327471"
---
# <a name="hold-your-own-key-hyok-protection-for-azure-information-protection"></a>Manter a sua própria proteção de chave (HYOK) para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Utilize as seguintes informações para compreender o que espera que é sua própria proteção por chave (HYOK) para o Azure Information Protection, e como é diferente do que a proteção predefinida de baseado na nuvem. Antes de utilizar a proteção de HYOK, certifique-se de que compreende quando é adequado, os cenários suportados, as limitações e requisitos. 

## <a name="cloud-based-protection-vs-hyok"></a>Vs proteção baseada na nuvem. HYOK

Proteger os seus documentos e e-mails mais confidenciais utilizando o Azure Information Protection, fazê-lo, normalmente, ao aplicar uma chave de acesso baseado na nuvem que utiliza a proteção do Azure Rights Management (Azure RMS) para beneficiar do seguinte:

- Não é necessária nenhuma infraestrutura de servidor, o que torna a solução mais rápida e económica para implementar e manter do que uma solução no local.

- Uma partilha mais fácil com parceiros e os utilizadores de outras organizações utilizando a autenticação baseada na cloud.

- Integração sólida com outros serviços do Azure e o Office 365, como pesquisa, visualizadores web, vistas dinâmicas, antimalware, deteção de dados Eletrónicos e Delve.

- Controlo, revogação e notificação por e-mail para documentos confidenciais que tenha partilhado.

Uma chave baseada na nuvem protege os documentos e e-mails da sua organização ao utilizar uma chave privada para a organização que é gerida pela Microsoft (predefinição) ou gerida por si (a "traga a sua própria chave" ou cenário BYOK). Para obter mais informações sobre as opções de chave de inquilino, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md).

Documentos e e-mails que proteger foi possível armazenar na nuvem ou no local. Para obter mais informações sobre como funciona o o processo de proteção para esta chave baseado na nuvem, consulte [que é o Azure Rights Management?](../understand-explore/what-is-azure-rms.md )

Serviços do Office 365 e aplicações baseadas na nuvem para o seu inquilino podem integrar com o Azure Information Protection, para que funciona de negócio importantes, tais como serviços de pesquisa, indexação, arquivar e antimalware continuem a funcionar de forma totalmente integrada para o conteúdo que está protegida pelo Azure Information Protection. Esta capacidade para ler o conteúdo encriptado nestes cenários é frequentemente referida como "raciocínio através de dados". Por exemplo, é esta capacidade que permite ao Exchange Online desencriptar mensagens de correio eletrónico para análise de software maligno e executar regras de (DLP) de prevenção de perda de dados nos e-mails encriptados.

No entanto, para requisitos de regulamentação, algumas organizações poderão ser necessárias para encriptar o conteúdo com uma chave que está isolada da nuvem. Este isolamento significa que o conteúdo encriptado pode ser lidos apenas por aplicações no local e serviços no local. Esta opção de gestão de chaves é suportada pelo Azure Information Protection, e é referido como "tenha a sua própria chave" ou HYOK. Quando utilizar o Azure Information Protection com HYOK, o seu inquilino tem uma chave baseada na nuvem e uma chave no local.

## <a name="hyok-guidance-and-best-practices"></a>HYOK orientações e melhores práticas

Utilize a proteção de HYOK apenas para os documentos e e-mails que necessitam de ser isolados da nuvem a chave de encriptação. Proteção de HYOK não fornece as vantagens indicadas que obtém quando utiliza a proteção de chaves baseado na nuvem e -acarreta frequentemente "opacidade de dados". Expressão significa que apenas no local dos serviços de aplicações e poderá abrir os dados protegidos de HYOK; aplicações e serviços baseados na nuvem não é possível pelo motivo dados protegidos de HYOK acima.

Mesmo para as organizações que utilizam a proteção de HYOK, é normalmente adequado para um pequeno número de documentos que precisam de ser protegidas. Como orientação, utilizá-lo apenas para documentos e quando corresponderem os seguintes critérios:

- O conteúdo contém a classificação mais elevada na sua organização ("Top segredo") e o acesso é restringido a apenas algumas pessoas

- O conteúdo não está a ser partilhado fora da organização

- O conteúdo apenas consumido na rede interna

Porque a proteção de HYOK é uma opção de configuração de administrador para uma etiqueta, fluxos de trabalho do utilizador permanecerem o mesmo, independentemente se a proteção utiliza uma chave baseada na nuvem ou HYOK.

[Políticas de âmbito](configure-policy-scope.md) são uma boa forma de garantir que apenas os utilizadores que necessitam para aplicar a proteção de HYOK etiquetas que estão configuradas para proteção de HYOK. 

## <a name="supported-scenarios-for-hyok"></a>Cenários suportados de HYOK

Para aplicar a proteção de HYOK, utilize etiquetas do Azure Information Protection. 

A tabela seguinte lista os cenários suportados para proteger conteúdo através da utilização de etiquetas que estão configuradas para HYOK e conteúdo abrir (consumir) que está protegido por HYOK.

|Platform|Aplicação|Suportado|
|----------------------|----------|-----------|
|Windows|Cliente de proteção de informações do Azure com o Office 2016 ou Office 2013 <br /><br />-Word, Excel, PowerPoint|Proteção: Sim<br /><br />Consumo: Sim|
|Windows|Cliente de proteção de informações do Azure com o Office 2016 ou Office 2013 <br /><br />-Outlook|Proteção: Sim<br /><br />Consumo: Sim|
|Windows|Cliente de proteção de informações do Azure com o Explorador de ficheiros|Proteção: Sim <br /><br />Consumo: Sim|
|Windows|Visualizador de proteção de informações do Azure|Proteção: Não aplicável<br /><br />Consumo: Sim|
|Windows|Cliente de proteção de informações do Azure com o PowerShell etiquetagem cmdlets|Proteção: Sim<br /><br />Consumo: Sim|
|Windows|Análise do Azure Information Protection|Proteção: Sim<br /><br />Consumo: Sim|
|Windows|Aplicação de partilha Rights Management|Proteção: não<br /><br />Consumo: Sim|
|MacOS|Office para Mac <br /><br /> -Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: Sim|
|MacOS|Office para Mac<br /><br />-Outlook|Proteção: não<br /><br />Consumo: Sim|
|MacOS|Aplicação de partilha Rights Management|Proteção: não<br /><br />Consumo: Sim|
|iOS|Office Mobile <br /><br />-Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: Sim|
|iOS|Office Mobile <br /><br />-Outlook|Proteção: não<br /><br />Consumo: não|
|iOS|Visualizador de proteção de informações do Azure|Proteção: Não aplicável<br /><br />Consumo: Sim|
|Android|Office Mobile <br /><br />-Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: Sim|
|Android|Office Mobile <br /><br />-Outlook|Proteção: não<br /><br />Consumo: não|
|Android|Visualizador de proteção de informações do Azure|Proteção: Não aplicável<br /><br />Consumo: Sim|
|Web|Outlook na web|Proteção: não<br /><br />Consumo: não|
|Web|Office Online<br /><br />-Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: não|
|Universal|Aplicações Universal do Office<br /><br />-Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: não|


## <a name="additional-limitations-when-using-hyok"></a>Limitações adicionais ao utilizar HYOK

Além disso, utilizar a proteção de HYOK com etiquetas do Azure Information Protection tem as seguintes limitações:

- Não suporta o Office 2010 ou o Office 2007.

- Serviços do Office 365 e outros serviços online não poderá desencriptar protegidos de HYOK documentos e e-mails para inspecionar os conteúdos e tomar medidas. Esta limitação expande a protegidos de HYOK documentos e e-mails que foram protegidos com o conector Rights Management. 
    
    Esta perda da funcionalidade de correio eletrónico protegidos de HYOK inclui scanners de software maligno, soluções de prevenção (DLP) de perda de dados, as regras de encaminhamento de correio, registo em diário, deteção de dados Eletrónicos, arquivo soluções e do Exchange ActiveSync. Além disso, os utilizadores não compreender por que motivo alguns dispositivos não é possível abrir os e-mails protegidos de HYOK, e isto pode resultar em chamadas para o suporte técnico. Devido a estas muitas limitações, não recomendamos que utilize proteção de HYOK para e-mails.

## <a name="implementing-hyok"></a>Implementar HYOK

HYOK é suportado pelo Azure Information Protection quando tem uma implementação do Active Directory Rights Management Services (AD RMS) com os requisitos documentados na secção seguinte. Neste cenário, as políticas de direitos de utilização e a chave privada da organização que protege estas políticas são geridas e mantidas no local, enquanto a política do Azure Information Protection para etiquetagem e classificação permanece gerida e armazenada no Azure. 

Não confunda HYOK e Azure Information Protection com a utilização de uma implementação completa do AD RMS e Azure Information Protection, ou como uma alternativa ao migrar o AD RMS para o Azure Information Protection. HYOK só é suportado pelo aplicar etiquetas, não oferece paridade de funcionalidades com o AD RMS e não suporta todas as configurações de implementação de AD RMS:

- Para obter mais informações sobre os cenários que HYOK suporta para proteger conteúdo e consumir conteúdo protegido, consulte o [suportado cenários para HYOK](#supported-scenarios-for-hyok) secção.

- Para obter instruções de migração do AD RMS, consulte [migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

- Para obter mais informações sobre os requisitos de implementação do AD RMS, consulte a secção seguinte.

### <a name="requirements-for-ad-rms-to-support-hyok"></a>Requisitos do AD RMS para suportar HYOK

Uma implementação de AD RMS têm de cumprir os seguintes requisitos para fornecer proteção de HYOK para etiquetas do Azure Information Protection.

- Configuração do AD RMS:
    
    - Versão mínima do Windows Server 2012 R2: necessária para ambientes de produção, mas para fins de teste ou avaliação, pode utilizar uma versão mínima do Windows Server 2008 R2 com o Service Pack 1.
    
    - Uma das seguintes topologias:
        
        - Floresta única com um único cluster de raiz de AD RMS. 
        
        - Várias florestas com clusters independentes de raiz de AD RMS e os utilizadores não têm acesso ao conteúdo que está protegido pelos utilizadores nas outras florestas.
        
        - Clusters de várias florestas com o AD RMS em cada um deles. Cada cluster de AD RMS partilhas de um URL de licenciamento que aponta para o mesmo cluster de AD RMS. Neste cluster de AD RMS, tem de importar todos os certificados de domínio (TUD) de utilizadores fidedignos de todos os outros clusters de AD RMS. Para obter mais informações sobre esta topologia, consulte [domínio de utilizador fidedigno] (https://technet.microsoft.com/library/dd983944(v=ws.10\). aspx).
        
    Quando tiver vários clusters de AD RMS em florestas diferentes, elimine as etiquetas na política de global que aplicarem a proteção de HYOK (AD RMS) e configurar um [âmbito política](configure-policy-scope.md) para cada cluster. Em seguida, atribua utilizadores para cada cluster a respetiva política de âmbito, certificando-se de que não utilize grupos que resultariam num utilizador que está a ser atribuído a mais de uma política no âmbito. O resultado deve ser que cada utilizador tem as etiquetas para um cluster AD RMS. 
    
    - [Modo criptográfico 2](https://technet.microsoft.com/library/hh867439.aspx): pode confirmar o modo ao verificar as propriedades de cluster de AD RMS, **geral** separador.
    
    - Cada servidor do AD RMS está configurado para o URL de certificação. [Instruções](#configuring-ad-rms-servers-to-locate-the-certification-url) 
    
    - Um ponto de ligação de serviço (SCP) não pode estar registado no Active Directory: não são utilizados SCPs ao utilizar a proteção do AD RMS com o Azure Information Protection. 
    
        - Se tiver registado um SCP na implementação do AD RMS, tem de removê-lo para que a [deteção do serviço](../rms-client/client-deployment-notes.md#rms-service-discovery) seja bem-sucedida para a proteção do Azure Rights Management. 
        
        - Se estiver a instalar um novo cluster de AD RMS para HYOK, ignore o passo para registar o SCP durante a configuração do nó primeiro. Para cada nó adicional, certifique-se de que o servidor está configurado para o URL de certificação antes de adicionar a função de AD RMS e aderirem ao cluster existente.
    
    - Os servidores do AD RMS estão configurados para utilizar SSL/TLS com um certificado x.509 válido que seja considerado fidedigno pelos clientes ligados: necessários para ambientes de produção, mas não para fins de teste ou avaliação.
    
    - Modelos de direitos configurados.
    
    - Não configurado para IRM do Exchange.
    
    - Para dispositivos móveis e computadores Mac: O [Active Directory extensão gestão de direitos serviços móveis dispositivo](https://technet.microsoft.com/library/dn673574.aspx) está instalado e configurado.

- Sincronização de diretórios está configurada entre o Active Directory no local e o Azure Active Directory e os utilizadores que irão utilizar a proteção de HYOK estão configurados para o início de sessão único.

- Se partilhar documentos ou e-mails protegidos pelo HYOK com outras pessoas fora da sua organização: AD RMS está configurado para confianças explicitamente definidas numa relação ponto a ponto direta com as outras organizações utilizando fidedigno domínios de utilizadores (TUDs) ou confianças federadas criadas utilizando os serviços de Federação do Active Directory (AD FS).

- Os utilizadores têm uma versão do Office que é o Office 2016 Professional Plus ou Office 2013 Professional Plus com Service Pack 1, com Windows 7 Service Pack 1 ou posterior. Tenha em atenção que o Office 2010 e o Office 2007 não são suportados neste cenário.
    
    - Para o Office 2016, Microsoft Installer (. msi)-com base em edição: instalou [atualizar 4018295 para o Microsoft Office 2016, que foram lançadas nos 6 de Março de 2018](https://support.microsoft.com/en-us/help/4018295/march-6-2018-update-for-office-2016-kb4018295).

> [!IMPORTANT]
> Para cumprir a certeza elevada oferecida que oferece proteção de HYOK, é recomendável que os servidores do AD RMS não estejam localizados no seu DMZ e sejam utilizados pelo apenas dispositivos geridos. 
> 
> Recomendamos também que o cluster do AD RMS utilize um módulo de segurança de hardware (HSM), para que a chave privada do Certificado de Licenciante para Servidor (SLC) não possa ser exposta ou roubada caso a sua implementação do AD RMS seja alguma vez violada ou comprometida. 

Para obter informações de implementação e instruções para o AD RMS, veja [Serviços de Gestão de Direitos do Active Directory](https://technet.microsoft.com/library/hh831364.aspx) na biblioteca do Windows Server. 


### <a name="configuring-ad-rms-servers-to-locate-the-certification-url"></a>Configurar servidores do AD RMS para localizar o URL de certificação

1. Em cada servidor do AD RMS no cluster, crie a entrada de registo seguinte:

    `Computer\HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\GICURL = "<string>"`
    
    Para o \<valor da cadeia >, especifique um dos seguintes:
    
    - Para utilizar SSL/TLS clusters de AD RMS:

            https://<cluster_name>/_wmcs/certification/certification.asmx
    
    - Para AD RMS clusters não utilizar SSL/TLS (redes apenas teste):
        
            http://<cluster_name>/_wmcs/certification/certification.asmx

2. Reinicie o IIS.

### <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Localizar as informações para especificar a proteção do AD RMS com uma etiqueta do Azure Information Protection

Quando configurar uma etiqueta para **HYOK (AD RMS)** proteção, tem de especificar o URL de licenciamento do cluster do AD RMS. Além disso, tem de especificar a um modelo que configurou para conhecer as permissões conceder aos utilizadores ou permitir que os utilizadores a definir as permissões e os utilizadores. 

Pode encontrar o GUID do modelo e licenciamento valores do URL da consola de serviços de gestão de direitos do Active Directory:

- Para localizar um GUID do modelo: expanda o cluster e clique em **modelos de política de direitos**. A partir das informações em **Modelos de Política de Direitos Distribuídos**, pode copiar o GUID do modelo que pretende utilizar. Por exemplo: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Para localizar o URL de licenciamento: clique no nome do cluster. A partir das informações em **Detalhes do Cluster**, copie o valor de **Licenciamento** menos a cadeia **/_wmcs/licensing**. Por exemplo: https://rmscluster.contoso.com 
    
    Se tiver um valor de licenciamento de extranet, bem como um valor de licenciamento de intranet e forem diferentes: especifique o valor de extranet apenas se for partilhar documentos ou e-mails protegidos com parceiros que definiu com confianças ponto a ponto explícitas. Caso contrário, utilize o valor de intranet e certifique-se de que todos os computadores cliente que utilizam a proteção do AD RMS com o Azure Information Protection se ligam através de uma ligação de intranet (por exemplo, computadores remotos que utilizam uma ligação VPN).


## <a name="next-steps"></a>Próximos passos

Para configurar uma etiqueta para a proteção de HYOK, consulte [como configurar uma etiqueta para a proteção Rights Management](../deploy-use/configure-policy-protection.md). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]