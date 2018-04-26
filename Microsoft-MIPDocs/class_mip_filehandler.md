# <a name="class-mipfilehandler"></a>classe mip::FileHandler 
Interface para o ficheiro de todas as funções de processamento.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
GetLabelAsync void público | Inicia a obter a etiqueta de sensibilidade do ficheiro.
GetProtectionAsync void público | Inicia a obter a política de proteção a partir do ficheiro.
pública SetLabelLabelingOptions void & labelingOptions) | Define a etiqueta de sensibilidade para o ficheiro.
DeleteLabel void público | Elimina a etiqueta de sensibilidade do ficheiro.
pública SetCustomPermissionsPolicyDescriptor void > & policydescriptor …) | Define as permissões personalizadas para o ficheiro.
RemoveProtection void público | Remove a proteção do ficheiro. Se o ficheiro tem o nome, a etiqueta serão perdida.
CommitAsync void público | Grava as alterações para o ficheiro especificado pelo \|outputFilePath\| parâmetro.
pública CommitAsyncStream void > & outputStream, const std::shared_ptr < void > & contexto) | Grava as alterações no fluxo especificada pelo \|outputStream\| parâmetro.
std::string pública GetOutputFileName | Calcula o nome de ficheiro de saída e a extensão com base no nome do ficheiro original e as alterações acumuladas.
pública inline virtual ~ FileHandler | 
inline protegido FileHandler | 
## <a name="members"></a>Membros
### <a name="getlabelasync"></a>GetLabelAsync
Inicia a obter a etiqueta de sensibilidade do ficheiro.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) será chamado após o êxito ou falha.
#### <a name="parameters"></a>Parâmetros
* contexto de cliente de contexto que será transmitido opaquely novamente para o observador.
### <a name="getprotectionasync"></a>GetProtectionAsync
Inicia a obter a política de proteção a partir do ficheiro.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) será chamado após o êxito ou falha.
#### <a name="parameters"></a>Parâmetros
* contexto de cliente de contexto que será transmitido opaquely novamente para o observador.
### <a name="setlabel"></a>SetLabel
Define a etiqueta de sensibilidade para o ficheiro.
As alterações não serão escritas para o ficheiro até CommitAsync será chamado.
Emitir [JustificationRequiredError](#classmip_1_1_justification_required_error) quando definir a etiqueta necessita de uma justificação e não foi fornecida nenhuma mensagem justificação através do parâmetro labelingOptions.
### <a name="deletelabel"></a>DeleteLabel
Elimina a etiqueta de sensibilidade do ficheiro.
As alterações não serão escritas para o ficheiro até CommitAsync será chamado. Método Privilegd e automática permite que a API substituir qualquer gera etiqueta existente [JustificationRequiredError](#classmip_1_1_justification_required_error) quando definir a etiqueta necessita de uma justificação e não foi fornecida nenhuma mensagem justificação através de justificationMessage parâmetro.
### <a name="setcustompermissions"></a>SetCustomPermissions
Define as permissões personalizadas para o ficheiro.
As alterações não serão escritas para o ficheiro até CommitAsync será chamado.
### <a name="removeprotection"></a>RemoveProtection
Remove a proteção do ficheiro. Se o ficheiro tem o nome, a etiqueta serão perdida.
As alterações não serão escritas para o ficheiro até CommitAsync será chamado.
### <a name="commitasync"></a>CommitAsync
Grava as alterações para o ficheiro especificado pelo | outputFilePath | parâmetro.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) será chamado após o êxito ou falha.
### <a name="commitasync"></a>CommitAsync
Grava as alterações no fluxo especificada pela | outputStream | parâmetro.
[FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) será chamado após o êxito ou falha.
### <a name="getoutputfilename"></a>GetOutputFileName
Calcula o nome de ficheiro de saída e a extensão com base no nome do ficheiro original e as alterações acumuladas.
### <a name="filehandler"></a>~ FileHandler
### <a name="filehandler"></a>FileHandler