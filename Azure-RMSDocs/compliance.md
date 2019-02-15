---
title: Conformidade e informações do Azure Information Protection
description: Informações de suporte para o Azure Information Protection incluem informações legais, conformidade e SLAs.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/06/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b3a7127b-6d24-4439-bc4e-2a0a325e8ea3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4f611f97309851364324618e436ca13d4bd9fee7
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254718"
---
# <a name="compliance-and-supporting-information-for-azureinformation-protection"></a>Informações de suporte do Azure Information Protection e conformidade

O Azure Information Protection suporta outros serviços e também depende de outros serviços. Se estiver procurando por informações relacionadas com o Azure Information Protection, mas não sobre como utilizar o serviço do Azure Information Protection, consulte os seguintes recursos:

## <a name="suitability-for-different-countries"></a>Adequação para diferentes países

Tendo em conta a variabilidade entre as leis e regulamentos em diferentes países, diferentes casos de utilização e cenários e os requisitos variados entre os setores de negócios diferentes, terá de consultar o seu consultor legal que o ajudarão a responder se o Azure Proteção de informações é adequada para seu país/região.

No entanto, algumas informações relevantes que ajudem a seu consultor legal tornar a determinação:

- O Azure Information Protection utiliza AES 256 e AES 128 para encriptar documentos. [Mais informações](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Todas as chaves de encriptação utilizadas pelo Azure Information Protection estão protegidas com uma chave de raiz de específicas do cliente que utiliza RSA 2048 bits. RSA 1024, como também é suportado para compatibilidade com versões anteriores. [Mais informações](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Chaves de raiz de específicas do cliente são geridas pela Microsoft ou aprovisionadas pelo cliente num HSM da Thales através da utilização "[traga a sua própria chave](plan-implement-tenant-key.md)" (BYOK). O Azure Information Protection também suporta a funcionalidade limitada com uma chave no local utilizando "[tenha a sua própria chave](configure-adrms-restrictions.md)" (HYOK) para o conteúdo que é afetado pelos requisitos que indicam que não devem ser protegidos com uma chave com base na cloud.

- O serviço Azure Information Protection está alojado em datacenters regionais em todo o mundo. Chaves de proteção de informações e as políticas do Azure sempre permanecerem dentro da região na qual está implementada originalmente.
 
- O Azure Information Protection não transmitir conteúdo de documentos a partir de clientes para o serviço Azure Information Protection. As operações de criptografia e descriptografia conteúdas são executadas no local no dispositivo cliente. Em alternativa, para processamento com base no serviço, estas operações são realizadas no âmbito do serviço que está sendo o conteúdo. [Mais informações](./how-does-it-work.md)

## <a name="legal-and-privacy"></a>Informações legais e privacidade

- Para obter informações de contrato do Microsoft Azure: [Microsoft Azure Agreement](https://azure.microsoft.com/support/legal/subscription-agreement/)

- Para obter informações de privacidade do Microsoft Azure: [Declaração de privacidade do Microsoft Azure](https://azure.microsoft.com/support/legal/privacy-statement/)

## <a name="security-compliance-and-auditing"></a>Segurança, conformidade e auditoria

Veja a secção [Requisitos de segurança, conformidade e regulamentação](./what-is-azure-rms.md#security-compliance-and-regulatory-requirements) no artigo [Que problemas resolve o Azure RMS?](./azure-rms-problems-it-solves.md), para obter informações sobre certificados específicos para o serviço Azure Rights Management. Além disso:

- Para obter certificados externos do Azure Information Protection: [Centro de fidedignidade do Microsoft Azure](https://azure.microsoft.com/support/trust-center/)

- Para obter informações de FIPS 140: [O FIPS 140 validação](https://technet.microsoft.com/library/security/cc750357.aspx)

Para obter informações técnicas detalhadas sobre como funciona a tecnologia de proteção, veja [Como funciona o Azure RMS?](./how-does-it-work.md) 

## <a name="service-level-agreements"></a>Contratos de nível de serviço

- [SLA do Azure Information Protection](https://azure.microsoft.com/support/legal/sla/information-protection/v1_0/)

- [SLA para o Azure Active Directory](https://azure.microsoft.com/support/legal/sla/active-directory/v1_0/)

- [SLA para o Cofre de chaves do Azure](https://azure.microsoft.com/support/legal/sla/key-vault/v1_0/)

## <a name="documentation"></a>Documentação

- Documentação do Azure Active Directory: [O Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis)

- Documentação do Office 365 Enterprise: [Office 365](https://docs.microsoft.com/en-us/Office365/Enterprise/)

