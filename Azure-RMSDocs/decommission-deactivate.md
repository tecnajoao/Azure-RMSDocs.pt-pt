---
title: Encerrar e desativar o Azure RMS
description: Informações e instruções caso decida que já não pretendem utilizar o serviço de proteção baseada na cloud do Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 97a5296ade0a81433f07f8db76aada5646929373
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804952"
---
# <a name="decommissioning-and-deactivating-protection-for-azure-information-protection"></a>Encerrar e desativar a proteção do Azure Information Protection

>*Aplica-se a: [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

São sempre controlar se a organização protege conteúdo através do serviço Azure Rights Management do Azure Information Protection. Se decidir que já não pretende utilizar este serviço de proteção de informações, tem a garantia de que não ficará impedido de aceder ao conteúdo que foi protegido anteriormente.

Se não precisar de acesso contínuo ao conteúdo anteriormente protegido, desativar o serviço e permitir que a sua subscrição do Azure Information Protection expire. Por exemplo, isto poderá ser adequado para quando terminar de testar o Azure Information Protection antes de o implementar num ambiente de produção.

No entanto, se tiver implementado o Azure Information Protection na produção e proteger documentos e e-mails, certifique-se de que tem uma cópia da sua chave de inquilino do Azure Information Protection antes de desativar o serviço Azure Rights Management. Certifique-se de que tem uma cópia da chave antes de sua assinatura expire para se certificar de que pode manter o acesso a conteúdo que foi protegido pelo Azure Rights Management depois do serviço ser desativado. Se utilizou a traga a sua própria solução de chave (BYOK), a qual gerar e gerir a sua própria chave num HSM, já tem a chave de inquilino do Azure Information Protection. Mas se foi gerida pela Microsoft (predefinição), veja as instruções para exportar a chave de inquilino [operações para a chave de inquilino do Azure Information Protection](operations-tenant-key.md) artigo.

> [!TIP]
> Mesmo após a sua subscrição expirar, o seu inquilino do Azure Information Protection permanecerá disponível para consumir conteúdos durante um período prolongado. No entanto, vai deixar de poder exportar a sua chave de inquilino.

Quando tiver a sua chave de inquilino do Azure Information Protection, pode implementar o Rights Management no local (AD RMS) e importar a chave de inquilino como um domínio de publicação fidedigno (TPD). Em seguida, tem as seguintes opções para desativar a implementação do Azure Information Protection:

|Se isto se aplica a si...|… efetue o seguinte:|
|----------------------------|--------------|
|Quer que todos os utilizadores continuem a utilizar o Rights Management, mas utiliza uma solução no local em vez de utilizar o Azure Information Protection    →|Utilize o cmdlet [Set-AadrmMigrationUrl](/powershell/module/aadrm/Set-AadrmMigrationUrl) para direcionar os utilizadores existentes para a sua implementação no local quando consumirem conteúdo protegido após esta alteração. Os utilizadores utilizarão automaticamente a instalação do AD RMS para consumir conteúdo protegido.<br /><br />Para os utilizadores consumam conteúdo que foi protegido antes desta alteração, redirecionar os clientes para a implementação no local utilizando o **LicensingRedirection** chave de registo para o Office 2016 ou Office 2013. Para obter instruções, consulte a [secção de deteção do serviço](./rms-client/client-deployment-notes.md) nas notas de implementação do cliente do RMS e o **LicenseServerRedirection** chave de registo para o Office 2010, conforme descrito em [Office Definições de registo](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Pretende deixar de utilizar as tecnologias de Rights Management completamente    →|Conceda a um administrador designado [direitos de Superutilizador](configure-super-users.md) e instale o [cliente Azure Information Protection](./rms-client/client-admin-guide-install.md) para este utilizador.<br /><br />Este administrador, em seguida, pode utilizar o módulo do PowerShell a partir deste cliente para desencriptar em volume ficheiros em pastas que foram protegidos pelo serviço Azure Rights Management. Ficheiros voltem a estar desprotegidos e, portanto, podem ser lidos sem uma tecnologia de Rights Management, como o Azure Information Protection ou o AD RMS. Uma vez que este módulo do PowerShell pode ser utilizado com o serviço Azure Rights Management do Azure Information Protection e o AD RMS, terá a opção de desencriptar ficheiros antes ou depois de desativar o serviço Azure Rights Management ou uma combinação.|
|Não é possível identificar todos os ficheiros que foram protegidos pelo serviço Azure Rights Management do Azure Information Protection. Ou, se desejar que todos os utilizadores possam ler automaticamente quaisquer ficheiros protegidos em falta →|Implemente uma definição de registo em todos os computadores cliente utilizando a chave de registo **LicensingRedirection** para o Office 2016 ou o Office 2013, tal como descrito na [secção de deteção do serviço](./rms-client/client-deployment-notes.md) nas notas de implementação do cliente do RMS, bem como a chave de registo **LicenseServerRedirection** para o Office 2010, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Implemente também outra definição de registo para impedir que os utilizadores protejam novos ficheiros ao definir **DisableCreation** como **1**, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Pretende um serviço de recuperação manual controlado para ficheiros em falta    →|Conceda a utilizadores num grupo de recuperação de dados designados [direitos de Superutilizador](configure-super-users.md) e instale o [cliente Azure Information Protection](./rms-client/client-admin-guide-install.md) para estes utilizadores, para que possam desproteger ficheiros quando esta ação é solicitada por usuários padrão.<br /><br />Implemente em todos os computadores a definição de registo para impedir que os utilizadores protejam novos ficheiros ao definir **DisableCreation** como **1**, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
Para obter mais informações sobre os procedimentos nesta tabela, consulte os recursos seguintes:

- Para obter informações acerca do AD RMS e ter acesso às referências de implementação, consulte [Descrição Geral dos Serviços de Gestão de Direitos do Active Directory](https://technet.microsoft.com/library/hh831364.aspx).

- Para obter instruções para importar a sua chave de inquilino do Azure Information Protection como um ficheiro TPD, consulte [Adicionar um Domínio de Publicação Fidedigno](https://technet.microsoft.com/library/cc771460.aspx).

- Para instalar o módulo do Windows PowerShell para o Azure Rights Management, para definir o URL de migração, consulte [instalar o módulo do PowerShell do AADRM](install-powershell.md).

- Para utilizar o PowerShell com o cliente do Azure Information Protection, veja [utilizar o PowerShell com o cliente do Azure Information Protection](./rms-client/client-admin-guide-powershell.md).

Quando estiver pronto para desativar o serviço Azure Rights Management na sua organização, utilize as instruções que se seguem.

## <a name="deactivating-rights-management"></a>Desativar o Rights Management
Utilize um dos seguintes procedimentos para desativar o Azure Rights Management.

> [!TIP]
> Também pode utilizar o cmdlet Windows PowerShell, [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm), para desativar o Rights Management.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Para desativar o Rights Management a partir do centro de administração do Office 365

1. Aceda à [página do Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) para administradores do Office 365.
    
    Se lhe for pedido para iniciar sessão, utilize uma conta que seja um administrador global do Office 365.    

2. Na página **gestão de direitos**, clique em **desativar**.

3.  Quando lhe for pedido **que pretende desativar o Rights Management?** clique em **desativar**.

Já deverá estar visível **O Rights Management não está ativado** e a opção para ativar.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Para desativar o Rights Management a partir do portal do Azure

1. Se ainda não o tiver feito, abra uma nova janela do browser e [inicie sessão no portal do Azure](configure-policy.md#signing-in-to-the-azure-portal). Em seguida, navegue para o painel **Azure Information Protection**.
    
    Por exemplo, no hub menu, clique em **todos os serviços** e comece a escrever **informações** na caixa Filtro. Selecione **Azure Information Protection**.

2. No inicial **do Azure Information Protection** painel, selecione **ativação de proteção**. 

3.  Sobre o **do Azure Information Protection – ativação de proteção** painel, selecione **desativar**. Selecione **Sim** para confirmar a sua escolha.

A barra de informações apresenta **desativação foi concluída com êxito** e **desativar** foi substituída por **ativar**. 




