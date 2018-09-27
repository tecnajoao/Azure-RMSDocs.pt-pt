# <a name="class-miphttpdelegate"></a>classe mip::HttpDelegate 
Interface para substituir o tratamento de http.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
público std::shared_ptr<HttpResponse> enviar (const std::shared_ptr<HttpRequest>& pedido, const std::shared_ptr<void>& contexto)  |  Envie pedido de http.
  
## <a name="members"></a>Membros
  
### <a name="httpresponse"></a>HttpResponse
Envie pedido de http.

Parâmetros:  
* **pedido**: pedido de Http 


* **contexto**: O mesmo contexto de cliente opaco, que foi passado para a API que resultaram neste pedido de http



  
**Devolve**: resposta de Http