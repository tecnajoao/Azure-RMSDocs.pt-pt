---
title: Instruções sobre como proceder para cenários comuns que utilizam o Azure Information Protection.
description: Identificar casos de utilização que classificar e proteger os dados da sua organização através da utilização do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/08/2018
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 7986648999a830985c4dbd1f31855bb222a443c2
ms.sourcegitcommit: 2a1c0882d2b0400f4da6370dbc1830df09867e3d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53218379"
---
# <a name="how-to-guides-for-common-scenarios-that-use-azure-information-protection"></a>Guias de procedimentos para cenários comuns que utilizam o Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Existem várias formas em que pode utilizar o Azure Information Protection para classificar e, opcionalmente, proteger documentos e e-mails da sua organização. 

As implementações mais bem-sucedidos são aqueles que identificar casos de utilização específico que fornecem o máximo proveito de negócios para a organização. Utilize a seguinte lista de instruções e cenários comuns para obter a sua implementação deslocar o.

## <a name="common-scenarios"></a>Cenários comuns

|Cenário: Pretendo...|Instruções|
|----------------|---------------|
|Localizar quais sensíveis informações a minha organização armazena no local|[Início rápido: Localizar as informações confidenciais que tiver no ficheiros armazenados no local](quickstart-findsensitiveinfo.md)|
|Torna mais fácil para os utilizadores a proteger os e-mails que contêm informações confidenciais|[Início rápido: Configurar uma etiqueta para os utilizadores a proteger facilmente os e-mails que contêm informações confidenciais](quickstart-label-dnf-protectedemail.md)|
|Torna mais fácil para os utilizadores classificar dados, como ele foi criado ou editado e protegê-lo se contiver informações confidenciais| [Tutorial: Editar a política e criar uma nova etiqueta](infoprotect-quick-start-tutorial.md)|
|Torna mais fácil para os utilizadores colaborar num documento protegido|[Configuração da colaboração de documentos segura, utilizando o Azure Information Protection](secure-collaboration-documents.md)|
|Proteger automaticamente e-mails dos utilizadores que são enviadas para fora da organização| [Configurar regras de fluxo de correio para etiquetas do Azure Information Protection](configure-exo-rules.md)
|Automaticamente classificar e proteger os dados existentes nos meus arquivos de dados no local|[Implementar o scanner do Azure Information Protection](deploy-aip-scanner.md)|
|Utilizar a minha própria chave para proteger os dados da minha organização| [Planear e implementar a chave de inquilino](plan-implement-tenant-key.md)|
|Migrar do AD RMS|[Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)|

## <a name="additional-deployment-instructions"></a>Instruções de implementação adicionais

Nosso [blog técnico do Azure Information Protection](https://aka.ms/AIPblog) tem instruções passo a passo adicionais da nossa equipa de engenharia de experiência do cliente. Por exemplo:

- [Usando o Azure Information Protection para proteger do PDF e Adobe Acrobat Reader para visualizá-los](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Using-Azure-Information-Protection-to-protect-PDF-s-and-Adobe/ba-p/282010)

- [Catalogação seus dados confidenciais com AIP, até mesmo antes de configurar as etiquetas!](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Cataloging-your-Sensitive-Data-with-AIP-Even-Before-Configuring/ba-p/267241)

- [Instalação rápida do Azure Information Protection Scanner](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Azure-Information-Protection-Scanner-Express-Installation/ba-p/265424)

- [Deteção de dados confidenciais a utilizar o verificador AIP (AIP Premium P1)](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discovery-of-Sensitive-Data-Using-the-AIP-Scanner-AIP-Premium-P1/ba-p/252040)

## <a name="next-steps"></a>Passos Seguintes

Não vê o seu cenário listado? Verifique os [plano de implementação](deployment-roadmap.md) para uma lista completa dos passos de planeamento e implementação.

Se estiver familiarizado com o Azure Information Protection, consulte [o que é o Azure Information Protection?](what-is-information-protection.md) para uma introdução rápida para o serviço antes de começar a implementação.
