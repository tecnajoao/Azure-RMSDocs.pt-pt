# <a name="class-mipgetuserpolicyresult"></a>classe mip::GetUserPolicyResult 
Descreve os resultados de um pedido de obtenção de política de utilizador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público GetUserPolicyResultStatus GetResultStatus()  |  Obtém o estado do pedido de obtenção de política.
público std::shared_ptr Std:: < String > GetReferrer()  |  Obtém o endereço de refererrer da política.
público std::shared_ptr<UserPolicy> GetPolicy()  |  Obtém uma [UserPolicy](class_mip_userpolicy.md) instância.
  
## <a name="members"></a>Membros
  
### <a name="getuserpolicyresultstatus"></a>GetUserPolicyResultStatus
Obtém o estado do pedido de obtenção de política.

  
**Devolve**: Estado do pedido de obtenção de política
  
### <a name="getreferrer"></a>GetReferrer
Obtém o endereço de refererrer da política.

  
**Devolve**: Referrerer endereço da política do referenciador é um URI que pode ser apresentado ao utilizador após a aquisição de política com falha que contém informações sobre como esse utilizador pode obter a permissão para aceder ao conteúdo.
  
### <a name="userpolicy"></a>UserPolicy
Obtém uma [UserPolicy](class_mip_userpolicy.md) instância.

  
**Devolve**: [UserPolicy](class_mip_userpolicy.md) instância se aquisição foi concluída com êxito, nullptr outra