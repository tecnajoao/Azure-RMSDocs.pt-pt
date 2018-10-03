---
title: Conceitos - autenticação no SDK do MIP.
description: Este artigo ajuda-o a compreender como o SDK de MIP implementa a autenticação e os requisitos para aplicativos de cliente fornecer a lógica de aquisição do token de acesso de OAuth2.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 288342c467574cf84c60e1211238b65a9e716b6c
ms.sourcegitcommit: 860955fb2c292b3ca5910cd41095363f58caf553
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48230527"
---
# <a name="microsoft-information-protection-sdk---authentication-concepts"></a>SDK - conceitos de autenticação do Microsoft Information Protection

A autenticação no SDK do MIP é executada ao estender a classe `mip::AuthDelegate` para implementar o método de autenticação pretendido. `mip::AuthDelegate` contém:

- `mip::AuthDelegate::OAuth2Challenge` -uma classe que gere as informações da autoridade de OAuth2 e fornece para a aplicação cliente.
- `mip::AuthDelegate::OAuth2Token` -uma classe gerencia a aquisição de token de acesso de OAuth2 (da aplicação de cliente) e o armazenamento de token.
- `mip::AuthDelegate::AcquireOAuth2Token()` -uma função virtual pura, cuja implementação determina o método de aquisição de token de acesso. Depois de a ser chamado pelo SDK, adquire o token de acesso, em seguida, fornece-o novamente para a lógica de autenticação do SDK.

`mip::AuthDelegate::AcquireOAuth2Token` aceita os seguintes parâmetros e retorna um Booleano indicando se a aquisição do token foi concluída com êxito:

- `mip::Identity`: A identidade do utilizador ou serviço de autenticação, se conhecidos.
- `mip::AuthDelegate::OAuth2Challenge`: Aceita dois parâmetros, **autoridade** e **recurso**. **Autoridade** é o serviço será gerado contra o token. **Recurso** é o serviço que está a tentar aceder. O SDK processará passando estes parâmetros para o delegado quando chamado.
- `mip::AuthDelegate::OAuth2Token`: O resultado de token é escrito para este objeto. Serão consumida pelo SDK quando o motor é carregado. Fora da nossa implementação de autenticação, não deve ser necessário obter ou definir este valor em qualquer lugar.

**Importante:** os aplicativos não chamar `AcquireOAuth2Token` diretamente. O SDK irá chamar essa função, quando necessário.

## <a name="consent"></a>Consentimento

Azure AD requer um aplicativo a ser dado consentimento, antes de ela for concedida permissão para aceder a recursos protegidas/APIs sob a identidade de uma conta. Consentimento é registado como uma confirmação permanente de permissão no inquilino da conta, para a conta específica (consentimento do utilizador) ou todas as contas (consentimento de administrador). Consentimento ocorre em vários cenários, com base na API que está sendo acessado e as permissões que o aplicativo procura, e a conta utilizada para início de sessão: 

- contas a partir da *mesmo inquilino* onde a aplicação fica registada, se o utilizador ou um administrador não previamente consentir explicitamente acesso por meio do recurso de "Conceder permissões".
- contas a partir de um *inquilino diferente* se a aplicação fica registada como multi-inquilino e administrador de inquilinos não previamente dar o seu consentimento para todos os utilizadores com antecedência.

O `mip::Consent` enum classe implementa uma abordagem de fácil de usar que permite que os desenvolvedores de aplicativos para proporcionar uma experiência de consentimento personalizadas com base no ponto final que está sendo acessado pelo SDK. A notificação pode informar a um utilizador dos dados que serão recolhidos, como obter os dados removidos ou qualquer outra informação que é exigida por lei ou a conformidade de políticas. Assim que o utilizador concede consentimento, a aplicação pode continuar. 

### <a name="implementation"></a>Implementação

Consentimento é implementado por expandir os `mip::Consent` classe e a implementação base `GetUserConsent` para retornar um do `mip::Consent` valores de enumeração. 

O objeto derivado de `mip::Consent` é passado para o `mip::FileProfile::Settings` ou `mip::ProtectionProfile::Settings` construtor.

Quando um usuário executar uma operação que exigiria que fornece o consentimento, as chamadas SDK o `GetUserConsent` método, passando o URL de destino como o parâmetro. É nesse método onde um implementaria exibir as informações necessárias para o usuário, permitindo-lhes tomar uma decisão sobre se é ou não consentimento para utilizar o serviço. 

### <a name="consent-options"></a>Opções de consentimento

- **AcceptAlways**: consentimento e lembre-se a decisão.
- **Aceitar**: uma vez o consentimento.
- **Rejeitar**: não dar consentimento.

Quando o SDK pede consentimento do utilizador com este método, o aplicativo cliente deve apresentar o URL para o usuário. Aplicações de cliente devem fornecer alguns meios de obtenção de consentimento do utilizador e voltar a enumeração de consentimento apropriada que corresponde à decisão do usuário.

### <a name="sample-implementation"></a>Implementação de exemplo

#### <a name="consentdelegateimplh"></a>consent_delegate_impl.h

```cpp
class ConsentDelegateImpl final : public mip::ConsentDelegate {
public:
  ConsentDelegateImpl() = default;
  
  virtual mip::Consent GetUserConsent(const std::string& url) override;

};
```

#### <a name="consentdelegateimplcpp"></a>consent_delegate_impl.cpp

Quando o SDK necessita de consentimento, o `GetUserConsent` método é chamado *pelo SDK*, e o URL transmitido como um parâmetro. No exemplo abaixo, o utilizador é notificado de que o SDK irá ligar para que, desde o URL, em seguida, devolve `Consent::AcceptAlways`. Isso não é um ótimo exemplo de como o utilizador não foi apresentado com uma opção real.

```cpp
Consent ConsentDelegateImpl::GetUserConsent(const string& url) {
  //Print the consent URL, ask user to choose
  std::cout << "SDK will connect to: " << url << std::endl;

  std::cout << "1) Accept Always" << std::endl;
  std::cout << "2) Accept" << std::endl;
  std::cout << "3) Reject" << std::endl;
  std::cout << "Select an option: ";
  char input;
  std::cin >> input;

  switch (input)
  {
  case '1':
    return Consent::AcceptAlways;
    break;
  case '2':
    return Consent::Accept;
    break;
  case '3':
    return Consent::Reject;
    break;
  default:
    return Consent::Reject;
  }  
}
```

## <a name="next-steps"></a>Passos Seguintes

Para simplificar, exemplos que demonstram o delegado implementará a aquisição do token ao chamar um script externo. Este script pode ser substituído por qualquer outro tipo de script, uma biblioteca OAuth2 do código-fonte aberto ou uma biblioteca OAuth2 personalizada.

- [Adquirir um token de acesso com o PowerShell](concept-authentication-acquire-token-ps.md)
- [Adquirir um token de acesso com o Python](concept-authentication-acquire-token-py.md)
