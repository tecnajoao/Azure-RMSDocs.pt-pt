# <a name="class-miprmsexception"></a>classe mip::RMSException 
Exceção de base do RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 RMSException público (const ExceptionTypes tipo, erro de int const, const std::string & mensagem)  |  [RMSException](class_mip_rmsexception.md) construtor.
 RMSException público (tipo de const ExceptionTypes, erro de int const, const char * const & mensagem)  |  [RMSException](class_mip_rmsexception.md) construtor.
 pública virtual const char * what() const  |  Obtém a mensagem de exceção.
 pública type() virtual ExceptionTypes const  |  Obtém o tipo de exceção.
 int virtual pública error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmsexception"></a>RMSException
[RMSException](class_mip_rmsexception.md) construtor.

Parâmetros:  
* **tipo**: tipo de exceção 


* **erro**: [erro](class_mip_error.md) código 


* **mensagem**: mensagem de exceção


  
### <a name="rmsexception"></a>RMSException
[RMSException](class_mip_rmsexception.md) construtor.

Parâmetros:  
* **tipo**: tipo de exceção 


* **erro**: [erro](class_mip_error.md) código 


* **mensagem**: mensagem de exceção


  
### <a name="what"></a>O que
Obtém a mensagem de exceção.

  
**Devolve**: mensagem de exceção
  
### <a name="exceptiontypes"></a>ExceptionTypes
Obtém o tipo de exceção.

  
**Devolve**: tipo de exceção
  
### <a name="error"></a>Erro
Obtém o código de erro.

  
**Devolve**: [erro](class_mip_error.md) código