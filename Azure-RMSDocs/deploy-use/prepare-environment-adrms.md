---
title: Preparar o ambiente para o Azure RMS e o AD RMS
description: "Orientações para o caso de ter o Azure Rights Management com o AD RMS implementado."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5ab34172a4e822373161752142d9e082014285e1
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2018
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>Preparar o ambiente para o Azure Rights Management quando também tem os Serviços de Gestão de Direitos do Active Directory (AD RMS)

>*Aplica-se a: Azure Information Protection, Office 365*

Aplicar a documentação de orientação importante se já estiver a utilizar Active Directory Rights Management Services (AD RMS) e um dos seguintes cenários:

- [A subscrição que inclui o Azure Rights Management foi comprada na ou após Fevereiro de 2018](#your-subscription-was-purchased-during-or-after-february-2018).

- [Verá uma opção para ativar a proteção, quando configura a política do Azure Information Protection no portal do Azure](#you-see-an-option-to activate-azure-rights-management-when-you-configure-azure-information-protection)

## <a name="your-subscription-was-purchased-during-or-after-february-2018"></a>A subscrição foi comprada durante ou após Fevereiro de 2018

Se a sua subscrição que inclui o Azure Rights Management foi comprada durante ou após Februrary 2018, o serviço do Azure Rights Management está ativado por predefinição. Se também estiver a utilizar o Active Directory Rights Management Services (AD RMS), esta combinação não é compatível. Sem passos adicionais, alguns computadores podem iniciar automaticamente utilizando o serviço Azure Rights Management e também ligar ao cluster do AD RMS. Este cenário não é suportado e tem resultados pouco fiáveis, pelo que é importante que desative o serviço Azure Rights Management logo que possível. 

Quando estiver pronto para mover computadores do AD RMS para o serviço Azure Rights Management, pode iniciar o processo de migração. Um dos passos de migração é ativar o serviço novamente, mas efetuar este passo depois de exportar as informações de configuração do AD RMS para o serviço Azure Rights Management. Esta ordem garante que os documentos e e-mails que foram protegidos pelo AD RMS ainda podem ser abertos.

O primeiro passo é necessário desativar o serviço Azure Rights Management.

### <a name="step-1-deactivate-azure-rights-management"></a>Passo 1: Desativar o Azure Rights Management
Utilize um dos seguintes procedimentos para desativar o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Também pode utilizar o cmdlet do Windows PowerShell, [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), para desativar o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Para desativar o Rights Management a partir do centro de administração do Office 365

1. Aceda à [página do Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) para administradores do Office 365.
    
    Se lhe for pedido para iniciar sessão, utilize uma conta que seja um administrador global do Office 365.

2. Na página **gestão de direitos**, clique em **desativar**.

3.  Quando vir a linha de comandos **que pretende desativar o Rights Management?** clique **desativar**.

Já deverá estar visível **O Rights Management não está ativado** e a opção para ativar.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Para desativar o Rights Management a partir do portal do Azure

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.
    
    Se ainda não a aceder ao painel do Azure Information Protection antes, consulte o uso [passos adicionais](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time) para adicionar este painel no portal.

2. No iniciais **Azure Information Protection** painel, selecione **ativação da proteção**. 

3.  No **Azure Information Protection - ativação da proteção** painel, selecione **desativar**. Selecione **Sim** para confirmar a sua escolha.

Mostra a barra de informações **desativação foi concluído com sucesso** e **desativar** é agora substituída com **ativar**. 

### <a name="step-2-start-planning-for-migration"></a>Passo 2: começar a planear a migração

Consulte as instruções de migração: [migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Verá uma opção para ativar a proteção, quando configurar o Azure Information Protection

O **Azure Information Protection - ativação da proteção** painel tem uma opção para ativar o serviço Azure Rights Management (Azure RMS).  

Se também estiver a utilizar os Serviços de Gestão de Direitos do Active Directory (AD RMS), não selecione a opção **Ativar**. Se tiver o AD RMS, a ativação do Azure Rights Management também não é uma opção compatível. Este cenário não é suportado e tem resultados pouco fiáveis, pelo que é importante que não ative o Azure Rights Management nesta fase.  

Quando estiver pronto para mudar os computadores do AD RMS para o serviço Azure Rights Management, pode iniciar um processo de migração. Um dos passos da migração é ativar o serviço. No entanto, só deve fazê-lo depois de exportar as informações de configuração do AD RMS para o serviço Azure Rights Management. Este processo garante que continua a poder abrir os e-mails e documentos que foram protegidos pelo AD RMS. 

Quando o serviço Azure Rights Management não está ativado, continua a poder utilizar o Azure Information Protection apenas para etiquetas que aplicam classificação. É criada uma política predefinida especial que não inclui a proteção de dados. Essas opções de configuração permanecem indisponíveis até ativar o serviço Azure Rights Management.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Passo 1: configurar a política do Azure Information Protection para classificação e etiquetagem (sem proteção)

No painel inicial **Azure Information Protection**, selecione **Política global** para ver e configurar a sua política predefinida que não inclui opções de proteção de dados. Para mais informações, veja [Configurar a política do Azure Information Protection](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Passo 2: começar a planear a migração

Consulte as instruções de migração: [migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

### <a name="step-3-start-to-configure-labels-for-protection"></a>Passo 3: começar a configurar as etiquetas para a proteção

Depois de ativar o serviço Azure Rights Management como parte do processo de migração, pode configurar as etiquetas para a proteção de dados. No entanto, se migrar utilizadores em lotes, certifique-se de que as etiquetas que se aplicam a proteção estão no âmbito apenas a utilizadores migrados.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

