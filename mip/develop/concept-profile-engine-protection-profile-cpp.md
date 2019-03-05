---
title: Conceitos - o objeto de perfil de API de proteção
description: Este artigo ajuda-o a compreender os conceitos em todo o objeto de perfil de proteção, o que é criada durante a inicialização do aplicativo.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: c8e2785f68ea76c34384dccb079260b6c3ed45cb
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57329901"
---
# <a name="microsoft-information-protection-sdk---protection-api-profile-concepts"></a>SDK - conceitos de perfil de API de proteção do Microsoft Information Protection

Os dois exemplos abaixo mostram como criar o objeto de profileSettings utiliza o armazenamento local para o armazenamento de estado, assim como na memória apenas. Ambos partem do princípio de que o `authDelegateImpl` objeto já foi criado.

## <a name="load-a-profile"></a>Um perfil de carga

Agora que o `ProtectionProfileObserverImpl` e `AuthDelegateImpl` são definidas, vamos utilizar o-los para criar uma instância `mip::ProtectionProfile`. Criar a `mip::ProtectionProfile` objeto requer [ `mip::ProtectionProfile::Settings` ](reference/class_mip_ProtectionProfile_settings.md).

### <a name="protectionprofilesettings-parameters"></a>Parâmetros de ProtectionProfile::Settings

- `std::string path`: Caminho de ficheiro em que o registo, telemetria e outras estado persistente é armazenado.
- `bool useInMemoryStorage`: Define se é ou não a todos os Estados devem ser armazenados na memória, em vez de no disco.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: Um ponteiro compartilhado da classe `mip::AuthDelegate`.
- `std::shared_ptr<mip::ProtectionProfile::Observer> observer`: Um ponteiro compartilhado para o `ProtectionProfile::Observer` implementação.
- `mip::ApplicationInfo applicationInfo`: objeto. Utilizado para definir as informações sobre a aplicação que está a consumir o SDK.

Os dois exemplos abaixo mostram como criar o objeto de profileSettings utiliza o armazenamento local para o armazenamento de estado, assim como na memória apenas. Ambos partem do princípio de que o `authDelegateImpl` objeto já foi criado.

#### <a name="store-state-in-memory-only"></a>Estado de Store na memória apenas

```cpp
ProtectionProfile::Settings profileSettings(
    "",                                     //path to store settings
    true,                                   //useInMemoryStorage
    authDelegateImpl,                       //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),//new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Definições de perfil de leitura/escrita do caminho de armazenamento no disco

```cpp
ProtectionProfile::Settings profileSettings(
    "./mip_app_data",                       //path to store settings
    false,                                  //useInMemoryStorage
    authDelegateImpl,                       //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),//new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>(), //new protection profile
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

Em seguida, utilizar o padrão de promessa/futuro para carregar o `ProtectionProfile`.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<ProtectionProfile>>>();
auto profileFuture = profilePromise->get_future();
ProtectionProfile::LoadAsync(profileSettings, profilePromise);
```

Se o carregou um perfil, e a operação foi concluída com êxito, `ProtectionProfileObserverImpl::OnLoadSuccess`, nossa implementação de `mip::ProtectionProfile::Observer::OnLoadSuccess` é chamado. O objeto resultante ou ponteiro de exceção, bem como o contexto, é passado como parâmetros para a função. O contexto é um ponteiro para o `std::promise` que criámos para processar a operação assíncrona. A função simplesmente define o valor da promessa para o objeto de ProtectionProfile (contexto). Quando utiliza a função principal `Future.get()`, o resultado pode ser armazenado num novo objeto.

```cpp
//get the future value and store in profile.
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>Juntando as peças

Totalmente ter implementado o delegado de autenticação e observadores, agora é possível carregar totalmente um perfil. O recorte de código abaixo pressupõe que já estão incluídos todos os cabeçalhos necessários.

```cpp
int main()
{
    const string userName = "MyTestUser@contoso.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";
    auto authDelegateImpl = make_shared<sample::auth::AuthDelegateImpl>(userName, password, clientId);

    ProtectionProfile::Settings profileSettings("",
        false,
        authDelegateImpl,
        std::make_shared<ConsentDelegateImpl>(),
        std::make_shared<ProfileObserver>(),
        mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<ProtectionProfile>>>();
    auto profileFuture = profilePromise->get_future();
    ProtectionProfile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Resultar de final é que podemos carreguei o perfil com êxito e armazenadas no objeto chamado `profile`.

## <a name="next-steps"></a>Próximos Passos

Agora que o perfil foi adicionado, a próxima etapa é adicionar um mecanismo para o perfil.

[Conceitos de motor de proteção](concept-profile-engine-protection-engine-cpp.md)
