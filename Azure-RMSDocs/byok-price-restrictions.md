---
title: Preços e restrições de BYOK – AIP
description: Compreender as restrições ao utilizar chaves geridas pelo cliente (conhecido como "traga a sua própria chave" ou BYOK) com o Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 68e479eb7f19f60d6d68b913eae46dd287b5a04f
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305153"
---
# <a name="byok-pricing-and-restrictions"></a>Preços e restrições de BYOK

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


As organizações que tenham uma subscrição que inclui o Azure Information Protection podem configurar o respetivo inquilino do Azure Information Protection para utilizar uma chave gerida pelo cliente (BYOK) e [registar a sua utilização](./log-analyze-usage.md). 

A chave deve ser armazenada no Azure Key Vault, que requer uma subscrição do Azure. Para utilizar uma chave protegida por HSM, tem de utilizar a camada de serviços do Azure Key Vault Premium. A utilização de uma chave no Cofre de Chaves do Azure implica uma cobrança mensal. Para obter mais informações, veja a [página de Preços do Azure Key Vault](https://azure.microsoft.com/pricing/details/key-vault/).

Ao utilizar o Azure Key Vault para a sua chave de inquilino do Azure Information Protection, recomendamos que utilize um cofre de chaves dedicado para esta chave para ajudar a garantir que é utilizado pelo apenas o serviço Azure Rights Management. Esta configuração garante que as chamadas por outros serviços não implicam em que exceda o [limites de serviço](/azure/key-vault/key-vault-service-limits) para o Cofre de chaves, que pode limitar os tempos de resposta para o serviço Azure Rights Management.  

Além disso, uma vez cada serviço que utiliza o Azure Key Vault normalmente tem requisitos de gestão de chaves diferentes, recomendamos uma subscrição separada do Azure para este Cofre de chaves para o ajudar a proteger contra uma configuração incorreta. 

No entanto, se pretender partilhar uma subscrição do Azure com outros serviços que utilizam o Azure Key Vault, certifique-se de que a subscrição partilhas de um conjunto comum de administradores. Esta precaução significa que os administradores que utilizam a mesma tem uma boa compreensão de todas as chaves que têm acesso, para que fiquem menos provável que misconfigure-los. Por exemplo, uma partilhado subscrição do Azure se os administradores para a sua chave de inquilino do Azure Information Protection são as mesmas pessoas que administrar as chaves para a chave de cliente do Office 365 e CRM Online. Mas se a administradores que gerem as chaves para a chave de cliente ou CRM Online não são as mesmas pessoas que administrar a sua chave de inquilino do Azure Information Protection, em seguida, recomendamos que não partilham sua subscrição do Azure para o Azure Information Protection.

## <a name="benefits-of-using-azure-key-vault"></a>Vantagens de utilizar o Azure Key Vault

Além de utilizar o registo de utilização do Azure Information Protection, para uma segurança adicional, pode utilizá-lo como referência cruzada com o [registo do Azure Key Vault](/azure/key-vault/key-vault-logging) para monitorizar de forma independente e certificar-se de que apenas o serviço Azure Rights Management está a utilizar esta chave. Se for necessário, pode revogar imediatamente o acesso à chave ao remover as permissões no cofre de chaves.

Outras vantagens de utilizar o Azure Key Vault para a sua chave de inquilino do Azure Information Protection:

- O Azure Key Vault fornece uma solução de gestão de chaves centralizada que proporciona uma solução de gestão consistente para muitos serviços baseados na cloud e até serviços no local que utilizem encriptação.

- O Azure Key Vault suporta diversas interfaces incorporadas para a gestão de chaves, incluindo o PowerShell, a CLI, APIs REST e o portal do Azure. Foram integrados outros serviços e ferramentas com o Cofre de Chaves, para fornecer funcionalidades que sejam otimizadas para tarefas específicas, tais como a monitorização. Por exemplo, pode analisar os registos de utilização da sua chave através do Log Analytics do Operations Management Suite, definir alertas quando os critérios especificados forem correspondidos, entre outras tarefas.

- O Azure Key Vault proporciona uma separação de funções, como melhor prática de segurança comprovada. Os administradores do Azure Information Protection podem concentrar-se na gestão da proteção e classificação de dados e os administradores do Azure Key Vault podem concentrar-se na gestão de chaves de encriptação e todas as políticas especiais que possam ser necessárias para a segurança ou conformidade.

- Algumas organizações têm restrições relativamente ao local em que a chave mestra tem de ser armazenada. O Azure Key Vault fornece um elevado nível de controlo sobre o local onde armazena a chave mestra, uma vez que o serviço se encontra disponível em muitas regiões do Azure. Atualmente, pode escolher a partir de 28 regiões do Azure, e pode esperar que este número aumente. Para obter mais informações, consulte a [produtos disponíveis por região](https://azure.microsoft.com/regions/services/) página no site do Azure.

Além da gestão de chaves, o Azure Key Vault proporciona aos seus administradores de segurança a mesma experiência em gestão para armazenar, aceder e gerir certificados e segredos (por exemplo, palavras-passe) de outros serviços e aplicações que utilizam encriptação. 

Para mais informações sobre o Azure Key Vault, consulte [O que é o Azure Key Vault?](/azure/key-vault/key-vault-whatis) e aceda ao [blogue de equipa do Azure Key Vault](https://blogs.technet.microsoft.com/kv/) para consultar as informações mais recentes e saber como os outros serviços utilizam esta tecnologia.

## <a name="restrictions-when-using-byok"></a>Restrições de utilização de BYOK

O BYOK e o registo de utilização funcionam perfeitamente com todas as aplicações que se integra com o serviço Azure Rights Management, que é utilizado pelo Azure Information Protection. Isto inclui serviços cloud, como o SharePoint Online, servidores que executam o Exchange e SharePoint que utilizam o serviço Azure Rights Management ao utilizar o conector RMS e aplicações de cliente, como o Office 2016 e Office 2013 no local a pedido. Obter registos de utilização de chave, independentemente do que o aplicativo faz solicitações para o serviço Azure Rights Management.

Se anteriormente tiver ativado o IRM do Exchange Online através da importação de seu domínio de publicação fidedigno (TPD) do Azure RMS, siga as instruções em [configurar novas capacidades de encriptação de mensagens do Office 365 criadas com base no Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) para permitir que os novos recursos no Exchange Online, que suportam a utilização de BYOK do Azure Information Protection.

## <a name="next-steps"></a>Passos Seguintes

Se tiver tomado a decisão de gerir a sua própria chave, aceda a [implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).

Se tiver decidido manter-se com a configuração padrão em que a Microsoft gere o inquilino chave, consulte a [próximos passos](plan-implement-tenant-key.md#next-steps) secção de planear e implementar o seu artigo de chave de inquilino do Azure Information Protection.

