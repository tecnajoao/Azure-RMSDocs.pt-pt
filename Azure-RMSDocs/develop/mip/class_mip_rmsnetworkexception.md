# <a name="class-miprmsnetworkexception"></a>classe mip::RMSNetworkException 
Exceção de rede do RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública RMSNetworkException (const std::string & mensagem, razão razão)  |  [RMSNetworkException](#classmip_1_1_r_m_s_network_exception) construtor.
inline pública RMSNetworkException (const char * const & mensagem, razão razão)  |  [RMSNetworkException](#classmip_1_1_r_m_s_network_exception) construtor.
inline pública virtual razão reason() const  |  Obtém a classificação de falha de rede.
inline pública virtual const char * what() const  |  Obtém a mensagem de exceção.
inline pública virtual ExceptionTypes type() const  |  Obtém o tipo de exceção.
inline pública virtual int error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](#classmip_1_1_r_m_s_network_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* mensagem de exceção de mensagem 
* motivo classificação de falha de rede
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](#classmip_1_1_r_m_s_network_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* mensagem de exceção de mensagem 
* motivo classificação de falha de rede
  
### <a name="reason"></a>Razão
Obtém a classificação de falha de rede.
  
#### <a name="returns"></a>Devolve
Classificação de falha de rede
  
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