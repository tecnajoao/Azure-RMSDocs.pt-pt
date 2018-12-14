---
title: Preparar o ambiente para o Azure RMS e o AD RMS
description: Orientações para o caso de ter o Azure Rights Management com o AD RMS implementado.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/29/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 1a09edc0ed8a9bad27aa599282c9aaaf42ffc07a
ms.sourcegitcommit: 5b4eb0e17fb831d338d8c25844e9e6f4ca72246d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/10/2018
ms.locfileid: "53173677"
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>Preparar o ambiente para o Azure Rights Management quando também tem os Serviços de Gestão de Direitos do Active Directory (AD RMS)

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Documentação de orientação se estiver a utilizar o Active Directory Rights Management Services (AD RMS)

Se o serviço Azure Rights Management está ativado e que também está a utilizar o AD RMS, esta combinação não é compatível. Sem passos adicionais, alguns computadores podem iniciar automaticamente utilizando o serviço Azure Rights Management e também ligar ao cluster do AD RMS. Este cenário não é suportado e tem resultados pouco fiáveis, pelo que é importante que tome medidas adicionais. 

**Para verificar se implementou o AD RMS:**

1. Embora seja opcional, a maioria das implementações de AD RMS publique o ponto de ligação de serviço (SCP) do Active Directory para que os computadores do domínio podem detetar o cluster do AD RMS. 
    
    Utilize o Editor de ADSI para ver se tem um SCP publicado no Active Directory: `CN=Configuration [server name], CN=Services, CN=RightsManagementServices, CN=SCP`

