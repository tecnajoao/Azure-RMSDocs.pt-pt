# <a name="class-miprmsexception"></a>classe mip::RMSException 
Exceção de base do RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública RMSException (const ExceptionTypes tipo, erro de int const, const std::string & mensagem)  |  [RMSException](#classmip_1_1_r_m_s_exception) construtor.
inline pública RMSException (tipo de const ExceptionTypes, erro de int const, const char * const & mensagem)  |  [RMSException](#classmip_1_1_r_m_s_exception) construtor.
inline pública virtual const char * what() const  |  Obtém a mensagem de exceção.
inline pública virtual ExceptionTypes type() const  |  Obtém o tipo de exceção.
inline pública virtual int error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmsexception"></a>RMSException
[RMSException](#classmip_1_1_r_m_s_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* tipo de exceção 
* erro [erro](#classmip_1_1_error) código 
* mensagem de exceção de mensagem
  
### <a name="rmsexception"></a>RMSException
[RMSException](#classmip_1_1_r_m_s_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* tipo de exceção 
* erro [erro](#classmip_1_1_error) código 
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