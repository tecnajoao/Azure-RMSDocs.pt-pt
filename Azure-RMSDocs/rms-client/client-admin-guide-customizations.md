---
title: Configurações personalizadas do cliente do Azure Information Protection
description: Informações sobre a personalização do cliente do Azure Information Protection para Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/04/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: b4d0f104c0c0562f98c5418b9763adf62bdee97f
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44149780"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-client"></a>Guia do administrador: Configurações personalizadas para o cliente do Azure Information Protection

>*Aplica-se a: serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilize as seguintes informações para as configurações avançadas que poderá precisar para cenários específicos ou um subconjunto de utilizadores ao gerir o cliente do Azure Information Protection.

Algumas destas definições requerem a edição do registo e algumas utilizam definições avançadas que tem de configurar no portal do Azure e, em seguida, publicar para os clientes transferirem.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Como configurar as definições avançadas de configuração de cliente no portal

1. Se ainda não o tiver feito, numa nova janela do browser, [inicie sessão no portal do Azure](../configure-policy.md#signing-in-to-the-azure-portal)e, em seguida, navegue para o **do Azure Information Protection** painel.

2. Do **classificações** > **etiquetas** opção de menu: selecione **políticas**.

3. Sobre o **do Azure Information Protection - políticas** painel, selecione o menu de contexto (**...** ) junto à política que contém as definições avançadas. Em seguida, selecione **Definições avançadas**.
    
    Pode configurar as definições avançadas para a Política global, bem como para as políticas de âmbito.

4. No painel **Definições avançadas**, escreva o nome e o valor da definição avançada e, em seguida, selecione **Guardar e fechar**.

5. Certifique-se de que os utilizadores desta política reiniciam as aplicações do Office que tinham abertas.

6. Caso já não precise da definição e pretenda reverter para o comportamento predefinido: no painel **Definições avançadas**, selecione o menu de contexto (**...**) junto à definição que já não é precisa e, em seguida, selecione **Eliminar**. Em seguida, clique em **guarde e feche**.

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Impedir pedidos de início de sessão para computadores só com AD RMS

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection. Para computadores que só comunicam com AD RMS, esta configuração pode resultar num pedido desnecessário de início de sessão aos utilizadores. Pode impedir este pedido de início de sessão ao editar o registo:

Localize o nome do valor seguinte e, em seguida, defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Independentemente desta definição, o cliente do Azure Information Protection segue o [processo de deteção do serviço RMS](client-deployment-notes.md#rms-service-discovery) padrão, para localizar o respetivo cluster AD RMS.

## <a name="sign-in-as-a-different-user"></a>Iniciar sessão como um utilizador diferente

Num ambiente de produção, normalmente, os utilizadores não precisam de iniciar sessão como um utilizador diferente quando estão a utilizar o cliente do Azure Information Protection. No entanto, como administrador, poderá ter de iniciar sessão como um utilizador diferente durante uma fase de teste. 

Pode verificar com que conta tem sessão iniciada atualmente através da caixa de diálogo do **Microsoft Azure Information Protection**: abra uma aplicação do Office e, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e comentários**. O nome da sua conta é apresentado na secção **Estado do cliente**.

Confirme que também verifica o nome de domínio da conta com sessão iniciada que é apresentada. Pode não perceber que tem sessão iniciada com o nome da conta certo, mas com o domínio errado. Um sinal de utilização da conta errada inclui a impossibilidade de transferir a política do Azure Information Protection ou não ver as etiquetas ou o comportamento esperado.

Para iniciar sessão como um utilizador diferente:

1. Navegue para **%localappdata%\Microsoft\MSIP** e eliminar os **TokenCache** ficheiro.

2. Reinicie as aplicações do Office abertas e inicie sessão com a sua conta de utilizador diferente. Se não vir um pedido na aplicação do Office para iniciar sessão no serviço Azure Information Protection, volte à caixa de diálogo do **Microsoft Azure Information Protection** e clique em **Iniciar sessão** na secção **Estado do cliente** atualizada.

Além disso,

- esta solução é suportada para iniciar sessão como outro utilizador a partir do mesmo inquilino. Não é suportada para iniciar sessão como outro utilizador a partir de um inquilino diferente. Para testar o Azure Information Protection com vários inquilinos, utilize computadores diferentes.

- Se estiver a utilizar o início de sessão único, tem de terminar sessão no Windows e iniciar sessão com a sua outra conta de utilizador após editar o registo. O cliente do Azure Information Protection faz, em seguida, a autenticação automaticamente através da conta de utilizador com sessão iniciada.

- Pode utilizar o **repor definições** opção partir **ajuda e Feedback** para terminar sessão e eliminar a política do Azure Information Protection atualmente transferida.


## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>Impor o modo apenas de proteção quando a sua organização tiver uma mistura de licenças

Se sua organização não tem quaisquer licenças do Azure Information Protection, mas tem licenças para o Office 365 que incluem o serviço Azure Rights Management para proteger os dados, o cliente do Azure Information Protection para Windows é executada automaticamente [modo apenas de proteção](client-protection-only-mode.md).

No entanto, se sua organização tiver uma subscrição do Azure Information Protection, por predefinição todos os computadores Windows podem transferir a política do Azure Information Protection. O cliente do Azure Information Protection não fazer para licenciar a verificação e de imposição. 

Se tiver alguns utilizadores que não tem uma licença do Azure Information Protection, mas tiver uma licença do Office 365 que inclui o serviço Azure Rights Management, editar o registo nos computadores dos utilizadores, estes para impedir que os utilizadores a executar o não licenciados classificação e etiquetagem funcionalidades do Azure Information Protection.

Localize o nome do valor seguinte e defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Além disso, verifique que estes computadores não têm um arquivo chamado **msip** no **%LocalAppData%\Microsoft\MSIP** pasta. Se este ficheiro já existir, elimine-o. Este ficheiro contém a política do Azure Information Protection e poderá ter transferido antes de editar o registo ou se o cliente do Azure Information Protection foi instalado com a opção de demonstração.

## <a name="modify-the-email-address-for-the-report-an-issue-link"></a>Modificar o endereço de e-mail para o relatório de uma ligação de problema

Esta opção de configuração está atualmente em pré-visualização e está sujeitas a alterações. Também requer a versão de pré-visualização do cliente do Azure Information Protection.

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando os utilizadores selecionam a **comunicar um problema** uma ligação a **ajuda e Feedback** caixa de diálogo de cliente, por predefinição, um endereço é preenchido numa mensagem de e-mail da Microsoft. Utilize o seguinte avançada de definição de cliente para modificar esse endereço. Por exemplo, especificar `mailto:helpdesk@contoso.com` para o endereço de e-mail do suporte técnico. 

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **ReportAnIssueLink**

- Valor:  **\<cadeia de caracteres HTTP >**

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ocultar a opção de menu Classificar e Proteger no Explorador de Ficheiros do Windows

Crie o nome do valor DWORD seguinte (com quaisquer dados do valor):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Suporte para computadores desligados

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection para transferir a política do Azure Information Protection mais recente. Se tiver computadores que sabe que não será possível estabelecer ligação à Internet durante um período de tempo, pode impedir que o cliente tentar ligar ao serviço ao editar o registo. 

Tenha em atenção que sem uma ligação à Internet, o cliente não é possível aplicar proteção (ou remover proteção), utilizando a chave de com base na cloud da sua organização. Em vez disso, o cliente está limitado a utilizar as etiquetas que aplicam apenas a classificação ou proteção que utiliza [HYOK](../configure-adrms-restrictions.md).

Para configurar esta definição, localize o nome do valor seguinte no Registro e defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Certifique-se de que o cliente tem um ficheiro de política válido denominado **msip**, na **%LocalAppData%\Microsoft\MSIP** pasta. Se necessário, pode exportar a política global ou de uma política de âmbito do portal do Azure e copie o ficheiro exportado para o computador cliente. Também pode utilizar este método para substituir um ficheiro de política desatualizada pela política publicada mais recente. No entanto, exportar a política não suporta o cenário em que um utilizador pertencer a mais do que uma política de âmbito. Também tenha em atenção que se os utilizadores selecionarem a **repor definições** opção partir [ajuda e feedback](client-admin-guide.md#help-and-feedback-section), esta ação elimina o ficheiro de política e apresenta-o cliente inoperável até que substitua manualmente o ficheiro de política ou o cliente liga-se ao serviço transferir a política.

Ao exportar a política do portal do Azure, será transferido um arquivo zipado contém várias versões da política. Estas versões de política correspondem a diferentes versões do cliente do Azure Information Protection:

1. Deszipe o ficheiro e utilize a seguinte tabela para identificar qual arquivo de política que precisa. 
    
    |Nome de ficheiro|Versão de cliente correspondente|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |versão 1.2|
    |Policy1.2.msip |versão 1.3 1.7|
    |Policy1.3.msip |versão 1.8 1.29|
    |Policy1.4.msip |versão 1.32 e posterior|
    
2. Mudar o nome do ficheiro identificado para **msip**e, em seguida, copie-o para o **%LocalAppData%\Microsoft\MSIP** pasta em computadores que tenham o cliente do Azure Information Protection instalado. 


## <a name="hide-or-show-the-do-not-forward-button-in-outlook"></a>Ocultar ou mostrar o botão não reencaminhar no Outlook

O método recomendado para configurar esta opção é utilizar o [definição de política](../configure-policy-settings.md) **adicionar o botão não reencaminhar ao Friso do Outlook**. No entanto, também pode configurar esta opção ao utilizar um [definição de cliente avançado](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que configurar no portal do Azure.

Quando configura esta definição, oculta ou mostra os **não reencaminhar** botão da faixa de opções no Outlook. Esta definição não tem nenhum efeito sobre a opção não reencaminhar de menus do Office.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **DisableDNF**

- Valor: **True** para ocultar o botão, ou **falso** para mostrar o botão

## <a name="make-the-custom-permissions-options-available-or-unavailable-to-users"></a>Tornar as opções de permissões personalizadas disponíveis ou não está disponível para utilizadores

O método recomendado para configurar esta opção é utilizar o [definição de política](../configure-policy-settings.md) **disponibilizar a opção de permissões personalizadas para utilizadores**. No entanto, também pode configurar esta opção ao utilizar um [definição de cliente avançado](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que configurar no portal do Azure. 

Quando configura esta definição e publica a política para utilizadores, as opções de permissões personalizadas ficam visíveis para os utilizadores selecionarem suas próprias definições de proteção ou eles estão ocultos para que os utilizadores não é possível selecionar suas próprias definições de proteção, a menos que lhe for pedido.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **EnableCustomPermissions**

- Valor: **True** para fazer com a opção de permissões personalizadas visível, ou **falso** para ocultar esta opção


## <a name="permanently-hide-the-azure-information-protection-bar"></a>Ocultar permanentemente a barra do Azure Information Protection

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Usá-lo apenas quando os [definição de política](../configure-policy-settings.md) **apresentar a barra de Information Protection nas aplicações do Office** está definida como **no**.

Quando configura esta definição e publica a política para os utilizadores, se um utilizador optar por não mostrar a barra do Azure Information Protection nas aplicações do Office, a barra permanece oculta. Tal acontece quando o utilizador desmarca a opção **Mostrar Barra** do separador **Base**, grupo de **Proteção**, botão **Proteger**. Esta definição não tem qualquer efeito caso o utilizador feche a barra através do ícone **Fechar esta barra**.

Apesar de a barra do Azure Information Protection permanecer oculta, os utilizadores ainda podem selecionar uma etiqueta na barra apresentada temporariamente caso tenha configurado a classificação recomendada ou um documento ou um e-mail tenha de ter uma etiqueta. 

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **EnableBarHiding**

- Valor: **Verdadeiro**


## <a name="enable-recommended-classification-in-outlook"></a>Ativar a classificação recomendada no Outlook

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Esta definição está em pré-visualização e podem ser alteradas.

Quando configura uma etiqueta para a classificação recomendada, é pedido aos utilizadores que aceitem ou dispensar a etiqueta recomendada no Word, Excel e PowerPoint. Esta definição se estende esta recomendação de etiqueta também exibir no Outlook.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **OutlookRecommendationEnabled**

- Valor: **Verdadeiro**


## <a name="set-a-different-default-label-for-outlook"></a>Definir uma etiqueta predefinida diferente para o Outlook

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando configura esta definição, o Outlook não aplica a etiqueta predefinida que é configurada na política do Azure Information Protection para a definição **selecione a etiqueta predefinida**. Em vez disso, o Outlook pode aplicar uma etiqueta predefinida diferente, ou nenhuma etiqueta.

Para aplicar uma etiqueta diferente, tem de especificar o ID da etiqueta. O valor de ID de etiqueta é apresentado no **etiqueta** painel, quando ver ou configurar a política do Azure Information Protection no portal do Azure. Para os ficheiros que tenham as etiquetas aplicadas, também pode executar o [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) cmdlet do PowerShell para identificar o ID de etiqueta (MainLabelId ou SubLabelId). Quando uma etiqueta tem subetiquetas, sempre Especifica o ID de apenas uma subetiqueta e não a etiqueta principal.

Assim que o Outlook não se aplica a etiqueta predefinida, especifique **None**.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **OutlookDefaultLabel**

- Valor: \< **ID de etiqueta**> ou **None**

## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>Remova "Agora não" para os documentos quando utiliza a etiquetagem obrigatório

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando utiliza a [definição de política](../configure-policy-settings.md) dos **todos os documentos e e-mails devem ter uma etiqueta**, é pedido aos utilizadores para selecionar uma etiqueta quando eles primeiramente salvarem um documento do Office e quando eles enviam uma mensagem de e-mail. Para documentos, os utilizadores podem selecionar **agora não** temporariamente dispensar o pedido para selecionar uma etiqueta e retornar ao documento. No entanto, eles não é possível fechar o documento guardado sem rotulando-o. 

Quando configurar esta definição, remove a **agora não** opção para que os utilizadores devem selecionar uma etiqueta, quando o documento é salvo em primeiro lugar.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **PostponeMandatoryBeforeSave**

- Valor: **Falso**

## <a name="turn-on-classification-to-run-continuously-in-the-background"></a>Ativar a classificação para executar continuamente em segundo plano

Esta opção de configuração está atualmente em pré-visualização e está sujeitas a alterações.

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando configura esta definição, ele altera a [predefinição de comportamento](../configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied) de como o cliente do Azure Information Protection aplica etiquetas automáticas e recomendadas para documentos: 

- Para Word, Excel e PowerPoint, a classificação automática seja executada continuamente em segundo plano.  

O comportamento não é alterada para o Outlook.

Quando o cliente do Azure Information Protection verifica periodicamente a documentos para as regras de condição que especificar, este comportamento permite a classificação automática e recomendada e proteção para documentos armazenados no SharePoint Online. Ficheiros grandes também poupar mais rapidamente porque as regras de condição já estiver a executar. 

As regras de condição não são executados em tempo real conforme um usuário digita. Em vez disso, eles são executados periodicamente como uma tarefa em segundo plano se o documento for modificado.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **RunPolicyInBackground**

- Valor: **Verdadeiro**

## <a name="dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption"></a>Não proteger ficheiros PDF com a norma ISO para a encriptação de PDF

Esta opção de configuração está atualmente em pré-visualização e está sujeitas a alterações. Também requer a versão de pré-visualização do cliente do Azure Information Protection.

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando a versão de disponibilidade geral (GA) do cliente do Azure Information Protection protege um ficheiro PDF, o arquivo resultante tem uma extensão de nome de ficheiro. ppdf. No entanto, quando a versão de pré-visualização atual do cliente do Azure Information Protection protege um ficheiro PDF, a extensão de nome de ficheiro resultante permanece como. pdf e cumpre a norma ISO para a encriptação de PDF. Para obter mais informações sobre este padrão, consulte a secção **encriptação 7.6** partir a [documento que é derivado da ISO 32000-1](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf) e publicado por Incorporated de sistemas do Adobe.

Se tiver a versão de pré-visualização atual do cliente para reverter para o comportamento de disponibilidade geral, use a seguinte configuração avançada ao introduzir a seguinte cadeia:

- Chave: **EnablePDFv2Protection**

- Valor: **Falso**

Para o scanner do Azure Information Protection utilizar a nova definição, é necessário reiniciar o serviço de scanner.

## <a name="support-for-files-protected-by-secure-islands"></a>Suporte para ficheiros protegidos por Secure Islands

Esta opção de configuração está atualmente em pré-visualização e está sujeitas a alterações. Também requer que as versões de pré-visualização do cliente do Azure Information Protection, o scanner do Azure Information Protection ou o Visualizador do Azure Information Protection.

Se utilizou a Secure Islands para proteger documentos, poderá proteger texto e arquivos de imagem e ficheiros protegidos genericamente, como resultado desta proteção. Por exemplo, ficheiros que tenham uma extensão de nome de ficheiro. ptxt,. pjpeg ou. pfile. Ao editar o registo da seguinte forma, o Azure Information Protection pode descriptografar esses arquivos:


Adicione o seguinte valor DWORD de **EnableIQPFormats** para o seguinte caminho de registo e defina os dados de valor como **1**:

- Para uma versão de 64 bits do Windows: HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\MSIP

- Para uma versão de 32 bits do Windows: HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\MSIP

Como resultado desta edição de registo, são suportados os seguintes cenários:

- O Visualizador do Azure Information Protection pode abrir estes ficheiros protegidos.

- Explorador de ficheiros e o PowerShell podem desproteger estes ficheiros ou volte a protegê-los com o Azure Information Protection.

- Explorador de ficheiros, o PowerShell e o scanner do Azure Information Protection podem Etiquetar estes ficheiros.

- O scanner do Azure Information Protection pode inspecionar esses arquivos de informações confidenciais.

- Pode utilizar o [personalização do cliente de migração de etiquetagem](#migrate-labels-from-secure-islands-and-other-labeling-solutions) para converter a etiqueta de Secure Islands sobre esses protegidos ficheiros para uma etiqueta do Azure Information Protection.

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Migrar as etiquetas de Secure Islands e outras soluções de etiquetas

Esta opção de configuração está atualmente em pré-visualização e está sujeitas a alterações.

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Para documentos do Office e dos documentos em PDF que estão identificados por Secure Islands, pode relabel estes documentos com uma etiqueta do Azure Information Protection ao utilizar um mapeamento por si. Também utilizar este método reutilizar as etiquetas de outras soluções existentes, quando os rótulos são em documentos do Office. 

> [!NOTE]
> Se tiver ficheiros diferentes dos documentos PDF e do Office protegidos pelo Secure Islands, estes podem de ser relabeled depois de editar o registo, conforme descrito no [secção anterior](#support-for-files-protected-by-secure-islands). 

Como resultado desta opção de configuração, a nova etiqueta do Azure Information Protection é aplicada pelo cliente do Azure Information Protection da seguinte forma:

- Para documentos do Office: quando o documento é aberto na aplicação do ambiente de trabalho, a nova etiqueta do Azure Information Protection é mostrada como o conjunto e é aplicada quando o documento é salvo.

- Explorador de ficheiros: Na caixa de diálogo do Azure Information Protection, a nova etiqueta do Azure Information Protection é mostrada como o conjunto e é aplicada quando o usuário seleciona **aplicar**. Se o utilizador seleciona **Cancelar**, não se aplica a nova etiqueta.

- Para o PowerShell: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) aplica-se a nova etiqueta do Azure Information Protection. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) não apresenta a nova etiqueta do Azure Information Protection até que ele é definido por outro método.

- Para o scanner do Azure Information Protection: relatórios de deteção, quando a nova etiqueta do Azure Information Protection seria definida e pode ser aplicada esta etiqueta com o modo de imposição.

Esta configuração requer que especifique um definição com o nome de cliente avançado **LabelbyCustomProperty** para cada etiqueta do Azure Information Protection que pretende mapear para a etiqueta antiga. Em seguida, para cada entrada, defina o valor utilizando a seguinte sintaxe:

`[Azure Information Protection label ID],[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

O valor de ID de etiqueta é apresentado no **etiqueta** painel, quando ver ou configurar a política do Azure Information Protection no portal do Azure. Para especificar uma subetiqueta, a etiqueta principal tem de ser no mesmo escopo, ou na política global.

Especifique a sua escolha de um nome de regra de migração. Utilize um nome descritivo, que ajuda a identificar como um ou mais etiquetas da sua solução de etiquetagem anterior deve ser mapeado para uma etiqueta do Azure Information Protection. O nome é apresentado nos relatórios de scanner e no Visualizador de eventos. 

Tenha em atenção que esta definição não remove quaisquer marcas visuais que possa ter aplicados a etiqueta antiga. Para remover os cabeçalhos e rodapés, consulte a secção seguinte, [remover os cabeçalhos e rodapés de outras soluções de etiquetas](#remove-headers-and-footers-from-other-labeling-solutions).

### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Exemplo 1: Mapeamento o mesmo nome de etiqueta

Documentos que tenham uma etiqueta de Secure Islands de "Confidencial" devem ser relabeled como "Confidencial" pelo Azure Information Protection.

Neste exemplo:

- A etiqueta do Azure Information Protection **confidencial** tem um ID de etiqueta de 1ace2cc3-14bc-4142-9125-bf946a70542c. 

- A etiqueta de Secure Islands é armazenada na propriedade personalizada com o nome **classificação**.

A definição de cliente avançado:

    
|Nome|Valor|
|---------------------|---------|
|LabelbyCustomProperty|1ace2cc3-14bc-4142-9125-bf946a70542c, "etiqueta Secure Islands é confidencial", classificação, confidencial|

### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Exemplo 2: Mapeamento para um nome de etiqueta diferente

Documentos identificados como "Confidenciais" por Secure Islands devem ser relabeled como "Altamente confidencial" pelo Azure Information Protection.

Neste exemplo:

- A etiqueta do Azure Information Protection **altamente confidencial** tem um ID de etiqueta de 3e9df74d-3168-48af-8b11-037e3021813f.

- A etiqueta de Secure Islands é armazenada na propriedade personalizada com o nome **classificação**.

A definição de cliente avançado:

    
|Nome|Valor|
|---------------------|---------|
|LabelbyCustomProperty|3e9df74d-3168-48af-8b11-037e3021813f, "etiqueta Secure Islands é sensível a", classificação, com diferenciação de|


### <a name="example-3-many-to-one-mapping-of-label-names"></a>Exemplo 3: Muitos-para-um mapeamento de nomes de etiqueta

Tem duas etiquetas de Secure Islands que incluíssem a palavra "Interno" e pretender que os documentos com qualquer um destas etiquetas de Secure Islands para ser relabeled como "Geral" pelo Azure Information Protection.

Neste exemplo:

- A etiqueta do Azure Information Protection **gerais** tem um ID de etiqueta de 2beb8fe7-8293-444 c-9768-7fdc6f75014d.

- A etiqueta de Secure Islands é armazenada na propriedade personalizada com o nome **classificação**.

A definição de cliente avançado:

    
|Nome|Valor|
|---------------------|---------|
|LabelbyCustomProperty|2beb8fe7-8293-444c-9768-7fdc6f75014d, "a etiqueta de Secure Islands contém interno", classificação,. \*Interno.\*|


## <a name="remove-headers-and-footers-from-other-labeling-solutions"></a>Remover os cabeçalhos e rodapés de outras soluções de etiquetas

Esta opção de configuração está atualmente em pré-visualização e está sujeitas a alterações. Também requer a versão de pré-visualização do cliente do Azure Information Protection.

Esta configuração utiliza várias [definições de cliente avançadas](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure.

Estas definições permitem-lhe remover ou substituir os cabeçalhos ou rodapés de documentos quando essas marcas visuais foram aplicadas por outra solução de etiquetagem. Por exemplo, o rodapé antigo contém o nome de uma etiqueta antigo agora migrado para o Azure Information Protection com um novo nome de etiqueta e o seu próprio rodapé.

Quando o cliente recebe esta configuração em sua diretiva, o antigos cabeçalhos e rodapés são removidas ou substituídas quando o documento é aberto na aplicação do Office e qualquer etiqueta do Azure Information Protection é aplicada ao documento.

Esta configuração não é suportada para o Outlook e lembre-se de que quando usá-lo com o Word, Excel e PowerPoint, ele pode afetar negativamente o desempenho desses aplicativos para os utilizadores. A configuração permite-lhe definir as definições por aplicação, por exemplo, pesquisa de texto nos cabeçalhos e rodapés de documentos do Word, mas não planilhas do Excel ou apresentações do PowerPoint.

Uma vez que a correspondência de padrões afeta o desempenho para os utilizadores, recomendamos que limita os tipos de aplicações do Office (**W**ord, **i**xcel, **P**owerPoint) para apenas as que tem de ser pesquisada:

- Chave: **RemoveExternalContentMarkingInApp**

- Valor: \< **WXP de tipos de aplicação do Office**> 

Exemplos:

- Para pesquisar apenas a documentos do Word, especifique **W**.

- Para procurar documentos do Word e apresentações do PowerPoint, especifique **WP**.

Em seguida, tem de, pelo menos, uma definição de cliente mais avançado **ExternalContentMarkingToRemove**para especificar o conteúdo do cabeçalho ou rodapé de e como remover ou substituí-los.

### <a name="how-to-configure-externalcontentmarkingtoremove"></a>Como configurar ExternalContentMarkingToRemove

Quando especificar o valor de cadeia de caracteres para o **ExternalContentMarkingToRemove** chaves, tem três opções usam expressões regulares:

- Correspondência parcial para remover tudo no cabeçalho ou rodapé de.
    
    Exemplo: Cabeçalhos ou rodapés de contêm a cadeia de caracteres **texto para remover**. Pretende remover completamente esses cabeçalhos ou rodapés. Especificar o valor: `*TEXT*`.

- Correspondência completa para remover palavras específicas no cabeçalho ou rodapé de.
    
    Exemplo: Cabeçalhos ou rodapés de contêm a cadeia de caracteres **texto para remover**. Pretende remover a palavra **texto** apenas, que deixa a cadeia de cabeçalho ou rodapé como **para remover**. Especificar o valor: `TEXT `.

- Correspondência completa para remover tudo no cabeçalho ou rodapé de.
    
    Exemplo: Cabeçalhos ou rodapés de tenham a cadeia de caracteres **texto para remover**. Pretende remover os cabeçalhos ou rodapés que têm exatamente essa cadeia de caracteres. Especificar o valor: `^TEXT TO REMOVE$`.
    

O padrão correspondente para a cadeia de caracteres que especificar diferencia maiúsculas de minúsculas. O comprimento máximo da cadeia é 255 carateres.

Uma vez que alguns documentos podem incluir diferentes tipos de espaços ou tabulações ou carateres de invisíveis, a cadeia de caracteres que especificou para uma frase ou frase poderão não ser detetada. Sempre que possível, especifique uma única palavra distinguir para o valor e certifique-se de que os resultados de teste antes de implementar na produção.

- Chave: **ExternalContentMarkingToRemove**

- Valor: \< **para corresponder de cadeias de caracteres, definida como expressão regular**> 

#### <a name="multiline-headers-or-footers"></a>Várias linhas cabeçalhos ou rodapés de

Se uma mensagem de texto do cabeçalho ou rodapé é mais do que uma única linha, crie uma chave e valor para cada linha. Por exemplo, tem o rodapé seguinte com duas linhas:

**O ficheiro é classificado como confidencial**

**Etiqueta aplicada manualmente**

Para remover este rodapé multline, crie as seguintes duas entradas:

- Chave 1: **ExternalContentMarkingToRemove**

- Valor da chave 1:  **\*confidenciais***

- Chave 2: **ExternalContentMarkingToRemove**

- Valor da chave 2:  **\*etiqueta aplicada*** 

#### <a name="optimization-for-powerpoint"></a>Otimização para o PowerPoint

Rodapés no PowerPoint são implementados como formas. Para evitar a remoção de formas que contêm o texto que especificou, mas não são cabeçalhos ou rodapés, utilize um cliente avançado adicional definição denominada **PowerPointShapeNameToRemove**. Também recomendamos que utilize esta definição para evitar a verificar o texto em todas as formas, que é um processo com muitos recursos.

Se não especificar esta adicional definição de cliente avançada, e o PowerPoint está incluído nos **RemoveExternalContentMarkingInApp** valor, chave todas as formas serão verificadas para o texto que especificou no  **ExternalContentMarkingToRemove** valor. 

Para localizar o nome da forma que está usando como um cabeçalho ou rodapé:

1. No PowerPoint, apresentar os **seleção** painel: **formato** separador > **Arrange** grupo > **painel de seleção**.

2. Selecione a forma no slide que contém o cabeçalho ou rodapé. O nome da forma selecionada agora é realçado na **seleção** painel.

Utilize o nome da forma para especificar um valor de cadeia de caracteres para o **PowerPointShapeNameToRemove** chave. 

Exemplo: É o nome da forma **fc**. Para remover a forma com este nome, tem de especificar o valor: `fc`.

- Chave: **PowerPointShapeNameToRemove**

- Valor: \< **nome de forma do PowerPoint**> 

Quando tiver mais de uma forma de PowerPoint para remover, crie tantos **PowerPointShapeNameToRemove** chaves que tenha formas para remover. Para cada entrada, especifique o nome da forma remover.

Por predefinição, apenas o mestre de slides são verificados para cabeçalhos e rodapés. Expandir esta pesquisa para todos os slides, que é um processo muito mais com muitos recursos, utilizar um cliente de avançadas adicional definição denominada **RemoveExternalContentMarkingInAllSlides**:

- Chave: **RemoveExternalContentMarkingInAllSlides**

- Valor: **Verdadeiro**

## <a name="label-an-office-document-by-using-an-existing-custom-property"></a>Etiqueta de um documento do Office usando uma propriedade personalizada existente

> [!NOTE]
> Se utilizar esta configuração e a configuração para [migrar as etiquetas de Secure Islands e outras soluções de etiquetas](#migrate-labels-from-secure-islands-and-other-labeling-solutions), a migração de etiquetagem definição tem precedência. 

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando configura esta definição, pode classificar (e, opcionalmente, proteger) um documento do Office quando tem uma propriedade personalizada existente com um valor que corresponde a um dos seus nomes de etiquetas. Esta propriedade personalizada pode ser definida a partir de outra solução de classificação ou pode ser definida como uma propriedade pelo SharePoint.

Como resultado nesta configuração, quando um documento sem uma etiqueta do Azure Information Protection é aberto e salvo por um utilizador da aplicação do Office, o documento tem, em seguida, o nome de acordo com o valor de propriedade correspondente. 

Esta configuração requer que especifique duas configurações avançadas que funcionam em conjunto. A primeira é denominada **SyncPropertyName**, que é o nome de propriedade personalizada que foi definido de outra solução de classificação ou uma propriedade que é definida pelo SharePoint. A segunda é denominada **SyncPropertyState** e tem de ser definido como OneWay.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave 1: **SyncPropertyName**

- Valor de chave 1: \< **nome da propriedade**> 

- Chave 2: **SyncPropertyState**

- Valor de chave 2: **OneWay**

Utilize estas chaves e valores correspondentes para apenas uma propriedade personalizada.

Por exemplo, tem uma coluna de SharePoint com o nome **classificação** que tem valores possíveis dos **pública**, **geral**, e **altamente confidencial todos Os funcionários**. Documentos são armazenados no SharePoint e ter **pública**, **gerais**, ou **altamente confidencial todos os funcionários** como valores definidos para a propriedade de classificação.

Para um documento do Office com um dos seguintes valores de classificação de etiqueta, defina **SyncPropertyName** ao **classificação**, e **SyncPropertyState** para  **OneWay**. 

Agora, quando um utilizador abre e salva um desses documentos do Office, ele tem o nome **pública**, **gerais**, ou **altamente confidencial \ todos os funcionários** se tiver etiquetas com estes nomes na sua política do Azure Information Protection. Se não tiver etiquetas com esses nomes, o documento permanece sem etiqueta.

## <a name="disable-the-low-integrity-level-for-the-scanner"></a>Desativar o nível de baixa integridade para a deteção de impressão

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Por predefinição, o scanner do Azure Information Protection é executado com um nível de baixa integridade. Esta definição proporciona maior isolamento de segurança, mas ao custo de desempenho. Um nível de baixa integridade é adequado se executar a deteção de impressão com uma conta que tem direitos (por exemplo, uma conta de administrador local) privilegiado porque esta definição ajuda a proteger o computador que executa a deteção de impressão.

No entanto, quando a conta de serviço que executa a deteção de impressão tem apenas os direitos documentados no [pré-requisitos do scanner](../deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner), nível baixo de integridade não é necessário e não é recomendado porque ele afeta negativamente o desempenho. 

Para obter mais informações sobre os níveis de integridade do Windows, consulte [o que é o mecanismo de integridade do Windows?](https://msdn.microsoft.com/library/bb625957.aspx)

Para configurar as definições avançadas para que o scanner é executado com um nível de integridade será automaticamente atribuído pelo Windows (uma conta de usuário padrão é executado com um nível de integridade média), introduza as seguintes cadeias:

- Chave: **ProcessUsingLowIntegrity**

- Valor: **Falso**


## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integração com a classificação de mensagem do Exchange para uma solução de etiquetagem do dispositivo móvel

Embora o Outlook na web ainda não suporta nativamente a classificação de Azure Information Protection e a proteção, pode utilizar a classificação de mensagem do Exchange para expandir suas etiquetas do Azure Information Protection para usuários móveis quando utilizarem o Outlook no Web. Outlook Mobile não suporta a classificação de mensagens do Exchange.

Para obter esta solução: 

1. Utilize o cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) do Exchange PowerShell para criar classificações de mensagens com a propriedade Nome que mapeia os seus nomes de etiquetas na sua política do Azure Information Protection. 

2. Criar uma regra de fluxo de correio do Exchange para cada etiqueta: aplique a regra quando as propriedades da mensagem incluírem a classificação que configurou e modifique as propriedades da mensagem para definir um cabeçalho de mensagem. 

     Para o cabeçalho da mensagem, encontra as informações a especificar ao inspecionar os cabeçalhos de Internet do e-mail que enviou e classificou com a etiqueta do Azure Information Protection. Procure o cabeçalho **msip_labels** e a cadeia que imediatamente a seguir, até ao ponto e vírgula, inclusive. Por exemplo:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Em seguida, para o cabeçalho da mensagem na regra, especifique **msip_labels** para o cabeçalho e a parte restante da cadeia para o valor do cabeçalho. Por exemplo:
    
    ![Exemplo do fluxo de correio Exchange Online de regra que define o cabeçalho da mensagem para uma etiqueta específica do Azure Information Protection](../media/exchange-rule-for-message-header.png)
    
    Nota: Quando a etiqueta é uma subetiqueta, também tem de especificar a etiqueta principal antes da subetiqueta no valor de cabeçalho, usando o mesmo formato. Por exemplo, se seu subetiqueta tem um GUID de 27efdf94-80a0 - 4d 02-b88c-b615c12d69a9, o valor pode ser semelhante ao seguinte: `MSIP_Label_ab70158b-bdcc-42a3-8493-2a80736e9cbd_Enabled=True;MSIP_Label_27efdf94-80a0-4d02-b88c-b615c12d69a9_Enabled=True;`

Antes de testar esta configuração, lembre-se de que é, muitas vezes, um atraso ao criar ou editar as regras de fluxo de correio (por exemplo, aguarde uma hora). Quando a regra entrar em vigor, agora que os seguintes eventos acontecem quando os utilizadores utilizarem o Outlook na web ou um cliente de dispositivo móvel que suporte IRM do Exchange ActiveSync: 

- Os utilizadores selecionam a classificação de mensagens do Exchange e enviam o e-mail.

- A regra do Exchange deteta a classificação do Exchange e modifica o cabeçalho da mensagem em conformidade para adicionar a classificação do Azure Information Protection.

- Quando os destinatários internos veem o e-mail no Outlook e têm o cliente do Azure Information Protection instalado, verão a etiqueta do Azure Information Protection atribuída. 

Se as etiquetas do Azure Information Protection aplicarem a proteção, adicione esta proteção à configuração da regra: selecionar a opção para modificar a segurança de mensagem, aplicar a proteção de direitos e, em seguida, selecione a opção não reencaminhar ou modelo de RMS.

Também pode configurar as regras de fluxo de correio para proceder ao mapeamento inverso. Quando uma etiqueta do Azure Information Protection é detetada, é definida uma classificação de mensagens do Exchange correspondente:

- Para cada etiqueta do Azure Information Protection: crie uma regra de fluxo de correio que seja aplicada quando o **msip_labels** cabeçalho inclui o nome da sua etiqueta (por exemplo, **geral**) e aplique uma mensagem classificação que mapeie esta etiqueta.


## <a name="next-steps"></a>Passos Seguintes
Agora que personalizou o cliente do Azure Information Protection, veja os seguintes recursos para obter informações adicionais que poderá precisar para suportar este cliente:

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


