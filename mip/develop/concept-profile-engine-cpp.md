---
title: Conceitos - conceitos básicos do SDK do MIP - perfil e de motor
description: Este artigo ajuda-o a compreender os conceitos SDK core chamados o perfil e o mecanismo, que são criados durante a inicialização do aplicativo.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6f11944e7cceed39423af2a8104ce044d1f6eec6
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453423"
---
# <a name="microsoft-information-protection-sdk---profile-and-engine-object-concepts"></a>Conceitos de objeto do SDK - perfil e de motor do Microsoft Information Protection

## <a name="profiles"></a>Perfis

O perfil é a classe de raiz para todas as operações no SDK do MIP. Antes de utilizar uma das APIs de três, um perfil tem de ser criado pela aplicação de cliente. Todas as operações futuras serão efetuadas pelo perfil ou por outros objetos *adicionado* ao perfil.

Existem três tipos de perfil no SDK do MIP:

- [`PolicyProfile`](reference/class_mip_policyprofile.md): A classe de perfil para a API de política de MIP.
- [`ProtectionProfile`](reference/class_mip_protectionprofile.md): A classe de perfil para a API de proteção de MIP.
- [`FileProfile`](reference/class_mip_fileprofile.md): A classe de perfil para a API de ficheiros MIP.

A API utilizada na aplicação de consumo irá determinar a classe que perfil deve ser utilizado.

O próprio perfil fornece as seguintes funcionalidades:

- Define a localização de armazenamento para o estado do SDK. Dados de estado incluem detalhes de utilizador, políticas de utilizador transferido, registos e dados de telemetria.
- Define se o estado deve ser carregado na memória ou persistido no disco.
- Processa a autenticação ao aceitar uma `mip::AuthDelegate`.
- Define o ID da aplicação e o nome amigável da aplicação consumindo o SDK.

### <a name="profile-settings"></a>Definições de perfil

- `Path`: Caminho de ficheiro em que o registo, telemetria e outras estado persistente é armazenado.
- `useInMemoryStorage`: Um bool que define se o estado deve ser armazenado na memória, ou no disco.
- `authDelegate`: Um ponteiro compartilhado da classe `mip::AuthDelegate`. 
- `consentDelegate`: Um ponteiro compartilhado da classe `mip::ConsentDelegate`. 
- `observer`: Um ponteiro compartilhado para o perfil `Observer` implementação (na `PolicyProfile`, `ProtectionProfile`, e `EngineProfile`).
- `applicationInfo`: Um `mip::ApplicationInfo` objeto. Informações sobre a aplicação que está a consumir o SDK.

## <a name="engines"></a>Mecanismos de

O ficheiro, perfil e APIs de proteção, mecanismos de fornecem uma interface para operações executadas em nome de uma identidade específica. Um mecanismo será adicionado ao objeto de perfil, para cada utilizador que inicia sessão na aplicação. Todas as operações executadas pelo motor estará no contexto de identidade.

Existem três classes de motor no SDK, um para cada API. A lista seguinte mostra as classes de motor e algumas das funções associadas a cada:

- [`mip::ProtectionEngine`]
- [`mip::PolicyEngine`](reference/class_mip_policyengine.md)
  - `ListSensitivityLabels()`: Obtém a lista de etiquetas para o mecanismo de carregá-lo.
  - `GetSensitivityLabel()`: Obtém o rótulo de conteúdo existente.
  - `ComputeActions()`: Fornecido com um ID de etiqueta e opcionais metadados, devolve a lista de ações que deve ocorrer para um item específico.
- [`mip::FileEngine`](reference/class_mip_fileengine.md)
  - `ListSensitivityLabels()`: Obtém a lista de etiquetas para o mecanismo de carregá-lo.
  - `CreateFileHandler()`: Cria um `mip::FileHandler` para um ficheiro específico ou fluxo.

### <a name="engine-states"></a>Motor de Estados

Um motor de pode ter um de dois Estados:

