---
title: Conceitos - APIs no SDK do MIP.
description: Este artigo ajuda-o a compreender os 3 tipos de APIs no SDK do MIP, como estão relacionadas e casos de utilização para uso de cada.
services: information-protection
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 02fc1ef3c53cd94c35943a4a093c42968c251cdf
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47214970"
---
# <a name="mip-sdk-apis"></a>APIs do SDK de MIP

O SDK de MIP é composto por três APIs:

- [API de proteção](#protection-api)
- [Política de API](#policy-api)
- [API de ficheiros](#file-api)

## <a name="protection-api"></a>API de proteção

A API de proteção fornece a capacidade para os desenvolvedores de software converter os fluxos de texto sem formatação em fluxos geridos de direitos e vice-versa.

### <a name="protection-api-use-cases"></a>Casos de utilização de API de proteção

- Software de impressão 3d com um formato de arquivo proprietárias sejam desenvolvidas pela sua organização. Que pretende utilizar MIP para proteger o ficheiro, pelo que pode ser impresso apenas por utilizadores específicos. Usando a API de proteção, pode aplicar a proteção para o ficheiro para que os consumidores autorizados seria capaz de abrir e/ou impressão. 

- Uma solução de deteção de dados Eletrónicos que processa as caixas de correio do Exchange e arquivos PST desenvolvidas pela sua organização. Seu aplicativo deve ser capaz de utilizador para desencriptar mensagens para executar totalmente a deteção de dados eletrónicos. Utilizar um analisador de mensagens/RPMSG personalizada e uma conta privilegiada suficientemente, poderia usar a API de RMS para desencriptar o ficheiro encriptado, verificar o conteúdo e eliminar se fora do âmbito ou pacote em caso de âmbito.

## <a name="policy-api"></a>Política de API

A API de política ou o motor de política Universal (UPE), fornece a capacidade para os desenvolvedores de software obter as políticas de etiquetas para um utilizador específico, em seguida, para as ações de "computação" essas etiquetas deve demorar.

A API de política irá ser aproveitada principalmente por aplicações cliente em que o desenvolver controla o formato de ficheiro e de interface, ou onde o único requisito é obter a política de utilizador e não necessariamente para etiquetar ficheiros diretamente. 

### <a name="policy-api-use-cases"></a>Casos de utilização de API de política

- Software de 3D design que usa um formato de arquivos proprietários desenvolvidas pela sua organização. Os clientes utilizam o Microsoft Information Protection e querem ser capazes de aplicar etiquetas nativamente através da sua aplicação. Como o engenheiro de software, usaria a API de política e um controle personalizado para apresentar as etiquetas disponíveis para o usuário autenticado. Assim que o usuário seleciona uma etiqueta, chamaria o método de ação de computação da API de saber exatamente o que deve ser aplicado com relação às General metadados, a marcação de conteúdo e a proteção.

- Um serviço DLP que permite que os clientes configurar políticas DLP através de um portal de administração central desenvolvidas pela sua organização. Terá dos clientes que utilizam o Microsoft Information Protection e gostariam de conseguir ler ou aplicar etiquetas AIP como parte de políticas DLP. Como o engenheiro de software, pode usar a API de política para obter uma lista de etiquetas de organização do cliente, em seguida, leia essas etiquetas como parte de uma regra DLP ou aplicar as informações da etiqueta como parte de uma ação de regra.

## <a name="file-api"></a>API de ficheiros

A API de ficheiros é uma abstração da proteção e a política de APIs. Ele fornece fácil de usar interfaces para a leitura de etiquetas de serviço, aplicar etiquetas a tipos de ficheiros definidos, bem como as etiquetas de leitura desses tipos de ficheiros. A API de ficheiros irá ser utilizada por qualquer serviço ou aplicação onde está envolvido um tipo de ficheiro suportados e as etiquetas devem ser lidos ou gravadas ou conteúdo protegido ou desencriptados.

### <a name="file-api-use-cases"></a>Casos de utilização de API de ficheiros

- É um engenheiro de software numa instituição de serviços financeiros. Não se esqueça de que os dados a partir de seus aplicativos de LOB, normalmente exportados no formato do Excel, estão identificados no exportação com base no conteúdo. API de ficheiros pode ser utilizado para listar as etiquetas disponíveis, em seguida, para aplicar a etiqueta adequada para um formato de ficheiro suportados.

- Um mediador de segurança de acesso de nuvem (CASB) desenvolvidas pela sua organização. Peça aos seus clientes para a capacidade de aplicar etiquetas MIP a documentos do Microsoft Office e PDF. A API de ficheiros possibilitará que apresentar uma lista de etiquetas configuradas, em seguida, permitem que os clientes podem criar regras que seriam aplicada a etiqueta pretendida. Ficheiro de API, levando a ID de etiqueta, lidaria com os restantes para ficheiros que cumpram os critérios do cliente.

- Sua organização fornece uma solução de prevenção de perda de dados baseada em serviços e/ou um CASB que monitoriza aplicações SaaS para a atividade de arquivos. Para reduzir o risco de perda de dados ou exposição em que os dados estão protegidos com MIP, seu serviço tem de ser capaz de analisar o conteúdo de ficheiros protegidos. Usando a API de ficheiros para os formatos suportados, quando o serviço é um utilizador com privilégios, pode remover a proteção, procure o conteúdo restrito ou conteúdo confidencial, descartar o resultado de texto sem formatação e aplicar uma regra de serviço para o relatório ou remediar o risco de se encontrar.
