---
title: Guia do administrador do cliente do Azure Information Protection
description: "Instruções e informações para administradores numa rede empresarial responsáveis por implementar o cliente do Azure Information Protection para o Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: b6a8477078a333aa23ccfe5904af3582216a1e96
ms.lasthandoff: 02/24/2017


---


# <a name="azure-information-protection-client-administrator-guide"></a>Guia do administrador do cliente do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8 e Windows 7 com SP1*


Utilize as seguintes informações se for responsável pelo cliente do Azure Information Protection numa rede empresarial ou se pretender mais informações técnicas além das que estão no [Guia do utilizador do cliente do Azure Information Protection](client-user-guide.md).

O cliente do Azure Information Protection inclui o seguinte:

- Um suplemento do Office, que instala a barra do Azure Information Protection para os utilizadores selecionarem etiquetas de classificação e um botão **Proteger** no friso para opções adicionais.

- Opções de clique com o botão direito do rato do Explorador de Ficheiros do Windows para os utilizadores aplicarem etiquetas de classificação e proteção a ficheiros.

- Um visualizador para apresentar ficheiros protegidos quando uma aplicação nativa não consegue abri-los.

- Um módulo do PowerShell para aplicar e remover etiquetas de classificação e proteção de ficheiros.

- O cliente do Rights Management que comunica com o Azure Rights Management (Azure RMS) ou os Serviços de Gestão de Direitos do Active Directory (AD RMS).

