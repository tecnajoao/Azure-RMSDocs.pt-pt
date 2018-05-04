# <a name="class-miplabel"></a>classe mip::Label 
Abstração para uma etiqueta única da Microsoft Information Protection.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública std::string const & GetId() const  |  Obter a etiqueta ID.
pública std::string const & GetName() const  |  Obter o nome de etiqueta.
pública std::string const & GetDescription() const  |  Obter a descrição da etiqueta.
pública std::string const & GetColor() const  |  Obter a cor que da etiqueta deve ser apresentada.
pública std::string const & GetOrder() const  |  Obter a ordem da etiqueta.
pública std::string const & GetTooltip() const  |  Obter a descrição de descrição da etiqueta.
bool pública IsActive() const  |  Obtém um valor boleano sinalização se a etiqueta está ativa.
std::weak_ptr pública<Label> GetParent() const  |  Obter a etiqueta principal.
pública std::vector const < std::shared_ptr<Label>> & GetChildren() const  |  Obter os subordinados etiquetas da etiqueta do atual.
  
## <a name="members"></a>Membros
  
### <a name="getid"></a>GetId
Obter a etiqueta ID.
  
#### <a name="returns"></a>Devolve
o id da etiqueta.
  
### <a name="getname"></a>GetName
Obter o nome de etiqueta.
  
#### <a name="returns"></a>Devolve
o nome de etiqueta.
  
### <a name="getdescription"></a>GetDescription
Obter a descrição da etiqueta.
  
#### <a name="returns"></a>Devolve
a descrição da etiqueta.
  
### <a name="getcolor"></a>GetColor
Obter a cor que da etiqueta deve ser apresentada.
  
#### <a name="returns"></a>Devolve
o formato de cadeia de valor de cor. "#RRGGBB" em que cada um dos RR, GG, BB é um hexadecimal 0-f.
  
### <a name="getorder"></a>GetOrder
Obter a ordem da etiqueta.
  
#### <a name="returns"></a>Devolve
um valor numérico espacial atribuído como uma cadeia.
  
### <a name="gettooltip"></a>GetTooltip
Obter a descrição de descrição da etiqueta.
  
#### <a name="returns"></a>Devolve
uma cadeia de descrição.
  
### <a name="isactive"></a>Quando IsActive
Obtém um valor boleano sinalização se a etiqueta está ativa.
Etiquetas de Active Directory só podem ser aplicadas. Etiquetas Inativas não não possível aplicar e são utilizadas para efeitos de apresentação apenas. 
  
#### <a name="returns"></a>Devolve
VERDADEIRO se a etiqueta é o Active Directory, caso contrário FALSO.
  
### <a name="label"></a>Etiqueta
Obter a etiqueta principal.
  
#### <a name="returns"></a>Devolve
etiqueta de um ponteiro fraco para o elemento principal se senão existe um ponteiro vazio.
  
### <a name="label"></a>Etiqueta
Obter os subordinados etiquetas da etiqueta do atual.
  
#### <a name="returns"></a>Devolve
um vetor de apontadores partilhados para etiquetas.