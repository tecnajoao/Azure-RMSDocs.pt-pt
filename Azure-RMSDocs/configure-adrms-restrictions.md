---
title: Proteção do HYOK para o Azure Information Protection
description: Descrição geral de proteção do HYOK (AD RMS) com o Azure Information Protection, seus cenários suportados, limitações, pré-requisitos e recomendações.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/16/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: d4d653f5244467b29fc2be7d4554d92d035d0f87
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151763"
---
# <a name="hold-your-own-key-hyok-protection-for-azure-information-protection"></a>Manter a proteção da sua própria chave (HYOK) para o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Utilize as seguintes informações para compreender o que contêm a que sua própria proteção por chave (HYOK) é para o Azure Information Protection, e como isso é diferente da proteção padrão com base na cloud. Antes de utilizar a proteção do HYOK, certificar-se de que compreende quando é apropriado, os cenários suportados, as limitações e requisitos. 

## <a name="cloud-based-protection-vs-hyok"></a>Proteção baseada na cloud vs. HYOK

Quando protege os documentos e e-mails mais confidenciais utilizando o Azure Information Protection, normalmente fá-lo através da aplicação de uma chave de acesso baseado na nuvem que utiliza a proteção Azure Rights Management (Azure RMS) para beneficiar do seguinte:

- Não é necessária nenhuma infraestrutura de servidor, o que torna a solução mais rápida e económica para implementar e manter do que uma solução no local.

- Uma partilha mais fácil com parceiros e os utilizadores de outras organizações utilizando a autenticação baseada na cloud.

- Integração total com outros serviços do Azure e o Office 365, como pesquisa, visualizadores web, vistas dinâmicas, antimalware, deteção de dados Eletrónicos e Delve.

- Controlo, revogação e notificação por e-mail para documentos confidenciais que tenha partilhado.

Uma chave com base na cloud protege os documentos e e-mails da sua organização através de uma chave privada para a organização que é gerida pela Microsoft (predefinição) ou gerida por si (o "traga a sua própria chave" ou cenário BYOK). Para obter mais informações sobre as opções de chave de inquilino, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

Documentos e e-mails que protege poderiam ser armazenados na cloud ou no local. Para obter mais informações sobre como funciona o o processo de proteção para esta chave com base na cloud, consulte [o que é o Azure Rights Management?](what-is-azure-rms.md )

Serviços do Office 365 e aplicações baseadas na cloud para o seu inquilino podem integrar com o Azure Information Protection para que as funções empresariais importantes, como serviços de pesquisa, indexação, arquivamento e antimalware continuem a funcionar de forma totalmente integrada para o conteúdo que está protegida pelo Azure Information Protection. Esta capacidade de ler o conteúdo encriptado para esses cenários é frequentemente referida como "raciocínio através de dados". Por exemplo, é esta capacidade que permite o Exchange Online desencriptar mensagens de correio eletrónico de verificação de malware e para executar regras de (DLP) de prevenção de perda de dados nos e-mails encriptados.

No entanto, para requisitos de regulamentação, algumas organizações poderão ser necessário para encriptar o conteúdo com uma chave que é isolada a partir da cloud. Esse isolamento significa que o conteúdo encriptado pode ser lido apenas pela aplicações no local e serviços no local. Esta opção de gestão de chaves é suportada pelo Azure Information Protection, e essa é referida como "tenha a sua própria chave" ou HYOK. Quando utiliza o Azure Information Protection com HYOK, o seu inquilino tem uma chave com base na cloud e uma chave no local.

## <a name="hyok-guidance-and-best-practices"></a>HYOK orientações e melhores práticas

Utilize a proteção do HYOK apenas para os documentos e e-mails que exigem a chave de encriptação estar isolado a partir da cloud. A proteção do HYOK não fornece as vantagens indicadas que obtém quando utiliza a proteção de chaves com base na cloud e, muitas vezes, é fornecido ao custo de "opacidade de dados". Isso significa de frase que apenas no local e serviços de aplicações será capaz de abrir os dados protegidos de HYOK; aplicações e serviços baseados na nuvem não é possível compreender os dados protegidos de HYOK.

Mesmo para as organizações que utilizam a proteção do HYOK, é normalmente adequado para um pequeno número de documentos que precisam ser protegidos. Como orientação, utilizá-lo apenas para documentos e quando eles correspondem a todos os seguintes critérios:

- O conteúdo tem a classificação mais elevada na sua organização ("Confidencial") e o acesso é restringido a apenas algumas pessoas

