# <a name="class-mipjustificationrequirederror"></a>classe mip::JustificationRequiredError 
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública JustificationRequiredError | 
inline pública virtual std::shared_ptr < erro > Clone | Clone o erro.
inline pública char const * que | Receber uma mensagem de erro cstring.
inline pública virtual ErrorType GetErrorType | Obter o tipo de erro.
inline público de std::string const virtual & GetErrorName | Obter o nome de erro.
inline público de std::string const virtual & GetMessage | Obter a mensagem de erro.
pública inline virtual void SetMessage | Defina a mensagem de erro.
## <a name="members"></a>Membros
### <a name="justificationrequirederror"></a>JustificationRequiredError
### <a name="error"></a>Error
Clone o erro.
#### <a name="returns"></a>Devolve
um clone do erro.
### <a name="what"></a>O que
Receber uma mensagem de erro cstring.
#### <a name="returns"></a>Devolve
um cstring err mensagem
### <a name="errortype"></a>ErrorType
Obter o tipo de erro.
#### <a name="returns"></a>Devolve
o tipo de erro.
### <a name="geterrorname"></a>GetErrorName
Obter o nome de erro.
#### <a name="returns"></a>Devolve
o nome de erro.
### <a name="getmessage"></a>GetMessage
Obter a mensagem de erro.
#### <a name="returns"></a>Devolve
a mensagem de erro.
### <a name="setmessage"></a>SetMessage
Defina a mensagem de erro.
#### <a name="parameters"></a>Parâmetros
* a mensagem de erro tarifas de mensagens.