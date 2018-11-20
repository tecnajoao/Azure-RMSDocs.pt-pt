---
title: Conceitos - etiqueta de metadados no SDK do MIP
description: Este artigo ajuda-o a compreender os metadados que é gerado pelo SDK do Microsoft Information Protection.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 11/08/2018
ms.author: tommos
ms.openlocfilehash: 9f9e4768a01d3d82f7b9563cb907533e53c7a228
ms.sourcegitcommit: 03c9d1131177041e320d1bdbbdd92852a0d1d5cd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52156859"
---
# <a name="microsoft-information-protection-sdk---metadata"></a>SDK - metadados do Microsoft Information Protection

O SDK do Microsoft Information Protection gera o conjunto de metadados que devem ser aplicado a um ficheiro. Estes metadados são uma representação da etiqueta. Este documento descreve os metadados, que o SDK gera a aplicar ao e-mail, documentos e outros registos.

## <a name="labels"></a>Etiquetas

As etiquetas no SDK do Microsoft Information Protection são aplicadas a informação para descrever a confidencialidade dessas informações. Os dados de etiqueta são mantidos para arquivo ou Registro num conjunto de pares chave-valor que descrevem a etiqueta. O nome de metadados baseia-se a seguinte estrutura:

`DefinedPrefix_ElementType_GlobalIdentifier_AttributeName`

Quando aplicados aos dados com o nome com Microsoft Information Protection, o resultado é:

`MSIP_Label_GUID_Enabled = true`

O GUID é um identificador exclusivo para cada etiqueta numa organização.

## <a name="microsoft-information-protection-sdk-metadata"></a>Metadados SDK do Microsoft Information Protection

O SDK de MIP aplica-se o seguinte conjunto de metadados.

| Atributo | Tipo de valor                 | Descrição                                                                                                                                                                                                                                        | Obrigatório |
|-----------|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| **Ativado**   | VERDADEIRO ou FALSO                 | Este atributo indica se a classificação representada por este conjunto de pares chave-valor está ativada para o item de dados. Produtos DLP normalmente validam a existência desta chave para identificar a etiqueta de classificação. | Sim       |
| **SiteId**    | GUID                          | ID do inquilino do Azure Active Directory                                                                                                                                                                                                                   | Sim       |
| **ActionId**  | GUID                          | ActionID é alterada sempre que uma etiqueta está definida. Registos de auditoria incluirá actionID antigo e novo para permitir que o encadeamento de etiquetagem de atividade para o item de dados.                                                                                 | Sim       |
| **Método**    | Standard, com privilégios ou automática        | Definido por meio de mip::AssignmentMethod                                                                                                                                                                                                                 | Não        |
| **SetDate**   | Formato de data do expandida ISO 8601 | O carimbo de hora quando a etiqueta foi definida.                                                                                                                                                                                                              | Não        |
| **Nome**      | cadeia                        | Nome de etiqueta única no inquilino. Ele não necessariamente corresponde ao nome a apresentar.                                                                                                                                                              | Não      |
| **ContentBits** | número inteiro | Máscara de bits que descreve os tipos de conteúdo a marcação que deve ser aplicada a um ficheiro. CONTENT_HEADER = 0X1, CONTENT_FOOTER = 0X2, MARCA D'ÁGUA = 0X4
 | Não |

Quando aplicada a um ficheiro, o resultado é semelhante para a tabela abaixo.

| Chave                                                         | Valor                                |
|-------------------------------------------------------------|--------------------------------------|
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled     | true                                 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate     | 2018-11-08T21:13:16-0800             |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method      | Com privilégios                           |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name        | Confidencial                         |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId      | cb46c030-1825-4E81-a295-151c039dbf02 |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits | 2                                    |
| MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId    | 88124cf5-1340-457d-90e1-0000a9427c99 |

## <a name="extending-metadata-with-custom-attributes"></a>Estendendo metadados com atributos personalizados

Metadados personalizados podem ser acrescentado através de ficheiros e política de API. Atributos personalizados tem de manter a base de `MSIP_Label_GUID` prefixo. 

Por exemplo, um aplicativo escrito pela Contoso Corporation tem de aplicar metadados que indicam qual sistema gerou um ficheiro com nome. O aplicativo pode criar uma nova etiqueta, o prefixo `MSIP_Label_GUID`. O nome do fornecedor de software e o atributo personalizado são acrescentadas para o prefixo para gerar os metadados personalizados.

```
MSIP_Label_f048e7b8-f3aa-4857-bf32-a317f4bc3f29_ContosoCorp_GeneratedBy = HRReportingSystem
```

> [!Note]
> Para manter a compatibilidade entre aplicativos comuns, o comprimento máximo para cada uma chave e um valor é 255 carateres.

## <a name="versioning"></a>Controlo de versões

Ao longo do tempo, atributos serão introduzidos, modificados ou retirados. Espera-se que aplicações vão continuar a processar estes antigo ou atributos extintos, quanto substituir o valor de uma empresa podem demorar anos.

Ao substituir um atributo com uma versão mais recente, um sufixo de versão deve ser adicionado ao atributo:

`MSIP_Label_GUID_EnabledV2 = True | False | Condition`

## <a name="email"></a>E-mail

Metadados aplicado ao e-mail mantém a formatar um par chave/valor semelhante de documentos. A principal diferença é que todos os atributos são serializados na um cabeçalho de e-mail único chamado **MSIP_Labels**. Os pares chave/valor são delimitados por ponto e vírgula e um espaço em branco e colocados no cabeçalho do novo.

Com os metadados de exemplo acima:

```
MSIP_Labels: MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Enabled=true; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SetDate=2018-11-08T21:13:16-0800; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Method=Privileged; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_Name=Confidential; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_SiteId=cb46c030-1825-4e81-a295-151c039dbf02; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ContentBits=2; MSIP_Label_2096f6a2-d2f7-48be-b329-b73aaa526e5d_ActionId=88124cf5-1340-457d-90e1-0000a9427c99
```
