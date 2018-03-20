---
title: "Preços e restrições de BYOK – AIP"
description: "Compreender as restrições quando utilizar chaves gerida pelo cliente (conhecido como \"traga a sua própria chave\", ou BYOK) com o Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ac9324a0418a557682714b6f2b5621a2d9f7530e
ms.sourcegitcommit: 758e0cfeb6c05f4c6f5310dc36fbf0c02c256eed
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/17/2018
---
# <a name="byok-pricing-and-restrictions"></a>Preços e restrições de BYOK

>*Aplica-se a: Azure Information Protection, Office 365*


As organizações que têm uma subscrição que inclui o Azure Information Protection podem configurar o respetivo inquilino do Azure Information Protection para utilizar uma chave gerida pelo cliente (BYOK) e [registar a sua utilização](../deploy-use/log-analyze-usage.md) sem custos adicionais. 

A chave deve ser armazenada no Cofre de chaves do Azure, o que necessita de uma subscrição do Azure. Para utilizar uma chave protegida por HSM, tem de utilizar a camada de serviços do Azure Premium do Cofre de chave. A utilização de uma chave no Cofre de Chaves do Azure implica uma cobrança mensal. Para obter mais informações, veja a [página de Preços do Azure Key Vault](https://azure.microsoft.com/pricing/details/key-vault/).

Quando utiliza o Cofre de chaves do Azure para a sua chave de inquilino do Azure Information Protection, recomendamos que utilize um cofre de chaves dedicado para esta chave para ajudar a garantir que é utilizada pelo apenas o serviço Azure Rights Management. Esta configuração assegura que as chamadas por outros serviços não resultar exceder o [os limites de serviço](/azure/key-vault/key-vault-service-limits) para o Cofre de chaves, que pode limitar os tempos de resposta para o serviço Azure Rights Management.  

Além disso, uma vez cada serviço que utiliza o Cofre de chaves do Azure normalmente tem requisitos de gestão de chaves diferentes, recomendamos que uma subscrição do Azure separada para este Cofre de chaves ajudar a salvaguardar contra uma configuração incorreta. 

No entanto, se pretender partilhar uma subscrição do Azure com outros serviços que utilizam o Cofre de chaves do Azure, certifique-se de que a subscrição partilhas de um conjunto comum de administradores. Esta precaução significa que os administradores que utilizam essa subscrição têm uma boa compreensão de todas as chaves que têm acesso, para que fiquem menor probabilidade de misconfigure-los. Por exemplo, uma partilhado subscrição do Azure se os administradores para a sua chave de inquilino do Azure Information Protection são as pessoas mesmas que administrar chaves para a chave de cliente do Office 365 e CRM Online. Mas se a administradores que gerem as chaves para a chave de cliente ou CRM Online não são as pessoas mesmas que administrar a sua chave de inquilino do Azure Information Protection, em seguida, recomendamos que não partilha a sua subscrição do Azure para o Azure Information Protection.

## <a name="benefits-of-using-azure-key-vault"></a>Vantagens de utilizar o Azure Key Vault

Além de utilizar o registo de utilização do Azure Information Protection, para uma segurança adicional, pode utilizá-lo como referência cruzada com o [registo do Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-logging/) para monitorizar de forma independente e certificar-se de que apenas o serviço Azure Rights Management está a utilizar esta chave. Se for necessário, pode revogar imediatamente o acesso à chave ao remover as permissões no cofre de chaves.

Outras vantagens de utilizar o Azure Key Vault para a sua chave de inquilino do Azure Information Protection:

- O Azure Key Vault fornece uma solução de gestão de chaves centralizada que proporciona uma solução de gestão consistente para muitos serviços baseados na cloud e até serviços no local que utilizem encriptação.

- O Azure Key Vault suporta diversas interfaces incorporadas para a gestão de chaves, incluindo o PowerShell, a CLI, APIs REST e o portal do Azure. Foram integrados outros serviços e ferramentas com o Cofre de Chaves, para fornecer funcionalidades que sejam otimizadas para tarefas específicas, tais como a monitorização. Por exemplo, pode analisar os registos de utilização da sua chave através do Log Analytics do Operations Management Suite, definir alertas quando os critérios especificados forem correspondidos, entre outras tarefas.

- O Azure Key Vault proporciona uma separação de funções, como melhor prática de segurança comprovada. Os administradores do Azure Information Protection podem concentrar-se na gestão da proteção e classificação de dados e os administradores do Azure Key Vault podem concentrar-se na gestão de chaves de encriptação e todas as políticas especiais que possam ser necessárias para a segurança ou conformidade.

- Algumas organizações têm restrições relativamente ao local em que a chave mestra tem de ser armazenada. O Azure Key Vault fornece um elevado nível de controlo sobre o local onde armazena a chave mestra, uma vez que o serviço se encontra disponível em muitas regiões do Azure. Atualmente, pode escolher entre 28 regiões do Azure e que pode esperar aumentar este número. Para obter mais informações, consulte [produtos disponíveis por região] (https://azure.microsoft.com/regions/services/) página no site do Azure.

Além da gestão de chaves, o Azure Key Vault proporciona aos seus administradores de segurança a mesma experiência em gestão para armazenar, aceder e gerir certificados e segredos (por exemplo, palavras-passe) de outros serviços e aplicações que utilizam encriptação. 

Para mais informações sobre o Azure Key Vault, consulte [O que é o Azure Key Vault?](/azure/key-vault/key-vault-whatis) e aceda ao [blogue de equipa do Azure Key Vault](https://cloudblogs.microsoft.com/kv/) para consultar as informações mais recentes e saber como os outros serviços utilizam esta tecnologia.

## <a name="restrictions-when-using-byok"></a>Restrições de utilização de BYOK

O BYOK e o registo de utilização funcionam perfeitamente com todas as aplicações que se integra com o serviço Azure Rights Management, que é utilizado pelo Azure Information Protection. Isto inclui serviços em nuvem como o SharePoint Online, servidores que executam o Exchange e SharePoint que utilizam o serviço Azure Rights Management utilizando o conector RMS e aplicações de cliente, tais como o Office 2016 ou Office 2013 no local a pedido. Obter registos de utilização de chave, independentemente da que aplicação fizer pedidos para o serviço Azure Rights Management.

Se anteriormente tiver ativado a IRM do Exchange Online ao importar o domínio de publicação fidedigno (TPD) do Azure RMS, siga as instruções em [configurar novas capacidades de encriptação de mensagens do Office 365 desenvolvidas Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) para ativar as novas funcionalidades no Exchange Online, que suportam a utilizar uma BYOK do Azure Information Protection.

## <a name="next-steps"></a>Próximos passos

Se tiver tomado a decisão de gerir a sua própria chave, aceda a [implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).

Se tiver decidido manter a configuração predefinida onde a Microsoft gere a chave, consulte de inquilino de [passos](plan-implement-tenant-key.md#next-steps) secção de planear e implementar o seu artigo de chave de inquilino do Azure Information Protection.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
