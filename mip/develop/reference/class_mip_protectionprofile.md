---
title: classe mip ProtectionProfile
description: Referência para a classe mip ProtectionProfile
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a7dffb4a6b1490ef185eb9a5062f394f4509f00a
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446690"
---
# <a name="class-mipprotectionprofile"></a>classe mip::ProtectionProfile 
[ProtectionProfile](class_mip_protectionprofile.md) é a classe de raiz para a execução de operações de proteção.
Um aplicativo precisa criar uma [ProtectionProfile](class_mip_protectionprofile.md) antes de realizar quaisquer operações de proteção
  
## <a name="summary"></a>Resumo
 Membros                        | Descrições                                
--------------------------------|---------------------------------------------
 Definições de const públicas & GetSettings() const  |  Obtém as definições utilizadas pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo de seu ciclo de vida.
ListEnginesAsync void pública (const std::shared_ptr<void>& contexto)  |  Começa a lista a operação de mecanismos.
público Std:: vector Std:: < String > ListEngines()  |  Mecanismos de lista.
AddEngineAsync void pública (const ProtectionEngine::Settings e definições, const std::shared_ptr<void>& contexto)  |  Inicia a adicionar um novo mecanismo de proteção para o perfil.
público std::shared_ptr<ProtectionEngine> AddEngine (const ProtectionEngine::Settings e definições)  |  Adicione um novo mecanismo de proteção para o perfil.
DeleteEngineAsync void pública (Std:: String const & engineId, const std::shared_ptr<void>& contexto)  |  Começa a eliminar o mecanismo de proteção com o ID especificado. Todos os dados para o mecanismo de determinado serão eliminados.
 DeleteEngine void pública (const Std:: String & engineId)  |  Eliminar o mecanismo de proteção com o ID especificado. Todos os dados para o mecanismo de determinado serão eliminados.
  
## <a name="members"></a>Membros
  
### <a name="settings"></a>Definições
Obtém as definições utilizadas pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo de seu ciclo de vida.

  
**Devolve**: [configurações](class_mip_protectionprofile_settings.md) utilizado pelo [ProtectionProfile](class_mip_protectionprofile.md) durante a inicialização e ao longo de seu ciclo de vida
  
### <a name="listenginesasync"></a>ListEnginesAsync
Começa a lista a operação de mecanismos.

Parâmetros:  
* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para observadores


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="listengines"></a>ListEngines
Mecanismos de lista.

  
**Devolve**: em cache os IDs de motor
  
### <a name="addengineasync"></a>AddEngineAsync
Inicia a adicionar um novo mecanismo de proteção para o perfil.

Parâmetros:  
* **as definições**: a [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) objeto que especifica as definições do mecanismo. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para observadores


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="protectionengine"></a>ProtectionEngine
Adicione um novo mecanismo de proteção para o perfil.

Parâmetros:  
* **as definições**: a [mip::ProtectionEngine::Settings](class_mip_protectionengine_settings.md) objeto que especifica as definições do mecanismo.



  
**Devolve**: recém-criado [ProtectionEngine](class_mip_protectionengine.md)
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Começa a eliminar o mecanismo de proteção com o ID especificado. Todos os dados para o mecanismo de determinado serão eliminados.

Parâmetros:  
* **ID**: o ID exclusivo do motor. 


* **contexto**: contexto de cliente que irá ser transmitido de forma opaca para observadores


[ProtectionProfile::Observer](class_mip_protectionprofile_observer.md) será chamado após o êxito ou falha.
  
### <a name="deleteengine"></a>DeleteEngine
Eliminar o mecanismo de proteção com o ID especificado. Todos os dados para o mecanismo de determinado serão eliminados.

Parâmetros:  
* **ID**: o ID exclusivo do motor.