- O conteúdo não é partilhado fora da organização

- Os conteúdos só serão consumidos na rede interna

Como a proteção do HYOK é uma opção de configuração de administrador para uma etiqueta, fluxos de trabalho de utilizador permanecem iguais, independentemente se a proteção utiliza uma chave com base na cloud ou HYOK.

[Políticas de âmbito](configure-policy-scope.md) são uma boa forma de garantir que apenas os utilizadores que precisam para aplicar a proteção do HYOK verem as etiquetas configuradas para proteção do HYOK. 

## <a name="supported-scenarios-for-hyok"></a>Cenários suportados de HYOK

Para aplicar a proteção do HYOK, utilize etiquetas do Azure Information Protection. 

A tabela seguinte lista os cenários suportados para proteger conteúdo através da utilização de etiquetas que estão configuradas para HYOK e conteúdo de abrir (consumir) de mensagens em fila que é protegido pelo HYOK.

|Platform|Aplicação|Suportado|
|----------------------|----------|-----------|
|Windows|Cliente de proteção de informações do Azure com o Office 2016 e Office 2013 <br /><br />-Word, Excel, PowerPoint|Proteção: Sim<br /><br />Consumo: Sim|
|Windows|Cliente de proteção de informações do Azure com o Office 2016 e Office 2013 <br /><br />-Outlook|Proteção: Sim<br /><br />Consumo: Sim|
|Windows|Cliente de proteção de informações do Azure com o Explorador de ficheiros|Proteção: Sim <br /><br />Consumo: Sim|
|Windows|Visualizador do Azure Information Protection|Proteção: Não aplicável<br /><br />Consumo: Sim|
|Windows|Cliente de proteção de informações do Azure com o PowerShell cmdlets de etiquetagem|Proteção: Sim<br /><br />Consumo: Sim|
|Windows|Scanner do Azure Information Protection|Proteção: Sim<br /><br />Consumo: Sim|
|Windows|Aplicação de partilha Rights Management|Proteção: não<br /><br />Consumo: Sim|
|MacOS|Office para Mac <br /><br /> -Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: Sim|
|MacOS|Office para Mac<br /><br />-Outlook|Proteção: não<br /><br />Consumo: Sim|
|MacOS|Aplicação de partilha Rights Management|Proteção: não<br /><br />Consumo: Sim|
|iOS|Office Mobile <br /><br />-Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: Sim|
|iOS|Office Mobile <br /><br />-Outlook|Proteção: não<br /><br />Consumo: não|
|iOS|Visualizador do Azure Information Protection|Proteção: Não aplicável<br /><br />Consumo: Sim|
|Android|Office Mobile <br /><br />-Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: Sim|
|Android|Office Mobile <br /><br />-Outlook|Proteção: não<br /><br />Consumo: não|
|Android|Visualizador do Azure Information Protection|Proteção: Não aplicável<br /><br />Consumo: Sim|
|Web|Outlook na web|Proteção: não<br /><br />Consumo: não|
|Web|Office Online<br /><br />-Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: não|
|Universal|Aplicações universais do Office<br /><br />-Word, Excel, PowerPoint|Proteção: não<br /><br />Consumo: não|


## <a name="additional-limitations-when-using-hyok"></a>Limitações adicionais ao utilizar HYOK

Além disso, se utilizar a proteção do HYOK com etiquetas do Azure Information Protection tem as seguintes limitações:

- Não suporta versões do Office anterior ao Office 2013.

- Serviços do Office 365 e outros serviços online não será capazes de descriptografar protegida HYOK documentos e e-mails para inspecionar o conteúdo e tomar medidas. Esta limitação se estende a documentos protegidos por HYOK e e-mails que foram protegidos com o conector Rights Management. 
    
    Esta perda de funcionalidade para e-mail com proteção do HYOK inclui scanners de malware, soluções de (DLP) de prevenção de perda de dados, as regras de roteamento de emails, registros no diário, deteção de dados Eletrónicos, arquivamento soluções e do Exchange ActiveSync. Além disso, os utilizadores não compreender por que alguns dispositivos não é possível abrir os e-mails protegidos por HYOK, e isso pode resultar em chamadas para o suporte técnico. Devido a essas limitações muitos, não recomendamos que utilize proteção do HYOK para e-mails.

## <a name="implementing-hyok"></a>Implementando o HYOK

