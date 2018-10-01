---
title: SDK de MIP para referência C++ (pré-visualização)
description: SDK de MIP para referência C++ (pré-visualização)
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 06d8bb26a8e3026562006d68d4ae8d1630eba81c
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446333"
---
# <a name="mip-sdk-for-c-preview-reference"></a>SDK de MIP para referência C++ (pré-visualização)

A Microsoft Information Protection (MIP) do SDK para C++ (pré-visualização) permite aos desenvolvedores de gerenciar e aplicar políticas de proteção de dados para dados e outros ativos digitais.  

Para obter mais informações, consulte [blogue para programadores de MIP](https://aka.ms/MIPDevelopers)<!-- and [MIP samples](https://aka.ms/mipsdksamples)-->.

O SDK de MIP para C++ inclui:

- [Enumerações e estruturas](mip-enums-and-structs.md)
- [Funções](mip-functions.md)
- As seguintes classes:

| Nome da classe | Descrição |
| :----------|:------------|
[AccessDeniedError](class_mip_accessdeniederror.md)  |  O utilizador não foi possível obter acesso ao conteúdo. Por exemplo, não existem permissões, conteúdos revogaram.
[Action](class_mip_action.md)  |  Interface para uma ação. Cada ação se traduz numa etapa que é necessário realizar pela aplicação para aplicar a etiqueta (conforme definido na política)
[AddContentFooterAction](class_mip_addcontentfooteraction.md)  |  Uma classe de ação que especifica a adicionar um rodapé de conteúdo ao documento.
[AddContentHeaderAction](class_mip_addcontentheaderaction.md)  |  Uma classe de ação que especifica o cabeçalho de conteúdo a adicionar.
[AddWatermarkAction](class_mip_addwatermarkaction.md)  |  Uma classe de ação que especifica o limite de tamanho de adição.
[ApplyLabelAction](class_mip_applylabelaction.md)  |  Aplicar ações de etiqueta requer que o aplicativo de chamada para aplicar uma etiqueta específica.
[BadInputError](class_mip_badinputerror.md)  |  Erro entrado ruim, lançado quando a entrada a uma API do SDK é inválida.
[ClassificationResult](class_mip_classificationresult.md)  |  Classe que contém o resultado de uma chamada de classificação no estado de execução.
[ConsentDelegate](class_consentdelegate.md)  |  Delegado, consentimento operações relacionadas com.
[ConsentDeniedError](class_mip_consentdeniederror.md)  |  Uma operação que é necessário o consentimento do utilizador não foi concedida ao consentimento.
[ContentLabel](class_mip_contentlabel.md)  |  Abstração para uma etiqueta do Microsoft Information Protection que é aplicada a uma parte do conteúdo, normalmente, um documento.
[CustomAction](class_mip_customaction.md)  |  [CustomAction](class_mip_customaction.md) é uma classe de ação genérica que captura todas as propriedades secundárias da ação como uma matriz de propriedades. O chamador é da responsabilidade compreender o significado da ação.
[Error](class_mip_error.md)  |  Classe para todos os erros que serão reportadas (emitida ou devolveu) base do MIP SDK.
[ExecutionState](class_mip_executionstate.md)  |  Interface para todos os Estados necessários para executar o motor.
[FileEngine::Settings](class_mip_fileengine_settings.md)  | _Ainda não documentado._
[FileEngine](class_mip_fileengine.md)  |  Essa classe fornece uma interface para todas as funções de motor.
[FileHandler::Observer](class_mip_filehandler_observer.md)  |  [Observador](class_mip_filehandler_observer.md) interface para que os clientes obter notificações de eventos relacionados com o manipulador de arquivo.
[FileHandler](class_mip_filehandler.md)  |  Interface para o ficheiro de todas as funções de manipulação.
[FileIOError](class_mip_fileioerror.md)  |  Erro de e/s de ficheiros.
[FileProfile::Observer](class_mip_fileprofile_observer.md)  |  [Observador](class_mip_fileprofile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
[FileProfile::Settings](class_mip_fileprofile_settings.md)  |  [As definições](class_mip_fileprofile_settings.md) utilizada pelo [FileProfile](class_mip_fileprofile.md) durante sua criação e ao longo de seu ciclo de vida.
[FileProfile](class_mip_fileprofile.md)  |  [FileProfile](class_mip_fileprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar.
[HttpDelegate](class_mip_httpdelegate.md)  |  Interface para substituir o tratamento de HTTP.
[httpRequest](class_mip_httprequest.md)  |  Interface que descreve um único pedido HTTP.
[HttpResponse](class_mip_httpresponse.md)  |  Interface que descreve uma única resposta HTTP, implementada pela aplicação de cliente, ao substituir [HttpDelegate](class_mip_httpdelegate.md).
[InternalError](class_mip_internalerror.md)  |  Erro interno. Este erro é apresentado quando algo inesperado acontece durante a execução.
[JustificationRequiredError](class_mip_justificationrequirederror.md)  | _Ainda não documentado._
[JustifyAction](class_mip_justifyaction.md)  |  Justificar [ação](class_mip_action.md) necessita de fornecer uma justificação para baixar uma etiqueta e definir a resposta no estado de execução.
[Label](class_mip_label.md)  |  Abstração para um único rótulo do Microsoft Information Protection.
[LabelingOptions](class_mip_labelingoptions.md)  |  Interface para configurar opções de etiquetas para os métodos de SetLabel/DeleteLabel.
[LoggerDelegate](class_mip_loggerdelegate.md)  |  Uma classe que define a interface para o agente de log MIP SDK.
[MetadataAction](class_mip_metadataaction.md)  |  Uma [ação](class_mip_action.md) que adiciona informações de metadados para o conteúdo.
[NetworkError](class_mip_networkerror.md)  |  Erro de sistema de rede. Causado por um comportamento inesperado ao efetuar chamadas de rede para pontos finais de serviço.
[NotSupportedError](class_mip_notsupportederror.md)  |  A operação pedida pelo aplicativo não é suportada pelo SDK.
[PolicyEngine::Settings](class_mip_policyengine_settings.md)  |  Especifica as definições associadas com uma [PolicyEngine](class_mip_policyengine.md).
[PolicyEngine](class_mip_policyengine.md)  |  Essa classe fornece uma interface para todas as funções de motor.
[PolicyHandler](class_mip_policyhandler.md)  |  Essa classe fornece uma interface para todas as funções do manipulador de política num arquivo.
[PolicyProfile::Observer](class_mip_policyprofile_observer.md)  |  [Observador](class_mip_policyprofile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
[PolicyProfile::Settings](class_mip_policyprofile_settings.md)  |  [As definições](class_mip_policyprofile_settings.md) utilizada pelo [PolicyProfile](class_mip_policyprofile.md) durante sua criação e ao longo de seu ciclo de vida.
[PolicyProfile](class_mip_policyprofile.md)  |  [PolicyProfile](class_mip_policyprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar. Um aplicativo típico irá apenas precisa de um [PolicyProfile](class_mip_policyprofile.md) , mas ele pode criar vários perfis, se for necessário.
[PolicySyncError](class_mip_policysyncerror.md)  |  Falha ao tentar sincronizar dados de política.
[PrivilegedRequiredError](class_mip_privilegedrequirederror.md)  |  Etiqueta atual foi atribuída como uma operação com privilégios (o equivalente a uma operação de administrador), portanto não pode ser substituído.
[ProtectAdhocAction](class_mip_protectadhocaction.md)  |  Uma classe de ação que especifica a adição de ad hoc proteção para o documento.
[ProtectByTemplateAction](class_mip_protectbytemplateaction.md)  |  Uma classe de ação que especifica a adição de proteção pelo modelo para o documento.
[ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md)  |  Uma classe de ação que especifica a adicionar não reencaminhar proteção para o documento.
[ProtectionDescriptor](class_mip_protectiondescriptor.md)  |  Descrição de proteção associada a uma parte do conteúdo.
[ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)  |  Constrói uma [ProtectionDescriptor](class_mip_protectiondescriptor.md) que descreve a proteção associada a uma parte do conteúdo.
[ProtectionEngine::Observer](class_mip_protectionengine_observer.md)  |  Interface que recebe notificações relacionadas com a [ProtectionEngine](class_mip_protectionengine.md).
[ProtectionEngine::Settings](class_mip_protectionengine_settings.md)  |  [As definições](class_mip_protectionengine_settings.md) utilizada pelo [ProtectionEngine](class_mip_protectionengine.md) durante sua criação e ao longo de seu ciclo de vida.
[ProtectionEngine](class_mip_protectionengine.md)  |  Gere as ações relacionadas com a proteção relacionados com uma identidade específica.
[ProtectionHandler::Observer](class_mip_protectionhandler.md)  |  Interface que recebe notificações relacionadas com a [ProtectionHandler](class_mip_protectionhandler.md).
[ProtectionHandler](class_mip_protectionhandler.md)  |  Gere as ações relacionadas com a proteção para uma configuração de proteção específico.
[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)  |  Interface que recebe notificações relacionadas com a [ProtectionProfile](class_mip_protectionprofile.md).
[ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)  |  [As definições](class_mip_protectionprofile_settings.md) utilizada pelo [ProtectionProfile](class_mip_protectionprofile.md) durante sua criação e ao longo de seu ciclo de vida.
[ProtectionProfile](class_mip_protectionprofile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md) é a classe de raiz para a execução de operações de proteção.
[RecommendLabelAction](class_mip_recommendlabelaction.md)  |  Recomendamos a ações de etiqueta destina-se a sugerir uma etiqueta para os utilizadores. Suprimir esta chamada depois que um utilizador ignora a etiqueta recomendada deve ser feito por meio de ações suportadas sobre o estado de execução.
[RemoveContentFooterAction](class_mip_removecontentfooteraction.md)  |  Uma classe de ação que especifica a remover o rodapé de conteúdo do documento.
[RemoveContentHeaderAction](class_mip_removecontentheaderaction.md)  |  Uma classe de ação que especifica a remover o cabeçalho de conteúdo do documento.
[RemoveProtectionAction](class_mip_removeprotectionaction.md)  |  Uma classe de ação que especifica a remoção da proteção do documento.
[RemoveWatermarkAction](class_mip_removewatermarkaction.md)  |  Uma classe de ação que especifica a remover as marcas de água do documento.
[Stream](class_mip_stream.md)  |  Uma classe que define a interface entre o SDK de MIP e baseada em fluxo conteúdo de mensagens em fila.
[TransientNetworkError](class_mip_transientnetworkerror.md)  |  Erro de sistema de rede transitório. Causado por um comportamento inesperado ao efetuar chamadas de rede para pontos finais de serviço. A operação pode ser repetida como este erro é um erro transitório.
[UserRights](class_mip_userrights.md)  |  Um grupo de utilizadores e os direitos associados aos mesmos.
[UserRoles](class_mip_userroles.md)  |  Um grupo de utilizadores e as funções associadas a eles.