2. Se não estiver a utilizar um SCP, computadores Windows, que se ligam a um cluster do AD RMS tem de ser configurados para a deteção do serviço do lado do cliente ou de redirecionamento do licenciamento através do registo do Windows: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation` ou `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`
    
    Para obter mais informações sobre estas configurações de registro, consulte [Ativar deteção de serviço do lado do cliente através do registo do Windows](./rms-client/client-deployment-notes.md#enabling-client-side-service-discovery-by-using-the-windows-registry) e [redirecionar o tráfego de servidor de licenciamento](./rms-client/client-deployment-notes.md#redirecting-licensing-server-traffic).   

Se o AD RMS é implementado na sua organização, considere se é possível migrar para o Azure Information Protection. O Azure Information Protection tem muitas vantagens ao longo do AD RMS. Por exemplo, um melhor suporte para dispositivos móveis e integração com serviços do Office 365, bem como com o Exchange Server e SharePoint Server. Para obter mais informações, consulte [comparar o Azure Information Protection e o AD RMS](compare-on-premise.md).

Ao migrar para o Azure Information Protection, não perderá o acesso ao conteúdo anteriormente protegido e não tiver a desproteger ou voltar a proteger seu conteúdo. Ainda podem ser abertos a documentos e e-mails que foram protegidos pelo AD RMS, mesmo depois de ter desaprovisionado AD RMS.

Se optar por migrar para o Azure Information Protection ou optar por aceitar as limitações de sessão com a sua implementação atual do AD RMS, primeiro tem de garantir que o serviço Azure Rights Management é desativado. Para obter instruções, siga os passos para o cenário que se aplica a:

- [A subscrição que inclui o Azure Rights Management foi comprada durante ou após Fevereiro de 2018](#your-subscription-was-purchased-during-or-after-february-2018)

- [Sua assinatura tiver sido adquirida antes ou durante a Fevereiro de 2018 e tiver o Exchange Online](#your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online)

- [Verá uma opção para ativar a proteção quando configurar a política de proteção de informações do Azure no portal do Azure](#you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection)


## <a name="your-subscription-was-purchased-during-or-after-february-2018"></a>Sua assinatura tiver sido adquirida durante ou após Fevereiro de 2018

Até o final de Fevereiro de 2018, as subscrições novas que incluem o Azure Information Protection agora ativar o serviço Azure Rights Management por predefinição. Se este serviço é ativado automaticamente para e também estiver a utilizar o Active Directory Rights Management Services (AD RMS), esta combinação não é compatível pelo que é importante que desative o serviço Azure Rights Management logo que possível. 

### <a name="step-1-deactivate-azure-rights-management"></a>Passo 1: Desativar o Azure Rights Management
Utilize um dos seguintes procedimentos para desativar o Azure Rights Management.

> [!TIP]
> Também pode utilizar o cmdlet Windows PowerShell, [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm), para desativar o serviço Azure Rights Management.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Para desativar o Rights Management a partir do centro de administração do Office 365

1. Aceda à [página do Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) para administradores do Office 365.
    
    Se lhe for pedido para iniciar sessão, utilize uma conta que seja um administrador global do Office 365.

2. Na página **gestão de direitos**, clique em **desativar**.

3.  Quando vir a linha de comandos **que pretende desativar o Rights Management?** clique em **desativar**.

Já deverá estar visível **O Rights Management não está ativado** e a opção para ativar.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Para desativar o Rights Management a partir do portal do Azure

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.
    
    Se ainda não tiver acedido o painel do Azure Information Protection antes, consulte o Monouso [passos adicionais](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time) para adicionar este painel para o portal.

2. Selecione **ativação de proteção** entre as opções de menu. 

3.  Sobre o **do Azure Information Protection – ativação de proteção** painel, selecione **desativar**. Selecione **Sim** para confirmar a sua escolha.

A barra de informações apresenta **desativação foi concluída com êxito** e **desativar** foi substituída por **ativar**. 

### <a name="step-2-start-planning-for-migration"></a>Passo 2: Começar a planejar a migração

Veja as orientações de migração: [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)


## <a name="your-subscription-was-purchased-before-or-during-february-2018-and-you-have-exchange-online"></a>Sua assinatura tiver sido adquirida antes ou durante a Fevereiro de 2018 e tiver o Exchange Online

Microsoft está a começar a ativar o serviço Azure Rights Management para assinaturas que incluem o Azure Rights Management ou do Azure Information Protection e os inquilinos estiver a utilizar o Exchange Online. Para estes inquilinos, a ativação automática é começar a implementar de 1 de Agosto de 2018.

Se o serviço é ativado automaticamente para e também estiver a utilizar o AD RMS, esta combinação não é compatível pelo que é importante que o inquilino é excluído da atualização automática do serviço. 

### <a name="step-1-opt-out-from-the-automatic-service-update"></a>Passo 1: Optar ativamente por participar da atualização do serviço automática

Utilize o seguinte procedimento [Set-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/set-irmconfiguration) comando do PowerShell do Exchange Online:`Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false`

[Mais informações](https://support.office.com/article/protection-features-in-azure-information-protection-rolling-out-to-existing-office-365-tenants-7ad6f58e-65d7-4c82-8e65-0b773666634d) 

### <a name="step-2-start-planning-for-migration"></a>Passo 2: Começar a planejar a migração

Veja as orientações de migração: [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)


## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Verá uma opção para ativar a proteção quando configurar o Azure Information Protection

O **do Azure Information Protection – ativação de proteção** painel tem uma opção para ativar o serviço Azure Rights Management.  

Se também estiver a utilizar o AD RMS, não selecione a **Activate** opção. Quando o serviço Azure Rights Management não está ativado, continua a poder utilizar o Azure Information Protection apenas para etiquetas que aplicam classificação. É criada uma política predefinida especial que não inclui a proteção de dados. Essas opções de configuração permanecem indisponíveis até ativar o serviço Azure Rights Management.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Passo 1: Configurar a política do Azure Information Protection para classificação e etiquetagem (sem proteção)

Do **do Azure Information Protection – etiquetas** painel, ver e configurar as etiquetas que não incluem as opções de proteção de dados. Para obter mais informações sobre como configurar as etiquetas e as definições de política, consulte [política de configuração do Azure Information Protection](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Passo 2: Começar a planejar a migração

Veja as orientações de migração: [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)

### <a name="step-3-configure-labels-for-protection"></a>Passo 3: Configurar etiquetas para proteção

Depois de ativar o serviço Azure Rights Management como parte do processo de migração, pode configurar as etiquetas para a proteção de dados. No entanto, se migrar utilizadores em lotes, certifique-se de que as etiquetas que aplicam a proteção estão no âmbito apenas a utilizadores migrados.


