# <a name="class-mipconsentcallback"></a>classe mip::ConsentCallback 
Interface para notificações de pedido de consentimento.
Esse retorno de chamada é implementado por uma aplicação de cliente para saber quando deve ser apresentada uma notificação de consentimento ao utilizador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público ConsentList Consents(ConsentList& consents)  |  Chamado quando o SDK necessita de consentimento do utilizador para uma operação.
  
## <a name="members"></a>Membros
  
### <a name="consentlist"></a>ConsentList
Chamado quando o SDK necessita de consentimento do utilizador para uma operação.

Parâmetros:  
* **autorizar**: A lista de autorizações pedido pelo SDK



  
**Devolve**: [consentimento](class_mip_consent.md) resultados quando consentimentos são solicitados pelo SDK, o aplicativo cliente deve obter consentimento do usuário, os resultados de cada consentimento devem ser armazenados por meio de [Consent::Result (const ConsentResult &)](class_mip_consent.md#result), e deve ser devolvida uma lista dos consentimentos resolvidos.