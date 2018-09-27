# <a name="class-mipconsentresult"></a>classe mip::ConsentResult 
Descreve o resultado do pedido de consentimento após a interação do utilizador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 ConsentResult pública (bool aceites, bool showAgain, Std:: String const e ID de utilizador)  |  [ConsentResult](class_mip_consentresult.md) construtor.
 bool pública Accepted() const  |  Obtém se ou não consentidas por utilizadores para a ação.
 bool pública ShowAgain() const  |  Obtém se ou não é necessário para futuros pedidos do consentimento explícito.
 público const Std:: String & UserId() const  |  Obtém de quem foi pedido o consentimento do utilizador (endereço de e-mail).
  
## <a name="members"></a>Membros
  
### <a name="consentresult"></a>ConsentResult
[ConsentResult](class_mip_consentresult.md) construtor.

Parâmetros:  
* **aceite**: se é ou não consentidas por utilizadores para uma ação 


* **showAgain**: se é ou não é necessário para pedidos de ação futuras o consentimento explícito 


* **ID de utilizador**: utilizador (endereço de e-mail) de quem o consentimento foi pedido


  
### <a name="accepted"></a>Aceite
Obtém se ou não consentidas por utilizadores para a ação.

  
**Devolve**: se deve ou não utilizador contented a ação
  
### <a name="showagain"></a>ShowAgain
Obtém se ou não é necessário para futuros pedidos do consentimento explícito.

  
**Devolve**: se é ou não consentimento explícito é necessário para as solicitações futuras se isso for VERDADEIRO, o SDK irá memorizar o resultado deste consentimento e não pedir a aplicação de cliente para consentimento no futuro.
  
### <a name="userid"></a>UserId
Obtém de quem foi pedido o consentimento do utilizador (endereço de e-mail).

  
**Devolve**: de quem foi pedido o consentimento do utilizador