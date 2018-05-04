# <a name="class-miprmspfileexception"></a>classe mip::RMSPFileException 
Exceção de RMS PFile.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública RMSPFileException (const std::string & mensagem, razão razão)  |  [RMSPFileException](#classmip_1_1_r_m_s_p_file_exception) construtor.
inline pública RMSPFileException (const char * const & mensagem, razão razão)  |  [RMSPFileException](#classmip_1_1_r_m_s_p_file_exception) construtor.
inline pública virtual razão reason() const  |  Obtém a classificação de erro PFile.
inline pública virtual const char * what() const  |  Obtém a mensagem de exceção.
inline pública virtual ExceptionTypes type() const  |  Obtém o tipo de exceção.
inline pública virtual int error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](#classmip_1_1_r_m_s_p_file_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* mensagem de exceção de mensagem 
* motivo PFile classificação de erro
  
### <a name="rmspfileexception"></a>RMSPFileException
[RMSPFileException](#classmip_1_1_r_m_s_p_file_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* mensagem de exceção de mensagem 
* motivo PFile classificação de erro
  
### <a name="reason"></a>Razão
Obtém a classificação de erro PFile.
  
#### <a name="returns"></a>Devolve
Classificação de erro PFile
  
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