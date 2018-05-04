# <a name="class-miprmsofficefileexception"></a>classe mip::RMSOfficeFileException 
Exceção de ficheiro do Office para RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública RMSOfficeFileException (const std::string & mensagem, razão razão)  |  [RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) construtor.
inline pública RMSOfficeFileException (const char * const & mensagem, razão razão)  |  [RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) construtor.
inline pública virtual razão reason() const  |  Obtém a classificação de falha de ficheiros do Office.
inline pública virtual const char * what() const  |  Obtém a mensagem de exceção.
inline pública virtual ExceptionTypes type() const  |  Obtém o tipo de exceção.
inline pública virtual int error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* mensagem de exceção de mensagem 
* motivo classificação de falha de ficheiros do Office
  
### <a name="rmsofficefileexception"></a>RMSOfficeFileException
[RMSOfficeFileException](#classmip_1_1_r_m_s_office_file_exception) construtor.
  
#### <a name="parameters"></a>Parâmetros
* mensagem de exceção de mensagem 
* motivo classificação de falha de ficheiros do Office
  
### <a name="reason"></a>Razão
Obtém a classificação de falha de ficheiros do Office.
  
#### <a name="returns"></a>Devolve
Classificação de falha de ficheiros do Office
  
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