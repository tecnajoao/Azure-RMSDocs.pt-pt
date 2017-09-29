---
title: "Preços e restrições de BYOK – AIP"
description: "Compreender as restrições quando utilizar chaves gerida pelo cliente (conhecido como \"traga a sua própria chave\", ou BYOK) com o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: afc25e638cff4bddc342ed29dee7fab304d67bd7
ms.sourcegitcommit: faaab68064f365c977dfd1890f7c8b05a144a95c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2017
---
# <a name="byok-pricing-and-restrictions"></a>Preços e restrições de BYOK

>*Aplica-se a: Azure Information Protection, Office 365*


As organizações que têm uma subscrição que inclui o Azure Information Protection podem configurar o respetivo inquilino do Azure Information Protection para utilizar uma chave gerida pelo cliente (BYOK) e [registar a sua utilização](../deploy-use/log-analyze-usage.md) sem custos adicionais. 

A chave deve ser armazenada no Cofre de chaves do Azure, o que necessita de uma subscrição do Azure. Para utilizar uma chave protegida por HSM, tem de utilizar a camada de serviços do Azure Premium do Cofre de chave. A utilização de uma chave no Cofre de Chaves do Azure implica uma cobrança mensal. Para obter mais informações, veja a [página de Preços do Azure Key Vault](https://azure.microsoft.com/en-us/pricing/details/key-vault/).

Quando utiliza o Cofre de chaves do Azure para a sua chave de inquilino do Azure Information Protection, recomendamos que utilize um cofre de chaves dedicado para esta chave com uma subscrição dedicada. Esta configuração ajuda a garantir que é utilizada pelo apenas o serviço Azure Rights Management. 

## <a name="benefits-of-using-azure-key-vault"></a>Vantagens de utilizar o Azure Key Vault

Além de utilizar o registo de utilização do Azure Information Protection, para uma segurança adicional, pode utilizá-lo como referência cruzada com o [registo do Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-logging/) para monitorizar de forma independente e certificar-se de que apenas o serviço Azure Rights Management está a utilizar esta chave. Se for necessário, pode revogar imediatamente o acesso à chave ao remover as permissões no cofre de chaves.

Outras vantagens de utilizar o Azure Key Vault para a sua chave de inquilino do Azure Information Protection:

- O Azure Key Vault fornece uma solução de gestão de chaves centralizada que proporciona uma solução de gestão consistente para muitos serviços baseados na cloud e até serviços no local que utilizem encriptação.

- O Azure Key Vault suporta diversas interfaces incorporadas para a gestão de chaves, incluindo o PowerShell, a CLI, APIs REST e o portal do Azure. Foram integrados outros serviços e ferramentas com o Cofre de Chaves, para fornecer funcionalidades que sejam otimizadas para tarefas específicas, tais como a monitorização. Por exemplo, pode analisar os registos de utilização da sua chave através do Log Analytics do Operations Management Suite, definir alertas quando os critérios especificados forem correspondidos, entre outras tarefas.

- O Azure Key Vault proporciona uma separação de funções, como melhor prática de segurança comprovada. Os administradores do Azure Information Protection podem concentrar-se na gestão da proteção e classificação de dados e os administradores do Azure Key Vault podem concentrar-se na gestão de chaves de encriptação e todas as políticas especiais que possam ser necessárias para a segurança ou conformidade.

- Algumas organizações têm restrições relativamente ao local em que a chave mestra tem de ser armazenada. O Azure Key Vault fornece um elevado nível de controlo sobre o local onde armazena a chave mestra, uma vez que o serviço se encontra disponível em muitas regiões do Azure. Neste momento, dispõe de 28 regiões à escolha [regiões do Azure e é provável que este número aumente. Para mais informações, consulte a página [Produtos disponíveis por região] (https://azure.microsoft.com/regions/services/) no site do Azure.

Além da gestão de chaves, o Azure Key Vault proporciona aos seus administradores de segurança a mesma experiência em gestão para armazenar, aceder e gerir certificados e segredos (por exemplo, palavras-passe) de outros serviços e aplicações que utilizam encriptação. 

Para mais informações sobre o Azure Key Vault, consulte [O que é o Azure Key Vault?](/azure/key-vault/key-vault-whatis) e aceda ao [blogue de equipa do Azure Key Vault](https://blogs.technet.microsoft.com/kv/) para consultar as informações mais recentes e saber como os outros serviços utilizam esta tecnologia.

## <a name="restrictions-when-using-byok"></a>Restrições de utilização de BYOK

O BYOK e o registo de utilização funcionam perfeitamente com todas as aplicações que se integra com o serviço Azure Rights Management, que é utilizado pelo Azure Information Protection. Isto inclui serviços em nuvem como o SharePoint Online, servidores que executam o Exchange e SharePoint que utilizam o serviço Azure Rights Management utilizando o conector RMS e aplicações de cliente, tais como o Office 2016 ou Office 2013 no local a pedido. Irá obter registos de utilização de chave, independentemente da que aplicação fizer pedidos para o serviço Azure Rights Management.

Se anteriormente tiver ativado a IRM do Exchange Online ao importar o domínio de publicação fidedigno (TPD) do Azure RMS, siga as instruções em [configurar novas capacidades de encriptação de mensagens do Office 365 desenvolvidas Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) para ativar as novas funcionalidades no Exchange Online, que suportam a utilizar uma BYOK do Azure Information Protection.

## <a name="next-steps"></a>Próximos passos

Se tiver tomado a decisão de gerir a sua própria chave, aceda a [Implementar a sua chave de inquilino do Azure Rights Management](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).

Se tiver decidido manter a configuração predefinida, em que a Microsoft gere a sua chave de inquilino, consulte a secção [Passos seguintes](plan-implement-tenant-key.md#next-steps) do artigo Planear e implementar a sua chave de inquilino do Azure Rights Management.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
