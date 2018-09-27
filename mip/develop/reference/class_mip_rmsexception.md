# <a name="class-miprmsexception"></a>classe mip::RMSException 
Exceção de base do RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 RMSException pública (tipo de ExceptionTypes const, const int erro, const Std:: String e mensagem)  |  [RMSException](class_mip_rmsexception.md) construtor.
 RMSException pública (const ExceptionTypes erro do tipo, const int, const char * const & mensagem)  |  [RMSException](class_mip_rmsexception.md) construtor.
 público virtual const char * what() const  |  Obtém a mensagem de exceção.
 público type() virtual ExceptionTypes const  |  Obtém o tipo de exceção.
 público int virtual error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmsexception"></a>RMSException
[RMSException](class_mip_rmsexception.md) construtor.

Parâmetros:  
* **tipo de**: tipo de exceção 


* **erro**: [erro](class_mip_error.md) código 


* **mensagem**: mensagem de exceção


  
### <a name="rmsexception"></a>RMSException
[RMSException](class_mip_rmsexception.md) construtor.

Parâmetros:  
* **tipo de**: tipo de exceção 


* **erro**: [erro](class_mip_error.md) código 


* **mensagem**: mensagem de exceção


  
### <a name="what"></a>o que
Obtém a mensagem de exceção.

  
**Devolve**: mensagem de exceção
  
### <a name="exceptiontypes"></a>ExceptionTypes
Obtém o tipo de exceção.

  
**Devolve**: tipo de exceção
  
### <a name="error"></a>erro
Obtém o código de erro.

  
**Devolve**: [erro](class_mip_error.md) código