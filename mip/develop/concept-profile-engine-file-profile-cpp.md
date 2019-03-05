---
title: Conceitos - o objeto de perfil de API de ficheiros
description: Este artigo ajuda-o a compreender os conceitos em todo o objeto de perfil do ficheiro, o que é criada durante a inicialização do aplicativo.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: 19b283017929858299bd1c9af0662b170b4206f0
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333015"
---
# <a name="microsoft-information-protection-sdk---file-api-profile-concepts"></a>SDK - conceitos de perfil de API de ficheiros do Microsoft Information Protection

O perfil é a classe de raiz para todas as operações no SDK do MIP. Antes de utilizar qualquer uma das funcionalidades de API de ficheiros, um `FileProfile` tem de ser criada e todas as operações futuras serão executadas pelo perfil ou por outros objetos *adicionado* ao perfil.

Existem alguns pré-requisitos de código devem ser cumpridos antes de tentar criar uma instância de um perfil:

- `AuthDelegateImpl` é implementado para expandir `mip::AuthDelegate`.
- `ConsentDelegateImpl` é implementado para expandir `mip::ConsentDelegate`.
- O aplicativo tiver sido [registado no Azure Active Directory](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad.md) e o cliente ID é hard-coded para os ficheiros de configuração ou aplicação. 
- Uma classe a herdar `mip::FileProfile::Observer` foi implementado corretamente.

## <a name="load-a-profile"></a>Um perfil de carga

Com o `ProfileObserver`, `ConsentDelegateImpl`, e `AuthDelegateImpl` definidos, `mip::FileProfile` agora pode ser instanciado. Criar a `mip::FileProfile` objeto requer [ `mip::FileProfile::Settings` ](reference/class_mip_fileprofile_settings.md) para armazenar todas as informações de definições sobre o `FileProfile`.

### <a name="fileprofilesettings-parameters"></a>Parâmetros de FileProfile::Settings

O `FileProfile::Settings` construtor aceita parâmetros de cinco, listados abaixo:

- `std::string path`: Caminho de ficheiro em que o registo, telemetria e outras estado persistente é armazenado.
- `bool useInMemoryStorage`: Define se é ou não a todos os Estados devem ser armazenados na memória, em vez de no disco.
- `std::shared_ptr<mip::AuthDelegate> authDelegate`: Um ponteiro compartilhado da classe `mip::AuthDelegate` 
- `std::shared_ptr<mip::ConsentDelegate>`: 
- `std::shared_ptr<mip::FileProfile::Observer> observer`: Um ponteiro compartilhado para o `FileProfile::Observer` implementação.
- `mip::ApplicationInfo applicationInfo`: objeto. Utilizado para definir as informações sobre a aplicação que está a consumir o SDK.

Os exemplos seguintes mostram como criar o `profileSettings` utiliza o armazenamento local para o armazenamento de estado, assim como na memória apenas de objeto. Ambos partem do princípio de que o `authDelegateImpl` objeto já foi criado.

#### <a name="store-state-in-memory-only"></a>Estado de Store na memória apenas

```cpp
FileProfile::Settings profileSettings(
    "",                                          //path to store settings
    true,                                        //useInMemoryStorage
    authDelegateImpl,                            //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),     //new consent delegate
    std::make_shared<FileProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>Definições de perfil de leitura/escrita do caminho de armazenamento no disco

O recorte de código seguinte instruirá o `FileProfile` para armazenar todos os dados de estado de aplicação no `./mip_app_data`.

```cpp
FileProfile::Settings profileSettings(
    "./mip_app_data",                            //path to store settings
    false,                                       //useInMemoryStorage
    authDelegateImpl,                            //auth delegate object
    std::make_shared<ConsentDelegateImpl>(),     //new consent delegate
    std::make_shared<FileProfileObserverImpl>(), //new protection profile observer
    mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" }); //ApplicationInfo object
```

#### <a name="load-the-profile"></a>O perfil de carga

Utilizar qualquer um dos detalhes da abordagem acima, agora a utilizar o padrão de promessa/futuro para carregar o `FileProfile`.

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<FileProfile>>>();
auto profileFuture = profilePromise->get_future();
FileProfile::LoadAsync(profileSettings, profilePromise);
```

Se o carregou um perfil, e a operação foi concluída com êxito, `ProfileObserver::OnLoadSuccess`, nossa implementação de `mip::FileProfile::Observer::OnLoadSuccess` é chamado. O objeto resultante ou ponteiro de exceção, bem como o contexto, é passado como parâmetros para a função. O contexto é um ponteiro para o `std::promise` que criámos para processar a operação assíncrona. A função simplesmente define o valor da promessa para o objeto de FileProfile que foi passado para o primeiro parâmetro. Quando utiliza a função principal `Future.get()`, o resultado pode ser armazenado num novo objeto.

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

    FileProfile::Settings profileSettings("",
            false,
            authDelegateImpl,
            std::make_shared<ConsentDelegateImpl>(),
            std::make_shared<ProfileObserver>(),
            mip::ApplicationInfo{ "MyClientId", "MyAppFriendlyName" });

    auto profilePromise = std::make_shared<promise<shared_ptr<FileProfile>>>();
    auto profileFuture = profilePromise->get_future();
    FileProfile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

Resultar de final é que podemos carreguei o perfil com êxito e armazenadas no objeto chamado `profile`.

## <a name="next-steps"></a>Próximos Passos

Agora que o perfil foi adicionado, a próxima etapa é adicionar um mecanismo para o perfil. 

- [Conceitos de motor de ficheiros](concept-profile-engine-file-engine-cpp.md)
