---
title: Configurações personalizadas do cliente do Azure Information Protection
description: Informações sobre a personalização do cliente do Azure Information Protection para Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: de7829532139556b6407506d61bc89de936b3739
ms.sourcegitcommit: 9e2719ab070fa2d1e3ac8f6f11e57640939a1dff
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/12/2018
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-client"></a>Guia de administração: Configurações personalizadas para o cliente Azure Information Protection

>*Aplica-se a: serviços de gestão de direitos do Active Directory [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilize as seguintes informações para as configurações avançadas que poderá precisar para cenários específicos ou um subconjunto de utilizadores ao gerir o cliente do Azure Information Protection.

Algumas destas definições requerem a edição do registo e algumas utilizam definições avançadas que tem de configurar no portal do Azure e, em seguida, publicar para os clientes transferirem.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Como configurar as definições avançadas de configuração de cliente no portal

1. Se ainda não o tiver feito deste modo, numa nova janela do browser, [inicie sessão no portal do Azure](../deploy-use/configure-policy.md#signing-in-to-the-azure-portal)e, em seguida, navegue para o **Azure Information Protection** painel.

2. Do **classificações** > **etiquetas** opção do menu: selecione **políticas**.

3. No **Azure Information Protection - políticas** painel, selecione o menu de contexto (**...** ) junto a política que contém as definições avançadas. Em seguida, selecione **Definições avançadas**.
    
    Pode configurar as definições avançadas para a Política global, bem como para as políticas de âmbito.

4. No painel **Definições avançadas**, escreva o nome e o valor da definição avançada e, em seguida, selecione **Guardar e fechar**.

5. Certifique-se de que os utilizadores para esta política reinicie as aplicações do Office que tinha abrirem.

6. Caso já não precise da definição e pretenda reverter para o comportamento predefinido: no painel **Definições avançadas**, selecione o menu de contexto (**...** ) junto à definição que já não é precisa e, em seguida, selecione **Eliminar**. Em seguida, clique em **guarde e feche**.

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Impedir pedidos de início de sessão para computadores só com AD RMS

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection. Para computadores que só comunicam com AD RMS, esta configuração pode resultar num pedido desnecessário de início de sessão aos utilizadores. Pode impedir este pedido de início de sessão ao editar o registo:

Localize o nome do valor seguinte e, em seguida, defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Independentemente desta definição, o cliente do Azure Information Protection segue o [processo de deteção do serviço RMS](../rms-client/client-deployment-notes.md#rms-service-discovery) padrão, para localizar o respetivo cluster AD RMS.

## <a name="suppress-the-initial-congratulations-welcome-page"></a>Suprimir as iniciais "parabéns!" Página de boas-vindas

Quando o cliente Azure Information Protection é instalado pela primeira vez num computador e um utilizador abre o Word, Excel, PowerPoint ou Outlook, um **Parabéns!** página é apresentada com instruções abreviadas como utilizar a nova barra do Information Protection para selecionar etiquetas. Pode suprimir esta página ao editar o registo.

1. Se a seguinte chave de registo não existir, crie-o:
    
    **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP**

2. Se um valor DWORD de (32 bits) (REG DWORD) com o nome **EnableWelcomeExperience** não existir, crie-o e defina o valor de dados para **0**:

## <a name="suppress-the-whats-new-in-azure-information-protection-page"></a>Suprimir a "Novidades do Azure Information Protection?" Página

Quando o cliente Azure Information Protection está instalado ou atualizado num computador pela primeira vez e barra do Azure Information Protection é apresentada no Word, Excel, PowerPoint ou Outlook, um **Novidades do Azure Information Protection?** página apresenta a informar os utilizadores sobre permissões personalizadas e controlar a utilização. Pode suprimir esta página ao editar o registo.

1. Se a seguinte chave de registo não existir, crie-o:
    
    **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP**

2.  Se um valor de cadeia (REG SZ) com o nome **WhatsNewVersion** não existir, crie-o e defina o valor de dados para **1.4**.

## <a name="sign-in-as-a-different-user"></a>Iniciar sessão como um utilizador diferente

Num ambiente de produção, normalmente, os utilizadores não precisam de iniciar sessão como um utilizador diferente quando estão a utilizar o cliente do Azure Information Protection. No entanto, como administrador, poderá ter de iniciar sessão como um utilizador diferente durante uma fase de teste. 

Pode verificar com que conta tem sessão iniciada atualmente através da caixa de diálogo do **Microsoft Azure Information Protection**: abra uma aplicação do Office e, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e comentários**. O nome da sua conta é apresentado na secção **Estado do cliente**.

Confirme que também verifica o nome de domínio da conta com sessão iniciada que é apresentada. Pode não perceber que tem sessão iniciada com o nome da conta certo, mas com o domínio errado. Um sinal de utilização da conta errada inclui a impossibilidade de transferir a política do Azure Information Protection ou não ver as etiquetas ou o comportamento esperado.

Para iniciar sessão como um utilizador diferente:

1. Navegue para **%localappdata%\Microsoft\MSIP** e elimine o **TokenCache** ficheiro.

2. Reinicie as aplicações do Office abertas e inicie sessão com a sua conta de utilizador diferente. Se não vir um pedido na aplicação do Office para iniciar sessão no serviço Azure Information Protection, volte à caixa de diálogo do **Microsoft Azure Information Protection** e clique em **Iniciar sessão** na secção **Estado do cliente** atualizada.

Além disso,

- esta solução é suportada para iniciar sessão como outro utilizador a partir do mesmo inquilino. Não é suportada para iniciar sessão como outro utilizador a partir de um inquilino diferente. Para testar o Azure Information Protection com vários inquilinos, utilize computadores diferentes.

- Se estiver a utilizar o início de sessão único, tem de terminar sessão no Windows e iniciar sessão com a sua outra conta de utilizador após editar o registo. O cliente do Azure Information Protection faz, em seguida, a autenticação automaticamente através da conta de utilizador com sessão iniciada.

- Pode utilizar o **repor definições** opção de **ajuda e comentários** para terminar sessão e eliminar a política do Azure Information Protection atualmente transferida.


## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>Impor o modo só de proteção quando a sua organização tem uma combinação de licenças

Se a sua organização não tem as licenças do Azure Information Protection, mas tenha licenças para o Office 365 que inclua o serviço Azure Rights Management para proteção de dados, o cliente Azure Information Protection para o Windows é executado automaticamente [modo só de proteção](../rms-client/client-protection-only-mode.md).

No entanto, se a sua organização tiver uma subscrição do Azure Information Protection, por predefinição todos os computadores Windows podem transferir a política do Azure Information Protection. O Azure Information Protection does de cliente não licenças verificação e de imposição. 

Se tiver alguns utilizadores não possuem uma licença para o Azure Information Protection, mas tem uma licença para o Office 365 que inclui o serviço Azure Rights Management, editar o registo nos computadores dos utilizadores, estes para impedir que os utilizadores executem o sem licença classificação e etiquetagem funcionalidades do Azure Information Protection.

Localize o nome do valor seguinte e defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Além disso, verifique que estes computadores não têm um ficheiro denominado **Policy.msip** no **%LocalAppData%\Microsoft\MSIP** pasta. Se este ficheiro, elimine-o. Este ficheiro contém a política do Azure Information Protection e poderá ter transferido antes de editar o registo ou se o cliente Azure Information Protection foi instalado com a opção de demonstração.

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ocultar a opção de menu Classificar e Proteger no Explorador de Ficheiros do Windows

Crie o nome do valor DWORD seguinte (com quaisquer dados do valor):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Suporte para computadores desligados

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection para transferir a política do Azure Information Protection mais recente. Se tiver um computador que sabe que não poderá estabelecer ligação à Internet durante um período de tempo, poderá impedir o cliente de tentar estabelecer ligação ao serviço ao editar o registo. 

Localize o nome do valor seguinte e defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Certifique-se de que o cliente tem um ficheiro de política válido denominado **Policy.msip**, além de **%LocalAppData%\Microsoft\MSIP** pasta. Se necessário, pode exportar a política a partir do portal do Azure e copiar o ficheiro exportado para o computador cliente. Também pode utilizar este método para substituir um ficheiro de política desatualizada pela política publicada mais recente.

Ao exportar a política, esta ação transfere um ficheiro zipped com várias versões da política que corresponde ao versões diferentes do cliente Azure Information Protection:

1. Deszipe o ficheiro e utilize a tabela seguinte para identificar o ficheiro de política é necessário. 
    
    |Nome de ficheiro|Versão de cliente correspondente|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |versão 1.2|
    |Policy1.2.msip |versão 1.3 1.7|
    |Policy1.3.msip |versão 1.8 e posterior|
    
2. Mudar o nome do ficheiro identificado para **Policy.msip**e, em seguida, copie-o para o **%LocalAppData%\Microsoft\MSIP** pasta em computadores que tenham o cliente do Azure information protection instalado. 


## <a name="hide-or-show-the-do-not-forward-button-in-outlook"></a>Ocultar ou mostrar o botão não reencaminhar no Outlook

O método recomendado para configurar esta opção é utilizar o [definição de política](../deploy-use/configure-policy-settings.md) **adicionar botão não reencaminhar para o Friso Outlook**. No entanto, também pode configurar esta opção, utilizando um [definição de cliente avançado](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que configurar no portal do Azure.

Quando configurar esta definição, oculta ou mostra o **não reencaminhar** botão no Friso do Outlook. Esta definição não tem efeito a opção não reencaminhar de menus do Office.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **DisableDNF**

- Valor: **verdadeiro** para ocultar o botão de ou **falso** para mostrar o botão

## <a name="make-the-custom-permissions-options-available-or-unavailable-to-users"></a>Se as opções de permissões personalizadas disponível ou não está disponível para utilizadores

O método recomendado para configurar esta opção é utilizar o [definição de política](../deploy-use/configure-policy-settings.md) **tornar a opção de permissões personalizadas disponíveis para os utilizadores**. No entanto, também pode configurar esta opção, utilizando um [definição de cliente avançado](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que configurar no portal do Azure. 

Quando configurar esta definição e publicar a política para utilizadores, as opções de permissões personalizadas tornar-se disponível para os utilizadores selecionem as suas próprias definições de proteção ou não está disponível para que os utilizadores não é possível selecionar as suas próprias definições de proteção, a menos que lhe for pedido.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **EnableCustomPermissions**

- Valor: **verdadeiro** para disponibilizar a opção de permissões personalizadas, ou **falso** para tornar esta opção indisponível


## <a name="permanently-hide-the-azure-information-protection-bar"></a>Ocultar permanentemente a barra do Azure Information Protection

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Utilizá-lo apenas quando o [definição de política](../deploy-use/configure-policy-settings.md) **apresentar a barra do Information Protection em aplicações do Office** está definido como **no**.

Quando configura esta definição e publica a política para os utilizadores, se um utilizador optar por não mostrar a barra do Azure Information Protection nas aplicações do Office, a barra permanece oculta. Tal acontece quando o utilizador desmarca a opção **Mostrar Barra** do separador **Base**, grupo de **Proteção**, botão **Proteger**. Esta definição não tem qualquer efeito caso o utilizador feche a barra através do ícone **Fechar esta barra**.

Apesar de a barra do Azure Information Protection permanecer oculta, os utilizadores ainda podem selecionar uma etiqueta na barra apresentada temporariamente caso tenha configurado a classificação recomendada ou um documento ou um e-mail tenha de ter uma etiqueta. 

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **EnableBarHiding**

- Valor: **Verdadeiro**


## <a name="enable-recommended-classification-in-outlook"></a>Ativar a classificação recomendada no Outlook

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Esta definição está em pré-visualização e pode ser alterado.

Quando configurar uma etiqueta para a classificação recomendada, os utilizadores recebem um pedido para aceitar ou ignorar a etiqueta recomendada no Word, Excel e PowerPoint. Esta definição prolonga esta recomendação de etiqueta a apresentar também no Outlook.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **OutlookRecommendationEnabled**

- Valor: **Verdadeiro**


## <a name="set-a-different-default-label-for-outlook"></a>Definir uma etiqueta predefinida diferente para o Outlook

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando configurar esta definição, Outlook não se aplica a etiqueta predefinida que está configurada na política de proteção de informações do Azure para a definição **selecione a etiqueta predefinida**. Em vez disso, o Outlook pode aplicar uma etiqueta predefinida diferente ou sem etiqueta.

Para aplicar uma etiqueta diferente, tem de especificar o ID da etiqueta. O valor de ID da etiqueta é apresentado no **etiqueta** painel, ao ver ou configurar a política do Azure Information Protection no portal do Azure. Para os ficheiros que tenham etiquetas aplicadas, também pode executar o [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) cmdlet do PowerShell para identificar o ID de etiqueta (MainLabelId ou SubLabelId). Quando uma etiqueta tem sublabels, sempre especificar o ID de apenas um sublabel e não a etiqueta principal.

Por isso que Outlook não se aplica a etiqueta predefinida, especifique **nenhum**.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **OutlookDefaultLabel**

- Valor: \< **etiqueta ID**> ou **None**

## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>Remover "Não agora" para documentos quando utiliza a etiquetagem obrigatório

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando utiliza o [definição de política](../deploy-use/configure-policy-settings.md) de **todos os documentos e e-mails devem ter uma etiqueta**, os utilizadores recebem Selecione uma etiqueta ao guardam primeiro um documento do Office e quando enviam mensagens de correio eletrónico. Para documentos, os utilizadores podem selecionar **não agora** temporariamente dispensar o pedido para selecionar uma etiqueta e voltar para o documento. No entanto, ele não é possível fechar o documento guardado sem etiquetagem-lo. 

Quando configurar esta definição, remove o **não agora** opção para que os utilizadores devem selecionar uma etiqueta, quando o documento é guardado primeiro.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **PostponeMandatoryBeforeSave**

- Valor: **Falso**

## <a name="turn-on-classification-to-run-continuously-in-the-background"></a>Ativar a classificação a executar continuamente em segundo plano

Esta opção de configuração está atualmente em pré-visualização e está sujeita a alterações.

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando configurar esta definição, altera o [predefinido comportamento](../deploy-use/configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied) da forma como o cliente Azure Information Protection aplica etiquetas automáticas e recomendadas da seguinte forma:

- A classificação automática aplica-se ao Word, Excel, PowerPoint e Outlook. Para documentos, a classificação automática é executada continuamente em segundo plano. Para o Outlook, a classificação automática é executada quando os e-mails são enviados. 
    
    Não é possível utilizar a classificação automática para documentos que foram anteriormente etiquetados de forma manual ou anteriormente automaticamente com a etiqueta com uma classificação superior. A exceção a este comportamento é se utilizar a análise do Azure Information Protection com o parâmetro de OverrideLabel definido no.

- A classificação recomendada aplica-se ao Word, Excel e PowerPoint. Para estes documentos, recomendado execuções de classificação continuamente em segundo plano. Não é possível utilizar a classificação recomendada para o Outlook.
    
    Pode utilizar a classificação recomendada para os documentos que foram anteriormente com a etiqueta, com ou sem uma classificação superior. 

Quando o cliente Azure Information Protection verifica periodicamente a documentos para as regras de condição que especificar, este comportamento permite a classificação automática e recomendada e proteção de documentos que estão armazenados no SharePoint Online. Ficheiros grandes também guardar mais rapidamente porque as regras de condição já estiver a executar. 

As regras da condição não são executados em tempo real como tipos de utilizador. Em vez disso, executam periodicamente como uma tarefa em segundo plano se o documento está modificado.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **RunPolicyInBackground**

- Valor: **Verdadeiro**

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Migrar as etiquetas de Secure Islands e outras soluções de etiquetas

Esta opção de configuração está atualmente em pré-visualização e está sujeita a alterações. Além disso, esta opção de configuração requer a versão de pré-visualização do cliente ou o scanner do Azure Information Protection.

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Para documentos do Office e os documentos PDF que são etiquetados pelo Secure Islands, pode relabel estes documentos com uma etiqueta de Azure Information Protection utilizando um mapeamento por si. Utilize também este método reutilizar as etiquetas de outras soluções quando as etiquetas estão em documentos do Office. 

Como resultado desta opção de configuração, a nova etiqueta do Azure Information Protection é aplicada ao cliente Azure Information Protection da seguinte forma:

- Para documentos do Office: quando o documento é aberto na aplicação do ambiente de trabalho, a nova etiqueta do Azure Information Protection é mostrada como conjunto e é aplicada quando o documento é guardado.

- Explorador de ficheiros: Na caixa de diálogo do Azure Information Protection, a nova etiqueta do Azure Information Protection é mostrada como conjunto e é aplicada quando o utilizador seleciona **aplicar**. Se o utilizador seleciona **Cancelar**, a nova etiqueta não é aplicada.

- Para o PowerShell: [conjunto AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) aplica-se a nova etiqueta do Azure Information Protection. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) não apresentam a nova etiqueta do Azure Information Protection até que está definido por outro método.

- Para a análise do Azure Information Protection: quando a nova etiqueta do Azure Information Protection seria definida e pode ser aplicada esta etiqueta com o modo de impor a relatórios de deteção.

Esta configuração requer a especificação de um cliente avançado definição denominada **LabelbyCustomProperty** para cada etiqueta do Azure Information Protection que pretende mapear para a etiqueta antiga. Em seguida, para cada entrada, defina o valor utilizando a seguinte sintaxe:

`[Azure Information Protection label ID],[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

O valor de ID da etiqueta é apresentado no **etiqueta** painel, ao ver ou configurar a política do Azure Information Protection no portal do Azure. Para especificar um sublabel, a etiqueta principal tem de ser no mesmo âmbito, ou na política de global.

Especifique a sua escolha de um nome de regra de migração. Utilize um nome descritivo que ajuda a identificar como um ou mais etiquetas da sua solução de etiquetas anterior deve ser mapeado para uma etiqueta de Azure Information Protection. O nome é apresentado nos relatórios do scanner e no Visualizador de eventos. 

### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Exemplo 1: Mapeamento um para um com o mesmo nome de etiqueta

Devem ser relabeled documentos que tenham uma etiqueta de Secure Islands de "Confidencial" como "Confidencial", pelo Azure Information Protection.

Neste exemplo:

- A etiqueta do Azure Information Protection da **confidencial** tem um ID de etiqueta de 1ace2cc3-14bc-4142-9125-bf946a70542c. 

- A etiqueta de Secure Islands é armazenada na propriedade personalizada com o nome **classificação**.

A definição de cliente avançado:

    
|Nome|Valor|
|---------------------|---------|
|LabelbyCustomProperty|1ace2cc3-14bc-4142-9125-bf946a70542c, "a etiqueta de Secure Islands é confidencial", classificação, confidencial|

### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Exemplo 2: Mapeamento um para um para um nome de etiqueta diferentes

Documentos etiquetados como "Confidencial" pelo Secure Islands devem ser relabeled "Altamente confidencial" como pelo Azure Information Protection.

Neste exemplo:

- A etiqueta do Azure Information Protection **altamente confidenciais** tem um ID de etiqueta de 3e9df74d-em com 3168-48af-8b11-037e3021813f.

- A etiqueta de Secure Islands é armazenada na propriedade personalizada com o nome **classificação**.

A definição de cliente avançado:

    
|Nome|Valor|
|---------------------|---------|
|LabelbyCustomProperty|3e9df74d-em com 3168-48af-8b11-037e3021813f, "a etiqueta de Secure Islands é confidencial", classificação, sensíveis|


### <a name="example-3-many-to-one-mapping-of-label-names"></a>Exemplo 3: Muitos-para-um mapeamento de nomes de etiqueta

Tem duas etiquetas de Secure Islands que incluem a palavra "Interno" e pretende que os documentos que tenham uma das etiquetas destes Secure Islands relabeled como "Geral", pelo Azure Information Protection.

Neste exemplo:

- A etiqueta do Azure Information Protection **geral** tem um ID de etiqueta de 2beb8fe7-8293-444 c-9768-7fdc6f75014d.

- A etiqueta de Secure Islands é armazenada na propriedade personalizada com o nome **classificação**.

A definição de cliente avançado:

    
|Nome|Valor|
|---------------------|---------|
|LabelbyCustomProperty|2beb8fe7-8293-444c-9768-7fdc6f75014d, "a etiqueta de Secure Islands contém interno", a classificação,. \*Interno.\*|


## <a name="label-an-office-document-by-using-an-existing-custom-property"></a>Etiqueta de um documento do Office através da utilização de uma propriedade personalizada existente

> [!NOTE]
> Se utilizar esta configuração e a configuração da secção anterior para migrar a partir de outra solução de etiquetas, a definição de migração de etiquetas tem precedência. 

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando configurar esta definição, pode classificar (e, opcionalmente, proteger) um documento do Office quando tem uma propriedade personalizada existente com um valor que corresponde a um dos nomes de etiqueta. Esta propriedade personalizada pode ser definida a partir de outra solução de classificação, ou pode ser definida como uma propriedade pelo SharePoint.

Como resultado esta configuração, quando um documento sem uma etiqueta de Azure Information Protection é aberto e guardado pelo utilizador numa aplicação do Office, o documento é, em seguida, com a etiqueta para corresponder ao valor de propriedade correspondente. 

Esta configuração requer que especifique duas definições avançadas que trabalham em conjunto. O primeiro nome **SyncPropertyName**, que é o nome de propriedade personalizada que foi definido por outra solução de classificação ou uma propriedade que é definida pelo SharePoint. O segundo é denominado **SyncPropertyState** e tem de ser definida para OneWay.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave 1: **SyncPropertyName**

- Valor de chave 1: \< **nome da propriedade**> 

- Chave 2: **SyncPropertyState**

- Valor de chave 2: **OneWay**

Utilize estas chaves e valores correspondentes para apenas uma propriedade personalizada.

Como exemplo, tem uma coluna do SharePoint com o nome **classificação** que tem os valores possíveis de **pública**, **geral**, e **confidencial**. Documentos são armazenados no SharePoint e tem um dos seguintes valores definido para a propriedade de classificação.

Para identificar um documento do Office com um dos seguintes valores de classificação, defina **SyncPropertyName** para **classificação**, e **SyncPropertyState** para  **OneWay**. 

Agora, quando um utilizador abre e guarda um destes documentos do Office, está assinalada como **pública**, **geral**, ou **confidencial** se tiver etiquetas com estes nomes no seu Azure Política de proteção de informações. Se tiver etiquetas com estes nomes, o documento permanece sem etiqueta.

## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integração com a classificação de mensagem do Exchange para uma solução de etiquetagem do dispositivo móvel

Embora o Outlook na web ainda não suporta nativamente classificação do Azure Information Protection e a proteção, pode utilizar a classificação de mensagem do Exchange para expandir as etiquetas de Azure Information Protection para os utilizadores móveis quando utilizarem o Outlook no Web. Outlook Mobile não suporta a classificação de mensagem do Exchange.

Para obter esta solução: 

1. Utilize o cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) do Exchange PowerShell para criar classificações de mensagens com a propriedade Nome que mapeia os seus nomes de etiquetas na sua política do Azure Information Protection. 

2. Criar uma regra de fluxo de correio do Exchange para cada etiqueta: aplicar a regra quando as propriedades da mensagem incluem a classificação que configurou e modificar as propriedades da mensagem para definir um cabeçalho da mensagem. 

     Para o cabeçalho da mensagem, encontra as informações a especificar ao inspecionar os cabeçalhos de Internet do e-mail que enviou e classificou com a etiqueta do Azure Information Protection. Procure o cabeçalho **msip_labels** e a cadeia que imediatamente a seguir, até ao ponto e vírgula, inclusive. Por exemplo:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Em seguida, para o cabeçalho da mensagem na regra, especifique **msip_labels** para o cabeçalho e a parte restante da cadeia para o valor do cabeçalho. Por exemplo:
    
    ![Exemplo de regra de fluxo de correio eletrónico Exchange Online, que define o cabeçalho da mensagem para uma etiqueta específica do Azure Information Protection](../media/exchange-rule-for-message-header.png)
    
    Nota: Quando a etiqueta é um sublabel, também tem de especificar a etiqueta principal antes do sublabel no valor de cabeçalho, o mesmo formato a utilizar. Por exemplo, se a sua sublabel tiver um GUID de 27efdf94-80a0 - 4d 02-b88c-b615c12d69a9, o valor de aspeto que poderá ter o seguinte: `MSIP_Label_ab70158b-bdcc-42a3-8493-2a80736e9cbd_Enabled=True;MSIP_Label_27efdf94-80a0-4d02-b88c-b615c12d69a9_Enabled=True;`

Antes de testar esta configuração, lembre-se de que há frequentemente um atraso quando criar ou editar regras de fluxo de correio (por exemplo, aguarde uma hora). Quando a regra está em vigor, os seguintes eventos de acontecer agora quando os utilizadores utilizam o Outlook web ou um cliente de dispositivo móvel que suporte a IRM do Exchange ActiveSync: 

- Os utilizadores selecionam a classificação de mensagens do Exchange e enviam o e-mail.

- A regra do Exchange deteta a classificação do Exchange e modifica o cabeçalho da mensagem em conformidade para adicionar a classificação do Azure Information Protection.

- Quando os destinatários veem o e-mail no Outlook e têm o cliente do Azure Information Protection instalado, veem a etiqueta do Azure Information Protection atribuída e quaisquer cabeçalhos, rodapés ou marcas de água de e-mail correspondentes. 

Se as etiquetas de Azure Information Protection se aplicar a proteção, adicione esta proteção à configuração de regra: selecionando a opção para modificar a segurança da mensagem, aplicar proteção de direitos e, em seguida, selecione o modelo de RMS ou a opção não reencaminhar.

Também pode configurar as regras do fluxo de correio para fazer o mapeamento inverso. Quando uma etiqueta do Azure Information Protection é detetada, é definida uma classificação de mensagens do Exchange correspondente:

- Para cada etiqueta do Azure Information Protection: criar uma regra de fluxo de correio eletrónico que é aplicada quando o **msip_labels** cabeçalho inclui o nome do seu etiqueta (por exemplo, **geral**) e aplicar uma mensagem classificação que mapeia para esta etiqueta.


## <a name="next-steps"></a>Próximos passos
Agora que personalizou o cliente do Azure Information Protection, veja os seguintes recursos para obter informações adicionais que poderá precisar para suportar este cliente:

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
