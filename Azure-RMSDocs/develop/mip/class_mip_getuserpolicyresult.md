# <a name="class-mipgetuserpolicyresult"></a>classe mip::GetUserPolicyResult 
Descreve os resultados de um pedido de aquisição de política de utilizador.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública GetUserPolicyResultStatus GetResultStatus()  |  Obtém o estado do pedido de aquisição de política.
std::shared_ptr pública < std::string > GetReferrer()  |  Obtém o endereço de referência da política.
std::shared_ptr pública<UserPolicy> GetPolicy()  |  Obtém um [UserPolicy](#classmip_1_1_user_policy) instância.
  
## <a name="members"></a>Membros
  
### <a name="getuserpolicyresultstatus"></a>GetUserPolicyResultStatus
Obtém o estado do pedido de aquisição de política.
  
#### <a name="returns"></a>Devolve
Estado do pedido de aquisição de política
  
### <a name="getreferrer"></a>GetReferrer
Obtém o endereço de referência da política.
  
#### <a name="returns"></a>Devolve
Endereço de referência da política de referência é um URI que pode ser apresentado ao utilizador após a aquisição de política de falha que contém informações sobre a forma como esse utilizador pode ter permissão para aceder ao conteúdo.
  
### <a name="userpolicy"></a>UserPolicy
Obtém um [UserPolicy](#classmip_1_1_user_policy) instância.
  
#### <a name="returns"></a>Devolve
[UserPolicy](#classmip_1_1_user_policy) instância se aquisição foi bem sucedida, caso contrário `nullptr`.