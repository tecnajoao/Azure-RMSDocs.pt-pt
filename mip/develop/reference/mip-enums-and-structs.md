# <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
**Comuns** |
 Enum consentimento       |  Representa a decisão de um utilizador para dar consentimento para ligar a um ponto de extremidade de serviço.
 struct ApplicationInfo  |  ID da aplicação conforme definido no portal do Azure AD.
**Mip** |
 Enum ErrorType       | _Ainda não documentado._
 Enum HttpRequestType       |  Tipo de pedido de HTTP.
 Enum LogLevel       |  Níveis de registo diferentes utilizados em todo o sdk de mip.
 Enum ProtectionHandlerCreationOptions       |  Sinalizadores de bits que ditam o comportamento de criação de política adicionais.
 Enum ProtectionType       |  Descreve se proteção baseia-se desativar um modelo ou ad-hoc (personalizado)
 Enum ActionType       |  Tipos de ação diferentes.
 struct mip::PublishingLicenseContext | Contém os detalhes de uma licença de publicação utilizado para criar um manipulador de proteção.


  
## <a name="enumerations-common"></a>Enumerações (comum)
  
### <a name="consent"></a>Consentimento
Representa a decisão de um utilizador para dar consentimento para ligar a um ponto de extremidade de serviço.

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
AcceptAlways            | Dar consentimento e lembre-se esta decisão
Aceitar            | Dar consentimento, apenas uma vez
Rejeitar            | Não consentimento
  
## <a name="enumerations-mip"></a>Enumerações (mip)

### <a name="actiontype"></a>ActionType
 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
ADD_CONTENT_FOOTER            | Adicione um rodapé de conteúdo para o tipo de ação do documento.
ADD_CONTENT_HEADER            | Adicione um cabeçalho de conteúdo para o tipo de ação do documento.
ADD_WATERMARK            | Adicione uma marca de água para o tipo de ação de todo o documento.
PERSONALIZADO            | Um tipo de ação personalizada de definidos.
JUSTIFICAR            | Um tipo de ação justify.
METADADOS            | Tipo de ação de alteração de dados de uma Meta.
PROTECT_ADHOC            | Um proteger por tipo de ação de política ad hoc.
PROTECT_BY_TEMPLATE            | Um proteger por tipo de ação de modelo.
PROTECT_DO_NOT_FORWARD            | Um proteger por não reencaminhar o tipo de ação.
REMOVE_CONTENT_FOOTER            | Remova o tipo de ação de rodapé de conteúdo.
REMOVE_CONTENT_HEADER            | Remova tipo de conteúdo do cabeçalho de ação.
REMOVE_PROTECTION            | Remova o tipo de ação de proteção.
REMOVE_WATERMARK            | Remova tipo de ação de marca d'água.
APPLY_LABEL            | Aplicam-se o tipo de ação da etiqueta.
RECOMMEND_LABEL            | Recomendamos o tipo de ação da etiqueta.

Tipos de ação diferentes.

PERSONALIZADO é o tipo de ação genérica. Todos os outros tipos de ação é uma ação específica com um significado específico.

É possível combinar valores ActionType utilizando os seguintes operadores

- Ou o operador (|) para [ação](class_mip_action.md).
- E (&) operador para [ação](class_mip_action.md).
- Lógica ou (Xor) (^) operador para [ação](class_mip_action.md).


### <a name="errortype"></a>ErrorType
 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | Autor da chamada transmitida uma entrada incorreta.
FILE_IO_ERROR            | Erro de e/s de arquivo de geral.
NETWORK_ERROR            | Problemas gerais de rede; Por exemplo, serviço inacessível.
TRANSIENT_NETWORK_ERROR            | Problemas de rede transitórios; Por exemplo, gateway inválido.
INTERNAL_ERROR            | Erros inesperados internos. Por exemplo, no protocolo de cliente-servidor (resposta inesperada recebida).
JUSTIFICATION_REQUIRED            | Deve fornecer a justificação para concluir a ação no ficheiro.
NOT_SUPPORTED_OPERATION            | A operação pedida ainda não é suportada.
PRIVILEGED_REQUIRED            | Não é possível substituir a etiqueta com privilégios quando o novo método de etiqueta é padrão.
ACCESS_DENIED            | O utilizador não foi possível obter acesso ao conteúdo. Por exemplo, não existem permissões, conteúdos revogaram etc.
CONSENT_DENIED            | Uma operação que é necessário o consentimento do utilizador não foi concedida ao consentimento.
  
