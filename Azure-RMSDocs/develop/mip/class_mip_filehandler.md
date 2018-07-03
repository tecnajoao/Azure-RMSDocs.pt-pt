# <a name="class-mipfilehandler"></a>classe mip::FileHandler 
Interface para o ficheiro de todas as funções de manipulação.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
GetLabelAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a obter a etiqueta de sensibilidade do ficheiro.
GetProtectionAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a obter a política de proteção do ficheiro.
 SetLabel void pública (const Std:: String & labelId, const LabelingOptions & labelingOptions)  |  Define a etiqueta de sensibilidade para o ficheiro.
 público DeleteLabel void (método AssignmentMethod, const Std:: String e justificationMessage)  |  Elimina a etiqueta de sensibilidade a partir do ficheiro.
SetProtection void pública (const std::shared_ptr<ProtectionDescriptor>& protectionDescriptor)  |  Define personalizado ou modelo com base em permissões (de acordo com protectionDescriptor -> GetProtectionType) para o ficheiro.
 público RemoveProtection() void  |  Remove a proteção do ficheiro. Se o ficheiro tem o nome, a etiqueta serão perdida.
CommitAsync void pública (Std:: String const & outputFilePath, const std::shared_ptr<void>& contexto) | Grava as alterações para o ficheiro especificado pelo \|outputFilePath\ |  parâmetro.
CommitAsync void pública (const std::shared_ptr<Stream>& outputStream, const std::shared_ptr<void>& contexto) | Grava as alterações no fluxo especificado pelo \|outputStream\ |  parâmetro.
 público Std:: String GetOutputFileName()  |  Calcula o nome de ficheiro de saída e a extensão com base no nome do ficheiro original e as alterações acumuladas.
 público ~FileHandler() virtual  | _Ainda não documentado._
 FileHandler() protegido  | _Ainda não documentado._
  
## <a name="members"></a>Membros
  
### <a name="getlabelasync"></a>GetLabelAsync
Começa a obter a etiqueta de sensibilidade do ficheiro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.

Parâmetros:  
* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="getprotectionasync"></a>GetProtectionAsync
Começa a obter a política de proteção do ficheiro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.

Parâmetros:  
* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="setlabel"></a>SetLabel
Define a etiqueta de sensibilidade para o ficheiro.
As alterações não serão escritas para o ficheiro até CommitAsync será chamado.
Lança [JustificationRequiredError](class_mip_justificationrequirederror.md) quando definir a etiqueta requer uma justificação e nenhuma mensagem de justificação foi fornecida por meio do parâmetro labelingOptions.
  
### <a name="deletelabel"></a>DeleteLabel
Elimina a etiqueta de sensibilidade a partir do ficheiro.
As alterações não serão escritas para o ficheiro até CommitAsync será chamado. Com privilégios e o método de automática permite que a API para substituir qualquer lança etiqueta existente [JustificationRequiredError](class_mip_justificationrequirederror.md) quando definir a etiqueta requer uma justificação e nenhuma mensagem de justificação foi fornecida por meio do justificationMessage parâmetro.
  
### <a name="setprotection"></a>SetProtection
Define personalizado ou modelo com base em permissões (de acordo com protectionDescriptor -> GetProtectionType) para o ficheiro.
As alterações não serão escritas para o ficheiro até CommitAsync será chamado.
  
### <a name="removeprotection"></a>RemoveProtection
Remove a proteção do ficheiro. Se o ficheiro tem o nome, a etiqueta serão perdida.
As alterações não serão escritas para o ficheiro até CommitAsync será chamado.
  
### <a name="commitasync"></a>CommitAsync
Grava as alterações para o ficheiro especificado pelo | outputFilePath | parâmetro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.
  
### <a name="commitasync"></a>CommitAsync
Grava as alterações no fluxo especificado pelo | outputStream | parâmetro.
[FileHandler::Observer](class_mip_filehandler_observer.md) será chamado após o êxito ou falha.
  
### <a name="getoutputfilename"></a>GetOutputFileName
Calcula o nome de ficheiro de saída e a extensão com base no nome do ficheiro original e as alterações acumuladas.
  
### <a name="filehandler"></a>~ FileHandler
_Não documentados ainda._

  
### <a name="filehandler"></a>FileHandler
_Não documentados ainda._
