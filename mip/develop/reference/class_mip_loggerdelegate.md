# <a name="class-miploggerdelegate"></a>classe mip::LoggerDelegate 
Uma classe que define a interface para o agente de log do mip sdk.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Init void pública (Std:: String const & storagePath, LogLevel logLevel)  |  Inicialize o agente de log.
 público GetLogLevel() de LogLevel const  |  Obtenha o loglevel mínimo que irá acionar um evento de log.
 Flush () de void pública  |  Esvaziar o agente de log.
 WriteToLog void pública (nível de LogLevel const, Std:: String const & mensagem, Std:: String const & função, Std:: String const & ficheiro, const int32_t linha)  |  Escreva uma instrução de registo para o ficheiro de registo.
  
## <a name="members"></a>Membros
  
### <a name="init"></a>Init
Inicialize o agente de log.

Parâmetros:  
* **storagePath**: o caminho para a localização onde o estado persistente, incluindo registos, pode ser armazenado. 


* **logLevel**: o loglevel mínimo que irá acionar um evento de log.


  
### <a name="loglevel"></a>LogLevel
Obtenha o loglevel mínimo que irá acionar um evento de log.

  
**Devolve**: O loglevel mínimo que irá acionar um evento de log.
  
### <a name="flush"></a>Remoção da cache
Esvaziar o agente de log.
  
### <a name="writetolog"></a>WriteToLog
Escreva uma instrução de registo para o ficheiro de registo.

Parâmetros:  
* **nível**: loglevel para a instrução de log. 


* **mensagem**: a mensagem para a instrução de log. 


* **função**: o nome da função para a instrução de log. 


* **ficheiro**: o nome do ficheiro onde foi gerada a instrução de log. 


* **linha**: o número de linha em que a instrução de log foi gerada.

