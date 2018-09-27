# <a name="class-mipfileengine"></a>classe mip::FileEngine 
Essa classe fornece uma interface para todas as funções de motor.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Devolve as definições de motor.
Std:: vector const público < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Devolve uma lista de etiquetas de sensibilidade.
 público const Std:: String & GetMoreInfoUrl() const  |  Forneça um url para buscar mais informações sobre as política/etiquetas.
 bool pública IsLabelingRequired() const  |  Verifica se é ou não a política determina que um documento deve ser o nome.
CreateFileHandlerAsync void pública (const Std:: String & inputFilePath, const mip::ContentState contentState, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& contexto)  |  Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.
CreateFileHandlerAsync void pública (const std::shared_ptr<Stream>& inputStream, const Std:: String & inputFileName, const mip::ContentState contentState, const std::shared_ptr < FileHandler::Observer > & fileHandlerObserver, const std::shared_ptr<void>& contexto)  |  É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Devolve as definições de motor.
  
### <a name="label"></a>Etiqueta
Devolve uma lista de etiquetas de sensibilidade.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Forneça um url para buscar mais informações sobre as política/etiquetas.

  
**Devolve**: um url no formato de cadeia de caracteres.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Verifica se é ou não a política determina que um documento deve ser o nome.

  
**Devolve**: VERDADEIRO se a etiquetagem é obrigatório, caso contrário FALSO.
  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
Caminho do ficheiro é iniciada a criação de um manipulador de arquivo para determinados.

Parâmetros:  
* **O**: ficheiro para o abrir. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. 


* **contentState**: O estado do conteúdo que está a ser alterado: MOTION | REST | UTILIZAÇÃO 


* **R**: a implementação da classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.


  
### <a name="createfilehandlerasync"></a>CreateFileHandlerAsync
É iniciada a criação de um manipulador de arquivo para determinados ficheiros stream.

Parâmetros:  
* **inputStream**: um fluxo que representa o ficheiro. 


* **inputFileName**: O caminho para o ficheiro. O caminho tem de incluir o nome de ficheiro e, se um existe, a extensão de nome de ficheiro. 


* **contentState**: O estado do conteúdo que está a ser alterado: MOTION | REST | UTILIZAÇÃO 


* **fileHandlerObserver**: implementar uma classe a [FileHandler::Observer](class_mip_filehandler_observer.md) interface. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para o observador.

