# <a name="class-miprmspfileexception"></a>classe mip::RMSPFileException 
Exceção de RMS PFile.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 RMSPFileException público (const std::string & mensagem, razão razão)  |  [RMSPFileException](class_mip_rmspfileexception.md) construtor.
 RMSPFileException público (const char * const & mensagem, razão razão)  |  [RMSPFileException](class_mip_rmspfileexception.md) construtor.
 pública reason() virtual razão const  |  Obtém a classificação de erro PFile.
 pública virtual const char * what() const  |  Obtém a mensagem de exceção.
 pública type() virtual ExceptionTypes const  |  Obtém o tipo de exceção.
 int virtual pública error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](class_mip_rmspfileexception.md) construtor.

Parâmetros:  
* **mensagem**: mensagem de exceção 


* **motivo**: classificação de erro PFile


  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](class_mip_rmspfileexception.md) construtor.

Parâmetros:  
* **mensagem**: mensagem de exceção 


* **motivo**: classificação de erro PFile


  
### <a name="reason"></a>Razão
Obtém a classificação de erro PFile.

  
**Devolve**: classificação de erro PFile
  
### <a name="what"></a>O que
Obtém a mensagem de exceção.

  
**Devolve**: mensagem de exceção
  
### <a name="exceptiontypes"></a>ExceptionTypes
Obtém o tipo de exceção.

  
**Devolve**: tipo de exceção
  
### <a name="error"></a>Erro
Obtém o código de erro.

  
**Devolve**: [erro](class_mip_error.md) código