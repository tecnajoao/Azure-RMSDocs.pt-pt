---
title: SDK de MIP para referência do C++
description: SDK de MIP para referência do C++
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 1db2faeca6c2ff00a0053a7d65d16872190d306f
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574062"
---
# <a name="mip-sdk-for-c-reference"></a>SDK de MIP para referência do C++

A Microsoft Information Protection (MIP) do SDK para C++ permite aos desenvolvedores de gerenciar e aplicar políticas de proteção de dados para dados e outros ativos digitais.

O SDK de MIP para C++ inclui:

- [Enumerações e estruturas](mip-enums-and-structs.md)
- [Funções](mip-functions.md)
- As seguintes classes:

 Classe                         | Descrição                                
--------------------------------|---------------------------------------------
classe mip::AccessDeniedError  |  O utilizador não foi possível obter acesso ao conteúdo. Por exemplo, não existem permissões, conteúdos revogaram.
classe mip::Action  |  Interface para uma ação. Cada ação se traduz numa etapa que é necessário realizar pela aplicação para aplicar a etiqueta (conforme definido na política)
classe mip::AddContentFooterAction  |  Uma classe de ação que especifica a adicionar um rodapé de conteúdo ao documento.
class mip::AddContentHeaderAction  |  Uma classe de ação que especifica o cabeçalho de conteúdo a adicionar.
classe mip::AddWatermarkAction  |  Uma classe de ação que especifica o limite de tamanho de adição.
classe mip::AdhocProtectionRequiredError  |  Proteção do ad hoc deve ser definida para concluir a ação no ficheiro.
classe mip::ApplyLabelAction  |  Aplicar ações de etiqueta requer que o aplicativo de chamada para aplicar uma etiqueta específica.
classe mip::AuthDelegate  |  Delegado para autenticação operações relacionadas com.
classe mip::AuthDelegate::OAuth2Challenge  |  uma classe que contém todas as informações necessárias do aplicativo de chamada para gerar um token oauth2.
classe mip::AuthDelegate::OAuth2Token  |  Uma classe de definir a forma como o SDK de MIP espera que o token oauth2 a serem passados de volta para o SDK.
classe mip::BadInputError  |  Erro entrado ruim, lançado quando a entrada a uma API do SDK é inválida.
classe mip::ClassificationRequest  |  Classe que contém o pedido de uma chamada de classificação no estado de execução.
classe mip::ClassificationResult  |  Classe que contém o resultado de uma chamada de classificação no estado de execução.
classe mip::ConsentDelegate  |  Delegado, consentimento operações relacionadas com.
classe mip::ConsentDeniedError  |  Uma operação que é necessário o consentimento do utilizador não foi concedida ao consentimento.
classe mip::ContentLabel  |  Abstração para uma etiqueta do Microsoft Information Protection que é aplicada a uma parte do conteúdo, normalmente, um documento.
classe mip::CustomAction  |  [CustomAction](class_mip_customaction.md) é uma classe de ação genérica que captura todas as propriedades secundárias da ação como uma matriz de propriedades. O chamador é da responsabilidade compreender o significado da ação.
classe mip::Error  |  Classe para todos os erros que serão reportadas (emitida ou devolveu) base do MIP SDK.
classe mip::ExecutionState  |  Interface para todos os Estados necessários para executar o motor.
classe mip::FileEngine  |  Essa classe fornece uma interface para todas as funções de motor.
classe mip::FileEngine::Settings  | _Ainda não documentado._
classe mip::FileExecutionState  | _Ainda não documentado._
classe mip::FileHandler  |  Interface para o ficheiro de todas as funções de manipulação.
classe mip::FileHandler::Observer  |  [Observador](class_mip_filehandler_observer.md) interface para que os clientes obter notificações de eventos relacionados com o manipulador de arquivo.
classe mip::FileIOError  |  Erro de e/s de ficheiros.
classe mip::FileProfile  |  [FileProfile](class_mip_fileprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar.
classe mip::FileProfile::Observer  |  [Observador](class_mip_fileprofile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
classe mip::FileProfile::Settings  |  [As definições](class_mip_fileprofile_settings.md) utilizada pelo [FileProfile](class_mip_fileprofile.md) durante sua criação e ao longo de seu ciclo de vida.
classe mip::HttpDelegate  |  Interface para substituir o tratamento de HTTP.
classe mip::HttpOperation  |  Interface que descreve uma única operação de HTTP, implementada pela aplicação de cliente, ao substituir [HttpDelegate](class_mip_httpdelegate.md).
classe mip::HttpRequest  |  Interface que descreve um único pedido HTTP.
classe mip::HttpResponse  |  Interface que descreve uma única resposta HTTP, implementada pela aplicação de cliente, ao substituir [HttpDelegate](class_mip_httpdelegate.md).
classe mip::Identity  |  Abstração para a identidade.
classe mip::InternalError  |  Erro interno. Este erro é apresentado quando algo inesperado acontece durante a execução.
classe mip::JustificationRequiredError  | _Ainda não documentado._
classe mip::JustifyAction  |  Justificar [ação](class_mip_action.md) necessita de fornecer uma justificação para baixar uma etiqueta e definir a resposta no estado de execução.
classe mip::Label  |  Abstração para um único rótulo do Microsoft Information Protection.
classe mip::LabelingOptions  |  Interface para configurar opções de etiquetas para os métodos de SetLabel/DeleteLabel.
classe mip::LoggerDelegate  |  Uma classe que define a interface para o agente de log MIP SDK.
classe mip::MetadataAction  |  Uma [ação](class_mip_action.md) que adiciona informações de metadados para o conteúdo.
classe mip::NetworkError  |  Erro de sistema de rede. Causado por um comportamento inesperado ao efetuar chamadas de rede para pontos finais de serviço.
classe mip::NoAuthTokenError  |  O utilizador não foi possível obter acesso ao conteúdo devido à falta de token de autenticação.
classe mip::NoPermissionsError  |  O utilizador não foi possível obter acesso ao conteúdo. Por exemplo, não existem permissões, conteúdos revogaram.
classe mip::NoPolicyError  |  Política de inquilino não está configurada para/etiquetas de classificação.
classe mip::NotSupportedError  |  A operação pedida pelo aplicativo não é suportada pelo SDK.
classe mip::OperationCancelledError  |  A operação foi cancelada.
classe mip::PolicyEngine  |  Essa classe fornece uma interface para todas as funções de motor.
classe mip::PolicyEngine::Settings  |  Especifica as definições associadas com uma [PolicyEngine](class_mip_policyengine.md).
classe mip::PolicyHandler  |  Essa classe fornece uma interface para todas as funções do manipulador de política num arquivo.
classe mip::PolicyProfile  |  [PolicyProfile](class_mip_policyprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar. Um aplicativo típico irá apenas precisa de um [PolicyProfile](class_mip_policyprofile.md) , mas ele pode criar vários perfis, se for necessário.
classe mip::PolicyProfile::Observer  |  [Observador](class_mip_policyprofile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
classe mip::PolicyProfile::Settings  |  [As definições](class_mip_policyprofile_settings.md) utilizada pelo [PolicyProfile](class_mip_policyprofile.md) durante sua criação e ao longo de seu ciclo de vida.
classe mip::PolicySyncError  |  Falha ao tentar sincronizar dados de política.
classe mip::PrivilegedRequiredError  |  Etiqueta atual foi atribuída como uma operação com privilégios (o equivalente a uma operação de administrador), portanto não pode ser substituído.
classe mip::ProtectAdhocAction  |  Uma classe de ação que especifica a adição de ad hoc proteção para o documento.
classe mip::ProtectByTemplateAction  |  Uma classe de ação que especifica a adição de proteção pelo modelo para o documento.
classe mip::ProtectDoNotForwardAction  |  Uma classe de ação que especifica a adicionar não reencaminhar proteção para o documento.
classe mip::ProtectionDescriptor  |  Descrição de proteção associada a uma parte do conteúdo.
classe mip::ProtectionDescriptorBuilder  |  Constrói uma [ProtectionDescriptor](class_mip_protectiondescriptor.md) que descreve a proteção associada a uma parte do conteúdo.
classe mip::ProtectionEngine  |  Gere as ações relacionadas com a proteção relacionados com uma identidade específica.
classe mip::ProtectionEngine::Observer  |  Interface que recebe notificações relacionadas com a [ProtectionEngine](class_mip_protectionengine.md).
classe mip::ProtectionEngine::Settings  |  [As definições](class_mip_protectionengine_settings.md) utilizada pelo [ProtectionEngine](class_mip_protectionengine.md) durante sua criação e ao longo de seu ciclo de vida.
classe mip::ProtectionHandler  |  Gere as ações relacionadas com a proteção para uma configuração de proteção específico.
classe mip::ProtectionHandler::Observer  |  Interface que recebe notificações relacionadas com a [ProtectionHandler](class_mip_protectionhandler.md).
classe mip::ProtectionProfile  |  [ProtectionProfile](class_mip_protectionprofile.md) é a classe de raiz para a execução de operações de proteção.
classe mip::ProtectionProfile::Observer  |  Interface que recebe notificações relacionadas com a [ProtectionProfile](class_mip_protectionprofile.md).
classe mip::ProtectionProfile::Settings  |  [As definições](class_mip_protectionprofile_settings.md) utilizada pelo [ProtectionProfile](class_mip_protectionprofile.md) durante sua criação e ao longo de seu ciclo de vida.
classe mip::ProxyAuthenticationError  |  Falha de autenticação de proxy.
class mip::RecommendLabelAction  |  Recomendamos a ações de etiqueta destina-se a sugerir uma etiqueta para os utilizadores. Suprimir esta chamada depois que um utilizador ignora a etiqueta recomendada deve ser feito por meio de ações suportadas sobre o estado de execução.
class mip::RemoveContentFooterAction  |  Uma classe de ação que especifica a remover o rodapé de conteúdo do documento.
class mip::RemoveContentHeaderAction  |  Uma classe de ação que especifica a remover o cabeçalho de conteúdo do documento.
class mip::RemoveProtectionAction  |  Uma classe de ação que especifica a remoção da proteção do documento.
class mip::RemoveWatermarkAction  |  Uma classe de ação que especifica a remover as marcas de água do documento.
classe mip::SensitivityTypesRulePackage  | _Ainda não documentado._
classe mip::ServiceDisabledError  |  O utilizador não foi possível obter acesso ao conteúdo devido a um serviço que está a ser desabilitado.
classe mip::Stream  |  Uma classe que define a interface entre o SDK de MIP e baseada em fluxo conteúdo de mensagens em fila.
classe mip::TaskDispatcherDelegate  |  Uma classe que define a interface ao dispatcher de tarefa MIP SDK.
classe mip::TransientNetworkError  |  Erro de sistema de rede transitório. Causado por um comportamento inesperado ao efetuar chamadas de rede para pontos finais de serviço. A operação pode ser repetida como este erro é um erro transitório.
classe mip::UserRights  |  Um grupo de utilizadores e os direitos associados aos mesmos.
classe mip::UserRoles  |  Um grupo de utilizadores e as funções associadas a eles.