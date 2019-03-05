---
title: Conceitos - APIs no SDK do MIP.
description: Este artigo ajuda-o a compreender os 3 tipos de APIs no SDK do MIP, como estão relacionadas e casos de utilização para uso de cada.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 10/16/2018
ms.author: mbaldwin
ms.openlocfilehash: d4bef66f8e3d808b195ac49f7bb42ab0eb62b7d5
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57330173"
---
# <a name="microsoft-information-protection-sdk---api-concepts"></a>Microsoft Information Protection SDK - conceitos de API

O SDK de proteção de informações da Microsoft (MIP) é composto por três APIs, conforme mostrado no diagrama seguinte:

[![Diagrama da API do SDK MIP](media/concept-apis-use-cases/mip-sdk-components.png)](media/concept-apis-use-cases/mip-sdk-components.png#lightbox)

Consoante as necessidades da sua aplicação, poderá querer de interface na camada de API de ficheiros ou poderá ter de trabalhar diretamente com as camadas de política ou a API de proteção.

## <a name="file-api"></a>API de Ficheiros

A API de ficheiros é uma abstração da proteção e a política de APIs. Ele fornece fácil de usar interfaces para ler as etiquetas do serviço, aplicar etiquetas a tipos de ficheiro definido e ler as etiquetas desses tipos de ficheiros. A API de ficheiros será usada por qualquer serviço ou de aplicativo onde:

- está envolvido um tipo de ficheiro suportados
- as etiquetas devem ser lidos ou gravadas
- conteúdo tem de ser protegido ou desencriptado

### <a name="file-api-use-cases"></a>Casos de utilização de API de ficheiros

- É um engenheiro de software numa instituição de serviços financeiros. Não se esqueça de que os dados a partir de seus aplicativos de LOB, normalmente exportados no formato do Excel, estão identificados no exportação com base no conteúdo. A API de ficheiros pode ser utilizada para listar as etiquetas disponíveis, em seguida, aplicar a etiqueta adequada para um formato de ficheiro suportados.

- Um mediador de segurança de acesso de nuvem (CASB) desenvolvidas pela sua organização. Peça aos seus clientes para a capacidade de aplicar etiquetas MIP a documentos do Microsoft Office e PDF. A API de ficheiros permite-lhe apresentar uma lista de etiquetas configuradas, em seguida, permitir que os clientes podem criar regras que aplicam uma etiqueta específica. A API de ficheiros, levando a ID de etiqueta, lidaria com os restantes para ficheiros que cumpram os critérios do cliente.

- Sua organização fornece uma solução de prevenção de perda de dados com base no serviço ou um CASB que monitoriza aplicações SaaS para a atividade de arquivos. Para reduzir o risco de perda de dados ou exposição em que os dados estão protegidos com MIP, seu serviço tem de analisar o conteúdo de ficheiros protegidos. Usando a API de ficheiros para os formatos suportados, quando o serviço é um utilizador com privilégios, ele pode:

  1. Remover a proteção
  2. analisar o conteúdo para conteúdos sensíveis ou confidenciais restritos
  3. rejeitar o resultado de texto sem formatação
  4. aplicar uma regra de serviço para o relatório ou remediar o risco, se foi encontrado

## <a name="policy-api"></a>Política de API

A API de política ou o motor de política Universal (UPE), fornece a capacidade para os desenvolvedores de software obter as políticas de etiquetas para um utilizador específico. Ele pode, em seguida, "computação" as ações essas etiquetas devem demorar.

A API de política é utilizada principalmente por aplicações de cliente, onde o desenvolvedor controla o formato de ficheiro e de interface. Também é utilizado quando o único requisito é obter a política de utilizador e não os ficheiros de etiqueta diretamente. 

### <a name="policy-api-use-cases"></a>Casos de utilização de API de política

- Software de 3D design que usa um formato de arquivos proprietários desenvolvidas pela sua organização. Os seus clientes utilizam MIP e pretendem aplicar etiquetas nativamente através da sua aplicação. Como o engenheiro de software, usa a API de política e um controle personalizado para apresentar as etiquetas disponíveis para o usuário autenticado. Depois do usuário seleciona uma etiqueta, chama o método de ação de computação da API. A API informa exatamente o que deve ser aplicado com relação às General metadados, a marcação de conteúdo e a proteção.

- Um serviço de prevenção de perda de dados (DLP), que permite que os clientes configurar políticas DLP através de um portal de administração central desenvolvidas pela sua organização. Terá dos clientes que utilizam MIP e que precisam ler ou aplicar etiquetas AIP, como parte de políticas DLP. Como engenheiro de software, pode usar a API de política para obter uma lista de etiquetas para a organização do cliente. Em seguida, pode ler essas etiquetas como parte de uma regra DLP ou aplicar as informações da etiqueta como parte de uma ação de regra.

## <a name="protection-api"></a>API de proteção

A API de proteção fornece a capacidade para os desenvolvedores de software converter os fluxos de texto sem formatação em fluxos geridos de direitos e vice-versa.

### <a name="protection-api-use-cases"></a>Casos de utilização de API de proteção

- Software de impressão 3d com um formato de arquivo proprietárias sejam desenvolvidas pela sua organização. Que pretende utilizar MIP para proteger o ficheiro, pelo que pode ser impresso apenas por utilizadores específicos. Usando a API de proteção, pode aplicar a proteção para o ficheiro para que consumidores autorizados possam abrir e imprimi-lo. 

- Sua organização desenvolve uma solução de deteção de dados Eletrónicos que processa as caixas de correio do Exchange e. Arquivos PST. Seu aplicativo precisa permitir que os utilizadores desencriptar mensagens para executar a deteção de dados eletrónicos. Utilizar um analisador de mensagens/RPMSG personalizada e uma conta suficientemente com privilégios, pode utilizar a API de RMS para:
  - desencriptar o ficheiro encriptado
  - analisar o conteúdo
  - rejeição se fora do âmbito, ou o pacote em caso de âmbito

## <a name="next-steps"></a>Passos Seguintes

Agora que tem uma ideia geral de APIs de MIP disponíveis e como eles são usados, prosseguir [conceitos de objeto de perfil e de motor](concept-profile-engine-cpp.md). Esses conceitos são fundamentais e aplicam a todos os conjuntos de API de MIP.
