# <a name="class-miphttpresponse"></a>classe mip::HttpResponse 
Interface que descreve uma resposta de http única, implementada pela aplicação de cliente, ao substituir [HttpDelegate](class_mip_httpdelegate.md).
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público int32_t GetStatusCode() const  |  Obter o código de estado de resposta.
 público const Std:: String & GetBody() const  |  Obtenha o corpo do pedido.
público std::map const < Std:: String, Std:: String, CaseInsensitiveComparator > & GetHeaders() const  |  Obtenha os cabeçalhos de pedido.
  
## <a name="members"></a>Membros
  
### <a name="getstatuscode"></a>GetStatusCode
Obter o código de estado de resposta.

  
**Devolve**: código de estado
  
### <a name="getbody"></a>GetBody
Obtenha o corpo do pedido.

  
**Devolve**: corpo do pedido
  
### <a name="getheaders"></a>GetHeaders
Obtenha os cabeçalhos de pedido.

  
**Devolve**: cabeçalhos de pedido