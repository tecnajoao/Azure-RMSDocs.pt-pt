---
title: Encerrar e desativar o Azure RMS
description: "Informações e instruções caso decida que já não quer utilizar este serviço de proteção de informações do Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f577337cf7ce904a82ff23b165fdc7befe319092
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="decommissioning-and-deactivating-azure-rights-management"></a>Encerrar e desativar o Azure Rights Management

>*Aplica-se a: Azure Information Protection, Office 365*

Pode sempre controlar se a organização protege conteúdos com o serviço Azure Rights Management do Azure Information Protection e, se decidir que já não quer utilizar este serviço de proteção de informações, tem a garantia de que não ficará impedido de aceder aos conteúdos que foram protegidos anteriormente. Se não precisar de acesso contínuo aos conteúdos anteriormente protegidos, basta desativar o serviço e pode deixar que a sua subscrição do Azure Information Protection expire. Por exemplo, isto poderá ser adequado para quando terminar de testar o Azure Information Protection antes de o implementar num ambiente de produção.

No entanto, se tiver implementado o Azure Information Protection na produção e em documentos e e-mails protegidos, certifique-se de que tem uma cópia da sua chave de inquilino do Azure Information Protection antes de desativar o serviço Azure Rights Management e efetue este procedimento antes de a sua subscrição expirar, uma vez que isto irá garantir que pode manter o acesso aos conteúdos que foram protegidos pelo Azure Rights Management após o serviço ser desativado. Se utilizou a solução traga a sua própria chave (BYOK), em que gera e faz a gestão da sua própria chave num HSM, já terá a chave de inquilino do Azure Information Protection. Mas se foi gerida pela Microsoft (predefinição), consulte as instruções para exportar a chave de inquilino no artigo [Operações para a chave de inquilino do Azure Rights Management](operations-tenant-key.md).

> [!TIP]
> Mesmo após a sua subscrição expirar, o seu inquilino do Azure Information Protection permanecerá disponível para consumir conteúdos durante um período prolongado. No entanto, vai deixar de poder exportar a sua chave de inquilino.

Quando tiver a sua chave de inquilino do Azure Information Protection, pode implementar o Rights Management no local (AD RMS) e importar a chave de inquilino como um domínio de publicação fidedigno (TPD). Em seguida, tem as seguintes opções para desativar a implementação do Azure Information Protection:

|Se isto se aplica a si...|… efetue o seguinte:|
|----------------------------|--------------|
|Quer que todos os utilizadores continuem a utilizar o Rights Management, mas utiliza uma solução no local em vez de utilizar o Azure Information Protection    →|Utilize o cmdlet [Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx) para direcionar os utilizadores existentes para a sua implementação no local quando consumirem conteúdo protegido após esta alteração. Os utilizadores utilizarão automaticamente a instalação do AD RMS para consumir conteúdo protegido.<br /><br />Para que os utilizadores consumam conteúdo que foi protegido antes desta alteração, redirecione os seus clientes para a implementação no local utilizando a chave de registo **LicensingRedirection** para o Office 2016 ou o Office 2013, tal como descrito na [secção de deteção do serviço](../rms-client/client-deployment-notes.md) nas notas de implementação do cliente do RMS, bem como a chave de registo **LicenseServerRedirection** para o Office 2010, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Pretende deixar de utilizar as tecnologias de Rights Management completamente    →|Conceda a um administrador designado [direitos de superutilizador](../deploy-use/configure-super-users.md) e forneça-lhe a [Ferramenta de Proteção RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />Este administrador pode então utilizar a ferramenta para desencriptar ficheiros em volume em pastas que estavam protegidas pelo serviço Azure Rights Management, para que os ficheiros voltem a estar desprotegidos e, por conseguinte, possam ser lidos sem uma tecnologia de Rights Management, como o Azure Information Protection ou o AD RMS. Esta ferramenta pode ser utilizada com o serviço Azure Rights Management a partir do Azure Information Protection e AD RMS, para que possa escolher entre desencriptar ficheiros antes ou depois de desativar o serviço Azure Rights Management (ou uma combinação de ambos).|
|Não consegue identificar todos os ficheiros que estavam protegidos pelo serviço Azure Rights Management do Azure Information Protection ou quer que todos os utilizadores possam ler automaticamente quaisquer ficheiros protegidos em falta    →|Implemente uma definição de registo em todos os computadores cliente utilizando a chave de registo **LicensingRedirection** para o Office 2016 ou o Office 2013, tal como descrito na [secção de deteção do serviço](../rms-client/client-deployment-notes.md) nas notas de implementação do cliente do RMS, bem como a chave de registo **LicenseServerRedirection** para o Office 2010, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).<br /><br />Implemente também outra definição de registo para impedir que os utilizadores protejam novos ficheiros ao definir **DisableCreation** como **1**, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Pretende um serviço de recuperação manual controlado para ficheiros em falta    →|Conceda a utilizadores designados num grupo de recuperação de dados [direitos de superutilizador](../deploy-use/configure-super-users.md) e forneça-lhes a [Ferramenta de Proteção RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256) para que possam desproteger ficheiros quando solicitado por utilizadores padrão.<br /><br />Implemente em todos os computadores a definição de registo para impedir que os utilizadores protejam novos ficheiros ao definir **DisableCreation** como **1**, conforme descrito nas [Definições de Registo do Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
Para obter mais informações sobre os procedimentos nesta tabela, consulte os recursos seguintes:

-   Para obter informações acerca do AD RMS e ter acesso às referências de implementação, consulte [Descrição Geral dos Serviços de Gestão de Direitos do Active Directory](https://technet.microsoft.com/library/hh831364.aspx).

-   Para obter instruções para importar a sua chave de inquilino do Azure Information Protection como um ficheiro TPD, consulte [Adicionar um Domínio de Publicação Fidedigno](https://technet.microsoft.com/library/cc771460.aspx).

-   Para instalar o módulo do Windows PowerShell para o Azure Rights Management, para definir o URL de migração, consulte [Instalar o Windows PowerShell para o Azure Rights Management](install-powershell.md).

Quando estiver pronto para desativar o serviço Azure Rights Management na sua organização, utilize as instruções que se seguem.

## <a name="deactivating-rights-management"></a>Desativar o Rights Management
Utilize um dos seguintes procedimentos para desativar o [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Também pode utilizar o cmdlet do Windows PowerShell, [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), para desativar o [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Para desativar o Rights Management a partir do centro de administração do Office 365

1. Aceda à [página do Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) para administradores do Office 365.
    
    Se lhe for pedido para iniciar sessão, utilize uma conta que seja um administrador global do Office 365.    

2. Na página **gestão de direitos**, clique em **desativar**.

3.  Quando lhe for perguntado **Pretende desativar o Rights Management?**, clique em **desativar**.

Já deverá estar visível **O Rights Management não está ativado** e a opção para ativar.

#### <a name="to-deactivate-rights-management-from-the-azure-classic-portal"></a>Para desativar o Rights Management a partir do portal clássico do Azure

1.  Inicie sessão no [portal clássico do Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  No painel esquerdo, clique em **ACTIVE DIRECTORY**.

3.  Na página **active directory**, clique em **RIGHTS MANAGEMENT**.

4.  Confirme se o nome do inquilino está selecionado, clique em **DESATIVAR** e, em seguida, confirme a ação.

O **ESTADO DO RIGHTS MANAGEMENT** deverá agora apresentar **Inativo** e a opção **DESATIVAR** é substituída por **ATIVAR**.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


