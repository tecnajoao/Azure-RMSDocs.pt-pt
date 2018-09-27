# <a name="functions"></a>Funções

 Funções (âmbito)                        | Descrições                                
--------------------------------|---------------------------------------------
público const Std:: String & GetCustomSettingExportPolicyFileName()       |  Nome da definição para especificar explicitamente o caminho do ficheiro para exportar dados de política de SCC.
público const Std:: String & GetCustomSettingPolicyDataFile()       |  Nome da definição para especificar explicitamente o caminho do ficheiro de dados de política.
público const Std:: String & GetCustomSettingPolicyDataName()       |  Nome da definição para especificar explicitamente os dados de política.
**funções de Mip** |
std::shared_ptr público < mip::Stream > CreateStreamFromBuffer (uint8_t * buffer, tamanho de int64_t const)       |  Cria um [Stream](class_mip_stream.md) de uma memória intermédia.
std::shared_ptr público < mip::Stream > CreateStreamFromStdStream (const std::shared_ptr < std::iostream > & stdIOStream)       |  Cria um [Stream](class_mip_stream.md) de um std::iostream.
std::shared_ptr público < mip::Stream > CreateStreamFromStdStream (const std::shared_ptr < std::istream > & stdIStream)       |  Cria um [Stream](class_mip_stream.md) de um std::istream.
std::shared_ptr público < mip::Stream > CreateStreamFromStdStream (const std::shared_ptr < std::ostream > & stdOStream)       |  Cria um [Stream](class_mip_stream.md) de um std::ostream.
ReleaseAllResources() de void MIP_API pública       |  Todos os recursos (threads, etc.) antes do Desligamento de versão.
**funções de Mip::Rights**|
público Std:: String AuditedExtract()       |  Obtém de cadeias de caracteres identificador para "auditado extrair" à direita.
público Std:: String Comment()       |  Obtém de cadeias de caracteres identificador de "Comentários" à direita.
público Std:: vector Std:: < String > CommonRights()       |  Obtém uma lista de direitos que se aplicam a todos os cenários.
público Std:: String Edit()       |  Obtém o identificador para "Editar" certo de cadeia.
público Std:: vector Std:: < String > EditableDocumentRights()       |  Obtém uma lista de direitos que se aplicam aos documentos.
público Std:: vector Std:: < String > EmailRights()       |  Obtém uma lista de direitos que se aplicam a mensagens de correio eletrónico.
público Std:: String Export()       |  Obtém de cadeias de caracteres identificador para "Exportar" à direita.
público Std:: String Extract()       |  Obtém de cadeias de caracteres identificador para '' direito extrair.
público Std:: String Forward()       |  Obtém de cadeias de caracteres identificador para a direita 'Encaminhamento'.
público Std:: String Owner()       |  Obtém o identificador para o "proprietário" certo de cadeia.
público Std:: String Print()       |  Obtém o identificador para a direita "impressão" de cadeia.
público Std:: String Reply()       |  Obtém cadeia de identificador de "resposta" à direita.
público Std:: String ReplyAll()       |  Obtém de cadeias de caracteres identificador para o direito de "responder a todos".
público Std:: String View()       |  Obtém cadeia certo identificador para 'view'.
**funções de Mip::roles**|
público Std:: String Author()       |  Obtém de cadeias de caracteres identificador para a função de "autor".
público Std:: String CoOwner()       |  Obtém o identificador para a função de 'coproprietário' de cadeia.
público Std:: String Reviewer()       |  Obtém o identificador para a função de "revisor" de cadeia.
público Std:: String Viewer()       |  Obtém o identificador para a função de "Visualizador" de cadeia.

  
## <a name="functions-common"></a>Funções (comum)

### <a name="getcustomsettingpolicydataname"></a>GetCustomSettingPolicyDataName
Nome da definição para especificar explicitamente os dados de política.

  
**Devolve**: A chave de definições personalizadas.
  
### <a name="getcustomsettingexportpolicyfilename"></a>GetCustomSettingExportPolicyFileName
Nome da definição para especificar explicitamente o caminho do ficheiro para exportar dados de política de SCC.

  
**Devolve**: A chave de definições personalizadas.
  
### <a name="getcustomsettingpolicydatafile"></a>GetCustomSettingPolicyDataFile
Nome da definição para especificar explicitamente o caminho do ficheiro de dados de política.

  
**Devolve**: A chave de definições personalizadas.

## <a name="functions-mip"></a>Funções (mip)

### <a name="mipcreatestreamfrombufferbuffer"></a>Mip::CreateStreamFromBuffer(buffer)

Cria um [Stream](class_mip_stream.md) de uma memória intermédia.

Parâmetros:  
* **memória intermédia**: aponta para um buffer

**Devolve**: **tamanho** da memória intermédia
  

### <a name="mipcreatestreamfromstdstreamistream"></a>Mip::CreateStreamFromStdStream(IStream)

Cria um [Stream](class_mip_stream.md) de um std::istream.

Parâmetros:  

* **stdIStream**: std::istream de segurança
  
**Devolve**: [Stream](class_mip_stream.md) um std::istream de encapsulamento de aplicações
  
### <a name="mipcreatestreamfromstdstreamostream"></a>Mip::CreateStreamFromStdStream(ostream)