O cliente do Azure Information Protection é mais adequado para funcionar com os respetivos serviços do Azure; o Azure Information Protection e o respetivo serviço de proteção de dados, o Azure Rights Management. No entanto, com algumas limitações, o cliente do Azure Information Protection também funciona com a versão no local do Rights Management, o AD RMS. Para ver uma comparação detalhada das funcionalidades suportadas pelo Azure Information Protection e pelo AD RMS, consulte [Comparar o Azure Information Protection e o AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). Se tiver o AD RMS e quiser migrar para o Azure Information Protection, consulte [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

**Tem uma pergunta que não foi respondida por esta documentação?** Visite o nosso [site Yammer do Azure Information Protection](https://www.yammer.com/AskIPTeam). 


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Deve implementar o cliente do Azure Information Protection?

Implemente o cliente do Azure Information Protection no caso de se aplicar alguma das seguintes condições:

- Quer classificar (e, opcionalmente, proteger) documentos e e-mails ao selecionar etiquetas a partir das suas aplicações do Office (Word, Excel, PowerPoint, Outlook).

- Quer classificar (e, opcionalmente, proteger) documentos e e-mails através do Explorador de Ficheiros, que suporta outros tipos de ficheiro, a seleção múltipla e as pastas.

- Quer executar scripts que classificam (e, opcionalmente, protegem) documentos ao utilizar comandos do PowerShell.

- Quer ver documentos protegidos quando uma aplicação nativa para apresentar o ficheiro não está instalada ou não consegue abrir estes documentos.

- Quer apenas proteger os ficheiros através do Explorador de Ficheiros ou através de comandos do Powershell.

- Quer que os utilizadores e os administradores possam monitorizar e revogar documentos protegidos.

- Quer remover a encriptação dos ficheiros e contentores (desproteger) em massa para fins de recuperação de dados.

- Utiliza o Office 2010 e quer proteger documentos e e-mails através do serviço Azure Rights Management.

Exemplo que mostra o suplemento do cliente do Azure Information Protection em aplicações do Office a apresentar as etiquetas de classificação para a sua organização e o novo botão **Proteger** no friso:

![Barra do Azure Information Protection com a política predefinida](../media/info-protect-bar-default.png)

## <a name="how-to-install-the-azure-information-protection-client-for-users"></a>Como instalar o cliente do Azure Information Protection para os utilizadores

Antes de instalar o cliente, verifique se tem as versões de sistema operativo e as aplicações necessárias para o cliente do Azure Information Protection: [Requisitos do Azure Information Protection](../get-started/requirements-azure-rms.md). 

Além disso:

- A instalação completa do cliente do Azure Information Protection requer a versão mínima do Microsoft .NET Framework 4.6.2 e, se esta estiver em falta, o instalador tentará transferir e instalar este pré-requisito. Quando este pré-requisito é instalado como parte da instalação do cliente, o computador tem de ser reiniciado.

- Se o Visualizador do Azure Information Protection for instalado à parte, precisará da versão mínima do Microsoft .NET Framework 4.5.2 e, se esta estiver em falta, o instalador não a transfere nem a instala.

- O módulo do PowerShell requer o Windows PowerShell versão 4.0, que poderá ter de ser instalado em sistemas operativos mais antigos. Para obter mais informações, consulte [Como Instalar o Windows PowerShell 4.0](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx). Para verificar que versão do Windows PowerShell está a executar, escreva **$PSVersionTable** numa sessão do PowerShell.

- Os computadores com o Windows 7 Service Pack 1 instalado requerem o [KB 2533623](https://support.microsoft.com/en-us/kb/2533623), que pode ser instalado após a instalação do cliente. Se esta atualização for exigida, mas não estiver instalada, ser-lhe-á pedido que a instale.

> [!NOTE]
> A instalação requer permissões administrativas locais.

Além de utilizar as seguintes instruções, o cliente do Azure Information Protection também está incluído no catálogo Microsoft Update, pelo que pode instalar e atualizar o cliente com qualquer serviço de atualização de software que utilize o catálogo. 

1. Transfira o cliente do Azure Information Protection a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 

2. Para uma instalação predefinida, basta executar o ficheiro **AzInfoProtection.exe**. Porém, para ver as opções de instalação, execute primeiro o ficheiro com **/help**: `AzInfoProtection.exe /help`

   Exemplo de como instalar automaticamente o cliente: `AzInfoProtection.exe /quiet`
   
   Exemplo de como instalar automaticamente apenas os cmdlets do PowerShell: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
   
   Além disso, se estiver a instalar o cliente em computadores com o Office 2010, tem de especificar o parâmetro **ServiceLocation** (não incluído no ecrã de ajuda) caso os utilizadores não sejam administradores locais nos computadores. Veja a secção seguinte para obter mais informações.

3. Se estiver a instalar interativamente, selecione a opção para instalar uma **política de demonstração** se não puder ligar-se ao Office 365 ou ao Azure Active Directory e quiser ver e experimentar o lado do cliente do Azure Information Protection com uma política local para efeitos de demonstração. Quando o cliente se liga a um serviço Azure Information Protection, esta política de demonstração é substituída pela política do Azure Information Protection da organização.
    
4. Para concluir a instalação: 

    - Se o computador estiver a executar o Office 2010, reinicie o computador. 
        
        Se o cliente não tiver sido instalado com o parâmetro ServiceLocation, quando abre uma das aplicações do Office que utilizam a barra do Azure Information Protection (por exemplo, o Word) pela primeira vez, terá de confirmar todos os pedidos para atualizar o registo para esta primeira utilização. A [deteção do serviço](../rms-client/client-deployment-notes.md#rms-service-discovery) é utilizada para preencher as chaves de registo. 
    
    - Para outras versões do Office, reinicie todas as aplicações do Office e todas as instâncias do Explorador de Ficheiros. 
        
5. Pode confirmar que a instalação foi concluída com êxito ao verificar o ficheiro de registo de instalação na pasta %temp%. Este ficheiro tem o seguinte formato de nomes: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`. Por exemplo: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    Procure a seguinte cadeia neste ficheiro de registo: **Product: Microsoft Azure Information Protection -- Installation completed successfully.**

### <a name="additional-instructions-for-office-2010-only"></a>Instruções adicionais apenas para o Office 2010

Quando instala o cliente para utilizadores que têm o Office 2010 e não têm permissões administrativas locais, especifique o parâmetro ServiceLocation e o URL para o serviço Azure Rights Management. O parâmetro e o valor criam e definem as seguintes chaves de registo:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

Utilize o seguinte procedimento para identificar o valor a especificar para o parâmetro ServiceLocation. 

#### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>Para identificar o valor a especificar para o parâmetro ServiceLocation

1. A partir de uma sessão do PowerShell, primeiro execute [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice) e especifique as suas credenciais de administrador para ligar ao serviço Azure Rights Management. Em seguida, execute [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration). 
 
    Se ainda não tiver instalado o módulo do PowerShell para o serviço Azure Rights Management, veja [Instalar o Windows PowerShell para o Azure Rights Management](../deploy-use/install-powershell.md).

2. A partir da saída, identifique o valor **LicensingIntranetDistributionPointUrl**.

    Por exemplo: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. No valor, remova **/_wmcs/licensing** desta cadeia. Por exemplo: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    A cadeia restante é o valor a especificar para o parâmetro ServiceLocation.

Exemplo de como instalar automaticamente o cliente para o Office 2010 e para o Azure RMS: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


## <a name="to-uninstall-the-azure-information-protection-client"></a>Para instalar o cliente do Azure Information Protection

Pode utilizar uma das seguintes opções:

- Utilize o Painel de Controlo para desinstalar um programa: clique em **Microsoft Azure Information Protection** > **Desinstalar**

- Volte a executar o ficheiro executável (por exemplo, **AzInfoProtection.exe**) e, na página **Modificar Configuração**, clique em **Desinstalar**. 

- Execute o ficheiro executável com **/uninstall**. Por exemplo: `AzInfoProtection.exe /uninstall`


## <a name="to-verify-installation-connection-status-or-send-feedback"></a>Para verificar a instalação, o estado da ligação ou enviar comentários

1. Abra uma aplicação do Office, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e feedback**.

2. Na caixa de diálogo **Microsoft Azure Information Protection**, tenha em consideração o seguinte:

    - Na secção **estado do cliente**: utilize o valor **Versão** para verificar que a instalação foi efetuada com êxito. Para além disso, pode ver quando é que o cliente se ligou ao serviço Azure Information Protection da sua organização pela última vez e quando é que a política do Azure Information Protection foi instalada ou atualizada pela última vez. Quando o cliente se liga ao serviço, é transferida automaticamente a política mais recente se forem detetadas alterações em relação à política atual. Se tiver efetuado alterações de política após a hora apresentada, feche e reabra a aplicação do Office.
    
        Também o seu nome de utilizador apresentado, que identifica a conta utilizada para o autenticar no Azure Information Protection. Este nome de utilizador tem de corresponder a uma conta que utiliza para o Office 365 ou o Azure Active Directory e que pertence a um inquilino configurado para o Azure Information Protection.

    - Na secção **Ajuda e feedback**: a **ligação Mais informações** direciona-o, por predefinição, para o site do [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection), mas pode ser configurada para um URL personalizado, de acordo com uma das [definições da política](../deploy-use/configure-policy-settings.md) da política do Azure Information Protection.
        
        Utilize a ligação **Enviar comentários** para enviar pedidos ou sugestões para a equipa do Information Protection. Não utilize esta opção para o suporte técnico e, em vez disso, veja [Opções de suporte e recursos da comunidade](../get-started/information-support.md#support-options-and-community-resources). 
    
        Para ver as informações de diagnóstico e para repor o cliente, clique em **Executar diagnósticos**. Quando os testes de diagnóstico forem concluídos, clique em **Copiar Resultados** para colar as informações num e-mail que pode enviar em seguida para o seu apoio técnico ou para o suporte da Microsoft. Quando os testes forem concluídos, também pode repor o cliente.
        
        Mais informações acerca da opção **Repor**:
        
        - Não precisa de ser um administrador local para utilizar esta opção e esta ação não é registada no Visualizador de Eventos. 
        
        - A menos que os ficheiros estejam bloqueados, esta ação elimina todos os ficheiros existentes em **%localappdata%\Microsoft\MSIPC**, que é o local onde os certificados de cliente e os modelos de gestão de direitos estão armazenados. Não elimina a política do Azure Information Protection ou os ficheiros de registo de clientes nem termina a sessão do utilizador.
        
        - A chave de registo e definições seguintes são eliminadas: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Caso configure definições para esta chave de registo (por exemplo, definições de redirecionamento para o seu inquilino do Azure Information Protection porque está a migrar do AD RMS e ainda tem um Ponto de Ligação de Serviço na sua rede), tem de voltar a configurar as definições de registo após efetuar a reposição do cliente.
        
        - Caso tenha efetuado a reposição do cliente, tem de reiniciar o ambiente do utilizador (também conhecido como "bootstrapping"), o que irá transferir para o cliente certificados e os modelos mais recentes. Para o fazer, feche todas as instâncias do Office e, em seguida, reinicie uma aplicação do Office. Esta ação também irá verificar se transferiu a política do Azure Information Protection mais recente. Não execute novamente os testes de diagnóstico até ter efetuado esta ação.


## <a name="next-steps"></a>Passos seguintes
Agora que instalou o cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]

