# <a name="class-miprmslogicexception"></a>classe mip::RMSLogicException 
Exceção de lógica de RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública RMSLogicException (erro de ErrorTypes const, const std::string & te mensagem)  |  [RMSLogicException](#classmip_1_1_r_m_s_logic_exception) construtor.
inline pública RMSLogicException (erro de ErrorTypes const, const char * const & mensagem)  |  [RMSLogicException](#classmip_1_1_r_m_s_logic_exception) construtor.
inline pública virtual const char * what() const  |  Obtém a mensagem de exceção.
inline pública virtual ExceptionTypes type() const  |  Obtém o tipo de exceção.
inline pública virtual int error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](#classmip_1_1_r_m_s_logic_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* erro [erro](#classmip_1_1_error) código 
* mensagem de exceção de mensagem
  
### <a name="rmslogicexception"></a>RMSLogicException
[RMSLogicException](#classmip_1_1_r_m_s_logic_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
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