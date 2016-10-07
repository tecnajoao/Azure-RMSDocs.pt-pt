---
title: "Preços e restrições de BYOK | Azure Information Protection"
description: Understand the restrictions when you use customer-managed keys (known as "bring your own key", or BYOK) with Azure RMS.
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 36e392d7e9a2fc8cec0419a3e66f92b42137bc72
ms.openlocfilehash: 3ed4f3c770c1c34d2bda7481d8ca405c51d3fe8c


---

# Preços e restrições de BYOK

>*Aplica-se a: Azure Information Protection, Office 365*


As organizações que tenham uma subscrição que inclua o Azure Rights Management podem utilizar chaves geridas pelo cliente (BYOK) no Cofre de Chaves do Azure e registar a respetiva utilização sem qualquer custo adicional. No entanto, para utilizar o Cofre de Chaves do Azure, é necessário ter uma subscrição do Azure que suporte o Cofre de Chaves com chaves protegidas por HSM. A utilização de uma chave no Cofre de Chaves do Azure implica uma cobrança mensal. Para obter mais informações, veja a [página de Preços do Cofre de Chaves do Azure](https://azure.microsoft.com/en-us/pricing/details/key-vault/).

Se tiver utilizadores que se inscreveram numa conta gratuita utilizando o RMS para indivíduos, não pode utilizar o BYOK nem o registo de utilização porque esta configuração não tem um administrador inquilino para configurar estas funcionalidades.


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

## Passos seguintes

Se tiver tomado a decisão de gerir a sua própria chave, aceda a [Implementar a sua chave de inquilino do Azure Rights Management](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key).

Se tiver decidido manter a configuração predefinida, em que a Microsoft gere a sua chave de inquilino, consulte a secção [Passos seguintes](plan-implement-tenant-key.md#next-steps) do artigo Planear e implementar a sua chave de inquilino do Azure Rights Management.




<!--HONumber=Sep16_HO4-->