Cria um [Stream](class_mip_stream.md) de um std::ostream.

Parâmetros:  
* **stdOStream**: std::ostream de segurança

  
**Devolve**: [Stream](class_mip_stream.md) um std::ostream de encapsulamento de aplicações
  
### <a name="mipcreatestreamfromstdstreamiostream"></a>Mip::CreateStreamFromStdStream(iostream)

Cria um [Stream](class_mip_stream.md) de um std::iostream.

Parâmetros:  
* **stdIOStream**: std::iostream de segurança
  
**Devolve**: [Stream](class_mip_stream.md) um std::iostream de encapsulamento de aplicações
  
### <a name="mipreleaseallresources"></a>Mip::ReleaseAllResources

Todos os recursos (threads, etc.) antes do Desligamento de versão.

Se as bibliotecas de dinâmicas de MIP estão carregados com atraso por uma aplicação, esta função tem de ser chamada antes do aplicativo explicitamente descarregamento dessas bibliotecas MIP para evitar o deadlock. Por exemplo, no win32, esta função tem de ser chamada antes de todas as chamadas para o descarregamento de explicitamente MIP DLLs via FreeLibrary ou \__FUnloadDelayLoadedDLL2. Aplicativos deverá liberar referências a todos os objetos de MIP (por exemplo, perfis, motores, manipuladores) antes de chamar essa função.

## <a name="functions-miprights"></a>Funções (mip::rights)

### <a name="auditedextract"></a>AuditedExtract
Obtém de cadeias de caracteres identificador para "auditado extrair" à direita.

  
**Devolve**: cadeia de identificador para "auditado extract" à direita
  
### <a name="comment"></a>Comentário
Obtém de cadeias de caracteres identificador de "Comentários" à direita.

  
**Devolve**: cadeia de identificador de "Comentários" à direita
  
### <a name="commonrights"></a>CommonRights
Obtém uma lista de direitos que se aplicam a todos os cenários.

  
**Devolve**: uma lista de direitos que se aplicam a todos os cenários

### <a name="edit"></a>Editar
Obtém o identificador para "Editar" certo de cadeia.

  
**Devolve**: identificador de cadeia de caracteres de "Editar" à direita
  
### <a name="editabledocumentrights"></a>EditableDocumentRights
Obtém uma lista de direitos que se aplicam aos documentos.

  
**Devolve**: uma lista de direitos que se aplicam a documentos
  
### <a name="emailrights"></a>EmailRights
Obtém uma lista de direitos que se aplicam a mensagens de correio eletrónico.

  
**Devolve**: uma lista de direitos que se aplicam a mensagens de correio eletrónico
  
### <a name="export"></a>Exportar
Obtém de cadeias de caracteres identificador para "Exportar" à direita.

  
**Devolve**: cadeia de identificador para "Exportar" à direita
  
### <a name="extract"></a>Extração
Obtém de cadeias de caracteres identificador para '' direito extrair.

  
**Devolve**: identificador de cadeia de caracteres para "extrair' direita
  

### <a name="forward"></a>Reencaminhar
Obtém de cadeias de caracteres identificador para a direita 'Encaminhamento'.

  
**Devolve**: cadeia de caracteres de identificador de direito de "reencaminhar"
  
### <a name="owner"></a>Proprietário
Obtém o identificador para o "proprietário" certo de cadeia.

  
**Devolve**: identificador de cadeia de caracteres para o "proprietário" certo
  
### <a name="print"></a>Imprimir
Obtém o identificador para a direita "impressão" de cadeia.

  
**Devolve**: cadeia de caracteres de identificador para a direita "impressão"
  
### <a name="reply"></a>Responder
Obtém cadeia de identificador de "resposta" à direita.

  
**Devolve**: cadeia de identificador de "resposta" à direita
  
### <a name="replyall"></a>ReplyAll
Obtém de cadeias de caracteres identificador para o direito de "responder a todos".

  
**Devolve**: cadeia de caracteres de identificador para o direito de "responder a todos"
  
### <a name="view"></a>Veja os
Obtém cadeia certo identificador para 'view'.

  
**Devolve**: cadeia de identificador para 'view' à direita
  
## <a name="functions-miproles"></a>Funções (mip::roles)

### <a name="author"></a>Autor
Obtém de cadeias de caracteres identificador para a função de "autor".

  
**Devolve**: identificador de cadeia de caracteres para a função de "autor" autor pode ver, editar, copiar e imprimir o conteúdo.
  
### <a name="coowner"></a>CoOwner
Obtém o identificador para a função de 'coproprietário' de cadeia.

  
**Devolve**: identificador de cadeia de caracteres para os coproprietário de função A 'coproprietário' tem todas as permissões

### <a name="reviewer"></a>Revisor
Obtém o identificador para a função de "revisor" de cadeia.

  
**Devolve**: identificador de cadeia de caracteres para a função de "revisor" um revisor pode visualizar e editar o conteúdo. Não é possível copiar ou imprimir.

### <a name="viewer"></a>Visualizador
Obtém o identificador para a função de "Visualizador" de cadeia.

  
**Devolve**: identificador de cadeia de caracteres para a função de "Visualizador" um visualizador só pode ver o conteúdo. Não é possível editar, copiar ou imprimir.
  
  
