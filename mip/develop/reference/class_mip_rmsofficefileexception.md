# <a name="class-miprmsofficefileexception"></a>classe mip::RMSOfficeFileException 
Exceção de ficheiro do Office para RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 RMSOfficeFileException pública (Std:: String const & mensagem, o motivo de motivo)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md) construtor.
 RMSOfficeFileException pública (const char * const & da mensagem, o motivo de motivo)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md) construtor.
 público reason() virtual motivo const  |  Obtém a classificação de falha de ficheiros do Office.
 público virtual const char * what() const  |  Obtém a mensagem de exceção.
 público type() virtual ExceptionTypes const  |  Obtém o tipo de exceção.
 público int virtual error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](class_mip_rmsofficefileexception.md) construtor.

Parâmetros:  
* **mensagem**: mensagem de exceção 


* **motivo**: classificação de falha de ficheiros do Office


  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](class_mip_rmsofficefileexception.md) construtor.

Parâmetros:  
* **mensagem**: mensagem de exceção 


* **motivo**: classificação de falha de ficheiros do Office


  
### <a name="reason"></a>Razão
Obtém a classificação de falha de ficheiros do Office.

  
**Devolve**: classificação de falha de ficheiros do Office
  
### <a name="what"></a>o que
Obtém a mensagem de exceção.

  
**Devolve**: mensagem de exceção
  
### <a name="exceptiontypes"></a>ExceptionTypes
Obtém o tipo de exceção.

  
**Devolve**: tipo de exceção
  
### <a name="error"></a>erro
Obtém o código de erro.

  
**Devolve**: [erro](class_mip_error.md) código