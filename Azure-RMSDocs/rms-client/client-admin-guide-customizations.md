---
title: Configurações personalizadas do cliente do Azure Information Protection
description: Informações sobre a personalização do cliente do Azure Information Protection para Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/08/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 3cd27fc4a060b6c7328495ad46d53768c28ff223
ms.sourcegitcommit: ce2078712d111f102a72b3a8697121f1390bdf07
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59289473"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-client"></a>Guia do administrador: Configurações personalizadas do cliente do Azure Information Protection

>*Aplica-se a: Serviços de gestão de direitos do Active Directory [do Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 com SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Utilize as seguintes informações para as configurações avançadas que poderá precisar para cenários específicos ou um subconjunto de utilizadores ao gerir o cliente do Azure Information Protection.

Algumas destas definições requerem a edição do registo e algumas utilizam definições avançadas que tem de configurar no portal do Azure e, em seguida, publicar para os clientes transferirem.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Como configurar as definições avançadas de configuração de cliente no portal

1. Se ainda não o tiver feito, numa nova janela do browser, [inicie sessão no portal do Azure](../configure-policy.md#signing-in-to-the-azure-portal)e, em seguida, navegue para o **do Azure Information Protection** painel.

2. Do **classificações** > **etiquetas** opção de menu: Selecione **políticas**.

3. Sobre o **do Azure Information Protection - políticas** painel, selecione o menu de contexto (**...** ) junto à política que contém as definições avançadas. Em seguida, selecione **Definições avançadas**.
    
    Pode configurar as definições avançadas para a Política global, bem como para as políticas de âmbito.

4. No painel **Definições avançadas**, escreva o nome e o valor da definição avançada e, em seguida, selecione **Guardar e fechar**.

5. Certifique-se de que os utilizadores desta política reiniciam as aplicações do Office que tinham abertas.

6. Se já não precisar da definição e pretenda reverter para o comportamento padrão: Sobre o **definições avançadas** painel, selecione o menu de contexto (**...** ) junto à definição que já não precisa e, em seguida, selecione **eliminar**. Em seguida, clique em **guarde e feche**.

#### <a name="available-advanced-client-settings"></a>Definições de cliente avançadas disponíveis

|Definição|Cenário e instruções|
|----------------|---------------|
|DisableDNF|[Ocultar ou mostrar o botão não reencaminhar no Outlook](#hide-or-show-the-do-not-forward-button-in-outlook)|
|CompareSubLabelsInAttachmentAction|[Ativar o suporte de ordem para subetiquetas](#enable-order-support-for-sublabels-on-attachments) 
|EnableBarHiding|[Ocultar permanentemente a barra do Azure Information Protection](#permanently-hide-the-azure-information-protection-bar)|
|EnableCustomPermissions|[Tornar as opções de permissões personalizadas disponíveis ou não está disponível para utilizadores](#make-the-custom-permissions-options-available-or-unavailable-to-users)|
|EnableCustomPermissionsForCustomProtectedFiles|[Para ficheiros protegidos com permissões personalizadas, apresentar sempre permissões personalizadas aos utilizadores no Explorador de ficheiros](#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer) |
|EnablePDFv2Protection|[Não proteger ficheiros PDF com a norma ISO para a encriptação de PDF](#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption)|
|LabelbyCustomProperty|[Migrar as etiquetas de Secure Islands e outras soluções de etiquetas](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|LabelToSMIME|[Configurar uma etiqueta para aplicar a proteção de S/MIME no Outlook](#configure-a-label-to-apply-smime-protection-in-outlook)|
|Nível de Registo|[Alterar o nível de registo de local](#change-the-local-logging-level)
|LogMatchedContent|[Desativar o envio correspondências de tipo de informações para um subconjunto de utilizadores](#disable-sending-information-type-matches-for-a-subset-of-users)|
|OutlookBlockUntrustedCollaborationLabel|[Implementar as mensagens pop-up no Outlook que avisar, justificar ou bloquear mensagens de e-mail a ser enviadas](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookCollaborationTrustedDomains|[Implementar as mensagens pop-up no Outlook que avisar, justificar ou bloquear mensagens de e-mail a ser enviadas](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookDefaultLabel|[Definir uma etiqueta predefinida diferente para o Outlook](#set-a-different-default-label-for-outlook)|
|OutlookJustifyUntrustedCollaborationLabel|[Implementar as mensagens pop-up no Outlook que avisar, justificar ou bloquear mensagens de e-mail a ser enviadas](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookRecommendationEnabled|[Ativar a classificação recomendada no Outlook](#enable-recommended-classification-in-outlook)|
|OutlookWarnUntrustedCollaborationLabel|[Implementar as mensagens pop-up no Outlook que avisar, justificar ou bloquear mensagens de e-mail a ser enviadas](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|PostponeMandatoryBeforeSave|[Remova "Agora não" para os documentos quando utiliza a etiquetagem obrigatório](#remove-not-now-for-documents-when-you-use-mandatory-labeling)|
|ProcessUsingLowIntegrity|[Desativar o nível de baixa integridade para a deteção de impressão](#disable-the-low-integrity-level-for-the-scanner)|
|PullPolicy|[Suporte para computadores desligados](#support-for-disconnected-computers)
|RemoveExternalContentMarkingInApp|[Remover os cabeçalhos e rodapés de outras soluções de etiquetas](#remove-headers-and-footers-from-other-labeling-solutions)|
|ReportAnIssueLink|[Adicionar "Relatar um problema" para os utilizadores](#add-report-an-issue-for-users)|
|RunAuditInformationTypeDiscovery|[Ativar a análise do Azure Information Protection detetar informações confidenciais em documentos](#enable-azure-information-protection-analytics-to-discover-sensitive-information-in-documents)|
|RunPolicyInBackground|[Ativar a classificação para executar continuamente em segundo plano](#turn-on-classification-to-run-continuously-in-the-background)|
|ScannerConcurrencyLevel|[Limitar o número de segmentos utilizados pelo leitor](#limit-the-number-of-threads-used-by-the-scanner)|
|SyncPropertyName|[Etiqueta de um documento do Office usando uma propriedade personalizada existente](#label-an-office-document-by-using-an-existing-custom-property)|
|SyncPropertyState|[Etiqueta de um documento do Office usando uma propriedade personalizada existente](#label-an-office-document-by-using-an-existing-custom-property)|

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Impedir pedidos de início de sessão para computadores só com AD RMS

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection. Para computadores que só comunicam com AD RMS, esta configuração pode resultar num pedido desnecessário de início de sessão aos utilizadores. Pode impedir que este pedido de início de sessão ao editar o registo.

 - Localize o nome do valor seguinte e, em seguida, defina os dados do valor como **0**:
    
    **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Independentemente desta definição, o cliente do Azure Information Protection ainda segue o padrão [processo de deteção do serviço de RMS](client-deployment-notes.md#rms-service-discovery) para localizar o respetivo cluster AD RMS.

## <a name="sign-in-as-a-different-user"></a>Iniciar sessão como um utilizador diferente

Num ambiente de produção, normalmente, os utilizadores não precisam de iniciar sessão como um utilizador diferente quando estão a utilizar o cliente do Azure Information Protection. No entanto, como administrador, poderá ter de iniciar sessão como um utilizador diferente durante uma fase de teste. 

Pode verificar com que conta tem atualmente sessão iniciada como ao utilizar o **Microsoft Azure Information Protection** caixa de diálogo: Abra uma aplicação do Office, no separador **Base**, no grupo **Proteção**, clique em **Proteger** e, em seguida, clique em **Ajuda e feedback**. O nome da sua conta é apresentado na secção **Estado do cliente**.

Confirme que também verifica o nome de domínio da conta com sessão iniciada que é apresentada. Pode não perceber que tem sessão iniciada com o nome da conta certo, mas com o domínio errado. Um sinal de utilização da conta errada inclui a impossibilidade de transferir a política do Azure Information Protection ou não ver as etiquetas ou o comportamento esperado.

Para iniciar sessão como um utilizador diferente:

1. Navegue para **%localappdata%\Microsoft\MSIP** e eliminar os **TokenCache** ficheiro.

2. Reinicie as aplicações do Office abertas e inicie sessão com a sua conta de utilizador diferente. Se não vir um pedido na aplicação do Office para iniciar sessão no serviço Azure Information Protection, volte à caixa de diálogo do **Microsoft Azure Information Protection** e clique em **Iniciar sessão** na secção **Estado do cliente** atualizada.

Além disso:

- Se o cliente do Azure Information Protection é ainda com sessão iniciado com a conta antiga depois de concluir estes passos, elimine todos os cookies do Internet Explorer e, em seguida, repita os passos 1 e 2.

- Se estiver a utilizar o início de sessão único, tem de terminar sessão no Windows e inicie sessão com a sua conta de utilizador diferente depois de eliminar o ficheiro de token. O cliente do Azure Information Protection faz, em seguida, a autenticação automaticamente através da conta de utilizador com sessão iniciada.

- esta solução é suportada para iniciar sessão como outro utilizador a partir do mesmo inquilino. Não é suportada para iniciar sessão como outro utilizador a partir de um inquilino diferente. Para testar o Azure Information Protection com vários inquilinos, utilize computadores diferentes.

- Pode utilizar o **repor definições** opção partir **ajuda e Feedback** para terminar sessão e eliminar a política do Azure Information Protection atualmente transferida.


## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>Impor o modo apenas de proteção quando a sua organização tiver uma mistura de licenças

Se sua organização não tem quaisquer licenças do Azure Information Protection, mas tem licenças para o Office 365 que incluem o serviço Azure Rights Management para proteger os dados, o cliente do Azure Information Protection para Windows é executada automaticamente [modo apenas de proteção](client-protection-only-mode.md).

No entanto, se sua organização tiver uma subscrição do Azure Information Protection, por predefinição todos os computadores Windows podem transferir a política do Azure Information Protection. O cliente do Azure Information Protection não fazer para licenciar a verificação e de imposição. 

Se tiver alguns utilizadores que não tem uma licença do Azure Information Protection, mas tiver uma licença do Office 365 que inclui o serviço Azure Rights Management, editar o registo nos computadores dos utilizadores, estes para impedir que os utilizadores a executar o não licenciados classificação e etiquetagem funcionalidades do Azure Information Protection.

Localize o nome do valor seguinte e defina os dados do valor como **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Além disso, verifique que estes computadores não têm um arquivo chamado **msip** no **%LocalAppData%\Microsoft\MSIP** pasta. Se este ficheiro já existir, elimine-o. Este ficheiro contém a política do Azure Information Protection e poderá ter transferido antes de editar o registo ou se o cliente do Azure Information Protection foi instalado com a opção de demonstração.

## <a name="add-report-an-issue-for-users"></a>Adicionar "Relatar um problema" para os utilizadores

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando especificar a seguinte definição de cliente avançada, os utilizadores verão uma **comunicar um problema** opção que pode selecionar a partir do **ajuda e Feedback** caixa de diálogo do cliente. Especifique uma cadeia de caracteres HTTP para a ligação. Por exemplo, uma página da web personalizada para os utilizadores comuniquem problemas, ou um endereço de e-mail que vai para o suporte técnico. 

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **ReportAnIssueLink**

- Valor: **\<Cadeia de caracteres HTTP >**

Valor de exemplo para um Web site: `https://support.contoso.com`

Valor de exemplo para um endereço de e-mail: `mailto:helpdesk@contoso.com`

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ocultar a opção de menu Classificar e Proteger no Explorador de Ficheiros do Windows

Crie o nome do valor DWORD seguinte (com quaisquer dados do valor):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Suporte para computadores desligados

Por predefinição, o cliente do Azure Information Protection tenta automaticamente estabelecer ligação ao serviço Azure Information Protection para transferir a política do Azure Information Protection mais recente. Se tiver computadores que sabe que não será possível estabelecer ligação à Internet durante um período de tempo, pode impedir que o cliente tentar ligar ao serviço ao editar o registo. 

Tenha em atenção que sem uma ligação à Internet, o cliente não é possível aplicar proteção (ou remover proteção), utilizando a chave de com base na cloud da sua organização. Em vez disso, o cliente está limitado a utilizar as etiquetas que aplicam apenas a classificação ou proteção que utiliza [HYOK](../configure-adrms-restrictions.md).

Pode impedir que um pedido de início de sessão para o serviço Azure Information Protection ao utilizar um [definição de cliente avançado](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure e, em seguida, transferir a política para os computadores. Em alternativa, pode impedir este pedido de início de sessão ao editar o registo.

- Para configurar a definição de cliente avançado:
    
    1. Introduza as seguintes cadeias:
    
        - Chave: **PullPolicy**
        
        - Valor: **FALSO**
    
    2. Transferir a política com esta definição e instalá-lo em computadores utilizando as instruções que se seguem.

- Em alternativa, editar o registo:
    
    - Localize o nome do valor seguinte e, em seguida, defina os dados do valor como **0**:
    
        **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 


O cliente tem de ter um ficheiro de política válido denominado **msip**, na **%LocalAppData%\Microsoft\MSIP** pasta.

Pode exportar a política global ou de uma política de âmbito do portal do Azure e copie o ficheiro exportado para o computador cliente. Também pode utilizar este método para substituir o ficheiro de política de um-fora-de-data com a política mais recente. No entanto, exportar a política não suporta o cenário em que um utilizador pertencer a mais do que uma política de âmbito. Também tenha em atenção que se os utilizadores selecionarem a **repor definições** opção partir [ajuda e feedback](client-admin-guide.md#help-and-feedback-section), esta ação elimina o ficheiro de política e apresenta-o cliente inoperável até que substitua manualmente o ficheiro de política ou o cliente liga-se ao serviço transferir a política.

Ao exportar a política do portal do Azure, será transferido um arquivo zipado contém várias versões da política. Estas versões de política correspondem a diferentes versões do cliente do Azure Information Protection:

1. Deszipe o ficheiro e utilize a seguinte tabela para identificar qual arquivo de política que precisa. 
    
    |Nome de ficheiro|Versão de cliente correspondente|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |versão 1.2|
    |Policy1.2.msip |versão 1.3 1.7|
    |Policy1.3.msip |versão 1.8 1.29|
    |Policy1.4.msip |versão 1.32 e posterior|
    
2. Mudar o nome do ficheiro identificado para **msip**e, em seguida, copie-o para o **%LocalAppData%\Microsoft\MSIP** pasta em computadores que tenham o cliente do Azure Information Protection instalado. 

Se o computador desconectado estiver a executar a versão de pré-visualização do scanner do Azure Information Protection, existem passos de configuração adicionais que deve efetuar. Para obter mais informações, consulte [restrição: O servidor de scanner não pode ter conectividade à Internet](../deploy-aip-scanner-preview.md#restriction-the-scanner-server-cannot-have-internet-connectivity) das instruções de implementação do scanner.

## <a name="hide-or-show-the-do-not-forward-button-in-outlook"></a>Ocultar ou mostrar o botão não reencaminhar no Outlook

O método recomendado para configurar esta opção é utilizar o [definição de política](../configure-policy-settings.md) **adicionar o botão não reencaminhar ao Friso do Outlook**. No entanto, também pode configurar esta opção ao utilizar um [definição de cliente avançado](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que configurar no portal do Azure.

Quando configura esta definição, oculta ou mostra os **não reencaminhar** botão da faixa de opções no Outlook. Esta definição não tem nenhum efeito sobre a opção não reencaminhar de menus do Office.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **DisableDNF**

- Valor: **TRUE** para ocultar o botão, ou **False** para mostrar o botão

## <a name="make-the-custom-permissions-options-available-or-unavailable-to-users"></a>Tornar as opções de permissões personalizadas disponíveis ou não está disponível para utilizadores

O método recomendado para configurar esta opção é utilizar o [definição de política](../configure-policy-settings.md) **disponibilizar a opção de permissões personalizadas para utilizadores**. No entanto, também pode configurar esta opção ao utilizar um [definição de cliente avançado](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que configurar no portal do Azure. 

Quando configura esta definição e publica a política para utilizadores, as opções de permissões personalizadas ficam visíveis para os utilizadores selecionarem suas próprias definições de proteção ou eles estão ocultos para que os utilizadores não é possível selecionar suas próprias definições de proteção, a menos que lhe for pedido.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **EnableCustomPermissions**

- Valor: **TRUE** para tornar a opção de permissões personalizadas visível, ou **False** para ocultar esta opção

## <a name="for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer"></a>Para ficheiros protegidos com permissões personalizadas, apresentar sempre permissões personalizadas aos utilizadores no Explorador de ficheiros

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Esta definição está em pré-visualização e requer a versão de pré-visualização do cliente.

Quando configura a [definição de política](../configure-policy-settings.md) **disponibilizar a opção de permissões personalizadas para utilizadores** ou o equivalente definição de cliente avançado na secção anterior, os utilizadores não são capazes de ver ou alterar o permissões personalizadas que já estiverem definidas num documento protegido. 

Quando criar e configurar este cliente avançado definição, os utilizadores podem ver e alterar as permissões personalizadas para um documento protegido, quando utilizar o Explorador de ficheiros e o ficheiro com o botão direito. O **permissões personalizadas** opção a partir do **proteger** botão da faixa de opções do Office permanece oculto.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **EnableCustomPermissionsForCustomProtectedFiles**

- Valor: **Verdadeiro**

## <a name="permanently-hide-the-azure-information-protection-bar"></a>Ocultar permanentemente a barra do Azure Information Protection

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Usá-lo apenas quando os [definição de política](../configure-policy-settings.md) **apresentar a barra de Information Protection nas aplicações do Office** está definida como **no**.

Por predefinição, se um utilizador desmarca a **Mostrar barra** opção da **home page** separador, **proteção** grupo, **proteger** botão, as informações Barra de proteção já não é apresentado nessa aplicação do Office. No entanto, a barra apresenta automaticamente novamente na próxima vez em que uma aplicação do Office é aberta.

Para impedir que a barra de exibir automaticamente novamente depois de um usuário tiver escolhido para ocultá-lo, utilize esta definição de cliente. Esta definição não tem qualquer efeito caso o utilizador feche a barra através do ícone **Fechar esta barra**.

Mesmo que a barra do Azure Information Protection permanece oculta, os utilizadores podem ainda a selecionar uma etiqueta de uma barra apresentada temporariamente, se tiver configurado a classificação recomendada ou quando um documento ou e-mail tem de ter uma etiqueta. 

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **EnableBarHiding**

- Valor: **Verdadeiro**

## <a name="enable-order-support-for-sublabels-on-attachments"></a>Ativar o suporte de ordem para subetiquetas nos anexos

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure.

Utilize esta definição quando tiver subetiquetas e tiver configurado o seguinte procedimento [definição de política](../configure-policy-settings.md):

- **Para mensagens de e-mail com anexos, aplique uma etiqueta que corresponda à classificação mais elevada desses anexos**

Configure as seguintes cadeias:

- Chave: **CompareSubLabelsInAttachmentAction**

- Valor: **Verdadeiro**

Sem esta definição, a primeira etiqueta, que se encontra na etiqueta principal com a classificação mais alta é aplicada à mensagem de e-mail. 

Com esta definição, a subetiqueta que está ordenada pela última vez da etiqueta principal com a classificação mais alta é aplicada à mensagem de e-mail. Se precisar reordenar as suas etiquetas para aplicar a etiqueta que pretende para este cenário, consulte [como eliminar ou reordenar uma etiqueta do Azure Information Protection](../configure-policy-delete-reorder.md).

## <a name="enable-recommended-classification-in-outlook"></a>Ativar a classificação recomendada no Outlook

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Esta definição está em pré-visualização e podem ser alteradas.

Quando configura uma etiqueta para a classificação recomendada, é pedido aos utilizadores que aceitem ou dispensar a etiqueta recomendada no Word, Excel e PowerPoint. Esta definição se estende esta recomendação de etiqueta também exibir no Outlook.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **OutlookRecommendationEnabled**

- Valor: **Verdadeiro**

## <a name="implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent"></a>Implementar as mensagens pop-up no Outlook que avisar, justificar ou bloquear mensagens de e-mail a ser enviadas

Esta configuração utiliza várias [definições de cliente avançadas](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Esta definição está em pré-visualização e requer a versão de pré-visualização do cliente.

Quando cria e configurar as seguintes definições de cliente avançado, os utilizadores verão mensagens pop-up no Outlook, que podem avisá-los antes de enviar uma mensagem de e-mail, peça-lhe para fornecer uma justificação por que eles estão a enviar uma mensagem de e-mail ou impedi-los de enviar um e-mail para qualquer um dos os seguintes cenários:

- **O e-mail ou anexo do e-mail tem uma etiqueta específica**:
    - O anexo pode ser qualquer tipo de ficheiro

- **O e-mail ou anexo do e-mail não tem uma etiqueta**:
    - O anexo pode ser um documento do Office ou o documento PDF

Quando estas condições são cumpridas e endereço de e-mail do destinatário não está incluído numa lista de nomes de domínio permitido que tenha especificado, o utilizador verá uma mensagem de pop-up com uma das seguintes ações:

- **Warn**: O utilizador pode confirmar e enviar ou Cancelar.

- **Justificar**: É pedido ao utilizador uma justificação (opções predefinidas ou de forma livre).  O utilizador pode, em seguida, enviar ou cancelar a mensagem de e-mail. O texto de justificação é escrito para o x-cabeçalho de e-mail, para que possa ser lido por outros sistemas. Por exemplo, serviços de (DLP) de prevenção de perda de dados.

- **Bloco**: O utilizador é impedido de enviar o e-mail, enquanto a condição permanece. A mensagem inclui a razão para bloquear o e-mail, para que o utilizador pode resolver o problema. Por exemplo, remova a destinatários específicos ou identifique o e-mail. 

A ação resultante é registada no registo de eventos do Windows local **Applications and Services Logs** > **do Azure Information Protection**:

- Avise mensagens: ID de informações 301

- Justificar mensagens: ID de informações 302

- Bloquear mensagens: ID de informações 303

Entrada de evento de exemplo de uma mensagem de justify:

```
Client Version: 1.48.1.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Price list.msg
Item Name: Price list
Process Name: OUTLOOK
Action: Justify
User Justification: My manager approved sharing of this content
Action Source: 
User Response: Confirmed
```


### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-specific-labels"></a>Para implementar o aviso, justificar ou bloquear as mensagens pop-up para etiquetas específicas:

Para implementar as mensagens pop-up para procurar etiquetas de específicas, deve conhecer o ID de etiqueta para essas etiquetas. O valor de ID de etiqueta é apresentado no **etiqueta** painel, quando ver ou configurar a política do Azure Information Protection no portal do Azure. Para os ficheiros que tenham as etiquetas aplicadas, também pode executar o [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) cmdlet do PowerShell para identificar o ID de etiqueta (MainLabelId ou SubLabelId). Quando uma etiqueta tem subetiquetas, sempre Especifica o ID de apenas uma subetiqueta e não a etiqueta principal.

Crie um ou mais das seguintes definições de cliente avançado com as seguintes chaves. Para os valores, especifique um ou mais etiquetas por suas IDs, cada um separado por vírgulas.

Valor de exemplo para vários IDs de etiqueta como uma cadeia separada por vírgulas: `dcf781ba-727f-4860-b3c1-73479e31912b,1ace2cc3-14bc-4142-9125-bf946a70542c,3e9df74d-3168-48af-8b11-037e3021813f`


- Avise mensagens:
    
    - Chave: **OutlookWarnUntrustedCollaborationLabel**
    
    - Valor: \< **IDs, separados por vírgulas de etiqueta**>

- Mensagens de justificação:
    
    - Chave: **OutlookJustifyUntrustedCollaborationLabel**
    
    - Valor: \< **IDs, separados por vírgulas de etiqueta**>

- Bloquear mensagens:
    
    - Chave: **OutlookBlockUntrustedCollaborationLabel**
    
    - Valor: \< **IDs, separados por vírgulas de etiqueta**>


### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-emails-or-attachments-that-dont-have-a-label"></a>Para implementar o aviso, justificar ou bloquear as mensagens pop-up para e-mails e anexos que não tenham uma etiqueta:

Crie o seguinte avançada de definição de cliente com um dos seguintes valores:

- Avise mensagens:
    
    - Chave: **OutlookUnlabeledCollaborationAction**
    
    - Valor: **Warn**

- Mensagens de justificação:
    
    - Chave: **OutlookUnlabeledCollaborationAction**
    
    - Valor: **Justificar**

- Bloquear mensagens:
    
    - Chave: **OutlookUnlabeledCollaborationAction**
    
    - Valor: **Bloquear**

- Desative estas mensagens:
    
    - Chave: **OutlookUnlabeledCollaborationAction**
    
    - Valor: **Off**

### <a name="to-specify-the-allowed-domain-names-for-recipients-exempt-from-the-pop-up-messages"></a>Para especificar os nomes de domínio permitido para isentar as mensagens pop-up de destinatários

Quando especificar um nome de domínio num definição de cliente avançado, os utilizadores não veem as mensagens pop-up para destinatários que têm de ter esse nome de domínio incluído no respetivo endereço de e-mail. Neste caso, os e-mails são enviados sem interrupção. Para especificar vários domínios, tem de adicioná-los como uma cadeia única, separada por vírgulas.

É uma configuração típica apresentar as mensagens pop-up apenas para os destinatários que são externas à sua organização ou que não estão autorizados parceiros para a sua organização. Neste caso, especificar todos os domínios de e-mail que são utilizados pela sua organização e pelos seus parceiros.

Crie a seguinte chave de definição de cliente avançado. Para o valor, especifique um ou mais domínios, cada um separado por vírgulas.

Valor de exemplo para múltiplos domínios como uma cadeia separada por vírgulas: `contoso.com,fabrikam.com,litware.com`

- Chave: **OutlookCollaborationTrustedDomains**

- Valor: **\<** nomes de domínio, separados por vírgulas**>**

Por exemplo, se especificar o nome de domínio contoso.com, os utilizadores não veem as mensagens pop-up no Outlook quando enviam um e-mail para john@sales.contoso.com.

## <a name="set-a-different-default-label-for-outlook"></a>Definir uma etiqueta predefinida diferente para o Outlook

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando configura esta definição, o Outlook não aplica a etiqueta predefinida que é configurada na política do Azure Information Protection para a definição **selecione a etiqueta predefinida**. Em vez disso, o Outlook pode aplicar uma etiqueta predefinida diferente, ou nenhuma etiqueta.

Para aplicar uma etiqueta diferente, tem de especificar o ID da etiqueta. O valor de ID de etiqueta é apresentado no **etiqueta** painel, quando ver ou configurar a política do Azure Information Protection no portal do Azure. Para os ficheiros que tenham as etiquetas aplicadas, também pode executar o [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) cmdlet do PowerShell para identificar o ID de etiqueta (MainLabelId ou SubLabelId). Quando uma etiqueta tem subetiquetas, sempre Especifica o ID de apenas uma subetiqueta e não a etiqueta principal.

Assim que o Outlook não se aplica a etiqueta predefinida, especifique **None**.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **OutlookDefaultLabel**

- Valor: \< **ID de etiqueta**> ou **None**

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Configurar uma etiqueta para aplicar a proteção de S/MIME no Outlook

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure.

Utilize esta definição apenas quando tem um funcionamento [implementação de S/MIME](https://docs.microsoft.com/office365/SecurityCompliance/s-mime-for-message-signing-and-encryption) e quiser uma etiqueta para aplicar automaticamente este método de proteção para mensagens de e-mail em vez de proteção do Rights Management do Azure Information Protection. A proteção resultante é o mesmo que quando um utilizador seleciona manualmente as opções de S/MIME do Outlook.

Esta configuração requer que especifique um definição com o nome de cliente avançado **LabelToSMIME** para cada etiqueta do Azure Information Protection que pretende aplicar a proteção de S/MIME. Em seguida, para cada entrada, defina o valor utilizando a seguinte sintaxe:

`[Azure Information Protection label ID];[S/MIME action]`

O valor de ID de etiqueta é apresentado no **etiqueta** painel, quando ver ou configurar a política do Azure Information Protection no portal do Azure. Para utilizar S/MIME com uma subetiqueta, sempre Especifica o ID de apenas a subetiqueta e não a etiqueta principal. Quando especificar uma subetiqueta, a etiqueta principal tem de ser no mesmo escopo, ou na política global.

A ação de S/MIME pode ser:

- `Sign;Encrypt`: Para aplicar uma assinatura digital e a encriptação S/MIME

- `Encrypt`: Para aplicar apenas a encriptação S/MIME

- `Sign`: Para aplicar uma assinatura digital apenas

Valores de exemplo para obter um ID de etiqueta de **dcf781ba-727f-4860-b3c1-73479e31912b**:

- Para aplicar uma assinatura digital e a encriptação S/MIME:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Sign;Encrypt**

- Para aplicar apenas a encriptação S/MIME:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Encrypt**
    
- Para aplicar uma assinatura digital apenas:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Sign**

Como resultado nesta configuração, quando a etiqueta é aplicada para uma mensagem de e-mail, a proteção de S/MIME é aplicada à mensagem de e-mail, além de classificação da etiqueta.

Se a etiqueta que especificou está configurada para proteção do Rights Management no portal do Azure, proteção de S/MIME substitui a proteção do Rights Management apenas no Outlook. Para todos os outros cenários que suportam a etiquetagem, será aplicada proteção do Rights Management.

Se pretender que a etiqueta a só ser visível no Outlook, configurar a etiqueta para aplicar a ação única definida pelo utilizador de **não reencaminhar**, conforme descrito no [início rápido: Configurar uma etiqueta para os utilizadores a proteger facilmente os e-mails que contêm informações confidenciais](../quickstart-label-dnf-protectedemail.md).

## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>Remova "Agora não" para os documentos quando utiliza a etiquetagem obrigatório

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando utiliza a [definição de política](../configure-policy-settings.md) dos **todos os documentos e e-mails devem ter uma etiqueta**, é pedido aos utilizadores para selecionar uma etiqueta quando eles primeiramente salvarem um documento do Office e quando eles enviam uma mensagem de e-mail. Para documentos, os utilizadores podem selecionar **agora não** temporariamente dispensar o pedido para selecionar uma etiqueta e retornar ao documento. No entanto, eles não é possível fechar o documento guardado sem rotulando-o. 

Quando configurar esta definição, remove a **agora não** opção para que os utilizadores devem selecionar uma etiqueta, quando o documento é salvo em primeiro lugar.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **PostponeMandatoryBeforeSave**

- Valor: **FALSO**

## <a name="turn-on-classification-to-run-continuously-in-the-background"></a>Ativar a classificação para executar continuamente em segundo plano

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Esta definição está em pré-visualização e podem ser alteradas.

Quando configura esta definição, ele altera a [predefinição de comportamento](../configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied) de como o cliente do Azure Information Protection aplica etiquetas automáticas e recomendadas para documentos: 

- Para Word, Excel e PowerPoint, a classificação automática seja executada continuamente em segundo plano.  

O comportamento não é alterada para o Outlook.

Quando o cliente do Azure Information Protection verifica periodicamente a documentos para as regras de condição que especificar, este comportamento permite a classificação automática e recomendada e proteção para documentos armazenados no SharePoint Online. Ficheiros grandes também poupar mais rapidamente porque as regras de condição já estiver a executar. 

As regras de condição não são executados em tempo real conforme um usuário digita. Em vez disso, eles são executados periodicamente como uma tarefa em segundo plano se o documento for modificado.

Para configurar esta definição avançada, introduza as cadeias seguintes:

- Chave: **RunPolicyInBackground**

- Valor: **Verdadeiro**

## <a name="dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption"></a>Não proteger ficheiros PDF com a norma ISO para a encriptação de PDF

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. 

Quando a versão mais recente do cliente do Azure Information Protection protege um ficheiro PDF, a extensão de nome de ficheiro resultante permanece como. pdf e respeita o ISO padrão para a encriptação de PDF. Para obter mais informações sobre este padrão, consulte a secção **encriptação 7.6** partir a [documento que é derivado da ISO 32000-1](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf) e publicado por Incorporated de sistemas do Adobe.

Se precisar do cliente para reverter para o comportamento em versões mais antigas do cliente que os ficheiros PDF protegidos através da utilização de uma extensão de nome de ficheiro. ppdf, utilize a seguinte definição avançada ao introduzir a seguinte cadeia:

- Chave: **EnablePDFv2Protection**

- Valor: **FALSO**

Por exemplo, poderá ter esta definição para todos os utilizadores se usar um leitor de PDF que não suporta a norma ISO para a encriptação de PDF. Em alternativa, poderá ter de configurá-lo para alguns usuários, como gradualmente na fase de numa alteração de leitor de PDF que suporta o novo formato. Outro motivo potencial para utilizar esta definição é se precisa adicionar proteção para documentos em PDF assinados. Documentos em PDF assinados podem ser protegidos além com o formato. ppdf porque esta proteção é implementada como um wrapper para o ficheiro. 

Para o scanner do Azure Information Protection utilizar a nova definição, é necessário reiniciar o serviço de scanner. Além disso, o scanner já não irá proteger documentos PDF por predefinição. Se pretender que os documentos PDF a ser protegido pelo leitor quando EnablePDFv2Protection é definido como False, deve [editar o registo](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner).

Para obter mais informações sobre a nova criptografia de PDF, consulte a mensagem de blogue [novo suporte para encriptação de PDF com proteção de informações do Microsoft](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757).

Para obter uma lista de leitores PDF que suportam a norma ISO para a encriptação de PDF e os leitores que suportam formatos mais antigos, consulte [leitores de PDF suportadas para o Microsoft Information Protection](protected-pdf-readers.md).

### <a name="to-convert-existing-ppdf-files-to-protected-pdf-files"></a>Para converter ficheiros. ppdf existentes para os ficheiros. pdf protegidos

Quando o cliente do Azure Information Protection tiver baixado a política de cliente com a nova definição, pode utilizar comandos do PowerShell para converter os arquivos existentes. ppdf para ficheiros. pdf protegidos que utilizam a norma ISO para a encriptação de PDF. 

Para utilizar as seguintes instruções para os ficheiros que não proteger a mesmo, tem de ter uma [direito de utilização da gestão de direitos](../configure-usage-rights.md) para remover a proteção de ficheiros ou ser um Superutilizador. Para ativar a funcionalidade de Superutilizador e configurar a sua conta para ser um Superutilizador, veja [configurar superutilizadores para o Azure Rights Management e serviços de deteção ou recuperação de dados](../configure-super-users.md).

Além disso, quando utilizar estas instruções para os ficheiros que não proteger a próprio, passa a [RMS emissor](../configure-usage-rights.md#rights-management-issuer-and-rights-management-owner). Neste cenário, o utilizador que originalmente protegeu o documento já não pode controlar e revogar. Se os utilizadores precisam de controlar e revogar os documentos PDF protegidos, peça-lhe para remover manualmente e, em seguida, volte a aplicar a etiqueta com o Explorador de ficheiros, faça duplo clique.

Utilizar comandos do PowerShell para converter os arquivos existentes. ppdf para ficheiros. pdf protegidos que utilizam a norma ISO para a encriptação de PDF:

1. Uso [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) com o ficheiro. ppdf. Por exemplo:
    
        Get-AIPFileStatus -Path \\Finance\Projectx\sales.ppdf

2. A partir da saída, tome nota dos seguintes valores de parâmetro:
    
   - O valor (GUID) para **SubLabelId**, se existir um. Se este valor está em branco, uma subetiqueta não foi usada, por isso, tenha em atenção o valor para **MainLabelId** em vez disso.
    
     Nota: Se não houver nenhum valor para **MainLabelId** pode ser, o ficheiro não é identificado. Neste caso, pode utilizar o [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) comando e [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) comando em vez dos comandos no passo 3 e 4.
    
   - O valor para **RMSTemplateId**. Se este valor é **acesso restrito**, um utilizador protegeu o ficheiro com permissões personalizadas, em vez das definições de proteção que estão configuradas para a etiqueta. Se continuar, essas permissões personalizadas serão substituídas por definições de proteção da etiqueta. Decida se pretende continuar ou pedir ao utilizador (valor apresentado para o **RMSIssuer**) remover a etiqueta e voltar a aplicar, juntamente com as respetivas permissões personalizadas originais.

3. Remover a etiqueta através de [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) com o *RemoveLabel* parâmetro. Se estiver a utilizar o [definição de política](../configure-policy-settings.md) dos **os utilizadores têm de fornecer justificação para definir uma etiqueta de classificação inferior, remover uma etiqueta ou remover a proteção**, também tem de especificar o  *Justificação* parâmetro com o motivo. Por exemplo: 
    
        Set-AIPFileLabel \\Finance\Projectx\sales.ppdf -RemoveLabel -JustificationMessage 'Removing .ppdf protection to replace with .pdf ISO standard'

4. Volte a aplicar a etiqueta original, especificando o valor para a etiqueta que identificou no passo 1. Por exemplo:
    
        Set-AIPFileLabel \\Finance\Projectx\sales.pdf -LabelId d9f23ae3-1234-1234-1234-f515f824c57b

O ficheiro mantém a extensão de nome de ficheiro. pdf, mas é classificado como antes, e é protegida utilizando a norma ISO para a encriptação de PDF.

## <a name="support-for-files-protected-by-secure-islands"></a>Suporte para ficheiros protegidos por Secure Islands

Esta opção de configuração está em pré-visualização e está sujeitas a alterações.

Se utilizou a Secure Islands para proteger documentos, poderá proteger texto e arquivos de imagem e ficheiros protegidos genericamente, como resultado desta proteção. Por exemplo, ficheiros que tenham uma extensão de nome de ficheiro. ptxt,. pjpeg ou. pfile. Ao editar o registo da seguinte forma, o Azure Information Protection pode descriptografar esses arquivos:


Adicione o seguinte valor DWORD de **EnableIQPFormats** para o seguinte caminho de registo e defina os dados de valor como **1**:

- Para uma versão de 64 bits do Windows: HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\MSIP

- Para uma versão de 32 bits do Windows: HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\MSIP

Como resultado desta edição de registo, são suportados os seguintes cenários:

- O Visualizador do Azure Information Protection pode abrir estes ficheiros protegidos.

- O scanner do Azure Information Protection pode inspecionar esses arquivos de informações confidenciais.

- Explorador de ficheiros, o PowerShell e o scanner do Azure Information Protection podem Etiquetar estes ficheiros. Como resultado, pode aplicar uma etiqueta do Azure Information Protection que aplica-se a nova proteção do Azure Information Protection ou que remove a proteção existente da Secure Islands.

- Pode utilizar o [personalização do cliente de migração de etiquetagem](#migrate-labels-from-secure-islands-and-other-labeling-solutions) para converter automaticamente a etiqueta de Secure Islands sobre esses protegidos ficheiros para uma etiqueta do Azure Information Protection.

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Migrar as etiquetas de Secure Islands e outras soluções de etiquetas

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure.

Esta configuração não é atualmente compatível com o novo comportamento padrão que protege ficheiros PDF com a norma ISO para a encriptação de PDF. Neste cenário, os ficheiros. ppdf não não possível abrir Explorador de ficheiros, PowerShell ou a deteção de impressão. Para resolver este problema, utilize o definição de cliente avançado [não utilize a norma ISO para encriptação de PDF](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption).

Para documentos do Office e dos documentos em PDF que estão identificados por Secure Islands, pode relabel estes documentos com uma etiqueta do Azure Information Protection ao utilizar um mapeamento por si. Também utilizar este método reutilizar as etiquetas de outras soluções existentes, quando os rótulos são em documentos do Office. 

> [!NOTE]
> Se tiver ficheiros diferentes dos documentos PDF e do Office protegidos pelo Secure Islands, estes podem de ser relabeled depois de editar o registo, conforme descrito no [secção anterior](#support-for-files-protected-by-secure-islands). 

Como resultado desta opção de configuração, a nova etiqueta do Azure Information Protection é aplicada pelo cliente do Azure Information Protection da seguinte forma:

- Para documentos do Office: Quando o documento é aberto na aplicação do ambiente de trabalho, a nova etiqueta do Azure Information Protection é mostrada como o conjunto e é aplicada quando o documento é salvo.

- Explorador de ficheiros: Na caixa de diálogo do Azure Information Protection, a nova etiqueta do Azure Information Protection é mostrada como o conjunto e é aplicada quando o usuário seleciona **aplicar**. Se o utilizador seleciona **Cancelar**, não se aplica a nova etiqueta.

- Para o PowerShell: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) aplica-se a nova etiqueta do Azure Information Protection. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) não apresenta a nova etiqueta do Azure Information Protection até que ele é definido por outro método.

- Para o scanner do Azure Information Protection: Relatórios de deteção quando a nova etiqueta do Azure Information Protection seria definida e pode ser aplicada esta etiqueta com o modo de imposição.

Esta configuração requer que especifique um definição com o nome de cliente avançado **LabelbyCustomProperty** para cada etiqueta do Azure Information Protection que pretende mapear para a etiqueta antiga. Em seguida, para cada entrada, defina o valor utilizando a seguinte sintaxe:

`[Azure Information Protection label ID],[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

O valor de ID de etiqueta é apresentado no **etiqueta** painel, quando ver ou configurar a política do Azure Information Protection no portal do Azure. Para especificar uma subetiqueta, a etiqueta principal tem de ser no mesmo escopo, ou na política global.

Especifique a sua escolha de um nome de regra de migração. Utilize um nome descritivo, que ajuda a identificar como um ou mais etiquetas da sua solução de etiquetagem anterior deve ser mapeado para uma etiqueta do Azure Information Protection. O nome é apresentado nos relatórios de scanner e no Visualizador de eventos. Tenha em atenção que esta definição não remove a etiqueta original do documento ou qualquer marcas visuais no documento que possa ter aplicados a etiqueta original. Para remover os cabeçalhos e rodapés, consulte a secção seguinte, [remover os cabeçalhos e rodapés de outras soluções de etiquetas](#remove-headers-and-footers-from-other-labeling-solutions).

### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Exemplo 1: Mapeamento do mesmo nome de etiqueta

Requisito: Documentos que tenham uma etiqueta de Secure Islands de "Confidencial" devem ser relabeled como "Confidencial" pelo Azure Information Protection.

Neste exemplo:

- A etiqueta do Azure Information Protection que pretende utilizar com o nome **confidencial** e tem um ID de etiqueta de **1ace2cc3-14bc-4142-9125-bf946a70542c**. 

- Com o nome da etiqueta de Secure Islands **confidencial** e armazenados na propriedade personalizada com o nome **classificação**.

A definição de cliente avançado:

    
|Nome|Valor|
|---------------------|---------|
|LabelbyCustomProperty|1ace2cc3-14bc-4142-9125-bf946a70542c, "etiqueta Secure Islands é confidencial", classificação, confidencial|

### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Exemplo 2: Mapeamento para um nome de etiqueta diferente

Requisito: Documentos identificados como "Confidenciais" por Secure Islands devem ser relabeled como "Altamente confidencial" pelo Azure Information Protection.

Neste exemplo:

- A etiqueta do Azure Information Protection que pretende utilizar com o nome **altamente confidencial** e tem um ID de etiqueta de **3e9df74d-3168-48af-8b11-037e3021813f**.

- Com o nome da etiqueta de Secure Islands **confidenciais** e armazenados na propriedade personalizada com o nome **classificação**.

A definição de cliente avançado:

    
|Nome|Valor|
|---------------------|---------|
|LabelbyCustomProperty|3e9df74d-3168-48af-8b11-037e3021813f, "etiqueta Secure Islands é sensível a", classificação, com diferenciação de|


### <a name="example-3-many-to-one-mapping-of-label-names"></a>Exemplo 3: Muitos-para-um mapeamento de nomes de etiqueta

Requisito: Tem duas etiquetas de Secure Islands que incluíssem a palavra "Interno" e pretender que os documentos com qualquer um destas etiquetas de Secure Islands para ser relabeled como "Geral" pelo Azure Information Protection.

Neste exemplo:

- A etiqueta do Azure Information Protection que pretende utilizar com o nome **gerais** e tem um ID de etiqueta de **2beb8fe7-8293-444c-9768-7fdc6f75014d**.

- As etiquetas de Secure Islands incluem a palavra **interno** e são armazenados na propriedade personalizada com o nome **classificação**.

A definição de cliente avançado:

    
|Nome|Valor|
|---------------------|---------|
|LabelbyCustomProperty|2beb8fe7-8293-444c-9768-7fdc6f75014d, "a etiqueta de Secure Islands contém interno", classificação,. \*Interno.\*|


## <a name="remove-headers-and-footers-from-other-labeling-solutions"></a>Remover os cabeçalhos e rodapés de outras soluções de etiquetas

Esta configuração utiliza várias [definições de cliente avançadas](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure. Estas definições estão em pré-visualização e podem ser alteradas.

As definições permitem-lhe remover ou substituir o texto com base em cabeçalhos ou rodapés de documentos quando essas marcas visuais foram aplicadas por outra solução de etiquetagem. Por exemplo, o rodapé antigo contém o nome de uma etiqueta antigo agora migrado para o Azure Information Protection com um novo nome de etiqueta e o seu próprio rodapé.

Quando o cliente recebe esta configuração em sua diretiva, o antigos cabeçalhos e rodapés são removidas ou substituídas quando o documento é aberto na aplicação do Office e qualquer etiqueta do Azure Information Protection é aplicada ao documento.

Esta configuração não é suportada para o Outlook e lembre-se de que quando usá-lo com o Word, Excel e PowerPoint, ele pode afetar negativamente o desempenho desses aplicativos para os utilizadores. A configuração permite-lhe definir as definições por aplicação, por exemplo, pesquisa de texto nos cabeçalhos e rodapés de documentos do Word, mas não planilhas do Excel ou apresentações do PowerPoint.

Uma vez que a correspondência de padrões afeta o desempenho para os utilizadores, recomendamos que limita os tipos de aplicações do Office (**W**ord, **i**xcel, **P**owerPoint) para apenas as que tem de ser pesquisada:

- Chave: **RemoveExternalContentMarkingInApp**

- Valor: \<**Tipos de aplicações do Office WXP**> 

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

Para remover este rodapé com várias linhas, crie as seguintes duas entradas:

- Chave 1: **ExternalContentMarkingToRemove**

- Valor da chave 1: **\*Confidencial***

- Chave 2: **ExternalContentMarkingToRemove**

- Valor da chave 2: **\*Etiqueta aplicada*** 

#### <a name="optimization-for-powerpoint"></a>Otimização para o PowerPoint

Rodapés no PowerPoint são implementados como formas. Para evitar a remoção de formas que contêm o texto que especificou, mas não são cabeçalhos ou rodapés, utilize um cliente avançado adicional definição denominada **PowerPointShapeNameToRemove**. Também recomendamos que utilize esta definição para evitar a verificar o texto em todas as formas, que é um processo com muitos recursos.

Se não especificar esta adicional definição de cliente avançada, e o PowerPoint está incluído nos **RemoveExternalContentMarkingInApp** valor, chave todas as formas serão verificadas para o texto que especificou no  **ExternalContentMarkingToRemove** valor. 

Para localizar o nome da forma que está usando como um cabeçalho ou rodapé:

1. No PowerPoint, apresentar os **seleção** painel: **Formato** separador > **dispor** grupo > **painel de seleção**.

2. Selecione a forma no slide que contém o cabeçalho ou rodapé. O nome da forma selecionada agora é realçado na **seleção** painel.

Utilize o nome da forma para especificar um valor de cadeia de caracteres para o **PowerPointShapeNameToRemove** chave. 

Exemplo: É o nome de forma **fc**. Para remover a forma com este nome, tem de especificar o valor: `fc`.

- Chave: **PowerPointShapeNameToRemove**

- Valor: \<**Nome da forma de PowerPoint**> 

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

## <a name="enable-azure-information-protection-analytics-to-discover-sensitive-information-in-documents"></a>Ativar a análise do Azure Information Protection detetar informações confidenciais em documentos

Esta configuração utiliza um [definição de cliente avançado](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure e requer a versão de pré-visualização atual do cliente do Azure Information Protection.

[A análise do Azure Information Protection](../reports-aip.md) pode detetar e comunicar documentos salvos pelos clientes do Azure Information Protection quando esse conteúdo contêm informações confidenciais. Por predefinição, estas informações não são enviadas para a análise do Azure Information Protection.

Para alterar este comportamento para que estas informações são enviadas, introduza as seguintes cadeias:

- Chave: **RunAuditInformationTypeDiscovery**

- Valor: **Verdadeiro**

Se não definir este cliente avançado definir, ainda que os resultados de auditoria são enviados do cliente do Azure Information Protection, mas a informação é limitada a quando um utilizador acedeu conteúdos etiquetados.

Por exemplo:

- Sem esta definição, pode ver que um utilizador acedeu Financial.docx assinalada como **confidencial \ vendas**.

- Com esta definição, pode ver que Financial.docx contém 6 números de cartão de crédito.
    
    - Se também de ativar [correspondências de conteúdo para uma análise mais aprofundada](../reports-aip.md#content-matches-for-deeper-analysis), além disso será possível ver quais são esses números de cartão de crédito.

## <a name="disable-sending-information-type-matches-for-a-subset-of-users"></a>Desativar o envio correspondências de tipo de informações para um subconjunto de utilizadores

Esta configuração utiliza um [definição de cliente avançado](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure e requer a versão de pré-visualização atual do cliente do Azure Information Protection.

Quando seleciona a caixa de verificação [analytics do Azure Information Protection](../reports-aip.md) que recolhe o conteúdo corresponde para seus tipos de informações confidenciais ou de suas condições personalizadas, por predefinição, estas informações são enviadas por todos os utilizadores. Se tiver alguns utilizadores que não devem enviar estes dados, crie a seguinte definição de cliente avançado um [política de âmbito](../configure-policy-scope.md) para estes utilizadores: 

- Chave: **LogMatchedContent**

- Valor: **Desativar**


## <a name="limit-the-number-of-threads-used-by-the-scanner"></a>Limitar o número de segmentos utilizados pelo leitor

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure.

Por predefinição, o scanner utiliza todos os recursos de processador disponíveis no computador que executa o serviço de scanner. Se tiver de limitar o consumo da CPU, enquanto este serviço está a analisar, crie a seguinte definição avançada. 

Para o valor, especifique o número de threads em simultâneo que a deteção de impressão pode ser executadas em paralelo. O scanner usa um thread separado para cada ficheiro que verifica a, pelo que esta configuração de limitação também define o número de ficheiros que podem ser analisados em paralelo. 

Quando configura pela primeira vez o valor para fins de teste, recomendamos que especifique 2 por núcleo e, em seguida, monitorize os resultados. Por exemplo, se executar a deteção de impressão num computador que tenha de 4 núcleos, primeiro defina o valor como 8. Se necessário, aumentar ou diminuir esse número, de acordo com o desempenho resultante que necessita para o computador de scanner e as taxas de verificação. 

- Chave: **ScannerConcurrencyLevel**

- Valor:  **\<número de threads em simultâneo >**

## <a name="disable-the-low-integrity-level-for-the-scanner"></a>Desativar o nível de baixa integridade para a deteção de impressão

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure.

Por predefinição, o scanner do Azure Information Protection é executado com um nível de baixa integridade. Esta definição proporciona maior isolamento de segurança, mas ao custo de desempenho. Um nível de baixa integridade é adequado se executar a deteção de impressão com uma conta que tem direitos (por exemplo, uma conta de administrador local) privilegiado porque esta definição ajuda a proteger o computador que executa a deteção de impressão.

No entanto, quando a conta de serviço que executa a deteção de impressão tem apenas os direitos documentados no [pré-requisitos do scanner](../deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner), nível baixo de integridade não é necessário e não é recomendado porque ele afeta negativamente o desempenho. 

Para obter mais informações sobre os níveis de integridade do Windows, consulte [o que é o mecanismo de integridade do Windows?](https://msdn.microsoft.com/library/bb625957.aspx)

Para configurar as definições avançadas para que o scanner é executado com um nível de integridade será automaticamente atribuído pelo Windows (uma conta de usuário padrão é executado com um nível de integridade média), introduza as seguintes cadeias:

- Chave: **ProcessUsingLowIntegrity**

- Valor: **FALSO**


## <a name="change-the-local-logging-level"></a>Alterar o nível de registo de local

Esta configuração utiliza uma [definição avançada de cliente](#how-to-configure-advanced-client-configuration-settings-in-the-portal) que tem de configurar no portal do Azure.

Por predefinição, o cliente do Azure Information Protection escreve cliente ficheiros de registo do **%localappdata%\Microsoft\MSIP** pasta. Estes ficheiros destinam-se para a resolução de problemas Support da Microsoft.
 
Para alterar o nível de registo para esses ficheiros, configure o seguinte avançada de definição de cliente:

- Chave: **LogLevel**

- Valor:  **\<nível de registo >**

Defina o nível de registo para um dos seguintes valores:

- **Off**: Nenhum registo local.

- **Erro**: Apenas erros.

- **Informações de**: Registo mínimo, que não inclui a nenhum evento IDs (a predefinição para a deteção de impressão).

- **Depurar**: Obter informações completas.

- **Rastreio**: Registo detalhado (a predefinição para os clientes). Para o scanner, esta definição tem um impacto significativo no desempenho e deve estar ativada para o scanner apenas se for solicitado pelo Support da Microsoft. Se é instruído para definir esse nível de registo para a deteção de impressão, não se esqueça de definir um valor diferente de quando os registos relevantes tiverem sido recolhidos.

Esta definição de cliente avançada não altera as informações que são enviadas para o Azure Information Protection para [central reporting](../reports-aip.md), ou alterar as informações que são gravadas para local [registo de eventos](client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client).

## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integração com a classificação de mensagem do Exchange para uma solução de etiquetagem do dispositivo móvel

Embora o Outlook na web ainda não suporta nativamente a classificação de Azure Information Protection e a proteção, pode utilizar a classificação de mensagem do Exchange para expandir suas etiquetas do Azure Information Protection para usuários móveis quando utilizarem o Outlook no Web. Outlook Mobile não suporta a classificação de mensagens do Exchange.

Para obter esta solução: 

1. Utilize o cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) do Exchange PowerShell para criar classificações de mensagens com a propriedade Nome que mapeia os seus nomes de etiquetas na sua política do Azure Information Protection. 

2. Crie uma regra de fluxo de correio do Exchange para cada etiqueta: Aplicar a regra quando as propriedades da mensagem incluírem a classificação que configurou e modifique as propriedades da mensagem para definir um cabeçalho de mensagem. 

     Para o cabeçalho da mensagem, encontra as informações a especificar ao inspecionar os cabeçalhos de Internet do e-mail que enviou e classificou com a etiqueta do Azure Information Protection. Procure o cabeçalho **msip_labels** e a cadeia que imediatamente a seguir, até ao ponto e vírgula, inclusive. Por exemplo:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Em seguida, para o cabeçalho da mensagem na regra, especifique **msip_labels** para o cabeçalho e a parte restante da cadeia para o valor do cabeçalho. Por exemplo:
    
    ![Exemplo do fluxo de correio Exchange Online de regra que define o cabeçalho da mensagem para uma etiqueta específica do Azure Information Protection](../media/exchange-rule-for-message-header.png)
    
    Nota: Quando a etiqueta é uma subetiqueta, também tem de especificar a etiqueta principal antes da subetiqueta no valor de cabeçalho, usando o mesmo formato. Por exemplo, se seu subetiqueta tem um GUID de 27efdf94-80a0 - 4d 02-b88c-b615c12d69a9, o valor pode ser semelhante ao seguinte: `MSIP_Label_ab70158b-bdcc-42a3-8493-2a80736e9cbd_Enabled=True;MSIP_Label_27efdf94-80a0-4d02-b88c-b615c12d69a9_Enabled=True;`

Antes de testar esta configuração, lembre-se de que é, muitas vezes, um atraso ao criar ou editar as regras de fluxo de correio (por exemplo, aguarde uma hora). Quando a regra entrar em vigor, agora que os seguintes eventos acontecem quando os utilizadores utilizarem o Outlook na web: 

- Os utilizadores selecionam a classificação de mensagens do Exchange e enviam o e-mail.

- A regra do Exchange deteta a classificação do Exchange e modifica o cabeçalho da mensagem em conformidade para adicionar a classificação do Azure Information Protection.

- Quando os destinatários internos veem o e-mail no Outlook e têm o cliente do Azure Information Protection instalado, verão a etiqueta do Azure Information Protection atribuída. 

Se as etiquetas do Azure Information Protection aplicarem a proteção, adicione esta proteção à configuração da regra: Selecionar a opção para modificar a segurança de mensagem, aplicar a proteção de direitos e, em seguida, selecione a opção não reencaminhar ou modelo de proteção.

Também pode configurar as regras de fluxo de correio para proceder ao mapeamento inverso. Quando uma etiqueta do Azure Information Protection é detetada, é definida uma classificação de mensagens do Exchange correspondente:

- Para cada etiqueta do Azure Information Protection: Crie uma regra de fluxo de correio que seja aplicada quando o **msip_labels** cabeçalho inclui o nome da sua etiqueta (por exemplo, **geral**) e aplique uma classificação de mensagens que mapeie esta etiqueta.


## <a name="next-steps"></a>Passos Seguintes
Agora que personalizou o cliente do Azure Information Protection, veja os seguintes recursos para obter informações adicionais que poderá precisar para suportar este cliente:

- [Ficheiros de cliente e registo de utilização](client-admin-guide-files-and-logging.md)

- [Controlo de documentos](client-admin-guide-document-tracking.md)

- [Tipos de ficheiro suportados](client-admin-guide-file-types.md)

- [Comandos do PowerShell](client-admin-guide-powershell.md)


