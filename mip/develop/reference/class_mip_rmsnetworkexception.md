# <a name="class-miprmsnetworkexception"></a>classe mip::RMSNetworkException 
Exceção de rede do RMS.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 RMSNetworkException pública (Std:: String const & mensagem, o motivo de motivo)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md) construtor.
 RMSNetworkException pública (const char * const & da mensagem, o motivo de motivo)  |  [RMSNetworkException](class_mip_rmsnetworkexception.md) construtor.
 público reason() virtual motivo const  |  Obtém a classificação de falha de rede.
 público virtual const char * what() const  |  Obtém a mensagem de exceção.
 público type() virtual ExceptionTypes const  |  Obtém o tipo de exceção.
 público int virtual error() const  |  Obtém o código de erro.
  
## <a name="members"></a>Membros
  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md) construtor.

Parâmetros:  
* **mensagem**: mensagem de exceção 


* **motivo**: classificação de falha de rede


  
### <a name="rmsnetworkexception"></a>RMSNetworkException
[RMSNetworkException](class_mip_rmsnetworkexception.md) construtor.

Parâmetros:  
* **mensagem**: mensagem de exceção 


* **motivo**: classificação de falha de rede


  
### <a name="reason"></a>Razão
Obtém a classificação de falha de rede.

  
**Devolve**: classificação de falha de rede
  
### <a name="what"></a>o que
Obtém a mensagem de exceção.

  
**Devolve**: mensagem de exceção
  
### <a name="exceptiontypes"></a>ExceptionTypes
Obtém o tipo de exceção.

  
**Devolve**: tipo de exceção
  
### <a name="error"></a>erro
Obtém o código de erro.

  
**Devolve**: [erro](class_mip_error.md) código