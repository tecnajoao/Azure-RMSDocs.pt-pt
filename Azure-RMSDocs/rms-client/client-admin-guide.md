---
title: Guia do administrador do cliente do Azure Information Protection
description: "Instruções e informações para administradores numa rede empresarial responsáveis por implementar o cliente do Azure Information Protection para o Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/26/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 74abbe0db07a155afe500388810945a3ff5a35a5
ms.sourcegitcommit: 3ff6c072a228994308402778c493727cc682c6b7
translationtype: HT
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

O cliente do Azure Information Protection é mais adequado para funcionar com os respetivos serviços do Azure; o Azure Information Protection e o respetivo serviço de proteção de dados, o Azure Rights Management. No entanto, com algumas limitações, o cliente do Azure Information Protection também funciona com a versão no local do Rights Management, o AD RMS. Para ver uma comparação detalhada das funcionalidades suportadas pelo Azure Information Protection e pelo AD RMS, veja [Comparar o Azure Information Protection e o AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). 

Se tiver o AD RMS e quiser migrar para o Azure Information Protection, veja [Migrar do AD RMS para o Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

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

![Barra do Azure Information Protection com a política predefinida](../media/word2016-calloutsv2.png)

## <a name="how-to-install-the-azure-information-protection-client-for-users"></a>Como instalar o cliente do Azure Information Protection para os utilizadores

Antes de instalar o cliente, verifique se tem as versões de sistema operativo e as aplicações necessárias para o cliente do Azure Information Protection: [Requisitos do Azure Information Protection](../get-started/requirements-azure-rms.md). 

Pré-requisitos adicionais para o cliente do Azure Information Protection:

- A instalação completa do cliente do Azure Information Protection requer, por predefinição, a versão mínima do Microsoft .NET Framework 4.6.2 e, se estiver em falta, o instalador tentará transferir e instalar este pré-requisito. Quando este pré-requisito é instalado como parte da instalação do cliente, o computador tem de ser reiniciado. Embora não seja recomendado, pode ignorar este pré-requisito com um parâmetro de instalação personalizada.

- Se o Visualizador do Azure Information Protection for instalado à parte, precisará da versão mínima do Microsoft .NET Framework 4.5.2 e, se esta estiver em falta, o instalador não a transfere nem a instala.

- O módulo do PowerShell requer o Windows PowerShell versão 4.0, que poderá ter de ser instalado em sistemas operativos mais antigos. Para obter mais informações, veja [Como Instalar o Windows PowerShell 4.0](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx). O instalador não verifica nem instala este pré-requisito automaticamente. Para verificar que versão do Windows PowerShell está a executar, escreva **$PSVersionTable** numa sessão do PowerShell.

- Os computadores que executem o Windows 7 Service Pack 1 requerem a KB 2533623. Para obter mais informações sobre esta atualização, veja [Aviso de Segurança da Microsoft: o carregamento de bibliotecas não seguro pode permitir a execução remota de códigos](https://support.microsoft.com/en-us/kb/2533623). Poderá instalar diretamente esta atualização ou ser substituída por outra atualização que a instala por si.
    
    Se esta atualização for obrigatória e não estiver instalada, a instalação do cliente avisa-o de que tem de ser instalada. Esta atualização pode ser instalada após a instalação do cliente, mas algumas ações serão bloqueadas e a mensagem é apresentada novamente.  

> [!NOTE]
> A instalação requer permissões administrativas locais.

O cliente Azure Information Protection também está incluído no catálogo Microsoft Update, pelo que pode instalar e atualizar o cliente utilizando qualquer serviço de atualização de software que utilize o catálogo. 

1. Transfira o cliente do Azure Information Protection a partir do [Centro de Transferências da Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 
    
    Se existir uma versão de pré-visualização disponível, mantenha esta versão apenas para teste. Não se destina a utilizadores finais num ambiente de produção. 

2. Para uma instalação predefinida, basta executar o ficheiro **AzInfoProtection.exe**, por exemplo. Porém, para ver as opções de instalação, execute primeiro o ficheiro com **/help**: `AzInfoProtection.exe /help`

    Exemplo de como instalar automaticamente o cliente: `AzInfoProtection.exe /quiet`
    
    Exemplo de como instalar automaticamente apenas os cmdlets do PowerShell: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
    
    Parâmetros adicionais que não estão listados no ecrã de ajuda:
    
    - **ServiceLocation**: utilize este parâmetro se estiver a instalar o cliente em computadores com o Office 2010 e se os utilizadores não forem administradores locais nos computadores deles ou se não quiser que lhes seja pedido. [Mais informações](#more-information-about-the-servicelocation-installation-parameter) 
    
    - **DowngradeDotNetRequirement**: utilize este parâmetro para ignorar o requisito para o Microsoft Framework .NET versão 4.6.2. [Mais informações](#more-information-about-the-downgradedotnetrequirement-installation-parameter)

3. Se estiver a instalar interativamente, selecione a opção para instalar uma **política de demonstração** se não puder ligar-se ao Office 365 ou ao Azure Active Directory e quiser ver e experimentar o lado do cliente do Azure Information Protection com uma política local para efeitos de demonstração. Quando o cliente se liga a um serviço Azure Information Protection, esta política de demonstração é substituída pela política do Azure Information Protection da organização.
    
4. Para concluir a instalação: 

    - Se o computador estiver a executar o Office 2010, reinicie o computador. 
        
        Se o cliente não tiver sido instalado com o parâmetro ServiceLocation, quando abre uma das aplicações do Office que utilizam a barra do Azure Information Protection (por exemplo, o Word) pela primeira vez, terá de confirmar todos os pedidos para atualizar o registo para esta primeira utilização. A [deteção do serviço](../rms-client/client-deployment-notes.md#rms-service-discovery) é utilizada para preencher as chaves de registo. 
    
    - Para outras versões do Office, reinicie todas as aplicações do Office e todas as instâncias do Explorador de Ficheiros. 
        
5. Pode confirmar que a instalação foi concluída com êxito ao verificar o ficheiro de registo de instalação que, por predefinição, é criado na pasta %temp%. Pode alterar esta localização com o parâmetro de instalação **/log**. 
 
    Este ficheiro tem o seguinte formato de nomes: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`
    
    Por exemplo: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    Procure a seguinte cadeia neste ficheiro de registo: **Product: Microsoft Azure Information Protection -- Installation completed successfully.** Se a instalação falhou, este ficheiro de registo contém detalhes que o ajudam a identificar e resolver qualquer tipo de problemas.

### <a name="more-information-about-the-servicelocation-installation-parameter"></a>Mais informações sobre o parâmetro de instalação ServiceLocation

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


### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>Mais informações sobre o parâmetro de instalação DowngradeDotNetRequirement

Para suportar as atualizações automáticas através do Windows Update e para integração fiável com aplicações do Office, o cliente do Azure Information Protection utiliza o Microsoft .NET Framework versão 4.6.2. Por predefinição, a instalação procura esta versão e tenta instalá-la se estiver em falta. A instalação exige então que o computador seja reiniciado.

Se a instalação desta versão posterior do Microsoft .NET Framework não for conveniente, poderá instalar o cliente com o parâmetro e valor **DowngradeDotNetRequirement=True**, que ignorará este requisito se o Microsoft .NET Framework 4.5.1 estiver instalado.

Por exemplo: `AzInfoProtection.exe DowngradeDotNetRequirement=True`

Recomendamos que utilize este parâmetro com cuidado e com o conhecimento de que existem problemas comunicados com aplicações do Office pendentes quando o cliente do Azure Information Protection é utilizado com esta versão mais antiga do Microsoft .NET Framework. Se surgirem problemas de aplicações pendentes, atualize para a versão recomendada antes de experimentar outras soluções para resolução de problemas. 

Lembre-se também de que, se utilizar o Windows Update para manter atualizado o cliente do Azure Information Protection, vai precisar de outro mecanismo de implementação de software para atualizar o cliente para versões posteriores.

## <a name="additional-checks-and-troubleshooting"></a>Verificações adicionais e resolução de problemas

Utilize a opção **Ajuda e Feedback** para abrir a caixa de diálogo **Microsoft Azure Information Protection**:

- A partir de uma aplicação do Office: no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, selecione **Ajuda e Feedback**.

- No Explorador de Ficheiros: selecione com o botão direito do rato um ficheiro, ficheiros ou pasta, selecione **Classificar e proteger** e, em seguida, selecione **Ajuda e Feedback**. 

### <a name="help-and-feedback-section"></a>Secção **Ajuda e Feedback**

A **ligação Mais informações** direciona-o, por predefinição, para o site do [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection), mas pode ser configurada para um URL personalizado, de acordo com uma das [definições da política](../deploy-use/configure-policy-settings.md) da política do Azure Information Protection.

Utilize a ligação **Enviar Comentários** para enviar pedidos ou sugestões para a equipa do Information Protection. Não utilize esta opção para o suporte técnico e, em vez disso, veja [Opções de suporte e recursos da comunidade](../get-started/information-support.md#support-options-and-community-resources). 

**Exportar Registos** serve para recolher e anexar automaticamente ficheiros de registo para o cliente de Azure Information Protection se lhe tiver sido pedido para os enviar ao Suporte da Microsoft. Esta opção também serve para os utilizadores finais enviarem estes ficheiros de registo ao suporte técnico.

Para ver as informações de diagnóstico e para repor o cliente, selecione **Executar diagnósticos**. Quando os testes de diagnóstico forem concluídos, clique em **Copiar Resultados** para colar as informações num e-mail que pode enviar ao Suporte da Microsoft ou os utilizadores podem enviar ao seu suporte técnico. Quando os testes forem concluídos, também pode repor o cliente.

Mais informações acerca da opção **Repor**:

- Não precisa de ser um administrador local para utilizar esta opção e esta ação não é registada no Visualizador de Eventos. 

- A menos que os ficheiros estejam bloqueados, esta ação elimina todos os ficheiros existentes em **%localappdata%\Microsoft\MSIPC**, que é o local onde os certificados de cliente e os modelos de gestão de direitos estão armazenados. Não elimina a política do Azure Information Protection ou os ficheiros de registo de clientes nem termina a sessão do utilizador.

- A chave de registo e definições seguintes são eliminadas: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Caso configure definições para esta chave de registo (por exemplo, definições de redirecionamento para o seu inquilino do Azure Information Protection porque está a migrar do AD RMS e ainda tem um Ponto de Ligação de Serviço na sua rede), tem de voltar a configurar as definições de registo após efetuar a reposição do cliente.

- Depois da reposição do cliente, tem de reinicializar o ambiente do utilizador, o que irá transferir para o cliente certificados e os modelos mais recentes. Para o fazer, feche todas as instâncias do Office e, em seguida, reinicie uma aplicação do Office. Esta ação também irá verificar se transferiu a política do Azure Information Protection mais recente. Não execute novamente os testes de diagnóstico até ter efetuado esta ação.


### <a name="client-status-section"></a>Secção **Estado de cliente**

Utilize o valor **Ligado como** para confirmar que o nome de utilizador apresentado identifica a conta a ser utilizada para autenticação do Azure Information Protection. Este nome de utilizador tem de corresponder a uma conta que serve para o Office 365 ou o Azure Active Directory e que pertence a um inquilino configurado para o Azure Information Protection.

Se precisar de iniciar sessão como um utilizador diferente do apresentado, veja a secção [Iniciar sessão como um utilizador diferente](#sign-in-as-a-different-user) nesta página.

**Última ligação** apresenta quando o cliente se ligou pela última vez ao serviço do Azure Information Protection da sua organização e pode ser utilizada com a data e hora em que **a política do Information Protection foi instalada** para confirmar quando a política do Azure Information Protection foi instalada ou atualizada pela última vez. Quando o cliente se liga ao serviço, será transferida automaticamente a política mais recente se forem detetadas alterações em relação à política atual e, também, a cada 24 horas. Se tiver efetuado alterações de política após a hora apresentada, feche e reabra a aplicação do Office.

Se vir **O cliente não está licenciado para o Office Professional Plus**: significa que o cliente do Azure Information Protection detetou que a edição instalada do Office não suporta a aplicação da proteção Rights Management. Quando esta deteção é feita, as etiquetas que aplicam a proteção não são apresentadas na barra do Azure Information Protection.

Utilize as informações da **Versão** para confirmar que versão do cliente está instalada. Pode verificar se esta é a versão mais recente, bem como as correções correspondentes e as novas funcionalidades, ao clicar na ligação **Novidades**, para ler o [Histórico do Lançamento de Versões](client-version-release-history.md) do cliente.

## <a name="custom-configurations"></a>Configurações personalizadas

Utilize as seguintes informações para as configurações avançadas que poderá precisar para cenários específicos ou um subconjunto de utilizadores. 

### <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Impedir pedidos de início de sessão para computadores só com AD RMS

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection. Para computadores que só comunicam com AD RMS, isto pode resultar num pedido desnecessário de início de sessão aos utilizadores. Pode impedir este pedido de início de sessão ao editar o registo:

Localize o nome do valor seguinte e, em seguida, defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Independentemente desta definição, o cliente do Azure Information Protection segue o [processo de deteção do serviço RMS](../rms-client/client-deployment-notes.md#rms-service-discovery) padrão, para localizar o respetivo cluster AD RMS.

### <a name="sign-in-as-a-different-user"></a>Iniciar sessão como um utilizador diferente

Num ambiente de produção, normalmente, os utilizadores não precisam de iniciar sessão como um utilizador diferente quando estão a utilizar o cliente do Azure Information Protection. No entanto, poderá ter de o fazer como administrador se tiver vários inquilinos. Por exemplo, tem um inquilino de teste além do inquilino do Office 365 ou do Azure que a sua organização utiliza.

Pode verificar com que conta tem sessão iniciada atualmente através da caixa de diálogo do **Microsoft Azure Information Protection**: abra uma aplicação do Office e, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e comentários**. O nome da sua conta é apresentado na secção **Estado do cliente**.

Especialmente quando estiver a utilizar uma conta de administrador, verifique o nome de domínio da conta com sessão iniciada que é apresentada. Por exemplo, se tiver uma conta de administrador em dois inquilinos diferentes, pode não perceber que tem sessão iniciada com o nome da conta certo, mas com o domínio errado. Um sinal de tal engano pode ser a impossibilidade de transferir a política do Azure Information Protection ou não ver as etiquetas ou o comportamento esperado.

Para iniciar sessão como um utilizador diferente:

1. Com um editor de registo, navegue até **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP** e elimine o valor **TokenCache** (e os dados do valor associados).

2. Reinicie as aplicações do Office abertas e inicie sessão com a sua conta de utilizador diferente. Se não vir um pedido na aplicação do Office para iniciar sessão no serviço Azure Information Protection, volte à caixa de diálogo do **Microsoft Azure Information Protection** e clique em **Iniciar sessão** na secção **Estado do cliente** atualizada.

Além disso,

- Se estiver a utilizar o início de sessão único, terá de terminar sessão no Windows e iniciar sessão com a sua outra conta de utilizador após editar o registo. O cliente do Azure Information Protection fará a autenticação automaticamente através da conta de utilizador com sessão iniciada.

- Se pretender reinicializar o ambiente do serviço Azure Rights Management (também conhecido como arranque do sistema), pode fazê-lo através da opção **Repor** da [ferramenta RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Se pretender eliminar a política do Azure Information Protection atualmente transferida, elimine o ficheiro **Policy.msip** da pasta **%localappdata%\Microsoft\MSIP**.

### <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ocultar a opção de menu Classificar e Proteger no Explorador de Ficheiros do Windows

Pode configurar esta configuração avançada ao editar o registo quando tiver a versão do cliente do Azure Information Protection 1.3.0.0 ou superior. 

Crie o nome do valor DWORD seguinte (com quaisquer dados do valor):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

### <a name="support-for-disconnected-computers"></a>Suporte para computadores desligados

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection para transferir a política do Azure Information Protection mais recente. Se tiver um computador que sabe que não poderá estabelecer ligação à Internet durante um período de tempo, poderá impedir o cliente de tentar estabelecer ligação ao serviço ao editar o registo. Localize o nome do valor seguinte e defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Confirme se o cliente tem um ficheiro de política válido denominado **Policy.msip** na pasta **%localappdata%\Microsoft\MSIP**. Se necessário, pode exportar a política a partir do portal do Azure e copiar o ficheiro exportado para o computador cliente. Também pode utilizar este método para substituir um ficheiro de política desatualizada pela política publicada mais recente.

## <a name="to-uninstall-the-azure-information-protection-client"></a>Para instalar o cliente do Azure Information Protection

Pode utilizar uma das seguintes opções:

- Utilize o Painel de Controlo para desinstalar um programa: clique em **Microsoft Azure Information Protection** > **Desinstalar**

- Volte a executar o ficheiro executável (por exemplo, **AzInfoProtection.exe**) e, na página **Modificar Configuração**, clique em **Desinstalar**. 

- Execute o ficheiro executável com **/uninstall**. Por exemplo: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Próximos passos
Agora que instalou o cliente do Azure Information Protection, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
