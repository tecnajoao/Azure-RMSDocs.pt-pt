# <a name="class-miprmslogicexception"></a>classe mip::RMSLogicException 
Exceção de lógica de RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 RMSLogicException público (erro de ErrorTypes const, const std::string & te mensagem)  |  [RMSLogicException](class_mip_rmslogicexception.md) construtor.
 RMSLogicException público (erro de ErrorTypes const, const char * const & mensagem)  |  [RMSLogicException](class_mip_rmslogicexception.md) construtor.
 pública virtual const char * what() const  |  Obtém a mensagem de exceção.
 pública type() virtual ExceptionTypes const  |  Obtém o tipo de exceção.
 int virtual pública error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](class_mip_rmslogicexception.md) construtor.

Parâmetros:  
* **erro**: [erro](class_mip_error.md) código 


* **mensagem**: mensagem de exceção


  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](class_mip_rmslogicexception.md) construtor.

Parâmetros:  
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