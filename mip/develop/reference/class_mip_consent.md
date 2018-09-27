# <a name="class-mipconsent"></a>classe mip::Consent 
Representa aceitação/recusa um utilizador, para permitir que uma ação.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 público mip::ConsentResult const & Result() const  |  Obtém o resultado de um pedido de consentimento.
 void pública resultar (const ConsentResult & valor)  |  Define o resultado de um pedido de consentimento.
 público mip::ConsentType Type() const  |  Obtém o tipo de consentimento.
público const Std:: vector Std:: < String > Urls() const  |  Obtém os URLs envolvidos no pedido de consentimento.
 público const Std:: String User() const  |  Obtém o utilizador (endereço de e-mail) de quem é solicitado consentimento.
 público const Std:: String Domain() const  |  Obtém o domínio associado de quem é solicitado consentimento pelo usuário.
  
## <a name="members"></a>Membros
  
### <a name="mipconsentresult"></a>Mip::ConsentResult
Obtém o resultado de um pedido de consentimento.

  
**Devolve**: resultado do pedido de consentimento
  
### <a name="result"></a>Resultado
Define o resultado de um pedido de consentimento.

Parâmetros:  
* **valor**: resultado do pedido de consentimento


  
### <a name="mipconsenttype"></a>Mip::ConsentType
Obtém o tipo de consentimento.

  
**Devolve**: tipo de consentimento
  
### <a name="urls"></a>URLs
Obtém os URLs envolvidos no pedido de consentimento.

  
**Devolve**: URLs envolvidos no pedido de consentimento
  
### <a name="user"></a>Função do
Obtém o utilizador (endereço de e-mail) de quem é solicitado consentimento.

  
**Devolve**: de quem é solicitado o consentimento do utilizador
  
### <a name="domain"></a>Domínio
Obtém o domínio associado de quem é solicitado consentimento pelo usuário.

  
**Devolve**: domínio associado com o utilizador de quem é solicitado consentimento