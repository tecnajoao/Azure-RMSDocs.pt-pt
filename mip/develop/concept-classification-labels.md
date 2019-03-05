---
title: Conceitos - etiquetas de classificação
description: Este artigo ajuda-o a compreender como os rótulos são usados para classificação de dados.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: e1101bd505a35e02fdeeed032d5dec61364bfb8d
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333680"
---
# <a name="microsoft-information-protection-sdk---classification-label-concepts"></a>SDK - conceitos de etiqueta de classificação do Microsoft Information Protection

Como parte de uma estratégia de proteção de dados abrangente, as organizações devem implementar um sistema de classificação de dados que descreve os níveis de sensibilidade dos dados dentro da organização e, em seguida, mapear os atributos de documento para essas classificações.

Atributos relacionados com a classificação normalmente envolvem a **risco** para a organização se esse documento ou dados devem ser perdidos ou vistos por assuntos indesejados. No sistema de familiar dos Estados Unidos government classificação, existem três níveis de classificação. Cada um tem uma definição que descreve quando deve ser aplicada essa classificação:

* **Principais segredo**: Deve ser aplicada a informações, a divulgação não autorizada que razoavelmente poderia ser esperada provocar danos excepcionalmente graves à segurança nacional que a autoridade de classificação original é capaz de identificar ou forneça uma descrição.
* **Segredo**: Deve ser aplicada a informações, a divulgação não autorizada que razoavelmente poderia ser esperada para causar graves danos à segurança nacional que a autoridade de classificação original é capaz de identificar ou forneça uma descrição.
* **Confidencial**: Deve ser aplicada a informações, a divulgação não autorizada que razoavelmente poderia ser esperada para causar danos à segurança nacional que a autoridade de classificação original é capaz de identificar ou forneça uma descrição.
* **Não classificado**: Isso não é, na verdade, uma classificação, mas em vez disso, a ausência de uma das três acima.

Num aplicativo de setor privado ou comercial, podemos pode definir uma lista semelhante para a predefinição no serviço de proteção de informações do Azure, com valores monetários anexados.

* **Altamente confidencial**: Deve ser aplicada a informações, a divulgação não autorizada que razoavelmente poderia ser esperada para fazer com que a maiores do que USD $1 milhão de danos.
* **Confidencial**: Deve ser aplicada a informações, a divulgação não autorizada que razoavelmente poderia ser esperada para provocar danos maiores do que USD $100 mil.
* **Geral**: Deve ser aplicada a informações, a divulgação não autorizada que razoavelmente poderia ser esperada para provocar danos mensuráveis pequeno.
* **Público**: Deve ser aplicada a informações destinadas para consumo público, externo. 
* **Não comerciais**: Deve ser aplicada a informações que não está relacionado com o negócio da empresa, direto ou indireto.

Cada classificação descreve o risco para a empresa em caso de divulgação não autorizada de informações. Depois de identificar estes classificação e condições, devem ser identificados os atributos que ajudam os proprietários de dados para compreender qual a classificação a aplicar.

## <a name="labeling"></a>Etiquetagem

O ato de associar uma classificação de dados com um conjunto de informações é referido como **etiquetagem**. Uma vez que o SDK de MIP está lidando na aplicação de classificação **etiquetas** para documentos, não veja classificações, mas em vez disso, as etiquetas. Um utilizador ou processo já foi **classificados** os dados com base no conhecimento das informações: Irá utilizar o SDK de MIP **etiqueta** as informações.

## <a name="labels-in-the-mip-sdk"></a>Etiquetas no SDK do MIP

As etiquetas são um componente fundamental do MIP SDK. Etiquetas de conduzir a marcação, proteção, e marcação de conteúdo de todos os documentos tocado pelo SDK. O SDK pode:

* Aplicar etiquetas a documentos
* Leia as etiquetas existentes em documentos
* Alterar uma justificação de etiqueta e mandado existente quando requerido pela política
* Remover uma etiqueta de um documento

A etiqueta será aplicada a proteção e a marcação de conteúdo com base na etiqueta de configuração definidas no Centro de conformidade e de segurança administradores. 

## <a name="miplabel-vs-mipcontentlabel"></a>mip::Label vs. mip::ContentLabel

Existem dois tipos de etiqueta no SDK do MIP. `Label` e `ContentLabel`.

* Etiqueta: Uma etiqueta que pode ser aplicada por um utilizador ou processo, conforme definido na política organizacional.
* ContentLabel: Uma etiqueta que já existe um documento ou informações. Pode ser de leitura, atualizado ou removido. 

Em outras palavras, o `ContentLabel` é um `Label` que tenha sido aplicada a uma parte da informação.

## <a name="metadata"></a>Metadados

O SDK também suporte a adição de metadados adicionais para documentos sob a forma de pares chave/valor. Se sua organização tiver classificações secundárias ou etiquetas que descrevem as informações de forma mais específica, o SDK pode ser utilizado para aplicar esses metadados.

## <a name="next-steps"></a>Passos Seguintes

Para obter mais detalhes sobre o sistema de classificação do Governo dos Estados Unidos, consulte https://www.gpo.gov/fdsys/pkg/FR-2010-01-05/html/E9-31418.htm.
