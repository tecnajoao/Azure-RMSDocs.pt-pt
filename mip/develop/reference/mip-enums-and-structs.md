---
title: SDK de MIP para estruturas de referência do C++ e enumerações
description: Documentação de referência para as estruturas de MIP C++ SDK e enums.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: c9e634d436d02b147fc10a734c8c3d5b1fcdec71
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573960"
---
# <a name="enumerations-and-structures"></a>Enumerações e estruturas

## <a name="namespace-mip"></a>Espaço de nomes mip

 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
Enum ActionSource       |  Define o que acionou o evento de SetLabel
Enum ActionType       |  Tipos de ação diferentes.
Enum AssignmentMethod       |  O método de atribuição da etiqueta do documento. Se a atribuição da etiqueta foi feita automaticamente, padrão ou como uma operação com privilégios (o equivalente a uma operação de administrador).
Enum consentimento       |  Resposta de um utilizador quando consentimento é solicitado para ligar a um ponto de extremidade de serviço.
Enum ContentFormat       |  Formato de conteúdo.
enum ContentMarkAlignment       |  Marca de alinhamento para o conteúdo (conteúdo cabeçalho ou rodapé de conteúdo).
Enum DataState       |  Define o estado dos dados está a aplicação a funcionar após.
Enum ErrorType       | _Ainda não documentado._
Enum HttpRequestType       |  Tipo de pedido HTTP.
enum LogLevel       |  Níveis de registo diferentes utilizados em todo o SDK de MIP.
Enum ProtectionHandlerCreationOptions       |  Sinalizadores de bits que ditam o comportamento de criação de política adicionais.
Enum ProtectionType       |  Descreve se proteção baseia-se desativar um modelo ou ad-hoc (personalizado)
Enum WatermarkLayout       |  Esquema das marcas d'água.
struct ApplicationInfo  |  Uma estrutura que inclui informações específicas do aplicativo.
struct PublishingLicenseContext  |  Contém os detalhes de uma licença de publicação utilizado para criar um manipulador de proteção.
  
## <a name="enumerations-mip"></a>Enumerações (mip)

### <a name="actionsource"></a>ActionSource

Define o que acionou o evento de SetLabel.

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
MANUAL            | Selecionada manualmente pelo utilizador
AUTOMÁTICA            | Definir condições de política
RECOMENDADO            | Definido pelo utilizador após a etiqueta foi recomendada por condições de política
PADRÃO            | Definido por predefinição na política
OBRIGATÓRIO            | Definido pelo utilizador após a política imposta para definir uma etiqueta



### <a name="actiontype"></a>ActionType

Tipos de ação diferentes. PERSONALIZADO é o tipo de ação genérica. Todos os outros tipos de ação é uma ação específica com um significado específico.

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
ADD_CONTENT_FOOTER            | Adicione um rodapé de conteúdo para o tipo de ação do documento.
ADD_CONTENT_HEADER            | Adicione um cabeçalho de conteúdo para o tipo de ação do documento.
ADD_WATERMARK            | Adicione uma marca de água para o tipo de ação de todo o documento.
PERSONALIZADO            | Um tipo de ação personalizada de definidos.
JUSTIFICAR            | Um tipo de ação justify.
METADATA            | Tipo de ação de alteração de dados de uma Meta.
PROTECT_ADHOC            | Um proteger por tipo de ação de política ad hoc.
PROTECT_BY_TEMPLATE            | Um proteger por tipo de ação de modelo.
PROTECT_DO_NOT_FORWARD            | Um proteger por não reencaminhar o tipo de ação.
REMOVE_CONTENT_FOOTER            | Remova o tipo de ação de rodapé de conteúdo.
REMOVE_CONTENT_HEADER            | Remova tipo de conteúdo do cabeçalho de ação.
REMOVE_PROTECTION            | Remova o tipo de ação de proteção.
REMOVE_WATERMARK            | Remova tipo de ação de marca d'água.
APPLY_LABEL            | Aplicam-se o tipo de ação da etiqueta.
RECOMMEND_LABEL            | Recomendamos o tipo de ação da etiqueta.


### <a name="assignmentmethod"></a>AssignmentMethod

O método de atribuição da etiqueta do documento. Se a atribuição da etiqueta foi feita automaticamente, padrão ou como uma operação com privilégios (o equivalente a uma operação de administrador).

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
STANDARD            | [Etiqueta](class_mip_label.md) é o método de atribuição standard
COM PRIVILÉGIOS            | [Etiqueta](class_mip_label.md) privilegiado do método de atribuição
AUTO            | [Etiqueta](class_mip_label.md) método de atribuição é automático


### <a name="consent"></a>Consentimento

Resposta de um utilizador quando consentimento é solicitado para ligar a um ponto de extremidade de serviço.

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
AcceptAlways            | Dar consentimento e lembre-se esta decisão
Aceitar            | Dar consentimento, apenas uma vez
Rejeitar            | Não consentimento


### <a name="contentformat"></a>ContentFormat

Formato de conteúdo.

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
PADRÃO            | Formato de conteúdo é o formato de arquivo padrão
CORREIO ELETRÓNICO            | Formato do conteúdo é o formato de correio eletrónico

### <a name="contentmarkalignment"></a>ContentMarkAlignment

Marca de alinhamento para o conteúdo (conteúdo cabeçalho ou rodapé de conteúdo).

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
À ESQUERDA            | Marcação de conteúdo é alinhada à esquerda
DIREITA            | Marcação de conteúdo é alinhada à direita
CENTRO            | Marcação de conteúdo centra-se

### <a name="datastate"></a>DataState
 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
