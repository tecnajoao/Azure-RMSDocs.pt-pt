# <a name="mip-sdk-for-c-preview-reference"></a>SDK de MIP para referência C++ (pré-visualização)

A Microsoft Information Protection (MIP) do SDK para C++ (pré-visualização) permite aos desenvolvedores de gerenciar e aplicar políticas de proteção de dados para dados e outros ativos digitais.  

Para obter mais informações, consulte [blogue para programadores de MIP](https://aka.ms/MIPDevelopers) e [exemplos de MIP](https://aka.ms/mipsdksamples).

O SDK de MIP para C++ inclui:

- [Enumerações e estruturas](mip-enums-and-structs.md)
- [Funções](mip-functions.md)
- As seguintes classes:

| Nome da classe | Descrição |
| :----------|:------------|
[ConsentDelegate](class_consentdelegate.md)  |  Delegado, consentimento operações relacionadas com.
[Mip::AccessDeniedError](class_mip_accessdeniederror.md)  |  O utilizador não foi possível obter acesso ao conteúdo. Por exemplo, não existem permissões, conteúdos revogaram etc.
[Mip::Action](class_mip_action.md)  |  Interface para uma ação. Cada ação se traduz numa etapa que é necessário realizar pela aplicação para aplicar a etiqueta (conforme definido na política)
[Mip::AddContentFooterAction](class_mip_addcontentfooteraction.md)  |  Uma classe de ação que especifica a adicionar um rodapé de conteúdo ao documento.
[Mip::AddContentHeaderAction](class_mip_addcontentheaderaction.md)  |  Uma classe de ação que especifica o cabeçalho de conteúdo a adicionar.
[Mip::AddWatermarkAction](class_mip_addwatermarkaction.md)  |  Uma classe de ação que especifica o limite de tamanho de adição.
[Mip::ApplyLabelAction](class_mip_applylabelaction.md)  |  Aplicar ações de etiqueta requer que o aplicativo de chamada para aplicar uma etiqueta específica.
[Mip::BadInputError](class_mip_badinputerror.md)  |  Erro entrado ruim, lançado quando a entrada para um sdk api é inválido.
[Mip::ClassificationResult](class_mip_classificationresult.md)  |  Classe que contém o resultado de uma chamada de classificação no estado de execução.
[Mip::ContentLabel](class_mip_contentlabel.md)  |  Abstração para uma etiqueta do Microsoft Information Protection que é aplicada a uma parte do conteúdo, normalmente, um documento.
[Mip::CustomAction](class_mip_customaction.md)  |  [CustomAction](class_mip_customaction.md) é uma classe de ação genérica que captura todas as propriedades secundárias da ação como uma matriz de propriedades. O chamador é da responsabilidade compreender o significado da ação.
[Mip::Error](class_mip_error.md)  |  Classe para todos os erros que serão reportadas (emitida ou devolveu) base do MIP SDK.
[Mip::ExecutionState](class_mip_executionstate.md)  |  Interface para todos os Estados necessários para executar o motor.
[Mip::FileEngine](class_mip_fileengine.md)  |  Interface para todas as funções de motor.
[Mip::FileEngine::Settings](class_mip_fileengine::settings.md)  | _Ainda não documentado._
[Mip::FileHandler](class_mip_filehandler.md)  |  Interface para o ficheiro de todas as funções de manipulação.
[Mip::FileHandler::Observer](class_mip_filehandler::observer.md)  |  [Observador](class_mip_filehandler_observer.md) interface para os clientes obter notificações para ficheiros relacionados com o manipulador de eventos.
[Mip::FileIOError](class_mip_fileioerror.md)  |  Erro de e/s de ficheiros.
[Mip::FileProfile](class_mip_fileprofile.md)  |  [FileProfile](class_mip_fileprofile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar.
[Mip::FileProfile::Observer](class_mip_fileprofile_observer.md)  |  [Observador](class_mip_fileprofile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
[Mip::FileProfile::Settings](class_mip_fileprofile_settings.md)  |  [As definições](class_mip_fileprofile_settings.md) utilizada pelo [FileProfile](class_mip_fileprofile.md) durante sua criação e ao longo de seu ciclo de vida.
[Mip::InternalError](class_mip_internalerror.md)  |  Erro interno. Este erro é apresentado quando algo inesperado acontece durante a execução.
[Mip::JustificationRequiredError](class_mip_justificationrequirederror.md)  | _Ainda não documentado._
[Mip::JustifyAction](class_mip_justifyaction.md)  |  Justificar [ação](class_mip_action.md) necessita de fornecer uma justificação para baixar uma etiqueta e definir a resposta no estado de execução.
[Mip::Label](class_mip_label.md)  |  Abstração para um único rótulo do Microsoft Information Protection.
[Mip::LabelingOptions](class_mip_labelingoptions.md)  |  Interface para configurar opções de etiquetas para o método SetLabel.
[Mip::LoggerDelegate](class_mip_loggerdelegate.md)  |  Uma classe que define a interface para o agente de log MIP SDK.
[Mip::MetadataAction](class_mip_metadataaction.md)  |  Uma [ação](class_mip_action.md) que adiciona informações de metadados para o conteúdo.
[Mip::NetworkError](class_mip_networkerror.md)  |  Erro de sistema de rede. Causado por um comportamento inesperado ao efetuar chamadas de rede para pontos finais de serviço.
[Mip::NotSupportedError](class_mip_notsupportederror.md)  |  A operação pedida pelo aplicativo não é suportada pelo sdk.
[Mip::PolicyEngine](class_mip_policyengine.md)  |  Essa classe fornece uma interface para todas as funções de motor.
[Mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)  |  Deve ser fornecer uma instância dessa classe com os parâmetros adequados para iniciar um motor.
[Mip::PrivilegedRequiredError](class_mip_privilegedrequirederror.md)  |  Etiqueta atual foi atribuída como uma operação com privilégios (o equivalente a uma operação de administrador), portanto não pode ser substituído.
[Mip::Profile](class_mip_profile.md)  |  [Perfil](class_mip_profile.md) classe é a classe de raiz para as operações do Microsoft Information Protection a utilizar. Um aplicativo típico irá apenas precisa de um [perfil](class_mip_profile.md) , mas ele pode criar vários perfis, se for necessário.
[Mip::profile::Observer](class_mip_profile_observer.md)  |  [Observador](class_mip_profile_observer.md) interface para os clientes a obter notificações do perfil eventos relacionados.
[Mip::profile::Settings](class_mip_profile_settings.md)  |  [As definições](class_mip_profile_settings.md) utilizada pelo [perfil](class_mip_profile.md) durante sua criação e ao longo de seu ciclo de vida.
[Mip::ProtectAdhocAction](class_mip_protectadhocaction.md)  |  Uma classe de ação que especifica a adição de ad hoc proteção para o documento.
[Mip::ProtectByTemplateAction](class_mip_protectbytemplateaction.md)  |  Uma classe de ação que especifica a adição de proteção através do modelo para o documento.
[Mip::ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md)  |  Uma classe de ação que especifica a adicionar não reencaminhar proteção para o documento.
[Mip::ProtectionDescriptor](class_mip_protectiondescriptor.md)  |  Representa uma política ad-hoc associada com conteúdo protegido.
[Mip::ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)  |  Representa uma política ad-hoc associada com conteúdo protegido.
[Mip::ProtectionEngine](class_mip_protectionengine.md)  |  Executa ações relacionadas com a proteção relacionados com uma identidade específica.
[Mip::ProtectionEngine::Observer](class_mip_protectionengine_observer.md)  |  Interface que recebe notificações relacionadas com a [ProtectionEngine](class_mip_protectionengine.md).
[Mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md)  |  [As definições](class_mip_protectionengine_settings.md) utilizada pelo [ProtectionEngine](class_mip_protectionengine.md) durante sua criação e ao longo de seu ciclo de vida.
[Mip::ProtectionHandler](class_mip_protectionhandler.md)  |  Executa ações relacionadas com a proteção para uma configuração de proteção específico (ou seja, os usuários, direitos, funções, etc.)
[Mip::ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)  |  Interface que recebe notificações relacionadas com a [ProtectionHandler](class_mip_protectionhandler.md).
[Mip::ProtectionProfile](class_mip_protectionprofile.md)  |  [ProtectionProfile](class_mip_protectionprofile.md) é a classe de raiz para a execução de operações de proteção.
[Mip::ProtectionProfile::Observer](class_mip_protectionprofile_observer.md)  |  Interface que recebe notificações relacionadas com a [ProtectionProfile](class_mip_protectionprofile.md).
[Mip::ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)  |  [As definições](class_mip_protectionprofile_settings.md) utilizada pelo [ProtectionProfile](class_mip_protectionprofile.md) durante sua criação e ao longo de seu ciclo de vida.
[Mip::RecommendLabelAction](class_mip_recommendlabelaction.md)  |  Recomendamos a ações de etiqueta destina-se a sugerir uma etiqueta para os utilizadores. Suprimir esta chamada depois que um utilizador ignora a etiqueta recomendada deve ser feito por meio de ações suportadas sobre o estado de execução.
[Mip::RemoveContentFooterAction](class_mip_removecontentfooteraction.md)  |  Uma classe de ação que especifica a remover o rodapé de conteúdo do documento.
[Mip::RemoveContentHeaderAction](class_mip_removecontentheaderaction.md)  |  Uma classe de ação que especifica a remover o cabeçalho de conteúdo do documento.
[Mip::RemoveProtectionAction](class_mip_removeprotectionaction.md)  |  Uma classe de ação que especifica a remover proteção do documento.
[Mip::RemoveWatermarkAction](class_mip_removewatermarkaction.md)  |  Uma classe de ação que especifica a remover as marcas de água do documento.
[Mip::Stream](class_mip_stream.md)  |  Uma classe que define a interface entre o mip sdk e o fluxo com base em conteúdo.
[Mip::UserRights](class_mip_userrights.md)  |  Representa um grupo de utilizadores e os direitos associados aos mesmos.
[Mip::UserRoles](class_mip_userroles.md)  |  Representa um grupo de utilizadores e as funções associadas a eles.

 