HYOK é suportado pelo Azure Information Protection quando tem uma implementação do Active Directory Rights Management Services (AD RMS) com os requisitos documentados na secção seguinte. Neste cenário, as políticas de direitos de utilização e a chave privada da organização que protege estas políticas são geridas e mantidas no local, enquanto a política do Azure Information Protection para etiquetagem e classificação permanece gerida e armazenada no Azure. 

Não confunda HYOK e Azure Information Protection com o uso de uma implementação completa do AD RMS e Azure Information Protection, ou como uma alternativa ao migrar o AD RMS para o Azure Information Protection. HYOK só é suportada ao aplicar etiquetas, não oferece a paridade de funcionalidades com o AD RMS e não suporta todas as configurações de implementação do AD RMS:

- Para obter mais informações sobre os cenários que suporta o HYOK para proteger conteúdo e consumir conteúdo protegido, consulte a [cenários suportados para HYOK](#supported-scenarios-for-hyok) secção.

- Para obter instruções de migração do AD RMS, consulte [migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

- Para obter mais informações sobre os requisitos de implementação do AD RMS, consulte a secção seguinte.

### <a name="requirements-for-ad-rms-to-support-hyok"></a>Requisitos do AD RMS para suportar o HYOK

Uma implementação do AD RMS têm de cumprir os seguintes requisitos para fornecer proteção do HYOK etiquetas do Azure Information Protection.

- Configuração do AD RMS:
    
    - Versão mínima do Windows Server 2012 R2: necessária para ambientes de produção, mas para fins de teste ou avaliação, pode utilizar uma versão mínima do Windows Server 2008 R2 com o Service Pack 1.
    
    - Uma das seguintes topologias:
        
        - Floresta única com um único cluster de raiz do AD RMS. 
        
        - Várias florestas com clusters independentes de raiz de AD RMS e os utilizadores não têm acesso ao conteúdo protegido pelos utilizadores nas outras florestas.
        
        - Clusters de várias florestas com o AD RMS em cada um deles. Cada cluster do AD RMS compartilha um URL de licenciamento que aponta para o mesmo cluster de AD RMS. Neste cluster de AD RMS, tem de importar todos os certificados de domínio (TUD) de utilizadores fidedignos de todos os outros clusters de AD RMS. Para obter mais informações sobre essa topologia, consulte [domínio de utilizador fidedigno] (https://technet.microsoft.com/library/dd983944(v=ws.10\).aspx).
        
    Quando tiver vários clusters do AD RMS em florestas independentes, elimine quaisquer etiquetas na política global que aplicarem a proteção do HYOK (AD RMS) e configurar uma [política de âmbito](configure-policy-scope.md) para cada cluster. Em seguida, atribua utilizadores para cada cluster a respetiva política de âmbito, certificar-se de que não utilize grupos que resultariam num utilizador que está a ser atribuído a mais do que uma política de âmbito. O resultado deve ser a que cada utilizador tem etiquetas para um cluster AD RMS. 
    
    - [Modo criptográfico 2](https://technet.microsoft.com/library/hh867439.aspx): pode confirmar o modo ao verificar as propriedades de cluster de AD RMS **gerais** separador.
    
    - Cada servidor do AD RMS está configurado para o URL de certificação. [Instruções](#configuring-ad-rms-servers-to-locate-the-certification-url) 
    
    - Um ponto de ligação de serviço (SCP) não pode estar registado no Active Directory: não são utilizados SCPs ao utilizar a proteção do AD RMS com o Azure Information Protection. 
    
        - Se tiver registado um SCP na implementação do AD RMS, tem de removê-lo para que a [deteção do serviço](./rms-client/client-deployment-notes.md#rms-service-discovery) seja bem-sucedida para a proteção do Azure Rights Management. 
        
        - Se estiver a instalar um novo cluster de AD RMS para HYOK, ignore o passo para registar o SCP durante a configuração do nó primeiro. Para cada nó adicional, certifique-se de que o servidor está configurado para o URL de certificação antes de adicionar a função de AD RMS e Junte-se do cluster existente.
    
    - Os servidores do AD RMS estão configurados para utilizar SSL/TLS com um certificado x.509 válido que seja considerado fidedigno pelos clientes ligados: necessários para ambientes de produção, mas não para fins de teste ou avaliação.
    
    - Modelos de direitos configurados.
    
    - Não configurado para IRM do Exchange.
    
    - Para dispositivos móveis e computadores Mac: os [extensão de dispositivo de móveis de serviços do Rights Management Active Directory](https://technet.microsoft.com/library/dn673574.aspx) está instalado e configurado.

- Sincronização de diretórios está configurada entre o Active Directory no local e o Azure Active Directory e utilizadores que irão utilizar a proteção do HYOK estão configurados para início de sessão único.

- Se partilhar documentos ou e-mails protegidos pelo HYOK com outras pessoas fora da sua organização: AD RMS está configurado para confianças explicitamente definidas numa relação ponto a ponto direta com as outras organizações através de um utilizador domínios fidedignos (TUDs) ou confianças federadas criadas utilizando os serviços de Federação do Active Directory (AD FS).

- Os utilizadores têm uma versão do Office 2016 Professional Plus ou do Office 2013 Professional Plus com Service Pack 1, em execução no Windows 7 Service Pack 1 ou posterior. Tenha em atenção que o Office 2010 e o Office 2007 não são suportados neste cenário.
    
    - Para o Office 2016, o Microsoft Installer (. msi)-com base edition: instalou [atualizar 4018295 para o Microsoft Office 2016, foi lançado no dia 6 de Março de 2018](https://support.microsoft.com/en-us/help/4018295/march-6-2018-update-for-office-2016-kb4018295).

> [!IMPORTANT]
> Para satisfazer a garantia de alta que oferece proteção do HYOK, recomendamos que os servidores do AD RMS não estejam localizados na sua rede de Perímetro e que são utilizados por apenas a dispositivos geridos. 
> 
> Recomendamos também que o cluster do AD RMS utilize um módulo de segurança de hardware (HSM), para que a chave privada do Certificado de Licenciante para Servidor (SLC) não possa ser exposta ou roubada caso a sua implementação do AD RMS seja alguma vez violada ou comprometida. 

Para obter informações de implementação e instruções para o AD RMS, veja [Serviços de Gestão de Direitos do Active Directory](https://technet.microsoft.com/library/hh831364.aspx) na biblioteca do Windows Server. 


### <a name="configuring-ad-rms-servers-to-locate-the-certification-url"></a>Configurar servidores do AD RMS para localizar o URL de certificação

1. Em cada servidor do AD RMS no cluster, crie a seguinte entrada de registo:

    `Computer\HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\GICURL = "<string>"`
    
    Para o \<valor da cadeia >, especifique um dos seguintes:
    
    - Para utilizar SSL/TLS clusters do AD RMS:

            https://<cluster_name>/_wmcs/certification/certification.asmx
    
    - Para o AD RMS clusters não utilizar SSL/TLS (redes apenas teste):
        
            http://<cluster_name>/_wmcs/certification/certification.asmx

2. Reinicie o IIS.

### <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Localizar as informações para especificar a proteção do AD RMS com uma etiqueta do Azure Information Protection

Quando configura uma etiqueta para a **HYOK (AD RMS)** proteção, tem de especificar o URL de licenciamento do cluster do AD RMS. Além disso, tem de especificar qualquer um de um modelo que configurou para as permissões conceder aos utilizadores ou permitir que os utilizadores, definir as permissões e os utilizadores. 

Pode encontrar o GUID do modelo e licenciamento de valores de URL a partir da consola de serviços de gestão de direitos do Active Directory:

- Para localizar um GUID do modelo: expanda o cluster e clique em **modelos de política de direitos**. A partir das informações em **Modelos de Política de Direitos Distribuídos**, pode copiar o GUID do modelo que pretende utilizar. Por exemplo: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Para localizar o URL de licenciamento: clique no nome do cluster. A partir das informações em **Detalhes do Cluster**, copie o valor de **Licenciamento** menos a cadeia **/_wmcs/licensing**. Por exemplo: https://rmscluster.contoso.com 
    
    Se tiver um valor de licenciamento de extranet, bem como um valor de licenciamento de intranet e forem diferentes: especifique o valor de extranet apenas se for partilhar documentos ou e-mails protegidos com parceiros que definiu com confianças ponto a ponto explícitas. Caso contrário, utilize o valor de intranet e certifique-se de que todos os computadores cliente que utilizam a proteção do AD RMS com o Azure Information Protection se ligam através de uma ligação de intranet (por exemplo, computadores remotos que utilizam uma ligação VPN).


## <a name="next-steps"></a>Passos Seguintes

Para configurar uma etiqueta para a proteção do HYOK, consulte [como configurar uma etiqueta para proteção do Rights Management](configure-policy-protection.md). 
