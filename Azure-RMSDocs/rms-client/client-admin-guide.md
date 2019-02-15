---
title: Guia do administrador do cliente do Azure Information Protection
description: Instruções e informações para administradores numa rede empresarial responsáveis por implementar o cliente do Azure Information Protection para o Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 01/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 33a5982f-7125-4031-92c2-05daf760ced1
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: a0addbf7d4e613ab49ea29e750fd67a3b8ef1793
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254582"
---
# <a name="azure-information-protection-client-administrator-guide"></a>Guia do administrador do cliente do Azure Information Protection

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilize as informações deste guia se for responsável pelo cliente do Azure Information Protection numa rede empresarial ou se pretender mais informações técnicas além das que estão no [Guia do utilizador do cliente do Azure Information Protection](client-user-guide.md). 

Por exemplo:

- Entender os diferentes componentes do cliente e se o deve instalar

- Como instalar o cliente para utilizadores, com informações sobre pré-requisitos, opções de instalação e parâmetros e verificações

- Como inserir configurações personalizadas que muitas vezes exigem a edição do registo

- Encontre os ficheiros de cliente e registos de utilização

- Identifique os tipos de ficheiro suportados pelo cliente

- Configure e utilize o site de controlo de documentos para os utilizadores

- Utilize o cliente com o PowerShell para controlo de linha de comandos

