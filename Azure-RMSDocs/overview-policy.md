---
title: Descrição geral da política do Azure Information Protection
description: Compreenda as etiquetas e as definições numa política do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/27/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 29f573ae997431d621a616eccb9591c830ae8e9c
ms.sourcegitcommit: 1fe9720526a2ff814cd5d353249b16497cfcaadc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2019
ms.locfileid: "56425934"
---
# <a name="overview-of-the-azure-information-protection-policy"></a>Descrição geral da política do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Uma política do Azure Information Protection contém os elementos seguintes que pode configurar:
    
- As etiquetas são incluídas que permitem que os administradores e utilizadores classificar (e, opcionalmente, proteger) documentos e e-mails.

- Título e descrição para a barra Information Protection que os utilizadores veem nas aplicações do Office.

- A opção para definir uma etiqueta predefinida como ponto de partida para classificar documentos e e-mails.

- A opção para impor a classificação quando os utilizadores guardam documentos e enviam e-mails.

- A opção para solicitar aos utilizadores que indiquem um motivo quando estes selecionam uma etiqueta que tem um nível de sensibilidade inferior ao original.

- A opção para etiquetar automaticamente uma mensagem de e-mail com base nos respetivos anexos.

- A opção para controlar se a barra do Information Protection é apresentada em aplicativos do Office.

- A opção para controlar se o botão não reencaminhar é apresentado no Outlook.

- A opção para permitir aos utilizadores especificar suas próprias permissões para documentos.

- A opção para fornecer uma ligação de ajuda personalizada para os utilizadores.

O Azure Information Protection tem uma [política predefinida](configure-policy-default.md) que contém cinco etiquetas principais. Duas destas etiquetas contenham subetiquetas para fornecer subcategorias, quando necessário. 

Quando uma etiqueta está configurada para subetiquetas, os utilizadores não é possível selecionar a etiqueta principal, mas tem de selecionar uma das subetiquetas. Neste cenário, a etiqueta principal é suportada como um contêiner de exibição apenas para o nome e a cor.

As etiquetas do Azure Information Protection podem ser utilizadas com o intervalo completo de dados que uma organização normalmente cria e armazena, desde a classificação mais baixa de dados pessoais, à classificação mais elevada de dados altamente confidenciais. 

Pode utilizar as etiquetas predefinidas sem alterações ou pode personalizá-las, eliminá-las ou criar novas etiquetas. Para obter instruções completas, consulte [configurar a política do Azure Information Protection](configure-policy.md).

## <a name="next-steps"></a>Passos Seguintes

Para obter exemplos de como personalizar a política do Azure Information Protection e ver o comportamento resultante para os utilizadores, experimente os seguintes tutoriais:

- [Editar a política do Azure Information Protection e criar uma nova etiqueta e criar uma nova etiqueta](infoprotect-quick-start-tutorial.md)

- [Configurar definições de política do Azure Information Protection que funcionam em conjunto](infoprotect-settings-tutorial.md)
