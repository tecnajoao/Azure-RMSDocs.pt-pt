# <a name="class-mipconsentresult"></a>classe mip::ConsentResult 
Descreve o resultado do pedido de consentimento após a interação do utilizador.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública ConsentResult inline pública bool aceites | Obtém ou não utilizador autorizado ação.
inline pública bool ShowAgain | Obtém ou não consentimento explícito não é necessário para pedidos futuros.
std::string const inline pública & UserId | Obtém o utilizador (endereço de correio eletrónico) de quem foi solicitado o consentimento.
## <a name="members"></a>Membros
### <a name="consentresult"></a>ConsentResult
[ConsentResult](#classmip_1_1_consent_result) construtor.
#### <a name="parameters"></a>Parâmetros
* aceite ou não autorizado de utilizador para a acção 
* showAgain ou não é necessário para pedidos de ação futuras consentimento explícito 
* ID de utilizador de quem foi solicitado o consentimento do utilizador (endereço de correio eletrónico)
### <a name="accepted"></a>Aceite
Obtém ou não utilizador autorizado ação.
#### <a name="returns"></a>Devolve
Se deve ou não contented utilizador para a acção
### <a name="showagain"></a>ShowAgain
Obtém ou não consentimento explícito não é necessário para pedidos futuros.
#### <a name="returns"></a>Devolve
Se pretende ou não consentimento explícito não é necessário para pedidos futuros se for VERDADEIRO, o SDK será Lembre-se o resultado deste consentimento e solicita a aplicação de cliente confirmação no futuro.
### <a name="userid"></a>UserId
Obtém o utilizador (endereço de correio eletrónico) de quem foi solicitado o consentimento.
#### <a name="returns"></a>Devolve
Foi pedido ao utilizador a partir do qual consentimento