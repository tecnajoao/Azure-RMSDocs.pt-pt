# <a name="class-miprmsstreamexception"></a>classe mip::RMSStreamException 
Exceção de fluxo do RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública RMSStreamException (const std::string & te mensagem)  |  [RMSStreamException](#classmip_1_1_r_m_s_stream_exception) construtor.
inline pública RMSStreamException (const char * const & mensagem)  |  [RMSStreamException](#classmip_1_1_r_m_s_stream_exception) construtor.
inline pública virtual const char * what() const  |  Obtém a mensagem de exceção.
inline pública virtual ExceptionTypes type() const  |  Obtém o tipo de exceção.
inline pública virtual int error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](#classmip_1_1_r_m_s_stream_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* mensagem de exceção de mensagem
  
### <a name="rmsstreamexception"></a>RMSStreamException
[RMSStreamException](#classmip_1_1_r_m_s_stream_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* mensagem de exceção de mensagem
  
### <a name="what"></a>O que
Obtém a mensagem de exceção.
  
#### <a name="returns"></a>Devolve
Mensagem de exceção
  
### <a name="exceptiontypes"></a>ExceptionTypes
Obtém o tipo de exceção.
  
#### <a name="returns"></a>Devolve
Tipo de exceção
  
### <a name="error"></a>Erro
Obtém o código de erro.
  
#### <a name="returns"></a>Devolve
[Erro](#classmip_1_1_error) código