---
title: "Restrições de HYOK | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/18/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
translationtype: Human Translation
ms.sourcegitcommit: a80866576dc7d6400bcebc2fc1c37bc0367bcdf3
ms.openlocfilehash: 1cbf6bd6c209a8aafd1db61422ce03b628aaec07


---

# Requisitos e restrições de Tenha a sua própria chave (HYOK) para proteção do AD RMS

>*Aplica-se a: pré-visualização do Azure Information Protection*

**[Estas informações são preliminares e estão sujeitas a alterações. ]**

Quando protege os documentos e e-mails mais confidenciais, normalmente vai fazê-lo através da aplicação de proteção Azure Rights Management para beneficiar do seguinte:

- Não é necessária nenhuma infraestrutura de servidor, o que torna a solução mais rápida e económica para implementar e manter do que uma solução no local.

- Uma partilha mais fácil com parceiros e os utilizadores de outras organizações utilizando a autenticação baseada na nuvem.

- Integração completa com os serviços do Office 365, como pesquisa, visualizadores Web, vistas dinâmicas, antimalware, Deteção de Dados Eletrónicos e Delve.

- Controlo, revogação e notificação por e-mail para documentos confidenciais que tenha partilhado.

O Azure RMS protege os documentos e e-mails da sua organização através de uma chave privada para a organização gerida pela Microsoft (predefinição) ou gerida por si ("traga a sua própria chave" ou cenário BYOK). As informações que proteger com o Azure RMS nunca são enviadas para a nuvem; os documentos e e-mails protegidos não são armazenados no Azure, a menos que os armazene aí explicitamente ou utilize outro serviço em nuvem que os armazene no Azure. Para obter mais informações sobre as opções de chave de inquilino, veja [Planear e implementar a sua chave de inquilino do Azure Rights Management](../plan-design/plan-implement-tenant-key.md). 

No entanto, alguns clientes podem ter de proteger os documentos e e-mails selecionados com uma chave alojada no local. Por exemplo, isto pode ser necessário por motivos de regulamentação e conformidade. 

Esta configuração é, por vezes, referida como "tenha a sua própria chave" (HYOK) e é suportada pelo Azure Information Protection quando tem uma implementação de Serviços de Gestão de Direitos do Active Directory (AD RMS) ativa com os requisitos documentados na secção seguinte. 

Neste cenário de HYOK, as políticas de direitos e a chave privada da organização que protege estas políticas são geridas e mantidas no local, enquanto que a política do Azure Information Protection para etiquetagem e classificação permanece gerida e armazenada no Azure. Tal como acontece com a proteção do Azure RMS, as informações que proteger com o AD RMS nunca são enviadas para a nuvem.

> [!NOTE]
> Utilize esta configuração apenas quando tiver de o fazer e apenas para os documentos e e-mails que a requeiram. A proteção do AD RMS não fornece as vantagens indicadas que obtém quando utiliza a proteção do Azure RMS e o seu objetivo é "opacidade de dados a todo o custo".

Os utilizadores não saberão quando uma etiqueta utiliza a proteção do AD RMS em vez da proteção do Azure RMS. Devido às restrições incluídas na proteção do AD RMS, certifique-se de que fornece orientações simples para quando os utilizadores devem selecionar etiquetas que aplicam a proteção do AD RMS.

## Requisitos para HYOK

Verifique se a sua implementação do AD RMS cumpre os requisitos seguintes para fornecer proteção do AD RMS para o Azure Information Protection.

