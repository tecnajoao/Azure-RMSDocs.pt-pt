# <a name="class-mipfileengine"></a>classe mip::FileEngine 
Interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 pública ~FileEngine() virtual  | _Ainda não documentado._
 Definições de const público & GetSettings() const  |  Devolve as definições de motor.
pública std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Devolve uma lista de etiquetas de sensibilidade.
std::shared_ptr pública<FileHandler> CreateFileHandler (const std::string & inputFilePath, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver)  |  Devolve o processador de ficheiros de fornecidos o caminho de ficheiro.
std::shared_ptr pública<FileHandler> CreateFileHandler (const std::shared_ptr<Stream>& inputStream, const std::string & inputFileName, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver)  |  Devolve o processador de ficheiros de fornecido sequência de ficheiros.
 FileEngine() protegido  | _Ainda não documentado._
  
## <a name="members"></a>Membros
  
### <a name="fileengine"></a>~ FileEngine
_Não documentados ainda._

  
### <a name="settings"></a>Definições
Devolve as definições de motor.
  
### <a name="label"></a>Etiqueta
Devolve uma lista de etiquetas de sensibilidade.
  
### <a name="filehandler"></a>FileHandler
Devolve o processador de ficheiros de fornecidos o caminho de ficheiro.

Parâmetros:  
* **O**: ficheiro para o abrir. O caminho tem de incluir o nome de ficheiro e, se existe, a extensão de nome de ficheiro. 


* **A**: implementar a classe de [FileHandler::Observer](class_mip_filehandler_observer.md) interface.


  
### <a name="filehandler"></a>FileHandler
Devolve o processador de ficheiros de fornecido sequência de ficheiros.

Parâmetros:  
* **A**: fluxo que representa o ficheiro. 


* **O**: caminho do ficheiro. O caminho tem de incluir o nome de ficheiro e, se existe, a extensão de nome de ficheiro. 


* **A**: implementar a classe de [FileHandler::Observer](class_mip_filehandler_observer.md) interface.


  
### <a name="fileengine"></a>FileEngine
_Não documentados ainda._
