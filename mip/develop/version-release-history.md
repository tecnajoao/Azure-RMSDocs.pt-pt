---
title: Versão do SDK de proteção de informações da Microsoft (MIP) histórico de versões e política de suporte
description: Um guia de início rápido que mostra como escrever a lógica de inicialização para um cliente de proteção de informações da Microsoft (MIP) SDK de aplicações.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 01/08/2019
ms.author: bryanla
manager: barbkess
ms.openlocfilehash: 1d7b30832441180f8673e7430d7d32e8a58a5205
ms.sourcegitcommit: 8c2de5119105cf5d5bc91fcc2202b64e5a779e7c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/12/2019
ms.locfileid: "56082813"
---
# <a name="microsoft-information-protection-mip-sdk-version-release-history-and-support-policy"></a>Versão do SDK de proteção de informações da Microsoft (MIP) histórico de versões e política de suporte

## <a name="servicing"></a>Manutenção 

Cada versão de disponibilidade geral (GA) é suportada durante seis meses depois da próxima versão de disponibilidade geral é a versão. A documentação não pode incluir informações sobre as versões não suportadas. Só são aplicadas para a versão de DG mais recentes correções e novas funcionalidades.

Versões de pré-visualização não devem ser implantadas em produção. Em vez disso, utilize a versão de pré-visualização mais recente para testar novas funcionalidades ou correções disponíveis na versão de DG. Apenas a versão de pré-visualização mais recente é suportada.

## <a name="release-history"></a>Histórico de versões

Utilize as seguintes informações para ver o que há de novo ou alterado para uma versão suportada. A versão mais atual aparece em primeiro na lista. 

> [!NOTE]
> Pequenas correções não são listadas para que se ocorrer um problema com o SDK, recomendamos que verifique se ser corrigido com o lançamento de DG mais recente. Se o problema persistir, verifique a versão de pré-visualização atual.
>  
> Para obter suporte técnico, visite o [fórum do Stack Overflow Microsoft Information Protection](https://stackoverflow.com/questions/tagged/microsoft-information-protection). 

## <a name="version-110"></a>Versão 1.1.0

**Data de lançamento**: TBD

Esta versão introduz o suporte para as seguintes plataformas:

  - .NET
  - iOS SDK (política de API)
  - SDK Android (política de API e a API de proteção)

**Novas funcionalidades:**

- Suporte ADRMS
- Operações de API de proteção são verdadeiramente assíncronas (no Win32), permitindo que para operações de encriptação/desencriptação sem bloqueio simultânea
  - Retornos de chamada do aplicativo (AuthDelegate, HTTPDelegate, etc.) agora podem ser invocados no *qualquer* em segundo plano thread
- Propriedades da etiqueta personalizada definidas por administradores de TI agora podem ser lidos por meio de mip::Label::GetCustomSettings
- Licença de publicação serializada agora pode ser recuperada diretamente a partir de um ficheiro sem quaisquer operações HTTP por meio de mip::FileHandler::GetSerializedPublishingLicense
- As aplicações são notificados se uma operação de HTTP é necessário para concluir a criação de um mip::FileEngine mip::PolicyEngine via mip::FileProfile::Observer::OnAddPolicyEngineStarting / mip::PolicyProfile::Observer::OnAddEngineStarting
- Deteção de se o conteúdo protegido tem uma data de expiração ou não foi simplificada mip::ProtectionDescriptor::DoesContentExpire do método de conveniência
- Classificação:
  - Tipos de sensibilidade (expressões de regex para #, passport # 's, etc.) podem ser compradas a partir do serviço de SCC
    - Ativar funcionalidade definindo mip::FileEngine::Settings / mip::PolicyEngine::Settings sinalizador
    - Ler tipos via mip::FileEngine::ListSensitivityTypes / mip::PolicyEngine::ListSensitivityTypes
  - Resultados de classificação de utilitários de scanner de documentos externos podem ser alimentados para MIP para orientar recomendado/necessário etiquetas com base no conteúdo do documento
    - Transmitir os resultados para MIP via mip::FileExecutionState::GetClassificationResults / mip::ExecutionState::GetClassificationResults
    - Mip::ApplyLabelAction e mip::RecommendLabelAction podem ser devolvidos por mip::PolicyEngine::ComputeActions quando os resultados de classificação correspondem a uma regra de política que indica as etiquetas necessárias/recomendado

- Novos requisitos:
  - Imposto de população de ID/nome/versão campos mip::ApplicationInfo ao criar mip::FileProfile, mip::PolicyProfile e mip::ProtectionProfile
  - Aplicativos devem implementar a nova interface de mip::FileExecutionState durante a criação de mip::FileHandlers
  
- Exceções atualizadas:
  - Mip::NoAuthTokenError emitida se AuthDelegate da aplicação devolver um token vazio (devido a cancelamento)
    - Aplica-se a criação de:
      - mip::FileEngine
      - mip::FileHandler
      - mip::PolicyEngine
      - mip::ProtectionHandler
  - Mip::NoPolicyError gerada se o inquilino não está configurado para etiquetas
    - Aplica-se a criação de:
      - mip::FileEngine
      - mip::PolicyEngine
  - Mip::ServiceDisabledError gerada se o serviço RMS está desabilitado para um utilizador/dispositivo/plataforma/inquilino específico
    - Aplica-se a criação de:
      - mip::FileHandler
      - mip::ProtectionHandler
  - Mip::NoPermissionsError emitida se um utilizador não tem direitos para descriptografar um documento ou o conteúdo está expirado
    - Aplica-se a criação de:
      - mip::FileHandler
      - mip::ProtectionHandler

**Correções**:

TBD

## <a name="next-steps"></a>Passos Seguintes

- Ver [MIP SDK FAQ e problemas](faqs-known-issues.md) para obter informações sobre as plataformas suportadas e muito mais.
- Ver [MIP SDK instalação e configuração](setup-configure-mip.md) para obter informações sobre como começar com o SDK de MIP.