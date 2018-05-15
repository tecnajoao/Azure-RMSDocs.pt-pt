# <a name="class-miprmsstreamexception"></a>classe mip::RMSStreamException 
Exceção de fluxo do RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 RMSStreamException público (const std::string & te mensagem)  |  [RMSStreamException](class_mip_rmsstream_exception.md) construtor.
 RMSStreamException público (const char * const & mensagem)  |  [RMSStreamException](class_mip_rmsstream_exception.md) construtor.
 pública virtual const char * what() const  |  Obtém a mensagem de exceção.
 pública type() virtual ExceptionTypes const  |  Obtém o tipo de exceção.
 int virtual pública error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstream_exception.md) construtor.

Parâmetros:  
* **mensagem**: mensagem de exceção


  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](class_mip_rmsstream_exception.md) construtor.

Parâmetros:  
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