- `CREATED`: Criado indica que o SDK tem informações suficientes estado local depois de chamar os serviços de back-end necessários.
- `LOADED`: O SDK criou as estruturas de dados necessários para o mecanismo de estar operacional.

Um motor tem de ser criado e carregado para executar qualquer operação. O `Profile` classe expõe alguns métodos de gestão do motor: `AddEngineAsync`, `RemoveEngineAsync`, e `UnloadEngineAsync`.

A tabela seguinte descreve os Estados possíveis motor e qual o método pode altera esse Estado.

|         | NENHUM              | CRIADO           | CARREGADO         |
|---------|-------------------|-------------------|----------------|
| NENHUM    |                   |                   | AddEngineAsync |
| CRIADO | DeleteEngineAsync |                   | AddEngineAsync |
| CARREGADO  | DeleteEngineAsync | UnloadEngineAsync |                |

### <a name="engine-id"></a>ID do motor

Cada motor tem um identificador exclusivo, `id`, que é utilizado em todas as operações de gestão do motor. A aplicação pode fornecer um `id` ou o SDK irá gerar um novo identificador exclusivo, se não for fornecido pela aplicação. Todas as outras propriedades de mecanismo (por exemplo, endereço de e-mail nas informações de identidade) são payloads opacos para o SDK. O SDK não realizar qualquer lógica para manter qualquer uma das outras propriedades exclusivas ou impor outras restrições.

### <a name="engine-management-methods"></a>Métodos de gestão do motor

Conforme mencionado acima, existem três métodos de gestão do motor no SDK: `AddEngineAsync`, `DeleteEngineAsync`, e `UnloadEngineAsync`.

#### <a name="addengineasync"></a>AddEngineAsync

Este método carrega um motor de existente ou cria um novo, se ainda não existir no estado local.

Se a aplicação não fornecer um `id`, `AddEngineAsync` gera um novo `id`. Em seguida, verifica se um motor de com que `id` já existe no estado local. Se assim for, ele carrega desse motor. Se o motor faz *não* existe no estado local, um novo mecanismo é criado chamando as APIs necessárias e os serviços de back-end.

Em ambos os casos, se o método tiver êxito, o mecanismo é carregada e pronta a utilizar.

#### <a name="deleteengineasync"></a>DeleteEngineAsync

Elimina o motor com o determinado `id`. Todos os rastreios do motor de são removidos do Estado local.

#### <a name="unloadengineasync"></a>UnloadEngineAsync

Descarrega as estruturas de dados na memória para o motor com o determinado `id`. O estado local desse mecanismo ainda está intacto e pode ser recarregado com `AddEngineAsync`.

Este método permite que o aplicativo ser criterioso sobre o uso de memória, pelos mecanismos de descarregamento que não devem ser utilizados em breve.

## <a name="next-steps"></a>Passos Seguintes

- Em seguida, saiba mais sobre [conceitos de autenticação](concept-authentication-cpp.md) e [observadores](concept-async-observers.md). MIP fornece um modelo de autenticação extensível, enquanto os observadores são utilizados para fornecer notificações de eventos para eventos assíncronos. Ambos são fundamentais e aplicam a todos os conjuntos de API de MIP.
- Em seguida, trabalhar com os conceitos de perfil e um mecanismo para o ficheiro, a política e a APIs de proteção
  - [Conceitos de perfil de API de ficheiros](concept-profile-engine-file-profile-cpp.md)
  - [Conceitos de motor de API de ficheiros](concept-profile-engine-file-engine-cpp.md)
  - [Conceitos de perfil de política de API](concept-profile-engine-file-profile-cpp.md)
  - [Conceitos de motor de política de API](concept-profile-engine-file-engine-cpp.md)
  - [Conceitos de perfil de API de proteção](concept-profile-engine-file-profile-cpp.md)
  - [Conceitos de motor de API de proteção](concept-profile-engine-file-engine-cpp.md)  
