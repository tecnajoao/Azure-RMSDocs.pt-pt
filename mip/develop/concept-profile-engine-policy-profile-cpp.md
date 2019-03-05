---
title: Conceitos - o objeto de perfil de API de política
description: Este artigo ajuda-o a compreender os conceitos em todo o objeto de perfil de política, o que é criada durante a inicialização do aplicativo.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: f9bb02dd4508b5e09761b3684a2a4e6d92224b6a
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333046"
---
# <a name="microsoft-information-protection-sdk---policy-api-profile-concepts"></a>SDK - conceitos de perfil de política de API do Microsoft Information Protection

O `mip::Profile` têm de ser carregados antes de quaisquer operações de API de política podem ser executadas.

Os dois exemplos abaixo mostram como criar o objeto de profileSettings utiliza o armazenamento local para o armazenamento de estado, assim como na memória apenas. Ambos partem do princípio de que o `authDelegateImpl` objeto já foi criado.

## <a name="load-a-profile"></a>Um perfil de carga

Agora que o `ProfileObserver` e `AuthDelegateImpl` são definidas, vamos utilizar o-los para criar uma instância `mip::PolicyProfile`. Criar a `mip::PolicyProfile` objeto requer [ `mip::PolicyProfile::Settings` ](reference/class_mip_PolicyProfile_settings.md).

### <a name="profilesettings-parameters"></a>Parâmetros de Profile::Settings

- `std::string path`: Caminho de ficheiro em que o registo, telemetria e outras estado persistente é armazenado.
- `bool useInMemoryStorage`: Define se é ou não a todos os Estados devem ser armazenados na memória, em vez de no disco.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: Um ponteiro compartilhado da classe `mip::AuthDelegate` 
- `std::shared_ptr<mip::PolicyProfile::Observer> observer`: Um ponteiro compartilhado para o `PolicyProfile::Observer` implementação.
- `mip::ApplicationInfo applicationInfo`: objeto. Utilizado para definir as informações sobre a aplicação que está a consumir o SDK.

Os dois exemplos abaixo mostram como criar o objeto de profileSettings utiliza o armazenamento local para o armazenamento de estado, assim como na memória apenas. Ambos partem do princípio de que o `authDelegateImpl` objeto já foi criado.

#### <a name="store-state-in-memory-only"></a>Estado de Store na memória apenas

```cpp
Profile::Settings profileSettings("",
    true,
    authDelegateImpl,
    std::make_shared<ProfileObserver>(),
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Definições de perfil de leitura/escrita do caminho de armazenamento no disco

```cpp
Profile::Settings profileSettings("./mip_app_data",
    false,
    authDelegateImpl,
    std::make_shared<ProfileObserver>(),
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });
```

Em seguida, utilizar o padrão de promessa/futuro para carregar o `Profile`.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<Profile>>>();
auto profileFuture = profilePromise->get_future();
Profile::LoadAsync(profileSettings, profilePromise);
```

Se um perfil é carregado com êxito, `ProfileObserver::OnLoadSuccess`, nossa implementação de `mip::Profile::Observer::OnLoadSuccess` é notificado. O objeto resultante, neste caso um `mip::Profile`, bem como o contexto, são passados como parâmetros para a função de observador.

O *contexto* é um ponteiro para o `std::promise` que criámos para processar a operação assíncrona. A função simplesmente define o valor da promessa para o objeto de perfil que foi passado para o primeiro parâmetro. Quando utiliza a função principal `Future.get()`, o resultado pode ser armazenado num novo objeto no thread de chamada.

```cpp
//get the future value and store in profile. 
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>Juntando as peças

Totalmente ter implementado o delegado de autenticação e observadores, agora é possível carregar totalmente um perfil. O recorte de código abaixo pressupõe que já estão incluídos todos os cabeçalhos necessários.

```cpp
int main()
{
    const string userName = "MyTestUser@consoto.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";
    auto authDelegateImpl = make_shared<sample::auth::AuthDelegateImpl>(userName, password, clientId);

    Profile::Settings profileSettings("", false, authDelegateImpl, std::make_shared<ProfileObserver>(), mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<Profile>>>();
    auto profileFuture = profilePromise->get_future();
    Profile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Resultar de final é que podemos carreguei o perfil com êxito e armazenadas no objeto chamado `profile`.

## <a name="next-steps"></a>Próximos Passos

Agora que o perfil foi adicionado, a próxima etapa é adicionar um mecanismo para o perfil.

[Conceitos de motor de política](concept-profile-engine-policy-engine-cpp.md)
