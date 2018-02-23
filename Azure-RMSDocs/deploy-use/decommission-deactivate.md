---
title: Encerrar e desativar o Azure RMS
description: "Informações e instruções se decidir que já não pretendem utilizar o serviço de proteção baseada na nuvem do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 18eff00f6b316c48dbca5a9a8ec2c2ab4e58f76c
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2018
---
# <a name="decommissioning-and-deactivating-protection-for-azure-information-protection"></a>Encerrar e desativar a proteção do Azure Information Protection

>*Aplica-se a: Azure Information Protection, Office 365*

São sempre no controlo dos se a organização protege conteúdo utilizando o serviço Azure Rights Management do Azure Information Protection. Se decidir que já não pretende utilizar este serviço de proteção de informações, tem a garantia que lhe não ficará impedido conteúdo que foi anteriormente protegido.

Se não precisa de acesso contínuo ao conteúdo anteriormente protegido, desativar o serviço e permita que a sua subscrição do Azure Information Protection expirar. Por exemplo, isto poderá ser adequado para quando terminar de testar o Azure Information Protection antes de o implementar num ambiente de produção.

No entanto, se tiver implementado o Azure Information Protection na produção e proteger documentos e e-mails, certifique-se de que tem uma cópia da sua chave de inquilino do Azure Information Protection antes de desativar o serviço Azure Rights Management. Certifique-se de que tem uma cópia da sua chave antes da sua subscrição expirar para se certificar de que pode manter o acesso ao conteúdo que foi protegido pelo Azure Rights Management depois do serviço ser desativado. Se utilizou a traga a sua própria solução de chave (BYOK), a qual gerar e gerir a sua própria chave num HSM, já tem a chave de inquilino do Azure Information Protection. Mas se foi gerida pela Microsoft (predefinição), consulte as instruções para exportar a chave de inquilino no artigo [Operações para a chave de inquilino do Azure Rights Management](operations-tenant-key.md).

> [!TIP]
> Mesmo após a sua subscrição expirar, o seu inquilino do Azure Information Protection permanecerá disponível para consumir conteúdos durante um período prolongado. No entanto, vai deixar de poder exportar a sua chave de inquilino.

Quando tiver a sua chave de inquilino do Azure Information Protection, pode implementar o Rights Management no local (AD RMS) e importar a chave de inquilino como um domínio de publicação fidedigno (TPD). Em seguida, tem as seguintes opções para desativar a implementação do Azure Information Protection:

