# <a name="class-mipconsent"></a>classe mip::Consent 
Representa aceitação/refusal um utilizador para permitir uma ação.
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
pública mip::ConsentResult const & resultado | Obtém o resultado de um pedido de consentimento.
pública ResultConsentResult void & valor) | Define o resultado de um pedido de consentimento.
Tipo de mip::ConsentType público | Obtém o tipo de consentimento.
std::vector const pública < std::string > Urls | Obtém os URLs envolvidos no pedido de consentimento.
std::string const pública utilizador | Obtém o utilizador (endereço de correio eletrónico) de quem é solicitado o consentimento.
std::string const pública domínio | Obtém o domínio associado ao utilizador de quem é solicitado o consentimento.
## <a name="members"></a>Membros
### <a name="mipconsentresult"></a>Mip::ConsentResult
Obtém o resultado de um pedido de consentimento.
#### <a name="returns"></a>Devolve
Resultado do pedido de consentimento
### <a name="result"></a>Resultado
Define o resultado de um pedido de consentimento.
#### <a name="parameters"></a>Parâmetros
* Resultado do pedido de consentimento de valor
### <a name="mipconsenttype"></a>Mip::ConsentType
Obtém o tipo de consentimento.
#### <a name="returns"></a>Devolve
Tipo de consentimento
### <a name="urls"></a>URLs
Obtém os URLs envolvidos no pedido de consentimento.
#### <a name="returns"></a>Devolve
URLs envolvidos no pedido de consentimento
### <a name="user"></a>Função do
Obtém o utilizador (endereço de correio eletrónico) de quem é solicitado o consentimento.
#### <a name="returns"></a>Devolve
De quem é solicitado o consentimento do utilizador
### <a name="domain"></a>Domínio
Obtém o domínio associado ao utilizador de quem é solicitado o consentimento.
#### <a name="returns"></a>Devolve
Domínio associado ao utilizador a partir do qual consentimento for solicitado