**Tem uma pergunta que não foi respondida nesta documentação?** Visite o nosso [site Yammer do Azure Information Protection](https://www.yammer.com/AskIPTeam). 

## <a name="technical-overview-of-the-azure-information-protection-client"></a>Descrição geral técnica sobre o cliente do Azure Information Protection

O cliente do Azure Information Protection inclui o seguinte:

- Um suplemento para Office, que instala a barra do Azure Information Protection para os utilizadores selecionarem etiquetas de classificação, e um **Protect** botão da faixa de opções para obter opções adicionais. Para o Outlook, uma **não reencaminhar** botão também está disponível para a faixa de opções.

- Opções de clique com o botão direito do rato do Explorador de Ficheiros do Windows para os utilizadores aplicarem etiquetas de classificação e proteção a ficheiros.

- Um visualizador para apresentar ficheiros protegidos quando uma aplicação nativa não consegue abri-los.

- Um módulo do PowerShell para aplicar e remover etiquetas de classificação e proteção de ficheiros. 
    
    Este módulo inclui cmdlets para instalar e configurar o [scanner do Azure Information Protection](../deploy-aip-scanner.md) que é executado como um serviço no Windows Server. Este serviço permite-lhe detetar, classificar e proteger ficheiros em arquivos de dados, como compartilhamentos de rede e de bibliotecas do SharePoint Server.

- O cliente do Rights Management que comunica com o Azure Rights Management (Azure RMS) ou os Serviços de Gestão de Direitos do Active Directory (AD RMS).

O cliente do Azure Information Protection é mais adequado para funcionar com os respetivos serviços do Azure; o Azure Information Protection e o respetivo serviço de proteção de dados, o Azure Rights Management. No entanto, com algumas limitações, o cliente do Azure Information Protection também funciona com a versão no local do Rights Management, o AD RMS. Para ver uma comparação detalhada das funcionalidades suportadas pelo Azure Information Protection e pelo AD RMS, veja [Comparar o Azure Information Protection e o AD RMS](../compare-on-premise.md). 

Se tiver o AD RMS e quiser migrar para o Azure Information Protection, consulte [Migrar do AD RMS para o Azure Information Protection](../migrate-from-ad-rms-to-azure-rms.md).


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Deve implementar o cliente do Azure Information Protection?

Implemente o cliente do Azure Information Protection no caso de se aplicar alguma das seguintes condições:

- Quer classificar (e, opcionalmente, proteger) documentos e e-mails ao selecionar etiquetas a partir das suas aplicações do Office (Word, Excel, PowerPoint, Outlook).

- Pretende classificar (e, opcionalmente, proteger) ficheiros ao utilizar o Explorador de ficheiros, oferecendo suporte a tipos de ficheiro adicionais que são suportados pelo Office, a seleção múltipla e pastas.

- Quer executar scripts que classificam (e, opcionalmente, protegem) documentos ao utilizar comandos do PowerShell.

- Pretende executar um serviço que Deteta, classifica (e, opcionalmente, protege) ficheiros que estão armazenados no local.

- Quer ver documentos protegidos quando uma aplicação nativa para apresentar o ficheiro não está instalada ou não consegue abrir estes documentos.

- Quer apenas proteger os ficheiros através do Explorador de Ficheiros ou através de comandos do PowerShell.

- Quer que os utilizadores e os administradores possam monitorizar e revogar documentos protegidos.

- Quer remover a encriptação dos ficheiros e contentores (desproteger) em massa para fins de recuperação de dados.

- Utiliza o Office 2010 e quer proteger documentos e e-mails através do serviço Azure Rights Management.

Exemplo que mostra o cliente do Azure Information Protection add-in para uma aplicação do Office, apresentar as etiquetas de classificação para a sua organização e a nova **Protect** botão na faixa de opções:

![Barra do Azure Information Protection com a política predefinida](../media/word2016-calloutsv2.png)

## <a name="installing-and-supporting-the-azure-information-protection-client"></a>Instalar e suporte ao cliente Azure Information Protection

Pode instalar o cliente do Azure Information Protection através de um executável ou um ficheiro de instalador do Windows. Para obter mais informações sobre cada opção e instruções, consulte [instalar o cliente do Azure Information Protection para utilizadores](client-admin-guide-install.md).  

Utilize as secções seguintes para informações sobre como instalar o cliente de suporte. 

### <a name="installation-checks-and-troubleshooting"></a>Verificações de instalação e resolução de problemas

Quando o cliente é instalado, utilize o **ajuda e Feedback** opção para abrir o **Microsoft Azure Information Protection** caixa de diálogo:

- A partir de uma aplicação do Office: Sobre o **home page** separador a **proteção** grupo, selecione **proteger**e, em seguida, selecione **ajuda e Feedback**.

- No Explorador de ficheiros: Direito-selecione um ficheiro, ficheiros ou pasta, selecione **classificar e proteger**e, em seguida, selecione **ajuda e Feedback**. 

#### <a name="help-and-feedback-section"></a>Secção **Ajuda e Feedback**

A **ligação Mais informações** direciona-o, por predefinição, para o site do [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection), mas pode configurá-la para um URL personalizado, de acordo com uma das [definições da política](../configure-policy-settings.md) da política do Azure Information Protection.

O **comunicar um problema** ligação mostra apenas se especificou um [definição de cliente avançado](client-admin-guide-customizations.md#add-report-an-issue-for-users). Quando configurar esta definição, especifique uma ligação HTTP, como o endereço de e-mail do suporte técnico.

**Exportar Registos** recolhe e anexa automaticamente ficheiros de registo para o cliente de Azure Information Protection se lhe tiver sido pedido para os enviar ao Suporte da Microsoft. Esta opção também serve para os utilizadores finais enviarem estes ficheiros de registo ao suporte técnico.

O **repor definições** encerrar a sessão do utilizador, elimina a política do Azure Information Protection atualmente transferida e repõe as definições de utilizador para o serviço Azure Rights Management.

##### <a name="more-information-about-the-reset-settings-option"></a>Obter mais informações sobre a opção de repor definições

- Não precisa de ser um administrador local para utilizar esta opção e esta ação não é registada no Visualizador de Eventos. 

- A menos que os ficheiros estejam bloqueados, esta ação elimina todos os ficheiros nas seguintes localizações. Estes ficheiros incluem certificados de cliente, modelos do Rights Management, a política do Azure Information Protection e as credenciais de utilizador em cache. Não são eliminados os ficheiros de registo de cliente.
    
    - %LocalAppData%\Microsoft\DRM
    
    - %LocalAppData%\Microsoft\MSIPC
    
    - %LocalAppData%\Microsoft\MSIP\Policy.msip
    
    - %LocalAppData%\Microsoft\MSIP\TokenCache

- As seguintes chaves do registo e definições são eliminadas. Se as definições de qualquer uma dessas chaves de registro tem valores personalizados, estes têm de ser reconfigurados depois de repor o cliente. 
    
    Normalmente, para redes corporativas, estas definições são configuradas utilizando a política de grupo, caso em que eles são serão automaticamente reaplicados quando a política de grupo é atualizada no computador. No entanto, poderão existir algumas definições que estão configuradas uma vez com um script ou configuradas manualmente. Nestes casos, tem de efetuar passos adicionais para reconfigurar estas definições. Por exemplo, computadores podem executar um script uma vez para configurar as definições de redirecionamento para o Azure Information Protection porque está a migrar do AD RMS e ainda tem um ponto de ligação de serviço na sua rede. Depois de a repor o cliente, o computador tem de executar este script novamente.
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\16.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Classes\Local Settings\Software\Microsoft\MSIPC    

- É terminada a sessão do utilizador com sessão iniciada atualmente.

#### <a name="client-status-section"></a>Secção **Estado de cliente**

Utilize o valor **Ligado como** para confirmar que o nome de utilizador apresentado identifica a conta a ser utilizada para autenticação do Azure Information Protection. Este nome de utilizador tem de corresponder a uma conta utilizada no Office 365 ou no Azure Active Directory. A conta também tem de pertencer a um inquilino configurado para o Azure Information Protection.

Se precisar de iniciar sessão como um utilizador diferente do apresentado, veja a personalização [Iniciar sessão como um utilizador diferente](client-admin-guide-customizations.md#sign-in-as-a-different-user).

A **Última ligação** mostra quando o cliente esteve ligado pela última vez ao serviço Azure Information Protection da organização. Pode utilizar esta informação com a data e hora apresentada em **A política do Information Protection foi instalada a** para confirmar quando foi a última vez em que a política do Azure Information Protection foi instalada ou atualizada. Quando o cliente se liga ao serviço, será transferida automaticamente a política mais recente se forem detetadas alterações em relação à política atual e, também, a cada 24 horas. Se tiver efetuado alterações de política após a hora apresentada, feche e reabra a aplicação do Office.

Se vir **o cliente não está licenciado para o Office Professional Plus**: O cliente do Azure Information Protection detetou que a edição instalada do Office não suporta a aplicação da proteção Rights Management. Quando esta deteção é feita, as etiquetas que aplicam a proteção não são apresentadas na barra do Azure Information Protection.

Utilize as informações da **Versão** para confirmar que versão do cliente está instalada. Pode verificar se esta é a versão mais recente, bem como as correções correspondentes e as novas funcionalidades, ao clicar na ligação **Novidades**, para ler o [Histórico do Lançamento de Versões](client-version-release-history.md) do cliente.

## <a name="support-for-multiple-languages"></a>Suporte para múltiplos idiomas

O cliente do Azure Information Protection suporta os mesmos idiomas que suporta o Office 365. Para obter uma lista de idiomas, consulte a **Office 365, o Exchange Online Protection e o Power BI** secção da [disponibilidade internacional](https://products.office.com/business/international-availability) página do Office.

Para estes idiomas, opções de menu, caixas de diálogo e mensagens do Azure Information Protection cliente apresentar no idioma do utilizador. Há um único instalador para Deteta o idioma, para que nenhuma configuração adicional é necessário para instalar o cliente do Azure Information Protection para diferentes idiomas. 

No entanto, os nomes de etiqueta e descrições que especificou não são traduzidas automaticamente quando configurar as etiquetas na política do Azure Information Protection. A partir do dia 30 de Agosto de 2017, o atual [política predefinida](../configure-policy-default.md) inclui suporte para alguns idiomas. Para os utilizadores verem as etiquetas em seu idioma preferencial, fornecem suas próprias traduções e configurar a política do Azure Information Protection para utilizar essas conversões. Para obter mais informações, veja [Como configurar etiquetas para diferentes idiomas no Azure Information Protection](../configure-policy-languages.md). Marcas visuais não são traduzidas e não suportam mais de um idioma.

## <a name="post-installation-tasks"></a>Tarefas de pós-instalação

Depois de instalar o cliente do Azure Information Protection, certifique-se de que dê instruções sobre os utilizadores como etiquetar os documentos e e-mails e orientação para as etiquetas escolher para cenários específicos. Por exemplo:

- Instruções de utilizador online: [Guia do utilizador do Azure Information Protection](client-user-guide.md)

- Baixe um guia do usuário personalizável: [Guia de adoção de utilizador final do Azure Information Protection](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf)

### <a name="update-macros-in-excel-spreadsheets"></a>Atualizar as macros do planilhas do Excel

Se tiver folhas de cálculo do Excel que contêm as macros, edite as macros da seguinte forma para garantir que continuam a funcionar como esperado após a instalação do cliente do Azure Information Protection:

1. No início da macro, adicione:

        Application.EnableEvents = False

2. No final da macro, adicione:

        Application.EnableEvents = True

Para obter mais informações, consulte [Application.EnableEvents propriedade (Excel)](https://msdn.microsoft.com/vba/excel-vba/articles/application-enableevents-property-excel).

## <a name="upgrading-and-maintaining-the-azure-information-protection-client"></a>Atualização e manutenção de cliente do Azure Information Protection

A equipa do Azure Information Protection atualiza regularmente o cliente do Azure Information Protection para novas funcionalidades e correções. Anúncios são lançados para a equipe [site do Yammer](https://www.yammer.com/AskIPTeam).

Se estiver a utilizar o Windows Update, o cliente do Azure Information Protection atualiza automaticamente a versão de disponibilidade geral do cliente, independentemente da forma como o cliente foi instalado. Novas versões de cliente são publicadas para o catálogo de poucas semanas após o lançamento.

Em alternativa, manualmente pode atualizar o cliente baixando a nova versão dos [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Em seguida, instale a nova versão para atualizar o cliente. Tem de utilizar este método para atualizar as versões de pré-visualização.

Quando tem de atualizar manualmente, desinstale primeiro a versão anterior apenas se estiver a alterar o método de instalação. Por exemplo, altera de versão do executável (.exe) do cliente para a versão do Windows installer (MSI) do cliente. Em alternativa, se precisar de instalar uma versão anterior do cliente. Por exemplo, tem a versão de pré-visualização atual instalada para testar e agora tem de reverter para a versão atual da disponibilidade geral.

Utilize o [política de histórico e suporte de lançamento de versão](client-version-release-history.md) para compreender a política de suporte para o cliente do Azure Information Protection, as versões que são atualmente suportadas e o que é a nova e alterada para as versões suportadas. 

### <a name="upgrading-the-azure-information-protection-scanner"></a>Atualizar o scanner do Azure Information Protection

Como atualizar o scanner depende se estiver a atualizar para a versão de DG atual ou para a versão de pré-visualização atual.

#### <a name="to-upgrade-the-scanner-to-the-current-ga-version"></a>Para atualizar o scanner para a versão atual do GA

Para atualizar o scanner do Azure Information Protection, instale a versão mais recente do cliente do Azure Information Protection. Em seguida, efetue a seguinte ação única. Depois de fazer isso, não é necessário para reanalisar já ficheiros.

- Execute [AIPScanner atualização](/powershell/module/azureinformationprotection/Update-AIPScanner) depois de ter atualizado o cliente do Azure Information Protection. As definições de configuração para o scanner e repositórios serão mantidas. Executar este cmdlet é necessário para atualizar o esquema de base de dados para a deteção de impressão e se necessário, a conta de serviço do scanner também recebe eliminar as permissões para a base de dados do scanner. 
    
    Até que executar este cmdlet de atualização, o scanner não é executado e verá o ID de evento normalmente **1000** no registo de eventos do Windows, com a seguinte mensagem de erro: **Nome de objeto inválido 'ScannerStatus'**.

#### <a name="to-upgrade-the-scanner-to-the-current-preview-version"></a>Para atualizar o scanner para a versão de pré-visualização atual

> [!IMPORTANT]
> Para um caminho de atualização suave, não instale a versão de pré-visualização do cliente do Azure Information Protection no computador com o scanner como o primeiro passo para atualizar o scanner. Em vez disso, utilize as seguintes instruções de atualização.

Para a versão de pré-visualização atual do scanner, o processo de atualização é diferente de versões anteriores. Atualizar o scanner automaticamente altera o scanner para obtém as definições de configuração do portal do Azure. Além disso, o esquema é atualizado para o banco de dados de configuração do scanner, e esta base de dados também é mudado da AzInfoProtection:

- Se não especificar o nome do seu perfil, a base de dados de configuração foi mudado **AIPScanner_\<nome_do_computador >**. 

- Se especificar o nome do seu perfil, a base de dados de configuração foi mudado **AIPScanner_\<Nome_do_perfil >**.

Embora seja possível atualizar o scanner numa ordem diferente, recomendamos os seguintes passos:

1. Utilize o portal do Azure para criar um novo perfil de scanner, que inclui definições para a deteção de impressão e seus repositórios de dados com as definições que precisam. Para obter ajuda com este passo, consulte a [configurar a deteção de impressão no portal do Azure](../deploy-aip-scanner-preview.md#configure-the-scanner-in-the-azure-portal) secção das instruções de implementação do Verificador de pré-visualização.
    
    Se o computador que executa a deteção de impressão estiver desligado da Internet, ainda tem de efetuar este passo. Em seguida, a partir do portal do Azure, utilize o **exportar** opção para exportar o seu perfil de scanner para um ficheiro.

2. No computador de scanner, pare o serviço de scanner, **do Azure Information Protection Scanner**.

3. Atualizar o cliente do Azure Information Protection ao instalar a versão de pré-visualização atual a partir da [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

4. Numa sessão do PowerShell, execute o comando de atualização AIPScanner com o mesmo nome de perfil que especificou no passo 1. Por exemplo: `Update-AIPScanner –Profile USWest`

5. Apenas se o scanner está em execução num computador desligado: Agora, execute [Import-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration) e especifique o ficheiro que contém as definições exportadas.

6. Reinicie o serviço de Azure Information Protection Scanner **do Azure Information Protection Scanner**.

##### <a name="upgrading-in-a-different-order-to-the-recommended-steps"></a>Atualização numa ordem diferente para os passos recomendados

Se não configurar a deteção de impressão no portal do Azure antes de executar o comando de atualização AIPScanner, não terá um nome de perfil para especificar que identifica as definições de configuração de scanner para o processo de atualização. 

Neste cenário, quando configurar a deteção de impressão no portal do Azure, tem de especificar exatamente o mesmo nome do perfil que foi utilizado quando executou o comando de atualização AIPScanner. Se o nome não corresponder, o scanner não será configurado para as suas definições. 

> [!TIP]
> Para identificar scanners que têm esta configuração incorreta, utilize o **do Azure Information Protection – nós** painel no portal do Azure.
>  
> Para scanners que tem ligação à Internet, eles exibem o respetivo nome de computador com o número de versão de pré-visualização do cliente do Azure Information Protection, mas nenhum nome de perfil. Apenas os scanners que têm um número de versão 1.41.51.0 não deverá apresentar a nenhum nome de perfil neste painel. 

Se não tiver especificado um nome de perfil quando executou o comando de atualização AIPScanner, o nome do computador é utilizado para criar automaticamente o nome de perfil para a deteção de impressão.

#### <a name="moving-the-scanner-configuration-database-to-a-different-sql-server-instance"></a>Mover a base de dados de configuração do scanner para uma instância diferente do SQL Server

Na versão de pré-visualização atual, existe um problema conhecido se tentar mover a base de dados de configuração do scanner para uma nova instância do SQL Server depois de executar o comando de atualização.

Se souber que pretende mover a base de dados de configuração de scanner para a versão de pré-visualização, faça o seguinte:

1. Desinstale o scanner utilizando [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner).

2. Se ainda não tiver atualizado para a versão de pré-visualização do cliente do Azure Information Protection, agora a atualizar o cliente.

3. Instalar o scanner, utilizando [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner), especificando a nova instância do SQL Server e nome de perfil.

4. Opcional: Se não pretender que o scanner para reanalisar todos os ficheiros, a tabela de ScannerFiles de exportar e importá-lo para a nova base de dados.

## <a name="uninstalling-the-azure-information-protection-client"></a>Desinstalar o cliente do Azure Information Protection

Pode usar qualquer uma das seguintes opções para desinstalar o cliente:

- Utilize o painel de controlo para desinstalar um programa: Clique em **do Microsoft Azure Information Protection** > **desinstalar**

- Volte a executar o ficheiro executável (por exemplo, **AzInfoProtection.exe**) e, na página **Modificar Configuração**, clique em **Desinstalar**. 

- Execute o ficheiro executável com **/uninstall**. Por exemplo: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Passos Seguintes
Para instalar o cliente, consulte [instalar o cliente do Azure Information Protection para utilizadores](client-admin-guide-install.md).

Se já tiver instalado o cliente, veja o seguinte para obter informações adicionais que poderá precisar para suportar este cliente:

- [Personalizações](client-admin-guide-customizations.md)

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