### <a name="httprequesttype"></a>HttpRequestType
 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
Obter            | GET
Post            | POST
Tipo de pedido de HTTP.
  
### <a name="loglevel"></a>LogLevel
 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
Rastreio            | 
Informações            | 
Aviso            | 
Error            | 
Níveis de registo diferentes utilizados em todo o sdk de mip.
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions
 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
Nenhum            | Nenhum
OfflineOnly            | Não permita operações de rede e da interface do Usuário.
AllowAuditedExtraction            | Conteúdo pode ser aberto num aplicativo sem proteção-sdk-suporte para
PreferDeprecatedAlgorithms            | Utilização despromovida algoritmos criptográficos (ECB) para efeitos compatibilidade
Sinalizadores de bits que ditam o comportamento de criação de política adicionais.
  
### <a name="protectiontype"></a>ProtectionType
 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
TemplateBased            | Identificador foi criado a partir de um modelo
Personalizar            | Identificador foi criado ad hoc
Descreve se proteção baseia-se desativar um modelo ou ad-hoc (personalizado)
  
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions
Operador de OR bit a bit ProtectionHandlerCreationOptions.

Parâmetros:  
* **um**: deixado valor 

* **b**: com o botão direito valor

### <a name="releaseallresources"></a>ReleaseAllResources
Todos os recursos (threads, etc.) antes do Desligamento de versão.
Se as bibliotecas de dinâmicas de MIP estão carregados com atraso por uma aplicação, esta função tem de ser chamada antes do aplicativo explicitamente descarregamento dessas bibliotecas MIP para evitar o deadlock. Por exemplo, no win32, esta função tem de ser chamada antes de todas as chamadas para o descarregamento de explicitamente MIP DLLs via FreeLibrary ou \__FUnloadDelayLoadedDLL2. Aplicativos deverá liberar referências a todos os objetos de MIP (por exemplo, perfis, motores, manipuladores) antes de chamar essa função.
  
**Devolve**: totalmente ou de parâmetros
  
### <a name="mipstream"></a>Mip::Stream
Cria um [Stream](class_mip_stream.md) de um fluxo ou memória intermédia.

Parâmetros:  
* **stdStream**: std::istream, de segurança 

**Devolve**: [Stream](class_mip_stream.md) um std::istream de encapsulamento de aplicações
  
### <a name="mipstream"></a>Mip::Stream
Cria um [Stream](class_mip_stream.md) de um std::ostream.

Parâmetros:  
* **stdOStream**: std::ostream de segurança

**Devolve**: [Stream](class_mip_stream.md) um std::ostream de encapsulamento de aplicações
  
### <a name="mipstream"></a>Mip::Stream
Cria um [Stream](class_mip_stream.md) de um std::iostream.

Parâmetros:  
* **stdIOStream**: std::iostream de segurança

**Devolve**: [Stream](class_mip_stream.md) um std::iostream de encapsulamento de aplicações
  
### <a name="mipstream"></a>Mip::Stream
Cria um [Stream](class_mip_stream.md) de uma memória intermédia.

Parâmetros:  
* **memória intermédia**: aponta para um buffer

**Devolve**: tamanho de tamanho do buffer
  
## <a name="structures"></a>Estruturas

### <a name="applicationinfo"></a>ApplicationInfo 
Identificador da aplicação conforme definido no portal do Azure AD.
  
 Campos                        | Descrições                                
--------------------------------|---------------------------------------------
 applicationId Std:: String pública  | ID da aplicação no portal do Azure AD.
 friendlyName Std:: String pública  | Nome amigável da aplicação, conforme especificado no portal.
  
### <a name="mippublishinglicensecontext"></a>Mip::PublishingLicenseContext 
Contém os detalhes de uma licença de publicação utilizado para criar um manipulador de proteção.
  
 Campos                        | Descrições                                
--------------------------------|---------------------------------------------
público licenseInfo const de Std:: vector < uint8_t >  | _Ainda não documentado._
público serializedPublishingLicense const de Std:: vector < uint8_t >  | _Ainda não documentado._
PublishingLicenseContext pública (const Std:: vector < uint8_t > licenseInfo, const Std:: vector < uint8_t > & serializedPublishingLicense)  | _Ainda não documentado._
  
