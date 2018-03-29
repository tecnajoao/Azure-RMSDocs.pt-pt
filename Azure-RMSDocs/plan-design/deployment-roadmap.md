---
title: Plano de implementação do Azure Information Protection
description: Utilize estes passos para preparar, implementar e gerir o Azure Information Protection para a sua organização.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: b459babbf16b536b1cd73d0bb0ec2c36a499f9e1
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/28/2018
---
# <a name="azure-information-protection-deployment-roadmap"></a>Plano de implementação do Azure Information Protection

>*Aplica-se a: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize os seguintes passos conforme recomendações para o ajudar a preparar, implementar e gerir o Azure Information Protection na sua organização.

Contudo, se apenas quiser experimentar rapidamente o Azure Information Protection para si próprio, em vez de o implementar num ambiente de produção, consulte [Tutorial de início rápido do Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

> [!IMPORTANT]
> Antes de efetuar os passos seguintes, certifique-se de que consultou os [Requisitos do Azure Information Protection](../get-started/requirements-azure-rms.md).

Selecione o plano de implementação que se aplica à sua organização e corresponde às [funcionalidades da subscrição](https://azure.microsoft.com/pricing/details/information-protection/) de que precisa:

- [Utilizar classificação, etiquetagem e proteção](#deployment-roadmap-for-classification-labeling-and-protection)

- [Utilizar apenas proteção de dados](#deployment-roadmap-for-data-protection-only)


## <a name="deployment-roadmap-for-classification-labeling-and-protection"></a>Plano de implementação para classificação, etiquetagem e proteção

> [!NOTE]
> Já a utilizar a funcionalidade de proteção do Azure Information Protection? Pode ignorar muitos destes passos e concentrar-se nos passos 3 e 5.1.

### <a name="step-1-confirm-your-subscription-and-assign-user-licenses"></a>Passo 1: confirmar a sua subscrição e atribuir licenças de utilizador
Reveja a lista de informações e a funcionalidade de subscrição do [preços de proteção de informações do Azure](https://azure.microsoft.com/pricing/details/information-protection) página para confirmar que a sua organização tem uma subscrição que inclui a funcionalidade e as funcionalidades que pretende. Em seguida, atribua uma licença desta subscrição a todos os utilizadores na sua organização que irão classificar, etiquetar e proteger documentos e e-mails.

Nota: não atribua licenças de utilizador manualmente a partir da subscrição do RMS para utilizadores individuais gratuita e não utilize esta licença para administrar o serviço Azure Rights Management para a sua organização. Estas licenças são apresentadas como **Adhoc do Rights Management** no Centro de administração do Office 365 e **RIGHTSMANAGEMENT_ADHOC** quando executa o cmdlet do Azure AD PowerShell, [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx). Para obter mais informações sobre como a subscrição do RMS para utilizadores individuais é automaticamente concedida e atribuída aos utilizadores, consulte [RMS para utilizadores individuais e Azure Information Protection](../understand-explore/rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Passo 2: preparar o inquilino para utilizar o Azure Information Protection
Antes de começar a utilizar o Azure Information Protection, efetue a seguinte preparação:

- Confirme que tem grupos e contas de utilizador no Office 365 ou no Azure Active Directory que serão utilizados pelo Azure Information Protection para autenticar e autorizar os utilizadores da sua organização. Se for necessário, crie estas contas e grupos ou sincronize-os partir do seu diretório local. Para obter mais informações, veja [Preparar utilizadores e grupos para o Azure Information Protection](prepare.md).

### <a name="step-3-configure-and-deploy-classification-and-labeling"></a>Passo 3: configurar e implementar a classificação e a etiquetagem

Se ainda não tiver uma estratégia de classificação, reveja a [política predefinida do Azure Information Protection](../deploy-use/configure-policy-default.md) e utilize-a como base para decidir as etiquetas de classificação a atribuir aos dados da organização. Pode personalizá-las para cumprir os seus requisitos empresariais. 

Reconfigure as etiquetas predefinidas do Azure Information Protection para fazer todas as alterações necessárias para suportar as suas decisões de classificação. Configure a política para etiquetagem manual pelos utilizadores e escreva a orientação do utilizador que explica qual a etiqueta a aplicar e quando. Se a política predefinida foi criada com as etiquetas que aplicam automaticamente a proteção, remova as definições de proteção ou desativar a etiqueta. Para obter mais informações sobre como configurar a política do Azure Information Protection, consulte [Configurar a política do Azure Information Protection](../deploy-use/configure-policy.md).

Em seguida, implemente o cliente do Azure Information Protection para os utilizadores e forneça suporte através de formações de utilizador e instruções sobre quando selecionar as etiquetas. Para obter mais informações sobre a instalação e o suporte ao cliente, veja o [Guia do administrador do cliente do Azure Information Protection](../rms-client/client-admin-guide.md).

Após algum tempo, quando os utilizadores estiverem confortáveis a etiquetar os documentos e e-mails, apresente configurações mais avançadas. Estas podem incluir:

- Aplicar uma etiqueta predefinida

- Pedir aos utilizadores uma justificação se escolherem uma etiqueta com um nível de classificação inferior

- Exigir que todos os documentos e e-mails tenham uma etiqueta

- Cabeçalhos, rodapés ou marcas d'água personalizados

- Condições para suportar as recomendações e a etiquetagem automática

Nesta fase, não selecione a opção para proteger documentos e e-mails.

### <a name="step-4-prepare-for-data-protection"></a>Passo 4: Preparar para a proteção de dados

Quando os utilizadores estiverem mais confortáveis a etiquetar documentos e e-mails, estará pronto para começar a apresentar a proteção dos dados mais confidenciais. Nesta fase requer a preparação seguinte:

1. Decida se pretende que a Microsoft efetue a gestão da sua chave de inquilino (predefinição) ou se pretende gerar e gerir a sua chave de inquilino sozinho (conhecido como traga a sua própria chave ou BYOK). Para obter mais informações, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

2. Instale o módulo do PowerShell para AADRM em, pelo menos, um computador que tenha acesso à Internet. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [instalar o módulo do AADRM PowerShell](../deploy-use/install-powershell.md).

3. Se estiver a utilizar o AD RMS: efetuar uma migração para mover as chaves, modelos e URLs para a nuvem. Para obter mais informações, consulte [Migrar do AD RMS para o Information Protection](migrate-from-ad-rms-to-azure-rms.md).

4. Certifique-se de que o serviço de proteção está ativado para que pode começar a proteger documentos e e-mails. Se for necessária uma implementação faseada, configure os controlos de inclusão do utilizador para restringir a utilização a utilizadores específicos. Para obter mais informações, consulte [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

Opcionalmente, considere configurar o seguinte:

-   Modelos personalizados para as definições de proteção se os modelos predefinidos não forem suficientes para a sua organização. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [configurar e gerir modelos do Azure Information Protection](../deploy-use/configure-policy-templates.md).

-   Registo de utilização para que pode monitorizar a sua organização como utilizar o serviço de proteção. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md).

### <a name="step-5-configure-your-azure-information-protection-policy-applications-and-services-for-data-protection"></a>Passo 5: Configurar a política do Azure Information Protection, aplicações e serviços para proteção de dados

1. Atualize a política do Azure Information Protection para aplicar a proteção de dados
    
    Modificar a política do Azure Information Protection, para que um ou mais etiquetas aplicarem a proteção. Para obter mais informações, consulte [Como configurar uma etiqueta para a proteção do Rights Management](../deploy-use/configure-policy-protection.md).
    
    Tenha em atenção que os utilizadores podem aplicar etiquetas no Outlook que apliquem a proteção de Gestão de Direitos mesmo que o Exchange não esteja configurado para a gestão de direitos de informação (IRM). No entanto, até que o Exchange está configurado para IRM ou [encriptação de mensagens do Office 365 com as novas capacidades](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e), a organização não irá obter todas as funcionalidades de utilizar a proteção do Azure Rights Management com o Exchange. Esta configuração adicional está incluída na lista seguinte (2 para o Exchange Online e 5 para o Exchange no local). 

2. Configurar serviços e aplicações do Office
    
    Configure aplicações e serviços do Office para as funcionalidades de gestão de direitos de informação (IRM) no SharePoint Online ou Exchange Online. Para obter mais informações, consulte [Configurar aplicações para o Azure Rights Management](../deploy-use/configure-applications.md).

3. Configurar a funcionalidade de superutilizador para recuperação de dados
    
    Se tiver serviços de TI existentes que necessitam de inspecionar ficheiros que irá proteger o Azure Information Protection — como soluções de prevenção (DLP) de fuga de dados, conteúdo (CEG) de gateways de encriptação e produtos de antimalware — configurar as contas de serviço para ser super utilizadores do Azure Rights Management. Para obter mais informações, consulte [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md).

4. Classificar e proteger ficheiros em massa – conforme necessário
    
    Os cmdlets do PowerShell que lhe permitem classificar e proteger ficheiros, bem como remover a classificação e a proteção, são automaticamente instalados com o cliente do Azure Information Protection. Para obter mais informações, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](..\rms-client\client-admin-guide-powershell.md) no guia do administrador.

6. Implementar o conector para servidores no local
    
    Se tiver serviços no local que pretende utilizar com o serviço de proteção, instalar e configurar o conector Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).

### <a name="step-6-use-and-monitor-your-data-protection-solutions"></a>Passo 6: utilizar e monitorizar as soluções de proteção de dados
Agora, está pronto para proteger os seus dados e inicie sessão como da sua empresa está a utilizar as etiquetas que configurou e a proteção de dados. Para obter informações adicionais de apoio nesta fase de implementação, veja o seguinte:

- [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](../deploy-use/help-users.md)

-  [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md)

- [Ficheiros de cliente e registo de utilização](../rms-client/client-admin-guide-files-and-logging.md)

Se estiver interessado em proteger ficheiros automaticamente ao utilizar a Infraestrutura de Classificação de Ficheiros num servidor de ficheiros baseado no Windows, consulte [Proteção RMS com Infraestrutura de Classificação de Ficheiros (FCI) do Windows Server](../rms-client/configure-fci.md).

### <a name="step-7-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Passo 7: Administrar o serviço de proteção para a sua conta de inquilino, conforme necessário
Como começar a utilizar o serviço de proteção, poderá achar útil para ajudar a efetuar scripts ou automatizar alterações administrativas do PowerShell. Para obter mais informações, consulte [Administrar o serviço Azure Rights Management ao utilizar o Windows PowerShell](../deploy-use/administer-powershell.md).


## <a name="deployment-roadmap-for-data-protection-only"></a>Plano de implementação apenas para proteção de dados

### <a name="step-1-confirm-that-you-have-a-subscription-that-includes-the-protection-service-from-azure-information-protection"></a>Passo 1: Confirmar que tem uma subscrição que inclui o serviço de proteção do Azure Information Protection
Reveja a lista de informações e a funcionalidade de subscrição do [preços de proteção de informações do Azure](https://azure.microsoft.com/pricing/details/information-protection) página para confirmar que a sua organização tem uma subscrição que inclui a funcionalidade e as funcionalidades que pretende. Em seguida, atribua uma licença desta subscrição para cada utilizador na sua organização que irá proteger documentos e e-mails.

Nota: não atribua licenças de utilizador manualmente a partir da subscrição do RMS para utilizadores individuais gratuita e não utilize esta licença para administrar o serviço Azure Rights Management para a sua organização. Estas licenças são apresentadas como **Adhoc do Rights Management** no Centro de administração do Office 365 e **RIGHTSMANAGEMENT_ADHOC** quando executa o cmdlet do Azure AD PowerShell, [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx). Para obter mais informações sobre como a subscrição do RMS para utilizadores individuais é automaticamente concedida e atribuída aos utilizadores, consulte [RMS para utilizadores individuais e Azure Information Protection](../understand-explore/rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Passo 2: preparar o inquilino para utilizar o Azure Information Protection
Antes de começar a utilizar o serviço de proteção do Azure Information Protection, efetue a preparação seguinte:

1.  Confirme que o seu inquilino do Office 365 contém os grupos e as contas de utilizador que serão utilizados pelo Azure Information Protection para autenticar e autorizar os utilizadores da sua organização. Se for necessário, crie estas contas e grupos ou sincronize-os partir do seu diretório local. Para obter mais informações, veja [Preparar utilizadores e grupos para o Azure Information Protection](prepare.md).

2. Decida se pretende que a Microsoft efetue a gestão da sua chave de inquilino (predefinição) ou se pretende gerar e gerir a sua chave de inquilino sozinho (conhecido como traga a sua própria chave ou BYOK). Para obter mais informações, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

3. Instale o módulo do PowerShell para AADRM em, pelo menos, um computador que tenha acesso à Internet. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [instalar o módulo do AADRM PowerShell](../deploy-use/install-powershell.md).

4. Se estiver a utilizar o AD RMS: efetuar uma migração para mover as chaves, modelos e URLs para a nuvem. Para obter mais informações, consulte [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

5. Certifique-se de que o serviço de proteção está ativado para que pode começar a proteger documentos e e-mails. Se for necessária uma implementação faseada, configure os controlos de inclusão do utilizador para restringir a utilização a utilizadores específicos. Para obter mais informações, consulte [Ativar o Azure Rights Management](../deploy-use/activate-service.md).

Opcionalmente, considere configurar o seguinte:

-   Modelos personalizados para as definições de proteção se os modelos predefinidos não forem suficientes para a sua organização. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [configurar e gerir modelos do Azure Information Protection](../deploy-use/configure-policy-templates.md).

- Registo de utilização para que pode monitorizar a sua organização como utilizar o serviço de proteção. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md).

### <a name="step-3-install-the-client-and-configure-applications-and-services-for-rights-management"></a>Passo 3: instalar o cliente e configurar as aplicações e os serviços para o Rights Management

1. Implementar o cliente do Azure Information Protection
    
    Instale o Azure Information Protection para utilizadores, para suportar o Office 2010, a fim de proteger ficheiros diferentes dos documentos do Office e dos e-mails e para controlar documentos protegidos. Disponibilize formação de utilizador para este cliente. Para obter mais informações, veja [Cliente do Azure Information Protection para Windows](../rms-client/aip-client.md).

2. Configurar serviços e aplicações do Office
    
    Configure aplicações e serviços do Office para as funcionalidades de gestão de direitos de informação (IRM) no SharePoint Online ou Exchange Online. Para obter mais informações, consulte [Configurar aplicações para o Azure Rights Management](../deploy-use/configure-applications.md).

3. Configurar a funcionalidade de superutilizador para recuperação de dados
    
    Se tiver serviços de TI existentes que necessitam de inspecionar ficheiros que irá proteger o Azure Information Protection — como soluções de prevenção (DLP) de fuga de dados, conteúdo (CEG) de gateways de encriptação e produtos de antimalware — configurar as contas de serviço para ser super utilizadores do Azure Rights Management. Para obter mais informações, consulte [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../deploy-use/configure-super-users.md).

4. Proteger ficheiros em massa – conforme necessário 
    
    Os cmdlets do PowerShell que permitem proteger ou desproteger vários tipos de ficheiro em massa são automaticamente instalados com o cliente do Azure Information Protection. Para obter mais informações, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](..\rms-client\client-admin-guide-powershell.md) no guia do administrador.

5. Implementar o conector para servidores no local
    
    Se tiver serviços no local que pretende utilizar com o serviço de proteção, instalar e configurar o conector Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](../deploy-use/deploy-rms-connector.md).


### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>Passo 4: utilizar e monitorizar as soluções de proteção de dados
Agora, está pronto para proteger os seus dados e inicie sessão como da sua empresa estiver a utilizar o serviço de proteção. Para obter mais informações úteis para esta fase de implementação, consulte [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](../deploy-use/help-users.md) e [Registar e analisar a utilização do serviço Azure Rights Management](../deploy-use/log-analyze-usage.md).

Se estiver interessado em proteger ficheiros automaticamente ao utilizar a Infraestrutura de Classificação de Ficheiros num servidor de ficheiros baseado no Windows, consulte [Proteção RMS com Infraestrutura de Classificação de Ficheiros (FCI) do Windows Server](../rms-client/configure-fci.md).

### <a name="step-5-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Passo 5: Administrar o serviço de proteção para a sua conta de inquilino, conforme necessário
Como começar a utilizar o serviço de proteção, poderá achar útil para ajudar a efetuar scripts ou automatizar alterações administrativas do PowerShell. Para obter mais informações, consulte [Administrar o serviço Azure Rights Management ao utilizar o Windows PowerShell](../deploy-use/administer-powershell.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
