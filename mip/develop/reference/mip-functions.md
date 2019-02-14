---
title: Funções
description: Funções
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.date: 01/28/2019
ms.author: bryanla
ms.openlocfilehash: 614e4bdd589e8c7ad3efdbf9be2f807e6d4ec43a
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254191"
---
# <a name="functions"></a>Funções

## <a name="summary"></a>Resumo

| Funções pelo âmbito do espaço de nomes   | Descrições                                |
|--------------------------------|---------------------------------------------|
**Namespace `mip` :** |
público Std:: String GetAssignmentMethodString (método AssignmentMethod)       |  Converte AssignmentMethod enum para uma descrição de cadeia de caracteres.
público estático Std:: String GetActionSourceString (ActionSource actionSource)       |  Obtenha o nome da origem de ação.
public static std::string GetContentStateString(mip::ContentState state)       |  Obtenha o nome do Estado de conteúdo.
public const std::string& GetCustomSettingPolicyDataName()       |  Nome da definição para especificar explicitamente os dados de política.
public const std::string& GetCustomSettingExportPolicyFileName()       |  Nome da definição para especificar explicitamente o caminho do ficheiro para exportar dados de política de SCC.
public const std::string& GetCustomSettingSensitivityTypesDataName()       |  Nome da definição para especificar explicitamente os dados de sensibilidade.
public const std::string& GetCustomSettingPolicyDataFile()       |  Nome da definição para especificar explicitamente o caminho do ficheiro de dados de política.
public const std::string& GetCustomSettingSensitivityTypesDataFile()       |  Nome da definição para especificar explicitamente o caminho do ficheiro de dados de tipos de sensibilidade.
público __CDECL de void MIP_API ReleaseAllResources()       |  Todos os recursos (threads, etc.) antes do encerramento da versão.
público MIP_API std::shared_ptr\<mip::Stream\> CreateStreamFromStdStream (const std::shared_ptr\<std::istream\>& stdIStream)       |  Cria um [Stream](class_mip_stream.md) de um std::istream.
público MIP_API std::shared_ptr\<mip::Stream\> CreateStreamFromStdStream (const std::shared_ptr\<std::ostream\>& stdOStream)       |  Cria um [Stream](class_mip_stream.md) de um std::ostream.
público MIP_API std::shared_ptr\<mip::Stream\> CreateStreamFromStdStream (const std::shared_ptr\<std::iostream\>& stdIOStream)       |  Cria um [Stream](class_mip_stream.md) de um std::iostream.
público MIP_API std::shared_ptr\<mip::Stream\> CreateStreamFromBuffer (uint8_t * buffer, tamanho de int64_t const)       |  Cria um [Stream](class_mip_stream.md) de uma memória intermédia.
 | 
**Namespace `mip::auditmetadatakeys` :** |
público Std:: String Sender()       |  Chaves de metadados na representação de cadeia de caracteres de auditoria.
público Std:: String Recipients()       | _Ainda não documentado._
público Std:: String LastModifiedBy()       | _Ainda não documentado._
público Std:: String LastModifiedDate()       | _Ainda não documentado._
 | 
**Namespace `mip::rights` :** |
público Std:: String Owner()       |  Obtém o identificador para o "proprietário" certo de cadeia.
público Std:: String View()       |  Obtém cadeia certo identificador para 'view'.
público Std:: String AuditedExtract()       |  Obtém de cadeias de caracteres identificador para "auditado extrair" à direita.
public std::string Edit()       |  Obtém o identificador para "Editar" certo de cadeia.
público Std:: String Export()       |  Obtém de cadeias de caracteres identificador para "Exportar" à direita.
público Std:: String Extract()       |  Obtém de cadeias de caracteres identificador para '' direito extrair.
público Std:: String Print()       |  Obtém o identificador para a direita "impressão" de cadeia.
público Std:: String Comment()       |  Obtém de cadeias de caracteres identificador de "Comentários" à direita.
public std::string Reply()       |  Obtém cadeia de identificador de "resposta" à direita.
public std::string ReplyAll()       |  Obtém de cadeias de caracteres identificador para o direito de "responder a todos".
público Std:: String Forward()       |  Obtém de cadeias de caracteres identificador para a direita 'Encaminhamento'.
public std::vector\<std::string\> EmailRights()       |  Obtém uma lista de direitos que se aplicam a mensagens de correio eletrónico.
public std::vector\<std::string\> EditableDocumentRights()       |  Obtém uma lista de direitos que se aplicam aos documentos.
public std::vector\<std::string\> CommonRights()       |  Obtém uma lista de direitos que se aplicam a todos os cenários.
 | 
