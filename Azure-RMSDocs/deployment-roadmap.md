---
title: Plano de implementação do Azure Information Protection
description: Utilize estes passos para preparar, implementar e gerir o Azure Information Protection para a sua organização.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4d1a63ac3ea5fae9782588b1779d7c7950738e23
ms.sourcegitcommit: 3b41a6e730fa40660a2bdf5b1a73d155c87aacc2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/06/2018
ms.locfileid: "48834611"
---
# <a name="azure-information-protection-deployment-roadmap"></a>Plano de implementação do Azure Information Protection

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Utilize os seguintes passos, como recomendações para ajudar a preparar, implementar e gerir o Azure Information Protection para a sua organização.

Contudo, se apenas quiser experimentar rapidamente o Azure Information Protection para si próprio, em vez de o implementar num ambiente de produção, consulte [Tutorial de início rápido do Azure Information Protection](./infoprotect-quick-start-tutorial.md).

> [!NOTE]
> Se estiver procurando por um mapa de versão do produto, consulte nosso [informações sobre novas versões e atualizações](information-support.md#information-about-new-releases-and-updates) secção.
> 
> Para obter informações sobre o unified etiquetagem experiências que estão atualmente em pré-visualização e anunciado na Microsoft Ignite de 2018, consulte [anúncio da disponibilidade das funcionalidades de proteção de informações para ajudar a proteger os seus dados confidenciais](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967) .

### <a name="identify-your-deployment-roadmap"></a>Identificar o seu plano de implementação

Antes de efetuar os seguintes passos para implementar o Azure Information Protection, certifique-se de que consultou [requisitos do Azure Information Protection](./requirements.md).

Em seguida, escolha o plano de implementação que se aplica à sua organização e que corresponde a [funcionalidades da subscrição](https://azure.microsoft.com/pricing/details/information-protection/) que terá de:

- [Utilizar classificação, etiquetagem e proteção](#deployment-roadmap-for-classification-labeling-and-protection)

- [Utilizar apenas proteção de dados](#deployment-roadmap-for-data-protection-only)


## <a name="deployment-roadmap-for-classification-labeling-and-protection"></a>Plano de implementação para classificação, etiquetagem e proteção

> [!NOTE]
> Já a utilizar a funcionalidade de proteção do Azure Information Protection? Pode ignorar muitos destes passos e concentrar-se nos passos 3 e 5.1.

### <a name="step-1-confirm-your-subscription-and-assign-user-licenses"></a>Passo 1: confirmar a sua subscrição e atribuir licenças de utilizador
Reveja a lista de informações e recursos de subscrição do [preços do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection) página para confirmar se a sua organização tem uma subscrição que inclui as funcionalidades que pretende. Em seguida, atribua licenças desta subscrição a todos os utilizadores na sua organização que irão classificar, Etiquetar e proteger documentos e e-mails.

Nota: não atribua licenças de utilizador manualmente a partir da subscrição do RMS para utilizadores individuais gratuita e não utilize esta licença para administrar o serviço Azure Rights Management para a sua organização. Estas licenças são apresentadas como **Adhoc do Rights Management** no Centro de administração do Office 365 e **RIGHTSMANAGEMENT_ADHOC** quando executa o cmdlet do Azure AD PowerShell, [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx). Para obter mais informações sobre como a subscrição do RMS para utilizadores individuais é automaticamente concedida e atribuída aos utilizadores, consulte [RMS para utilizadores individuais e Azure Information Protection](./rms-for-individuals.md).

### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Passo 2: preparar o inquilino para utilizar o Azure Information Protection
Antes de começar a utilizar o Azure Information Protection, certifique-se de que tem contas de utilizador e grupos no Office 365 ou Azure Active Directory. Estas contas de utilizador e grupos serão utilizados pelo Azure Information Protection para autenticar e autorizar os utilizadores da sua organização. Se for necessário, crie estas contas e grupos ou sincronize-os partir do seu diretório local. 

Para obter mais informações, veja [Preparar utilizadores e grupos para o Azure Information Protection](prepare.md).

### <a name="step-3-configure-and-deploy-classification-and-labeling"></a>Passo 3: configurar e implementar a classificação e a etiquetagem

> [!TIP]
> **Opcional mas recomendado**: considere implementar o [scanner do Azure Information Protection](deploy-aip-scanner.md) para detetar as informações confidenciais tiver em seus arquivos de dados local. As informações que localiza o scanner pode ajudá-lo com a taxonomia de classificação, fornece valiosas informações sobre etiquetas de que precisa, e quais arquivos precisam de proteger.
> 
> A deteção de impressão pode ser configurada para verificar tipos de informações confidenciais bem conhecidos em ficheiros locais no Windows Server, ficheiros nas partilhas de rede e ficheiros em versões no local do SharePoint. Porque esta configuração não exige que configurar etiquetas ou até mesmo ter sua taxonomia de classificação definida, que executa o scanner dessa maneira é adequado para este estágio inicial da sua implementação. Também pode utilizar esta configuração do scanner em paralelo com os seguintes passos de implementação, até que a configurar as condições para as etiquetas.

Se ainda não tiver uma estratégia de classificação, reveja a [política predefinida do Azure Information Protection](./configure-policy-default.md) e utilize-a como base para decidir as etiquetas de classificação a atribuir aos dados da organização. Pode personalizá-las para cumprir os seus requisitos empresariais.

Reconfigure as etiquetas predefinidas do Azure Information Protection para fazer todas as alterações necessárias para suportar as suas decisões de classificação. Configure a política para etiquetagem manual pelos utilizadores e escreva a orientação do utilizador que explica qual a etiqueta a aplicar e quando. Se sua política predefinida foi criada com as etiquetas que aplicam automaticamente a proteção, temporariamente remover as definições de proteção ou desativar a etiqueta. Para obter mais informações sobre como configurar a política do Azure Information Protection, consulte [Configurar a política do Azure Information Protection](./configure-policy.md).

Em seguida, implemente o cliente do Azure Information Protection para os utilizadores e forneça suporte através de formações de utilizador e instruções sobre quando selecionar as etiquetas. Para obter mais informações sobre a instalação e o suporte ao cliente, veja o [Guia do administrador do cliente do Azure Information Protection](./rms-client/client-admin-guide.md).

Após algum tempo, quando os utilizadores estiverem confortáveis a etiquetar os documentos e e-mails, apresente configurações mais avançadas. Estas podem incluir:

- Aplicar uma etiqueta predefinida

- Pedir aos utilizadores uma justificação se escolherem uma etiqueta com um nível de classificação inferior ou remover uma etiqueta

- Exigir que todos os documentos e e-mails tenham uma etiqueta

- Cabeçalhos, rodapés ou marcas d'água personalizados

- Condições para suportar as recomendações e a etiquetagem automática

Nesta fase, não selecione a opção para proteger documentos e e-mails. No entanto, depois de configurar etiquetas para a etiquetagem automática, execute o [scanner do Azure Information Protection](deploy-aip-scanner.md) nos seus dados locais armazena no modo de deteção e de acordo com a sua política. Executar a deteção de impressão com esta configuração indica quais as etiquetas seriam aplicadas a arquivos. Estas informações ajudam a ajustar a configuração de etiqueta e prepara para classificar e proteger ficheiros em massa. 

### <a name="step-4-prepare-for-data-protection"></a>Passo 4: Preparar para a proteção de dados

Quando os utilizadores estiverem mais confortáveis a etiquetar documentos e e-mails, estará pronto para começar a apresentar a proteção dos dados mais confidenciais. Esta fase requer a preparação seguinte:

1. Decida se pretende que a Microsoft efetue a gestão da sua chave de inquilino (predefinição) ou se pretende gerar e gerir a sua chave de inquilino sozinho (conhecido como traga a sua própria chave ou BYOK). Para obter mais informações, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

2. Instale o módulo do PowerShell para o AADRM em, pelo menos, um computador com acesso à Internet. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [instalar o módulo do PowerShell do AADRM](./install-powershell.md).

3. Se estiver a utilizar o AD RMS: efetuar uma migração para mover as chaves, modelos e URLs para a cloud. Para obter mais informações, consulte [Migrar do AD RMS para o Information Protection](migrate-from-ad-rms-to-azure-rms.md).

4. Certifique-se de que o serviço de proteção está ativado para que pode começar a proteger documentos e e-mails. Se uma implementação faseada for necessária, configure os controlos de inclusão do utilizador para restringir a capacidade dos utilizadores para aplicar a proteção. Para obter mais informações, veja [Ativar o Azure Rights Management](./activate-service.md).

Opcionalmente, considere configurar o seguinte:

- Registo de utilização para que possa monitorizar a forma como sua organização está a utilizar o serviço de proteção. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](./log-analyze-usage.md).

### <a name="step-5-configure-your-azure-information-protection-policy-applications-and-services-for-data-protection"></a>Passo 5: Configurar a sua política, aplicativos e serviços para proteção de dados do Azure Information Protection

1. Atualize a política do Azure Information Protection para aplicar a proteção de dados
    
    Modificar a política do Azure Information Protection para que um ou mais etiquetas apliquem a proteção. Para obter mais informações, consulte [Como configurar uma etiqueta para a proteção do Rights Management](./configure-policy-protection.md).
    
    Tenha em atenção que os utilizadores podem aplicar etiquetas no Outlook que apliquem a proteção de Gestão de Direitos mesmo que o Exchange não esteja configurado para a gestão de direitos de informação (IRM). No entanto, até que o Exchange seja configurado para IRM ou [encriptação de mensagens do Office 365 com os novos recursos](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e), sua organização não tem acesso a todas as funcionalidades de utilizar a proteção Azure Rights Management com o Exchange. Esta configuração adicional está incluída na lista seguinte (2 para o Exchange Online e 5 para o Exchange no local). 

2. Configurar aplicações e serviços Office
    
    Configure aplicações e serviços do Office para as funcionalidades de gestão de direitos de informação (IRM) no SharePoint Online ou Exchange Online. Para obter mais informações, consulte [Configurar aplicações para o Azure Rights Management](configure-applications.md).

3. Configurar a funcionalidade de superutilizador para recuperação de dados
    
    Se tiver serviços de TI existentes que precisem de inspecionar ficheiros que irá proteger do Azure Information Protection, tais como soluções de prevenção (DLP) de fuga de dados, encriptação gateways de conteúdo (CEG) e produtos antimalware de — configure as contas de serviço devem ser super utilizadores do Azure Rights Management. Para obter mais informações, consulte [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](./configure-super-users.md).

4. Classificar e proteger os ficheiros existentes em massa
    
    Para os arquivos de dados no local, agora, executados o [scanner do Azure Information Protection](deploy-aip-scanner.md) na imposição de modo que, para que os ficheiros são automaticamente identificados. Para arquivos de dados com base na cloud, utilize [do Azure Cloud App Security](https://docs.microsoft.com/cloud-app-security).
    
    Para os ficheiros em PCs, pode utilizar cmdlets do PowerShell para classificar e proteger ficheiros. Para obter mais informações, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](./rms-client/client-admin-guide-powershell.md) no guia do administrador.

6. Implementar o conector para bibliotecas protegidas por IRM no SharePoint Server e e-mails protegidos por IRM para o Exchange no local
    
    Se tiver o SharePoint e o Exchange no local e quisesse usar suas funcionalidades de gestão (IRM) direitos de informação, instalar e configurar o conector Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](./deploy-rms-connector.md).

### <a name="step-6-use-and-monitor-your-data-protection-solutions"></a>Passo 6: utilizar e monitorizar as soluções de proteção de dados
Agora, está pronto para monitorizar a forma como sua organização está a utilizar as etiquetas que configurou e confirme que está a proteger informações confidenciais. Para obter informações adicionais de apoio nesta fase de implementação, veja o seguinte:

- [Relatórios do Azure Information Protection](reports-aip.md) - atualmente em pré-visualização

- [Ficheiros de cliente e registo de utilização](./rms-client/client-admin-guide-files-and-logging.md)

- [Registar e analisar a utilização do serviço Azure Rights Management](./log-analyze-usage.md)

### <a name="step-7-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Passo 7: Administrar o serviço de proteção para a sua conta de inquilino, conforme necessário
Quando começar a utilizar o serviço de proteção, poderão ser úteis para ajudar a efetuar scripts ou a automatizar alterações administrativas do PowerShell. PowerShell também pode ser necessário para algumas das configurações avançadas. 

Para obter mais informações, consulte [Administrar o serviço Azure Rights Management ao utilizar o Windows PowerShell](./administer-powershell.md).


## <a name="deployment-roadmap-for-data-protection-only"></a>Plano de implementação apenas para proteção de dados

### <a name="step-1-confirm-that-you-have-a-subscription-that-includes-the-protection-service-from-azure-information-protection"></a>Passo 1: Confirmar que tem uma subscrição que inclui o serviço de proteção do Azure Information Protection
Reveja a lista de informações e recursos de subscrição do [preços do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection) página para confirmar se a sua organização tem uma subscrição que inclui as funcionalidades que pretende. Em seguida, atribua uma licença desta subscrição a todos os utilizadores na sua organização que irão proteger documentos e e-mails.

Nota: não atribua licenças de utilizador manualmente a partir da subscrição do RMS para utilizadores individuais gratuita e não utilize esta licença para administrar o serviço Azure Rights Management para a sua organização. Estas licenças são apresentadas como **Adhoc do Rights Management** no Centro de administração do Office 365 e **RIGHTSMANAGEMENT_ADHOC** quando executa o cmdlet do Azure AD PowerShell, [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx). Para obter mais informações sobre como a subscrição do RMS para utilizadores individuais é automaticamente concedida e atribuída aos utilizadores, consulte [RMS para utilizadores individuais e Azure Information Protection](./rms-for-individuals.md).


### <a name="step-2-prepare-your-tenant-to-use-azure-information-protection"></a>Passo 2: preparar o inquilino para utilizar o Azure Information Protection
Antes de começar a utilizar o serviço de proteção do Azure Information Protection, efetue a preparação seguinte:

1. Confirme que o seu inquilino do Office 365 contém os grupos e as contas de utilizador que serão utilizados pelo Azure Information Protection para autenticar e autorizar os utilizadores da sua organização. Se for necessário, crie estas contas e grupos ou sincronize-os partir do seu diretório local. Para obter mais informações, veja [Preparar utilizadores e grupos para o Azure Information Protection](prepare.md).

2. Decida se pretende que a Microsoft efetue a gestão da sua chave de inquilino (predefinição) ou se pretende gerar e gerir a sua chave de inquilino sozinho (conhecido como traga a sua própria chave ou BYOK). Para obter mais informações, consulte [Planear e implementar a sua chave de inquilino do Azure Information Protection](plan-implement-tenant-key.md).

3. Instale o módulo do PowerShell para o AADRM em, pelo menos, um computador com acesso à Internet. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [instalar o módulo do PowerShell do AADRM](./install-powershell.md).

4. Se estiver a utilizar o AD RMS: efetuar uma migração para mover as chaves, modelos e URLs para a cloud. Para obter mais informações, consulte [Migrar do AD RMS para o Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

5. Certifique-se de que o serviço de proteção está ativado para que pode começar a proteger documentos e e-mails. Se uma implementação faseada for necessária, configure os controlos de inclusão do utilizador para restringir a capacidade dos utilizadores para aplicar a proteção. Para obter mais informações, veja [Ativar o Azure Rights Management](./activate-service.md).

Opcionalmente, considere configurar o seguinte:

- Modelos personalizados para as definições de proteção se os modelos predefinidos não forem suficientes para a sua organização. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [configurando e gerenciando modelos do Azure Information Protection](./configure-policy-templates.md).

- Registo de utilização para que possa monitorizar a forma como sua organização está a utilizar o serviço de proteção. Pode efetuar este passo agora ou mais tarde. Para obter mais informações, consulte [Registar e analisar a utilização do serviço Azure Rights Management](./log-analyze-usage.md).

### <a name="step-3-install-the-client-and-configure-applications-and-services-for-rights-management"></a>Passo 3: instalar o cliente e configurar as aplicações e os serviços para o Rights Management

1. Implementar o cliente do Azure Information Protection
    
    Instale o Azure Information Protection para os utilizadores suportar o Office 2010, para proteger ficheiros diferentes dos documentos do Office e e-mails, e para controlar documentos protegidos. Disponibilize formação de utilizador para este cliente. Para obter mais informações, veja [Cliente do Azure Information Protection para Windows](./rms-client/aip-client.md).

2. Configurar aplicações e serviços Office
    
    Configure aplicações e serviços do Office para as funcionalidades de gestão de direitos de informação (IRM) no SharePoint Online ou Exchange Online. Para obter mais informações, consulte [Configurar aplicações para o Azure Rights Management](./configure-applications.md).

3. Configurar a funcionalidade de superutilizador para recuperação de dados
    
    Se tiver serviços de TI existentes que precisem de inspecionar ficheiros que irá proteger do Azure Information Protection, tais como soluções de prevenção (DLP) de fuga de dados, encriptação gateways de conteúdo (CEG) e produtos antimalware de — configure as contas de serviço devem ser super utilizadores do Azure Rights Management. Para obter mais informações, consulte [Configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](./configure-super-users.md).

4. Proteger ficheiros existentes em massa 
    
    Pode utilizar cmdlets do PowerShell para proteger em massa ou desproteger em volume de vários tipos de ficheiro. Para obter mais informações, veja [Utilizar o PowerShell com o cliente do Azure Information Protection](./rms-client/client-admin-guide-powershell.md) no guia do administrador.
    
    Para os ficheiros em servidores de ficheiros baseado no Windows, pode utilizar estes cmdlets com um script e a infraestrutura de classificação de ficheiros do Windows Server. Para obter mais informações, consulte [proteção RMS com o Windows Server classificação infraestrutura ficheiros (FCI)](./rms-client/configure-fci.md).

5. Implementar o conector para servidores no local
    
    Se tiver serviços no local que pretende utilizar com o serviço de proteção, instalar e configurar o conector Rights Management. Para obter mais informações, consulte [Implementar o conector do Azure Rights Management](./deploy-rms-connector.md).

### <a name="step-4-use-and-monitor-your-data-protection-solutions"></a>Passo 4: utilizar e monitorizar as soluções de proteção de dados
Agora, está pronto para proteger os seus dados e iniciar sessão como sua empresa está a utilizar o serviço de proteção. Para obter mais informações úteis para esta fase de implementação, consulte [Ajudar os utilizadores a proteger ficheiros com o serviço Azure Rights Management](./help-users.md) e [Registar e analisar a utilização do serviço Azure Rights Management](./log-analyze-usage.md).

### <a name="step-5-administer-the-protection-service-for-your-tenant-account-as-needed"></a>Passo 5: Administrar o serviço de proteção para a sua conta de inquilino, conforme necessário
Quando começar a utilizar o serviço de proteção, poderão ser úteis para ajudar a efetuar scripts ou a automatizar alterações administrativas do PowerShell. PowerShell também pode ser necessário para algumas das configurações avançadas. 

Para obter mais informações, consulte [Administrar o serviço Azure Rights Management ao utilizar o Windows PowerShell](./administer-powershell.md).
