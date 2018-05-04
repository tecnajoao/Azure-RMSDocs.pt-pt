# <a name="class-mipconsentcallback"></a>classe mip::ConsentCallback 
Interface de notificações de pedido de consentimento.
Esta chamada de retorno é implementada por uma aplicação de cliente para saber quando deve ser apresentada uma notificação de consentimento ao utilizador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública ConsentList Consents(ConsentList& consents)  |  Chamado quando o SDK requer consentimento do utilizador para uma operação.
  
## <a name="members"></a>Membros
  
### <a name="consentlist"></a>ConsentList
Chamado quando o SDK requer consentimento do utilizador para uma operação.
  
#### <a name="parameters"></a>Parâmetros
* permitir a lista de consents pedida pelo SDK
  
#### <a name="returns"></a>Devolve
[Consentimento](#classmip_1_1_consent) resultados quando são solicitados consents pelo SDK, a aplicação cliente deve obter consentimento do utilizador, os resultados de cada consentimento devem ser armazenados através de [Consent::Result(const ConsentResult&)](#classmip_1_1_consent_1ad6c17d9af548a40b2fe854fe0d9bca64)e um lista dos consents resolver deve ser devolvida.