REST            | Armazenados fisicamente em bases de dados/ficheiro/armazéns de dados Inativos
EQUIPE DO MOTION            | Dados atravessar uma rede ou temporariamente que reside na memória do computador para ser de leitura ou atualizado
USE            | Dados ativos em constante mudança armazenado fisicamente em bases de dados/ficheiro/armazéns etc


### <a name="errortype"></a>ErrorType
 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | Autor da chamada transmitida uma entrada incorreta.
FILE_IO_ERROR            | Erro de e/s de arquivo de geral.
NETWORK_ERROR            | Problemas gerais de rede; Por exemplo, serviço inacessível.
TRANSIENT_NETWORK_ERROR            | Problemas de rede transitórios; Por exemplo, gateway inválido.
INTERNAL_ERROR            | Erros inesperados internos.
JUSTIFICATION_REQUIRED            | Deve fornecer a justificação para concluir a ação no ficheiro.
NOT_SUPPORTED_OPERATION            | A operação pedida ainda não é suportada.
PRIVILEGED_REQUIRED            | Não é possível substituir a etiqueta com privilégios quando o novo método de etiqueta é padrão.
ACCESS_DENIED            | O utilizador não foi possível obter acesso aos serviços.
CONSENT_DENIED            | Uma operação que é necessário o consentimento do utilizador não foi concedida ao consentimento.
POLICY_SYNC_ERROR            | Falha ao tentar sincronizar dados de política.
NO_PERMISSIONS            | O utilizador não foi possível obter acesso ao conteúdo. Por exemplo, não existem permissões, conteúdos revogado
NO_AUTH_TOKEN            | O utilizador não foi possível obter acesso ao conteúdo devido a um token de autenticação vazia.
DISABLED_SERVICE            | O utilizador não foi possível obter acesso ao conteúdo devido a ser desativada
PROXY_AUTH_ERROR            | Falha na autenticação de proxy.
NO_POLICY_ERROR            | Nenhuma política está configurada para o utilizador/inquilino
OPERATION_CANCELLED            | Operação cancelada
ADHOC_PROTECTION_REQUIRED            | Proteção do ad hoc deve ser definida para concluir a ação no arquivo.
  
### <a name="httprequesttype"></a>HttpRequestType

Tipo de pedido HTTP.

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
Obter            | GET
Post            | POST

  
### <a name="loglevel"></a>LogLevel

Níveis de registo diferentes utilizados em todo o SDK de MIP.

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
Rastreio            | 
Informações            | 
Aviso            | 
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions

Sinalizadores de bits que ditam o comportamento de criação de política adicionais.

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
Nenhuma            | Nenhum
OfflineOnly            | Não permita operações de rede e da interface do Usuário.
AllowAuditedExtraction            | Conteúdo pode ser aberto num aplicativo sem proteção-SDK-suporte para
PreferDeprecatedAlgorithms            | Utilização despromovida algoritmos criptográficos (ECB) para efeitos compatibilidade


### <a name="protectiontype"></a>ProtectionType

Descreve se proteção baseia-se desativar um modelo ou ad-hoc (personalizado).

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
TemplateBased            | Identificador foi criado a partir de um modelo
Personalizar            | Identificador foi criado ad hoc

  
### <a name="watermarklayout"></a>WatermarkLayout

Esquema das marcas d'água.

 Valores                         | Descrições                                
--------------------------------|---------------------------------------------
HORIZONTAL            | Esquema de marca d'água é horizontal
DIAGONAL LARGA            | Esquema de marca d'água é diagonal


## <a name="structures"></a>Estruturas 

### <a name="mipapplicationinfo"></a>mip::ApplicationInfo 
Uma estrutura que inclui informações específicas do aplicativo.
  
#### <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
applicationId Std:: String pública  |  Identificador da aplicação como definido no portal do AAD, (deve ser um GUID sem parênteses Retos).
applicationName Std:: String pública  |  Nome da aplicação, (deve conter apenas carateres ASCII válido excluindo ';')
public std::string applicationVersion  |  A versão do aplicativo a ser utilizado, (deve conter apenas carateres ASCII válido excluindo ';')
  
#### <a name="members"></a>Membros
  
##### <a name="applicationid-struct-member"></a>Membro de struct applicationId
Identificador da aplicação como definido no portal do AAD, (deve ser um GUID sem parênteses Retos).
  
##### <a name="applicationname-struct-member"></a>applicationName struct membro
Nome da aplicação, (deve conter apenas carateres ASCII válido excluindo ';')
  
##### <a name="applicationversion-struct-member"></a>Membro de struct applicationVersion
A versão do aplicativo a ser utilizado, (deve conter apenas carateres ASCII válido excluindo ';')  

### <a name="mippublishinglicensecontext"></a>mip::PublishingLicenseContext 
Contém os detalhes de uma licença de publicação utilizado para criar um manipulador de proteção.
  
#### <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público const Std:: vector\<uint8_t\> licenseInfo  | _Ainda não documentado._
público const Std:: vector\<uint8_t\> serializedPublishingLicense  | _Ainda não documentado._
PublishingLicenseContext pública (Std:: vector const\<uint8_t\>& licenseInfo, Std:: vector const\<uint8_t\>& serializedPublishingLicense)  | _Ainda não documentado._
  
#### <a name="members"></a>Membros
  
##### <a name="licenseinfo-struct-member"></a>Membro de struct licenseInfo
_Não documentados ainda._

  
##### <a name="serializedpublishinglicense-struct-member"></a>Membro de struct serializedPublishingLicense
_Não documentados ainda._

  
##### <a name="publishinglicensecontext-function"></a>Função de PublishingLicenseContext
_Não documentados ainda._
