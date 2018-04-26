# <a name="mip-sdk-for-c-preview-reference"></a>SDK MIP para referência do C++ (pré-visualização)

A Microsoft informações proteção (MIP) do SDK para C++ (pré-visualização) permite aos programadores gerir e aplicar políticas de proteção de dados para dados e outros recursos digitais.  

Para obter mais informações, consulte [blogue para programadores de MIP](https://aka.ms/MIPDevelopers) e [amostras MIP](https://aka.ms/mipsdksamples).

O SDK de MIP para C++ inclui as seguintes classes:

| Nome da classe | Descrição |
| :----------|:------------|
[Mip::Action](class_mip_action.md) | Classe base para todas as ações. |
[Mip::AddContentFooterAction](class_mip_addcontentfooteraction.md) | Uma classe de ação que especifica a adição de um rodapé de conteúdo para o documento.
[Mip::addContentHeaderAction](class_mip_addcontentheaderaction.md) | Uma classe de ação que especifica o cabeçalho de conteúdo de adição.
[Mip::AddWatermarkAction](class_mip_addwatermarkaction.md) | Uma classe de ação que especifica a adição de marca de água.
[Mip::BadInputError](class_mip_badinputerror.md) | Danificados erro de entrada, de entrada para a API era inválida.
[Mip::CommonRights](class_mip_commonrights.md) | Direitos universalmente suportados.
[Mip::consent](class_mip_consent.md) | Representa aceitação/refusal um utilizador para permitir uma ação.
[Mip::ConsentCallback](class_mip_consentcallback.md) | Interface de notificações de pedido de consentimento.
[Mip::ConsentResult](class_mip_consentresult.md) | Descreve o resultado do pedido de consentimento após a interação do utilizador.
[Mip::ContentLabel](class_mip_contentlabel.md) | Abstração para uma etiqueta de Microsoft Information Protection, que é aplicada a um conjunto de conteúdo, normalmente, um documento.
[Mip::CustomAction](class_mip_customaction.md) | Classe de ação genérica que captura todas as propriedades secundárias da ação como uma matriz de propriedades.
[Mip::CustomProtectedStream](class_mip_customprotectedstream.md) | Encapsula num wrapper uma transmissão em fluxo para fornecer a encriptação transparente e desencriptação na leitura e escrita.
[Mip::EditableDocumentRights](class_mip_editabledocumentrights.md) | Direitos que se aplicam para documentos editáveis.
[Mip::EmailRights](class_mip_emailrights.md) | Direitos que se aplicam ao e-mail.
[Mip::Error](class_mip_error.md) | Classe de todos os erros que serão comunicadas (emitida ou devolvido) base do MIP SDK.
[Mip::ExecutionState](class_mip_executionstate.md) | Interface para todos os Estado necessário para o motor de execução.
[Mip::EileEngine](class_mip_fileengine.md) | Interface para todas as funções de motor.
[Mip::FileEngine::Settings](class_mip_fileengine_settings.md) | 
[Mip::FileHandler](class_mip_filehandler.md) | Interface para o ficheiro de todas as funções de processamento.
[Mip::FileHandler::Observer](class_mip_filehandler_observer.md) | Interface de observador para clientes a receber notificações de processador de ficheiros de eventos relacionados.
[Mip::FileIOError](class_mip_fileioerror.md) | Erro de e/s de ficheiro.
[Mip::FileProfile](class_mip_fileprofile.md) | Classe de raiz para operações de proteção de informações da Microsoft.
[Mip::FileProfile::Observer](class_mip_fileprofile_observer.md) | Interface de observador utilizado para receber notificações de eventos relacionados com o perfil.
[Mip::FileProfile::Settings](class_mip_fileprofile_settings.md) | Interface para gerir as definições de perfil do ficheiro.
[Mip::GetUserPolicyResult](class_mip_getuserpolicyresult.md) | Descreve os resultados de um pedido de aquisição de política de utilizador.
[Mip::InternalError](class_mip_internalerror.md) | Erro interno do SDK. Ocorreu algo de inesperado um.
[Mip::IStream](class_mip_istream.md) | Interface de base para fluxos protegidos.
[Mip::JustificationRequiredError](class_mip_justificationrequirederror.md) | Alteração pedida requer uma explicação para que a alteração.
[Mip::JustifyAction](class_mip_justifyaction.md) | Pedido requer a justificação para uma mudança de para versão anterior de etiqueta e definir a resposta em estado de execução.
[Mip::Label](class_mip_label.md) | Abstração para uma etiqueta única da Microsoft Information Protection.
[Mip::LabelingOptions](class_mip_labelingoptions.md) | Interface para configurar as opções de etiquetas para o método SetLabel.
[Mip::MetadataAction](class_mip_metadataaction.md) | Uma ação especificar as informações de metadados adicionados ao conteúdo.
[Mip::NetworkError](class_mip_networkerror.md) | Erro de rede.
[Mip::NotSupportedError](class_mip_notsupportederror.md) | Erro de operação não é suportada.
[Mip::PolicyDescriptor](class_mip_policydescriptor.md) | Representa uma política ad-hoc associada ao conteúdo protegido.
[Mip::PolicyEngine](class_mip_policyengine.md) | Esta classe fornece uma interface para todas as funções de motor.
[Mip::PolicyEngine::Settings](class_mip_policyengine_settings.md) | Forneça uma instância desta classe com approprieted parâmetros devem ser para iniciar um motor.
[Mip::PrivilegedRequiredError](class_mip_privilegedrequirederror.md) | Etiqueta atual foi definida por privilidge não pode substituir o método de atribuição.
[Mip::Profile](class_mip_profile.md) | Classe de raiz para operações de proteção de informações da Microsoft.
[Mip::profile::Observer](class_mip_profile_observer.md) | Interface utilizada para receber notificações para perfil relacionadas com as notificações de eventos.
[Mip::profile::Settings](class_mip_profile_settings.md) | Configura as definições de perfil.
[Mip::ProtectAdhocAction](class_mip_protectadhocaction.md) | Uma classe de ação que especifica a proteção de ad-hoc ao adicionar o documento.  
[Mip::ProtectbyTemplateAction](class_mip_protectbytemplateaction.md) | Uma classe de ação que especifica a adição de proteção através do modelo para o documento.
[Mip::ProtectDoNotForwardAction](class_mip_protectdonotforwardaction.md) | Uma classe de ação que especifica a adicionar não reencaminhar proteção para o documento.
[Mip::ProtectionProfile](class_mip_protectionprofile.md) | Classe base utilizado para executar operações de proteção.
[Mip::ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) | Utilize para receber notificações de perfil de proteção.
[Mip::ProtectionProfile::Settings](class_mip_protectionprofile_settings.md) | Definições de perfil de proteção utilizadas ao longo da duração da instância.
[Mip::RemoveContentFooterAction](class_mip_removecontentfooteraction.md) | Uma classe de ação que especifica a remoção do rodapé de conteúdo do documento.
[Mip::RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) | Uma classe de ação que especifica a remover o cabeçalho de conteúdo do documento.
[Mip::RemoveProtectionAction](class_mip_removeprotectionaction.md) | Uma classe de ação que especifica remover proteção do documento.
[Mip::RemoveWatermarkAction](class_mip_removewatermarkaction.md) | Uma classe de ação que especifica a remover o de marcas de água do documento.
[Mip::RMSCryptographyException](class_mip_rmscryptographyexception.md) | Exceção de criptografia do RMS.
[Mip::RMSException](class_mip_rmsexception.md) | Exceção de base do RMS.
[Mip::RMSInvalidArgumentException](class_mip_rmsinvalidargumentexception.md) | Exceção de argumento inválido do RMS.
[Mip::RMSLogicException](class_mip_rmslogicexception.md) | Exceção de lógica de RMS.
[Mip::RMSNetworkException](class_mip_rmsnetworkexception.md) | Exceção de rede do RMS.
[Mip::RMSNotFoundException](class_mip_rmsnotfoundexception.md) | Não foi encontrada a exceção de RMS.
[Mip::RMSNullPointerException](class_mip_rmsnullpointerexception.md) | Exceção de apontador nulo do RMS.
[Mip::RMSOfficeFileException](class_mip_rmsofficefileexception.md) | Exceção de ficheiro do Office para RMS.
[Mip::RMSPFileException](class_mip_rmspfileexception.md) | Exceção de RMS PFile.
[Mip::RMSRightsException](class_mip_rmsrightsexception.md) | Exceção de direitos do RMS.
[Mip::RMSStreamException](class_mip_rmsstreamexception.md) | Exceção de fluxo do RMS.
[Mip::roles](class_mip_roles.md) | Define as funções para proteger dados.
[Mip::Stream](class_mip_stream.md) | Uma classe que define a interface entre o sdk de mip e fluxo com base no conteúdo.
[Mip::TemplateDescriptor](class_mip_templatedescriptor.md) | Descreve um modelo de RMS.
[Mip::UserPolicy](class_mip_userpolicy.md) | Representa a política associada ao conteúdo protegido.
[Mip::UserRights](class_mip_userrights.md) | Representa um grupo de utilizadores e os direitos associados aos mesmos.
[Mip::UserRoles](class_mip_userroles.md) | Representa um grupo de utilizadores e as funções associadas.
 
