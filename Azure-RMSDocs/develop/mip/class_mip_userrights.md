# <a name="class-mipuserrights"></a>classe mip::UserRights 
Representa um grupo de utilizadores e os direitos associados aos mesmos.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
inline pública UserRights (const UserList & utilizadores, const RightList & direitos)  |  [UserRights](#classmip_1_1_user_rights) construtor.
inline pública const UserList & Users() const  |  Obtém os utilizadores associados a um conjunto de direitos.
inline pública const RightList & Rights() const  |  Obtém os direitos associados um grupo de utilizadores.
  
## <a name="members"></a>Membros
  
### <a name="userrights"></a>UserRights
[UserRights](#classmip_1_1_user_rights) construtor.
  
#### <a name="parameters"></a>Parâmetros
* Grupo de utilizadores que partilham os mesmos direitos de utilizadores 
* direitos direitos partilhados por grupo de utilizadores
  
### <a name="userlist"></a>UserList
Obtém os utilizadores associados a um conjunto de direitos.
  
#### <a name="returns"></a>Devolve
Utilizadores associados a um conjunto de direitos
  
### <a name="rightlist"></a>RightList
Obtém os direitos associados um grupo de utilizadores.
  
#### <a name="returns"></a>Devolve
Direitos associados um grupo de utilizadores