- Configuração do AD RMS:
    
    - Versão mínima do Windows Server 2012 R2: necessária para ambientes de produção, mas para fins de teste ou avaliação, pode utilizar uma versão mínima do Windows Server 2008 R2 com o Service Pack 1.
    
    - Cluster de raiz única do AD RMS.
    
    - [Modo Criptográfico 2](https://technet.microsoft.com/library/hh867439.aspx): pode confirmar a versão do modo criptográfico do cluster do AD RMS e o respetivo estado de funcionamento global utilizando a [ferramenta RMS Analyser](https://www.microsoft.com/en-us/download/details.aspx?id=46437).   
    
    - Os servidores do AD RMS estão configurados para utilizar SSL/TLS com um certificado x.509 válido que seja considerado fidedigno pelos clientes ligados: necessários para ambientes de produção, mas não para fins de teste ou avaliação.
    
    - Modelos de direitos configurados.

- A sincronização de diretórios está configurada entre o Active Directory no local e o Azure Active Directory, e os utilizadores que irão utilizar a proteção do AD RMS estão configurados para início de sessão único.

- Se vai partilhar documentos ou e-mails protegidos pelo AD RMS com outras pessoas fora da sua organização: o AD RMS está configurado para confianças explicitamente definidas numa relação ponto a ponto direta com as outras organizações utilizando domínios de utilizadores fidedignos (TUDs) ou confianças federadas criadas utilizando os Serviços de Federação do Active Directory (AD FS).

- Os utilizadores têm uma versão do Office 2013 Pro Plus com Service Pack 1 ou do Office 2016 Pro Plus em execução no Windows 7 Service Pack 1 ou posterior. Tenha em atenção que o Office 2010 e o Office 2007 não são suportados neste cenário.

- O [cliente do Azure Information Protection](info-protect-client.md) tem a versão **1.0.233.0** ou posterior.

> [!IMPORTANT]
> Para cumprir a certeza elevada oferecida por este cenário, recomendamos que os servidores do AD RMS não estejam localizados na sua rede de perímetro e sejam utilizados apenas por computadores bem geridos (por exemplo, sem ser dispositivos móveis ou computadores de grupo de trabalho). 
> 
> Recomendamos também que o cluster do AD RMS utilize um módulo de segurança de hardware (HSM), para que a chave privada do Certificado de Licenciante para Servidor (SLC) não possa ser exposta ou roubada caso a sua implementação do AD RMS seja alguma vez violada ou comprometida. 

Para obter informações de implementação e instruções para o AD RMS, veja [Serviços de Gestão de Direitos do Active Directory](https://technet.microsoft.com/library/hh831364.aspx) na biblioteca do Windows Server. 


## Localizar as informações para especificar a proteção do AD RMS com uma etiqueta do Azure Information Protection

Quando configura uma etiqueta para a proteção do AD RMS, tem de especificar o GUID do modelo e o URL de licenciamento do cluster do AD RMS. Pode localizar estes valores na consola dos Serviços de Gestão de Direitos do Active Directory:

- Para localizar o GUID do modelo: expanda o cluster e clique em **Modelos de Política de Direitos**. A partir das informações em **Modelos de Política de Direitos Distribuídos**, pode copiar o GUID do modelo que pretende utilizar. Por exemplo: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Para localizar o URL de licenciamento: clique no nome do cluster. A partir das informações em **Detalhes do Cluster**, copie o valor de **Licenciamento** menos a cadeia **/_wmcs/licensing**. Por exemplo: https://rmscluster.contoso.com 
    
    Se tiver um valor de licenciamento de extranet, bem como um valor de licenciamento de intranet e forem diferentes: especifique o valor de extranet apenas se for partilhar documentos ou e-mails protegidos com parceiros que definiu com confianças ponto a ponto explícitas. Caso contrário, utilize o valor de intranet e certifique-se de que todos os computadores cliente que utilizam a proteção do AD RMS com o Azure Information Protection se ligam através de uma ligação de intranet (por exemplo, computadores remotos que utilizam uma ligação VPN).

## Passos seguintes

Para ler mais informações sobre esta funcionalidade de pré-visualização, veja o anúncio de mensagem de blogue, [Azure Information Protection com HYOK (Tenha a Sua Própria Chave)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azure-information-protection-with-hyok-hold-your-own-key/).

Para configurar uma etiqueta para a proteção do AD RMS, veja [Como configurar uma etiqueta para aplicar a proteção Rights Management](configure-policy-protection.md). 



<!--HONumber=Aug16_HO3-->


