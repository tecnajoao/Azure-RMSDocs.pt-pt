# <a name="class-mipconsent"></a>classe mip::Consent 
Representa aceitação/refusal um utilizador para permitir uma ação.
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 pública mip::ConsentResult const & Result() const  |  Obtém o resultado de um pedido de consentimento.
 void pública resultar (const ConsentResult & valor)  |  Define o resultado de um pedido de consentimento.
 mip::ConsentType pública Type() const  |  Obtém o tipo de consentimento.
std::vector const pública < std::string > Urls() const  |  Obtém os URLs envolvidos no pedido de consentimento.
 std::string const pública User() const  |  Obtém o utilizador (endereço de correio eletrónico) de quem é solicitado o consentimento.
 std::string const pública Domain() const  |  Obtém o domínio associado ao utilizador de quem é solicitado o consentimento.
  
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

  
**Devolve**: envolvidos no pedido de consentimento de URLs
  
### <a name="user"></a>Função do
Obtém o utilizador (endereço de correio eletrónico) de quem é solicitado o consentimento.

  
**Devolve**: de quem é solicitado o consentimento do utilizador
  
### <a name="domain"></a>Domínio
Obtém o domínio associado ao utilizador de quem é solicitado o consentimento.

  
**Devolve**: domínio associados com o utilizador de quem é solicitado o consentimento