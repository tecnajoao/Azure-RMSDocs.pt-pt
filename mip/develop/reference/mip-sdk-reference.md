---
title: SDK de MIP para referência do C++
description: SDK de MIP para referência do C++
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: cae7955684d0fae0f61e2a7319cbb036263e129b
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650599"
---
# <a name="mip-sdk-for-c-reference"></a>SDK de MIP para referência do C++

A Microsoft Information Protection (MIP) do SDK para C++ permite aos desenvolvedores de gerenciar e aplicar políticas de proteção de dados para dados e outros ativos digitais.  

O SDK de MIP para C++ inclui:

- [Enumerações e estruturas](mip-enums-and-structs.md)
- [Funções](mip-functions.md)
- As seguintes classes:

| Nome de Namespace::Class | Descrição |
| :----------|:------------|
[mip::AccessDeniedError](class_mip_AccessDeniedError.md)  |  O utilizador não foi possível obter acesso ao conteúdo. Por exemplo, não existem permissões, conteúdos revogaram.
[mip::Action](class_mip_Action.md)  |  Interface para uma ação. Cada ação se traduz numa etapa que é necessário realizar pela aplicação para aplicar a etiqueta (conforme definido na política)
[mip::AddContentFooterAction](class_mip_AddContentFooterAction.md)  |  Uma classe de ação que especifica a adicionar um rodapé de conteúdo ao documento.
[mip::AddContentHeaderAction](class_mip_AddContentHeaderAction.md)  |  Uma classe de ação que especifica o cabeçalho de conteúdo a adicionar.
[mip::AddWatermarkAction](class_mip_AddWatermarkAction.md)  |  Uma classe de ação que especifica o limite de tamanho de adição.
[mip::ApplyLabelAction](class_mip_ApplyLabelAction.md)  |  Aplicar ações de etiqueta requer que o aplicativo de chamada para aplicar uma etiqueta específica.
[mip::AuthDelegate](class_mip_AuthDelegate.md)  |  Delegado para autenticação operações relacionadas com.
[mip::BadInputError](class_mip_BadInputError.md)  |  Erro entrado ruim, lançado quando a entrada a uma API do SDK é inválida.
[mip::ClassificationRequest](class_mip_ClassificationRequest.md)  |  Classe que contém o pedido de uma chamada de classificação no estado de execução.
[mip::ClassificationResult](class_mip_ClassificationResult.md)  |  Classe que contém o resultado de uma chamada de classificação no estado de execução.
[mip::ConsentDelegate](class_mip_ConsentDelegate.md)  |  Delegado, consentimento operações relacionadas com.
[mip::ConsentDeniedError](class_mip_ConsentDeniedError.md)  |  Uma operação que é necessário o consentimento do utilizador não foi concedida ao consentimento.
[mip::ContentLabel](class_mip_ContentLabel.md)  |  Abstração para uma etiqueta do Microsoft Information Protection que é aplicada a uma parte do conteúdo, normalmente, um documento.
[mip::CustomAction](class_mip_CustomAction.md)  |  [CustomAction](class_mip_customaction.md) é uma classe de ação genérica que captura todas as propriedades secundárias da ação como uma matriz de propriedades. O chamador é da responsabilidade compreender o significado da ação.
[mip::Error](class_mip_Error.md)  |  Classe para todos os erros que serão reportadas (emitida ou devolveu) base do MIP SDK.
[mip::ExecutionState](class_mip_ExecutionState.md)  |  Interface para todos os Estados necessários para executar o motor.
[mip::FileEngine](class_mip_FileEngine.md)  |  Essa classe fornece uma interface para todas as funções de motor.
[mip::FileExecutionState](class_mip_FileExecutionState.md)  | _Ainda não documentado._
[mip::FileHandler](class_mip_FileHandler.md)  |  Interface para o ficheiro de todas as funções de manipulação.
[mip::FileIOError](class_mip_FileIOError.md)  |  Erro de e/s de ficheiros.
[mip::FileProfile](class_mip_FileProfile.md)  |  [FileProfile](class_mip_fileprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar.
[mip::HttpDelegate](class_mip_HttpDelegate.md)  |  Interface para substituir o tratamento de HTTP.
[mip::HttpRequest](class_mip_HttpRequest.md)  |  Interface que descreve um único pedido HTTP.
[mip::HttpResponse](class_mip_HttpResponse.md)  |  Interface que descreve uma única resposta HTTP, implementada pela aplicação de cliente, ao substituir [HttpDelegate](class_mip_httpdelegate.md).
[mip::Identity](class_mip_Identity.md)  |  Abstração para a identidade.
[mip::InternalError](class_mip_InternalError.md)  |  Erro interno. Este erro é apresentado quando algo inesperado acontece durante a execução.
[mip::JustificationRequiredError](class_mip_JustificationRequiredError.md)  | _Ainda não documentado._
[mip::JustifyAction](class_mip_JustifyAction.md)  |  Justificar [ação](class_mip_action.md) necessita de fornecer uma justificação para baixar uma etiqueta e definir a resposta no estado de execução.
[mip::Label](class_mip_Label.md)  |  Abstração para um único rótulo do Microsoft Information Protection.
[mip::LabelingOptions](class_mip_LabelingOptions.md)  |  Interface para configurar opções de etiquetas para os métodos de SetLabel/DeleteLabel.
[mip::LoggerDelegate](class_mip_LoggerDelegate.md)  |  Uma classe que define a interface para o agente de log MIP SDK.
[mip::MetadataAction](class_mip_MetadataAction.md)  |  Uma [ação](class_mip_action.md) que adiciona informações de metadados para o conteúdo.
[mip::NetworkError](class_mip_NetworkError.md)  |  Erro de sistema de rede. Causado por um comportamento inesperado ao efetuar chamadas de rede para pontos finais de serviço.
[mip::NoAuthTokenError](class_mip_NoAuthTokenError.md)  |  O utilizador não foi possível obter acesso ao conteúdo devido à falta de token de autenticação.
[mip::NoPermissionsError](class_mip_NoPermissionsError.md)  |  O utilizador não foi possível obter acesso ao conteúdo. Por exemplo, não existem permissões, conteúdos revogaram.
[mip::NoPolicyError](class_mip_NoPolicyError.md)  |  Política de inquilino não está configurada para/etiquetas de classificação.
[mip::NotSupportedError](class_mip_NotSupportedError.md)  |  A operação pedida pelo aplicativo não é suportada pelo SDK.
[mip::PolicyEngine](class_mip_PolicyEngine.md)  |  Essa classe fornece uma interface para todas as funções de motor.
[mip::PolicyHandler](class_mip_PolicyHandler.md)  |  Essa classe fornece uma interface para todas as funções do manipulador de política num arquivo.
[mip::PolicyProfile](class_mip_PolicyProfile.md)  |  [PolicyProfile](class_mip_policyprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar. Um aplicativo típico irá apenas precisa de um [PolicyProfile](class_mip_policyprofile.md) , mas ele pode criar vários perfis, se for necessário.
[mip::PolicySyncError](class_mip_PolicySyncError.md)  |  Falha ao tentar sincronizar dados de política.
[mip::PrivilegedRequiredError](class_mip_PrivilegedRequiredError.md)  |  Etiqueta atual foi atribuída como uma operação com privilégios (o equivalente a uma operação de administrador), portanto não pode ser substituído.
[mip::ProtectAdhocAction](class_mip_ProtectAdhocAction.md)  |  Uma classe de ação que especifica a adição de ad hoc proteção para o documento.
[mip::ProtectByTemplateAction](class_mip_ProtectByTemplateAction.md)  |  Uma classe de ação que especifica a adição de proteção pelo modelo para o documento.
[mip::ProtectDoNotForwardAction](class_mip_ProtectDoNotForwardAction.md)  |  Uma classe de ação que especifica a adicionar não reencaminhar proteção para o documento.
[mip::ProtectionDescriptor](class_mip_ProtectionDescriptor.md)  |  Descrição de proteção associada a uma parte do conteúdo.
[mip::ProtectionDescriptorBuilder](class_mip_ProtectionDescriptorBuilder.md)  |  Constrói uma [ProtectionDescriptor](class_mip_protectiondescriptor.md) que descreve a proteção associada a uma parte do conteúdo.
[mip::ProtectionEngine](class_mip_ProtectionEngine.md)  |  Gere as ações relacionadas com a proteção relacionados com uma identidade específica.
[mip::ProtectionHandler](class_mip_ProtectionHandler.md)  |  Gere as ações relacionadas com a proteção para uma configuração de proteção específico.
[mip::ProtectionProfile](class_mip_ProtectionProfile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md) é a classe de raiz para a execução de operações de proteção.
[mip::ProxyAuthenticationError](class_mip_ProxyAuthenticationError.md)  |  Falha de autenticação de proxy.
[mip::RecommendLabelAction](class_mip_RecommendLabelAction.md)  |  Recomendamos a ações de etiqueta destina-se a sugerir uma etiqueta para os utilizadores. Suprimir esta chamada depois que um utilizador ignora a etiqueta recomendada deve ser feito por meio de ações suportadas sobre o estado de execução.
[mip::RemoveContentFooterAction](class_mip_RemoveContentFooterAction.md)  |  Uma classe de ação que especifica a remover o rodapé de conteúdo do documento.
[mip::RemoveContentHeaderAction](class_mip_RemoveContentHeaderAction.md)  |  Uma classe de ação que especifica a remover o cabeçalho de conteúdo do documento.
[mip::RemoveProtectionAction](class_mip_RemoveProtectionAction.md)  |  Uma classe de ação que especifica a remoção da proteção do documento.
[mip::RemoveWatermarkAction](class_mip_RemoveWatermarkAction.md)  |  Uma classe de ação que especifica a remover as marcas de água do documento.
[mip::SensitivityTypesRulePackage](class_mip_SensitivityTypesRulePackage.md)  | _Ainda não documentado._
[mip::ServiceDisabledError](class_mip_ServiceDisabledError.md)  |  O utilizador não foi possível obter acesso ao conteúdo devido a um serviço que está a ser desabilitado.
[mip::Stream](class_mip_Stream.md)  |  Uma classe que define a interface entre o SDK de MIP e baseada em fluxo conteúdo de mensagens em fila.
[mip::TransientNetworkError](class_mip_TransientNetworkError.md)  |  Erro de sistema de rede transitório. Causado por um comportamento inesperado ao efetuar chamadas de rede para pontos finais de serviço. A operação pode ser repetida como este erro é um erro transitório.
[mip::UserRights](class_mip_UserRights.md)  |  Um grupo de utilizadores e os direitos associados aos mesmos.
[mip::UserRoles](class_mip_UserRoles.md)  |  Um grupo de utilizadores e as funções associadas a eles.