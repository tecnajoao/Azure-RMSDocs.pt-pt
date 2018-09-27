# <a name="class-miprmspfileexception"></a>classe mip::RMSPFileException 
Exceção de RMS PFile.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 RMSPFileException pública (Std:: String const & mensagem, o motivo de motivo)  |  [RMSPFileException](class_mip_rmspfileexception.md) construtor.
 RMSPFileException pública (const char * const & da mensagem, o motivo de motivo)  |  [RMSPFileException](class_mip_rmspfileexception.md) construtor.
 público reason() virtual motivo const  |  Obtém a classificação de erro PFile.
 público virtual const char * what() const  |  Obtém a mensagem de exceção.
 público type() virtual ExceptionTypes const  |  Obtém o tipo de exceção.
 público int virtual error() const  |  Obtém o código de erro.
  
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
  
### <a name="what"></a>o que
Obtém a mensagem de exceção.

  
**Devolve**: mensagem de exceção
  
### <a name="exceptiontypes"></a>ExceptionTypes
Obtém o tipo de exceção.

  
**Devolve**: tipo de exceção
  
### <a name="error"></a>erro
Obtém o código de erro.

  
**Devolve**: [erro](class_mip_error.md) código