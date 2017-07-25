---
title: "Configurações personalizadas do cliente do Azure Information Protection"
description: "Informações sobre a personalização do cliente do Azure Information Protection para Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 41e9e8aff35727a40413e0bf18e46f1ad14e9222
ms.sourcegitcommit: 724b0b5d7a3ab694643988148ca68c0eac769f1e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/21/2017
---
# <a name="custom-configurations-for-the-azure-information-protection-client"></a>Configurações personalizadas do cliente do Azure Information Protection

>*Aplica-se a: Serviços de Gestão de Direitos do Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilize as seguintes informações para as configurações avançadas que poderá precisar para cenários específicos ou um subconjunto de utilizadores ao gerir o cliente do Azure Information Protection.

Algumas destas definições requerem a edição do registo e algumas utilizam definições avançadas que tem de configurar no portal do Azure e, em seguida, publicar para os clientes transferirem. 

Além disso, algumas definições apenas poderão estar disponíveis numa versão de pré-visualização do cliente do Azure Information Protection. Para estas definições, está documentada uma versão de cliente mínima. Para as definições e as configurações que são suportadas na versão de disponibilidade geral do cliente, não está documentado qualquer número da versão de cliente mínima.

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Como configurar as definições avançadas de configuração de cliente no portal

1. Caso ainda não o tenha feito, numa nova janela de browser, inicie sessão no [portal do Azure](https://portal.azure.com) como administrador de segurança ou administrador global e navegue para o painel **Azure Information Protection**.

2. No painel inicial do Azure Information Protection, selecione **Políticas de âmbito**.

3. No painel **Azure Information Protection - Políticas de âmbito**, selecione o menu de contexto (**...** ) junto à política que contém as definições avançadas. Em seguida, selecione **Definições avançadas**.
    
    Pode configurar as definições avançadas para a Política global, bem como para as políticas de âmbito.

4. No painel **Definições avançadas**, escreva o nome e o valor da definição avançada e, em seguida, selecione **Guardar e fechar**.

5. Clique em **Publicar**e garanta que os utilizadores desta política reiniciam as aplicações do Office que tinham abertas.

6. Caso já não precise da definição e pretenda reverter para o comportamento predefinido: no painel **Definições avançadas**, selecione o menu de contexto (**...** ) junto à definição que já não é precisa e, em seguida, selecione **Eliminar**. Em seguida, clique em **Guardar e fechar**e publique novamente a política modificada.

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Impedir pedidos de início de sessão para computadores só com AD RMS

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection. Para computadores que só comunicam com AD RMS, esta configuração pode resultar num pedido desnecessário de início de sessão aos utilizadores. Pode impedir este pedido de início de sessão ao editar o registo:

Localize o nome do valor seguinte e, em seguida, defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Independentemente desta definição, o cliente do Azure Information Protection segue o [processo de deteção do serviço RMS](../rms-client/client-deployment-notes.md#rms-service-discovery) padrão, para localizar o respetivo cluster AD RMS.

## <a name="sign-in-as-a-different-user"></a>Iniciar sessão como um utilizador diferente

Num ambiente de produção, normalmente, os utilizadores não precisam de iniciar sessão como um utilizador diferente quando estão a utilizar o cliente do Azure Information Protection. No entanto, como administrador, poderá ter de iniciar sessão como um utilizador diferente durante uma fase de teste. 

Pode verificar com que conta tem sessão iniciada atualmente através da caixa de diálogo do **Microsoft Azure Information Protection**: abra uma aplicação do Office e, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e comentários**. O nome da sua conta é apresentado na secção **Estado do cliente**.

Confirme que também verifica o nome de domínio da conta com sessão iniciada que é apresentada. Pode não perceber que tem sessão iniciada com o nome da conta certo, mas com o domínio errado. Um sinal de utilização da conta errada inclui a impossibilidade de transferir a política do Azure Information Protection ou não ver as etiquetas ou o comportamento esperado.

Para iniciar sessão como um utilizador diferente:

1. Dependendo da versão do cliente do Azure Information Protection: 
    
    - Para a versão de disponibilidade geral do cliente Azure Information Protection: com um editor de registo, navegue até **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP** e elimine o valor **TokenCache** (e os dados do valor associados).
    
    - Para a versão de pré-visualização atual do cliente Azure Information Protection: navegue até **%localappdata%\Microsoft\MSIP** e elimine o ficheiro **TokenCache**.

2. Reinicie as aplicações do Office abertas e inicie sessão com a sua conta de utilizador diferente. Se não vir um pedido na aplicação do Office para iniciar sessão no serviço Azure Information Protection, volte à caixa de diálogo do **Microsoft Azure Information Protection** e clique em **Iniciar sessão** na secção **Estado do cliente** atualizada.

Além disso,

- esta solução é suportada para iniciar sessão como outro utilizador a partir do mesmo inquilino. Não é suportada para iniciar sessão como outro utilizador a partir de um inquilino diferente. Para testar o Azure Information Protection com vários inquilinos, utilize computadores diferentes.

- Se estiver a utilizar o início de sessão único, tem de terminar sessão no Windows e iniciar sessão com a sua outra conta de utilizador após editar o registo. O cliente do Azure Information Protection faz, em seguida, a autenticação automaticamente através da conta de utilizador com sessão iniciada.

- Caso pretenda repor as definições de utilizador para o serviço Azure Rights Management, pode fazê-lo através da opção **Ajuda e Comentários**.

- Se pretender eliminar a política do Azure Information Protection atualmente transferida, elimine o ficheiro **Policy.msip** da pasta **%localappdata%\Microsoft\MSIP**.

- Se tiver a versão de pré-visualização atual do cliente Azure Information Protection, pode utilizar a opção **Repor definições** de **Ajuda e Feedback** para terminar sessão e eliminar a política do Azure Information Protection atualmente transferida.

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ocultar a opção de menu Classificar e Proteger no Explorador de Ficheiros do Windows

Pode configurar esta configuração avançada ao editar o registo quando tiver a versão do cliente do Azure Information Protection 1.3.0.0 ou superior. 

Crie o nome do valor DWORD seguinte (com quaisquer dados do valor):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Suporte para computadores desligados

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection para transferir a política do Azure Information Protection mais recente. Se tiver um computador que sabe que não poderá estabelecer ligação à Internet durante um período de tempo, poderá impedir o cliente de tentar estabelecer ligação ao serviço ao editar o registo. 

Localize o nome do valor seguinte e defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Confirme se o cliente tem um ficheiro de política válido denominado **Policy.msip** na pasta **%localappdata%\Microsoft\MSIP**. Se necessário, pode exportar a política a partir do portal do Azure e copiar o ficheiro exportado para o computador cliente. Também pode utilizar este método para substituir um ficheiro de política desatualizada pela política publicada mais recente.

## <a name="hide-the-do-not-forward-button-in-outlook"></a>Ocultar o botão Não Reencaminhar no Outlook

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Esta definição requer também uma versão de pré-visualização do cliente do Azure Information Protection com uma versão mínima de **1.8.41.0**.

Quando configura esta definição, oculta o botão **Não Reencaminhar** no friso do Outlook. Não oculta esta opção a partir dos menus do Office.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **DisableDNF**

- Valor: **Verdadeiro**

## <a name="make-the-custom-permissions-options-unavailable-to-users"></a>Tornar as opções de permissões personalizadas indisponíveis para os utilizadores

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando configura esta definição e publica a política para os utilizadores, as opções de permissões personalizadas das seguintes localizações ficam indisponíveis para seleção pelos utilizadores:

- Nas aplicações do Office: separador **Base** > grupo de **Proteção** > **Proteger** > **Permissões Personalizadas**

- No Explorador de Ficheiros: clique com o botão direito do rato > **Classificar e proteger** > **Permissões personalizadas**

Esta definição não tem efeito nas permissões personalizadas que pode configurar a partir das opções do menu do Office. 

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **EnableCustomPermissions**

- Valor: **Falso**

## <a name="permanently-hide-the-azure-information-protection-bar"></a>Ocultar permanentemente a barra do Azure Information Protection

Esta configuração utiliza uma definição avançada que tem de configurar no portal do Azure. Esta definição requer também uma versão de pré-visualização do cliente do Azure Information Protection com uma versão mínima de **1.9.58.0**.

Quando configura esta definição e publica a política para os utilizadores, se um utilizador optar por não mostrar a barra do Azure Information Protection nas aplicações do Office, a barra permanece oculta. Tal acontece quando o utilizador desmarca a opção **Mostrar Barra** do separador **Base**, grupo de **Proteção**, botão **Proteger**. Esta definição não tem qualquer efeito caso o utilizador feche a barra através do ícone **Fechar esta barra**.

Apesar de a barra do Azure Information Protection permanecer oculta, os utilizadores ainda podem selecionar uma etiqueta na barra apresentada temporariamente caso tenha configurado a classificação recomendada ou um documento ou um e-mail tenha de ter uma etiqueta. A definição não tem igualmente qualquer efeito nas etiquetas configuradas por si ou por terceiros, tais como a classificação manual ou automática, ou na definição de uma etiqueta predefinida.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **EnableBarHiding**

- Valor: **Verdadeiro**

## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integração com a classificação de mensagem do Exchange para uma solução de etiquetagem do dispositivo móvel

Embora o Outlook na Web ainda não ofereça suporte à proteção e à classificação do Azure Information Protection, pode utilizar a classificação de mensagem do Exchange para expandir as etiquetas do Azure Information Protection para os seus utilizadores móveis.

Para obter esta solução: 

1. Utilize o cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) do Exchange PowerShell para criar classificações de mensagens com a propriedade Nome que mapeia os seus nomes de etiquetas na sua política do Azure Information Protection. 

2. Crie uma regra de transporte do Exchange para cada etiqueta: aplique a regra quando as propriedades da mensagem incluírem a classificação que configurou e modifique as propriedades das mensagens para definir um cabeçalho da mensagem. 

    Para o cabeçalho da mensagem, encontra as informações a especificar ao inspecionar os cabeçalhos de Internet do e-mail que enviou e classificou com a etiqueta do Azure Information Protection. Procure o cabeçalho **msip_labels** e a cadeia que imediatamente a seguir, até ao ponto e vírgula, inclusive. Utilizando o exemplo anterior:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Em seguida, para o cabeçalho da mensagem na regra, especifique **msip_labels** para o cabeçalho e a parte restante da cadeia para o valor do cabeçalho. Por exemplo:
    
    ![Exemplo de uma regra de transporte do Exchange Online que define o cabeçalho de mensagem de uma etiqueta específica do Azure Information Protection](../media/exchange-rule-for-message-header.png)

Antes de testar esta configuração, lembre-se de que é frequente ocorrer um atraso ao criar ou editar regras de transporte (por exemplo, poderá ter de esperar uma hora). Quando a regra entrar em vigor, agora acontecerão os seguintes eventos quando os utilizadores utilizarem o Outlook na Web ou um cliente para dispositivos móveis que suporte a proteção do Rights Management: 

- Os utilizadores selecionam a classificação de mensagens do Exchange e enviam o e-mail.

- A regra do Exchange deteta a classificação do Exchange e modifica o cabeçalho da mensagem em conformidade para adicionar a classificação do Azure Information Protection.

- Quando os destinatários veem o e-mail no Outlook e têm o cliente do Azure Information Protection instalado, veem a etiqueta do Azure Information Protection atribuída e quaisquer cabeçalhos, rodapés ou marcas de água de e-mail correspondentes. 

Se as suas etiquetas do Azure Information Protection aplicarem a proteção da gestão de direitos, adicione esta proteção à configuração da regra: ao selecionar a opção para modificar a segurança da mensagem, aplique a proteção de direitos e, em seguida, selecione a opção Não Reencaminhar ou modelo do RMS.

Pode igualmente configurar regras de transporte para fazer o mapeamento inverso. Quando uma etiqueta do Azure Information Protection é detetada, é definida uma classificação de mensagens do Exchange correspondente:

- Para cada etiqueta do Azure Information Protection: crie uma regra de transporte que seja aplicada quando o cabeçalho **msip_labels** incluir o nome da sua etiqueta (por exemplo, **Geral**) e aplique uma classificação de mensagens que mapeie esta etiqueta.


## <a name="next-steps"></a>Próximos passos
Agora que personalizou o cliente do Azure Information Protection, veja os seguintes recursos para obter informações adicionais que poderá precisar para suportar este cliente:

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
