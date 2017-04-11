---
title: "Restrições de HYOK para o Azure Information Protection"
description: "Conheça as limitações, pré-requisitos e recomendações se selecionar a proteção do HYOK (AD RMS) com o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ms.openlocfilehash: b9217412778309917a5d259d09ab52a7bf121b41
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="hold-your-own-key-hyok-requirements-and-restrictions-for-ad-rms-protection"></a>Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS

>*Aplica-se a: Azure Information Protection*

Quando protege os documentos e e-mails mais confidenciais, normalmente fá-lo através da aplicação de proteção do Azure Rights Management (Azure RMS) para beneficiar do seguinte:

- Não é necessária nenhuma infraestrutura de servidor, o que torna a solução mais rápida e económica para implementar e manter do que uma solução no local.

- Uma partilha mais fácil com parceiros e os utilizadores de outras organizações utilizando a autenticação baseada na cloud.

- Integração completa com os serviços do Office 365, como pesquisa, visualizadores Web, vistas dinâmicas, antimalware, Deteção de Dados Eletrónicos e Delve.

- Controlo, revogação e notificação por e-mail para documentos confidenciais que tenha partilhado.

O Azure RMS protege os documentos e e-mails da sua organização através de uma chave privada para a organização gerida pela Microsoft (predefinição) ou gerida por si ("traga a sua própria chave" ou cenário BYOK). As informações que proteger com o Azure RMS nunca são enviadas para a cloud; os documentos e e-mails protegidos não são armazenados no Azure, a menos que os armazene aí explicitamente ou utilize outro serviço na cloud que os armazene no Azure. Para obter mais informações sobre as opções de chave de inquilino, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](../plan-design/plan-implement-tenant-key.md). 

No entanto, algumas organizações podem ter de proteger um pequeno subconjunto de documentos e e-mails com uma chave que está alojada no local. Por exemplo, isto pode ser necessário por motivos de regulamentação e conformidade.  

Esta configuração é, por vezes, referida como "tenha a sua própria chave" (HYOK) e é suportada pelo Azure Information Protection quando tem uma implementação de Serviços de Gestão de Direitos do Active Directory (AD RMS) ativa com os requisitos documentados na secção seguinte.

Neste cenário de HYOK, as políticas de direitos e a chave privada da organização que protege estas políticas são geridas e mantidas no local, enquanto que a política do Azure Information Protection para etiquetagem e classificação permanece gerida e armazenada no Azure. Tal como acontece com a proteção do Azure RMS, as informações que proteger com o AD RMS nunca são enviadas para a cloud.

> [!NOTE]
> Utilize esta configuração apenas quando tiver de o fazer e apenas para os documentos e e-mails que a requeiram. A proteção do AD RMS não fornece as vantagens indicadas que obtém quando utiliza a proteção do Azure RMS e o seu objetivo é "opacidade de dados a todo o custo".
>
> Normalmente, mesmo para as organizações que utilizam esta configuração, é adequada para menos de 10% de todos os conteúdos que têm de ser protegidos. Como orientação, utilize-a apenas para documentos ou e-mails que correspondam a todos os seguintes critérios:
> 
> - Os conteúdos possuem a classificação mais elevada na sua organização ("Confidencial") e o acesso é restringido a apenas algumas pessoas.
> 
> - Os conteúdos nunca serão partilhados fora da organização.
> 
> - Os conteúdos só serão consumidos na rede interna.
> 
> - Os conteúdos não precisam de ser consumidos em computadores Mac ou dispositivos móveis.

Os utilizadores não saberão quando uma etiqueta utiliza a proteção do AD RMS em vez da proteção do Azure RMS. Devido às limitações e restrições inerentes da proteção do AD RMS, certifique-se de que fornece orientações claras sobre as exceções para quando os utilizadores devem selecionar etiquetas que aplicam a proteção do AD RMS. 

As [políticas de âmbito](configure-policy-scope.md) são uma boa forma de garantir que apenas os utilizadores que precisam de aplicar a proteção do AD RMS veem as etiquetas configuradas para a proteção do AD RMS. 

## <a name="additional-limitations-when-using-hyok"></a>Limitações adicionais ao utilizar HYOK

Além de não suportar as vantagens indicadas que obtém quando utiliza a proteção do Azure RMS, utilizar a proteção do AD RMS com o Azure Information Protection tem as seguintes limitações:

- Não suporta o Office 2010 ou o Office 2007.

- Não utilize a opção **Não Reencaminhar** quando configurar uma etiqueta para a proteção do Azure RMS. Também tem de informar os utilizadores para não selecionarem manualmente esta opção no Outlook. 

    Se a opção Não Reencaminhar for aplicada por uma etiqueta ou manualmente pelos utilizadores, a opção poderá ser aplicada pela sua implementação do AD RMS em vez do serviço Azure Rights Management pretendido. Neste cenário, as pessoas com quem partilha externamente não poderão abrir mensagens de e-mail que têm esta opção Não Reencaminhar aplicada.

- Se os utilizadores escolherem uma etiqueta no Outlook que aplica a proteção do AD RMS e, em seguida, mudarem de ideias antes de enviar o e-mail e selecionarem uma etiqueta que aplica a proteção do Azure RMS, a última etiqueta selecionada não será aplicada. Os utilizadores verão a seguinte mensagem de erro: **O Azure Information Protection não pode aplicar esta etiqueta. Não tem permissão para efetuar esta ação.**
    
    A única solução é fechar a mensagem de e-mail e começar novamente. A mesma limitação é aplicável se os utilizadores escolherem primeiro uma etiqueta que aplica a proteção do Azure RMS e, em seguida, alterarem a etiqueta para uma que aplica a proteção do AD RMS.