**Namespace `mip::roles` :** |
público Std:: String Viewer()       |  Obtém o identificador para a função de "Visualizador" de cadeia.
public std::string Reviewer()       |  Obtém o identificador para a função de "revisor" de cadeia.
público Std:: String Author()       |  Obtém de cadeias de caracteres identificador para a função de "autor".
público Std:: String CoOwner()       |  Obtém o identificador para a função de 'coproprietário' de cadeia.



## <a name="namespace-mip"></a>Namespace `mip`

### <a name="getassignmentmethodstring-function"></a>Função de GetAssignmentMethodString
Converte AssignmentMethod enum para uma descrição de cadeia de caracteres.

Parâmetros:  
* **método**: um método de atribuição. 



  
**Devolve**: Uma descrição de cadeia de caracteres do método de atribuição.
  
### <a name="getactionsourcestring-function"></a>Função de GetActionSourceString
Obtenha o nome da origem de ação.

Parâmetros:  
* **actionSource**: A origem de ação. 



  
**Devolve**: Uma representação de cadeia de caracteres de origem de ação.
  
### <a name="getcontentstatestring-function"></a>Função de GetContentStateString
Obtenha o nome do Estado de conteúdo.

Parâmetros:  
* **actionSource**: O estado do conteúdo a ser executado após. 



  
**Devolve**: Uma representação de cadeia de caracteres do Estado do conteúdo.
  
### <a name="getcustomsettingpolicydataname-function"></a>Função de GetCustomSettingPolicyDataName
Nome da definição para especificar explicitamente os dados de política.

  
**Devolve**: A chave de definições personalizadas.
  
### <a name="getcustomsettingexportpolicyfilename-function"></a>Função de GetCustomSettingExportPolicyFileName
Nome da definição para especificar explicitamente o caminho do ficheiro para exportar dados de política de SCC.

  
**Devolve**: A chave de definições personalizadas.
  
### <a name="getcustomsettingsensitivitytypesdataname-function"></a>Função de GetCustomSettingSensitivityTypesDataName
Nome da definição para especificar explicitamente os dados de sensibilidade.

  
**Devolve**: A chave de definições personalizadas.
  
### <a name="getcustomsettingpolicydatafile-function"></a>Função de GetCustomSettingPolicyDataFile
Nome da definição para especificar explicitamente o caminho do ficheiro de dados de política.

  
**Devolve**: A chave de definições personalizadas.
  
### <a name="getcustomsettingsensitivitytypesdatafile-function"></a>Função de GetCustomSettingSensitivityTypesDataFile
Nome da definição para especificar explicitamente o caminho do ficheiro de dados de tipos de sensibilidade.

  
**Devolve**: A chave de definições personalizadas.
  
### <a name="releaseallresources-function"></a>Função de ReleaseAllResources
Todos os recursos (threads, etc.) antes do encerramento da versão.
Se as bibliotecas de dinâmicas de MIP estão carregados com atraso por uma aplicação, esta função tem de ser chamada antes da aplicação dessas bibliotecas MIP o descarregamento explicitamente para evitar o deadlock. Por exemplo, no win32, essa função deve ser chamada antes de todas as chamadas para explicitamente descarregar MIP DLLs via FreeLibrary ou __FUnloadDelayLoadedDLL2. Aplicativos deverá liberar referências a todos os objetos de MIP (por exemplo, manipuladores de perfis, motores,) antes de chamar essa função.
  
### <a name="operator-function"></a>operador | função
Operador de OR bit a bit ProtectionHandlerCreationOptions.

Parâmetros:  
* **a**: Valor da esquerda 


* **b**: Valor da direita



  
**Devolve**: OR bit a bit de ProtectionHandlerCreationOptions
  
### <a name="createstreamfromstdstream-function"></a>Função de CreateStreamFromStdStream
Cria um [Stream](class_mip_stream.md) de um std::istream.

Parâmetros:  
* **stdIStream**: Std::istream de segurança



  
**Devolve**: [Stream](class_mip_stream.md) um std::istream de encapsulamento de aplicações
  
### <a name="createstreamfromstdstream-function"></a>Função de CreateStreamFromStdStream
Cria um [Stream](class_mip_stream.md) de um std::ostream.

Parâmetros:  
* **stdOStream**: Std::ostream de segurança



  
**Devolve**: [Stream](class_mip_stream.md) um std::ostream de encapsulamento de aplicações
  
### <a name="createstreamfromstdstream-function"></a>Função de CreateStreamFromStdStream
Cria um [Stream](class_mip_stream.md) de um std::iostream.

Parâmetros:  
* **stdIOStream**: Std::iostream de segurança



  
**Devolve**: [Stream](class_mip_stream.md) um std::iostream de encapsulamento de aplicações
  
### <a name="createstreamfrombuffer-function"></a>Função de CreateStreamFromBuffer
Cria um [Stream](class_mip_stream.md) de uma memória intermédia.