|Se isto se aplica a si...|… efetue o seguinte:|
|----------------------------|--------------|
|Quer que todos os utilizadores continuem a utilizar o Rights Management, mas utiliza uma solução no local em vez de utilizar o Azure Information Protection    →|Utilize o cmdlet [Set-AadrmMigrationUrl](/powershell/module/aadrm/Set-AadrmMigrationUrl) para direcionar os utilizadores existentes para a sua implementação no local quando consumirem conteúdo protegido após esta alteração. Os utilizadores utilizarão automaticamente a instalação do AD RMS para consumir conteúdo protegido.<br /><br />Para os utilizadores consumam conteúdo que foi protegido antes desta alteração, redirecionar os clientes para a implementação no local utilizando o **LicensingRedirection** chave de registo para o Office 2016 ou Office 2013. Para obter instruções, consulte o [secção de deteção do serviço](../rms-client/client-deployment-notes.md) nas notas de implementação do cliente do RMS e o **LicenseServerRedirection** chave de registo para o Office 2010, conforme descrito em [definições de registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Pretende deixar de utilizar as tecnologias de Rights Management completamente    →|Conceda a um administrador designado [direitos de Superutilizador](../deploy-use/configure-super-users.md) e instalar o [cliente Azure Information Protection](../rms-client/client-admin-guide-install.md) para este utilizador.<br /><br />Este administrador, em seguida, pode utilizar o módulo do PowerShell deste cliente para desencriptar em volume ficheiros em pastas que foram protegidos pelo serviço do Azure Rights Management. Os ficheiros voltem a estar desprotegidos e, por conseguinte, podem ser lidos sem uma tecnologia de Rights Management, tais como o Azure Information Protection ou o AD RMS. Porque este módulo do PowerShell pode ser utilizado com o serviço Azure Rights Management do Azure Information Protection e o AD RMS, tem a opção de desencriptar ficheiros antes ou depois de desativar o serviço Azure Rights Management ou uma combinação.|
|Não é possível identificar todos os ficheiros que foram protegidos pelo serviço do Azure Rights Management do Azure Information Protection. Ou, se quiser todos os utilizadores possam ler automaticamente quaisquer ficheiros protegidos que estavam em falta →|Implemente uma definição de registo em todos os computadores cliente utilizando a chave de registo **LicensingRedirection** para o Office 2016 ou o Office 2013, tal como descrito na [secção de deteção do serviço](../rms-client/client-deployment-notes.md) nas notas de implementação do cliente do RMS, bem como a chave de registo **LicenseServerRedirection** para o Office 2010, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Implemente também outra definição de registo para impedir que os utilizadores protejam novos ficheiros ao definir **DisableCreation** como **1**, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Pretende um serviço de recuperação manual controlado para ficheiros em falta    →|Conceder a utilizadores designados num grupo de recuperação de dados [direitos de Superutilizador](../deploy-use/configure-super-users.md) e instalar o [cliente Azure Information Protection](../rms-client/client-admin-guide-install.md) para estes utilizadores, para que possam desproteger ficheiros quando solicitada por esta ação utilizadores padrão.<br /><br />Implemente em todos os computadores a definição de registo para impedir que os utilizadores protejam novos ficheiros ao definir **DisableCreation** como **1**, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
Para obter mais informações sobre os procedimentos nesta tabela, consulte os recursos seguintes:

- Para obter informações acerca do AD RMS e ter acesso às referências de implementação, consulte [Descrição Geral dos Serviços de Gestão de Direitos do Active Directory](https://technet.microsoft.com/library/hh831364.aspx).

- Para obter instruções para importar a sua chave de inquilino do Azure Information Protection como um ficheiro TPD, consulte [Adicionar um Domínio de Publicação Fidedigno](https://technet.microsoft.com/library/cc771460.aspx).

- Para instalar o módulo do Windows PowerShell para o Azure Rights Management, para definir o URL de migração, consulte [instalar o módulo do AADRM PowerShell](install-powershell.md).

- Para utilizar o PowerShell com o cliente Azure Information Protection, consulte o artigo [utilizando o PowerShell com o cliente Azure Information Protection](../rms-client/client-admin-guide-powershell.md).

Quando estiver pronto para desativar o serviço Azure Rights Management na sua organização, utilize as instruções que se seguem.

## <a name="deactivating-rights-management"></a>Desativar o Rights Management
Utilize um dos seguintes procedimentos para desativar o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Também pode utilizar o cmdlet do Windows PowerShell, [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm), para desativar o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Para desativar o Rights Management a partir do centro de administração do Office 365

1. Aceda à [página do Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) para administradores do Office 365.
    
    Se lhe for pedido para iniciar sessão, utilize uma conta que seja um administrador global do Office 365.    

2. Na página **gestão de direitos**, clique em **desativar**.

3.  Quando lhe for pedido **que pretende desativar o Rights Management?** clique **desativar**.

Já deverá estar visível **O Rights Management não está ativado** e a opção para ativar.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Para desativar o Rights Management a partir do portal do Azure

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. No iniciais **Azure Information Protection** painel, selecione **ativação da proteção**. 

3.  No **Azure Information Protection - ativação da proteção** painel, selecione **desativar**. Selecione **Sim** para confirmar a sua escolha.

Mostra a barra de informações **desativação foi concluído com sucesso** e **desativar** é agora substituída com **ativar**. 


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


