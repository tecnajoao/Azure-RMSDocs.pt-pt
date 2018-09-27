# <a name="class-consentdelegate"></a>classe ConsentDelegate 
Delegado, consentimento operações relacionadas com.
Este delegado é implementado por uma aplicação de cliente para saber quando uma notificação de pedido de consentimento deverá ser apresentada ao utilizador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público GetUserConsent(const std::string& url) consentimento  |  Chamado quando o SDK necessita de consentimento do utilizador para ligar a um ponto de extremidade de serviço.
  
## <a name="members"></a>Membros
  
### <a name="consent"></a>Consentimento
Chamado quando o SDK necessita de consentimento do utilizador para ligar a um ponto de extremidade de serviço.

Parâmetros:  
* **URL**: O URL para o qual o SDK necessita de consentimento do utilizador



  
**Devolve**: consentimento de uma enumeração com a decisão do usuário.
Quando o SDK pede consentimento do utilizador com este método, o aplicativo cliente deve apresentar o URL para o usuário. Aplicações de cliente devem fornecer alguns meios de obtenção de consentimento do utilizador e voltar a enumeração de consentimento apropriada que corresponde à decisão do usuário.