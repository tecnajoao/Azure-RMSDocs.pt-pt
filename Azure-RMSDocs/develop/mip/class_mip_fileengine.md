# <a name="class-mipfileengine"></a>classe mip::FileEngine 
Interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público ~FileEngine() virtual  | _Ainda não documentado._
 Definições de const públicas & GetSettings() const  |  Devolve as definições de motor.
Std:: vector const público < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Devolve uma lista de etiquetas de sensibilidade.
CreateFileHandlerAsync void pública (Std:: String const & inputFilePath, std::shared_ptr const < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& contexto)  |  Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.
CreateFileHandlerAsync void pública (const std::shared_ptr<Stream>& inputStream, const Std:: String e inputFileName, const std::shared_ptr < FileHandler::Observer > e fileHandlerObserver, const std::shared_ptr<void>& contexto)  |  É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.
 FileEngine() protegido  | _Ainda não documentado._
  
## <a name="members"></a>Membros
  
### <a name="fileengine"></a>~ FileEngine
_Não documentados ainda._

  
### <a name="settings"></a>Definições
Devolve as definições de motor.
  
### <a name="label"></a>Etiqueta
Devolve uma lista de etiquetas de sensibilidade.
  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.

Parâmetros:  
* **O**: ficheiro para o abrir. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. 


* **R**: a implementação da classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.

Parâmetros:  
* **A**: stream que representa o arquivo. 


* **O**: caminho do ficheiro. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. 


* **R**: a implementação da classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="fileengine"></a>FileEngine
_Não documentados ainda._
