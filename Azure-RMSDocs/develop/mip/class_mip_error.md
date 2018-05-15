# <a name="class-miperror"></a>classe mip::Error 
Classe de todos os erros que serão comunicadas (emitida ou devolvido) base do MIP SDK.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 const char pública const * what()  |  Receber uma mensagem de erro cstring.
std::shared_ptr pública<Error> const clone)  |  Clone o erro.
 pública GetErrorType() virtual ErrorType const  |  Obter o tipo de erro.
 pública std::string const virtual & GetErrorName() const  |  Obter o nome de erro.
 pública std::string const virtual & GetMessage() const  |  Obter a mensagem de erro.
 SetMessage void de virtual público (const std::string & tarifas de mensagens)  |  Defina a mensagem de erro.
  
## <a name="members"></a>Membros
  
### <a name="what"></a>O que
Receber uma mensagem de erro cstring.

  
**Devolve**: um cstring err mensagem
  
### <a name="error"></a>Error
Clone o erro.

  
**Devolve**: um clone do erro.
  
### <a name="errortype"></a>ErrorType
Obter o tipo de erro.

  
**Devolve**: O tipo de erro.
  
### <a name="geterrorname"></a>GetErrorName
Obter o nome de erro.

  
**Devolve**: O nome de erro.
  
### <a name="getmessage"></a>GetMessage
Obter a mensagem de erro.

  
**Devolve**: A mensagem de erro.
  
### <a name="setmessage"></a>SetMessage
Defina a mensagem de erro.

Parâmetros:  
* **tarifas de mensagens**: a mensagem de erro.

