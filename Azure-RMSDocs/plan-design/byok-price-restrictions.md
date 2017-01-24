---
title: "Preços e restrições de BYOK | Azure Information Protection"
description: "Compreenda as restrições na utilização de chaves geridas pelos clientes (conhecidas como &quot;traga a sua própria chave&quot; ou BYOK) com o Azure RMS."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/04/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 2e8a00d4c8d38387645d015d3f69a4d568fc9683


---

# <a name="byok-pricing-and-restrictions"></a>Preços e restrições de BYOK

>*Aplica-se a: Azure Information Protection, Office 365*


As organizações que têm uma subscrição que inclui o Azure Information Protection podem configurar o respetivo inquilino do Azure Information Protection para utilizar uma chave gerida pelo cliente (BYOK) e [registar a sua utilização](../deploy-use/log-analyze-usage.md) sem custos adicionais. 

A chave tem de ser armazenada no Cofre de Chaves do Azure, o que requer uma subscrição paga (ou de avaliação) do Azure além de que tem de utilizar a camada de serviço Cofre de Chaves do Azure Premium para suportar chaves protegidas por HSM. A utilização de uma chave protegida por HSM no Cofre de Chaves do Azure implica um custo mensal. Para obter mais informações, veja a [página de Preços do Cofre de Chaves do Azure](https://azure.microsoft.com/en-us/pricing/details/key-vault/).

Quando utilizar o Cofre de Chaves do Azure para a sua chave de inquilino do Azure Information Protection, recomendamos que tenha um cofre de chaves dedicado para esta chave com uma subscrição dedicada, para garantir que só é utilizada pelo serviço Azure Rights Management. 

## <a name="benefits-of-using-azure-key-vault"></a>Vantagens de utilizar o Cofre de Chaves do Azure

Além de utilizar o registo de utilização do Azure Information Protection, para uma segurança adicional, pode utilizá-lo como referência cruzada com o [registo do Cofre de Chaves do Azure](https://azure.microsoft.com/documentation/articles/key-vault-logging/) para monitorizar de forma independente e certificar-se de que apenas o serviço Azure Rights Management está a utilizar esta chave. Se for necessário, pode revogar imediatamente o acesso à chave ao remover as permissões no cofre de chaves.

Outras vantagens de utilizar o Cofre de Chaves do Azure para a sua chave de inquilino do Azure Information Protection:

- O Cofre de Chaves do Azure fornece uma solução de gestão de chaves centralizada que proporciona uma solução de gestão consistente para muitos serviços baseados na nuvem e até serviços no local que utilizem encriptação.

- O Cofre de Chaves do Azure suporta diversas interfaces incorporadas para a gestão de chaves, incluindo o PowerShell, a CLI, APIs REST e o portal do Azure. Foram integrados outros serviços e ferramentas com o Cofre de Chaves, para fornecer funcionalidades que sejam otimizadas para tarefas específicas, tais como a monitorização. Por exemplo, pode analisar os registos de utilização da sua chave através do Log Analytics do Operations Management Suite, definir alertas quando os critérios especificados forem correspondidos, entre outras tarefas.

- O Cofre de Chaves do Azure proporciona uma separação de funções, como melhor prática de segurança comprovada. Os administradores do Azure Information Protection podem concentrar-se na gestão da proteção e classificação de dados e os administradores do Cofre de Chaves do Azure podem concentrar-se na gestão de chaves de encriptação e todas as políticas especiais que possam ser necessárias para a segurança ou conformidade.

- Algumas organizações têm restrições relativamente ao local em que a chave mestra tem de ser armazenada. O Cofre de Chaves do Azure fornece um elevado nível de controlo sobre o local onde armazena a chave mestra, uma vez que o serviço se encontra disponível em muitas regiões do Azure. Neste momento, dispõe de 28 regiões à escolha [regiões do Azure e é provável que este número aumente. Para mais informações, consulte a página [Produtos disponíveis por região] (https://azure.microsoft.com/regions/services/) no site do Azure.

Além da gestão de chaves, o Cofre de Chaves do Azure proporciona aos seus administradores de segurança a mesma experiência em gestão para armazenar, aceder e gerir certificados e segredos (por exemplo, palavras-passe) de outros serviços e aplicações que utilizam encriptação. 

Para mais informações sobre o Cofre de Chaves do Azure, consulte [O que é o Cofre de Chaves do Azure?](https://azure.microsoft.com/documentation/articles/key-vault-whatis/) e aceda ao [blogue de equipa do Cofre de Chaves do Azure](https://blogs.technet.microsoft.com/kv/) para consultar as informações mais recentes e saber como os outros serviços utilizam esta tecnologia.


## <a name="restrictions-when-using-byok"></a>Restrições de utilização de BYOK

Se tiver utilizadores que se inscreveram numa conta gratuita através do RMS para indivíduos, não pode utilizar o BYOK nem o registo de utilização porque esta configuração não tem um administrador inquilinos para configurar estas funcionalidades.


> [!NOTE]
> Para obter mais informações sobre o RMS para indivíduos, consulte [RMS para indivíduos e Azure Rights Management](../understand-explore/rms-for-individuals.md).

![O BYOK não suporta o Exchange Online](../media/RMS_BYOK_noExchange.png)

O BYOK e o registo de utilização funcionam perfeitamente com todas as aplicações integradas no serviço Azure Rights Management (Azure RMS) utilizado pelo Azure Information Protection. Isto inclui serviços em nuvem como o SharePoint Online, servidores no local que executam o Exchange e SharePoint e que funcionam com o Azure RMS ao utilizar o conector RMS e aplicações de cliente como o Office 2016 e o Office 2013. Irá obter registos de utilização da chave, independentemente da aplicação que efetua os pedidos do Azure RMS.

Existe uma exceção: atualmente, o **BYOK do Azure RMS não é compatível com o Exchange Online**. Se desejar utilizar o Exchange Online, recomendamos que implemente agora o Azure RMS no modo de gestão de chaves predefinido, em que a Microsoft gera e faz a gestão da sua chave. Pode mudar para o BYOK posteriormente, por exemplo, quando o Exchange Online suportar o BYOK do Azure RMS. No entanto, se não puder aguardar, pode implementar o Azure RMS com o BYOK agora, com a funcionalidade do RMS reduzida no Exchange Online (os e-mails e anexos desprotegidos permanecem totalmente funcionais):

-   Os e-mails e anexos protegidos no Outlook Web Access não podem ser apresentados.

-   Os e-mails protegidos em dispositivos móveis que utilizem a IRM do Exchange ActiveSync não podem ser apresentados.

-   Não é possível realizar a desencriptação de transporte (por exemplo, para procurar software maligno) e a desencriptação do diário, por isso, os e-mails e anexos protegidos serão ignorados.

-   As regras de proteção de transporte e a prevenção de perda de dados (DLP) que impõem as políticas IRM não podem ser executadas, pelo que não é possível aplicar a proteção RMS com estes métodos.

-   A pesquisa baseada no servidor não abrange e-mails protegidos, por isso, estes serão ignorados.

Quando utilizar o BYOK do Azure RMS com funcionalidade reduzida do RMS no Exchange Online, o RMS irá funcionar com os clientes de e-mail no Outlook, Windows e Mac e noutros clientes de e-mail que não utilizem a IRM do Exchange ActiveSync.

Caso esteja a migrar para o Azure RMS a partir do AD RMS, pode ter importado a chave como um domínio de publicação fidedigno (TPD) para o Exchange Online (também denominado BYOK na terminologia do Exchange, que é diferente do BYOK do Cofre de Chaves do Azure). Neste cenário, tem de remover o TPD do Exchange Online para evitar que os modelos e políticas entrem em conflito. Para mais informações, consulte [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) na biblioteca de cmdlets do Exchange Online.

Por vezes, a exceção do BYOK do Azure RMS para o Exchange Online não é um problema a níveis práticos. Por exemplo, as organizações que precisam do BYOK e do registo executam as suas aplicações de dados (Exchange, SharePoint, Office) no local e utilizam o Azure RMS para obter funcionalidades que não estão facilmente disponíveis no AD RMS no local (por exemplo, a colaboração com outras empresas e o acesso a partir de clientes móveis). O BYOK e o registo funcionam bem neste cenário e permitem que a organização tenha um controlo total sobre a sua subscrição do Azure RMS.

## <a name="next-steps"></a>Passos seguintes

Se tiver tomado a decisão de gerir a sua própria chave, aceda a [Implementar a sua chave de inquilino do Azure Rights Management](plan-implement-tenant-key.md#implementing-your-azure-information-protection-tenant-key).

Se tiver decidido manter a configuração predefinida, em que a Microsoft gere a sua chave de inquilino, consulte a secção [Passos seguintes](plan-implement-tenant-key.md#next-steps) do artigo Planear e implementar a sua chave de inquilino do Azure Rights Management.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


