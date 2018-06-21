# <a name="class-mipconsentresult"></a>classe mip::ConsentResult 
Descreve o resultado do pedido de consentimento após a interação do utilizador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 ConsentResult público (bool aceite, bool showAgain, const std::string & userId)  |  [ConsentResult](class_mip_consentresult.md) construtor.
 bool pública Accepted() const  |  Obtém ou não utilizador autorizado ação.
 bool pública ShowAgain() const  |  Obtém ou não consentimento explícito não é necessário para pedidos futuros.
 pública std::string const & UserId() const  |  Obtém o utilizador (endereço de correio eletrónico) de quem foi solicitado o consentimento.
  
## <a name="members"></a>Membros
  
### <a name="consentresult"></a>ConsentResult
[ConsentResult](class_mip_consentresult.md) construtor.

Parâmetros:  
* **aceite**: se o utilizador autorizado para a acção 


* **showAgain**: ou não é necessário para pedidos de ação futuras consentimento explícito 


* **userId**: de quem foi solicitado o consentimento do utilizador (endereço de correio eletrónico)


  
### <a name="accepted"></a>Aceite
Obtém ou não utilizador autorizado ação.

  
**Devolve**: se deve ou não contented utilizador para a acção
  
### <a name="showagain"></a>ShowAgain
Obtém ou não consentimento explícito não é necessário para pedidos futuros.

  
**Devolve**: ou não consentimento explícito é necessário para pedidos de futuro, se for VERDADEIRO, o SDK será Lembre-se o resultado deste consentimento e solicita a aplicação de cliente confirmação no futuro.
  
### <a name="userid"></a>UserId
Obtém o utilizador (endereço de correio eletrónico) de quem foi solicitado o consentimento.

  
**Devolve**: de quem foi solicitado o consentimento do utilizador