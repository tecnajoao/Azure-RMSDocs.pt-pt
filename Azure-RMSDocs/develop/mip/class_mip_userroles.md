# <a name="class-mipuserroles"></a>classe mip::UserRoles 
Representa um grupo de utilizadores e as funções associadas.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 pública MIP_EXPORT UserRoles(const UserList& users, const RoleList& roles)  |  [Funções de utilizador](class_mip_userroles.md) construtor.
 pública UserList const & Users() const  |  Obtém os utilizadores associados a um conjunto de funções.
 pública RoleList const & Roles() const  |  Obtém as funções associadas um grupo de utilizadores.
  
## <a name="members"></a>Membros
  
### <a name="userroles"></a>Funções de utilizador
[Funções de utilizador](class_mip_userroles.md) construtor.

Parâmetros:  
* **os utilizadores**: grupo de utilizadores que partilham as mesmas funções 


* **funções**: [funções](class_mip_roles.md) partilhado por grupo de utilizadores


  
### <a name="userlist"></a>UserList
Obtém os utilizadores associados a um conjunto de funções.

  
**Devolve**: os utilizadores associados a um conjunto de funções
  
### <a name="rolelist"></a>RoleList
Obtém as funções associadas um grupo de utilizadores.

  
**Devolve**: [funções](class_mip_roles.md) associado um grupo de utilizadores