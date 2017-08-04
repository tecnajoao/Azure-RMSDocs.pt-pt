---
title: "Plano de implementação do Azure Information Protection"
description: "Utilize estes passos para preparar, implementar e gerir o Azure Information Protection para a sua organização."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: fabb31e2945b47cda688129d7ecd7cc3c26fd802
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/31/2017
---
# <a name="azure-information-protection-deployment-roadmap"></a>Plano de implementação do Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

Utilize os seguintes passos para preparar, implementar e gerir o Azure Information Protection para a sua organização.

Contudo, se apenas quiser experimentar rapidamente o Azure Information Protection para si próprio, em vez de o implementar num ambiente de produção, consulte [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

> [!IMPORTANT]
> Antes de efetuar os passos seguintes, certifique-se de que consultou os [Requisitos do Azure Information Protection](../get-started/requirements-azure-rms.md).

Selecione o plano de implementação que se aplica à sua organização e corresponde às [funcionalidades da subscrição](https://www.microsoft.com/cloud-platform/azure-information-protection-features) de que precisa:

- [Utilizar classificação, etiquetagem e proteção](#deployment-roadmap-for-classification-labeling-and-protection)

- [Utilizar apenas proteção de dados](#deployment-roadmap-for-data-protection-only)


## <a name="deployment-roadmap-for-classification-labeling-and-protection"></a>Plano de implementação para classificação, etiquetagem e proteção

> [!NOTE]
> Já está a utilizar o serviço Azure Rights Management para proteção de dados? Pode ignorar muitos destes passos e concentrar-se nos passos 3 e 5.1.

### <a name="step-1-confirm-your-subscription-and-assign-user-licenses"></a>Passo 1: confirmar a sua subscrição e atribuir licenças de utilizador
Consulte as [informações de subscrição](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) e a [lista de funcionalidades](https://www.microsoft.com/cloud-platform/azure-information-protection-features) no site do Azure Information Protection para confirmar se a sua organização tem uma subscrição que inclui as funcionalidades que pretende. Em seguida, atribua uma licença desta subscrição a todos os utilizadores na sua organização que irão classificar, etiquetar e proteger documentos e e-mails.

Nota: não atribua licenças de utilizador manualmente a partir da subscrição do RMS para utilizadores individuais gratuita e não utilize esta licença para administrar o serviço Azure Rights Management para a sua organização. Estas licenças são apresentadas como **Adhoc do Rights Management** no Centro de administração do Office 365 e **RIGHTSMANAGEMENT_ADHOC** quando executa o cmdlet do Azure AD PowerShell, [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx). Para obter mais informações sobre como a subscrição do RMS para utilizadores individuais é automaticamente concedida e atribuída aos utilizadores, consulte [RMS para utilizadores individuais e Azure Information Protection](../understand-explore/rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Passo 2: preparar o inquilino para utilizar o Azure Information Protection
Antes de começar a utilizar o Azure Information Protection, efetue a seguinte preparação:

- Confirme que tem grupos e contas de utilizador no Office 365 ou no Azure Active Directory que serão utilizados pelo Azure Information Protection para autenticar e autorizar os utilizadores da sua organização. Se for necessário, crie estas contas e grupos ou sincronize-os partir do seu diretório local. Para obter mais informações, veja [Preparar utilizadores e grupos para o Azure Information Protection](prepare.md).

### <a name="step-3-configure-and-deploy-classification-and-labeling"></a>Passo 3: configurar e implementar a classificação e a etiquetagem

Se ainda não tiver uma estratégia de classificação, reveja a [política predefinida do Azure Information Protection](../deploy-use/configure-policy-default.md) e utilize-a como base para decidir as etiquetas de classificação a atribuir aos dados da organização. Pode personalizá-las para cumprir os seus requisitos empresariais. 

Reconfigure as etiquetas predefinidas do Azure Information Protection para fazer todas as alterações necessárias para suportar as suas decisões de classificação. Configure a política para etiquetagem manual pelos utilizadores e escreva a orientação do utilizador que explica qual a etiqueta a aplicar e quando. Para obter mais informações sobre como configurar a política do Azure Information Protection, consulte [Configurar a política do Azure Information Protection](../deploy-use/configure-policy.md).

Em seguida, implemente o cliente do Azure Information Protection para os utilizadores e forneça suporte através de formações de utilizador e instruções sobre quando selecionar as etiquetas. Para obter mais informações sobre a instalação e o suporte ao cliente, veja o [Guia do administrador do cliente do Azure Information Protection](../rms-client/client-admin-guide.md).

Após algum tempo, quando os utilizadores estiverem confortáveis a etiquetar os documentos e e-mails, apresente configurações mais avançadas. Estas podem incluir:

- Aplicar uma etiqueta predefinida

- Pedir aos utilizadores uma justificação se escolherem uma etiqueta com um nível de classificação inferior

- Exigir que todos os documentos e e-mails tenham uma etiqueta

- Cabeçalhos, rodapés ou marcas d'água personalizados

- Condições para suportar as recomendações e a etiquetagem automática

Nesta fase, não selecione a opção para proteger documentos e e-mails.

### <a name="step-4-prepare-for-rights-management-data-protection"></a>Passo 4: preparar-se para a proteção de dados do Rights Management

Quando os utilizadores estiverem mais confortáveis a etiquetar documentos e e-mails, estará pronto para começar a apresentar a proteção dos dados mais confidenciais. Esta fase requer a seguinte preparação para o serviço Azure Rights Management:

1. Decida se pretende que a Microsoft efetue a gestão da sua chave de inquilino (predefinição) ou se pretende gerar e gerir a sua chave de inquilino sozinho (conhecido como traga a sua própria chave ou BYOK). Tenha em atenção que, atualmente, não é possível utilizar BYOK se utilizar o Exchange Online. Para obter mais informações, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

2. Instale o módulo do Windows PowerShell para o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] em, pelo menos, um computador que tenha acesso à Internet. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [Instalar o Windows PowerShell para o serviço Azure Rights Management](../deploy-use/install-powershell.md).

3. Se estiver a utilizar serviços de Gestão de Direitos no local: efetue uma migração para mover as chaves, os modelos e os URLs para a cloud. Para obter mais informações, consulte [Migrar do AD RMS para o Information Protection](migrate-from-ad-rms-to-azure-rms.md).

4. Ative o serviço Azure Rights Management para começar a proteger documentos e e-mails. Se for necessária uma implementação faseada, configure os controlos de inclusão do utilizador para restringir a utilização a utilizadores específicos. Para obter mais informações, consulte [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

Opcionalmente, considere configurar o seguinte:

-   Modelos personalizados se os modelos de política de direitos predefinidos não forem suficientes para a sua organização. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [configurar e gerir modelos do Azure Information Protection](../deploy-use/configure-policy-templates.md).

-   Registo de utilização para que possa monitorizar a forma como a sua organização utiliza o Rights Management. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md).

### <a name="step-5-configure-your-azure-information-protection-policy-applications-and-services-for-rights-management-data-protection"></a>Passo 5: configurar a política, aplicações e serviços do Azure Information Protection para a proteção de dados do Rights Management

1. Atualize a política do Azure Information Protection para aplicar a proteção de dados
    
    Modifique a sua política do Azure Information Protection para que uma ou mais etiquetas apliquem a proteção do Rights Management. Para obter mais informações, consulte [Como configurar uma etiqueta para a proteção do Rights Management](../deploy-use/configure-policy-protection.md).
    
    Tenha em atenção que os utilizadores podem aplicar etiquetas no Outlook que apliquem a proteção de Gestão de Direitos mesmo que o Exchange não esteja configurado para a gestão de direitos de informação (IRM). No entanto, até que o Exchange seja configurado para IRM, a sua organização não tem acesso a todas as funcionalidades associadas à utilização da proteção do Azure Rights Management com o Exchange. Esta configuração adicional está incluída na lista seguinte (2 para o Exchange Online e 5 para o Exchange no local). 

2. Configurar aplicações e serviços do Office para o IRM
    
    Configure aplicações e serviços do Office para as funcionalidades de gestão de direitos de informação (IRM) no SharePoint Online ou Exchange Online. Para obter mais informações, consulte [Configurar aplicações para o Azure Rights Management](../deploy-use/configure-applications.md).

3. Configurar a funcionalidade de superutilizador para recuperação de dados
    
    Se tiver serviços de TI existentes que precisem de inspecionar ficheiros que o Azure Rights Management irá proteger, tais como soluções de prevenção de fuga de dados (DLP), gateways de encriptação de conteúdo (CEG) e produtos antimalware, configure as contas de serviço para que sejam superutilizadores do Azure Rights Management. Para obter mais informações, consulte [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md).

4. Classificar e proteger ficheiros em massa – conforme necessário
    
    Os cmdlets do PowerShell que lhe permitem classificar e proteger ficheiros, bem como remover a classificação e a proteção, são automaticamente instalados com o cliente do Azure Information Protection. Para obter mais informações, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](..\rms-client\client-admin-guide-powershell.md) no guia do administrador.

6. Implementar o conector para servidores no local
    
    Se tiver serviços no local que pretende utilizar com o serviço Azure Rights Management, instale e configure o conector Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).

### <a name="step-6-use-and-monitor-your-data-protection-solutions"></a>Passo 6: utilizar e monitorizar as soluções de proteção de dados
Agora está pronto para proteger os seus dados e manter um registo de como a sua empresa está a utilizar as etiquetas que configurou e a proteção de dados do Rights Management. Para obter informações adicionais de apoio nesta fase de implementação, veja o seguinte:

- [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](../deploy-use/help-users.md)

-  [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md)

- [Ficheiros de cliente e registo de utilização](../rms-client/client-admin-guide-files-and-logging.md)

Se estiver interessado em proteger ficheiros automaticamente ao utilizar a Infraestrutura de Classificação de Ficheiros num servidor de ficheiros baseado no Windows, consulte [Proteção RMS com Infraestrutura de Classificação de Ficheiros (FCI) do Windows Server](../rms-client/configure-fci.md).

### <a name="step-7-administer-the-rights-management-service-for-your-tenant-account-as-needed"></a>Passo 7: administrar o serviço Rights Management para a sua conta de inquilino, conforme necessário
À medida que começar a utilizar o serviço Azure Rights Management, poderá considerar o Windows PowerShell útil para ajudar a efetuar scripts ou a automatizar alterações administrativas. Para obter mais informações, consulte [Administrar o serviço Azure Rights Management ao utilizar o Windows PowerShell](../deploy-use/administer-powershell.md).


## <a name="deployment-roadmap-for-data-protection-only"></a>Plano de implementação apenas para proteção de dados

### <a name="step-1-confirm-that-you-have-a-subscription-that-includes-azure-rights-management"></a>Passo 1: confirmar se tem uma subscrição que inclui o Azure Rights Management
Consulte as [informações de subscrição](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) e a [lista de funcionalidades](https://www.microsoft.com/cloud-platform/azure-information-protection-features) no site do Azure Information Protection para confirmar se a sua organização tem uma subscrição que inclui as funcionalidades que pretende. Em seguida, atribua uma licença desta subscrição a todos os utilizadores na sua organização que irão proteger documentos e e-mails através do serviço Azure Rights Management.

Nota: não atribua licenças de utilizador manualmente a partir da subscrição do RMS para utilizadores individuais gratuita e não utilize esta licença para administrar o serviço Azure Rights Management para a sua organização. Estas licenças são apresentadas como **Adhoc do Rights Management** no Centro de administração do Office 365 e **RIGHTSMANAGEMENT_ADHOC** quando executa o cmdlet do Azure AD PowerShell, [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx). Para obter mais informações sobre como a subscrição do RMS para utilizadores individuais é automaticamente concedida e atribuída aos utilizadores, consulte [RMS para utilizadores individuais e Azure Information Protection](../understand-explore/rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-the-azure-rights-management-service"></a>Passo 2: preparar o seu inquilino para utilizar o serviço Azure Rights Management
Antes de começar a utilizar o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], efetue a preparação seguinte:

1.  Confirme que o seu inquilino do Office 365 contém os grupos e as contas de utilizador que serão utilizados pelo Azure Information Protection para autenticar e autorizar os utilizadores da sua organização. Se for necessário, crie estas contas e grupos ou sincronize-os partir do seu diretório local. Para obter mais informações, veja [Preparar utilizadores e grupos para o Azure Information Protection](prepare.md).

2. Decida se pretende que a Microsoft efetue a gestão da sua chave de inquilino (predefinição) ou se pretende gerar e gerir a sua chave de inquilino sozinho (conhecido como traga a sua própria chave ou BYOK). Tenha em atenção que, atualmente, não é possível utilizar BYOK se utilizar o Exchange Online. Para obter mais informações, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

3. Instale o módulo do Windows PowerShell para o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] em, pelo menos, um computador que tenha acesso à Internet. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [Instalar o Windows PowerShell para o Azure Rights Management](../deploy-use/install-powershell.md).

4. Se estiver a utilizar serviços de Gestão de Direitos no local: efetue uma migração para mover as chaves, os modelos e os URLs para a cloud. Para obter mais informações, consulte [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

5. Ative o Rights Management de modo a poder começar a utilizar o serviço. Se for necessária uma implementação faseada, configure os controlos de inclusão do utilizador para restringir a utilização a utilizadores específicos. Para obter mais informações, consulte [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

Opcionalmente, considere configurar o seguinte:

-   Modelos personalizados se os modelos predefinidos não forem suficientes para a sua organização. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [configurar e gerir modelos do Azure Information Protection](../deploy-use/configure-policy-templates.md).

-   Registo de utilização para que possa monitorizar a forma como a sua organização utiliza o Rights Management. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md).

### <a name="step-3-install-the-client-and-configure-applications-and-services-for-rights-management"></a>Passo 3: instalar o cliente e configurar as aplicações e os serviços para o Rights Management

1. Implementar o cliente do Azure Information Protection
    
    Instale o Azure Information Protection para utilizadores, para suportar o Office 2010, a fim de proteger ficheiros diferentes dos documentos do Office e dos e-mails e para controlar documentos protegidos. Disponibilize formação de utilizador para este cliente. Para obter mais informações, veja [Cliente do Azure Information Protection para Windows](../rms-client/aip-client.md).

2. Configurar aplicações e serviços do Office para o IRM
    
    Configure aplicações e serviços do Office para as funcionalidades de gestão de direitos de informação (IRM) no SharePoint Online ou Exchange Online. Para obter mais informações, consulte [Configurar aplicações para o Azure Rights Management](../deploy-use/configure-applications.md).

3. Configurar a funcionalidade de superutilizador para recuperação de dados
    
    Se tiver serviços de TI existentes que precisem de inspecionar ficheiros que o Azure Rights Management irá proteger, tais como soluções de prevenção de fuga de dados (DLP), gateways de encriptação de conteúdo (CEG) e produtos antimalware, configure as contas de serviço para que sejam superutilizadores do Azure Rights Management. Para obter mais informações, consulte [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md).

4. Proteger ficheiros em massa – conforme necessário 
    
    Os cmdlets do PowerShell que permitem proteger ou desproteger vários tipos de ficheiro em massa são automaticamente instalados com o cliente do Azure Information Protection. Para obter mais informações, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](..\rms-client\client-admin-guide-powershell.md) no guia do administrador.

5. Implementar o conector para servidores no local
    
    Se tiver serviços no local que pretende utilizar com o serviço Azure Rights Management, instale e configure o conector Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).


### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>Passo 4: utilizar e monitorizar as soluções de proteção de dados
Agora está pronto para proteger os seus dados e manter um registo de como a sua empresa está a utilizar o Rights Management. Para obter mais informações úteis para esta fase de implementação, consulte [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](../deploy-use/help-users.md) e [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md).

Se estiver interessado em proteger ficheiros automaticamente ao utilizar a Infraestrutura de Classificação de Ficheiros num servidor de ficheiros baseado no Windows, consulte [Proteção RMS com Infraestrutura de Classificação de Ficheiros (FCI) do Windows Server](../rms-client/configure-fci.md).

### <a name="step-5-administer-the-rights-management-service-for-your-tenant-account-as-needed"></a>Passo 5: administrar o serviço Rights Management para a sua conta de inquilino, conforme necessário
À medida que começar a utilizar o serviço Azure Rights Management, poderá considerar o Windows PowerShell útil para ajudar a efetuar scripts ou a automatizar alterações administrativas. Para obter mais informações, consulte [Administrar o serviço Azure Rights Management ao utilizar o Windows PowerShell](../deploy-use/administer-powershell.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