Parâmetros:  
* **memória intermédia**: Aponta para um buffer



  
**Devolve**: Tamanho de tamanho do buffer
  



## <a name="namespace-mipauditmetadatakeys"></a>Namespace `mip::auditmetadatakeys`

### <a name="sender-function"></a>Função de remetente
Chaves de metadados na representação de cadeia de caracteres de auditoria.
  
### <a name="recipients-function"></a>Função de destinatários
_Não documentados ainda._

  
### <a name="lastmodifiedby-function"></a>Função de LastModifiedBy
_Não documentados ainda._
  
### <a name="lastmodifieddate-function"></a>Função de LastModifiedDate
_Não documentados ainda._





## <a name="namespace-miprights"></a>Namespace `mip::rights`

### <a name="owner-function"></a>Função de proprietário
Obtém o identificador para o "proprietário" certo de cadeia.

  
**Devolve**: Identificador para o "proprietário" certo de cadeias de caracteres
  
### <a name="view-function"></a>Função de vista
Obtém cadeia certo identificador para 'view'.

  
**Devolve**: Cadeia de identificador para 'view' à direita
  
### <a name="auditedextract-function"></a>Função de AuditedExtract
Obtém de cadeias de caracteres identificador para "auditado extrair" à direita.

  
**Devolve**: Cadeia de identificador para "auditado extract" à direita
  
### <a name="edit-function"></a>Editar função
Obtém o identificador para "Editar" certo de cadeia.

  
**Devolve**: Identificador de cadeia de caracteres para o direito de "Editar"
  
### <a name="export-function"></a>Função de exportação
Obtém de cadeias de caracteres identificador para "Exportar" à direita.

  
**Devolve**: Cadeia de identificador para "Exportar" à direita
  
### <a name="extract-function"></a>Extrair a função
Obtém de cadeias de caracteres identificador para '' direito extrair.

  
**Devolve**: Identificador de cadeia de caracteres para a direita 'extrair'
  
### <a name="print-function"></a>Função de impressa
Obtém o identificador para a direita "impressão" de cadeia.

  
**Devolve**: Cadeia de caracteres de identificador para a direita "impressão"
  
### <a name="comment-function"></a>Função de comentário
Obtém de cadeias de caracteres identificador de "Comentários" à direita.

  
**Devolve**: Cadeia de identificador de "Comentários" à direita
  
### <a name="reply-function"></a>Função de resposta
Obtém cadeia de identificador de "resposta" à direita.

  
**Devolve**: Cadeia de identificador de "resposta" à direita
  
### <a name="replyall-function"></a>Função de ReplyAll
Obtém de cadeias de caracteres identificador para o direito de "responder a todos".

  
**Devolve**: Cadeia de caracteres de identificador para o direito de "responder a todos"
  
### <a name="forward-function"></a>Função de encaminhamento
Obtém de cadeias de caracteres identificador para a direita 'Encaminhamento'.

  
**Devolve**: Cadeia de caracteres de identificador de direito de "reencaminhar"
  
### <a name="emailrights-function"></a>Função de EmailRights
Obtém uma lista de direitos que se aplicam a mensagens de correio eletrónico.

  
**Devolve**: Uma lista de direitos que se aplicam a mensagens de correio eletrónico
  
### <a name="editabledocumentrights-function"></a>Função de EditableDocumentRights
Obtém uma lista de direitos que se aplicam aos documentos.

  
**Devolve**: Uma lista de direitos que se aplicam a documentos
  
### <a name="commonrights-function"></a>Função de CommonRights
Obtém uma lista de direitos que se aplicam a todos os cenários.

  
**Devolve**: Uma lista de direitos que se aplicam a todos os cenários




## <a name="namespace-miproles"></a>Namespace `mip::roles`

### <a name="viewer-function"></a>Função de Visualizador
Obtém o identificador para a função de "Visualizador" de cadeia.

  
**Devolve**: Identificador de cadeia de caracteres para a função de "Visualizador" um visualizador só pode ver o conteúdo. Não é possível editar, copiar ou imprimir.
  
### <a name="reviewer-function"></a>Função do revisor
Obtém o identificador para a função de "revisor" de cadeia.

  
**Devolve**: Identificador de cadeia de caracteres para a função de "revisor" um revisor pode ver e editar o conteúdo. Não é possível copiar ou imprimir.
  
### <a name="author-function"></a>Função de autor
Obtém de cadeias de caracteres identificador para a função de "autor".

  
**Devolve**: Identificador para a função de "autor" autor pode ver, editar, copiar e imprimir o conteúdo de cadeia.
  
### <a name="coowner-function"></a>Função de coOwner
Obtém o identificador para a função de 'coproprietário' de cadeia.

  
**Devolve**: Identificador de cadeia de caracteres para a função de 'coproprietário' coproprietário tem todas as permissões
