---
title: "Ativar o Azure Rights Management – AIP"
description: "O serviço Azure Rights Management tem de ser ativado antes de a sua organização poder começar a proteger documentos e e-mails através da utilização de aplicações e serviços que suportam esta solução de proteção de informações."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6aa009795e45281df1c9406357f810b8d25302bc
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2017
---
# <a name="activating-azure-rights-management"></a>Ativar o Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

> [!NOTE]
> Estas informações de configuração são destinadas aos administradores responsáveis por um serviço que se aplica a todos os utilizadores de uma organização. Se estiver à procura de ajuda de utilizador e de informações sobre como utilizar a funcionalidade Rights Management para uma aplicação específica ou como abrir um ficheiro ou enviar um e-mail protegido por direitos, utilize a ajuda e as orientações incluídas na sua aplicação.
>
> Por exemplo, para aplicações do Office, clique no ícone Ajuda e introduza termos de pesquisa, como **Rights Management** ou **IRM**. Para o cliente do Azure Information Protection para o Windows, veja o [Guia do utilizador do cliente do Azure Information Protection](../rms-client/client-user-guide.md).
 
Quando o serviço Azure Rights Management para o Azure Information Protection é ativado para o seu inquilino, a sua organização pode começar a proteger dados importantes através da utilização de aplicações e serviços que suportam esta solução de proteção de informações. Os administradores também podem gerir e monitorizar e-mails e ficheiros protegidos de que a sua organização é proprietária. Este serviço tem de ser ativado antes de poder começar a utilizar as funcionalidades de gestão de direitos de informação (IRM) no Office, no SharePoint e no Exchange, e a proteger ficheiros confidenciais.

Se quiser saber mais acerca do serviço Azure Rights Management antes de o ativar (por exemplo, os problemas empresariais que resolve, alguns casos de utilização típicos e como funciona), veja [O que é o Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Não ative o serviço Azure Rights Management se tiver o Active Directory Rights Management Services (AD RMS) implementado na sua organização. [Mais informações](prepare-environment-adrms.md)

Antes de ativar o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], certifique-se de que a sua organização tem um plano de serviço que inclui a proteção de dados do Azure Rights Management. Caso contrário, não será possível ativar o Azure Rights Management. Tem de ter um dos seguintes:

- Um [plano do Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) 

- Um [plano do Office 365 que inclui o Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Quando o serviço Azure Rights Management está ativado, todos os utilizadores na sua organização podem aplicar a proteção de informações aos respetivos ficheiros e todos os utilizadores podem abrir (consumir) ficheiros que foram protegidos pelo Azure Rights Management. No entanto, se preferir, pode restringir quem pode aplicar a proteção de informações, ao utilizar controlos de inclusão para uma implementação faseada. Para obter mais informações, consulte a secção [Configurar os controlos de inclusão para uma implementação faseada](#configuring-onboarding-controls-for-a-phased-deployment) neste artigo.

Para obter instruções sobre como ativar os Rights Management service partir do portal de gestão, selecione se pretende utilizar o Centro de administração do Office 365 ou o portal do Azure:

- [**Centro de administração do Office 365** ](activate-office365.md) -requer a conta de administrador global

- [**Portal do Azure** ](activate-azure.md) -requer a conta de administrador global ou [conta de administrador de segurança](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles)

Em alternativa, pode utilizar o PowerShell para ativar o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]:

1. Instale a Ferramenta de Administração do Azure Rights Management, a qual instala o módulo de administração do Azure Rights Management. Para obter instruções, veja [Instalar o Windows PowerShell para o Azure Rights Management](../deploy-use/install-powershell.md).

2. A partir de uma sessão do PowerShell, execute [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice) e, quando for pedido, forneça os detalhes da conta de administrador global do inquilino do Azure Information Protection.

3. Execute o comando [Enable-Aadrm](/powershell/module/aadrm/enable-aadrm), que ativa o serviço Azure Rights Management.

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>Configurar os controlos de inclusão para uma implementação faseada
Se não quiser que todos os utilizadores possam proteger ficheiros imediatamente com o Azure Rights Management, pode configurar os controlos de inclusão do utilizador através do comando do PowerShell [Set-AadrmOnboardingControlPolicy](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy). Pode executar este comando antes ou depois de ativar o serviço Azure Rights Management.

> [!IMPORTANT]
> Para executar este comando, tem de ter no mínimo a versão **2.1.0.0** do [módulo do PowerShell para o Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721).
>
> Para verificar a versão que instalou, execute: **(Get-Module aadrm –ListAvailable).Version**

Por exemplo, se pretender inicialmente que apenas os administradores no grupo "Departamento de TI" (que tem uma ID de objeto de fbb99ded-32a0-45f1-b038-38b519009503) possam proteger conteúdo para fins de teste, utilize o seguinte comando:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fbb99ded-32a0-45f1-b038-38b519009503"
```

Tenha em atenção que para esta opção de configuração, tem de especificar um grupo. Não é possível especificar utilizadores individuais. Para obter o ID de objeto do grupo, pode utilizar o Azure AD PowerShell – por exemplo, para a versão 1.0 do módulo, utilize o comando [Get-MsolGroup](/powershell/msonline/v1/get-msolgroup). Em alternativa, pode copiar o valor do grupo **ID do objeto** do portal do Azure.

Em vez disso, se quiser certificar-se de que apenas os utilizadores que têm a licença correta para utilizar o Azure Information Protection podem proteger conteúdos:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $True
```

Quando já não precisar de utilizar os controlos de inclusão, quer tenha utilizado a opção de grupo ou de licença, execute:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False
```


Para obter mais informações sobre este cmdlet e exemplos adicionais, consulte a ajuda [Set-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/set-aadrmonboardingcontrolpolicy).

Quando utilizar estes controlos de inclusão, todos os utilizadores na organização podem sempre consumir conteúdo protegido que foi protegido pelo seu subconjunto de utilizadores, mas não poderão aplicar a proteção de informações a partir de aplicações de cliente. Por exemplo, não poderão ver nos seus clientes do Office os modelos predefinidos que são automaticamente publicados quando o Azure Rights Management está ativado ou os modelos personalizados que poderá configurar.  As aplicações do lado do servidor, como o Exchange, podem implementar os seus próprios controlos por utilizador para integrar o Rights Management, de forma a alcançar o mesmo resultado.


## <a name="next-steps"></a>Passos seguintes
Uma vez que ativou o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] para a sua organização, utilize o [Plano de implementação do Azure Information Protection](../plan-design/deployment-roadmap.md) para verificar se existem outros passos de configuração que necessite de realizar antes de implementar o Azure Information Protection para utilizadores e administradores. 

Por exemplo, pode querer utilizar [modelos](configure-policy-templates.md) para tornar mais fácil para os utilizadores aplicar proteção de informações aos ficheiros, ligar os servidores no local para utilizar [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] instalando o [conector Rights Management](deploy-rms-connector.md)e implementar o [cliente Azure Information Protection](../rms-client/aip-client.md) que suporta a proteção de todos os tipos de ficheiro em todos os dispositivos. 

Os serviços do Office, como o Exchange Online e o SharePoint Online, necessitam de configuração adicional antes de poder utilizar as respetivas funcionalidades de Gestão de Direitos de Informação (IRM). Para obter informações sobre a interação das suas aplicações com o serviço Rights Management, veja [Como as aplicações suportam o serviço Azure Rights Management](../understand-explore/applications-support.md).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]