# <a name="class-mipfileengine"></a>classe mip::FileEngine 
Interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
~FileEngine() virtual inline público  |  
Definições de const público & GetSettings() const  |  Devolve as definições de motor.
pública std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Devolve uma lista de etiquetas de sensibilidade.
std::shared_ptr pública<FileHandler> CreateFileHandler (const std::string & inputFilePath, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver)  |  Devolve o processador de ficheiros de fornecidos o caminho de ficheiro.
std::shared_ptr pública<FileHandler> CreateFileHandler (const std::shared_ptr<Stream>& inputStream, const std::string & inputFileName, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver)  |  Devolve o processador de ficheiros de fornecido sequência de ficheiros.
inline protegido FileEngine()  |  
  
## <a name="members"></a>Membros
  
### <a name="fileengine"></a>~ FileEngine
  
### <a name="settings"></a>Definições
Devolve as definições de motor.
  
### <a name="label"></a>Etiqueta
Devolve uma lista de etiquetas de sensibilidade.
  
### <a name="filehandler"></a>FileHandler
Devolve o processador de ficheiros de fornecidos o caminho de ficheiro.
  
#### <a name="parameters"></a>Parâmetros
* O ficheiro para o abrir. O caminho tem de incluir o nome de ficheiro e, se existe, a extensão de nome de ficheiro. 
* Implementar uma classe a [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) interface.
  
### <a name="filehandler"></a>FileHandler
Devolve o processador de ficheiros de fornecido sequência de ficheiros.
  
#### <a name="parameters"></a>Parâmetros
* Um fluxo que representa o ficheiro. 
* O caminho para o ficheiro. O caminho tem de incluir o nome de ficheiro e, se existe, a extensão de nome de ficheiro. 
* Implementar uma classe a [FileHandler::Observer](#classmip_1_1_file_handler_1_1_observer) interface.
  
### <a name="fileengine"></a>FileEngine