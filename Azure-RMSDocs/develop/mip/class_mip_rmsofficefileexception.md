# <a name="class-miprmsofficefileexception"></a>classe mip::RMSOfficeFileException 
Exceção de ficheiro do Office para RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 RMSOfficeFileException público (const std::string & mensagem, razão razão)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md) construtor.
 RMSOfficeFileException público (const char * const & mensagem, razão razão)  |  [RMSOfficeFileException](class_mip_rmsofficefileexception.md) construtor.
 pública reason() virtual razão const  |  Obtém a classificação de falha de ficheiros do Office.
 pública virtual const char * what() const  |  Obtém a mensagem de exceção.
 pública type() virtual ExceptionTypes const  |  Obtém o tipo de exceção.
 int virtual pública error() const  |  Obtém o código de erro.
  
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
  
### <a name="what"></a>O que
Obtém a mensagem de exceção.

  
**Devolve**: mensagem de exceção
  
### <a name="exceptiontypes"></a>ExceptionTypes
Obtém o tipo de exceção.

  
**Devolve**: tipo de exceção
  
### <a name="error"></a>Erro
Obtém o código de erro.

  
**Devolve**: [erro](class_mip_error.md) código