## <a name="requirements-for-hyok"></a>Requisitos para HYOK

Verifique se a sua implementação do AD RMS cumpre os requisitos seguintes para fornecer proteção do AD RMS para o Azure Information Protection.

- Configuração do AD RMS:
    
    - Versão mínima do Windows Server 2012 R2: necessária para ambientes de produção, mas para fins de teste ou avaliação, pode utilizar uma versão mínima do Windows Server 2008 R2 com o Service Pack 1.
    
    - Cluster de raiz única do AD RMS.
    
    - [Modo Criptográfico 2](https://technet.microsoft.com/library/hh867439.aspx): pode confirmar a versão do modo criptográfico do cluster do AD RMS e o respetivo estado de funcionamento global utilizando a [ferramenta RMS Analyser](https://www.microsoft.com/en-us/download/details.aspx?id=46437).   
    
    - Um ponto de ligação de serviço (SCP) não pode estar registado no Active Directory: não são utilizados SCPs ao utilizar a proteção do AD RMS com o Azure Information Protection. Se tiver registado um SCP na implementação do AD RMS, tem de removê-lo para que a [deteção do serviço](../rms-client/client-deployment-notes.md#rms-service-discovery) seja bem sucedida para a proteção do Azure Rights Management.
    
    - Os servidores do AD RMS estão configurados para utilizar SSL/TLS com um certificado x.509 válido que seja considerado fidedigno pelos clientes ligados: necessários para ambientes de produção, mas não para fins de teste ou avaliação.
    
    - Modelos de direitos configurados.

- A sincronização de diretórios está configurada entre o Active Directory no local e o Azure Active Directory, e os utilizadores que irão utilizar a proteção do AD RMS estão configurados para início de sessão único.

- Se vai partilhar documentos ou e-mails protegidos pelo AD RMS com outras pessoas fora da sua organização: o AD RMS está configurado para confianças explicitamente definidas numa relação ponto a ponto direta com as outras organizações utilizando domínios de utilizadores fidedignos (TUDs) ou confianças federadas criadas utilizando os Serviços de Federação do Active Directory (AD FS).

- Os utilizadores têm uma versão do Office 2013 Pro Plus com Service Pack 1 ou do Office 2016 Pro Plus em execução no Windows 7 Service Pack 1 ou posterior. Tenha em atenção que o Office 2010 e o Office 2007 não são suportados neste cenário.

> [!IMPORTANT]
> Para cumprir a certeza elevada oferecida por este cenário, recomendamos que os servidores do AD RMS não estejam localizados na sua rede de perímetro e sejam utilizados apenas por computadores bem geridos (por exemplo, sem ser dispositivos móveis ou computadores de grupo de trabalho). 
> 
> Recomendamos também que o cluster do AD RMS utilize um módulo de segurança de hardware (HSM), para que a chave privada do Certificado de Licenciante para Servidor (SLC) não possa ser exposta ou roubada caso a sua implementação do AD RMS seja alguma vez violada ou comprometida. 

Para obter informações de implementação e instruções para o AD RMS, veja [Serviços de Gestão de Direitos do Active Directory](https://technet.microsoft.com/library/hh831364.aspx) na biblioteca do Windows Server. 


## <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Localizar as informações para especificar a proteção do AD RMS com uma etiqueta do Azure Information Protection

Quando configura uma etiqueta para a proteção do **HYOK (AD RMS)**, tem de especificar o GUID do modelo e o URL de licenciamento do cluster do AD RMS. Pode localizar estes valores na consola dos Serviços de Gestão de Direitos do Active Directory:

- Para localizar o GUID do modelo: expanda o cluster e clique em **Modelos de Política de Direitos**. A partir das informações em **Modelos de Política de Direitos Distribuídos**, pode copiar o GUID do modelo que pretende utilizar. Por exemplo: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Para localizar o URL de licenciamento: clique no nome do cluster. A partir das informações em **Detalhes do Cluster**, copie o valor de **Licenciamento** menos a cadeia **/_wmcs/licensing**. Por exemplo: https://rmscluster.contoso.com 
    
    Se tiver um valor de licenciamento de extranet, bem como um valor de licenciamento de intranet e forem diferentes: especifique o valor de extranet apenas se for partilhar documentos ou e-mails protegidos com parceiros que definiu com confianças ponto a ponto explícitas. Caso contrário, utilize o valor de intranet e certifique-se de que todos os computadores cliente que utilizam a proteção do AD RMS com o Azure Information Protection se ligam através de uma ligação de intranet (por exemplo, computadores remotos que utilizam uma ligação VPN).

## <a name="next-steps"></a>Passos seguintes

Para obter mais informações sobre esta funcionalidade e orientações para quando a utilizar, consulte o anúncio do blogue [Azure Information Protection com HYOK (Tenha a Sua Própria Chave)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azure-information-protection-with-hyok-hold-your-own-key/).

Para configurar uma etiqueta para a proteção do AD RMS, veja [Como configurar uma etiqueta para a proteção do Rights Management](../deploy-use/configure-policy-protection.md). 

[!INCLUDE[Commenting house rules](../includes/houserules.md)]