# <a name="class-miphttprequest"></a>classe mip::HttpRequest 
Interface que descreve um pedido de http único.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público GetRequestType() de HttpRequestType const  |  Obter o tipo de pedido.
 público const Std:: String & GetUrl() const  |  Url do pedido GET.
 público const Std:: String & GetBody() const  |  Obtenha o corpo do pedido.
público std::map const < Std:: String, Std:: String, CaseInsensitiveComparator > & GetHeaders() const  |  Obtenha os cabeçalhos de pedido.
  
## <a name="members"></a>Membros
  
### <a name="httprequesttype"></a>HttpRequestType
Obter o tipo de pedido.

  
**Devolve**: tipo de pedido
  
### <a name="geturl"></a>GetUrl
Url do pedido GET.

  
**Devolve**: url do pedido
  
### <a name="getbody"></a>GetBody
Obtenha o corpo do pedido.

  
**Devolve**: corpo do pedido
  
### <a name="getheaders"></a>GetHeaders
Obtenha os cabeçalhos de pedido.

  
**Devolve**: cabeçalhos de pedido